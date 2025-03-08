---
tags:
  - linux
  - systemd
date: 2025-02-25
---
# systemd
*Systemd is the most popular "init" system in modern Linux environments. An init process is the first process ran after boot (PID 1). It manages and spawns most other processes and services}

⭐ After changes to configurations, remember to run:

```bash
# makes systemd aware of your config changes
systemctl daemon-reload 

# restarts particular service, integrating your changes
systemctl restart <target-service.service>
```

> [!info]+ init system responsibilities
> - System initialization
> - Starting/stopping services
> - Handling dependencies between services
> - Managing runlevels or target states
> - Monitoring services and restarting failed ones

> [!list]+ Related Notes
> - [systemd-journald](systemd-journald.md)
> - [systemd-timers](My%20Notes/Unsorted/systemd-timers.md)
> - [systemd_studygroup](../Works-in-Progress/systemd_studygroup.md)

## Basic Concepts

- Uses **Unit Files**, not shell scripts (as was the case with many traditional init systems).
- Handles **Parallel Startup** for faster boot times.
- systemd can start services when they're *needed*, rather than at boot time. For example, a service can be activated when:
	- A specific network socket receives data
	- A USB device is plugged in
	- A file in a specific location changes
	- A timer triggers
- systemd can create and restore **system state snapshots**.

## Units
> ==**Unit**== → A resource that the system knows how to manage.

**Types of Units**
- `.service` → **Service Units**. Manages **daemons** and **processes**.
- `.socket` → **Socket Units**. Manages **network sockets**.
- `.target` → **Target Units**. Groups units together for **synchronization points**.
- `.mount` → **Mount Units**. Controls the **mounting of filesystems**.
- `.device` → **Device Units**. Manages **devices**.
- `.timer` → **Timer Units**. *Triggers* **actions** based on **timers**.
- `.slice` → **Slice Units**. Groups and manages processes for **resource control**.
- `.scope` → **Scope Units**. Manages **externally created processes**.

systemd organizes these units in a *dependency tree*, creating a clear structure for system initialization and operation.

## Security of systemd

### Dynamic Users
systemd's `DynamicUser=` feature can run services as dynamically allocated users without requiring permanent system accounts.

### Credential Management
systemd provides more sophisticated options for credential management:

- **Environment file loading**: Services can load environment variables from secured files
- **RuntimeDirectory**: Services can have private runtime directories with restricted permissions
- **Dynamic Users**: Services can run as dynamically allocated users for isolation
- **LoadCredential/SetCredential**: Newer versions of systemd (≥246) allow passing credentials to services without exposing them in configuration files

## Creating a systemd service
You have to create a unit file either:
- `/etc/systemd/system/` → Used for administrator-defined services.
- `/usr/lib/systemd/system` → Intended for services created by the distro's package manager. e.g. machine-specific configurations for a service.
	- It's best to not customize files in this location as they are managed by the package manager and will likely be overwritten during updates.

```ini
[Unit]
Description=My Python Web Application
After=network.target

[Service]
User=webuser
WorkingDirectory=/opt/myapp
ExecStart=/usr/bin/python3 /opt/myapp/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

You could then start the service like so:
```bash
# Reload systemd to recognize the new service
systemctl daemon-reload

# Enable and start the service
systemctl enable myapp.service
systemctl start myapp.service
```

### Overrides
One of systemd's powerful features is its layered configuration approach. If a unit file exists in both locations, the one in `/etc/systemd/system/` takes precedence. This allows for elegant customization without modifying vendor files:

1. The original service definition remains intact in `/usr/lib/systemd/system/`
2. Your customizations go in `/etc/systemd/system/`
3. System updates can replace the vendor files without affecting your customizations

### Best Practices

1. **Never modify files in `/usr/lib/systemd/system/`** directly - they belong to the package manager and may be overwritten during updates
2. For small changes to existing services, use drop-in files in `/etc/systemd/system/[service-name].d/`
3. For completely custom services, place the full unit file in `/etc/systemd/system/`
4. After making changes, remember to run `systemctl daemon-reload` to apply them
5. Use version control or configuration management tools to track your customizations in `/etc/`



