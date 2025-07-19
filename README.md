# Learn to Cloud - Linux Challenge

This is a public repo to record my progress through my cloud learnings.

## Step 0 - Configuration of Cloud Environment.

To start, I needed to configure my chosen cloud environment. I am starting with Azure, since that is what my company uses and I already have high levels of access to that space. I will, of course, begin my learnings in a personal environment, but that access and those resources will be useful when I become confident in my skills (and save us a lot of money int he long run).

Requirements to complete this step:

1. Create an [Azure](https://portal.azure.com/#home) account.
2. Install [Terraform](https://developer.hashicorp.com/terraform/install)
    + Rather than build all the necessary resources (VM, disk, network, ip, etc.) via portal, we achieve consistency and automation via **Infrastructure as Code**.
3. Install [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)

Once these items are installed/configured, I am able to initiate an SSH tunnel to the Linux VM: `ssh ctf_users@VM_PUBLIC_IP_ADDRESS`

## Step 1 - Finding the Hidden File

**Objective:** Find a hidden file in the ctf_challenges directory and read its contents.

**Skills tested:**

+ Understanding of hidden files in Linux
+ Using ls with appropriate flags
+ Reading file contents