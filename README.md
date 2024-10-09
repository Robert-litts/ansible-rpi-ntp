## Ansible Playbook to Configure a Raspberry Pi NTP Server 

I've had a Raspberry Pi NTP server running for several years now, built using the below references. When my SD card recently broke, I decided I should automate the rebuild process using Ansible. This simple playbook documents the configuration steps found in the below two references. 

***These instructions assume you have followed the hardware setup from References 1 or 2 below.***

1. Flash [Raspberry Pi OS Lite](https://www.raspberrypi.com/software/operating-systems/) onto an SD card
2. Boot & enable SSH (preferably [key based authentication](https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server))
3. Run ``` sudo raspi-config``` and enable Serial Port (see Step 3 from Reference 1)
4. From your remote machine, ```git clone https://github.com/Robert-litts/ansible-rpi-ntp.git```
5. ```cd ansible-rpi-git``` 
6. Update ```hosts.ini``` to the IP address of your Raspberry Pi & customize any needed values in the ```ntp_server.yml``` file, particularly the chrony.conf section
7. Run ```ansible-playbook -i hosts.ini ntp_server.yml```

References:
1. [Network Profile](https://blog.networkprofile.org/gps-backed-local-ntp-server/)

2. [Austin's Nerdy Things](https://austinsnerdythings.com/2021/04/19/microsecond-accurate-ntp-with-a-raspberry-pi-and-pps-gps/)