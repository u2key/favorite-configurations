# How to Customize Minecraft

## 1. Install Neoforge
## 1.1. Download neoforge-installer.jar
```bash
wget "https://maven.neoforged.net/releases/net/neoforged/neoforge/26.1.2.20-beta/neoforge-26.1.2.20-beta-installer.jar" -O neoforge-26.1.2-installer.jar
```

## 1.2. Run neoforge-installer.jar
```bash
java -jar neoforge-26.1.2-installer.jar
```

## 2. Install Solas Shader
### 2.1. Download sodium.jar
```bash
wget "https://cdn.modrinth.com/data/AANobbMI/versions/Fg5Mk6Y3/sodium-neoforge-0.8.9%2Bmc26.1.1.jar" -O sodium-26.1.2.jar
```

### 2.2. Download iris.jar
```bash
wget "https://mediafilez.forgecdn.net/files/7867/946/iris-neoforge-1.10.9%2Bmc26.1.1.jar" -O iris-26.1.2.jar
```

### 2.3. Download Solas Shader
```bash
wget "https://mediafilez.forgecdn.net/files/7828/740/Solas%20Shader%20V3.5.zip" -O solas-shader-26.1.2.zip
```

### 2.4. Move jar files to .minecraft folder
```bash
cp sodium-26.1.2.jar iris-26.1.2.jar  ~/.minecraft/mods
```
```bash
cp solas-shader-26.1.2.zip ~/.minecraft/shaderpacks
```
