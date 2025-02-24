# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "debian/bookworm64"

  config.vm.network "forwarded_port", guest: 80, host: 5000

  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y git nano vim python-is-python3 python3-venv python3-pip
     sudo python -m venv flask_venv
     sudo source flask_venv/bin/activate
     sudo pip install Flask
     sudo touch hello.py
     "from flask import Flask
      app = Flask(__name__)
      @app.route('/')
      def hello():
      	return '<p>Hello, World!</p>'" >> hello.py
      sudo flask --app hello run --host=0.0.0.0
  SHELL
end
