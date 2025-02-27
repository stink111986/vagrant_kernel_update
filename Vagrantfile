Vagrant.configure("2") do |config|
  # Используем образ Ubuntu 22.04
  config.vm.box = "ubuntu.box"

  # Настройка сети
  config.vm.network "public_network", ip: "192.168.0.13",
    netmask: "255.255.255.0",
    gateway: "192.168.0.10"

  # Настройка DNS
  config.vm.provision "shell", inline: <<-SHELL
    echo "nameserver 192.168.0.3" | sudo tee /etc/resolv.conf > /dev/null
  SHELL

  # Настройка провайдера (VirtualBox)
  config.vm.provider "virtualbox" do |vb|
    vb.name = "TEST"  # Имя машины в VirtualBox
    vb.memory = "1024"  # Выделяем 1 ГБ оперативной памяти
    vb.cpus = "1"       # Выделяем 1 CPU
  end

  # Синхронизация папки с хоста в гостевую машину
  config.vm.synced_folder "D:/OTUS", "/mnt"

  # Автоматически обновляем пакеты и устанавливаем необходимые зависимости
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison mc
    # Разрешаем вход по паролю
    sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config.d/60-cloudimg-settings.conf
    sudo systemctl restart ssh
  SHELL

  # Установка пароля для пользователя vagrant
  config.vm.provision "shell", inline: <<-SHELL
    echo "vagrant:vagrant" | sudo chpasswd
  SHELL
end
