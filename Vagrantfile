# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "pozgo/centos7"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network :forwarded_port, guest: 22, host: 2223, id: "ssh"
  config.vm.provision "shell",
    inline: "sudo yum install -y java-1.7.0-openjdk"
  config.vm.provision "shell",
    inline: "sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo"
  config.vm.provision "shell",
    inline: "sudo rpm --import http://pkg.jenkins-ci.org/redhat-stable/jenkins-ci.org.key"
  config.vm.provision "shell",
    inline: "sudo yum install -y jenkins"
  config.vm.provision "shell",
    inline:"sudo systemctl stop firewalld"
  config.vm.provision "shell",
    inline:"sudo service jenkins start"
  config.vm.provision "shell",
    inline:"sudo yum install -y git"
  config.vm.provision "shell",
    inline:"sudo yum install -y epel-release"
  config.vm.provision "shell",
    inline:"sudo yum install -y python34"
  config.vm.provision "shell",
    inline:"sudo yum install -y groovy"
  config.vm.provision "shell",
    inline:"sudo systemctl stop firewalld"
  config.vm.provision "shell",
    inline:"sudo systemctl disable firewalld"
  config.vm.synced_folder "~/Projects", "/home/vagrant/Projects"
  config.vm.synced_folder "~/.ssh", "/var/lib/jenkins/.ssh"

end
