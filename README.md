# Ansible Role: Dotfiles
[![CI](https://github.com/skaary/ansible-role-dotfiles/actions/workflows/ci.yml/badge.svg?branch=main&event=push)](https://github.com/skaary/ansible-role-dotfiles/actions?query=workflow%3Ci)

An Ansible Role that clones and symlinks my personal dotfiles on Linux.

## Installation

Download the role directly from git by typing into your terminal:

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-dotfiles.git

```

or

```bash
$ ansible-galaxy install git+https://github.com/skaary/ansible-role-dotfiles.git,,dotfiles
```

to change the installed role name from _ansible-role-dotfiles_ to just _dotfiles_.

Alternatively, install the role via a _requirements.yml_ file, e.g. when installing multiple roles at once. See [ansible galaxy documentation](https://galaxy.ansible.com/docs/using/installing.html#installing-multiple-roles-from-a-file) for more information.

## Role variables

The variable `dotfile_repo` is used to target the github repository with the dotfiles to be downloaded (by default, this variable is empty). To set where the dotfiles will be downloaded to, the variable `dotfile_dir` can be used (by default, it is set to `{{ dotfile_home }}/dotfiles`).

## Example playbook

```yaml
- hosts: all
  roles:
    - ansible-role-dotfiles
```

## Testing the role

### Vagrant

Vagrant can be used to test the role in order to graphically see it working in a virtual machine. Make sure Vagrant and VirtualBox are installed:

```bash
$ sudo apt install vagrant virtualbox
```

Use the following commands to run vagrant and boot up the virtual machine:

```bash
$ cd tests
$ vagrant up
```

Use `vagrant destroy` after you are done testing to delete the virtual machine. For more information about Vagrant and its commands, see the [Vagrant documentation](https://www.vagrantup.com/docs/cli).

### Molecule with Docker

Molecule can be used to test the role with a docker container. Make sure Molecule is installed:

```bash
$ python3 -m pip install --user "molecule[docker]"
```

Use the following commands to run Molecule in order to create the docker container and access the created container:
```bash
$ molecule converge && molecule login
```

For more information on how to use Molecule please consult the [Molecule documentation](https://molecule.readthedocs.io/en/latest/getting-started.html).

> Note: Python and Docker are required for the use of molecule. For more information, see [Molecule installation](https://molecule.readthedocs.io/en/latest/installation.html).

## License

MIT / BSD
