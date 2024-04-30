# this little project deploys an echo service on bwCloud via Ansible

In order to deploy it on *your* server, do the following:

1) If not done yet, install Ansible on your computer (exact procedure depends on your operating system).
2) Set up a suitable VM in the bwCloud service. We assume its human-readable address to be \<host\>.
3) Clone this repo and cd into it.
4) Replace the string <address> in deploy-http-echo-server.yaml (lines 2 and 9) and inventory.ini (line 2) by the address of your VM.
5) Run the playbook via
   $> ansible-playbook -u debian -i inventory.ini deploy-http-echo-server.yaml
6) Use the service, e.g. by doing
   $> curl "http://\<host\>:3246"

*BTW*: The playbook is going to run files/echo.py which has been shamelessly stolen from https://github.com/cdfuller/echo-server . ;-)
