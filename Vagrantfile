# -*- mode: ruby -*-
# vi: set ft=ruby :

require "fileutils"


VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  #config.vm.box = "opentable/win-2012r2-standard-amd64-nocm"
  config.vm.box = "cdaf/WindowsServer"

  config.vm.box_check_update = true

  config.vm.network "private_network", ip: "10.0.20.101"

  config.vm.guest = :windows

  #config.winrm.username = "Administrator"
  #config.winrm.password = "vagrant"

  config.windows.set_work_network = true

  # Port forward WinRM and RDP
  #config.vm.network :forwarded_port, guest: 3389, host: 3389
  #config.vm.network :forwarded_port, guest: 5985, host: 5985, id: "winrm", auto_correct: true

  config.vm.synced_folder ".", "/vagrant_data"

   config.vm.provider "virtualbox" do |vb|
    # Don't boot with headless mode
    vb.gui = false
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus",   "2"]
  end
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
    config.vbguest.no_install = true
    config.vbguest.no_remote = true
  end
end
