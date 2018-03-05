# encoding: utf-8

##
VAGRANT_BOX = 'ubuntu/trusty64'
# project folder
VM_FOLDER = 'twoalpha'
# VM User — 'vagrant' by default
VM_USER = 'vagrant'
# Where to sync to on Guest — 'vagrant' is the default user name
GUEST_PATH = '/home/' + VM_USER + '/' + VM_FOLDER

Vagrant.configure(2) do |config|
  # Vagrant box from Hashicorp
  config.vm.box = VAGRANT_BOX
  
  
  #DHCP — comment this out if planning on using NAT instead
  # config.vm.network "private_network", type: "dhcp"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 3000, host: 3000, id: "test"

  # Sync folder
  config.vm.synced_folder '../', GUEST_PATH
  # Disable default Vagrant folder, use a unique path per project
  config.vm.synced_folder '.', '/home/' + VM_USER + '', disabled: true
  # Install Git, Node.js, ...
  config.vm.provision :shell, :path => 'setup.sh', :args => [VM_FOLDER, VM_USER]
end
