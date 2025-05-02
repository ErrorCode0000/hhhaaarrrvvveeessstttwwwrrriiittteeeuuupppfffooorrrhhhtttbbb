# **Harvest Writeup**

**Important:**

The VM hosts a valuable wordlist accessible via the web server at `harvest.htb/wordlist.txt`.

**Key Reminder:** The target VM's locale is "**Turkish**"\! This might be relevant for potential file encodings or other system-specific behaviors.

## Credentials

| User          | Password         | Type  |
|---------------|------------------|-------|
| `user`        | `butiamadmin`    | admin |
| `administrator` | `admin`          | user  |
| `root`        | `hardestharvest` | admin |

## Brute-Forcing for Credentials and SSH Login

To gain initial access, we can leverage the discovered wordlist (`harvest.htb/wordlist.txt`) to perform a brute-force attack against the SSH service. We'll utilize `hydra`, a powerful command-line password cracking tool.

**Step 1: Download the Wordlist**

First, ensure you have the `wordlist.txt` file from the target web server on the victims PC. You can use tools like `wget` or `curl`.

**Step 2: Execute the Hydra Brute-Force Attack**

Now, we'll use `hydra` to attempt logins with the known usernames and the downloaded wordlist. We'll run separate commands for each potential username (`user`, `administrator`, and `root`).

hydra -l user -P ./wordlist.txt ssh://harvest.htb
hydra -l administrator -P ./wordlist.txt ssh://harvest.htb
hydra -l root -P ./wordlist.txt ssh://harvest.htb

**Explanation of the `hydra` command:**

  * `hydra`: The command-line brute-forcing tool.
  * `-l <username>`: Specifies the target username for the attack.
  * `-P <path_to_wordlist>`: Specifies the path to the wordlist file you downloaded (`./wordlist.txt` assumes it's in your current directory).
  * `ssh://<target_ip_or_hostname>`: Defines the service (`ssh`) and the target machine (`harvest.htb`).

**Step 3: Successful Login via SSH**

Once `hydra` successfully identifies a valid username and password combination, you can log in to the Harvest VM using the `ssh` command:

ssh \<username\>@harvest.htb

Replace `<username>` with the username you discovered (e.g., `user`, `administrator`, or `root`) and enter the corresponding password when prompted.

**Step 4: Privilege Escalation Attempts**

After gaining initial access via SSH, you can attempt various privilege escalation techniques to gain higher-level access (e.g., `root`). Common commands to try include:
```bash
sudo -l
sudo python3
```

```python3
import os
os.system("su")
```

**Important Note:** The writeup mentions "(If you did not touched to the fake exploit file\!)". This implies there might be a decoy or misleading file on the system intended to divert your efforts. It's crucial to be aware of such potential rabbit holes during your enumeration.
