
Vagrant.configure(2) do |config|

  # Virtual Machine Basics
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |v|
    # Lower to 512 to save resources
    v.memory = 1024
    v.cpus   = 1
  end

  # Create a Test VM
  config.vm.define "test" do |test|
    # Nothing Else
  end

  # Provision Vagrant machine with Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "tests/test.yml"
    ansible.groups   = {
      "vagrant" => ["test"]
    }
  end

end
