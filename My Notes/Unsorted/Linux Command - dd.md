---
tags: 
date: 2025-03-23
---
# Linux Command - `dd`

Flashing a thumbdrive (with status indicators)
- run `lsblk` to find the correct path to your target drive

Then:
```bash
sudo dd if=/path/to/image.iso of=/dev/sdX bs=4M status=progress conv=fsync
```

- `conv=fsync` ensures that all data is written to the drive (sync'd to the disk) before the process completes.