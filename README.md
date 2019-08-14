# git-test
[Warning*]
$ git push -u origin master
Warning: Permanently added the RSA host key for IP address '####' to the list of known hosts.
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
_________________

[Solved*]
$ ssh-keygen -t rsa -b 4096 -C "email-name@email.com"

Generating public/private rsa key pair.
Enter file in which to save the key (~/.ssh/id_rsa):[Enter]
Enter passphrase (empty for no passphrase):[Input you password]
Enter same passphrase again: [Input you password again]
_________________
Change ssh-keygen password
$ ssh-keygen -p

Enter file in which the key is (~/.ssh/id_rsa):[current password]
Key has comment 'email-name@email'
Enter new passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved with the new passphrase.
_________________

$ eval $(ssh-agent -s)
Agent pid 329
_________________

$ ssh-add ~/.ssh/id_rsa
Enter passphrase for ~/.ssh/id_rsa:
Identity added: ~/.ssh/id_rsa (email-name@email)
_________________
check github allow SSH?
$ ssh -T git@github.com
Warning: Permanently added the RSA host key for IP address '#####' to the list of known hosts.
git@github.com: Permission denied (publickey).
_________________
$ cd ~/.ssh
_________________
$ cat id_rsa.pub
Copy this result and go to your Github account >Setting > SSH and GPG key > New SSH key. and paste over there.
_________________
And try git push your working directory again!
_________________
#[Warning**]
$ git commit -m "Warning and solve for beginner"
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
        modified:   README.md

Untracked files:
        git-profile.PNG

no changes added to commit
#[Solved**]
$ git add .
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory

//And try commit -m "" again



