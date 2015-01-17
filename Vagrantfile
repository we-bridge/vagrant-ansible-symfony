# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.network "private_network", ip: "192.168.50.4"

  config.vm.synced_folder "./", "/vagrant", type: "nfs"


  config.vm.provision :ansible do |ansible|
    ansible.playbook = 'provisioning/site.yml'
    ansible.extra_vars = {
        # APPNAME: 'MyApplication',
        DBNAME: 'symfony',
        DBUSER: 'vagrant',
        DBPASSWORD: 'vagrant'
    }
    # ansible.verbose = 'vvvv'
  end

end
