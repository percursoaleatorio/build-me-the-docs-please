Set up SSH for Git
=====================

.. note:: Sources

   Mostly from: 
   https://confluence.atlassian.com/display/BITBUCKET/Set+up+SSH+for+Git

   Mixed with: 
   https://help.github.com/categories/56/articles
   https://help.github.com/articles/working-with-ssh-key-passphrases
   http://nerderati.com/2011/03/17/simplify-your-life-with-an-ssh-config-file/
   
When you use HTTPS, you need to authenticate (supply a username and password) 
each time you take an action that communicates with the remote server. 
This page shows you how to use secure shell (SSH) 
to communicate with the Bitbucket or Github server and avoid having to manually type a password.
   
Step 1. Check if you have existing default Identity
---------------------------------------------------

The Git Bash shell comes with an SSH client. Do the following to verify your installation:

#. Double-click the Git Bash icon to start a terminal session.

#. Enter the following command to verify the SSH client is available::

      $ ssh -v
      OpenSSH_4.6p1, OpenSSL 0.9.8e 23 Feb 2007
      usage: ssh [-1246AaCfgkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]
      [-D [bind_address:]port] [-e escape_char] [-F configfile]
      [-i identity_file] [-L [bind_address:]port:host:hostport]
      [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
      [-R [bind_address:]port:host:hostport] [-S ctl_path]
      [-w local_tun[:remote_tun]] [user@]hostname [command]

#. If you have ssh installed, go to the next step.

   If you don't have ssh installed, install it now with your package manager.

#. List the contents of your ~/.ssh directory.

   If you have not used SSH on Bash you might see something like this::

      $ ls -a ~/.ssh
      ls: /c/Users/your-user-name/.ssh: No such file or directory
      
   If you have a default identity already, you'll see two id_* files::

      $ ls -a ~/.ssh
      .    ..    id_rsa    id_rsa.pub  known_hosts

   In this case, the default identity used RSA encryption (id_rsa.pub). 
   If you want to use an existing default identity for your Bitbucket account, 
   skip the next section and go to create a config file.

Step 2. Set up your default identity
-------------------------------------

By default, the system adds keys for all identities to the /Users/your-user-name/.ssh directory. 
The following procedure creates a default identity.

#. Open a terminal in your local system.
   Enter ssh-keygen at the command line:: 

      $ ssh-keygen
      Generating public/private rsa key pair.
      Enter file in which to save the key:

   To create a key with a name other than the default, specify the full path to the key. 
   Enter and renter a passphrase when prompted.
   Unless you need a key for a process such as script, you should always provide a passphrase. 
   The command creates your default identity with its public and private keys. 
   
#. List the contents of ~/.ssh to view the key files.
   You should see something like the following::

      $ ls ~/.ssh
      id_rsa  id_rsa.pub 
   
   The command created two files, 
   one for the public key ( for example id_rsa.pub ) 
   and one for the private key (for example, id_rsa ).

Step 3. Create a SSH config file
--------------------------------

#. Using a text editor, edit the ~/.ssh/config file.
   Add the following entries to the configuration file using the following format::

      Host bitbucket.org 
       IdentityFile ~/.ssh/id_rsa
       
      Host github.com
       IdentityFile ~/.ssh/id_rsa

   Every second line is indented. 
   That indentation (a single space) is important, so make sure you include it.  
   The second line is the location of your private key file.
   
#. Save and close the file.

#. Restart the GitBash terminal.

Step 4. Update your .bashrc profile file
----------------------------------------

It is a good idea to configure your GitBash shell 
to automatically start the agent when launch the shell.  
The .bashrc file is the shell initialization file. 
To start the agent automatically, do the following.

#. Start GitBash.

#. Edit your ~/.bashrc file.

   Add the following lines to the file::

      SSH_ENV=$HOME/.ssh/environment
         
      # start the ssh-agent
      function start_agent {
          echo "Initializing new SSH agent..."
          # spawn ssh-agent
          /usr/bin/ssh-agent | sed 's/^echo/#echo/' > "${SSH_ENV}"
          echo succeeded
          chmod 600 "${SSH_ENV}"
          . "${SSH_ENV}" > /dev/null
          /usr/bin/ssh-add
      }
         
      if [ -f "${SSH_ENV}" ]; then
           . "${SSH_ENV}" > /dev/null
           ps -ef | grep ${SSH_AGENT_PID} | grep ssh-agent$ > /dev/null || {
              start_agent;
          }
      else
          start_agent;
      fi

#. Save and close the file.
#. Restart the GitBash terminal.
#. The system prompts you for your passphrase.
#. Enter your passphrase.
   After accepting your passphrase, the system displays the command shell prompt. 
   Verify that the script identity added your identity successfully by querying the SSH agent::

      $ ssh-add -l

   After you install your public key to Bitbucket|Github, 
   having this script should prevent you 
   from having to enter a password each time you push or pull a repository from Bitbucket.

Step 5. Install the public key on your Bitbucket|Github account
---------------------------------------------------------------

In Bitbucket:

#. Open a browser and log into Bitbucket.
#. Choose avatar > Manage Account from the menu bar. 
#. The system displays the Account settings page.
   Click SSH keys.
   The SSH Keys page displays. It shows a list of any existing keys. Then, below that, a dialog for labeling and entering a new key.

   Copy the contents of the public key file into the SSH Key field.
   Click the Add key button.
   The system adds the key to your account.

In Github:

#. Goto to the account settings, everything is pretty much as above.
    
Return to the GitBash terminal window:

#. Verify your configuration by entering the following commands::

      ssh -T git@bitbucket.org
      
      ssh -T git@github.com

   The command message tells you which Bitbucket account can log in with that key. 
   Verify that the command returns your account name.

Step 6. Configure your repository to use the SSH protocol
---------------------------------------------------------

The URL you use for a repository 
depends on which protocol you are using, HTTPS and SSH. 

In Bitbucket:

   *  ssh://git@bitbucket.org/accountname/reponame.git

   *  https://accountname@bitbucket.org/accountname/reponame.git

The same goes for Github::

   *  ssh://git@github.com/accountname/reponame.git

   *  https://accountname@github.com/accountname/reponame.git

So...
   
#. View your current repository configuration file `.git/config`, that should similar to this::

      [remote "origin"]
        fetch = +refs/heads/*:refs/remotes/origin/*
        url = https://accountname@domain/accountname/reponame.git
      [branch "master"]
        remote = origin
        merge = refs/heads/master

#. Change the url::

      [remote "origin"]
        fetch = +refs/heads/*:refs/remotes/origin/*
        url = ssh://git@domain/accountname/reponame.git
      [branch "master"]
        remote = origin
        merge = refs/heads/master

#. Save your edits and close the file.
