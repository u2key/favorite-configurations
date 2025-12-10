# How to Mount NFS Using AutoFS

## 1. Install Required Packages
```bash
sudo apt install autofs nfs-common
```

## 2. Modify `/etc/auto.master`
```bash
sudo vim /etc/auto.master
```
```
/nfs /etc/auto.nfs
```

## 3. Create `/etc/auto.nfs`
```bash
sudo vim /etc/auto.nfs
```
```
home -fstype=nfs4,rw,hard,intr,proto=tcp,port=2049 nfs-server:/export/home/
```

## 4. Reload AutoFS
```bash
sudo systemctl restart autofs
```
