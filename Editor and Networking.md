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

