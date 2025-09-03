---
create date: 2024-03-06
modification date: 2024-03-06T14:00:00
tags:
  - 程序员
  - "#git"
  - 计算机工具学习
type: LearningNote
---
[Git and GitHub for Beginners - Crash Course](https://www.youtube.com/watch?v=RGOj5yH7evk&list=WL&index=1&t=2252s)
# Basic Knowledges and Concepts
## local/remote repository，add，commit，push，pull
## pull request(PR)

---
# Commands
> [!note] init and create a new repository, check status
> ```
>> git init
>> git add folder-name
>> git status
> ```

 >[!note] git commit 用法
 > ```
 >> git commit -m "Your commit message"
 > ``` 

> [!note] git branch 创建，切换，删除branch
> ```
> > git branch
>>  git checkout -b <brach_name>
>>  git branch -d branch name 
>  ```

> [!note] git push --set-upstream 创建一个新 branch in remote repository
> ```
>>  git push -set-upstream/-u origin <brach_name>
> ```
---
# Real examples
>[!question] 如何将之前 fork 的 main branch 转到 new branch 下

```git
git remote add upstream [original repository URL] git fetch upstream
git checkout -b [new branch] upstream/[new branch]
git push origin [new branch]
```