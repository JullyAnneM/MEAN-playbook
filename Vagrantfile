Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.hostname = "solucoesweb.each.com"

  config.vm.network "forwarded_port", guest: 4000, host: 4000 # Node.JS
  config.vm.network "forwarded_port", guest: 4200, host: 4200   # Angular
  config.vm.network "forwarded_port", guest: 27017, host: 27017   # MongoDB

  config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.synced_folder "../data", "/vagrant_data"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "solucoesweb.each.com"
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]  
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/playbook.yml"
    ansible.verbose = true
  end
end
