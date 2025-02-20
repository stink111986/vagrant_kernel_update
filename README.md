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

# Выливаем ветку в Github
git push -u origin feature
____________________________________________________________________________________________


