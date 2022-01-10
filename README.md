# SSH Key keygen and ssh from Windows into Linux-server

## Create SSH Key

```
ssh-keygen
```

## Terminal will ask

```
Generating public/private rsa key pair.
Enter file in which to save the key (/home/<yourUsername>/.ssh/id_rsa):
```

## If default is Ok for you hit Enter to save key-pair into "/home/<yourUsername>/.ssh"
 the dot in ".ssh" is because it's a hidden folder

## Next you'll be promted to enter a passphrase

```
Enter passphrase (empty for no passphrase):
```

It is recommended to enter a password to prevent unauthorized usage of your ssh-key.

## After entering and confirming your passphrase the generated key looks like this

```
Your identification has been saved in /home/<yourUsername>/.ssh/id_rsa.
Your public key has been saved in /home/<yourUsername>/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:/qRoQhRcIBTw0B4KpTUyK6YepyL6RZ2CQrtWsaicCd6 <yourUsername>@581e349f764a
The key's randomart image is:
+---[RSA 2048]----+
| .o=+....        |
|+.*o+o .         |
|+X.=o o          |
|@.=.oo .         |
|=O ...o S        |
|o.oo . .         |
|.E+ . . . .      |
|oo . ... +       |
|=.. .o. . .      |
+----[SHA256]-----+

```

## To manage multiple keys you have to setup a SSH config file

create a file: "~/.ssh/config" and open it in your favorite editor.
Then you can config your key like this:

```
Host mygithub-account
    HostName githib.com
    User git
    IdentityFile ~/.ssh/id_rsa
    IdentitiesOnly yes
```
You can use it now like:

```
git clone git@mygithub-account:<yourusername>/yourrepo.git
```
## Before using the key you have to remove any other key from the active ssh-agent session

```
ssh-add -D
```

## Another usecase for ssh keys is to manage servers

For this example I'am running a linux virtual machine with Ubuntu, wich I have set up with the Windows Hyper-V Manager. On the virtual machine I have installed ssh with:

```
sudo apt-get install ssh
```
## And then start the service with:

```
sudo service ssh start
```
## You can then check the status:
```
sudo service ssh status

● ssh.service - OpenBSD Secure Shell server
 	Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
 	Active: active (running) since Mon 2022-01-10 13:28:26 CET; 7min ago
   	Docs: man:sshd(8)
         	man:sshd_config(5)
   Main PID: 682 (sshd)
  	Tasks: 1 (limit: 2231)
 	Memory: 2.4M
 	CGroup: /system.slice/ssh.service
         	└─682 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

Jan 10 13:28:26 stephan-Virtual-Machine systemd[1]: Starting OpenBSD Secure Shell server...
Jan 10 13:28:26 stephan-Virtual-Machine sshd[682]: Server listening on 0.0.0.0 port 22.
Jan 10 13:28:26 stephan-Virtual-Machine sshd[682]: Server listening on :: port 22.
Jan 10 13:28:26 stephan-Virtual-Machine systemd[1]: Started OpenBSD Secure Shell server.
```

## To find your servers IP type ip addr show

```
stephan@stephan-Virtual-Machine:~$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
	link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
	inet 127.0.0.1/8 scope host lo
   	valid_lft forever preferred_lft forever
	inet6 ::1/128 scope host
   	valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
	link/ether 00:15:5d:0a:0c:00 brd ff:ff:ff:ff:ff:ff
	inet 172.28.14.13/20 brd 172.28.15.255 scope global dynamic noprefixroute eth0
   	valid_lft 81936sec preferred_lft 81936sec
	inet6 fe80::95e3:e841:3939:73ab/64 scope link noprefixroute
   	valid_lft forever preferred_lft forever
```
## Then you are able to ssh from your Windows Powershell into your Ubuntu server like:

```
ssh <yourServerUsername>@172.28.14.13
```
and now you can work in your Powershell with Linux commands like:

```

mkdir htdocs
touch index.html
......
```
## More detailed information you'll find under [OpenSSH](https://www.openssh.com/)


### to be continued 😃


