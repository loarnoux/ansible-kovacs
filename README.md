# ansible-kovacs
Depot du cours ansible S8

Fin du test 01 avec succès ! 

<img width="1920" height="1200" alt="Capture d’écran du 2026-03-11 11-36-02" src="https://github.com/user-attachments/assets/57946a08-f4c0-48de-86d4-8a3a3ab11fc3" />
Test de ping :

<img width="1920" height="1200" alt="Capture d’écran du 2026-03-11 11-38-32" src="https://github.com/user-attachments/assets/aa8178b4-4514-4234-8873-19c55fed305f" />

<img width="1920" height="1200" alt="Capture d’écran du 2026-03-11 11-41-17" src="https://github.com/user-attachments/assets/c6fb3ff3-afc9-4791-bfc2-8d3ddf4d5878" />


<img width="1920" height="1200" alt="Capture d’écran du 2026-03-11 12-28-05" src="https://github.com/user-attachments/assets/e233cb98-08db-4ac7-a6e9-69ecbcdc1c0a" />

<img width="1920" height="1200" alt="Capture d’écran du 2026-03-12 08-59-13" src="https://github.com/user-attachments/assets/286ca18c-b1e7-43f0-b914-0ea8430429d1" />

<img width="1920" height="1200" alt="Capture d’écran du 2026-03-12 09-20-30" src="https://github.com/user-attachments/assets/21e6eda4-c3bb-4f3d-8248-53ae2a181d12" />
<img width="1920" height="1200" alt="Capture d’écran du 2026-03-12 09-35-27" src="https://github.com/user-attachments/assets/9567d45d-6295-467f-8281-44bd3cbc26d1" />

# Challenge 1
```
vagrant up ubuntu
```
```
vagrant ssh ubuntu
```
```
sudo apt update
```
```
sudo apt-cache search --names-only ansible
```
```
sudo apt install -y ansible
```
```
ansible --version```

```
~$ ansible --version
ansible 2.10.8
  config file = None
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.10.12 (main, Aug 15 2025, 14:32:43) [GCC 11.4.0]
```
```
exit
vagrant destroy -f ubuntu
```
<img width="902" height="664" alt="Capture d’écran du 2026-03-12 10-09-54" src="https://github.com/user-attachments/assets/e9e3333a-3c62-47d1-9550-eb1004312493" />

# Challenge 2

```
vagrant up ubuntu
vagrant ssh ubuntu
```
```
$ sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install -y ansible
```
```
vagrant@ubuntu:~$ ansible --version
ansible [core 2.17.14]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vagrant/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible
  python version = 3.10.12 (main, Aug 15 2025, 14:32:43) [GCC 11.4.0] (/usr/bin/python3)
  jinja version = 3.0.3
  libyaml = True
```
```
exit
vagrant destroy -f ubuntu
```
<img width="902" height="664" alt="Capture d’écran du 2026-03-12 10-40-14" src="https://github.com/user-attachments/assets/6a67bfa6-bfdf-40a2-9148-11ef90bc53a0" />


# Challenge 3

```
vagrant up rocky
vagrant ssh rocky
```
```
sudo dnf install -y python3-pip
python3 -m venv ~/.venv/ansible
source ~/.venv/ansible/bin/activate
pip install --upgrade pip
pip install ansible
```
```
(ansible) [vagrant@rocky ~]$ ansible --version
ansible [core 2.15.13]
  config file = None
  configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vagrant/.venv/ansible/lib64/python3.9/site-packages/ansible
  ansible collection location = /home/vagrant/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vagrant/.venv/ansible/bin/ansible
  python version = 3.9.21 (main, Aug 19 2025, 00:00:00) [GCC 11.5.0 20240719 (Red Hat 11.5.0-5)] (/home/vagrant/.venv/ansible/bin/python3)
  jinja version = 3.1.6
  libyaml = True
```
<img width="902" height="664" alt="Capture d’écran du 2026-03-12 10-53-31" src="https://github.com/user-attachments/assets/ebd97a27-a4ed-4cf3-a5ef-6e13e8c03127" />
```
exit
vagrant destroy -f rocky
```

