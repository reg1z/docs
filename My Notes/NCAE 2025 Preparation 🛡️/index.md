---
tags:
  - blueteam
  - competitions
  - NCAE
---
# NCAE 2025 Preparation

These are my notes for helping **Blue Teams** prepare for the [NCAE Cyber Games](https://www.ncaecybergames.org). It's currently a work in progress and some notes are incomplete. You can access most relevant notes from here.


> [!warning]- WARNING - Practice Using the Correct Environment!
> **The competition this year is going to be using a MicroTik router, *NOT CentOS* (as it is no longer maintained)**. This was announced on the NCAE Discord.
>
> A new video was posted on the NCAE channel that goes over the new Mini Hack in the same way as the old one. It's very similar to the first Mini Hack and approachable even if you haven't watched the rest of the playlist after the video for the first Mini Hack.
> - [YouTube: NCAE 2025 Mini Hack](https://www.youtube.com/watch?v=gu5A2yCITRs&list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M&index=47)


> [!list]- Relevant Links
> - [YouTube: NCAE Sandbox Playlist](https://www.youtube.com/playlist?list=PLqux0fXsj7x3WYm6ZWuJnGC1rXQZ1018M)
> - [NCAE Website: Competition Rules](https://www.ncaecybergames.org/rules/)
> - [NCAE Discord](https://discord.ncaecybergames.org/)
> - Questions answered by NCAE staff (Discord):
> 	- *"[What is the line where an online service must be disclosed?](https://discord.com/channels/624969095292518401/1339009691044544542)"*

## Notes

- [Linux Maneuvers](Linux%20Maneuvers.md) → Place for brain-dumps and random considerations that don't seem to fit anywhere else. Includes some skills that *might* be important for one to know, depending on their role in a team.
- [Team Strategy](../Unsorted/Team%20Strategy.md) → Map of our strat.
- [NCAE AI Prompt](NCAE%20AI%20Prompt.md) → AI prompt to put at the start of an LLM conversation (chatgpt, claude, etc). Will give context matching what is publicly known about the competition.

### Core Linux Knowledge
Notes I've taken on modern Linux systems during competition prep.

- [systemd](../Unsorted/systemd.md) → systemd is the most popular "init" system in modern Linux environments. An init process is the first process ran after boot (PID 1). It manages and spawns most other processes.
- [systemd-journald](../Unsorted/systemd-journald.md) → logs.
- [systemd-timers](../Unsorted/systemd-timers.md) → a more granular alternative to `cron`. 

### Specific Topics
Niche topics that might be useful to know, depending on one's individual team responsibilities.

- [Microtik RouterOS](Microtik%20RouterOS.md)

### Sandbox Tutorial Video Notes
Notes from NCAE's Sandbox Tutorial Videos. These use the Mini Hack environment to teach players some fundamental concepts you might need for the competition.

- [NCAE Tutorial Playlist Notes](Tutorial%20Video%20Notes/NCAE%20Tutorial%20Playlist%20Notes.md)
	- Or start from the beginning: [01 Intro to the Environment](Tutorial%20Video%20Notes/01%20Intro%20to%20the%20Environment.md)

## Preparing a Game Plan
*Players might find this information useful when developing a strategy.*

### SPICE Configuration
**Copy/paste and automatic guest screen resizing are not available via the default in-browser remote desktop experience NCAE provides.** If you want these features, you should make sure you know how to set them up:

- [SPICE Configuration - Remote Desktop Shared Clipboard and Screen Resizing](SPICE%20Configuration%20-%20Remote%20Desktop%20Shared%20Clipboard%20and%20Screen%20Resizing.md)
- There might also be the possibility of adding copy/paste functionality to their noVNC implementation. Have not figured this out, however.

### System Hardening
A brainstormed list of potential attack vectors and corresponding defenses:

- [System Hardening Ideas](System%20Hardening%20Ideas.md)


---
### Misc.
Most of these are either in-progress, incomplete, or disorganized:

- [Quickdraw Notes](deprecated/Quickdraw%20Notes.md)
- [Other Tools to Consider](deprecated/Other%20Tools%20to%20Consider.md)
- [NCAE misc](Tutorial%20Video%20Notes/NCAE%20misc.md)
- [NCAE-minihack CentOS](Tutorial%20Video%20Notes/NCAE-minihack%20CentOS.md)
