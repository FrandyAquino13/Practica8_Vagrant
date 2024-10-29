# Configuración de Vagrant
Vagrant.configure("2") do |config|
    # Usar imagen de Ubuntu como base
    config.vm.box = "ubuntu/bionic64"
    
    # Configurar RAM y CPU
    config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
    end
    
    # Instalar Apache y configurar el directorio compartido
    config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt install -y apache2
    sudo rm -rf /var/www/html
    sudo ln -s /vagrant/html /var/www/html
    SHELL
    
    # Compartir directorio local con la carpeta de Apache
    config.vm.synced_folder "./html", "/vagrant/html"
    
    # Configurar red privada para acceder al servidor
    config.vm.network "private_network", ip: "192.168.56.10"
end
