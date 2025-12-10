# How to Customize WSL

## 1. Mount Windows Drive Letter on WSL File System
```bash
sudo mkdir -p /mnt/d
```
```bash
sudo mount -t drvfs D: /mnt/d
```

---
## 2. Port Forwarding from Windows
### 2.1. Display WSL IP Address
```bash
hostname -I
```
```
172.29.60.68 172.17.0.1
```

### 2.2. Configure Port Forwarding 
```
netsh.exe interface portproxy add v4tov4 listenport=25565 listenaddress=* connectport=25565 connectaddress=172.29.60.68
```

### 2.3. Confirm Port Forwarding Configuration
```
netsh.exe interface portproxy show all
```
```
Listen on ipv4: Connect to ipv4
Address         Port        Addres         Port
--------------- ----------  -------------- ----------
*               25565       172.29.60.68   25565
```

---
## 3. Connect USB Device from Windows
### 3.1. Install usbipd
```
winget install --interactive --exact dorssel.usbipd-win
```

### 3.2. Display USB Devices List
```
usbipd list
```
```
Connected:
BUSID  VID:PID    DEVICE                                                        STATE
2-1    18a5:0302  USB Flash Drive                                               Not shared
2-8    04f2:b7ba  Integrated Camera                                             Not shared
2-10   0bda:4853  Realtek Bluetooth Adapter                                     Not shared

Persisted:
GUID                                  DEVICE
```

### 3.3. Share the USB Device
```
usbipd bind --busid 2-1
```
```
usbipd list
```
```
Connected:
BUSID  VID:PID    DEVICE                                                        STATE
2-1    18a5:0302  USB Flash Drive                                               Shared
2-8    04f2:b7ba  Integrated Camera                                             Not shared
2-10   0bda:4853  Realtek Bluetooth Adapter                                     Not shared

Persisted:
GUID                                  DEVICE
```

### 3.4. Attach the USB Device to the WSL
```
usbipd attach --auto-attach --wsl --busid 2-1
```
```
usbipd: info: Using WSL distribution 'Ubuntu-24.04' to attach; the device will be available in all WSL 2 distributions.
usbipd: info: Loading vhci_hcd module.
usbipd: info: Detected networking mode 'nat'.
usbipd: info: Using IP address 172.29.48.1 to reach the host.
```
