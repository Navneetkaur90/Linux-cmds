## Service Management with systemd:
- systemd is System and Service manager for Linux.
- To run a script in the background, we have to define it as a service.
- Services are background processes often called daemons. 

#### Create a service unit file under `/etc/systemd/system/example-service.service`. Service Events (Start, Stop, Failure) are automatically logged in `systemd`.
---

### Tools for Managing `systemd` Services
1. Systemctl
2. Journalctl

**`systemctl`**: The primary command-line tool for controlling and managing `systemd` services and the system state.

* **Uses:**
```
    1.  `start <service_name>`: Start a service. </n>
    2.  `stop <service_name>`: Stop a service.
    3.  `restart <service_name>`: Restart a service.
    4.  `reload <service_name>`: Reload the configuration of a service without interrupting it.
    5.  `enable <service_name>`: Enable a service to start automatically during the boot process.
    6.  `disable <service_name>`: Disable a service from starting automatically during boot.
    7.  `status <service_name>`: View the current status of a service (active, inactive, running, failed, etc.).
    8.  `get-default  or set-default` : View and set targets.
    9.  `list-units --type=service --all`:  List all available service unit files (active and inactive).
    10. `list-unit-files --type=service`: shows only active units.
```

 * **Reloading system configuration:**
    - systemctl daemon-reload (Run this cmd after making any changes to service Unit file).
    - systemctl edit <service-name> --full (If edited this way, no need to run daemon reload command). 
      You can use the --full option to edit the entire original unit file directly, but this is generally discouraged.

**`Journalctl`(System Log Viewer)**: 
    * Queries journal (systemd logging system)
    * Used for troubleshooting issues with `systemd` units (services, etc.).
    * For troubleshooting service failures: Use `journalctl` to view detailed logs of the failed service.
    * Command to view logs for a specific service: `journalctl -u <service_name>`

* **Common `journalctl` Options:**
    * **`journalctl`**: Prints all logs from the current boot.
    * **`journalctl -b`**: Prints logs from the current boot.
    * **`journalctl --since "yesterday"` / `--until "now"` / `--since "2023-10-26 10:00:00"`**: Filter logs by time.
    * **`journalctl -u <unit_name>`**: Prints logs for a specific `systemd` unit (e.g., `journalctl -u docker.service`).

---
### Syslog:

- Syslog is a **standard logging protocol** that allows various system components (kernel, applications, services) to send log messages to a central logging daemon. 
- This daemon then processes and stores these messages, typically in **log files** (like `/var/log/syslog` or `/var/log/messages`).
- syslogd: A specific, older daemon that implements the syslog protocol.
- rsyslogd: `rsyslogd` is a updated daemon that manages logs in modern Linux systems
- All logs (using syslog service collection): tail -f /var/log/syslog

**Key points:**
* **Centralized Logging:** Collects logs from everywhere.
* **Standard Protocol:** Defined way for systems to send logs.
* **Log Files:** Where the messages are usually stored.
* **Daemon (`syslogd` or `rsyslogd`):** The background program that handles logs.
* Files maintained at `/etc/rsyslog.d`.

---
### Locate the Nginx Configuration Files
The primary Nginx configuration file is typically found in:
- `/etc/nginx/nginx.conf`

Additional configuration files might be located in:
- `/etc/nginx/sites-available/`
- `/etc/nginx/sites-enabled/`

Use the following command to locate all Nginx configuration files:
```bash
grep -R "listen" /etc/nginx/
```
