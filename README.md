# Vagrant
Адрес vagrant repo для просмотра имеющихся виртуальных машин для разных провайдеров
https://app.vagrantup.com/boxes/search

## Команды Vagrant
Адрес vagrant repo для просмотра имеющихся виртуальных машин для разных провайдеров
https://app.vagrantup.com/boxes/search  
Добавляем необходимые боксы в репозитарий пользователя (c:\Users\sergeev\.vagrant.d\boxes\)
```ps
vagrant box add hashicorp/bionic64
vagrant box add generic/ubuntu2004
```
Проверка статуса виртуальной машины, исходя из файла Vagrantfile
```powershell
vagrant box list
```
Cоздать пустой Vagrantfile, который содержит комментарии и общую структуру виртуальной машины.
```bash
vagrant init
```
Правим Vagrantfile
```bash
config.vm.box = "generic/ubuntu2004"
config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
```
Поднять ВМ из Vagrantfile. Запускается в той же директории, где и физически лежит Vagrantfile.
```bash
vagrant up 
```
Поднять ВМ с указанием провайдера
```bash
vagrant up --provider=hyperv
```
Проверка состояния ВМ
```bash
vagrant status
```
Вход на ВМ по SSH (default user: vagrant, default password: vagrant)
```bash
vagrant ssh 
vagrant ssh default
```
Копирование файлов с хостовой машины на гостевую
```bash
vagrant upload .\dist /var/www/htnl
```
Приостанавливает машины. vagrant up затем запустит машину без ее пересоздания
```bash
vagrant suspend
```
Выполнение команд указанных в секции provision
```bash
vagrant provision
```
Останавливает и потом запускает ВМ снова. Обычно требуется после внесения правок в конфигурационный файл Vargant
```bash
vagrant reload
```
Уничтожить ВМ и стиреть их жесткие диски 
```bash
vagrant destroy
```
