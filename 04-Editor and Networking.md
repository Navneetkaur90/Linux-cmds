## In Command Mode of Vi Editor:
* **Copy a line:** `yy`
* **Paste a line:** `p`
* **Save file:** `ZZ`
* **Delete a letter:** `x`
* **Delete a line:** `dd`
* **Delete 3 lines from current line:** `d3d`
* **Save file:** `:w`
* **Quit:** `:q`
* **Save & quit:** `:wq`
* **Quit without saving:** `:q!`

**Undo/Redo & Navigation:**
* **Undo:** `u`
* **Redo:** `<Ctrl> + r`
* **Find Next (forward direction):** `n`
* **Find Previous (backward direction):** `N`
* **Searching Text:** `/word` (type `/` followed by the word you want to search and press Enter)
* **Switch to last line:** `:`
---

## Networking:

| Task                                                    | Command                                                                 | Example                                  | Notes                                                                   |
| :------------------------------------------------------ | :---------------------------------------------------------------------- | :--------------------------------------- | :---------------------------------------------------------------------- |
| **See and MODIFY interfaces** | `ip link`                                                               |                                          |                                                                         |
| **See IP address assigned to host interface** | `ip addr`                                                               |                                          |                                                                         |
| **Display IP assigned to a specific interface** | `ip addr show <interface_name>`                                       | `ip addr show eth0`                      | Replace `<interface_name>` with the actual interface name (e.g., eth0). |
| **Assign IP address to a host interface** | `ip addr add <IP_address>/<subnet_mask> dev <interface_name>`         | `ip addr add 1.2.3.4/24 eth0`          | Replace `<IP_address>`, `<subnet_mask>`, and `<interface_name>`.       |
| **See routing configuration on a system** | `route`                                                               |                                          |                                                                         |
| **Configure a route (including a gateway)** | `ip route add <destination_ip> via <gateway_IP>`                      | `ip route add 192.168.2.1 via 192.168.1.1` | 
  

**NOTE:**
- If no router is configured, the device won't communicate with other networks.
- you have to configure a gateway in all networks.
- In all hosts update `/etc/resolv.conf` pointing to nameserver
  example: `nameserver 1.2.3.4` (Example)

**Key Concepts:**
* **IP Address:** Numerical label assigned to each device connected to a computer network.
* **Interface:** Network connection point (e.g., eth0, wlan0).
* **Subnet Mask:** Defines the network portion and the host portion of an IP address.
* **Gateway:** A router that allows traffic to flow between different networks.
* **Routing Table:** Contains information about network paths and where to forward data packets.
* **DNS (Domain Name System):** Translates domain names to IP addresses.
* `/etc/hosts`: A local file that maps hostnames to IP addresses.
* `/etc/resolv.conf`: Configuration file for the DNS resolver.

---
## DNS and Network Troubleshooting
**For DNS Troubleshooting:**
* Use `nslookup`
* Use `dig`

**When you don't know the route to a network(For example access any n/w on Internet):**
* Use the **default gateway**.
* .e., Set the router's IP as the default gateway.
* default and 0.0.0.0 ( any IP destination) has same meaning when present in destination field of route table
* However, `0.0.0.0` in the **gateway field** indicates that a gateway is **not needed**. That is when devices are in the **same network**.

| Destination Field | Gateway Field |
| :---------------- | :------------ | 
| default           | router_ip     | 
| 0.0.0.0           | router_ip     |          

* **Command to add default route:**
    ```bash
    # ip route add default via 192.168.2.1
    ```
   
**Important Note :** 
- Changes made through these commands (`ip route add`) are **temporary*
- To persist changes in the routing table:** Add these changes in the **/etc/network/interfaces** file.
- Compare /etc/resolv.conf with its backup /etc/resolv.conf.bak in case of inconsistencies.

## Common Networking Commands
* `ip link`
* `ip link set dev <interface> up/down`
* `ip addr`
* `ip addr add <IP>/<mask> dev <interface>`
* `ip route add`
* `route` or `ip route`

**Tools for Testing Remote Server Connectivity:**

* **Ping:**
    * To test basic reachability.
* **For DNS Troubleshooting:**
    * `nslookup`
    * `dig`
* **Trace the Network Route**
    * `traceroute` This tool outlines the route from the source (the laptop) to the remote server and highlights any problematic hops.
---
## Network Investigation Commands
**Netstat (Legacy - consider using `ss`):**
* Used to print info of:
    * Network connections
    * Routing tables
    * Interface statistics
    * Membership in multicast groups
    * etc.
* **Example:** you want to check if HTTP process is running on port 80, you can check with `netstat -antp | grep :80` (or similar using `ss`).
* **`netstat`**: List listening ports (Modern alternative is `ss`).
    * `netstat -tuln`: List listening TCP and UDP ports numerically.
    * `-l`: List listening ports.
    * `-n` Display IP addresses and ports numerically..
    * `lsof -i`: List open network files.

* **`curl localhost:<port>`**: Test HTTP service connectivity.
* **`nc -zv <host> <port>`**: Test TCP connection.
---
## File Permissions (chmod)
* **`chmod 600 <file/dir>`**: Gives the owner full read and write access, but no other user can access it.
    * **R**ead = 4
    * **W**rite = 2
    * e**X**ecute = 1
* **Best Practice (for SSH keys):**
    * `chmod 600 ~/.ssh/id_rsa`: Secure file permissions for private SSH key.
    * Review `~/.ssh/authorized_keys` file on the remote server.

## Understanding File Permission Notation
* **`chmod <owner><group><other> <file/dir>`**
    * Owner, Group, Other represent the permissions for each category.
    * Permissions are represented numerically (sum of R, W, X) or symbolically (rwx).
* **Example:**
    * `6` (owner) = `4` (read) + `2` (write) + `0` (execute) = `rw-`
    * `0` (group) = `0` (read) + `0` (write) + `0` (execute) = `---`
    * `0` (other) = `0` (read) + `0` (write) + `0` (execute) = `---`
    * So, `chmod 600` results in `rw-------` permissions.

## `stat` Command
* `stat <file/dir>`: You can do `stat` on a file or directory.
* It lists a lot of information about the file/directory.

## Verbose Output (`-v`)
* `-v` (verbose): Will print more messages on the output screen.

## Process Management (`ps`)
* `ps`: Show current running processes.
* `ps -ef | grep <process_name>`: To find specific processes.
## Linux Operators: 
* **Operator `&`:** To run process commands in the background (will only run if the command was successfully started).
* **Operator `&&`:** To make a list of commands to run sequentially.CMD2 will only run if CMD1 ran successfully.
