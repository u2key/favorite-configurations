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

### 4.4. Install required packages
```
apt update
```
```
apt install init libasound2t64 libdbus-1-3 libfontconfig1 libgl1 libglib2.0-0t64 libglx0 libnss3 libxcb-cursor0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-render-util0 libxcb-shape0 libxcb-xinerama0 libxcb-xkb1 libxext6 libxft2 libxi6 libxkbcommon-x11-0 libxtst6 locales ssh systemd
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
docker container run --privileged --mac-address 00:15:5d:f0:e8:50 -e DISPLAY=${DISPLAY} -v /tmp/.X11-unix:/tmp/.X11-unix --name momiji -it momiji /sbin/init
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
