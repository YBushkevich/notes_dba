## Переменные окружения

1. Локальные переменные окружения
2. Пользовательские переменные окружения
3. Системные переменные окружения

### Конфигурационные файлы переменных окружения

1. .bashrc
2. .bash_profile
3. /etc/environment
4. /etc/bash.bashrc
5. /etc/profile

/etc/profile = .bash_profile
/etc/bashrc = .bashrc

[Difference between Login Shell and Non-Login Shell](https://unix.stackexchange.com/questions/38175/difference-between-login-shell-and-non-login-shell)

[What's the difference between /sbin/nologin and /bin/false](https://unix.stackexchange.com/questions/10852/whats-the-difference-between-sbin-nologin-and-bin-false)

 /sbin/nologin => account currently not available

/bin/false => just immediately logged out

[Разница между login shell & non login shell](https://zalinux.ru/?p=3117)

**Login shell (оболочка с входом)**

	1. Процесс входа вызывает /etc/profile
 	2. /etc/profile/ вызывает скрипты в /etc/profile.d
 	3. Процесс входа вызывает ~/.bash_profile
 	4. ~/.bash_profile вызывает ~/.bashrc
 	5. ~/.bashrc вызывает /etc/bashrc

**Non login shell (оболочка без входа)**

	1. Процесс без входа (оболочка) вызывает ~/.bashrc
 	2. ~/.bashrc вызывает /etc/bashrc
 	3. /etc/bashrc вызывает скрипты в /etc/profile.d

   

   