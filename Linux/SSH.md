Tips and Tricks for SSH usage
=============================

-------------------------------
Execute local scripts on remote Host
------------------------------------

	ssh -t name@greatserver.com "$(< ~/setup.sh)"
	
The ``t`` option is required only if an interactive session is required. It allocates a pseudo terminal (PTY).
The target script is piped directly to the remote and is executed locally.

Found [here](https://unix.stackexchange.com/questions/100652/bash-interactive-remote-prompt). 
Also consider the [man page](https://man.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man1/ssh.1).
