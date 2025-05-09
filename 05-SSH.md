## SSH (Secure Shell)
* **Purpose:** To access a remote SSH server securely over encrypted connection.
* **Basic Usage:** Remote login and secure file transfer
* **Basic Command:**
  ```bash
  ssh <hostname or IP>
  ```
  * **Example:** `ssh user@hostname` or `ssh user@192.168.1.100`

* **If the port is not the default (22), specify it with -p::**
  ```bash
  ssh -p <port_number> <username>@<hostname or IP>
  ```
  * **Example:** `ssh -p 2222 user@remote.example.com`
#### NOTE: To login remote server, need either user/password combination or sshkeypair
---
### Generating SSH Key Pairs
* **Command:**
  ```bash
  ssh-keygen 
  ```
* **Options:**
  * `-t <type>`: Specifies the key type (e.g., `rsa`, `ed25519`). The default is `rsa`.
    * Example: `ssh-keygen -t rsa`
    * Example: `ssh-keygen -t ed25519`
  * `-b <bits>`: Specifies the number of bits in the key (for RSA). The default is 2048 bits.
    * Example: `ssh-keygen -t rsa -b 4096`

* **Output Files (Default for RSA):**
  * **Private Key:** `~/.ssh/id_rsa`
  * **Public Key:** `~/.ssh/id_rsa.pub`

* **Path:** The default location for SSH keys is the `.ssh` directory within the user's home directory (`~/.ssh`).
---
### Adding Public Key to Remote Server for Passwordless Login (Recommended)
 When a client's public key is added to the `~/.ssh/authorized_keys` file on a remote server, the server will grant access to the client possessing the corresponding private key without requiring a password.

**How to Copy Public Key to Remote Server:**
Run this cmd on client:
```bash
ssh-copy-id user@hostname
```
 * You will be asked for the password of the `user` on the remote server (i.e user account, created on remote server).
 * `ssh-copy-id` will then append your public key (typically from `~/.ssh/id_rsa.pub` to the `~/.ssh/authorized_keys` file on the remote server.

**Verification (On the Remote Server):**
You can manually check the `authorized_keys` file on the remote server to ensure your public key has been added:
```bash
cat /home/bob/.ssh/authorized_keys
```
---
### SCP (Secure Copy Protocol):
**Copy files to Remote server:**
```bash
scp /path/to/local/file user@remote:path/to/destination
```
**Example:**
```bash
scp myfile.txt user@192.168.1.100:/home/user/
```
**Copy files From Remote server:**
```bash
scp user@192.168.1.100:/home/user/myfile.txt ./
``` 
**SCP Options:**
* `-r`: To copy directories instead of files (recursive).
* `-p`: To preserve the ownership and permissions of the source files.

---
## File Permissions (chmod)
* **`chmod 600 <file/dir>`**: Gives the owner full read and write access no execute, but no other user can access it.
    * **R**ead = 4
    * **W**rite = 2
    * e**X**ecute = 1
* **Best Practice (for SSH keys):**
    * `chmod 600 ~/.ssh/id_rsa`: Secure file permissions for private SSH key.
    * Review `~/.ssh/authorized_keys` file on the remote server.