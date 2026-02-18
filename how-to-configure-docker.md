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

## 4. Sample: Docker Nginx Container
### 4.1. Pull Image
```
docker image pull ubuntu
```

### 4.2. Create Container
```
docker container run --network host -p 8080:80 --name momiji ubuntu
```

### 4.3. Display Container List
```
docker container ls -a
```

### 4.4. Open Container
```
docker start momiji
```
```
docker container exec -it momiji bash
```
