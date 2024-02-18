# Deploy Node Aleo

This repository contains Ansible scripts for setting up, updating, and removing a NuLink node on Linux systems. The playbook facilitates the deployment of a NuLink node, managing its services, and monitoring logs for troubleshooting.

## Prerequisites
A Linux system Ubuntu 22.04 TLS with root.
Git and Ansible installed on your machine.
Getting Started

## Step 1: Installing Dependencies
Update your system's package list:
```
sudo apt update && sudo apt upgrade -y
```

Install Ansible and Git:
```
sudo apt install ansible git -y
```

## Step 2: Downloading the Project
Clone this repository to get the Ansible playbook and all necessary files:
```
git clone https://github.com/user/deploy-node-nulink.git
cd deploy-node-nulink
```

## Step 3: Executing the Playbook
Run the playbook using the following command. You'll be prompted to specify the action (install, update, or remove):
```
ansible-playbook nulink_node.yml
```
Ensure you're running the playbook with root privileges or via a user with sudo access.

## Step 3: Executing the Playbook
Run the playbook using the following command. You'll be prompted to specify the action (install, update, or remove):
```
ansible-playbook nulink_node.yml
```
Ensure you're running the playbook with root privileges or via a user with sudo access.

## Step 4: NuLink Node Initialization

Open a terminal on your server and execute the following script:
sh /root/nulink/init_nulink_node.sh
You will be prompted to answer several questions to configure your node.

##  Step 5: Managing the Nulink Node

Starting Services
After a manual node initialization, start the NuLink node service:


```
sudo systemctl start nulink-node
```

Stopping Services
To stop the NuLink node service:
```
sudo systemctl stop nulink-node
```

## Step 6: Viewing Logs
To view the logs for the NuLink node:

```
journalctl -u nulink-node -f -o cat
```

## Step 7: Update Procedure
To update your NuLink node, execute the playbook with the update action. This will pull the latest Docker image of the NuLink node and restart the service:

```
ansible-playbook nulink_node.yml --extra-vars "node_action=update"
```


## Additional Note
After installation or update, the public wallet address is stored in /root/nulink/wallet_address.txt. Refer to this file for your node's wallet address. Ensure the initialization script /root/nulink/init_nulink_node.sh is executed manually to complete the node setup before starting the service.