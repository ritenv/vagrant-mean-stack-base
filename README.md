vagrant-mean-stack-base
============

Vagrant dev environment scaffold for MEAN stack apps

## Requirements
  [vagrant](http://www.vagrantup.com/) must be installed.

## Initializing & Setup
1. Clone the repo: `git clone git://github.com/ritenv/vagrant-mean-stack-base.git`
* Run with `vagrant up` from within the folder.
* SSH to the server via command `vagrant ssh meanserver`
* Launch server from folder `/usr/local/src/mean/mean-app` with command `node app.js`
* Browse to [Express Server](http://192.168.1.12:3000/) and the Express initial page will fire up

## Environment
	* Ubuntu 64-bit (precise)

## Loaded With Needed Tools
	* Nodejs v0.10.26
	* Express (ensured 3.5.1)
	* Jade (present version from npm)
	* Mongoose (present version from npm)
	* Bower (present version from npm)
	* Jasmine (present version from npm)
	* NodeUnit (present version from npm)
    * Application Server IP = 192.168.1.11
    * MongoDb Server IP = 192.168.1.12

## More Info
	* Apps are installed via Puppet
	* The modules directory is entirely managed by librarian-puppet
