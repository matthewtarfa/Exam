# DEPPLOYING AN ANSIBLE PLAYBOOK, THE OUTPUT OF SYSTEMCTL STATUS APACHE2 AFTER DEPLOYING THE PLAYBOOK AND A SCREENSHOT OF THE RENDERED PAGE. 
>Learning Tech isn't that hard it,s just not for the weak in mind!

--Matthew Tarfa


## To carry out this project we would need to install Ansible.

### **Install Ansible on your Host Machine on Vagrant**

```bash
$ sudo apt update
$ sudo apt install -y software-properties-common python-apt 
$ sudo apt install -y ansible
$ ansible --version
```


<br>

### **Creating Two Servers On Digital Ocean**

<br>


Creating a server on digital Ocean and SSh into it first of all you create a droplet 

<br>

![Droplet](droplet.png "oh yeah!")

<br>
You click on droplet and choose the different inputs of your choice like the version of Ubuntu you want to spin up the memory size the regin in which you want to spin it up.

<br>

![version](ubuntuversion.png "oh yeah!")

<br>

You then select ssh as a way to link your host machine to your sever, here you should have created your ssh key oh you host machine and copied it and placed it into your server to enable the coneection via port 22 by SSH.

below is the command to generate your ssh key on your host machine.

<br>

please note only the public key is to be copied and placed on your droplet.

```bash
ssh key-gen
```
<br>

![SSH](SSHtoserver.png "oh yeah!")

<br>

Before the final creation of the Server you should give your server a name that enables you easily identify them.Also you can indicate the number of servers you want to spin up.
<br>

![servername](nameserver.png "oh yeah!")

<br>

Now click on create droplets to create server.

<br>

![createdserver](serverscreated.png "oh yeah!")

so Two servers were created for this project.

<br>
ssh into the two servers

```bash
ssh root@139.59.173.218
```
<br>

you do this for both servers.

![SSHintoserver](sshintoserver.png "")


<br>

After the above is completed you go back your Host machine and create an Ansible directory.

<br>

```bash
sudo nano /etc/ansible/host

```
<br>

you nano into the ansible host to input the IP address of the server   server you intend to instale apache and move index.php file to. dont for get to give this a name on your host machine like you can se below [mattserver]

![etc](etcansiblehost.png "oh yeah!")

You create 2 files in the Ansible directory.

.yml file to create the ansible play book and the index.php

![files](indexandymlfile.png "oh yeah!")

<br>

Nano into the yml file with the below command to add your code for the play book
<br>

```bash
nano apacheplaybook.yml
```
![playbook](apacheplabookfile.png "")
![playbook2](apacheplabookfile2.png "oh yeah!")


<br>

Here is where you write all the instructions you want your playbook to manage and carry out

<br>

Nano into the index.php file

<br>

```bash
sudo nano index.php
```
![php](indexphp.png "")

<br>

Here you input the php instrction as given above.

<br>

Now before we go any futher lets ping ansible to ensure its working.

<br>




### **command**

```bash
ansible mattserver -m ping
```
![ping](ansible-mping.png "")


<br>

wow the ping worked our ansible is working.

<br>

Next we want to check our playbook to ensure our instructions are correctly inputed and will work

### **command**

```bash
ansible-playbook apacheplaybook.yml --check
```
![check](playbookcheck.png "")

<br>

Oh it worked awesome now we can execute the playbook.

<br>

### **command**

```bash
ansible-playbook apacheplaybook.yml
```
![execute](executeplaybook.png "")


<br>

Great playbook executed lets now see the out put of systemctl on our server.
<br>

**Command**

```bash
systemctl status apache2
```
![output](outputsysctl01.png "")

<br>

![output](outputsysctl02.png "")

<br>

so above displays apache is active on the 2 servers we created

<br>

We would now pick the ip address of each of ther servers and paste on our web browser and see what is rendared.

![output](outputip.png "")

![output](outputip2.png "")

<br>

wow it works both our servers are ready!

<br>

time to check our index.php
to get this we simply add slash index.php at the back of the ip on our browser.

![outphp](outputindexphp.png "")

<br>

**This Ends Our project**



