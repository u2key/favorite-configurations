# How to Configure LDAP Client

## 1. Install Required Packages
```bash
sudo apt install libnss-ldapd libpam-ldapd ldap-utils nscd nslcd
```

### 1.1. Specify LDAP Server
```
ldap://ldapserver.example.local
```

### 1.2. Configure Authentication Method
- Name services to configure
  - [x] passwd
  - [x] group
  - [x] shadow
 
## 2. (If needed) Reconfigure Authentication Settings
```bash
sudo dpkg-reconfigure nslcd
```
```bash
sudo dpkg-reconfigure libnss-ldapd
```
