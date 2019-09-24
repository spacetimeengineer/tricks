Bash Tricks
===========

1.) locate: Description: Lists all files with permission that contain string.
        
    $ locate <String>

    $ locate -i <String> | less

    $ locate -i -n <QuantityOfListItems> <String>
    
2.) grep:
        
    # Lists highlighted instances of <String> within <File> in a cat type format.
    $ grep <String> <File>

    # Lists highlighted instances of <String> within multiple files in a cat type format.
    $ grep <String> *

    # This searches for any occurence of "string" in /path.
    $ grep -rl "string" /path
        

3.) find: Lists all files in directory with <StringWithinFileName> contained in it's file name.

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


Hard Drives 
===========
 
    1.) List all devices.
        
        $ lsblk

    2.) 2. Create a mount point :

        $ sudo  mkdir /media/usb

    3.) Mount!

        sudo mount /dev/sdb1 /media/usb

    4.) Copy

        cp -a /home/android/Testproject/ /media/usb/ 


