Vagrant.configure("2") do |config|
  # Use a Windows base image
  config.vm.box = "StefanScherer/windows_10"
  config.vm.box_version = "2021.12.09"

  # Set VM properties
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "8192" # Adjust memory as needed
    vb.cpus = 4        # Adjust CPU count as needed
  end

  # Configure Windows-specific settings
  config.vm.communicator = "winrm" # Use WinRM as the communicator
  config.winrm.username = "vagrant"
  config.winrm.password = "vagrant"

  # Set up a private network (optional)
  config.vm.network "private_network", ip: "192.168.56.10" # Assign a static IP

  # Enable RDP for Windows VM (optional, if you want GUI access)
  #config.vm.network "forwarded_port", guest: 3389, host: 53390  # RDP

  # Provision with Ansible (you'll need to configure Windows to accept Ansible)
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "install_java_maven.yml"
    ansible.host_key_checking = false  # Disable host key checking
  end
end
