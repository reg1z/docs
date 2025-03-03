# Linux Drop Caches

> [!quote]+ Brave Leo - What are Linux **Drop Caches**?
> The `/proc/sys/vm/drop_caches` file in Linux is used to free up memory by dropping various caches. Writing a number to this file triggers different actions:
> 
> - Writing `1` to the file frees page cache.
> - Writing `2` to the file frees dentries and inodes.
> - Writing `3` to the file frees page cache, dentries, and inodes.
> 
> This operation is **non-destructive** and will only free things that are completely unused. Dirty objects will continue to be in use until written out to disk and are not freeable. Running `sync` first to flush them out to disk can help free more memory.

