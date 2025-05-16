# setup-multiple-git-acc-mac
Add new github profile

step 1: 
see the vim ~/.gitconfig

step 2: 
add this 
[includeIf "gitdir:~/desktop/company"]
    path = ~/.git-sonnul.conf

step 3:
create the .git-company.conf

step 4:
add this in ~/.git-company.conf
[user]
        name = harshCompany
        email = harsh@company.com

step 5:
see thi vim ~/.ssh/config

step 6:
add this
Host github.com-harshCompany
   HostName github.com
   User git
   IdentityFile ~/.ssh/github-company
   IdentitiesOnly yes


step 7:
run this command in ~/.ssh
ssh-keygen -t rsa -C "harsh@company.com" -f "github-company"

step 8:
run this 
pbcopy < ~/.ssh/github-company.pub

step 9:
open Github keys section 
click add ssh keys 
authentication type
paste and save 

you are done

step 10:
use this url pattern to add git repos

git remote add origin git@github.com-harshCompany:Harsh-2503/flask_api.git
