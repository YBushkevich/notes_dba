## 13. Стандартные сервисы (telnet, ssh, scp, rsync). Публичный и приватный ключ. Процесс установки соединения, VNC, screen, NFS, SMB, yum, rpm.

### Cron

Что именно делает этот самый крон, он активируется с интервалом в одну минуту, проверяет файлы crontab и запускает указанные в них программы. 

[Делаем «жизнь» в Linux проще или автоматизация запуска процессов с помощью cron](https://habr.com/ru/post/217655/)

минута : час : число : месяц : день недели : пользователь : задача

1. 05, 40 * * * * -> в 5 и 40 мин. каждого часа
2. */15 * * * * -> каждые 15 минут

В директорию cron.d добавляются скрипты для всех устанавливаемых программ если у них есть какие-то запланированные действия.

Системные задания:

1. cron.{hourly, daily, weekly, monthly}
2. cron.deny
3. crontab
4. cron.d

Пользовательские задачи  планировщика

`/var/spool/cron/crontabs`

При наличии cron.allow и cron.deny всегда будет выигрывать cron.allow. Если у нас только есть cron.allow то только те кто в этом листе могут пользоваться crontab. 

### Anacron & At

Anacron – это асинхронный планировщик, тот же самый cron только асинхронный.

At – планирует однократную задачу в любое время в будующем.

**Anacron**

​	/etc/anacrontab 

​	период(дни) : задержка(минуты) : id : команда

​	/var/spool/anacron

Anacron – при старте проверяет, выполнялись ли заданиями, и если нет, после задержки он начинает их выполнять. Интервал стоит для того чтоб после того как вы влючили компьютер после долгого отсутствия и чтоб anacron разом не начал выполнять все задания.

Анакрон определяет выполнялась ли задача в указанный период, если не выполнялась, он выполняет команду через заданный промежуток времени, и записывает выполнение в специальный файл. 

`ls -l /var/spool/anacron` -> cron.{daily, weekly, monthly}

**At**

​	At - создать

​	Atq - посмотрет

​	Atrm - удалить

at.deny & at.allow

---

### Telnet

[Что такое telnet](https://losst.ru/kak-polzovatsya-telnet)

Telnet – сетевая утилита, которая позволяет соединиться с удаленным портом любого компьютера и установить интерактивный канал связи, например, для передачи команд или получения информации. Можно сказать, что это универсальный браузер в терминале, который умеет работать со множеством сетевых протоколов.

### SSH

Сетевой протокол прикладного уровня, используется для удаленного управления операционными системами и для передачи файлов. Шифрует трафик, и по умолчанию использует 22 порт. Программные реализации SSH делятся на серверные и клиетские части. В основном в качестве сервера применяется OpenSSH, клиенты OpenSSH(UNIX), PuTTY.

> Для настройки используется конфигурационный файл /etc/ssh/sshd_config

## Процесс установки SSH соединения

[Алгоритм установления соединения в протоколе SSH](https://habr.com/ru/post/425637/)

1. Установка TCP-соединения
2. Открытие защищенного канала
   1. Обмен идентификационными данными
   2. Выбор алгоритмов: обмена ключами, шифрования, сжатия и т.п.
   3. Получение сессионного ключа шифрования
3. Аутентификация клиента
4. Уровень подключения

### Публичный и приватный ключ

[Read more](https://www.digitalocean.com/community/tutorials/ssh-ubuntu-18-04-ru)

Варианты копирования ключа

1. С помощью утилиты ssh-copy-id

2. Копирование публичного ключа через SSH 

   Если у вас есть пароль для входа по SSH, мы можем загрузить ключ вручную.

3. Копирование публичного ключа вручную

> Разрешения `authorized_keys` файла и директории родителькой должныть быть 700 для директории `.ssh/` и 600 для файла `authorized_keys` иначе работать не будет.
>
> [Read more](https://stackoverflow.com/questions/6377009/adding-public-key-to-ssh-authorized-keys-does-not-log-me-in-automatically)

---


### yum & rpm

RPM - RedHat Package Manager.
YUM - The Yellowdog Updater Modified.
EPEL - Extra Packages for Enterpise Linux

Difference between RPM and YUM

The biggest problem with the RPM is “Dependency Hell”. This problem occurs with
packages that depend on a lot of other packages, some of those packages also
depend on some other packages. You must install all dependencies for the program
to work correctly. RPM is unable to do this for you automatically. Note:
Although it can’t auto-install dependencies, RPM will still warn you about them.

YUM can check for all the dependencies of a package and install them for you
prior to installing the package that you wanted to install in the first place.
You only need to know the name of the package you want to install, you don’t
have to worry about whether the pre-requisite packages have been installed or
not.

Both tools can perform an install. RPM will let you install multiple versions
simultaneously while YUM will tell you that that package is already installed.
[More read about them](https://developer.ibm.com/tutorials/l-lpic1-102-5/)

How does yum know where to download packages from? The starting point is the
/etc/yum/repos.d/ directory, which usually contains several repo files. This is
the default location for repository information, but other location may be
specified in the YUM configuration file, normally /etc/yum.conf.

