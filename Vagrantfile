# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/centos7"

  config.vm.network :forwarded_port, guest: 22, host: 2222
  config.vm.network :forwarded_port, guest: 80, host: 2280
  config.vm.network :forwarded_port, guest: 8080, host: 2281

  config.vm.network "private_network", ip: "192.168.123.123"

  config.vm.provision "shell", inline: <<-SHELL
  yum -y update
  yum install ruby
  ruby -v
  gem -v
  gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
  \curl -sSL https://get.rvm.io | bash -s stable
  source /etc/profile.d/rvm.sh
  rvm install ruby
  ruby -v
  gem install jekyll
  jekyll -v
  gem install bundler
  cd /opt/
  jekyll new blog
  jekyll serve --host 192.168.123.123 --port 80
  SHELL
end
