[![Build Status](https://app.travis-ci.com/Rigrey/lab04.svg?token=sSjKqXpxzeqqaxAwq5f2&branch=main)](https://app.travis-ci.com/Rigrey/lab04)
## Laborary work II
Данная лабораторная работа посвещена изучению систем контроля версий на примере Git.
## Tutorial

```shell
export GITHUB_USERNAME=Rigrey
export GITHUB_EMAIL=ozhogin.m@gmail.com
export GITHUB_TOKEN=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
alias edit=gnome-text-editor
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace$ source ./scripts/activate
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace$ mkdir ~/.config
mkdir: cannot create directory ‘/home/rigrey/.config’: File exists
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace$ cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: ssh  
EOF
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace$ git config --global hub.protocol ssh
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace$ mkdir projects/lab02 && cd projects/lab02
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git init -b main
```
Initialized empty Git repository in /home/rigrey/VS/TIMP/Rigrey/workspace/projects/lab02/.git/
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git config --global user.name ${GITHUB_USERNAME}
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git config --global user.email ${GITHUB_EMAIL}
```
ozhogin.m@gmail.com
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git remote add origin git@github.com:${GITHUB_USERNAME}/lab02.git
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git pull origin main
```
fatal: couldn't find remote ref main
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ touch README.md
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git status
```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	README.md

nothing added to commit but untracked files present (use "git add" to track)
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git add README.md
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git commit -m "added README.md"
```
[main (root-commit) 39aec97] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git push origin main
```
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 217 bytes | 217.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Rigrey/lab02.git
 * [new branch]      main -> main
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git pull origin main
```
From github.com:Rigrey/lab02
 * branch            main       -> FETCH_HEAD
Updating 39aec97..ed55ce3
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git log
```
commit ed55ce33454876a67d116f9d2bd7ec8af2652900 (HEAD -> main, origin/main)
Author: Rigrey <76261099+Rigrey@users.noreply.github.com>
Date:   Mon Apr 22 17:41:37 2024 +0300

    Create .gitignore

commit 39aec977af9e28b05cf12a6a2f74099dcba19685
Author: Rigrey <ozhogin.m@gmail.com>
Date:   Mon Apr 22 17:38:22 2024 +0300

    added README.md
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ mkdir sources && mkdir include && mkdir examples
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
```
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```
```shell
edit README.md
git status
```
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	examples/
	include/
	sources/

nothing added to commit but untracked files present (use "git add" to track)
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git add .
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git commit -m "added everything"
```
[main a22b43b] added everything
 4 files changed, 32 insertions(+)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
```shell
rigrey@hmnah:~/VS/TIMP/Rigrey/workspace/projects/lab02$ git push origin main
```
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (9/9), 935 bytes | 935.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Rigrey/lab02.git
   ed55ce3..a22b43b  main -> main

