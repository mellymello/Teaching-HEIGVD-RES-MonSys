# Answers, Phase 1

```
# -- INSERT YOUR NAMES HERE -----
Calixte Melly
First name, Last name

We certify that we have done all the lab tasks and we have a running environment on our 
machine to prove it. We are ready to demonstrate it at any time and to explain the process
we have followed.
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 1 --

 C:\Users\Calixte\Documents\GitHub\Teaching-HEIGVD-RES-MonSys\monsys-web-infra> vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
> default: Box 'phusion-open-ubuntu-14.04-amd64' could not be found. Attempting to find and install...
  default: Box Provider: virtualbox
  default: Box Version: >= 0
> default: Adding box 'phusion-open-ubuntu-14.04-amd64' (v0) for provider: virtualbox
  default: Downloading: https://oss-binaries.phusionpassenger.com/vagrant/boxes/latest/ubuntu-14.04-amd64-vbox.box
  default: Progress: 100% (Rate: 2259k/s, Estimated time remaining: --:--:--)
> default: Successfully added box 'phusion-open-ubuntu-14.04-amd64' (v0) for 'virtualbox'!
> default: Importing base box 'phusion-open-ubuntu-14.04-amd64'...
> default: Matching MAC address for NAT networking...
> default: Setting the name of the VM: monsys-web-infra_default_1399532582418_97066
> default: Clearing any previously set forwarded ports...
> default: Clearing any previously set network interfaces...
> default: Preparing network interfaces based on configuration...
  default: Adapter 1: nat
  default: Adapter 2: hostonly
> default: Forwarding ports...
  default: 9090 => 8080 (adapter 1)
  default: 22 => 2222 (adapter 1)
> default: Booting VM...
> default: Waiting for machine to boot. This may take a few minutes...
  default: SSH address: 127.0.0.1:2222
  default: SSH username: vagrant
  default: SSH auth method: private key
  default: Warning: Connection timeout. Retrying...
> default: Machine booted and ready!
> default: Checking for guest additions in VM...
> default: Configuring and enabling network interfaces...
> default: Mounting shared folders...
  default: /vagrant => C:/Users/Calixte/Documents/GitHub/Teaching-HEIGVD-RES-MonSys/monsys-web-infra
> default: Running provisioner: shell...
  default: Running: inline script
> default: stdin: is not a tty
> default: Cleaning up Docker containers...
> default: /tmp/vagrant-shell: line 2: docker: command not found
> default: /tmp/vagrant-shell: line 3: docker: command not found
> default: /tmp/vagrant-shell: line 4: docker: command not found
> default: /tmp/vagrant-shell: line 5: docker: command not found
> default: /tmp/vagrant-shell: line 6: docker: command not found
> default: /tmp/vagrant-shell: line 7: docker: command not found
> default: /tmp/vagrant-shell: line 8: docker: command not found
> default: /tmp/vagrant-shell: line 9: docker: command not found
> default: Running provisioner: docker...
  default: Installing Docker (latest) onto machine...
  default: Configuring Docker to autostart containers...
> default: Building Docker images...
> default: -- Path: /vagrant/docker/rp-nginx
> default: -- Path: /vagrant/docker/web-apache
> default: -- Path: /vagrant/docker/app-nodejs
> default: Starting Docker containers...
> default: -- Container: rp-node
> default: -- Container: web-node-1
> default: -- Container: web-node-2
> default: -- Container: app-node

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 2 --
vagrant@ubuntu-14:~$ uname -a
Linux ubuntu-14 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 3 --
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
heig/app-nodejs     latest              3038a15648dc        12 minutes ago      398.9 MB
heig/web-apache     latest              164e67ff70ba        15 minutes ago      411.9 MB
heig/rp-nginx       latest              97d4d78bafb0        18 minutes ago      637.9 MB
dockerfile/ubuntu   latest              cbc81be8f75e        12 days ago         378.6 MB
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 4 --
CONTAINER ID        IMAGE                    COMMAND                CREATED             STATUS              PORTS
           NAMES
5e500e39d10e        heig/app-nodejs:latest   node /opt/server.js    28 seconds ago      Up 27 seconds       0.0.0.0:7070
->80/tcp   app-node
2469649f285c        heig/web-apache:latest   /usr/sbin/apache2ctl   28 seconds ago      Up 28 seconds       0.0.0.0:8082
->80/tcp   web-node-2
ee4e6a8d8a49        heig/web-apache:latest   /usr/sbin/apache2ctl   29 seconds ago      Up 29 seconds       0.0.0.0:8081
->80/tcp   web-node-1
2964da455198        heig/rp-nginx:latest     /opt/init.sh           30 seconds ago      Up 29 seconds       0.0.0.0:9090
->80/tcp   rp-node
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 5 --
Web-node-1
 "NetworkSettings": {
     "IPAddress": "172.17.0.3",
     "IPPrefixLen": 16,
     "Gateway": "172.17.42.1",
     "Bridge": "docker0",
     "PortMapping": null,
     "Ports": {
         "80/tcp": [
             {
                 "HostIp": "0.0.0.0",
                 "HostPort": "8081"
             }
         ]
     }
 },
 Web-node-2
  "NetworkSettings": {
     "IPAddress": "172.17.0.4",
     "IPPrefixLen": 16,
     "Gateway": "172.17.42.1",
     "Bridge": "docker0",
     "PortMapping": null,
     "Ports": {
         "80/tcp": [
             {
                 "HostIp": "0.0.0.0",
                 "HostPort": "8082"
             }
         ]
     }
 }
 
 rp-node
 "NetworkSettings": {
    "IPAddress": "172.17.0.2",
    "IPPrefixLen": 16,
    "Gateway": "172.17.42.1",
    "Bridge": "docker0",
    "PortMapping": null,
    "Ports": {
        "80/tcp": [
            {
                "HostIp": "0.0.0.0",
                "HostPort": "9090"
            }
        ]
    }
}

app-node

"NetworkSettings": {
    "IPAddress": "172.17.0.5",
    "IPPrefixLen": 16,
    "Gateway": "172.17.42.1",
    "Bridge": "docker0",
    "PortMapping": null,
    "Ports": {
        "80/tcp": [
            {
                "HostIp": "0.0.0.0",
                "HostPort": "7070"
            }
        ]
    }
}
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 6 --

Host (your laptop):
- IP address: H.H.H.H

Virtual Machine run by Virtual Box
- IP address: B.B.B.B
- PAT: packets arriving on H.H.H.H:PH are forwarded to B.B.B.B:PB

Docker Bridge
- IP address: DB.DB.DB.DB
- PAT: packets arriving on DB.DB.DB.DB:PB1 are forwarded to C1.C1.C1.C1:PC1
- PAT: packets arriving on DB.DB.DB.DB:PB2 are forwarded to C2.C2.C2.C2:PC2
- PAT: packets arriving on DB.DB.DB.DB:PB3 are forwarded to C3.C3.C3.C3:PC3
- PAT: packets arriving on DB.DB.DB.DB:PB4 are forwarded to C4.C4.C4.C4:PC4

Docker Container 1
- IP address: C1.C1.C1.C1

Docker Container 2
- IP address: C2.C2.C2.C2

Docker Container 3
- IP address: C3.C3.C3.C3

Docker Container 4
- IP address: C4.C4.C4.C4

# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 7 --

Which command did you type on the terminal to establish the connection?

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```

```
# -- YOUR ANSWER TO QUESTION 8 --

Which command did you type on the terminal to establish the connection?

What HTTP request did you type and send?

What HTTP response did you get?
# -------------------------------
```




