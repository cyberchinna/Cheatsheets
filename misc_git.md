# Git on localhost

```bash
git config --global user.name "<username>"
git config --global user.email "<email>"
```

```bash
# Generate key pair
ssh-keygen
```

```bash
# Copy content of id_rsa.pub to github repo
cat ~/.ssh/id_rsa.pub

Paste content into settings > SSH and GPG Keys > New SSH Key
Provide a title and paste content into Key section and Add SSH Key
```

```bash
# Set the repositorie's origin
git remote -v 
git remote set-url origin git@gitlab.com:<repo path>.git
```
