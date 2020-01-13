# Vendin_infra

Vendin Infra repository

## Homework 5
Знакомство с облачной инфраструктурой. Google Cloud Platform.

bastion_IP = 35.204.5.56
someinternalhost_IP = 10.164.0.4

```

Способ подключения к someinternalhost в одну
команду:

```
ssh -i ~/.ssh/<name> -A <name>@35.204.5.56 -tt ssh 10.164.0.4
```

Подключения из консоли при помощи команды вида `ssh someinternalhost`.

Необходимо добавить в `~/.ssh/config`:

```
Host someinternalhost
HostName 10.164.0.4
User <name>
IdentityFile ~/.ssh/<name>
Port 22
ProxyCommand ssh -A <name>@35.204.5.56 nc %h %p %r
```

## Homework 6
Деплой тестового приложения.

Данные конфигурации:

```
testapp_IP = 35.204.119.206
testapp_port = 9292
```

Развертывание новой VM с тестовым приложением через gcloud:

```
gcloud compute instances create reddit-app\
  --boot-disk-size=10GB \
  --image-family ubuntu-1604-lts \
  --image-project=ubuntu-os-cloud \
  --machine-type=g1-small \
  --tags puma-server \
  --restart-on-failure \
--metadata startup-script-url=https://storage.googleapis.com/vendin-infra/startup_script.sh

```

## Homework 7

Сборка образов VM при помощи Packer

Установка Packer.
Cоздания базового образа reddit-base через Packer, припер необходимых переменных хранится в variables.json.example.
Деплой приложения из прошлого задания, на виртуальную машину созданую из созданого образа.

## Homework 8

Принципы организации инфраструктурного кода и работа над инфраструктурой в команде на примере Terraform.

Использование terraform import - для импорта ресурсов
Отделение БД в отельный инстанс
Разбиение конфигураци terraform на модули app, db, vpc
Применил модуль из реестра для создания bucket

