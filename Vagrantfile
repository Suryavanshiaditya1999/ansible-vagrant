Vagrant.configure("2") do |config|

  config.vm.define "dev_ws" do |dev_ws|
    dev_ws.vm.box = "debian/bookworm64"
    dev_ws.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 1
    end
    dev_ws.vm.network "private_network", ip: "192.168.33.11"

    dev_ws.vm.provision "ansible" do |ansible|
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
