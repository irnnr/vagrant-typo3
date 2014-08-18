$project_name = 'vagrant-typo3'

Vagrant.require_version ">= 1.5.0"
VAGRANTFILE_API_VERSION = "2"

# ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- -----

# Required Vagrant plugins
#
# vagrant-hostmanager (1.4+)
# vagrant-omnibus
# vagrant-vbguest (recommended)

# ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- ----- -----


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "www.#{$project_name}.dev"
  config.vm.network :private_network, ip: "192.168.144.100"

  # automatically manage /etc/hosts on hosts and guests
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

  config.ssh.forward_agent = true
  
  config.vm.provider "virtualbox" do |vb|
    vb.name = "www.#{$project_name}.dev"
    
    vb.gui = false
    
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
  end

  config.omnibus.chef_version = "11.12.4"

  config.vm.provision :chef_solo do |chef|
    
    # Chef run list
    chef.add_recipe 'apt'
    chef.add_recipe 'vim'
    chef.add_recipe 'networking_basic'
    chef.add_recipe 'timezone'
    chef.add_recipe 'mysql::server'
    chef.add_recipe 'php'
    chef.add_recipe 'php::module_gd'
    chef.add_recipe 'php::module_apc'
    chef.add_recipe 'apache2'
    chef.add_recipe 'typo3'
    chef.add_recipe 'typo3::scheduler'
    chef.add_recipe 'typo3::vagrant'

    chef.json = {
      :tz => 'America/Los_Angeles',
      :mysql  => {
        :server_root_password   => "password",
        :server_repl_password   => "password",
        :server_debian_password => "password",
        :allow_remote_root      => true
      },
      :git    => {
        :prefix => "/usr/local"
      },
      :apache => {
        :default_site_enabled => false
      },
      :typo3  => {
        :version => '6.2.4',
        :package => 'source',
        :site_name => $project_name
      }
    }
  end

  # run host manager after chef
  config.vm.provision :hostmanager

end
