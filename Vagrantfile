Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = true
  config.vm.network "private_network", ip: "192.168.100.100"
  config.vm.synced_folder "/Users/MarioPitassi/Lab", "/var/www", type:"nfs"

end
