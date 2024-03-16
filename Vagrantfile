# ####################################################################
# ################### CONFIGURATION VARIABLES ########################
# ####################################################################
IMAGE_NAME_UBUNTU = "bento/ubuntu-20.04"    # Image to use for ubuntu
IMAGE_NAME_FEDORA = "generic/fedora28"      # Image to use for fedora
MEM = 2048                                  # Amount of RAM
CPU = 1                                     # Number of processors
UBUNTU_VM_NBR = 2                           # Number of ubuntu node
FEDORA_VM_NBR = 1                           # Number of fedora node
NETWORK_ADAPTER="wlp0s20f3"                 # Bridge network adapter


Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = MEM
    v.cpus = CPU
  end

  config.vm.synced_folder ".", "/vagrant"
  config.vm.provision "file", source: "./ssh/config", destination: "~/.ssh/config"
  config.vm.provision "shell" do |s|
    ssh_prv_key = ""
    ssh_pub_key = ""
    if File.file?("#{Dir.home}/.ssh/id_rsa")
      ssh_prv_key = File.read("#{Dir.home}/.ssh/id_rsa")
      ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    else
      puts "No SSH key found. You will need to remedy this before pushing to the repository."
    end
    s.inline = <<-SHELL
      if grep -sq "#{ssh_pub_key}" /home/vagrant/.ssh/authorized_keys; then
        echo "SSH keys already provisioned."
        exit 0;
      fi
      echo "SSH key provisioning."
      mkdir -p /home/vagrant/.ssh/
      touch /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} > /home/vagrant/.ssh/id_rsa.pub
      chmod 644 /home/vagrant/.ssh/id_rsa.pub
      echo "#{ssh_prv_key}" > /home/vagrant/.ssh/id_rsa
      chmod 600 /home/vagrant/.ssh/id_rsa
      chown -R vagrant:vagrant /home/vagrant
      exit 0
    SHELL
  end

  # Ubuntu node config
  (1..UBUNTU_VM_NBR).each do |i|
    config.ssh.insert_key = false
    config.vm.define "vmubuntu#{i}" do |vmubuntu|
      vmubuntu.vm.box = IMAGE_NAME_UBUNTU
      vmubuntu.vm.hostname = "vmubuntu#{i}"
      #vmubuntu.vm.network "public_network", bridge: NETWORK_ADAPTER
      vmubuntu.vm.network :private_network, ip: "192.168.56.1#{i}"
      vmubuntu.vm.post_up_message = "VM VMUBUNTU#{i} (192.168.56.2#{i}) is RUNNING !!!"
    end
  end

  # # Fedora node config
  # (1..FEDORA_VM_NBR).each do |i|
  #   config.ssh.insert_key = false
  #   config.vm.define "vmfedora#{i}" do |vmfedora|
  #     vmfedora.vm.box = IMAGE_NAME_FEDORA
  #     vmfedora.vm.hostname = "vmfedora#{i}"
  #     #vmfedora.vm.network "public_network", bridge: NETWORK_ADAPTER
  #     vmfedora.vm.network :private_network, ip: "192.168.56.2#{i}"
  #     vmfedora.vm.post_up_message = "VM VMFEDORA#{i} (192.168.56.2#{i}) is RUNNING !!!"
  #   end
  # end
end
