---
tags:
  - cloud
  - storage
  - devops
date: 2025-03-20
---
# Rclone

> [!quote]+ What is Rclone? [https://rclone.org](https://rclone.org/)
> *Rclone is a command-line program to manage files on cloud storage. It is a feature-rich alternative to cloud vendors' web storage interfaces. Over 70 cloud storage products support rclone including S3 object stores, business & consumer file storage services, as well as standard transfer protocols.*
> 
> *Rclone has powerful cloud equivalents to the unix commands rsync, cp, mv, mount, ls, ncdu, tree, rm, and cat. Rclone's familiar syntax includes shell pipeline support, and --dry-run protection. It is used at the command line, in scripts or via its API.*

> [!quote]+ Features
> **Rclone helps you:**
> 
> - Backup (and encrypt) files to cloud storage
> - Restore (and decrypt) files from cloud storage
> - Mirror cloud data to other cloud services or locally
> - Migrate data to the cloud, or between cloud storage vendors
> - Mount multiple, encrypted, cached or diverse cloud storage as a disk
> - Analyse and account for data held on cloud storage using [lsf](https://rclone.org/commands/rclone_lsf/), [ljson](https://rclone.org/commands/rclone_lsjson/), [size](https://rclone.org/commands/rclone_size/), [ncdu](https://rclone.org/commands/rclone_ncdu/)
> - [Union](https://rclone.org/union/) file systems together to present multiple local and/or cloud file systems as one
> 
> **[Rclone Features](https://rclone.org/#features)**
> 
> - Transfers
>     - MD5, SHA1 hashes are checked at all times for file integrity
>     - Timestamps are preserved on files
>     - Operations can be restarted at any time
>     - Can be to and from network, e.g. two different cloud providers
>     - Can use multi-threaded downloads to local disk
> - [Copy](https://rclone.org/commands/rclone_copy/) new or changed files to cloud storage
> - [Sync](https://rclone.org/commands/rclone_sync/) (one way) to make a directory identical
> - [Bisync](https://rclone.org/bisync/) (two way) to keep two directories in sync bidirectionally
> - [Move](https://rclone.org/commands/rclone_move/) files to cloud storage deleting the local after verification
> - [Check](https://rclone.org/commands/rclone_check/) hashes and for missing/extra files
> - [Mount](https://rclone.org/commands/rclone_mount/) your cloud storage as a network disk
> - [Serve](https://rclone.org/commands/rclone_serve/) local or remote files over [HTTP](https://rclone.org/commands/rclone_serve_http/)/[WebDav](https://rclone.org/commands/rclone_serve_webdav/)/[FTP](https://rclone.org/commands/rclone_serve_ftp/)/[SFTP](https://rclone.org/commands/rclone_serve_sftp/)/[DLNA](https://rclone.org/commands/rclone_serve_dlna/)
> - Experimental [Web based GUI](https://rclone.org/gui/)

