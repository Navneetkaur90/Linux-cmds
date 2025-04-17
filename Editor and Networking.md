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
* **To see and MODIFY interfaces:** `ip link`
* **To see IP address assigned to host interface** `ip addr`
* **Display IP assigned to interface:** `ip addr show <interface_name>`
* **To assign IP address to host interface:** `ip addr add <IP_address>/<subnet_mask> dev <interface_name>`
    * Example: `ip addr add 1.2.3.4/24 eth0`
    * **Note:** If no router configured, device will not communicate with other networks.
* **To see routing configuration on a system:** `route`
* **To configure a gateway (add route in table for gateway):** `ip route add <destination_ip> via <gateway_IP>`
    * Example: `ip route add 192.168.2.1 via 192.168.1.1`

**NOTE: you have to configure a gateway in all networks:**

**In all hosts update `/etc/resolv.conf` pointing to nameserver**
`nameserver 1.2.3.4` (Example)

**Key Concepts:**
* **IP Address:** Numerical label assigned to each device connected to a computer network.
* **Interface:** Network connection point (e.g., eth0, wlan0).
* **Subnet Mask:** Defines the network portion and the host portion of an IP address.
* **Gateway:** A router that allows traffic to flow between different networks.
* **Routing Table:** Contains information about network paths and where to forward data packets.
* **DNS (Domain Name System):** Translates domain names to IP addresses.
* `/etc/hosts`: A local file that maps hostnames to IP addresses.
* `/etc/resolv.conf`: Configuration file for the DNS resolver.

