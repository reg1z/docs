---
tags:
  - linux
  - systemd
date: 2025-03-07
---
# systemd-timers
A modern alternative to `cron`.

**Pair:**
`.timer` ←→ `.service`

*🌠 Each timer unit is typically paired with a matching service unit that it activates. For example, `backup.timer` would trigger `backup.service`.*

> [!question]+ Why Use Timer Units Instead of Cron?
> 
> Timer units offer several advantages over traditional cron jobs:
> 
> 1. **Logging integration** - Output and errors are automatically captured in the systemd journal, making troubleshooting much easier.
> 2. **Dependencies** - Timers can depend on other services or conditions, ensuring tasks run in the proper environment.
> 3. **Resource control** - You can apply systemd's resource management (CPU, memory limits, etc.) to scheduled tasks.
> 4. **Handling missed executions** - Timers can detect and run missed executions, which is useful for laptops that aren't always on.
> 5. **Randomized delays** - You can add randomized delays to prevent many timers from triggering simultaneously.
> 6. **More precise scheduling** - Beyond cron's limited expressions, timers allow complex calendar specifications.
> 

## Types of Timers
systemd supports two fundamental types of timers:

1. **Realtime timers (a.k.a. wallclock timers)** → These are based on calendar events, similar to cron jobs. They use the `OnCalendar=` setting and trigger at specific dates and times.
2. **Monotonic timers** → These are based on time intervals relative to specific events, such as system boot or when the timer was last triggered. They use settings like `OnBootSec=`, `OnUnitActiveSec=`, etc.

## Real-World Use Cases
Timer units are versatile and can handle many types of scheduled tasks:

1. **System maintenance** - Cleaning temporary files, updating databases
2. **Backups** - Regular data backups at specified times
3. **Reports** - Generating periodic reports or analytics
4. **Updates** - Checking for and applying software updates
5. **Monitoring** - Regular health checks of services
6. **Batch processing** - Processing data at off-peak hours

## Calendar Event Expressions
The `OnCalendar=` setting supports a rich syntax for specifying when a timer should trigger. Here are some examples:

- `OnCalendar=Mon,Tue *-*-* 17:00:00` - Every Monday and Tuesday at 5 PM
- `OnCalendar=*-*-* 4:30` - Every day at 4:30 AM
- `OnCalendar=*-*-1,15 01:00:00` - 1st and 15th of each month at 1 AM
- `OnCalendar=Mon..Fri *-*-* 9:00:00` - Weekdays at 9 AM
- `OnCalendar=*:0/15` - Every 15 minutes (at 0, 15, 30, 45 minutes past the hour)

The syntax is quite flexible, allowing specification down to the microsecond if needed.

## Key Timer Settings
Beyond the basic examples, here are important settings you can use in timer units:

### Monotonic Timer Settings

- `OnBootSec=` - Time after the system boot
- `OnStartupSec=` - Time after systemd was started
- `OnUnitActiveSec=` - Time after the timer unit was activated
- `OnUnitInactiveSec=` - Time after the timer unit became inactive

### Realtime Timer Settings

- `OnCalendar=` - Realtime (wall clock) calendar event

### Other Important Settings

- `AccuracySec=` - Accuracy of the timer (default is 1 minute)
- `RandomizedDelaySec=` - Random delay added to the timer
- `Persistent=` - Whether to trigger immediately if a timer was missed (e.g., system was off)
- `WakeSystem=` - Whether to wake the system from suspend to run the timer
- `RemainAfterElapse=` - Whether the timer stays loaded after it has elapsed

## Security of systemd Timers
systemd uses the more sophisticated polkit authorization framework for many operations. This allows for more nuanced permission handling, where different actions can have different authorization requirements. For example, a system administrator might grant a user permission to view but not modify timers.

Additionally, systemd timer files typically live in `/etc/systemd/system/` which usually requires root privileges to modify. However, systemd also supports user timers that run in the user's context without requiring root privileges.


> [!tip]+ systemd service security directives
> systemd timers benefit from the full range of security directives available to systemd services. These include:
> 
> - **Namespacing controls**: You can isolate services in their own namespace hierarchies
> - **Resource limits**: Set hard boundaries on CPU, memory, I/O usage, etc.
> - **Capability controls**: Precisely define what system capabilities the service has access to
> - **Sandboxing options**: Restrict file system access, network access, etc.
> 
> For example, you could create a timer-activated service that runs with:
> 
> ```ini
> [Service]
> # Restrict filesystem access
> ProtectSystem=strict
> ProtectHome=true
> PrivateTmp=true
> 
> # Network restrictions
> PrivateNetwork=true
> 
> # Additional protections
> NoNewPrivileges=true
> CapabilityBoundingSet=
> ```


## Best Practices for systemd Timers 🌠

1. **Name timer and service units consistently** - If your timer is `backup.timer`, your service should be `backup.service`.
2. **Use descriptive unit descriptions** - This makes `systemctl list-timers` output more informative.
3. **Set the `Persistent=true` option** - For important tasks that shouldn't be missed if the system is off at the scheduled time.
4. **Use `RandomizedDelaySec=` for non-critical tasks** - This prevents resource contention when many timers would otherwise trigger simultaneously.
5. **Keep timer definitions simple** - If you need complex logic, put it in the service's ExecStart script, not in the timer itself.
6. **For critical timers, consider monitoring** - Create a monitoring check that ensures your timer's associated service ran successfully.
7. **Think about resource limitations** - Add CPU, memory, and I/O constraints to service units for scheduled tasks to prevent them from overwhelming the system.


## When to Choose Which Option (Security Perspective)
From a security standpoint:

**Choose cron when:**

- You need a simple, battle-tested solution with minimal dependencies
- You're working in an environment where systemd isn't available
- Your security requirements are relatively basic

**Choose systemd timers when:**

- You need fine-grained security controls and isolation
- Comprehensive logging and auditing are important
- You want to apply resource limits to prevent denial-of-service scenarios
- You're already using other systemd components and want consistent management