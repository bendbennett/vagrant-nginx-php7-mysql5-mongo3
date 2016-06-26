# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "private_network", ip: "192.168.33.33"

  web_application_root_directory = "/var/www/{your_app}"
  web_application_owner_group = "www-data"

  config.vm.synced_folder "../{your_app}", web_application_root_directory, owner: web_application_owner_group, group: web_application_owner_group

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision :ansible do |ansible|
    ansible.extra_vars = {
      WEB_APPLICATION_ROOT_DIRECTORY: web_application_root_directory,
      WEB_APPLICATION_OWNER_GROUP: web_application_owner_group
    }
    ansible.playbook = "local.yml"
    ansible.verbose = "vvv"
  end

end
