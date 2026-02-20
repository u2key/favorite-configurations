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
sudo systemctl restart docker.service
```
```
sudo systemctl enable --now docker.service
```

## 4. Create systemd Enabled Container
### 4.1. Pull ubuntu Image
```
docker image pull ubuntu
```

### 4.2. Create Container
```
docker container run --privileged --network host --name momiji -it ubuntu /bin/bash
```

### 4.3. Open Container
```
docker start momiji
```
```
docker container exec -it momiji /bin/bash
```

### 4.4. Install systemd And init
```
apt update
```
```
apt install init systemd
```

### 4.5. Export momiji
```
docker container export momiji > momiji.docker.tar
```
```
docker container rm momiji
```

### 4.4. Import momiji
```
docker import - momiji:latest < momiji.docker.tar
```

### 4.5. Create Container
```
docker container run --privileged --network host --name momiji -it momiji /sbin/init
```

### 4.6. Open Container
```
docker start momiji
```
```
docker container exec -it momiji /bin/bash
```

## 5. Auto Start Container
```
docker update --restart=always momiji
```
