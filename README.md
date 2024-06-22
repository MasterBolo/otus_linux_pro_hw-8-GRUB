# Домашняя работа: Работа с загрузчиком

Цель работы: Изучить загрузку системы

Что нужно сделать?

- Включить отображение меню Grub
- Попасть в систему без пароля несколькими способами
- Установить систему с LVM, после чего переименовать VG
- Добавить модуль в initrd

# Выполнение

## Создаём виртуальную машину

Создаю в домашней директории Vagrantfile, собираю стенд.
 
## Включаем отображение меню Grub

Для отображения меню нужно отредактировать конфигурационный файл:

``` root@grub:~# vi /etc/default/grub ```

``` 
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
```
Обновляем конфигурацию загрузчика и перезагружаемся для проверки:
```
root@grub:~# update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-102-generic
Found initrd image: /boot/initrd.img-5.15.0-102-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
done
root@grub:~# reboot
```

## Попасть в систему без пароля несколькими способами

Открываем GUI VirtualBox , запускаем виртуальную машину и при выборе ядра для загрузки нажимаем e - в данном контексте edit. 
Попадаем в окно, где мы можем изменить параметры загрузки:

![Image 1](screenshots/pic1.png)

Способ № 1. init=/bin/bash

В конце строки, начинающейся с linux, добавляем init=/bin/bash и нажимаем сtrl-x для загрузки в систему.

![Image 2](screenshots/pic2.png)

Рутовая файловая система при этом монтируется в режиме Read-Only. Для монтирования ее в режим Read-Write, вводим команду:

![Image 2](screenshots/pic2.png)
