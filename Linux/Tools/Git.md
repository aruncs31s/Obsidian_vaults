---
id: Git
aliases: []
tags: []
---

# Git
- [Introduction](#introduction)
- [Installation](#installation)
- [Initial Setup](#initial%20setup)
- [Basics](#basics)
    - [Getting a Git repo]()
        - [Adding local directory to git](Linux/Tools/1709452138-SMNE.md)
        - [Cloning a repo]()
    - [Submitting that change]()


### **Introduction**


  Git is a `source control` created for the `Linux` Kernel by `Linus Torvalds`.
<details>
<summary>More</summary>
    Git works the familiar primitives of source control management systems such as `commits`, `diffs`,`trunks`, `tags`, branches, and so on. However, Git has the intrinsic property of being a distributed system - a system in which there is no official client/server relationship. Each repository contains the entire history of revisions. This means that there's no need to have network access or synchronization to a central repository. In essence, a git repository is nonlinear with regard to revisions. two different users may change source code in unique, independent ways without interfering with each other. one benefit of this model is that developers are freer to independently work with, experiment with, and tweak code.
	Git supports independent development and revision management, it also supports the means to share and incorporate revisions made in unsynchronized repositories.
</details>

###### summary
- Git is a VCS(version control system)
<details><summary>VCS</summary>
</details>
- Git stores data as snapshots and if file is not changed



---

### **Installation**
- Windows [Click Here](https://git-scm.com/download/win)
- Debian
```bash
sudo apt install git
```

- Fedora
```bash
sudo dnf install git
```

- Arch Linux 
```
sudo pacman -S git
```
---

### **Initial Setup**
This only required to do once like configuring user email and user name .
- Setting up you identity

```
git config --global user.name "You name"
git config --global user.email youremail@google.com
```
*You can exclude `--global` flag it sets this properties as global but if you want to keep repository wise configs you simply exclude that*



- You can use the following to see saved configs
```bash
git config --list 
```
---




### **Basics**
- [Creatig a repo](#creating%20a%20repo)





#### Creating a repo









- [[Branch]]



- [Merge Conflict](#mergeconflict)



- To upload local folder/repo to `github`
```
echo "# tic_tac_toe" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/BloBuster/tic_tac_toe.git
git push -u origin main
```

- Push existing repo
```
git remote add origin https://github.com/BloBuster/tic_tac_toe.git
git branch -M main
git push -u origin main
```



#### Merge Conflict
