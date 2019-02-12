# Index

> **index:** acts as a signpost to help you quickly locate the data you want

Most databases allow you to add and remove indexes as you see fit. This does not affect the contents of the database, only the performance of the queries.

Adding an index increases the performance of your reads, but sacrifices the performance of your writes because everytime data is added to the database, there needs to be extra writes to include the new data in the index.

#### Well-chosen indexes speed up read queries, but every index slows down writes.


-------------------------
**Further Reading:**
- [ ] http://www.csbio.unc.edu/mcmillan/Media/Comp521F10Lecture15.pdf

**Sources:**

¹ Kleppmann, Martin. _Designing Data-Intensive Applications: the Big Ideas behind Reliable, Scalable, and Maintainable Systems._ OReilly Media, 2018, pp 71
