# Vendin_infra

Vendin Infra repository

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

