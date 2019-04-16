# SSH examples and exercises

Secure Shell (SSH) is a UNIX-based command interface and protocol for securely getting access to a remote computer (server).

SSH allows you to connect from your client (laptop) to your server securely and perform Linux command-line operations.

## HPSA Cluster

We have access to 6 remote machines. To access them, you need to know your _student ID_ (`student-id` in the following) and _host ID_ (`host-id` in the following), that will be provided in class.

*   The _student ID_ is your personal student identification code assigned at the beginning of the semester.
*   The _host ID_ is one of the 6 remote machines, assigned in a round-robin fashion.

## SSH Examples

Once you login to the remote machine you can perform commands there. Please note that:

*   The commands will run in the remote machine (server), not on your local machine (laptop).
*   You need a working network connection (i.e., being connected to Internet) to open SSH connections.

### Remote execution of commands

Open a shell on you laptop and execute the following command on your laptop:

    uptime

The `uptime` command-line utility displays the current time, the length of time the system has been up, the number of users, and the load average of the system over the last 1, 5, and 15 minutes.

You can execute the same command on the server using SSH:

    ssh <student-id>@<host-id> uptime

You may see a warning like this:

    The authenticity of host '<host-id> (IP ADDRESS)' can't be established.
        > RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
        > Are you sure you want to continue connecting (yes/no)?

Input `yes` and continue. You will get another message:

    Warning: Permanently added 'noc.e0.ws.afnog.org' (DSA) to the list of known hosts.
    <student-id>@<host-id>'s password: <enter password here>

Input your password. If everything is successful, you will see on your video the output of the execution of the command-line utility **on the remote machine**.

The _fingerprint_ is a unique identity for the server. The first time you connect to a server, SSH has no way of knowing whether you are connecting to the real machine, or if a hacker is intercepting your communication. All it can do is to retrieve the `host-id` fingerprint belonging to the remote machine (which may be the real machine, or if you are very unlucky it may be an attacker). This fingerprint is called _server's public key_.

The server's public key is then recorded in `~/.ssh/known_hosts` on your own client machine - you can examine this file yourself. From now on, every time you connect, the remote-side's fingerprint is compared with the one which was learned during the first connection. If they are the same, you can be sure that you are connecting to the same machine.

### Remote access

With the previous exercises, we opened a secure connection from the client to the server, we executed a command on the server, we got back the output from the server, and we closed the connection.

SSH allows also to open a remote connection to the server and execute a **remote shell**, i.e., open a terminal program on the server and keep it open, redirecting our input from the client to the server and redirecting our output from the server to the client.

Open a shell on your laptop and execute the following command on your laptop:

    ssh <student-id>@<host-id>

You will get a terminal program (i.e. a remote shell) open on the server. If now you execute the following command on that shell

    uptime

you will see, again, on your video the output of the execution of the command-line utility **on the remote machine**.

When you need to to exit from the remote server run the following command:

    exit

This command, execute in the remote shell, will close the SSH connection.

### Secure copy

Files on your laptop are not accessible from remote machine. We need to transfer files between our client pc and the server.

In Unix, you can use Secure CoPy (SCP) to securely copy files and directories between machines without starting an FTP session or logging into the remote systems explicitly. The `scp` command uses SSH to transfer data, so it requires a password for authentication.

Create a file foo.txt:

    echo "test" > ~/foo.txt

This command creates a file called `foo.txt` on your local machine, whose content is `test`.

Copy the file `foo.txt` from the local machine to the remote machine:

    scp ~/foo.txt <student-id>@<host-id>:~/foo.txt

This command copies the file `foo.txt` on your local machine to the remote server `host-id`, in your home folder (`~`), with the same name. You can change the name of the remote file while copying:

    scp ~/foo.txt <student-id>@<host-id>:~/bar.txt

or later, using SSH:

    ssh <student-id>@<host-id> mv ~/foo.txt ~/bar.txt

Copy the file back from the server to the client and change the name on the local machine:

    scp <student-id>@<host-id>:~/foo.txt ~/foo_bar.txt

Read the content of the `foo_bar.txt` file:

    less ~/foo_bar.txt
