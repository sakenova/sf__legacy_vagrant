Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = "2"

  config.vm.provision "shell", inline: <<-SHELL
  sudo -s
  sh -c 'if ! grep -q "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" /etc/apt/sources.list.d/pgdg.list; then echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" >> /etc/apt/sources.list.d/pgdg.list; fi'
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
  apt-get update
  DEBIAN_FRONTEND=noninteractive apt-get install -y postgresql-8.4
  SHELL
  end
end