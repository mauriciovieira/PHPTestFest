VAGRANTFILE_API_VERSION = "2"
 
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  else
    puts "_Info_: Plugin '''vagrant-cachier''' is not installed."
  end
 
  config.vm.box = "ubuntu/trusty64"
 
  config.vm.network "forwarded_port", guest: 8042, host: 8042
 
  config.vm.provision "shell" do |s|
    s.inline = <<SCRIPT
echo "************************"
echo "Updating system packages"
echo "************************"
sudo apt-get -y update
sudo apt-get -y upgrade
 
echo "******************************"
echo "Installing supporting packages"
echo "******************************"
sudo apt-get -y install build-essential wget curl git vim
 
echo "****************************"
echo "Installing php5 dev packages"
echo "****************************"
sudo apt-get -y install php5-dev php-pear
 
SCRIPT
  end
 
end
