Vagrant.configure("2") do |config|
  # Use a Windows base image
  config.vm.box = "gusztavvargadr/windows-10"
  config.vm.box_version = "2202.0.2409"

  # Set VM properties
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192" # Adjust memory as needed
    vb.cpus = 4        # Adjust CPU count as needed
  end

    # Set Windows-specific configuration options
  config.vm.guest = :windows
  config.vm.communicator = "winrm"
  config.vm.winrm.username = "vagrant"
  config.vm.winrm.password = "vagrant"

  #config.vm.provision "shell", path: "enable_winrm.ps1"

  # Set up a private network (optional)
  config.vm.network "private_network", type: "dhcp"

  # Enable RDP for Windows VM (optional, if you want GUI access)
  #config.vm.network "forwarded_port", guest: 3389, host: 3389  # RDP

  # Provision with Ansible (you'll need to configure Windows to accept Ansible)
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "install_java_maven.yml"
    ansible.host_key_checking = false  # Disable host key checking
  end

end
