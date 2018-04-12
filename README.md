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
HostName [IP_NUM]
User [User_Name]
ProxyCommand ssh -W [IP_NUM]:22 [User_Name_2]@nexus.yonsei.ac.kr
```

* `[IP_NUM]` is internal ip number. Now (2018/4/12: Hive is located at **192.168.0.2**)
* `[User_Name]` is your user name in Hive
* `[User_Name_2]` is your user name in nexus

```sh
ssh [Host]
```

### - SSH Port forwarding

```sh
ssh -N -f -L localhost:[Port_Num]:localhost:[Port_Num] [User_Name]@[Host]
```

* `[Port_Num]` is port number which you want to use. (e.g. 8123)
* `[Host]` is host name of server (e.g. `nexus.yonsei.ac.kr` or `Hive`)
* `[User_Name]` is your user name of server

### - Tensorflow (GPU Version)

```sh
nvidia-docker run --name [Container_Name] -it -p [Port_Num]:8888 tensorflow/tensorflow:latest-gpu
```

* `[Container_Name]` will be name of your container. Write your preference.
* `[Port_Num]` should be 4 digits (Do not use 8888)
* If you finish your calculation, then plz shutdown jupyter server
