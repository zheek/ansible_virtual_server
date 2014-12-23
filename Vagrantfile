VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

   config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", "1536"]
   end

  config.vm.define 'sandbox' do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.hostname = 'sandbox-vagrant'
    machine.vm.network :private_network, ip: "192.168.2.101"
  end

  config.vm.synced_folder "./", "/home/vagrant/repos" 

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/provision.yml"
    ansible.sudo = true
    ansible.groups = {
      "sandbox-machine" => ["sandbox"],
      "all_groups:children" => ["sandbox-machine"]
    }
    # ansible.verbose = 'vvvv'
  end
end

