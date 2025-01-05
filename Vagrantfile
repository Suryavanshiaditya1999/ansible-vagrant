Vagrant.configure("2") do |config|

  config.vm.define "dev_ws_1" do |dev_ws_1|
    dev_ws_1.vm.box = "debian/bookworm64"
    dev_ws_1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 1
    end
    dev_ws_1.vm.network "private_network", ip: "192.168.33.11"

    dev_ws_1.vm.provision "ansible" do |ansible|
      ansible.playbook = "dev1.yaml"
      ansible.inventory_path = "inventory.ini"
    end
  end

  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "ubuntu/focal64"
    jenkins.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
    jenkins.vm.network "private_network", ip: "192.168.33.12"


    jenkins.vm.provision "ansible" do |ansible|
      ansible.playbook = "jenkins.yaml"
      ansible.inventory_path = "inventory.ini"
    end
  end
end
