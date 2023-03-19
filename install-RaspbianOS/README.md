<div align="center"><img src="./src/raspian2.webp" alt="raspbian-logo" /></div>

---

# Install a RaspbianOS

1. To install RPI go to https://www.raspberrypi.com/software/ and download RPI Imager.

<div align="center"><img src="./src/imager.webp" alt="imager-photo" /></div>

2. Insert SD card into laptop and choose OS to install (you can also download OS directly from the same web page) and write SD card.
3. Insert SD card into Raspberry Pi, connect monitor, mouse and keyboard and turn it on.
4. Choose a keyboard layout and language of RaspbianOS, and click Next
5. Choose your username and password
6. Wait RPI to restart

- After restart your desktop looks like this
  <div align="center"><img src="./src/desktop-screenshot.png" alt="desktop-screenshot" /></div>

---

# SSH

You can check [raspbbery pi documentation](https://www.raspberrypi.com/documentation/computers/remote-access.html#setting-up-an-ssh-server) and enable ssh connection or type into terminal:

1. `sudo systemctl enable ssh`
2. `sudo systemctl start ssh`

- After enabling ssh you can ssh into your raspberry.
  <div align="center"><img src="./src/ssh-connection.png" alt="ssh-connection" /></div>

> You have successfully install Raspbian and enable SSH connection. If you want to SSH into raspberry outside your LAN network, check my another tutorial [port forwarding](https://github.com/mvisnjic/RPI-tutorials/tree/main/port-forwarding).
> Check my other tutorials: [RPI-tutorials](https://github.com/mvisnjic/RPI-tutorials#readme)
