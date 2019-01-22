# Vagrant box Centos 6 with root ssh access 
This Vagrant file will deploy a centos 6 operating system, assign a private ip and also enable ssh access.<br/>
examples integrating ansible with vagrant is also shown in the Vagrant file<br/>
<br/>
Requirements<br/>
vagrant installation<br/>
ssh config for root access<br/>
ansible installation (optional) <br/>
<br/>
<pre>
Host appserver
        User root
        Hostname 192.168.10.2
</pre>
<br/>
comment out the lines below to integrate your ansible plays and rename "test.yml" to your play. <br/>
<pre>
#        appserver.vm.provision "ansible" do |ansible|
#               ansible.playbook = "#{Dir.home}//ansible/playbooks/test.yml"
#        end
</pre>
<br/>
Usage:<br/>
<pre>
vagrant up
ssh appserver
</pre>
<br/>
