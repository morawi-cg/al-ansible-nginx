<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/main_structure.jpeg?v=3&s=200" title="Main_Structure" alt="Main_Structure_LB_Webservers"></a>

***Below is the General diagram explaining the operation and components***

<a href="https://github.com/morawi-cg/al-ansible-nginx.git" ><img src="readme_images/VagrantAnsibleNginx01.jpeg?v=3&s=200" title="The_dynamic_Flow_of_automation_processes" alt="Main_Structure_LB_Webservers"></a>
> How to automate the creation of an Nginx load balanced pair of Nginx web servers  

> Deployable on a Linux host 

> include terms/tags that can be searched

**Key points**

- Compatibility , (Python versions and deprecated Ansible syntax)
- Different ways to install automation tools depending on the deployment targets 
- Know your Ansible! "ansible-playbook playbooks/PLAYBOOK_NAME.yml --flush-cache" known issue
- Advantages: virtual env offer flexibility: 'venv ,virtualenv' package for Python on Unix & Windows


- For more on these wonderful ~~badgers~~ badges, refer to <a href="https://github.com/morawi-cg/al-ansible-nginx" target="_blank">`VagrantAnsibleNginxLB`</a>.

*** ***


- To understand more about the system, glance at the `README`, *maybe* star it, or comment!
- It is constructed so that, people should understand instantly what this project is about based on this repo, the images and the description. Please leave a comment or a suggestion for future improvements.


> Tips

- Use Python virtual env, helps mitigate the delay of making big errors
- Use test inventory use the 'i' key to help 'ansible -i /etc/ansible/al-project webservers -m ping'
- Diagrams and images, a picture is a thousand word! (Many languages in one!)
- Use galaxy to create roles 'ansible-galaxy init al-webcluster-of-3'

> GIF Tools



## Table of Contents:

> The `README` has a lot of info, thus section headers might be nice to focuse on what the reader needs in specific.

