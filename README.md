# Vagrant
Адрес vagrant repo для просмотра имеющихся виртуальных машин для разных провайдеров
https://app.vagrantup.com/boxes/search

## Команды Vagrant
Добавляем необходимые боксы в репозитарий пользователя (c:\Users\sergeev\.vagrant.d\boxes\)
```powershell
vagrant box add hashicorp/bionic64
vagrant box add generic/ubuntu2004
```
Проверка статуса виртуальной машины, исходя из файла Vagrantfile
```powershell
vagrant box list
```
Cоздать пустой Vagrantfile, который содержит комментарии и общую структуру виртуальной машины.
```powershell
vagrant init
```
Правим Vagrantfile
```powershell
config.vm.box = "generic/ubuntu2004"
config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
```
Поднять ВМ из Vagrantfile. Запускается в той же директории, где и физически лежит Vagrantfile.
```powershell
vagrant up 
```
Запустить ВМ с указанием провайдера
```powershell
vagrant up --provider=hyperv
```
Проверка состояния ВМ
```powershell
vagrant status
```
Вход на ВМ по SSH (default user: vagrant, default password: vagrant)
```powershell
vagrant ssh 
vagrant ssh default
```
Копирование файлов с хостовой машины на гостевую
```powershell
vagrant upload .\dist /var/www/html
```
Приостанавливает машины. vagrant up затем запустит машину без ее пересоздания
```powershell
vagrant suspend
```
Выполнение команд указанных в секции provision
```powershell
vagrant provision
```
Останавливает и потом запускает ВМ снова. Обычно требуется после внесения правок в конфигурационный файл Vargant
```powershell
vagrant reload
```
Уничтожить ВМ и стиреть их жесткие диски 
```powershell
vagrant destroy
```
