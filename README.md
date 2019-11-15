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
- [Features](#features)
- [Contributing](#contributing)



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
Ansible is key, one must understand how it works, it is comprised of objects caller Roles, they are comprised of smaller objects called tasks, they are comprised of modules, those are likely to be Python modules that interact with the operating system the automation tool will by operating upon.

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/Ansible-Objects-Relations.jpeg?v=3&s=200" title="Main_Structure" alt="Main_Structure_LB_Webservers"></a>

Nginx is a very powerful webserver, aims at performance, its very sophisticated. Has multiple other uses, most popular is the an Application loadbalance, reverse proxy and an application server for programming languages such as Python, this is done through additioinal modules.

<a href="https://github.com/morawi-cg/al-ansible-nginx.git"><img src="readme_images/Load_balance_Options.jpeg?v=3&s=200" title="Main_Structure" alt="Main_Structure_LB_Webservers"></a>

## Usage
Activate the vagrant file, change directory to the repository, the file is called Vagrantfile, as long as your Computer's operating system can run Python, Ansible, VirtualBox and Vagrant), then you should be able to just run 'vagrant up'. This will generate the virtual machines. These type of machines are specially adapted to Vagrant. Packer can be used to transform them to images that can be used on cloud providers, this is why one can use this process as testing grounds. 

The vagrant part is not related or connected to Ansible components, ansible simply has roles, each role is assigned to a virtual machine, the idea its simpler to have roles independent per machine, this was a change will not need to be too impacting.

ansible-galaxy is used to create the 'Roles' it will create an empty structure of folders, these need to be filled, depending on how one wants to built the roles. The site.yml will be the central point to call the needed Roles. 

An example of the usage of the 'ansible-galaxy' is the code below. This was of automating the creation of a structure that represent an object has also been replicated on other automation tools such as Pupet. 

```
[root@localhost ansible]# ansible-galaxy init al-webcluster
- al-webcluster was created successfully
[root@localhost al-webcluster]# ansible-galaxy init al-loadbalancer
- al-loadbalancer was created successfully
[root@localhost al-webcluster]# ansible-galaxy init al-webserver01
- al-webserver01 was created successfully
[root@localhost al-webcluster]# ansible-galaxy init al-webserver02
- al-webserver02 was created successfully
```
## Documentation
There are excellent documentation on individual technologies involved. Leave me a note if more is needed.
## Tests
Its recommended to test units individually. Then combine in a larged structure.


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

