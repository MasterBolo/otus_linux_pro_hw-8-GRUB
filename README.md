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
