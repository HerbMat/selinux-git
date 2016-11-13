Vagrant.configure("2") do |config|
  
	config.vm.define "selinux"
	config.vm.box = "centos/7"
	config.vm.box_check_update = true
	config.ssh.forward_agent = true
	config.ssh.insert_key = false
	config.vm.network "forwarded_port",
		guest: 22,
		host: 2200,
		auto_correct: true
		
	config.vm.synced_folder ".", "/home/vagrant/ansible",
		create: true,
		owner: "vagrant",
		group: "vagrant",
		mount_options: ["dmask=027","fmask=137"]

	config.vm.network "private_network", ip: "192.168.33.10"
	config.vm.network "public_network"
	config.vm.provider "virtualbox" do |vb|
		vb.gui = false
		vb.cpus = 2
		vb.memory = 2048
	end
	config.vm.provision "shell", inline: <<-SHELL
		sudo yum install -y git
	SHELL
end
