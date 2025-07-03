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

to create and switch to main branch
```bash
git branch branch_name
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

to remove previous commit / undo commit 
To create a new commit that reverts the last commit  
```bash
git revert HEAD
```

to add upstream (add branch on forked_url from origin_url)
```bash
git add upstream origin original_url
git fetch upstream
git branch -b branch_name origin/branch_new_name
```

---------------------------------------------------
# git-commands

## Having multiple Github accounts
### Personal - Work

Open a command prompt and type in: ssh-keygen
```bash
C:\Users\PC> ssh-keygen
```
you can press enter a couple of times to accept the defaults. This will create a .ssh folder inside the C:\Users\<your username> folder

You can now navigate to this .ssh folder and type in the following command there:
```bash
cd .ssh
ssh-keygen -t rsa -C "imrosun@email.com"
```
It will then prompt you to enter the file name in which to save the key. type in personal:

Next it will prompt you to create a passcode for this key pair. You can either provide one, or just hit enter twice to not use a password for your keypair.

You now have a keypair. This consists of a public key which will be your “personal.pub” file which you will be sharing with Github, and a private key, which you DO NOT SHARE WITH ANYONE called simply “personal”. You will see both these files in the .ssh folder.

We’ll repeat this process once more, only this time for our business key pair:
```bash
ssh-keygen -t rsa -C "roshans@work.com"
```
When it prompts you to enter the file name in which to save the key, you could use “business” however you might find that you end up having multiple Github business accounts, and you may end up doing this multiple times, so in this instance I will save the keypairs as “work”

Once again, it creates another keypair in the .ssh folder. There will be a public work.pub file and a private key, simply called work.

The next thing to do is to add the private key identities to the SSH authentication agent. This is very simple using the ssh-add command:
```bash
C:\Users\PC\.ssh\ ssh-add personal
Identity added C:\Users\PC\.ssh\prsonal (imrosun@gmail.com)

C:\Users\PC\.ssh\ ssh-add work
Identity added C:\Users\PC\.ssh\prsonal (roshans@work.com)
```
If you see error like 
"Error connecting to agent: No such file or directory" 
OR
"could not open a connection to your authentication agent."
then try to activite agent by below command
```bash
eval "$(ssh-agent)"
```

The next thing we need to do is create a “config” file. This is a file with no extension (i.e. not .txt) and it will allow us to distinguish between the two gitub connections.

Inside the .ssh folder, create a file with the following inside it:
```bash
# Default personal github (imrosun@gmail.com)
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/personal

# work github (work)
Host github.com-work
 HostName github.com
 User git
 IdentityFile ~/.ssh/work
```
Save this filename as “config”.

Note that whilst the actual hostname (the thing you will connect to) remains identical (github.com) the actual “Host” connection will be different. For your personal account, you can leave it as the default (github.com) but for the wok account, we’ve amended it to say that the Host is github.com-work

Also the identity files point to their respective keys.

Now we login to each Github website so that we can add our public keys.

So first we’d login to the personal Github account and go into “settings” -> “SSH and GPG Keys”

We then add a new SSH key. We’ll called the key “personal” and we then paste in everything inside the “personal.pub” file:

(Note: if you are having trouble opening the personal.pub file, right-click on it and open-with notepad)

Now log out of the Github account and repeat this process in your work Github account, only this time using the public key from “work.pub”

All set just add git config user.email and user.name and start pushing.
