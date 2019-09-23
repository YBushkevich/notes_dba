## FTP

Активный режим мы отправляет ip и port серверу, и ждет пока сервер подключится к
нему.

Пассивный режим, сервер отправляет нам ip адрес и номер порта.

## How To Use Rsync to Sync with a Remote System 

[Link to read
more](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps)


Syncing to a remote system is trivial if you have SSH access to the remote
machine and rsync installed on both sides. If you need to set up SSH keys, click
here.

Once you have SSH access verified on between the two machines, you can sync the
dir1 folder from earlier to a remote computer by using this syntax (note that we
want to transfer the actual directory in this case, so we omit the trailing
slash):

    rsync -a ~/dir1 username@remote_host:destination_directory
    
This is called a “push” operation because it pushes a directory from the local
system to a remote system. The opposite operation is “pull”. It is used to sync
a remote directory to the local system. If the dir1 were on the remote system
instead of our local system, the syntax would be:

    rsync -a username@remote_host:/home/username/dir1 place_to_sync_on_local_machine

Like cp and similar tools, the source is always the first argument, and the
destination is always the second.

You may have noticed that there is a trailing slash (/) at the end of the first
argument in the above commands:

    rsync -a dir1/ dir2

This is necessary to mean “the contents of dir1”. The alternative, without the
trailing slash, would place dir1, including the directory, within dir2. This
would create a hierarchy that looks like:

    ~/dir2/dir1/[files]

Always double-check your arguments before executing an rsync command. 

How to sync with different port
rsync -avz -e "ssh -p $portNumber" user@remoteip:/path/to/files/ /local/path/

We can "pull" or "push" files to server or from the server. "pull" is used to
sync a remote directory to the local system. "push" is used to push directory
from a local to a remote system.














