#### Sparse checkout:
 * This command is used to create sparse checkouts, which change the working tree from having all tracked files present to only having a subset of those files
```bash 
 git clone --no-checkout https://github.com/elniko77/play
 cd play
 git sparse-checkout init --cone
 git checkout master
 # Set the needed directory
 git sparse-checkout set kubernetes
```
