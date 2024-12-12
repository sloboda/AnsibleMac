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


### Installing Ansible

As above, using the python 3.9 that ships with Mac OS 15.1.1 and the pip3 that
comes with that version of python.

With my config below, Homebrew installs its own version of Ansible.
One day in the future I will sort that out.

### Using Ansible

```
$ ansible-playbook main.yml -K  -i inventory  --list-tags

playbook: main.yml

  play #1 (all): Configure host.	TAGS: []
      TASK TAGS: [always, dock, dotfiles, homebrew, osx, post, sudoers, terminal, vim]
$ ansible-playbook main.yml -K  -i inventory --tags "homebrew, dotfiles, dock"
$ ansible-playbook main.yml -K  -i inventory --tags "dock"
```

