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
     sudo apt-get update
     sudo apt-get install -y git nano vim python-is-python3 python3-venv python3-pip
     sudo python -m venv flask_venv
     source flask_venv/bin/activate
     pip install Flask
     touch hello.py
     echo "from flask import Flask" >> hello.py
     echo "app = Flask(__name__)" >> hello.py
     echo "@app.route('/')" >> hello.py
     echo "def hello():" >> hello.py
     echo "	return '<p>Hello, World!</p>'" >> hello.py" >> hello.py
     sudo flask --app hello run --host=0.0.0.0

  SHELL
end
