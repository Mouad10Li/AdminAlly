# Ansible AdminAlly Automation Project

This project automates network configurations on Cisco routers and installs a DNS server (`bind9`) using Ansible. It uses GNS3 topology to simulate the routers and the server setup.

## Requirements

Before running the playbooks, ensure the following are installed and configured:

- **Python 3**
- **Ansible**
- **Cisco IOS routers** with SSH access
- **Virtual environment** set up (optional but recommended)

## Installation

1. **Set up a Python virtual environment:**

   ```bash
   python3 -m venv ansible_env
   source ansible_env/bin/activate
   ```

2. **Install dependencies:**
   After activating the virtual environment, run:

   ```bash
   pip install -r requirements.txt
   ```

   This will install the necessary Python packages, including `paramiko`, `ansible`, and `ansible-netcommon`. The Cisco IOS Ansible collection (`cisco.ios`) is also required and should be installed automatically using the command in the requirements file.

3. **Install Cisco IOS Collection:**
   If you need to manually install it:
   ```bash
   ansible-galaxy collection install cisco.ios
   ```

## Inventory Structure

The inventory file (`hosts`) specifies the target routers and the DNS server. It looks like this:

```ini
[routers]
router1 ansible_host=192.168.122.4
router2 ansible_host=192.168.122.2
router3 ansible_host=192.168.122.3

[dns_server]
192.168.122.200

[dns_server:vars]
ansible_ssh_private_key_file=~/.ssh/allyadmin.pub
ansible_user=moro

[routers:vars]
ansible_connection=network_cli
ansible_network_os=ios
ansible_user=mouad
ansible_ssh_pass=mouad
```

## Usage

### 1. **Assign IP Addresses to Interfaces on Routers**

To assign IP addresses to interfaces on the routers, run the following playbook:

```bash
ansible-playbook assign_ip_addresses.yaml
```

This playbook performs the following actions:

- Assigns IP addresses to the `GigabitEthernet` interfaces on `router1`, `router2`, and `router3`
- Saves the configuration to memory

### 2. **Create Loopback Interfaces on Routers**

To configure loopback interfaces on all routers, use:

```bash
ansible-playbook creat_Loooback_interface.yaml
```

This playbook will:

- Create `Loopback0` interface on each router and assign it the IP `1.1.1.1/32`
- Verify and display the loopback configuration

### 3. **Install and Configure `bind9` DNS Server**

To install and configure `bind9` on the DNS server, run:

```bash
ansible-playbook install_bind9.yaml
```

This playbook performs the following tasks:

- Updates the package list on the DNS server
- Installs `bind9` package
- Starts and enables the `bind9` service
- Verifies if the `bind9` service is running and displays the status

## Note

- Ensure that you have SSH access to the routers and the server using the correct credentials. The inventory file includes the necessary connection details for each device.

## Troubleshooting

- **SSH Connection Errors:** If you're having issues connecting to your devices, verify that the SSH keys or passwords are correctly configured.
- **Ansible Cisco IOS Collection Errors:** Make sure the `cisco.ios` collection is installed and up to date.
