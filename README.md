# Mina Validator Node Ansible Setup

## TL/DR

You run two playbook and set up a node. For example:

```bash
ansible-playbook -i inventory mina_prekey_setup.yml -e "target=mina01"
```

```bash
ansible-playbook -i inventory mina_postkey_setup.yml -e "target=mina01"
```
