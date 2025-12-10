# How to Fix Git Author

## 1. Install Required Packages
```
sudo apt install git-filter-repo
```

## 2. Create mailmap
```
vim mailmap
```
```mailmap
u2key <248891400+u2key@users.noreply.github.com> old-name <old-email@users.noreply.github.com>
```

## 3. Fix Git Author
```
git-filter-repo -f --mailmap mailmap
```
