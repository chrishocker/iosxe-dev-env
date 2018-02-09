# Create a Local IOS-XE Dev Environment Using Vagrant

## Prereqs
* OS-X
* Python 2.7 (preferrably separate from OS X system python; brew install python)
* Virtualenv (pip2 install virtualenv)
* Vagrant (brew cask install virtualbox)
* Virtualbox (brew cask install vagrant)

## Procedure

### Step 1 - Download and Install IOS-XE Vagrant Box

```
wget http://netprog.cisco.com/vagrant_box/iosxe-16.06.02.box

vagrant box add iosxe/16.06.02 iosxe-16.06.02.box --force
```

### Step 2 - Clone Repo

``` 
git clone https://github.com/chrishocker/iosxe-dev-env.git

cd iosxe-dev-env
```

### Step 3 - Create Virtualenv and Install Python Requirements

``` 
virtualenv venv

source venv/bin/activate

pip install -r requirements.txt
```

### Step 4 - Vagrant Up

```
vagrant up
```

### Step 5 - Run Ansible Playbook

```
ansible-playbook ansible-provision.yaml
```

Note: The last 2 tasks that enable guestshell and git will error out, but they should complete successfully.

### Step 6 - Verify

```
vagrant ssh

csr1kv#guestshell

[guestshell@guestshell ~]$ git
usage: git [--version] [--help] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p|--paginate|--no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

The most commonly used git commands are:
   add        Add file contents to the index
   bisect     Find by binary search the change that introduced a bug
   branch     List, create, or delete branches
   checkout   Checkout a branch or paths to the working tree
   clone      Clone a repository into a new directory
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   fetch      Download objects and refs from another repository
   grep       Print lines matching a pattern
   init       Create an empty Git repository or reinitialize an existing one
   log        Show commit logs
   merge      Join two or more development histories together
   mv         Move or rename a file, a directory, or a symlink
   pull       Fetch from and merge with another repository or a local branch
   push       Update remote refs along with associated objects
   rebase     Forward-port local commits to the updated upstream head
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index
   show       Show various types of objects
   status     Show the working tree status
   tag        Create, list, delete or verify a tag object signed with GPG

'git help -a' and 'git help -g' lists available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
```