# Common File Related Commands

## Current Working Directory:
```
import os
os.path.dirname(os.path.realpath(__file__))

> /users/username/dev
```

## Join Folders:
Just add `os.path.dirname` for however many directories you want to go back.
```
import os
os.path.join(os.path.dirname(os.path.dirname(os.path.realpath(__file__))), 'code')

> /users/username/code
```

## Step Through Directories And Subdirectories:

```
  root_dir = os.path.dirname(os.path.dirname(os.path.realpath(__file__)))

  for sub_dir, dirs, files in os.walk(root_dir):
      # sub_dir = all sub folder paths in the root_dir, including the ones nested within those
      #    dirs = list of folder names within the current sub_dir
      #   files = list of files within the current sub_dir

      for file in files:
          # to get the full file path of each file
          file_path = os.path.join(sub_dir, file)
```


## TODO:
Add in notes about [pathlib](https://docs.python.org/3/library/pathlib.html) and [glob](https://docs.python.org/2/library/glob.html).
