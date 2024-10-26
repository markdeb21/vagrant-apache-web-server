Vagrant.configure("2") do |config|
  # Configuración de la máquina virtual
  config.vm.box = "ubuntu/bionic64" # Usa Ubuntu 18.04 LTS
  config.vm.hostname = "apache-web-server"

  # Asigna recursos a la máquina virtual
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512" # Asigna 512 MB de RAM
    vb.cpus = 1       # Asigna 1 CPU
  end

  # Configura la red y la carpeta compartida
  config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.synced_folder "./web", "/var/www/html", SharedFoldersEnableSymlinksCreate: false

  # Provisión para instalar Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end
