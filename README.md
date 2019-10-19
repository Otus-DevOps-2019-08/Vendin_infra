# Vendin_infra

## Homework 5
Знакомство с облачной инфраструктурой. Google Cloud Platform.

Данные конфигурации:

```
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