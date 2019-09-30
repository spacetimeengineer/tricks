Bash Tricks
===========

locate: Description: Lists all files with permission that contain string.
        
    $ locate <String>

    $ locate -i <String> | less

    $ locate -i -n <QuantityOfListItems> <String>
    
Example:

    $ locate <String>

    $ locate -i <String> | less

    $ locate -i -n <QuantityOfListItems> <String>      
    
grep:
        
    # Lists highlighted instances of <String> within <File> in a cat type format.
    $ grep <String> <File>

    # Lists highlighted instances of <String> within multiple files in a cat type format.
    $ grep <String> *

    # This searches for any occurence of "string" in /path.
    $ grep -rl "string" /path
        

find: Lists all files in directory with <StringWithinFileName> contained in it's file name.

    # Lists all files in directory with <StringWithinFileName> contained in it's file name.
    $ find -name "*<StringWithinFileName>*"
      
      


Git management
==============

Create a new repository on GitHub. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub. Open Terminal and change the current working directory to your local project.
Initialize the local directory as a Git repository.

    $ git init


Add the files in your new local repository. This stages them for the first commit.

    $ git add .

Adds the files in the local repository and stages them for commit. To unstage a file, use 'git reset HEAD YOUR-FILE'. Commit the files that you've staged in your local repository.

    $ git commit -m "First commit"
    

Commits the tracked changes and prepares them to be pushed to a remote repository. To remove this commit and modify the file, use 'git reset --soft HEAD~1' and commit and add the file again. At the top of your GitHub repository's Quick Setup page, click  to copy the remote repository URL. In Terminal, add the URL for the remote repository where your local repository will be pushed.

    $ git remote add origin <remote repository url>

Sets the new remote.

    $ git remote -v

Verifies the new remote URL. Push the changes in your local repository to GitHub.

    $ git push -u origin master

Pushes the changes in your local repository up to the remote repository you specified as the origin

Dockerhub Managment
===================

Hard Drive Managment
====================
 
    1.) List all devices.
        
        $ lsblk

    2.) 2. Create a mount point :

        $ sudo  mkdir /media/usb

    3.) Mount!

        sudo mount /dev/sdb1 /media/usb

    4.) Copy

        cp -a /home/android/Testproject/ /media/usb/ 


Common DockerHub Repository Managment Commands

Name: Michael.C Ryan
Date: Thursday, April 27 2017


1.) Logging into your Dockerhub account. This is required if you want to push images to a repository.
    
    Command:
    $ sudo docker login --username=<DockerhubAccount> --email=<DockerHub Email>

    Example:
    $ sudo docker login --username=mriotimpactlabs --email=mr@iotimpactlabs.com
    
    stdout:
    Flag --email has been deprecated, will be removed in 17.06.
    Password: **docker*******
    Login Succeeded




2.) Suppose you have a container which you modified. If you wish to create a new image from it.

    Command:
    $ sudo docker commit <containerID> <Repository>:<Tag>

    Example:
    $ docker commit c3f279d17e0a  svendowideit/testimage:version3
    
    stdout:
    f5283438590d
    
    Command:
    $ docker images
    
    stdout:
    REPOSITORY               TAG        ID             CREATED          SIZE
    svendowideit/testimage   version3   f5283438590d   16 seconds ago   335.7 MB


    Technical Notes: 
    
    1.) New images will be located in your local image bank. You can find them by running $ docker images




3.) Suppose you want to push your new image to a repository on your DockerHub account:

    Command
    $ docker tag <imageID> <Repository>:<Tag>

    Example
    $ docker tag 7h8de2n5 spacetimeengineer/gmat:latest

    Command
    $ sudo docker push <imageID> <Repository>:<Tag>
    
    Example
    $ sudo docker push spacetimeengineer/gmat:latest

    stdout:
    [sudo] password for spacetimeengineer: 
    The push refers to a repository [docker.io/mriotimpactlabs/weewx-newmountain-nm150]
    c39628e5580e: Layer already exists 
    2bffca1b4f64: Layer already exists 
    31cf9754690f: Layer already exists 
    3bef87fe7c3b: Layer already exists 
    56827159aa8b: Layer already exists 
    440e02c3dcde: Layer already exists 
    29660d0e5bb2: Layer already exists 
    85782553e37a: Layer already exists 
    745f5be9952c: Layer already exists 
    latest: digest: sha256:b2637b08e886f68a29640f7ee278fb2641822f4ff44ee76eec0527509ded0995 size: 2192