- [Installation](#installation)
- [Setup](#setup)
- [Features](#features)
- [Usage](#usage)
- [Contributing](#contributing)
- [Documentation](#documentation)
- [Testing](#tests)





---

## Example  remote ssh setup for vs code:
   <p> some people may wish to use vscode, now almost a defacto code editor, it has a rather unique feature, </p>
   <p> this is rather neat for a free editor. Below is an example of setting it up to edit on remote host.</p>

   ``` 
      [
       {
         "hostname": "morawi-deployment01",
         "host": "192.168.1.107",
         "port": 22,
         "user": "engineer",
         "key": "/Users/mrawi/.ssh/id_rsa.pub "
       }
      ]
   ```   
 

```javascript
// code away!


```

---

## Installation

- All the images are based upon the vagrant image of Ubuntu specified in the requirements: 
   `https://app.vagrantup.com/ubuntu/boxes/bionic64`
- In principle any machine (Linux,Mac, Windows[10]) should be able to build the structure, components
  required will include Vagrant,Virtual Box, Ansible, Ansible dependencies in the form of Python libraries.
  some Ansible functionality may not be fully workable on windows yet! Need to be checked.
### Vagrant File
- Vagrant file should include the syntax required to pull machine images `https://app.vagrantup.com/ubuntu/boxes/bionic64`

### Setup

- Check that virtual box is installed, operational and tested manually via starting a vm:
- Install vagrant and ansible, refer to the help below

```shell
$ brew update
$ brew install ansible vagrant
# Or in the case of Linux RHEL:
$ sudo dnf -y update
$ sudo dnf -y install ansible vagrant
# Or in the case of Linux Debian/Ubuntu:
$ sudo apt -y update
$ sudo apt -y install ansible vagrant

# Ansible can be installed via python pip, less dependencies and this is more portable
```

> now install Python Pip and bower packages

On Ubuntu/Debian
```shell
$ sudo apt-get update
$ sudo apt install python3-pip
$ sudo python -m pip install ansible
```
One is advised to use Python3 and its components, 3.6 tends to be the most stable and compatible. Python3 will be retired soon

On RHEL/Centos/Fedora
```shell

$ sudo yum -y update
$ sudo su -
$ subscription-manager repos --enable rhel-7-server-optional-rpms  --enable rhel-server-rhscl-7-rpms
$ yum -y install @development
$ yum -y install rh-python36
 
$ yum -y install rh-python36-numpy  rh-python36-scipy rh-python36-python-tools rh-python36-python-six 
```
- For all the possible languages that support syntax highlithing on GitHub (which is basically all of them), refer <a href="https://github.com/github/linguist/blob/master/lib/linguist/languages.yml" target="_blank">here</a>.


---

## Features
Ansible is key, one must understand how it works, it is comprised of objects caller Roles, they are comprised of smaller objects called tasks, which are comprised of modules, those are likely to be Python modules that interact with the operating system the automation tool will by operating upon.

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/Ansible-Objects-Relations.jpeg?v=3&s=200" title="Main_Structure" alt="Main_Structure_LB_Webservers"></a>

Nginx is a very powerful webserver, aims at performance, its very sophisticated. Has multiple other uses, most popular is the an Application loadbalance, reverse proxy and an application server for programming languages such as Python, this is done through additioinal modules.

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/Load_balance_Options.jpeg?v=3&s=200" title="Main_Structure" alt="Main_Structure_LB_Webservers"></a>

## Usage

Access to vagrant boxes via ssh is best serverd from within the folder/repo-folder that they where initiated from. This is to keep matters simple, so that one will not need to start copying keys accross and deal with more complex authenticaiton issues. The ".vagrant" folder is where the "private" key is used to authenticate the access to the vagrant boxes.

```
drwxr-xr-x 8 root root  4096 Nov 17 02:33 .
drwxr-xr-x 7 root root  4096 Nov 16 14:59 ..
drwxr-xr-x 2 root root  4096 Nov 17 01:00 ansible_code
-rw-r--r-- 1 root root  6148 Nov 14 12:06 .DS_Store
drwxr-xr-x 8 root root  4096 Nov 14 12:06 .git
-rw-r--r-- 1 root root    12 Nov 14 12:06 .gitignore
-rw-r--r-- 1 root root   782 Nov 17 02:26 hosts
-rw-r--r-- 1 root root   537 Nov 16 20:47 oldhosts
drwxr-xr-x 2 root root  4096 Nov 14 12:06 readme_images
-rw-r--r-- 1 root root  5771 Nov 14 12:06 README.md
drwxr-xr-x 5 root root  4096 Nov 17 02:27 roles
-rw-r--r-- 1 root root   453 Nov 17 02:33 site.yml
drwxr-xr-x 2 root root  4096 Nov 17 00:13 templates
-rw-r--r-- 1 root root 12288 Nov 14 13:30 .test.swp
drwxr-xr-x 4 root root  4096 Nov 14 14:04 .vagrant
-rw-r--r-- 1 root root  1477 Nov 14 16:13 Vagrantfile

```

Activate the vagrant file, change directory to the repository, the file is called Vagrantfile, as long as your Computer's operating system can run Python, Ansible, VirtualBox and Vagrant), then you should be able to just run 'vagrant up'. This will generate the virtual machine(s),dependind on what has been specified. These type of machines are specially adapted to Vagrant. Packer can be used to transform them to images that can be used on cloud providers, this is why one can use this process as testing grounds. 

The vagrant part is not related or connected to Ansible components, ansible simply has roles, each role is assigned to a virtual machine, the idea its simpler to have roles independent per machine, this was a change will not need to be too impacting.

ansible-galaxy is used to create the 'Roles' it will create an empty structure of folders, these need to be filled, depending on how one wants to built the roles. The site.yml will be the central point to call the needed Roles. 

An example of the usage of the 'ansible-galaxy' is the code below. This was of automating the creation of a structure that represent an object has also been replicated on other automation tools such as Puppet.

There are folders that are used for reference only, in the evolutionary process of creating this code they where stepping stones and an early idea of a simpler strucrture. These folders are 'ansible_code' and 'templates', 'DS_Store' is a product of updating some Python components. The server the code was built was running Linux Fedora 30 64 bit, the vagrant machines are Ubuntu/Debian 18.04 64 bit.




```
[root@localhost ansible]# ansible-galaxy init role-al-webcluster
- al-webcluster was created successfully
[root@localhost al-webcluster]# ansible-galaxy init role-al-loadbalancer
- al-loadbalancer was created successfully
[root@localhost al-webcluster]# ansible-galaxy init role-al-webserver01
- al-webserver01 was created successfully
[root@localhost al-webcluster]# ansible-galaxy init role-al-webserver02
- al-webserver02 was created successfully
```

Using Ansible-Galaxy is the new way, Puppet another similar tool uses PDK, if you ever used it this concept is fairly similar to that of Pupper-PDK. ansible galaxy will create the structure that you can then fill in with the needed/required files, (don't need to populate every folder if you don't require it).
Below is a diagram that could help explain the structure a bit better:

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/Roles_structure.jpeg?v=3&s=200" title="Ansible_Structures" alt="Repository_Roles_Structure"></a>

## Load balancer
Upon tryinf to read about how to turn the opensouce nginx into an http loadbalancer is was preceived to be easy, the location of where this file was is to be dropped was a bit of a confusion point, the conclusion was after testing '/etc/nginx/conf.d/'. The file 'lb_nginx.conf' has a small picularity that needs to be highlighted
```
#http {
    upstream backend {
        least_conn;
        server webserver01.al.local:80;
        server webserver02.al.local:80;

    }

    server {
        listen 80;
        #server_name al.local;
        location / {
            proxy_pass http://backend;
        }
    }
#}
```
Most documentaion neglect the fact that is should never conflict with the main nginx config file, based in '/etc/nginx/nginx.conf' . Hence you see the #http stubs commented out, the error that was picked up by nginx logs or 'journalctl -xe' wasn't descriptive engough. so arrived it conclusion by logic.

This is how the main file '/etc/nginx/nginx.conf' would need to look like:

```
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
        worker_connections 768;
        # multi_accept on;
}

http {
#
#       ##
#       # Basic Settings
#       ##
#
#       sendfile on;
#       tcp_nopush on;
#       tcp_nodelay on;
#       keepalive_timeout 65;
#       types_hash_max_size 2048;
#       # server_tokens off;
#
#       # server_names_hash_bucket_size 64;
#       # server_name_in_redirect off;
#
        include /etc/nginx/mime.types;
        default_type application/octet-stream;
#
#       ##
#       # SSL Settings
#       ##
#
#       ssl_protocols TLSv1 TLSv1.1 TLSv1.2; # Dropping SSLv3, ref: POODLE
#       ssl_prefer_server_ciphers on;
#
#       ##
#       # Logging Settings
#       ##
#
        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;
#
#       ##
#       # Gzip Settings
#       ##
#
        gzip on;
#
        # gzip_vary on;
        # gzip_proxied any;
        # gzip_comp_level 6;
        # gzip_buffers 16 8k;
        # gzip_http_version 1.1;
        # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

        ##
        # Virtual Host Configs
        ##

        include /etc/nginx/conf.d/*.conf;
        include /etc/nginx/sites-enabled/*;
}


#mail {
#       # See sample authentication script at:
#       # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
#
#       # auth_http localhost/auth.php;
#       # pop3_capabilities "TOP" "USER";
#       # imap_capabilities "IMAP4rev1" "UIDPLUS";
#
#       server {
#               listen     localhost:110;
#               protocol   pop3;
#               proxy      on;
#       }
#
#       server {
#               listen     localhost:143;
#               protocol   imap;
#               proxy      on;
#       }
#}
                                                           85,2          Bot
                                                           64,0-1        73%


```
## Documentation
There are excellent documentation on individual technologies involved. Leave me a note if more is needed.
## Tests
Its recommended to test units individually. Then combine in a larged structure.
## A - Hosts file
During the testing I try to cause less disruption to the main environment. One of the most resommended measures is to keep the repo encapsulated separately with all its required dependencies in. 

Using add hock commands makes it very simple to test small components. I recommended doing so, its also good for learning more about components you don't necessarily now well. Don't pollute the main ansible setup but point it to your enclosed experiment repository, via the '-i' key for inventory so one can test the repo separately before approving it. 
one of the major sticky points was the 'hosts' files. The file contain system-descriptive details of the environment's hosts This file is like a dns and auth combined, for it to work it needs to follow the format below

```
[webservers]
webserver01.al.local ansible_ssh_host=10.0.0.14 ansible_connection=ssh ansible_user=vagrant ansible_pass=vagrant ansible_ssh_private_key_file=.vagrant/machines/webserver01.al.local/virtualbox/private_key ansible_become=yes ansible_become_user=root
webserver02.al.local ansible_ssh_host=10.0.0.15 ansible_connection=ssh ansible_user=vagrant ansible_pass=vagrant ansible_ssh_private_key_file=.vagrant/machines/webserver02.al.local/virtualbox/private_key ansible_become=yes ansible_become_user=root


[loadbalancers]
loadbalancer.al.local ansible_ssh_host=10.0.0.13 ansible_connection=ssh ansible_user=vagrant ansible_pass=vagrant ansible_ssh_private_key_file=.vagrant/machines/loadbalancer.al.local/virtualbox/private_key ansible_become=yes ansible_become_user=root

```
NOTE: "ansible_connection=local" is key to element to make note of, for this file to succeed  

## B - Communication with your instance(s)
Its important to ensure that there is full communication with the instances you have created. This will determine the success of the automation tasks. On a vagrant setup like this one authentication used by the communication will rely on "user_name, Password". This would be acceptable for testing purposes, this should not be the case for production or commercial deployments. Security is key thus its prudent to use tools such as "Ansible_Vault", "shared_keys"/renewable through a security policy, two factor authentication for general system access. There are more to list but for the purpose of this publication this should act as a serious note.
## C - Ad-hock commands
A good way of testing the communication with the instances, also from time to time testing components of the deployment that migh be sending errors or generally validating code output.
Example below

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/ansible_ad_hock_commands.jpeg?v=3&s=200" title="ad-hock-commands" alt="Ansible Add hock commands"></a> 

## D - Expand access rights with the become command/key
One must be a privileged user on the host that is hosting the vagrant boxes. The command below is example

```
ansible -i ansible_code/hosts --extra-vars "ansible_become_user=vagrant ansible_become_pass=vagrant" webservers -m  shell -a "ls -la  /root"

```
## E - Try more options with privileged access
Try more options, as an advice, for example manipulate files and access root folder, to ensure that the privileged access is fully working

```
ansible -i ansible_code/hosts --extra-vars "ansible_become_user=vagrant ansible_become_pass=vagrant" webservers -m  shell -a "rm -f /var/log/vbox-setup.log.1"

```
---

## Contributing

> To Contribute, please leave a comment and we can arrange that 

### Step 1

- **Option 1**
    - 🍴 Fork this repo!

- **Option 2**
    - 👯 Clone this repo to your local machine using `https://github.com/morawi-cg/al-ansible-nginx.git`

### Step 2

- **HACK AWAY!** 🔨🔨🔨

### Step 3

- 🔃 Create a new pull request using <a href="https://github.com/morawi-cg/al-ansible-nginx.git" target="_blank">`https://github.com/morawi-cg/al-ansible-nginx.git`</a>.
If you wish to manipulate the code please post to your own repo and change there, I will try to implement requests here but for speed its best to do at your own repo.

---

## FAQ


    - No problem! Leave me a comment and I will try to update as soon as possible.

---

## Support

> ignore error "dpkg-preconfigure: unable to re-open stdin: No such file or directory" it was highlighted in vagrant groups. 
Reach out to me at one of the following places!

- github at <a href="https://github.com/morawi-cg/al-ansible-nginx.git" target="_blank">`https://github.com/morawi-cg/al-ansible-nginx.git`</a>
- Comment section at <a href="https://github.com/morawi-cg/al-ansible-nginx.git" target="_blank">`@github.com`</a>
- I will insert more social links here.

---




---

