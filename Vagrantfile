# Configuration file to spin up a machine that will cache deb files.
# Author: Aidan Nagorcka-Smith (aidanns@gmail.com)

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Define which virtual machine to use as a base for this one.
  config.vm.box = "ubuntu-raring-server-amd64_13.04"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"

  # Create the shell script used to create the system in pkg_cmd.

  # Install squid-deb-proxy server.
  pkg_cmd = "apt-get update; apt-get install -y squid-deb-proxy avahi-utils; sudo cp /vagrant/squid-deb-proxy.conf /etc/squid-deb-proxy/squid-deb-proxy.conf; restart squid-deb-proxy; "

  # Install the client also.
  pkg_cmd << "apt-get install -y squid-deb-proxy-client; "

  # Install the English language pack.
  pkg_cmd << "apt-get install -y language-pack-en; "

  config.vm.provision :shell, :inline => pkg_cmd

  # Create a host-only network to the vagrant instance.
  config.vm.network :private_network, ip: "192.168.33.254"

end
