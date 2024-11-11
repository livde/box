# Vagrantfile para crear una VM con Apache
Vagrant.configure("2") do |config|
    # Selecciona una imagen de Ubuntu para la VM
    config.vm.box = "ubuntu/bionic64"
  
    # Asigna el nombre a la VM
    config.vm.hostname = "apache-server"
  
    # Configura red para acceder a Apache desde el host
    config.vm.network "forwarded_port", guest: 80, host: 8082
  
    # Asigna memoria RAM y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Sincroniza una carpeta local con la carpeta de Apache en la VM
    config.vm.synced_folder "./paginas", "/var/www/html"
  
    # Script para instalar Apache en la VM
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo ufw allow 80/tcp
    SHELL
  end
  