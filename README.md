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

