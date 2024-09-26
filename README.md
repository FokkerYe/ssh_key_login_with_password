# ssh_key_login_with_password
ssh password and key login testing
### step-1 Generate SSH Keys
```bash
 ssh-keygen -t rsa
```
### step-2 click  enter
 id_rsa: This file contains your private key. Keep it secure and do not share it.
 
id_rsa.pub: This file contains your public key. This key can be shared with servers you want to access.
 
 
###  step-3 Select if you want to create a password; if not, you can skip this step
 
###  step-4 Change to the SSH configuration directory:
 ```bash
 cd /root/.ssh
 ls
 ```
 ### step-5 Copy the Private Key to Your Local Computer
 
 Use a secure method (such as SCP or SFTP) to copy the id_rsa file (private key) to your local machine.
 
 ## step-6  please configure this file path
 ```bah
 cat /etc/ssh/sshd_config
 nano  /etc/ssh/sshd_config
 ```
 ## step -7 Ensure the following settings are configured:
 ```bash
PermitRootLogin yes
 PubkeyAuthentication yes
PasswordAuthentication yes
AuthorizedKeysFile      .ssh/authorized_keys .ssh/authorized_keys2
ChallengeResponseAuthentication yes
```

### step-8  Restart the SSH Service 
```bash 
systemctl restart sshd
```
### step-9   Move Public Key to Authorized Keys
Rename the id_rsa.pub file to authorized_keys to grant access permissions:
```bash 
 mv id_rsa.pub authorized_keys
```

### step-10   Set File Permissions
Set the appropriate permissions for the authorized_keys file and the .ssh directory:

 ```bash
chmod 600 ~/.ssh/authorized_keys
 chmod 700 ~/.ssh
sudo systemctl restart ssh
```

## step-11  “Use PuTTYgen software to convert the id_rsa (private key) file to a .ppk file.”
