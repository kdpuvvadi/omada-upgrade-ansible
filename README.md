# Upgrade Omada Controller with Ansible

Update you Omada Controller with Ansible

## Clone the repo

```bash
git clone https://github.com/kdpuvvadi/omada-upgrade-ansible.git && cd omada-ansible
```

## Vars & Inventory

* Copy inventory sample file `cp inventory.ini.j2 inventory.ini`
* Change the ip address with actual IP address of the host server.
* Copy varible file with `cp vars.yml.j2 vars.ini`

## Setup Ansible

* install python & pip with `sudo apt install python3 python3-pip -y`
* install ansible with `pip python3 -m pip install ansible`

## Test Connection

```bash
ansible all -m ping
```

If connection is good, output should be something like below.

```bash
server1 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

## Install

Run the playbook with

```bash
ansible-playbook main.yml
```

If user needs password for elevation, append `-K` to the above.

```bash
ansible-playbook main.yml -K
```

## Post Installation

If playbook run was successfull and didn't encounter any error, controller will be install and Omada controller will be available on `http://HOST-IP:8088/` or `https://HOST-IP:8043/`.

### Ports

From `v5.0.29` Adoption port has been changed to `29814/tcp`. Omada controller needs these ports `8088`, `8043`, `27001`, `27002`, `29810`, `29811`, `29812`, `29813` and `29814` to work properly.
