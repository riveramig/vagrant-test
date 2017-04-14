# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
$configScript = <<SCRIPT
  	#!/bin/bash
  	echo "Excecuting script"
  	if [ ! -x /usr/bin/git ]
  	then
  		apt-get install -y git
  	fi
  	if [ ! -x /usr/bin/node ]
	then
  		apt-get install -y nodejs
  		sudo ln -s /usr/bin/nodejs usr/bin/node
  	fi
  	if [ ! -x /usr/bin/npm ]
  	then
  		apt-get install -y npm
  	fi
  	if [ ! -e /home/vagrant/timoMarket/app.js ]
  	then
  		git clone https://github.com/riveramig/timoMarket
  	fi
SCRIPT
#Script de ejecucion de la maquina virtual

Vagrant.configure("2") do |config|
  #Se define el nombre de la maquina vitual, con la etiqueta primary para al realizar vagrant up se ejecute primero
  config.vm.define "web",primary: true do |web|
  	web.vm.box = "ubuntu/trusty32"
  	#Comando para realizar el reenvio de puerto de la maquina puerto 8080 al host puerto 7777
  	web.vm.network "forwarded_port",guest:8080, host:7777, host_ip:"127.0.0.1"
  	#Instalar nodeJS, clonar una aplicacion web y servirla
  	web.vm.provision "shell", inline: $configScript
  	web.vm.provision "shell", inline: "npm start /home/vagrant/timoMarket"
  	#En localhost:7777 esta servida la pagina web
  end
end