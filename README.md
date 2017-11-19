# shell-functools

A collection of functional programming tools for the shell.

## Examples

Assume we have the following directory contents:
``` bash
> tree
.
├── deeply
│   ├── nested
│   │   └── directory
│   │       └── song.mp3
│   └── portrait.jpg
├── doc_symlink.txt -> doc.txt
├── doc.txt
└── image.jpg

3 directories, 5 files
```

Basic usage of `map` and `filter`:
``` bash

> find | filter is_file | map basename
doc.txt
doc_symlink.txt
portrait.jpg
song.mp3
image.jpg
```

Working with two arguments:
```
> find -name '*.jpg' | map duplicate | map -c2 basename | map -c2 prepend "thumb_" | map run convert
Running 'convert' with arguments ['./deeply/portrait.jpg', 'thumb_portrait.jpg']
Running 'convert' with arguments ['./image.jpg', 'thumb_image.jpg']
```


Operations on integers:
``` bash
> seq 1 3 | map add 10
11
12
13
```