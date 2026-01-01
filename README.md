This guide walks through setting up a **Minecraft Java Edition server** on a fresh Ubuntu install using **PaperMC** for best performance and plugin support.

Tested on:
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS

## 1. Update the System

Always start by updating the OS.

```
sudo apt update && sudo apt upgrade -y
sudo reboot
```
Install OpenJDK 17:

```
sudo apt install openjdk-17-jre-headless -y

java -version
```

Expected output should show Java 17.

Create a Dedicated Minecraft User (Recommended)

This improves security and organization.

```
sudo adduser minecraft
sudo usermod -aG sudo minecraft
```

Switch to the new user:

```
su - minecraft
```

Create the Server Directory

```
mkdir ~/minecraft
cd ~/minecraft
```

Download the Minecraft Server (PaperMC)

Paper provides better performance and optimization than Vanilla.

Visit:
https://papermc.io/downloads

Download the latest Paper server .jar:

```
wget https://api.papermc.io/v2/projects/paper/versions/1.21.1/builds/XXX/downloads/paper-1.21.1-XXX.jar
```

Rename for simplicity:
```
mv paper-*.jar server.jar
```
Accept the EULA

Run the server once to generate required files:
```
java -jar server.jar
```

Edit the EULA file:
```nano eula.txt```

Change:
```eula=false```

To:
```eula=true```

Save and exit.

Create a Startup Script

```
nano start.sh
```

Paste the following (adjust RAM values as needed):
```
#!/bin/bash
java -Xms2G -Xmx4G -jar server.jar nogui
```

Make the script executable:
```
chmod +x start.sh
```

Start the server:
```
./start.sh
```

