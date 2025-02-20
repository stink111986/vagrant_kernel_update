# vagrant_kernel_update

____________________________________________________________________________________________
*VAGRANT*

Основные команды Vagrant

# Инициализация нового Vagrant-проекта.vagrant init
vagrant init 
# Запуск и создание виртуальной машины.vagrant up
vagrant up
# Подключение к виртуальной машине через SSH.vagrant ssh
vagrant ssh 
# Остановка виртуальной машины.vagrant halt
vagrant halt 
# Удаление виртуальной машины.vagrant destroy
vagrant destroy
# Проверка статуса виртуальной машины.vagrant status 
vagrant status 
# Применение изменений в конфигурации без перезагрузки виртуальной машины.vagrant provision
vagrant provision 
# Перезагрузка виртуальной машины с применением новых конфигураций.vagrant reload
vagrant reload 

******************
Конфигурация Vagrantfile
******************

*******************************
# Добавление локального образа в Vagrant
vagrant box add ubuntu-local/jammy64 /home/admin/boxes/ubuntu.box   или   vagrant box add ubuntu-local/jammy64 ~/boxes/ubuntu.box
#Проверяем что добавили
vagrant box list
# Указываем репу от куда брать образ
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
# какой образ ВМ будет использоваться
config.vm.box = "ubuntu/jammy64"
# Проверка обновлений образа По умолчанию она включена.
config.vm.box_check_update = false
# Настройка сети
* проброс портов
config.vm.network "forwarded_port", guest: 80, host: 8080
* приватная сеть 
config.vm.network "private_network", ip: "192.168.33.10"
* публичная сеть
config.vm.network "public_network"
#Пример
# Настройка сети
  config.vm.network "private_network", ip: "192.168.0.13",
    netmask: "255.255.255.0",
    gateway: "192.168.0.10"

  # Настройка DNS
  config.vm.provision "shell", inline: <<-SHELL
    echo "nameserver 192.168.0.3" | sudo tee /etc/resolv.conf > /dev/null
  SHELL

# Синхронизация папок (папка ../data на хосте будет доступна в виртуальной машине по пути /vagrant_data.)
config.vm.synced_folder "../data", "/vagrant_data"
# Провайдер
config.vm.provider "virtualbox" do |vb|
# включить графический интерфейс VirtualBox.
  vb.gui = true
# Оперативная память  
  vb.memory = "1024"
# Количество процессоров
  vb.cpus = "2"
end
# Provisioning (настройка виртуальной машины, выполнение команд после создания ВМ)

config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison mc
  SHELL
end