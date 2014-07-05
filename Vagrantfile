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
sudo apt-get -y install build-essential wget curl git vim re2c libxml2-dev m4

echo "****************************"
echo "Installing php5 dev packages"
echo "****************************"
sudo apt-get -y install php5-dev php-pear

echo "***********************************"
echo "Installing bison 2.7.1 dev packages"
echo "***********************************"
wget -q http://launchpadlibrarian.net/140087283/libbison-dev_2.7.1.dfsg-1_amd64.deb
wget -q http://launchpadlibrarian.net/140087282/bison_2.7.1.dfsg-1_amd64.deb

sudo dpkg -i libbison-dev_2.7.1.dfsg-1_amd64.deb
sudo dpkg -i bison_2.7.1.dfsg-1_amd64.deb
SCRIPT
  end
end
