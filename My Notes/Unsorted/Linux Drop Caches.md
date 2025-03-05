---
tags:
  - linux
  - memory
date: 2025-03-03
---
# Linux Drop Caches
Utilizing the drop caches is a great way to free up memory in a pinch.

> [!quote]+ What are Linux **Drop Caches**?
> The `/proc/sys/vm/drop_caches` file in Linux is used to free up memory by dropping various caches. Writing a number to this file triggers different actions:
> 
> - Writing `1` to the file frees page cache.
> - Writing `2` to the file frees dentries and inodes.
> - Writing `3` to the file frees page cache, dentries, and inodes.
> 
> This operation is **non-destructive** and will only free things that are completely unused. Dirty objects will continue to be in use until written out to disk and are not freeable. Running `sync` first to flush them out to disk can help free more memory.

> [!question]+ What are the page, dentry, and inode caches?
> - **Page Cache** - Stores **file contents** that have been read from or written to disk, allowing subsequent accesses to be served from memory instead of the slower disk.
> - **Dentry Cache (Directory Entry Cache)** - Caches the results of **path-to-inode** lookups, making it faster to access files and directories by avoiding repeated parsing of directory paths.
> - **Inode Cache** - Stores **inode structures** (metadata about files and directories) to speed up file access by avoiding repeated disk reads.

**1 - Page Cache**
```bash
sudo sync && echo 1 | sudo tee /proc/sys/vm/drop_caches
```

**2 - Dentries and inodes**
```bash
sudo sync && echo 2 | sudo tee /proc/sys/vm/drop_caches
```

**3 - Page Cache, dentries, and inodes**
```bash
sudo sync && echo 3 | sudo tee /proc/sys/vm/drop_caches
```


