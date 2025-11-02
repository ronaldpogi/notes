# Step 1: Check your current remote
```
git remote -v
```
### You’ll see something like:
```
origin  git@github.com:ronaldbibon/old-repo.git (fetch)
origin  git@github.com:ronaldbibon/old-repo.git (push)
```
# Step 2: Remove the old remote
```
git remote remove origin
```
### You can confirm it’s gone:
```
git remote -v
```
# Step 3: Connect to a new repository
```
git remote add origin https://github.com/ronaldbibon/new-repo.git
```
# Step 4: Push your local code to the new repo
```
git branch -M main
git push -u origin main
```
# Step 5: Verify connection
```
git remote -v
```


