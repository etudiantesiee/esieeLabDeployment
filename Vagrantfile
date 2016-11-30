# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Creation d'une machine virtuel UBUNTU
  config.vm.box = "hashicorp/precise32"

  config.vm.define "node1" do |machine|
  
  	  # Configuration spécifique de virtualbox
	  machine.vm.provider "virtualbox" do |vb|
	  	  # Config specifique car nous créons un VM dans une autre VM
	      vb.customize ["modifyvm", :id, "--cpus", "1"]
	      
	      # Nom de la VM node1
	      vb.name = "node1"
	  end
  
      # Adresse IP et nom du serveur distant
      machine.vm.network "private_network", ip: "192.168.33.10"
      machine.vm.hostname = "node1"
      
      # Provisionning du serveur à partir d'ansible
	  machine.vm.provision :ansible do |ansible|
	        ansible.limit = "all"
	        ansible.playbook = "site.yml"
	  end
   end
end
