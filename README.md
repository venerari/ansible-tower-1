# Ansible-Tower v3.2.x Installation

Tested on Vmware Workstation v12 or KVM either on an OS Centos7 or Redhat7.4 developer version (you should register your developer version) and either on a VM or physical computer. We run Ansible-Tower with 2 vcpu, 5GB ram and 60GB disk, this is the minimum resources, more is better and faster.

if this break, let us know

This will only take about 10-15 min if you are using SSD including vm provisioning. You may provision your centos7/redhat7 as no-gui server and make sure you can access the ip from the host browser whether it's a NAT or BRIDGE network.

Do these after the vm had been provisioned,

Create the centos7 repo on the centos7/redhat7.4 but login as root first
if you have redhat 7.x licensed, better

$ vi /etc/yum.repos.d/centos.repo

[centos]<br>
name=CentOS $releasever - $basearch<br>
baseurl=http://mirror.centos.org/centos/7/os/$basearch/<br>
enabled=1<br>
gpgcheck=1<br>
gpgkey=http://mirror.centos.org/centos/7/os/$basearch/RPM-GPG-KEY-CentOS-7<br>

Clean yum<br>
$ yum clean all

Install software<br>
$ yum install epel-release

$ yum update -y<br>
the epel-release should upgrade to 7-11 version

$ yum install git ansible -y

Established ssh<br>
$ ssh-keygen<br>
enter/enter/enter

$ ssh-copy-id localhost<br>
type yes and put the root password

Clone this repository<br>
$ git clone https://github.com/tso-ansible/ansible-tower.git

$ cd ansible-tower/

Run ansible-playbook<br>
$ ansible-playbook -i inventory ansible-tower.yml

And one last step, about 5-15min. It should give you the script to execute like /tmp/ansible-tower3.2.2/setup.sh , just copy and paste it back to shell,

$ /tmp/ansible-tower-setup-3.2.2/setup.sh<br>
and execute it
