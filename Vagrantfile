# -*- mode: ruby -*-
# vim: set ft=ruby :

MACHINES = {
    :otuslinux => {
        :box_name => "centos8-kernel6",
        :ip_addr => '192.168.11.101'
    },
}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|

    config.vm.synced_folder ".", "/vagrant", disabled: true
    config.vm.define boxname do |box|
      box.vm.box = boxconfig[:box_name]
      box.vm.host_name = boxname.to_s
      box.vm.network "private_network", ip: boxconfig[:ip_addr]

      box.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024"]
      end

      box.vm.provision "shell", path: "bootstrap.sh"

    end
  end
end
