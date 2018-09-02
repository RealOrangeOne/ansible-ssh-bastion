# Ansible SSH Config
Ansible playbook to setup an SSH bastion server and clients.

## Usage

1. Modify the values in `vars.yml` to match your requirements:
    - `user` is the user to be used on both the client and bastion machines
    - `bastion_ssh_key` is the key to use to connect to the bastion machine.
    - `enable_root` enables SSH connections as root to the bastion
    - `bastion_ip` is the IP of the bastion, to be baked into the config of the clients.

2. Populate `hosts` with your required hosts. A single `bastion`, and however many `clients`.
3. Run the playbook with `ansible-playbook bastion.yml -i hosts --ask-pass -K`
