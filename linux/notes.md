Активный режим мы отправляет ip и port серверу, и ждет пока сервер подключится к
нему

123.123.123.133:56795 > ftp 

ftp 123.123.123.123:56795  100.100.100.100:20

Пассивный режим, сервер отправляет нам ip адрес и номер порта

---

You may have noticed that there is a trailing slash (/) at the end of the first
argument in the above commands:

    rsync -a dir1/ dir2

This is necessary to mean “the contents of dir1”. The alternative, without the
trailing slash, would place dir1, including the directory, within dir2. This
would create a hierarchy that looks like:

~/dir2/dir1/[files]

Always double-check your arguments before executing an rsync command. 

---

## Rsync

How to sync with different port
rsync -avz -e "ssh -p $portNumber" user@remoteip:/path/to/files/ /local/path/

We can "pull" or "push" files to server or from the server. "pull" is used to
sync a remote directory to the local system. "push" is used to push directory
from a local to a remote system.

---












