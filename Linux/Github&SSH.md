Github Tips & Tricks
==================

-----------------------------------------------
Using multiple SSH-Keys
-----------------------------------------------

	vi ~/.ssh/config
	
	IdentityFile ~/.ssh/id_rsa
	IdentityFile ~/.ssh/id_rsa_old
	IdentityFile ~/.ssh/id_ed25519
	
This tries all keys in order until one is accepted. Does not work with git deployKeys. 
See next section for more information.


Example for a per host configuration:

	Host moongen github.com
		HostName github.com
		PreferredAuthentications publickey
		IdentityFile ~/moonsniff/moongenKey.ppk
		User myname
		
Here moongen and github.com become both aliases for github.com.

		
Click [here](https://man.openbsd.org/ssh_config) for a full overview what is possible to specify in the config file.
		
-----------------------------------------------
Using multiple Deploy Keys for the same account
-----------------------------------------------


**Step 1** 

Define aliases for github.com and specify the corresponding keys

	vi ~/.ssh/config

	Host moongen github.com
		HostName github.com
		PreferredAuthentications publickey
		IdentityFile ~/moonsniff/moongenKey.ppk

	Host libmoon github.com
		HostName github.com
		PreferredAuthentications publickey
		IdentityFile ~/moonsniff/libmoonKey.ppk
		
**Step 2**

Use the alias while cloning, so instead of:

	git clone git@github.com:username/repo1.git
	
Type:

	git clone git@moongen:username/repo1.git
	

For **existing** repositories update the remote URL

	git remote set-url origin git@github.com:username/repo-1.git
	
	
-------------------------------
Rename a remote
---------------

Change remote name from origin to github

	git remote rename origin github
	


-------------------------------
Add a remote
------------

	git remote add origin git@github.com:User/UserRepo.git
	
	
-------------------------------
Check current url of a remote
---------------------------

	git remote get-url origin
	
	
-------------------------------
Initialize/Update Submodules
----------------------------
Init is needed for first time initialization, recursive also intializes/updates submodule of all depths

	git submodule update --init --recursive
	
	
-------------------------------
Set local/global mail and username
----------------------------------

Change mail for one repository or all

	git config user.email "email@example.com"
	git config --global user.email "email@example.com"
	
Replace email with name to set the name

-------------------------------
Access rights for private keys
------------------------------

	chmod 600 id_rsa