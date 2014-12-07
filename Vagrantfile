Vagrant.configure('2') do |config|
  config.vm.box = 'opscode-ubuntu-14.04'
  config.vm.box_url = 'http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-14.04_chef-provisionerless.box'

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = './cookbooks'

    chef.add_recipe 'build-essential'
    chef.add_recipe 'ruby_build'
    chef.add_recipe 'rbenv::vagrant'
    chef.add_recipe 'rbenv::user'

    chef.json = {
        rbenv: {
            user_installs: [{
                user: 'vagrant',
                rubies: [ '1.9.3-p484' ],
                global: '1.9.3-p484',
                gems: {
                    :'1.9.3-p484' => [
                        { name: 'bundler' }
                    ]
                }
            }]
        }
    }
  end
end

# vagrant ssh -c 'wget https://www.getchef.com/chef/install.sh'
# vagrant ssh -c 'sudo bash install.sh -v 12.0.0'
# vagrant provision
