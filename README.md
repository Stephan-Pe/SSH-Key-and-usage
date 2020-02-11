# How to generate a SSH Key from Commandline

- open Git Bash Command Terminal and type in
- ssh-keygen -t rsa -b 4096 -C "your@email.adress"
### than Comp will say 
- Generating public/private rsa key pair.
- Enter file in which to save the key (/c/Users/you/.ssh/id_rsa):
### next press enter than Comp will say
- Enter passphrase (empty for no passphrase):
- Enter same passphrase again:
## Than Key will be generated
### Than start SSH Agent
- eval $(ssh-agent -s)
### Comp will show
- Agent pid *1234* (some numbers)
### next add ssh to default location
- ssh-add ~/.ssh/id_rsa
### Comp will say
- Enter the passphrase for /c/Users/you/.ssh/id_rsa
- Identity added: /c/Users/you/.ssh/id_rsa (/c/Users/you/.ssh/id_rsa)
### Next step copy the key
- clip < ~/.ssh/id_rsa.pub
### go to Github
- open Profile / Personal settings / SSH and GPG keys
- click on New SSH key
- give it a name
- paste key into Key field and save

