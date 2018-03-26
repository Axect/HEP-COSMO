# HEP-COSMO Server Administrate

## 1. Admin
### - Mathematica

The license file of Mathematica is in `/home/probe/.Mathematica`
Thus if an user wants to use, then
```bash
sudo cp -r /home/probe/.Mathematica /home/[user]/
```

### - Fail2Ban

Administer can unban ip
```bash
fail2ban-client set sshd unbanip [ip Adress]
```

## 2. User
### - Python
If any user want to install python package, then should use virtualenv.

```bash
cd ~

# Default : python2
virtualenv [envname]
# If you want to use python3 then
virtualenv -p python3 [envname]

# Activate
. [envname]/bin/activate

# Install Package
pip install [package]

# Deactivate
deactivate
```

### - SSH Proxy

* Edit or make `~/.ssh/config`

* e.g. Hive :

```config
Host Hive
HostName 192.168.0.2
User [User_Name]
ProxyCommand ssh -W 192.168.0.2:22 [User_Name_2]@nexus.yonsei.ac.kr
```

* `[User_Name]` is your user name in Hive
* `[User_Name_2]` is your user name in nexus

### - SSH Port forwarding

```sh
ssh -N -f -L localhost:[Port_Num]:localhost:[Port_Num] [User_Name]@[HostName]
```

* `[Port_Num]` is port number which you want to use. (e.g. 8123)
* `[HostName]` is host name of server (e.g. `nexus.yonsei.ac.kr` or `Hive`)
* `[User_Name]` is your user name of server

### - Tensorflow (GPU Version)

```sh
nvidia-docker run -it -p [Port_Num]:8888 tensorflow/tensorflow:latest-gpu
```

* `[Port_Num]` should be 4 digits (Do not use 8888)
* If you finish your calculation, then plz shutdown jupyter server
