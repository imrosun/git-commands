# git-commands

To initialize a project 
```bash
git init
```

To add file
```bash
git add . or git add <filename>
```

attach message to added file
```bash
git commit -m "add message"
```

switch to main branch
```bash
git checkout main
```

add github repository
```bash
git remote add origin https://github.com/imrosun/git-commands.git
git remote add origin https://github-token@github.com/imrosun/git-commands.git
```

push code to main branch
```bash
git push origin main
```

to pull recent updated codes
```bash
git pull origin main
```

to manege/see conflicts
```bash
git pull origin main --allow-unrelated-histories
```

to check the status of added files
```bash
git status
```

to remove remote origin 
```bash
git remote remove origin
```
