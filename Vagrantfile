# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.ssh.private_key_path = "keys/vagrant"
  ## Base Box File
  config.vm.box = "centos7_base"
  ## Auto Update Box
  config.vm.box_check_update = false

  config.vbguest.no_install = false
  
  ## Networking
  config.vm.network "private_network", ip: "192.168.33.33"
  
  ## Sync Folder
  ## ここ変更しろー
  config.vm.synced_folder ".", "/vagrant", type: nil
  
  ## Port Forwarding
  config.vm.network "forwarded_port", guest: 80, host: 8000, host_ip: "127.0.0.1", protocol: "tcp", auto_correct: true
  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1", protocol: "tcp", auto_correct: true
  config.vm.network "forwarded_port", guest: 443, host: 4430, host_ip: "127.0.0.1", protocol: "tcp", auto_correct: true
  config.vm.network "forwarded_port", guest: 3306, host: 3306, host_ip: "127.0.0.1", protocol: "tcp", auto_correct: true
  
  config.vm.provider "virtualbox" do |vbox, override|
    vbox.gui = false
    vbox.linked_clone = true
    ## Advanced virtualbox configuration
    vbox.cpus = 2
    vbox.memory = 512
    vbox.customize [
    "modifyvm", :id,
    "--cpus", "2",
    "--memory", "1024",
    "--ostype", "RedHat_64",
    "--cpuexecutioncap", "100",
    "--pae", "on",
    "--hwvirtex", "on",
    "--vtxvpid", "on",
    "--vtxux", "on",
    "--ioapic", "on",
    "--paravirtprovider", "kvm",
    "--nestedpaging", "on",
    "--largepages", "on",
    ]
  end

  ## cache
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "Provisioning/site.yml"
    ansible.verbose = "v"
  end
end
