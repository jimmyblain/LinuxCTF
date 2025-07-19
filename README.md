# Learn to Cloud - Linux Challenge

This is phase 1 of the [Learn to Cloud](https://learntocloud.guide/) curriculum - mastering the Linux operating system.

## Step 0 - Configuration of Cloud Environment

The challenges are performed in a Linux VM hosted in your preferred cloud provider. I have opted to use Microsoft Azure throughout this process as these skills are immediately of use in my current role.

Requirements to complete this step:

1. Create an [Azure](https://portal.azure.com/#home) account.
2. Install [Terraform](https://developer.hashicorp.com/terraform/install)
    + Rather than build all the necessary resources (VM, disk, network, ip, etc.) via portal, we achieve consistency and automation via **Infrastructure as Code**.
3. Install [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

Once these items are installed/configured, initiate an SSH tunnel to the Linux VM: `ssh ctf_users@VM_PUBLIC_IP_ADDRESS`

## Step 1 - Finding the Hidden File

**Objective:** Find a hidden file in the ctf_challenges directory and read its contents.

**Skills tested:**

+ Understanding of hidden files in Linux
+ Using ls with appropriate flags
+ Reading file contents

**Solution:**

1. `cd` to proper directory
2. `ls -a` to list all files, including hidden files
3. `cat` the hidden file to read it

## Challenge 2 - The Secret File

**Objective:** Locate a file containing "secret" in its name somewhere under your home directory.

**Solution:**

1. `cd` to `/home` directory
2. Run `find /home -type f -name secret*`
    + `find` searches a specific directory, file or directory type, and keyword match (use wildcard for pattern match)
3. Read hidden file

## Challenge 3 - The Largest Log

**Objective:** Find and read the contents of an unusually large file in `/var/log`.

**Solution:**

1. `cd` to specific directory
2. `ls -la` to list directory contents and their details
3. `tail` the largest log file to read the end of the file

## Challenge 4 - The User Detective

**Objective:** A user with UID 1002 has a flag in their login configuration.

Solution:

1. Read `/etc/passwd` file to find user associated with UID 1002
2. Navigate to user's home directory
3. `cat` .profile file in user directory

## Challenger 5 - The Permissive File

**Objective:** Find a suspicious file with wide-open permissions under `/opt`.

**Solution:**:

1. `find /opt -perm 777` to find highly permissive file
2. `cat` file found

## Challenge 6 - The Hidden Service

**Objective:** Something is listening on port `8080`. Connect to it to retrieve the flag.

**Solution:**

1. `netstat -tuln` to find information on the system's network ports
2. `curl localhost:8080` to find message at specified IP and port.

## Challenge 7 - The Encoded Secret

**Objective:** Find and decode an encoded flag in the `ctf_challenges` directory.

**Solution:**

1. `cat endoded_flag.txt` and pipe the output to `base64 --decode`
2. The flag is double encoded, so pipe that output into `base64 --decode` again

## Challenge 8 - SSH Key Authentication

**Objective:** Configure SSH key authentication and find a hidden flag.

**Solution:**

1. `find ~/.ssh -type f` to find files in .ssh directory in the home directory
2. Navigate to and `cat` the file with contents (non-zero filesize)

## Challenge 9 - DNS Troubleshoot

**Objective:** Someone modified a critical DNS configuration file. Fix it to reveal the flag.

**Solution:**

1. Navigate to `/etc/` for resolv.conf file
2. `diff resolv.conf resolv.conf.bak` to compare active DNS configuration file with its backup

## Challenge 10 - Remote Upload

**Objective:** Transfer any file to the `ctf_challenges` directory to trigger the flag.

**Solution:**

0. Prepare a file in local directory to be transferred
1. `sftp ctf_user@public_IP` to connect to remote server
2. `cd` to `ctf_challenges` directory
3. `put localFileName` to transfer local file to remote directory

## Challenge 11 - Web Configuration

**Objective:** The web server is running on a non-standard port. Find and fix it.

**Solution:**

1. Navigate to `/etc/nginx` directory and inspect .conf files with `cat`
2. `sudo nano /etc/nginx/sites-available/default` to edit file with built-in command line editor
3. `service nginx restart` to restart service and pick up new configuration
4. `curl 127.0.0.1` to check connection to local server and display content

## Challenge 12 - Network Traffic Analysis

**Objective:** Someone is sending secret messages via ping packets.

**Solution:**

1. `sudo tcpdump -i any -nn -s 0 icmp -w ~/ping_traffic.pcap` to capture and dump ping traffic to a file
2. `cat` file to find message.
