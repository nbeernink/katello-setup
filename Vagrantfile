Vagrant.configure("2") do |config|
  config.hostmanager.enabled=true
  config.hostmanager.manage_host = true

  # Foreman config
  config.vm.define "foreman.local.lan" do |foreman|
    foreman.vm.box = "centos/7"
    foreman.vm.hostname = "foreman.local.lan"
    foreman.vm.network "private_network", ip: "192.168.3.3"
    foreman.vm.provider :libvirt do |libvirt|
      libvirt.memory= 8192
      libvirt.cpus = 4
    end

    foreman.vm.synced_folder ".", "/vagrant", disabled: true
    foreman.vm.provision "ansible" do |ansible|
      ansible.playbook = 'provision/foreman.yml'
    end

  end

  # Node config for easy scaling
  (1..3).each do |i|
    config.vm.define "node-#{i}.local.lan" do |node|
      node.vm.box = "centos/7"
      node.vm.hostname = "node-#{i}.local.lan"
      node.vm.network "private_network", ip: "192.168.3.#{10+i}"

      node.vm.synced_folder ".", "/vagrant", disabled: true
      node.vm.provision "ansible" do |ansible|
        ansible.playbook = 'provision/node.yml'
      end
    end
  end
end
