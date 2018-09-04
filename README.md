# Ansible SSH Config
Ansible playbook to setup an SSH bastion server and clients.

## Security Features

- Non-standard SSH port for bastion
- Require key and password for bastion connections
- 5 minute connection timeout
- Login within 30 seconds of initial connection
- Disable SSHv1
- Separate key for connection to bastion and further hosts
- No warnings from [`ssh-audit`](https://github.com/arthepsy/ssh-audit)

Some of the hardening and configuration is based on https://joscor.com/blog/hardening-openssh-server-ubuntu-14-04/.

## Usage

1. Modify the values in `vars.yml` to match your requirements:
    - `user` is the user to be used on both the client and bastion machines
    - `bastion_ssh_key` is the key to use to connect to the bastion machine.
    - `enable_root` enables SSH connections as root to the bastion
    - `bastion_ip` is the IP of the bastion, to be baked into the config of the clients.
2. Populate `hosts` with your required hosts. A single `bastion`, and however many `clients`. `standalone` can be used to configure clients who don't require connections through the bastion.
3. Run the playbook with `ansible-playbook bastion.yml -i hosts --ask-pass -K`
