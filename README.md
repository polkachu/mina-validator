# Mina Validator Node Ansible Setup

## Summary

You run two playbooks to set up a node.

```bash
ansible-playbook -i inventory mina_prekey_setup.yml -e "target=mina01"
```

Then you set up your key. You can set up a new key according to https://docs.minaprotocol.com/en/using-mina/keypair, or copy over an existing key pair to the folder.

```bash
ansible-playbook -i inventory mina_postkey_setup.yml -e "target=mina01"
```
