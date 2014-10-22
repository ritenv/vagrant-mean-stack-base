# -*- mode: ruby -*-
# vi: set ft=ruby :

require "yaml"

_config = YAML.load(File.open(File.join(File.dirname(__FILE__), "/yaml/vagrantconfig.yaml"), File::RDONLY).read)

CONF = _config

Vagrant::Config.run do |config|
	config.vm.define :mongodb do |mongodb|
		mongodb.vm.box = "ubuntu_precise64"
		mongodb.vm.box_url = "http://files.vagrantup.com/precise64.box"
		mongodb.vm.network :hostonly, "192.168.1.11"

		# This shell provisioner installs librarian-puppet and runs it to install
		# puppet modules. This has to be done before the puppet provisioning so that
		# the modules are available when puppet tries to parse its manifests.
		# must pass in directory of the Puppetfile location
		mongodb.vm.provision :shell, :path => "shell/prereqs.sh", :args => "puppet/librarian/mongodb"

		# Now run the puppet provisioner. Note that the modules directory is entirely
		# managed by librarian-puppet
		mongodb.vm.provision :puppet do |mongodb_puppet|
			mongodb_puppet.manifests_path = "puppet/manifests"
			mongodb_puppet.manifest_file  = "mongo.pp"
		end
	end

	config.vm.define :meanserver do |meanserver|
		# choose the ubuntu 64 bit version as your VM Box
		meanserver.vm.box = "ubuntu_precise64"
		meanserver.vm.box_url = "http://files.vagrantup.com/precise64.box"
		meanserver.vm.network :hostonly, "192.168.1.12"

		# This shell provisioner installs librarian-puppet and runs it to install
		# puppet modules. This has to be done before the puppet provisioning so that
		# the modules are available when puppet tries to parse its manifests.
		# must pass in directory of the Puppetfile location
		meanserver.vm.provision :shell, :path => "shell/prereqs.sh", :args => "puppet/librarian/meanserver"

		# Now run the puppet provisioner. Note that the modules directory is entirely
		# managed by librarian-puppet
		meanserver.vm.provision :puppet do |meanserver_puppet|
			meanserver_puppet.manifests_path = "puppet/manifests"
			meanserver_puppet.manifest_file  = "meanserver.pp"
		end

		# define the name of your application here within the args e.g replace "mean-app" with your app name
		meanserver.vm.provision :shell, :path => "shell/kickstart-app.sh",:args => "mean-app"
	end
end
