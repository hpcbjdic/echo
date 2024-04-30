# this little project deploys an echo service on bwCloud via Ansible

In order to deploy it on *your* server, do the following:

1) If not done yet, install Ansible on your computer (exact procedure depends on your operating system).
2) Set up a suitable VM in the bwCloud service. We assume its human-readable address to be \<host\>. Access via ssh should be enabled.
3) Append your private key to \<host\>:~/.ssh/authorized\_keys and set proper file permissions for that file and the .ssh directory. We suggest to just do a $> ssh-copy-id -i ~/.ssh/\<yourKey\> debian@\<host\> which automatically cares about all those tasks. When being asked of a password, use the one you use to login to the bWCloud portal.
4) Clone this repo and cd into it.
5) Replace the address in deploy-http-echo-server.yaml (lines 2 and 5) by that of your VM.
6) Run the playbook via
   $> ansible-playbook -u debian -i inventory.ini deploy-http-echo-server.yaml
7) Use the service, e.g. by doing
   $> curl "http://\<host\>:3246"

*BTW*: The playbook is going to run files/echo.py which has been shamelessly stolen from https://github.com/cdfuller/echo-server . ;-)

</br>

*TODO*:
- "downgrade" VM to most tiny setup to save resources (the provided service is very very tiny!)
- restrict open ports to those necessary for ssh and HTTP(S) (22, 80, 443?)
- clean up leftovers from previous approaches
