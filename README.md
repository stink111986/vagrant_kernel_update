# vagrant_kernel_update
____________________________________________
*GIT*

# создаем репозиторий на git (add README, gitiignore actionscript, license BSD 3)
# создаем ключ на ПК 		
ssh-keygen -t ed25519
# копируем ключ
cat ~/.ssh/id_rsa.pub
# добавляем ключ на github в setting  ->  ssh and gpg -> new keygen
# копируем репозиторий на машину 
git clone git@github.com:stink111986/vagrant_kernel_update.git
# Проверить статус репозитория
git status
#  Добавить изменения в индекс (README.md это имя файла)
git add README.md 
# Добавить все изменения (включая новые файлы)
git add .
# Создать коммит
git commit -m "Описание действий"
# Отправить изминения
git push origin main
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