VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

	config.vm.define 'pgsql' do |pgsql|
		pgsql.vm.box = 'precise64'
		pgsql.vm.box_url = "http://files.vagrantup.com/precise64.box"

		pgsql.vm.network 'forwarded_port', guest: 5432, host: 5432

		pgsql.vm.provision 'puppet' do |puppet|
			puppet.module_path = 'puppet/modules'
			puppet.manifests_path = 'puppet/manifests'
			puppet.manifest_file = 'pgsql.pp'
			puppet.facter = {
					'db' => 'testdb'
			}
		end

	end
	
	config.vm.define 'mysql' do |mysql|
		mysql.vm.box = 'precise64'
		mysql.vm.box_url = "http://files.vagrantup.com/precise64.box"
		
		mysql.vm.network "forwarded_port", guest: 3306, host: 3306

		mysql.vm.provision "puppet" do |puppet|
			puppet.module_path = 'puppet/modules'
			puppet.manifests_path = 'puppet/manifests'
			puppet.manifest_file = 'mysql.pp'
			puppet.facter = {
					'db' => 'testdb'
			}
		end

	end
end