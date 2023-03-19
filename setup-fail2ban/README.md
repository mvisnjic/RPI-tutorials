<div align="center"><img src="https://www.fail2ban.org/fail2ban_logo.png" alt="fail2ban-logo" /></div>

# Setup fail2ban on RPI

Fail2ban is a software that attempts to block and ban bots and users who trying to login into your Raspberry Pi.

---

# Installing

1. `sudo apt-get install fail2ban`
2. Copy jail.conf into jail.local `sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`
3. Open jail.local in nano `sudo nano /etc/fail2ban/jail.local`
4. With Ctrl+W you can search for [sshd] and add some parameters
   <div align="center"><img src="./src/jail.local-screenshot.png" alt="jail.local-screenshot" /></div>   
   You can modify bantime and maxretry according to your needs.

5. Save changes and exit (Ctrl+x and y and hit enter)
6. `sudo service fail2ban restart`

- You can check `sudo fail2ban-client status sshd` and check banned IP addresses.
<div align="center"><img src="./src/status-sshd.png" alt="status-sshd" /></div>

---

- After 24hours
<div align="center"><img src="./src/status-sshd-2.png" alt="status-sshd-2" /></div>

> _This tutorial is based on [pimylifeup.com/raspberry-pi-fail2ban](https://pimylifeup.com/raspberry-pi-fail2ban/)._
> Check my other tutorials: [RPI-tutorials](https://github.com/mvisnjic/RPI-tutorials#readme)