4.) Suppose you wanted to tag an image with a timestamp or a most recent indicator.

    Command:
    $ docker tag <imageID> <Repository>:<Tag>

    Example:
    $ docker tag 7d9495d03763 mriotimpactlabs/weexw-newmountain-nm150:latest
    
    stdout:
    No output
    
    Technical Notes: 
    
    1.) Tags are great for time stamping. 
    
    2.) It is standard practice to tag an image as "latest" if it is the most recent.




5.) Suppose you wanted to pull an image from some repository.

    Command:
    $ docker pull <Repository>:<Tag>

    Example:
    $ docker pull mriotimpactlabs/weewx-newmountain-nm150:latest

    stdout:
    Using default tag: latest
    latest: Pulling from mriotimpactlabs/weewx-newmountain-nm150:latest
    d54efb8db41d: Pull complete 
    f8b845f45a87: Pull complete 
    e8db7bf7c39f: Pull complete 
    9654c40e9079: Pull complete 
    6d9ef359eaaa: Pull complete 
    8f08d69bea92: Pull complete 
    8290b19e2c0f: Pull complete 
    08fdfae9c106: Pull complete 
    5b7cd807f2cd: Pull complete 
    Digest: sha256:b2637b08e886f68a29640f7ee278fb2641822f4ff44ee76eec0527509ded0995
    Status: Downloaded newer image for mriotimpactlabs/weewx-newmountain-nm150:latest


Configuration Document: Installing and testing Mosquitto MQTT broker and clients on linux.
Maintatiner: Michael.C Ryan


1.) Install mosquitto-clients

    $ apt-get install mosquitto-clients.

2.) Test publishing.

    $ mosquitto_pub -h <broker> -m <message> -t <topic>
    
    Example:
    
    mosquitto_pub -h iot.eclipse.org -m "HELLO WORLD" -t testing/sensor/luminosity
 
3.) Test subscribing.

    $ mosquitto_sub -h <broker> -t <topic>
    
    Example:
    
    mosquitto_sub -h iot.eclipse.org -t testing/sensor/luminosity

