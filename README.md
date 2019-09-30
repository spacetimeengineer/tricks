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




