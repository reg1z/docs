---
tags:
  - terminology
date: 2025-04-05
---
# UUID

**UUID** stands for **Universally Unique Identifier**. It's a 128-bit value (usually shown as a 36-character string) used to uniquely identify things with **no centralized authority** required.

Typical Format:

```bash
550e8400-e29b-41d4-a716-446655440000
```


Types of UUIDs (versions). The most common UUID versions are:

| Version | Based on                     | Notes                                    |
| ------- | ---------------------------- | ---------------------------------------- |
| 1       | Timestamp + MAC address      | Leaks time & hardware info, but sortable |
| 3       | MD5 hash of namespace+name   | Deterministic                            |
| 4       | Random                       | Most common, easy, secure                |
| 5<br>   | SHA-1 hash of namespace+name | Deterministic                            |

