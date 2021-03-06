
GoCD Workshop
----

This repository contains the files required to run my GoCD workshop. The workshop is designed to introduce continuous delivery concepts using GoCD. 

####Contents
* Vagrantfile - This references a machine on atlas.hashicorp.com.
	* The virtual machine *will* change as I do more workshops and GoCD has new releases.
	* The virtual machine has all of the software needed for the workshop
		* git repositories
		* Docker beta elastic agent plugin
		* GoCD yaml configuration plugin
	* The instructions linked below go through the creation of several dependent pipelines
	* The "finished" yaml is also in .finished-yaml if you need to cheat

####To run the virtual machine

* Fork this repository (if you clone from here there's a high chance something will change that you may not expect)
* Bring up a command prompt 
* Type 'vagrant up' to start the machine
	* Note: This could take a long time the first time, depending on your available bandwidth. The virtual machine is 1.2GB. You do _not_ want to do this on a plane

####Clone workshop source code out of git server on VM

Next we need to modify your SSH configuration to use the Vagrant key. (Note, this step is optional. The point is to allow you to clone the git repos in the virtual machine with your own user so that you can use your own text editors, git clients or other tools. If you prefer, you can use the built in 'vagrant ssh' to access the box as the vagrant user and use the Linux command line tools.)

* Type 'vagrant ssh-config' - This will give you output that looks something like:

```markdown
Host default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /Users/kenmugrage/.vagrant.d/boxes/gocd-VAGRANTSLASH-2016-workshop/1.0/virtualbox/vagrant_private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

* Copy the line that begins with **IdentityFile**
* On your system, edit ~/.ssh/config and add the following section:

```markdown
Host workshop
    HostName localhost
    Port 2222
    IdentityFile /Users/kenmugrage/.vagrant.d/boxes/gocd-VAGRANTSLASH-2016-workshop/1.0/virtualbox/vagrant_private_key
    User vagrant
```

* Type 'git clone ssh://vagrant@workshop/gitrepo/application.git'
* Type 'git clone ssh://vagrant@workshop/gitrepo/gocd-configuration.git'

Workshop instructions at https://github.com/kmugrage/GoCD-Basic-Workshop/blob/master/WorkshopInstructions.md

