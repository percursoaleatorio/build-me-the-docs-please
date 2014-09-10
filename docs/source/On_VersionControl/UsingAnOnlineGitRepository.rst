.. metadata-placeholder

:DC.Title:
   Background information on the use of online repositories
:DC.Creator:
   Nery, Fernanda
:DC.Date:
   2014-09-01
:DC.Description:
   Brief introduction to online git repositories.
   Based on:
   http://intermediaware.com/blog/how-to-use-dropbox-as-a-git-repository
   https://freshmob.com.au/using-dropbox-as-a-git-repository/
   http://viralpatel.net/blogs/dropbox-svn-subversion-repository/
:DC.Language:
   en
:DC.Format:
   text/x-rst
:DC.Rights:
   Public.


Setting up an online Git Repository
***********************************

Three possible alternatives are:

*  Using Atlassian Bitbucket_:
   it is free for public and private repositories (up to 5 team members),
   and also supports Mercurial repositories.

*  Using GitHub_: it is free for public repositories

*  Using Dropbox_ : is is free up to a 2GB maximum storage.

Using Bitbucket
===============

1. Create a Bitbucket account and a new repository "projectXPTO"

2. Install Git in your computer
   and set the global configuration (usig Git Bash)::

   $ git config --global user.name "johndoe"
   $ git config --global user.email johndoe@example.com

3. Create a local git repository::

   $ mkdir /path/to/your/project
   $ cd /path/to/your/project
   $ git init

4. Link the remote git repository to your local repository::
    
   $ git remote add origin https://johndoe@bitbucket.org/johndoe/projectXPTO.git

5. Add a ReadMe file::

   $ echo "# This is my README" >> README.md
   $ git add README.md
    
6. Commit and push the first change::

   $ git commit -m "First commit. Adding a README."
   $ git push -u origin master

Using GitHub
============

The steps are similar to the ones when using Bitbucket...

1. Create a GitHub account and a new repository "projectXPTO"

(steps 2 and 3 as above)

4. Link the remote git repository to your local repository::

   $  git remote add origin https://github.com/johndoe/projectXPTO.git

(steps 5 and 6 as above)

Using Dropbox
=============

Please note that this is a more complicated solution,
that is only useful if the Bitbucket_ or Github_ options
cannot be used for some reason...

Dropbox_ is a cloud storage service provider.
A Dropbox client application
is available for Windows, Mac OSX, Linux and Android operating systems.
The client application synchronises the content of a local Dropbox folder
(in the client computer's disk) with the cloud Dropbox storage area.

A git repository is created in the local Dropbox folder
and it will work if it were an “remote” upstream git repository.

Another local repository
(located somewhere in the local disk, but **not** in the Dropbox folder)
can then clone, push or sync with the Dropbox “remote” repository.

The rest is done automatically by the Dropbox application:
the “remote” folder will be synced with online storage
and will accessible from anywhere.

Setup the “remote” and the local repositories
---------------------------------------------

#. Install both Git and the Dropbox client application on the computer.

#. Go to the local Dropbox folder and create a bare repository.
   Open a Git Bash window::

   $ cd ~/Dropbox
   $ mkdir -p remoteRepos/ProjectXPTO
   $ git init –bare remoteRepos/ProjectXPTO

#. Go to the local project folder, and start a local git repository::

   $ cd ~/localRepos/ProjectXPTO
   $ git init .
   $ git add .
   $ git commit –all -m "Initial commit"
    
#. Link the local repository to the “remote” repository on the Dropbox folder:: 
    
   $ git remote add dropbox /Dropbox/remoteRepos/ProjectXPTO/
   
#. Push all the local changes to the “remote” repository::

   $ git push dropbox master

Clone the “remote” repository to a different machine
----------------------------------------------------

#. Again, both Git and the Dropbox application must be installed
   **and** the Dropbox folders must be synced.

#. Then, clone the “remote” repository with::

   $ cd ~/otherMachine/ProjectXPTO
   $ git clone -o dropbox /Dropbox/remoteRepos/ProjectXPTO/
    
Push changes to the “remote” repository
---------------------------------------

#. Changes to the local project can be pushed back to the  “remote”::

   $ git commit –all -m "Changes made!"
   $ git push dropbox master

Sync the local copy with the “remote” repository
------------------------------------------------

#. To sync the local copy with the “remote” repository::

   $ git pull dropbox master


.. links-placeholder

.. include:: ../Z_SharedFiles/Z_GenericLinks.txt
