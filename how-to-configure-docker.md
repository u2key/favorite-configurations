# How to Configure Docker

## 1. Install Required Packages

```
sudo apt install docker.io
```

## 2. Change Root Directory

```
sudo vim /lib/systemd/system/docker.service
```
```
...
ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --data-root /home/ubuntu/docker/
...
```

## 3. Start Docker
```
sudo systemctl daemon-reload
```
```
sudo systemctl enable --now docker
```
