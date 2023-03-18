# Port forwarding

![port-forwarding-diagram](/port-forwarding/port-forwarding-diagram.png)

In short port forwarding is a NAT application that redirects requests from one address and port to another while the packets are traversing a router or a firewall.

1. Go to your home gateway (192.168.1.1)
   ![port-mapping-screenshot](Screenshot%20from%202023-03-17%2022-16-50.png)
2. Go to port-forwarding page and add new port maping application SSH (port 22) to a raspberry pi
   ![port-mapping-screenshot](/port-forwarding/Screenshot%20from%202023-03-17%2022-12-19.png)
3. Check here https://www.yougetsignal.com/tools/open-ports/ if is port 22 opened. If it's opened you can SSH into your raspberry through IP address of network where raspberry is connected.

- You can buy a domain and configure it to point to your ip address of a Raspberry Pi. The problem is when a network provider change the ip address of a Raspberry Pi network. You need to set up a dynamic DNS which will update your IP to your domain provider. I'm using https://www.namecheap.com/ which has option to update your IP address a HTTP request.

# Dynamic DNS with namecheap.com

1. Log in into your namecheap account
2. Go to your domain
3. Go to advanced DNS and find dynamic DNS password
   ![dynamic-dns-password](Screenshot%20from%202023-03-17%2022-39-12.png)
4. SSH into raspberry and add cron job to update an IP address. `crontab -e`
5. `*/10 * * * * curl 'curl 'https://dynamicdns.park-your-domain.com/update?host[host]&domain=[domain_name]&password=[ddns_password]&ip=[your_ip]' > ~/logs/dynamicdns.log`
   - automatic updating your IP address every 10 minutes
   -

`*/10 * * * *` - "At every 10th minute"
`curl 'https://dynamicdns.park-your-domain.com/update?host[host]&domain=[domain_name]&password=[ddns_password]&ip=[your_ip]'` - HTTP request to update your IP address on Namecheap
`> ~/logs/dynamicdns.log` - save response

- If you open your ports a lot of bots are try to brute force your raspberry. You can check your auth.log in `/var/log/auth.log | grep 'Failed'` and you can see how bots trying to connect to your raspberry pi. You can configure google-authenticator to have more secured authentication and setup fail2ban to ban every IP that failed authentication.
  <br>
  `cat /var/log/auth.log | grep 'Failed'`
  ![failed-pass-logs](Screenshot%20from%202023-03-18%2011-01-40.png)

Check my tutorials to [setup a fail2ban](https://github.com/mvisnjic/RPI-tutorials/tree/main/setup-fail2ban) and [setup google authenticator](https://github.com/mvisnjic/RPI-tutorials/tree/main/setup-google-authenticator)
