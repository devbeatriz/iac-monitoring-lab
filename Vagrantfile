Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  # Private network with static IP
  config.vm.network "private_network", ip: "192.168.56.20"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  # Provisioning with Ansible
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.install = true
  end
end