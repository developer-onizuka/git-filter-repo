# git-filter-repo

# 0. Install git-filter-repo
```
sudo apt install python3-pip
sudo pip3 install git-filter-repo
```

# 1. Make the file of mailmap
```
repo=<Target repo>
user=<your-github-id>
token=ghp_idXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

git clone https://github.com/$user/$repo
cd $repo
```
```
git config --global user.email
git config --global user.name
```
```
cat <<EOF > mailmap
<xxxxxxxx+id@users.noreply.github.com> <email@example.com>
EOF
git filter-repo --force --mailmap mailmap
git remote add origin https://$token@github.com/$user/$repo
git push --force origin --all
```

# 2. Check it
```
git clone https://github.com/$user/$repo
cd $repo
curl https://api.github.com/repos/$user/$repo/commits -k > gitlog.log
grep example.com gitlog.log
```
