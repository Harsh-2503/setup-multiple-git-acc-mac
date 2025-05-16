## 🔐 Add a New GitHub Profile with Custom SSH & Git Config

Follow these steps to configure a separate GitHub profile (e.g., for company work) using a custom `.gitconfig` and SSH setup.

---

### ✅ Step-by-Step Instructions

#### 1. View global Git config  
```bash
vim ~/.gitconfig
```

#### 2. Add directory-based config include  
In `~/.gitconfig`, add:
```ini
[includeIf "gitdir:~/desktop/company"]
  path = ~/.git-company.conf
```

#### 3. Create the company-specific Git config  
```bash
touch ~/.git-company.conf
```

#### 4. Add user identity in `~/.git-company.conf`  
```ini
[user]
  name = harshCompany
  email = harsh@company.com
```

#### 5. View SSH config file  
```bash
vim ~/.ssh/config
```

#### 6. Add custom SSH Host for the company GitHub profile  
```ssh
Host github.com-harshCompany
  HostName github.com
  User git
  IdentityFile ~/.ssh/github-company
  IdentitiesOnly yes
```

#### 7. Generate a new SSH key for company profile  
```bash
cd ~/.ssh
ssh-keygen -t rsa -C "harsh@company.com" -f "github-company"
```

#### 8. Copy the public key to clipboard  
```bash
pbcopy < ~/.ssh/github-company.pub
```

#### 9. Add SSH key to GitHub  
- Go to GitHub → **Settings** → **SSH and GPG keys**  
- Click **"New SSH key"**  
- Paste the key and save  

#### 10. Clone or push to repos using the custom host  
Use the following URL pattern:
```bash
git remote add origin git@github.com-harshCompany:Harsh-2503/flask_api.git
```

---

🎉 **You're all set with a new GitHub profile for company work!**
