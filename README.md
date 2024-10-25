# RHCSA Automated Practice Deployment (RHEL9)

## Purpose
The purpose of this project is to help individuals preparing for the RHCSA exam by providing a practice environment that simulates real exam conditions.

## Prerequisites
1. **VirtualBox**
 - [Install VirtualBox depending on your operating system.](https://www.virtualbox.org/wiki/Downloads)
 - [Install the VirtualBox Extension Pack that matches your installed version.](https://www.virtualbox.org/wiki/Downloads)
 >>**NOTE2:** VirtualBox 7, 6, 5, 4 only supported. **(Latest version of VirtualBox (7.1) is not supported)**

2. **Vagrant**
- [Install latest version of Vagrant depending on your operating system.]((https://www.vagrantup.com/downloads.html))
- After installing Vagrant, add the Vagrant Ansible plugin with the following command (supported on Windows as well)
```
vagrant plugin install vagrant-guest-ansible
```
3. **ruby**
- [Install latest version ruby depending on your operatingsystem.](https://www.ruby-lang.org/en/documentation/installation/)
4 **python**
- [Install python depending on your operatingsystem.](https://www.python.org/downloads/)


## Deployment

Once the above software is installed, Do the following.

1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)

`mkdir bin && cd bin`

2. Clone the repo to it with `git clone https://github.com/jithunarayanan/rhcsaenv.git` command.

3. Change to the `rhcsaenv` directory that is now in your `~/bin` directory.

`cd rhcsaenv`

4. Run `vagrant up` to deploy the environment (If the environment has a designated repo VM it will take the longest to deploy the first time only, this is because the repo system has all the packages available to the base release but will be quicker on subsequent deployments.)

**Also, don't be spooked by any scary red font during the setup process. There are known issues that won't have a negative affect on the environment.**

_Now the deployment should be up and running!_

## Useful Informations:
Deployment should take around 20 minutes depending on your computer and the internet speed. The first time you run the vagrant up command, it will download the OS images for later use. In other words, it will take longest the first time around but will be faster when it is deployed again.You can run `vagrant destroy -f` to destroy your environment at anytime. **This will erase everything**. This environment is meant to be reuseable, If you run the `vagrant up` command after destroying the environment, the OS image will already be downloaded and environment will deploy faster.

 You shouldn't need to access the IPA server during your practice exams. Everything should be provided that you would normally need during an actual exam. Hope this helps in your studies!You can also use the VirtualBox console to interact with the VMs or through a terminal. **If you need to reset the root password, you would need to use the console.**

## Notable Vagrant Commands to control the environment:
- `ansible-playbook playbooks/reset.yml` - Used for resetting the environment after attempting the practice exam in the Red Hat Certs Slack workspace practice exam channel. 
- `vagrant up` - Boots and provisions the environment
- `vagrant destroy vm-name` - To destroy a Virtual Machine
- `vagrant destroy -f` - Shuts down and destroys all the Virtual Machines
- `vagrant halt` - Only shuts down the environment VMs (can be booted up with `vagrant up`)
- `vagrant suspend` - Puts the VMs in a suspended state
- `vagrant resume` - Takes VMs out of a suspended state
- `vagrant box list` - To list the boxes downloaded
- `vagrant box remove box/name` - To remove a box

## Included systems:
- repo.lab.example.com
- server1.lab.example.com
- server2.lab.example.com

## System Details:
> server1
- 192.168.55.150
- Gateway - 192.168.55.1
- DNS - 8.8.8.8
> server2
- 192.168.55.151
- Gateway - 192.168.55.1
- DNS - 8.8.8.8

There is a Repo/AppStream available to use from `http://repo.lab.example.com/BaseOS` and `http://repo.lab.example.com/AppStream`

## Accessing the systems
Remember to add the IP addresses to your local host file if you want to connect to the guest systems with the hostname.
Username - vagrant
Password - vagrant
- For root - use `sudo` or `sudo su`
Access example - `ssh vagrant@192.168.55.150` or `vagrant ssh system`

## Help
If you're having problems with the environment, please submit an issue by going to the `ISSUES` tab at the top. If you have more questions, looking for practice exams to use against this environment, or just looking for a fantastic Red Hat community to join to get your questions answered, check out the Red Hat Certs Slack Workspace. You can find the invite link at the top of this page next to the description.

## Outcome.
Deploy a virtual environment on RHEL9 with predefined configurations, minimizing manual setup time.

_Powered by Ansible and Vagrant_ 

