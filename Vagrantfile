Vagrant.configure("2") do |config|

  ###################################################################################
  config.vm.define "mariadb-client" do |node|

    # which image to use
    node.vm.box = "opensuse/Leap-15.6.x86_64"

    # sizing of the VMs
    node.vm.provider "libvirt" do |lv|
      lv.random_hostname = true
      lv.memory = 1024
      lv.cpus = 2
    end

    # set the hostname
    node.vm.hostname = "mariadb-client"

    # disable shared folders
    node.vm.synced_folder ".", "/vagrant", disabled: true

  end # config.vm.define agents

  ###################################################################################
  config.vm.define "mariadb-server" do |node|

    # which image to use
    node.vm.box = "opensuse/Leap-15.6.x86_64"

    # sizing of the VMs
    node.vm.provider "libvirt" do |lv|
      lv.random_hostname = false
      lv.memory = 2048
      lv.cpus = 2
    end

    # set the hostname
    node.vm.hostname = "mariadb-server"

    # disable shared folders
    node.vm.synced_folder ".", "/vagrant", disabled: true

    # Ansible
    node.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.limit = "all"
      ansible.playbook = "ansible/playbook-vagrant.yml"
    end # node.vm.provision

  end # config.vm.define

end # Vagrant.configure
