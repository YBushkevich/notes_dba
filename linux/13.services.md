# 13. Стандартные сервисы (telnet, ssh, scp, rsync). Публичный и приватный ключ.

Процесс установки соединения, VNC, screen, NFS, SMB, yum, rpm.

tmux > screen

## yum & rpm

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

