# Self-defense

After studying Linux actively for 2 months. I decided it was time to get some proper hands on experience, purchase a Raspberry Pi and set up my 
own personal VPN server at home. 

#### First steps
- After succesfully setting up my Ras-Pi out of the box and connecting it to my home network.
I ssh:d into it and downloaded the PiVPN software with the command `curl -L https://install.pivpn.io | bash`
    - <img width="984" alt="Screenshot 2025-04-18 at 12 38 10" src="https://github.com/user-attachments/assets/4ac0e8fd-85bd-4fe6-982e-83362c57eb95" />
    

#### What is PiVPN you might ask?
- "PiVPN is a set of shell scripts developed to easily turn your Raspberry Pi™ into a VPN server using two free, open-source protocols:
      - Wireguard
      - OpenVPN"
    - More information on their website <https://www.pivpn.io>
- The PiVPN then ran an installation wizard to configure some basic setting like IP-addressing, hostnames, unattended upgrades, firewall, ports etc.

#### Configurations
First, I needed a dynamic domain name for my Raspberry Pi, since my public IP address changes frequently. A dynamic domain provides a more permanent solution that the VPN client can consistently connect to. This eliminates the need to manually update the client profile each time the IP address changes.
- I created my dynamic domain name on <https://freedns.afraid.org> and set the mapping to `0.0.0.0`
- Back on my Ras-pi I downloaded `ddclient` to automatically update the dynamic DNS service with my current public IP address.
- I copied a template from the freedns.afraid.org website to use in my `ddclient` configuration file and put in my own credentials.
      - <img width="957" alt="Screenshot 2025-04-18 at 12 59 39" src="https://github.com/user-attachments/assets/59171e2f-fdfe-4cc4-9928-7792d6259170" />
- I then configured `ddclient` to run as a daemon. 
      - <img width="910" alt="Screenshot 2025-04-18 at 13 06 23" src="https://github.com/user-attachments/assets/78012a1e-83aa-4b2a-ad8a-cb019ee34656" />
- Now all I had to do was restart the service and voila, my dynamic domain name was setup. To make sure of this I navigated back to the freedns.afraid.org website and saw that the domain name mapping had changed from `0.0.0.0` to my public IP-address. 