#Atelier-03
```
vagrant up
vagrant ssh ansible
````
on modifie le fichier /etc/hosts
```
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
127.0.1.1 ansible ansible
127.0.0.1      localhost.localdomain  localhost
192.168.56.10  ansible.sandbox.lan    ansible
192.168.56.20  rocky.sandbox.lan      rocky
192.168.56.30  debian.sandbox.lan     debian
192.168.56.40  suse.sandbox.lan       suse


```
```
[vagrant@ansible ~]$ for HOST in rocky debian suse; do ping -c 1 -q $HOST; done
PING rocky.sandbox.lan (192.168.56.20) 56(84) bytes of data.

--- rocky.sandbox.lan ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.183/1.183/1.183/0.000 ms
PING debian.sandbox.lan (192.168.56.30) 56(84) bytes of data.

--- debian.sandbox.lan ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.284/1.284/1.284/0.000 ms
PING suse.sandbox.lan (192.168.56.40) 56(84) bytes of data.

--- suse.sandbox.lan ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.755/0.755/0.755/0.000 ms
```

# Atelier-03

```
vagrant up
vagrant ssh control
```

```
vagrant@control:~$ type ansible
ansible is /usr/bin/ansible
```
On modifie le fichier /etc/hosts

```
27.0.0.1 localhost
127.0.1.1 vagrant
192.168.56.10 control
192.168.56.20 target01
192.168.56.30 target02
192.168.56.40 target03

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
127.0.2.1 control control
```
On teste le ping sur les machines
```
vagrant@control:~$ for HOST in target01 target02 target03; do ping -c 1 -q $HOST; done
PING target01 (192.168.56.20) 56(84) bytes of data.

--- target01 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.739/1.739/1.739/0.000 ms
PING target02 (192.168.56.30) 56(84) bytes of data.

--- target02 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.786/0.786/0.786/0.000 ms
PING target03 (192.168.56.40) 56(84) bytes of data.

--- target03 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.782/0.782/0.782/0.000 ms
```
```
vagrant@control:~$ ssh-keyscan -t rsa target01 target02 target03 >> .ssh/known_hosts
# target01:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
# target02:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
# target03:22 SSH-2.0-OpenSSH_8.9p1 Ubuntu-3ubuntu0.13
```
```
vagrant@control:~$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/vagrant/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/vagrant/.ssh/id_rsa
Your public key has been saved in /home/vagrant/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:oT5SmvBkldDV4PRVq0uwFfa4YQKys39C4Sa13cP/u08 vagrant@control
The key's randomart image is:
+---[RSA 3072]----+
|    ....=o  +..  |
|     ..* o.o + . |
|      = = + = o  |
|     . * = O +   |
|  . o = S o B    |
|   = = =   . +   |
|    = o o . . . E|
|     . . o     o |
|               o*|
+----[SHA256]-----+
```

```
vagrant@control:~$ ssh-copy-id vagrant@target01
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/vagrant/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
vagrant@target01's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'vagrant@target01'"
and check to make sure that only the key(s) you wanted were added.

vagrant@control:~$ ssh-copy-id vagrant@target02
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/vagrant/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
vagrant@target02's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'vagrant@target02'"
and check to make sure that only the key(s) you wanted were added.

vagrant@control:~$ ssh-copy-id vagrant@target03
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/vagrant/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
vagrant@target03's password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'vagrant@target03'"
and check to make sure that only the key(s) you wanted were added.
```
on obtiens le résultats en faisait la commande ping
```
vagrant@control:~$ ansible all -i target01,target02,target03 -u vagrant -m ping
target01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target03 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
target02 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}

```
<img width="857" height="952" alt="Capture d’écran du 2026-03-12 12-17-12" src="https://github.com/user-attachments/assets/747474fb-a95e-4412-98bf-ba10c9d14308" />

