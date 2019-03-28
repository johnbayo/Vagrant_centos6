# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/6"
  config.vm.define "appserver" do |appserver|
	appserver.vm.hostname="appserver"
  	appserver.vm.network "private_network", ip: "192.168.10.2"
	$script = <<-SCRIPT
	sudo sed -i 's/PasswordAuthentication\s*no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
	SCRIPT
	config.vm.provision "shell", inline: $script
        config.vm.provision "shell" do |s|
              s.inline = <<-SHELL
                      echo "enabling ssh password authentication for centos 6."
                      sudo service sshd restart
                      exit 0
              SHELL
        end
        config.vm.provision :host_shell do |host_shell|
	  host_shell.inline = "ssh-keyscan 192.168.10.2 >> ~/.ssh/known_hosts"
        end
	config.vm.provision :host_shell do |host_shell|
          host_shell.inline = "sshpass -p 'vagrant' ssh-copy-id -i ~/.ssh/id_rsa.pub root@appserver -f"
        end
#        appserver.vm.provision "ansible" do |ansible|
#        	ansible.playbook = "#{Dir.home}//ansible/playbooks/test.yml"
#        end
  end
end
