# -*- mode: ruby -*-
# vi: set ft=ruby :

# Following 3 parameters should be set to suit your dev environment
web_application_code_directory_relative_to_this_directory = "../{your_app_on_host_relative_to_this_dir}"
web_application_root_directory = "{your_app_on_guest}"                  # e.g., "/var/www/my_app"
web_application_owner_group = "{web_application_owner_and_group}"       # e.g., "www-data"


Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "private_network", ip: "192.168.33.33"

  config.vm.synced_folder web_application_code_directory_relative_to_this_directory, web_application_root_directory, owner: web_application_owner_group, group: web_application_owner_group

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
