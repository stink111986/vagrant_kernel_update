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


# Указываем репу от куда брать образ
ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
# какой образ ВМ будет использоваться
config.vm.box = "ubuntu/jammy64"
# Проверка обновлений образа По умолчанию она включена.
config.vm.box_check_update = false
# Настройка сети
# config.vm.network "forwarded_port", guest: 80, host: 8080
# config.vm.network "private_network", ip: "192.168.33.10"
# config.vm.network "public_network"