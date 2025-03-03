# systemd
- Why learn about it?
	- It's the predominant init system and service manager used on most modern Linux systems.
- potential topics
	- `systemctl`
	- Most commonly encountered systemd services
	- PRACTICAL USE. Actually using the tools instead of conceptual knowledge delivery.
		- What would be a good way to set up a relevant scenario? Set up a VM/tryhackme room for download?
- other factors

## History
- Sources:
	- [The Tragedy of Systemd - Benno Rice (YouTube)](https://www.youtube.com/watch?v=o_AIw9bGogo)
- systemd was controversial when it was first proposed. Origin story of Lennart Poettering and previous init systems...
- systemd's *alternate* approach was controversial, but enabled/encouraged new ways of doing things that didn't always have to follow a standard model. It wasn't boxed-in by existing standards.
	- this created some rifts in the UNIX community. many projects use different init systems (bsd, etc)

# UWSM

> [!quote]+ [Universal Wayland Session Manager](https://github.com/Vladimir-csp/uwsm)
> Wraps standalone Wayland compositors into a set of Systemd units on the fly. This provides robust session management including environment, XDG autostart support, bi-directional binding with login session, and clean shutdown.
> 
> For compositors this is an opportunity to offload Systemd integration and session/XDG autostart management in Systemd-managed environments.


- A text channel in the "Contributors" category for suggestions.
- A "Process / Workflow"  forum where each member of the team could post an overview/notes/tips on their own personal workflow. Software, tools, and other things they use (Obsidian, da vinci, feedly, etc.). If we all had that information at a glance it could be really useful if someone is considering a particular tool or trying to find something that works. It might also help converge our workflows somewhat so we know how to be compatible with one another.