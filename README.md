# Vagrant

## Установка Vagrant
На офф.  сайте скачать установщик под соотвествующую ОС (Linux, Windows, macOS):
```powershell
https://www.vagrantup.com/
```

## Скачивание Boxes
Адрес vagrant repo для просмотра имеющихся boxes для разных провайдеров:
```powershell
https://app.vagrantup.com/boxes/search
```

Адрес для скачивания boxes generic/ubuntu2004 под HyperV:
```powershell
https://app.vagrantup.com/generic/boxes/ubuntu2004/versions/4.1.8/providers/hyperv.box
```

## Команды Vagrant
Создаем локальный репозитарий c:\Users\Username\\.vagrant.d\boxes\
Добавляем необходимые boxes из сети в локальный репозитарий:
```powershell
vagrant box add hashicorp/bionic64
vagrant box add generic/ubuntu2004
```

Добавление в локальный репозитарий boxes из заранее скачанного файла:
```powershell 
vagrant box add generic/ubuntu2004 D:\ISO\path\to\vagrant\aac2390e-2cdd-4280-87b5-a77990bea64a
```

Проверка статуса ВМ, исходя из файла Vagrantfile
```powershell
vagrant box list
```

Cоздать пустой Vagrantfile, который содержит комментарии и общую структуру файла инициализации:
```powershell
vagrant init
```

Минимальные изменеия дефолтного Vagrantfile, полученного командой init:
```powershell
config.vm.box = "generic/ubuntu2004"
config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
```

Создать или запустить ВМ из описания Vagrantfile, запуск выполняется в той же директории, где и физически лежит Vagrantfile:
```powershell
vagrant up 
```

Запуск ВМ с указанием провайдера:
```powershell
vagrant up --provider=hyperv
```

Проверка состояния ВМ:
```powershell
vagrant status
```

Cписок всех, ранее созданных виртуальных машин на хост-системе:
```powershell
vagrant global-status
```

Приостанавливает (замораживает) ВМ, последующий запуск без пересоздания ВМ через vagrant up:
```powershell
vagrant suspend
```

Выключение ВМ:
```powershell
vagrant halt
```

Останавливает и потом запускает ВМ снова. Обычно требуется после внесения правок в конфигурационный файл Vargant
```powershell
vagrant reload
```

Уничтожить ВМ, также удаляет виртуальные жесткие диски ВМ:
```powershell
vagrant destroy
```

Копирование файлов с хостовой машины на гостевую:
```powershell
vagrant upload .\dist /var/www/html
```

Выполнение команд указанных в секции provision:
```powershell
vagrant provision
```

## Подключение к ВМ по SSH
default user: vagrant  
default password: vagrant

Подключение средствами vagrant:
```powershell
vagrant ssh 
 или
vagrant ssh default
 или
vagrant ssh controlnode
```

Стандартное подключение к ВМ по IP:
```powershell
ssh vagrant@192.168.10.20
```
