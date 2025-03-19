---
tags:
  - windows
  - linux
  - bash
  - powershell
date: 2025-03-19
---
# From Bash to PowerShell
*Mapping `bash` commands to their `pwsh` cmdlet equivalents.*

| `bash` command | `pwsh` cmdlet                                                                                         | `pwsh` aliases                            |
| -------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------- |
| `grep`         | **Select-String**<br>`Select-String -Pattern "text" -Path "file"`                                     | `sls`                                     |
| `ls`           | **Get-ChildItem**<br>`Get-ChildItem -Path "directory"`                                                | `gci`, `dir`, `ls`                        |
| `cd`           | **Set-Location**<br>`Set-Location -Path "directory"`                                                  | `sl`, `cd`, `chdir`                       |
| `pwd`          | **Get-Location**<br>`Get-Location`                                                                    | `gl`, `pwd`                               |
| `cp`           | **Copy-Item**<br>`Copy-Item -Path "source" -Destination "dest"`                                       | `copy`, `cp`, `cpi`                       |
| `mv`           | **Move-Item**<br>`Move-Item -Path "source" -Destination "dest"`                                       | `move`, `mv`, `mi`                        |
| `rm`           | **Remove-Item**<br>`Remove-Item -Path "file"`                                                         | `del`, `erase`, `rd`, `ri`, `rm`, `rmdir` |
| `mkdir`        | **New-Item**<br>`New-Item -Path "dir" -ItemType Directory`                                            | `ni`, `md`                                |
| `cat`          | **Get-Content**<br>`Get-Content -Path "file"`                                                         | `gc`, `type`, `cat`                       |
| `echo`         | **Write-Output**<br>`Write-Output "text"`                                                             | `echo`, `write`                           |
| `find`         | **Get-ChildItem** (with recursion)<br>`Get-ChildItem -Path "dir" -Recurse`                            | `gci -r`                                  |
| `head`         | **Get-Content** (with limit)<br>`Get-Content -Path "file" -TotalCount 10`                             | `gc -head`                                |
| `tail`         | **Get-Content** (with tail)<br>`Get-Content -Path "file" -Tail 10`                                    | `gc -tail`                                |
| `touch`        | **New-Item**<br>`New-Item -Path "file" -ItemType File`                                                | `ni`                                      |
| `wc`           | **Measure-Object**<br>`Get-Content "file" \| Measure-Object -Word/-Line/-Character`                   | `measure`                                 |
| `chmod`        | **Set-Acl** or **icacls**<br>`Set-Acl -Path "file" -AclObject $acl`                                   | None                                      |
| `chown`        | **Set-Acl**<br>`Set-Acl -Path "file" -AclObject $acl`                                                 | None                                      |
| `ps`           | **Get-Process**<br>`Get-Process`                                                                      | `gps`, `ps`                               |
| `kill`         | **Stop-Process**<br>`Stop-Process -Id pid` or `-Name name`                                            | `spps`, `kill`                            |
| `man`          | **Get-Help**<br>`Get-Help cmdlet-name -Full`                                                          | `help`                                    |
| `history`      | **Get-History**<br>`Get-History`                                                                      | `h`, `history`                            |
| `df`           | **Get-PSDrive**<br>`Get-PSDrive`                                                                      | `gdr`                                     |
| `du`           | **Measure-Object** on folder size<br>`Get-ChildItem -Recurse \| Measure-Object -Property Length -Sum` | None                                      |
| `wget`         | **Invoke-WebRequest**<br>`Invoke-WebRequest -Uri "url" -OutFile "file"`                               | `iwr`, `curl`, `wget`                     |
| `sort`         | **Sort-Object**<br>`command \| Sort-Object -Property Property`                                        | `sort`                                    |
| `uniq`         | **Get-Unique** or **Select-Object -Unique**<br>`command \| Sort-Object \| Get-Unique`                 | `gu`                                      |
| `which`        | **Get-Command**<br>`Get-Command commandname`                                                          | `gcm`                                     |
| `uniq`         | **Get-Unique** or **Select-Object -Unique**<br>`command`                                              | `gu`                                      |
| `count`        | **Measure-Command** or **Measure-Object**<br>`command`                                                | `measure`                                 |
