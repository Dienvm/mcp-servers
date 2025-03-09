# Command Denylist for Cursor YOLO Mode

This document outlines potentially dangerous commands that should be blocked in YOLO mode to protect sensitive information and prevent security breaches.

## System Commands

```bash
# File system operations that could be dangerous
rm -rf
rmdir
mkfs
dd
format
fdisk
mkfs.*

# System modification commands
sudo
su
passwd
chown
chmod
usermod
groupmod
visudo

# Network exposure commands
nc
netcat
nmap
tcpdump
wireshark
iptables
ufw

# Process/Service manipulation
kill
killall
service
systemctl
init
reboot
shutdown

# Shell access
bash
sh
zsh
csh
ksh

# Package management (to prevent unauthorized installations)
apt
apt-get
yum
dnf
brew
pip
npm install -g
gem install

# File viewing/editing of sensitive locations
cat /etc/passwd
cat /etc/shadow
vi /etc/*
nano /etc/*
less /etc/*
more /etc/*

# Environment and configuration access
env
printenv
set
export
source

# User information commands
who
w
last
finger
id

# File search/modification in sensitive areas
find / 
locate
updatedb
grep -r /

# Remote access
ssh
sftp
ftp
telnet
rsh
rlogin

## Git Security

# Commands that could expose git credentials
git config
git credential
git remote set-url

# Commands that could alter repository history
git push --force
git reset --hard
git clean -f
git rebase

## Cryptocurrency/Wallet Related

# Mining software
minerd
cgminer
bfgminer

# Wallet access
wallet
bitcoin-cli
geth
parity

## Cloud Credentials

# AWS
aws configure
aws sts
aws iam

# Google Cloud
gcloud auth
gcloud config
gcloud iam

# Azure
az login
az account
az role

## Database Access

# MySQL
mysql
mysqldump
mysqlshow

# PostgreSQL
psql
pg_dump
createdb

# MongoDB
mongo
mongodump
mongoexport

## Application Secrets

# Environment files
.env
.env.*
config.json
credentials.json
secret.*

# API keys and tokens
*_KEY
*_SECRET
*_TOKEN
*_PASSWORD

## Logging/Monitoring Prevention

# Log viewing/manipulation
tail -f
journalctl
dmesg
syslog
logrotate

## File Transfer

# Prevent data exfiltration
scp
rsync
rcp
curl -O
wget

## Memory/Process Inspection

# Memory dumping tools
gdb
lldb
strace
dtrace
ptrace

## Recommended Implementation

1. Regular Expression Patterns:
```regex
# Sensitive file patterns
\.(env|pem|key|crt|cer|p12|pfx|jks|keystore|truststore)$

# Sensitive command patterns
^(sudo|su)\s
.*password.*
.*secret.*
.*credential.*
```

2. Context-Aware Blocking:
- Commands accessing system directories (/etc/, /var/, /usr/)
- Commands with elevated privileges
- Commands accessing user data outside workspace
- Network exposure commands
- System modification commands

3. Additional Security Measures:
- Rate limiting command execution
- Logging suspicious patterns
- Alerting on blocked commands
- Workspace isolation
- Process sandboxing

## Usage

Implement these denylists in your security configuration:

```json
{
  "yolo_mode": {
    "command_denylist": [
      "^sudo",
      "^rm -rf",
      // ... add other patterns
    ],
    "file_patterns_denylist": [
      "\\.env$",
      "\\.pem$",
      // ... add other patterns
    ],
    "directory_denylist": [
      "/etc/",
      "/var/",
      // ... add other paths
    ]
  }
}
```

## Maintenance

- Regularly review and update the denylist
- Monitor security logs for new patterns
- Keep up with new security threats
- Test security measures regularly
- Document any changes or additions