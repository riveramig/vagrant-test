# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  #Se define el nombre de la maquina vitual, con la etiqueta primary para al realizar vagrant up se ejecute primero
  config.vm.define "web",primary: true do |web|
  	web.vm.box = "ubuntu/trusty32"
  	#Comando para realizar el reenvio de puerto de la maquina puerto 8080 al host puerto 7777
  	web.vm.network "forwarded_port",guest:8080, host:7777, host_ip:"127.0.0.1"
  	#Instalar nodeJS, clonar una aplicacion web y servirla
  	web.vm.provision "shell", inline:"apt-get install -y nodejs"
  	web.vm.provision "shell", inline:"apt-get install -y npm"
  	web.vm.provision "shell", inline:"apt-get install -y git"
  	web.vm.provision "shell", inline:"ln -s /usr/bin/nodejs /usr/bin/node"
  	web.vm.provision "shell", inline:"git clone https://github.com/riveramig/timoMarket"
  	web.vm.provision "shell", inline:"node /home/vagrant/timoMarket/app.js"
  	#En localhost:7777 esta servida la pagina web
  end
end