Pip Notes
=========

        479  pip3 install twine
        480  pip3 install --upgrade pip
        481  pip3 install twine
        482  pip3 install -U setuptools wheel
        483  cd
        484  cd Desktop/spacetimeengine
        485  ls
        486  python setup.py sdist
        487  python3 setup.py sdist
        488  cd
        489  cd Desktop/spacetimeengine
        490  ls
        491  twine upload --repository-url https://test.pypi.org/legacy/ dist/*
        492  twine upload dist/*
        494  pwd
        495  twine upload --repository pypi dist/*
        496  pip install -i https://upload.pypi.org/legacy/ spacetimeengine
        497  twine upload --repository pypi dist/*
        498  twine upload --repository https://upload.pypi.org/legacy/ dist/*
        499  twine upload --repository https://upload.pypi.org/legacy/ dist/*
        500  twine upload --repository pypi dist/*



        python setup.py sdist bdist_wheel
        twine upload dist/*

Prerequisites

    1.) You must have Ubuntu-Core-16 installed on your gateway.


Procedure


1.) Install network tools.

    $ sudo snap install docker
    
    $ snap install network-manager
    
    $ snap install modem-manager
    
    $ snap install wifi-ap 


3.) Check connection status:

    $ systemctl status snap.network-manager.networkmanager


4.) List wifi devices or connections.  

    $ network-manager.nmcli device wifi list


5.) Turn off radio

    $ network-manager.nmcli radio wifi off
    
    
6.) Turn on wifi radio

    $ network-manager.nmcli radio wifi on
    
      
7.) Delete connection 

    $ nmcli connection delete XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
    
    
8.) Show connections

    $ sudo network-manager.nmcli con
    
    
    

12.) Configure gsm connection.

    $ sudo network-manager.nmcli con add con-name vzw-wireless ifname ttyACM3 type gsm apn vzwinternet
    
13.) Activate connection.

    $ sudo network-manager.nmcli con up <name>
        


Configuring an ad-hoc network with Ubuntu Core 16.

    $ sudo network-manager.nmcli con edit “Wired connection 2”
        
        # Changes the name of the connection.
        nmcli> set connection.id "ad-hoc"
    
        # Prints out information associated with ipv4.
        nmcli> print ipv4

        # Sets a static IP address. This is the address that you ssh into with 


        $ sudo ssh admin@192.168.0.160



        nmcli> set ipv4.addresses 192.168.0.160/24

        # This will be prompted.
        Do you also want to set 'ipv4.method' to 'manual'? [yes]: yes

        # Save the configuration.
        nmcli> save


Wifi Notes
==========
        
        
        
$ mmcli -L 
Found 1 modems: 
/org/freedesktop/ModemManager1/Modem/2 [Telit] LE910-SV V2

Once the index number is obtained we need to edit the PDP context three with the correct APN. In this example, we are using we01.vzwstatic, but again the APN needed should be confirmed with Verizon.

$ mmcli -m 2 --command='+CGDCONT=3,"IPV4V6","we01.vzwstatic"'

You can confirm the profile was updated correctly by sending a query to the modem for its saved profiles:

$ mmcli -m 2 --command='+CGDCONT?' 
response:
'+CGDCONT: 1,"IPV4V6","vzwims","",0,0 
+CGDCONT: 2,"IPV4V6","vzwadmin","",0,0 
+CGDCONT: 3,"IPV4V6","ne01.vzwstatic","",0,0'
You can now create the connection profile in Ubuntu Network Manager and connect the network.



    $ sudo snap install wifi-ap


5.) Enable the access point and restart the service:


    $ sudo /snap/bin/wifi-ap.config set disabled=false


$ sudo systemctl start snap.wifi-ap.backend

                                   

WiFi-AP default SSID Ubuntu should now visible to clients.
 
Wifi-ap docs: https://docs.ubuntu.com/core/en/stacks/network/wifi-ap/docs



The snap can be installed from the Ubuntu Store with the following command
$ snap install wifi-ap
$ snap connect wifi-ap:network-manager network-manager:service





$ wifi-ap.status
$ sudo wifi-ap.config get wifi.security-passphrase
$ wifi-ap.config set disabled=false
$ wifi-ap.config set wifi.security=wpa2 wifi.security-passphrase=Test1234
Simultaneous STA / AP Mode
If your hardware and the kernel driver supports a simultaneous STA / AP mode you can stay connected to another access point while running your own. The only shortcoming here is that both have to operate on the same channel.
You may find the current channel being used for the STA connection by looking at the STA network interface with the iw command.
To get the iw command available on an Ubuntu Core system install the wireless-tools snap from the store
$ snap install wireless-tools
Connect required slots/plugs
$ snap connect wireless-tools:network-control core:network-control
Now you can run the iw command to find the current channel being used
$ wireless-tools.iw dev
phy#0
    Unnamed/non-netdev interface
        wdev 0x4
        addr aa:bb:cc:dd:ee:ff
        type P2P-device
    Interface wlan0
        ifindex 3
        wdev 0x1
        addr aa:bb:cc:dd:ee:ff
        type managed
        channel 1 (2412 MHz), width: 20 MHz, center1: 2412 MHz
NOTE: If the channel is not part of the output your kernel WiFi driver doesn’t report the channel.
The relevant line showing the channel being used is highlighted above. In this case it is channel 1. The next step is to configure the wifi-ap snap with the channel
$ wifi-ap.config set wifi.channel=1


