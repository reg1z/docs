---
tags:
  - linux
  - monitoring
  - logging
date: 2025-03-07
---
# rsyslog

## File Locations

### Configs
⭐ [rsyslog configuration documentation](https://www.rsyslog.com/doc/configuration/index.html)

- `/etc/rsyslog.conf` → Main config file
- `/etc/rsyslog.d/` → Dir. containing additional config files with the `.conf` extension

### State

- `/var/spool/rsyslog/imjournal.state` → rsyslog's **Journal Cursor**

### Log Files

- `/var/log/syslog` → normal log folder

#### Common Log Files

```bash

/var/log/syslog               # General system logs
/var/log/auth.log             # Authentication (ssh, sudo) logs
/var/log/kern.log             # Kernel messages
/var/log/ufw.log              # UFW firewall logs (if enabled)
/var/log/daemon.log           # Daemon logs
/var/log/messages             # General system messages (sometimes not present on Ubuntu)
/var/log/rsyslog.log          # Logs related to rsyslog's own operation

```

## Modules
Modules are plugin-like components that extend the functionality of the rsyslog system. They are loaded in the rsyslog configuration with directives like `module(load="imtcp")` and then configured with specific parameters.


> [!abstract]- All rsyslog modules
> ### Input Modules (im)
> 
> - **imfile** → Monitors and ingests data from text files.
> - **imjournal** → Reads logs from the systemd journal.
> - **imklog** → Reads kernel messages through /proc/kmsg.
> - **immark** → Generates periodic timestamp mark messages.
> - **impstats** → Provides periodic statistics about rsyslog's internal counters.
> - **imptcp** → Receives messages via plain TCP (persistent TCP connection).
> - **imrelp** → Receives syslog messages via the RELP protocol.
> - **imtcp** → Receives messages via plain TCP.
> - **imudp** → Receives syslog messages via UDP.
> - **imuxsock** → Provides local system logging (Unix sockets).
> 
> ### Output Modules (om)
> 
> - **omfile** → Writes log messages to files on the local filesystem.
> - **omfwd** → Forwards messages to remote hosts using UDP/TCP.
> - **omhiredis** → Outputs to Redis database.
> - **omjournal** → Forwards messages to the systemd journal.
> - **ommail** → Sends log data via email.
> - **omprog** → Forwards messages to an external program.
> - **omrelp** → Forwards messages via the RELP protocol.
> - **omruleset** → Calls a different ruleset for processing.
> - **omstdout** → Sends messages to standard output (stdout).
> - **omtesting** → Testing and debugging output module.
> 
> ### Parser Modules (pm)
> 
> - **pmciscoios** → Parses Cisco IOS message format.
> - **pmrfc3164** → Parses the traditional/legacy syslog format.
> - **pmrfc5424** → Parses structured syslog format (RFC5424).
> 
> ### Message Modification Modules (mm)
> 
> - **mmanon** → Anonymizes IP addresses in log messages.
> - **mmcount** → Counts occurrences of log messages based on given criteria.
> - **mmfields** → Extracts fields from structured log data.
> - **mmjsonparse** → Parses JSON formatted log messages.
> - **mmnormalize** → Normalizes log messages using liblognorm rules.
> - **mmrm1stspace** → Removes leading space from message content.
> - **mmsequence** → Adds a sequence number to log messages.
> - **mmutf8fix** → Fixes invalid UTF-8 sequences in log messages.
> 
> ### String Generator Modules (sm)
> 
> - **smfile** → Reads content from files to be used in templates.
> - **smfstream** → Accesses data from a file as a stream.
> - **smtradfile** → Traditional file content reader (legacy version).
> 
> ### Library Modules
> 
> - **lmnet** → Network-related helper functions.
> - **lmregexp** → Regular expression matching facilities.
> - **lmtcpclt** → TCP client functionality.
> - **lmtcpsrv** → TCP server functionality.
> - **lmzlibw** → Compression support using zlib.
> 
> ### Function Modules
> 
> - **fmhash** → Provides hash functions for message content.
> - **fmhttp** → HTTP-related functions for templates.


## Examples

### Recieving
```bash
module(load="imudp")
input(type="imudp" port="514")

module(load="imtcp")
input(type="imtcp" port="514")
```

### Forwarding

UDP
```bash
*.* @192.168.56.10:514        # Forward ALL logs via UDP
```

TCP
```bash
*.* @@192.168.56.10:514       # Forward forward ALL logs via TCP
```