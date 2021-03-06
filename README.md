# Apps Forge

Virtual Machines for Development.

## Requirements

* [Nugrant](https://github.com/maoueh/nugrant)
* [Vagrant 1.8.0](http://vagrantup.com)
* [Vagrant Host Manager](https://github.com/smdahlen/vagrant-hostmanager)
* [VirtualBox](https://www.virtualbox.org)

## How To Install The Plugins

```bash
host $ vagrant plugin install nugrant
host $ vagrant plugin install vagrant-hostmanager
```

## Available Boxes

### db:

**OS:** Ubuntu 14.04  
**Hostname:** db
**Default Ip:** 192.168.100.101

**Stack**

- Utilities from https://github.com/anxs/utilities
- Redis 2.8.9
- MySQL -latest
- PostgreSQL 9.3

### ruby:

**OS:** Ubuntu 14.04  
**Hostname:** ruby
**Default Ip:** 192.168.100.102

**Stack**

- Utilities from https://github.com/anxs/utilities
- rbenv with ruby 2.2.4 and 2.3.0
- nodejs

### js:

**OS:** Ubuntu 14.04  
**Hostname:** js
**Default Ip:** 192.168.100.103

**Stack**

- Utilities from https://github.com/anxs/utilities
- nvm with latest stable nodejs

## How to Build the Virtual Machines

Building the virtual machine is this easy:

```bash
host $ git clone https://github.com/pablocrivella/apps-forge.git
host $ cd apps-forge
```

Copy the ```.vagrantuser.example``` file:

```bash
host $ cp .vagrantuser.example .vagrantuser
```

And edit the configuration to suit your needs.

## First Time Setup

To create ALL vm's run:

```bash
host $ vagrant up
```

If you want to create a specific vm run:

```bash
host $ vagrant up <vm>
```

Where ```<vm>``` should be: ```db``` or ```ruby```

example:

```bash
host $ vagrant up db
host $ vagrant up ruby
```

or its oneliner equivalent

```bash
host $ vagrant up db ruby
```

Then, to connect to a specific vm run:

```bash
host $ vagrant ssh <vm>
```

### db vm specific config

You can export the following environment variables:

- ```mysql_root_passwd``` to set the password for user: root (defaults to blank)
- ```mysql_developer_passwd``` to set the password for user: developer (defaults to blank)
- ```postgresql_developer_passwd``` to set the password for user: developer (defaults to blank)

example:

```bash
host $ mysql_root_passwd=pass123 mysql_developer_passwd=pass321 postgresql_developer_passwd=pass321 vagrant up db
```

## Recommended Workflow

The recommended Workflow is:

* Edit files in the host computer
* Run within the virtual machine

## Virtual Machine Management

When done just log out with and suspend the virtual machine

```bash
host $ vagrant suspend <vm>
```

then, resume to hack again
```bash
host $ vagrant resume <vm>
```

Run
```bash
host $ vagrant halt <vm>
```

to shutdown the virtual machine, and

```bash
host $ vagrant up <vm>
```

to boot it again.

Or (for a shortcut) run

```bash
host $ vagrant reload <vm>
```

You can find out the state of a virtual machine anytime by invoking

```bash
host $ vagrant status <vm>
```

Finally, to completely wipe the virtual machine from the disk **destroying all its contents**:

```bash
host $ vagrant destroy <vm> # DANGER: all is gone
```

Please check the [Vagrant Documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.
