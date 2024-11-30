# AnsibleMac

Set up Apple Mac using Ansible!

## Install Ansible on a mac

See [Mac Development Ansible Playbook](https://github.com/geerlingguy/mac-dev-playbook)
These instructions expand upon those guidelines.

1. Use the Privileges application on the Mac to become a user with Administrator privileges.
    * This is required to run sudo. Some of the Ansible steps require sudo to run
2. Start a Terminal window after you have become the user with Administrator privileges.
3. Ensure Apple's command line tools are installed ( ` xcode-select --install ` to launch the installer).
    * Note this is also required to use `git`
4. Install Ansible:
    * Run the following command to add Python 3 to your $PATH: export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"
        * This requires the python3.9 that ships with Mac OS 15.1.1
    * Upgrade Pip: sudo pip3 install --upgrade pip
    * Install Ansible: pip3 install ansible
5. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
8. Install everything else using Ansible playbooks as shown below.


### Installing Pip

```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py --user
### NOTE The scripts pip, pip2 and pip2.7 are installed
### in '/Users/david/Library/Python/2.7/bin' which is not on PATH.
```

### Installing Ansible

```
pip3 install --user ansible
```

### Using Ansible

```
ansible-playbook main.yml -i inventory -K
ansible-playbook --list-tasks main.yml -i inventory -K
ansible-playbook --tags=vim  main.yml -i inventory -K
ansible-playbook --tags=Logbook  main.yml -i inventory -K
```

