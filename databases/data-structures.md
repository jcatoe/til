# Flat files

# Indexes

> **index:** acts as a signpost to help you quickly locate the data you want

Most databases allow you to add and remove indexes as you see fit. This does not affect the contents of the database, only the performance of the queries.

Adding an index increases the performance of your reads, but sacrifices the performance of your writes because everytime data is added to the database, there needs to be extra writes to include the new data in the index.

#### Well-chosen indexes speed up read queries, but every index slows down writes.

## Hash Indexes

A hash index is similar to a dictionary type implemented as a hash map. When you insert a new key into the database, the key and the location of that key is stored in a hash index. This makes it easy to query for that key as you can just reference the hash index for the exact location.

#### Hash tables must fit in memory.

Each time a key is updated, a new line is added to the log, but these logs can become unwiedly so it helps to break them apart, into segments, once they reach a certain size. Each segment has its own hash table that can be stored in-memory. Writing changes to these logs does not update the data within the logs, instead a new line is written each time a change is made and to preventl these segments from using up all of the disk space, the segments are compacted.

_Compaction_ allows you to reduce the size of the log files by removing duplicate keys in the segment and only keeping the most recent update for each key. You can then write the compacted data to a new segment file and continue writing all of the new updates to a new file. The compaction process runs as a background job.

Since each segment has its own hash table, a query will search the most recent hash table for the key and if it's not in there, the next most recent and so on until it finds the correct key. The process of compaction keeps the amount of segments needed to be searched small so the operation happens relatively quickly.


#### Why is the hash table design an "append-only" process?

* Appending and segment merging are sequential write operations because it is easier to write in order than randomly on a spinning disk.
* Concurrency and crash recovery are much simpler if the files are immutable so you don't end up with a record that is only partially updated.
* Merging old segments prevents data files from getting fragmented over time.

When designing a hash table index, there are a lot of details that need to be taken into consideration and best practices that go along with each one.

* The file format for the logs needs to be quick and simple. CSV is usually frowned upon and it is preferred to use a binary format.
* When you want to delete a record, you have to append a special deletion record (sometimes called a _tombstone_) to the data file so that when the merge happens, the process knows which records are safe to remove.
* If a database is restarted, you will lose your in-memory hash table. You _could_ read all of the segment files back into memory, but that would be incredibly time consuming. Instead, you can speed up recovery by storing a snapship of each segment's hash table on disk.
* To avoid partially written records, you should implement a check to make sure corrupted parts of the log are detected and ignored.
* To allow concurrency control, there should only be one thread responsible for writes, but you can have multiple threads for reading.

#### Limitations of a hash table index:

* hash table must fit in memory
* range queries are not efficient (you can't query for a range, you have to search for each individual key)
* god I hope hash map and hash table are synonymous here

-------------------------
**Further Readings:**
- [ ] http://www.csbio.unc.edu/mcmillan/Media/Comp521F10Lecture15.pdf
- [ ] http://basho.com/wp-content/uploads/2015/05/bitcask-intro.pdf

**Sources:**

¹ Kleppmann, Martin. _Designing Data-Intensive Applications: the Big Ideas behind Reliable, Scalable, and Maintainable Systems._ OReilly Media, 2018, pp 71
