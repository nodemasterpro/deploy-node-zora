# Deploy Zora Node

Join the Zora Network, a Layer 2 solution focused on decentralizing and democratizing access to digital media and culture. Backed by significant investments, Zora is dedicated to becoming the foundation for digital media's future through blockchain technology.

## Prerequisites

- Linux Ubuntu 22.04 LTS with Docker installed
- 200 GB available storage
- 16 GB RAM
- x86 architecture

Contabo VPS 2 is recommended for its reliability and performance. See the Contabo VPS Server Guide for setup instructions.

## Ethereum API Key for Zora Node

Before installing a Zora node, you need an Ethereum Mainnet API key from Alchemy:

1. Sign up and verify your account at [Alchemy](https://www.alchemy.com/).
2. Create a new app, name it, provide a description, and select Ethereum Mainnet as the network.
3. Access your API keys under "View Key" and copy your HTTPS key. It will be required during the Ansible script execution.

## Installing Dependencies

Update your system and install Ansible and Git:

```
sudo apt update && sudo apt upgrade -y
sudo apt install ansible git -y
```

## Downloading the Project

Clone the repository to access the Ansible playbook and all necessary files:

```
git clone https://github.com/nodemasterpro/deploy-node-zora.git
cd deploy-node-zora
```

## Executing the Playbook

Launch the installation with the following playbook command:
```
ansible-playbook zora_node.yml --extra-vars "node_action=install"
```

Run the playbook with root privileges.

## Starting Zora Node Service

After initializing, start the Zora node service:
```
sudo systemctl start zora-node
```

## Viewing Logs

To check the operation of your Zora node:
```
journalctl -u zora-node -f -o cat
```

## Additional Information

### Stopping Services
```
sudo systemctl stop zora-node
```

### Starting Services
```
sudo systemctl start zora-node
```

### Updating the Node
```
ansible-playbook zora_node.yml --extra-vars "node_action=update"
```
### Removing the Node
```
ansible-playbook zora_node.yml --extra-vars "node_action=remove"
```

Join the Zora community on Discord and Twitter to stay updated. For any questions, reach out on my Discord. Follow updates on [Twitter](https://twitter.com/NodeMasterPro), join the [Telegram Group](https://t.me/nodemasterpro), the [Discord Server](https://discord.gg/5q6VDPm97A), and subscribe to the [YouTube Channel](https://www.youtube.com/channel/UCM2svc9ijlWnTFBnqTTGZwA).


