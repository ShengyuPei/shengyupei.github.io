# This is a personal blog.
I have to do these operations.
## 1. Setting->SSH keys
Open Git Bash Here
```bash
ssh-keygen -t rsa -C "shengypei@gmail.com"
cat id_rsa.pub
```
## 2. New repository
Setting->GitHub Pages->Check it out here!
## 3. Unload files
Open Git Bash Here
Create new folder, new files
```bash
git init
git add .
git commit -m "commit note"
git branch -M main
git remote add origin git@github.com:psycv/psycv/github.io.git
git push -u origin main
```
## 4. Done