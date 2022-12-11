# Git Toolbox

## Set up multiple GitHub accounts on one machine
Generate SSH Keys:
```bash
cd ~/.ssh/
ssh-keygen -t ed25519 -C "user1@email.com" -f "id_ed25519_user1"
ssh-keygen -t ed25519 -C "user2@email.com" -f "id_ed25519_user2"
```
Register the new SSH keys with the ssh-agent:
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_user1
ssh-add ~/.ssh/id_ed25519_user2
```
Create SSH config file:
```bash
cd ~/.ssh/
touch config
code config
```
```
Host user1.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_user1

Host user2.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519_user2
```
Add the public SSH keys to the corresponding GitHub accounts.
