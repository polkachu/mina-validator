# Mina Validator Node Ansible Setup

Three playbooks to set up a node.

#### 1. Prepare a machine before keypair generation

```bash
ansible-playbook -i inventory mina_prekey_setup.yml -e "target=mina1a"
```

#### 2. Generate keypair

You have two options here. First, you can set up a new keypair according to https://docs.minaprotocol.com/en/using-mina/keypair, and you will need to copy the public key and password to the inventory file to prepare for the next step. The other option is to copy an existing key pair to the server. You will put the my-wallet and my-wallet.pub in the roles->key->files folder, and then run the playbook

```bash
ansible-playbook -i inventory mina_key_setup.yml -e "target=mina1a"
```

#### 3. Launch Mina

```bash
ansible-playbook -i inventory mina_postkey_setup.yml -e "target=mina1a"
```

#### Postscript

We highly recommend you install mina monitor. The server process is here: https://github.com/olton/mina-node-monitor/blob/master/server/SERVER-DOCS.md and the client process is here: https://github.com/olton/mina-node-monitor/blob/master/client/CLIENT-DOCS.md. We do not have the Ansible script here. Maybe one day we will update

I cannot make the mina client to automatically start with the script. Therefore, you should get into the server and run the following:

```bash
systemctl --user daemon-reload
systemctl --user stop mina
systemctl --user start mina
systemctl --user enable mina
sudo loginctl enable-linger
```

To check the health of mina service:

```bash
systemctl --user status mina
```

To check the status of mina client:

```bash
mina client status
```

To check the health of mina block producer sidecar:

```bash
sudo journalctl -f -u mina-bp-stats-sidecar.service
```

# Nominate Polkachu's Mina Validator

```
B62qizDizMYmXDS7LUkocoYNnrryPCxyrJM2v8eNJzaj31aU9bUfDAM
```

curl -sL https://deb.nodesource.com/setup_14.x | sudo bash -
sudo apt -y install nodejs
