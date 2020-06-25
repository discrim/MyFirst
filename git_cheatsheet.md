# Git Cheatsheet
1. [Glossary](#glossary)
1. [Typical workflow](#typical_workflow)
1. [Clone an existing remote repository to local](#clone-an-existing-remote-repository-to-local)
	1. [Master branch](#master-branch)
	1. [Other branch](#other-branch)
1. [Check git status](#check-git-status)
1. [Stage files](#stage-files)
1. [Commit changes](#commit-changes)
1. [Push](#push)
1. [`git reset`](#git-reset)

### Glossary
`remote_repo`: Put an address of your remote repository. (Ex. `https://github.com/username/term_project.git`)  
`branch_name`: Put a name of your branch. (Ex. `network_function`)  

### Typical workflow
[Clone an existing remote repository to local](#clone-an-existing-remote-repository-to-local)  
→ Edit files  
→ [Check git status](#check-git-status)  
→ [Stage files](#stage-files)  
→ [Check git status](#check-git-status)  
→ [Commit changes](#commit-changes)  
→ [Push](#push)

### Clone a certain branch from an existing remote repository to local
#### Master branch
```
git clone remote_repo
```
If prompted to enter username and password, do it.
#### Other branch
```
git clone -b branch_name remote_repo
```
If prompted to enter username and password, do it.

### Check git status
```
git status
```
Shows if there is any change; if there is, shows if the changeis untracked or staged.

### Stage files
If files are staged, they are ready to be committed.
#### All files
```
git add -A
```
#### All files in current directory and all subdirectories (not superdirectories)
```
git add .
git add *
```
#### Selected files
- `git add pycode.py`: Stage only one file, `pycode.py` only.  
- `git add pycode.py ccode.c`: Stage only two files, `pycode.py` and `ccode.c` only.  
- `git add *code*.*`: Stage files such as `pycode1.py`, `pycode2.py`, `ccode.c`, etc.
- `git add *.py`: Stage all `.py` files only in current directory.  
- `git add \*.py`: Stage all `.py` files in current directory and all subdirectories.   
- `git add *.*`: Stage all files who have file extension only in the current directory.  
**How to add all files only in the current directory, even if they don't have file extensions?**  

### Commit changes
```
git commit -m "your_memo"
```
Present tense is recommended for `"your_memo"` such as `"Implement conversion function"`

### Push
```
git push
```
If this is your first time `push`ing, you will be prompted to type `git push --set-upstream remote_repo`. Please follow the instruction.

### `git reset`
Ref: [Blog](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)
- `git reset`: Cancel add
- `git reset --soft HEAD^`: Cancel commit
