# git-workflow hello

1. 从 master 分支新建并检出 develop 分支
```
git branch develop master    # 从master分支上新建develop分支
git checkout develop    # 检出develop分支
# 此处可进行功能开发，并add和commit到develop分支
git push origin develop    # 推送develop分支到远端的origin/develop
```
2. 线上版本的代码（master分支）出现了紧急bug，需要修复。这里用到了hotfix分支。
```
git checkout master    # 切换回master分支
git checkout -b hotfix master    # 新建hotfix分支，并切换到该分支
......                 # 做一些bug修复工作
git checkout master    # 切换回master分支
git merge --no-ff hotfix    # 合并hotfix分支，此时bug已被修复（无冲突）
git tag v0.2    # 新建tag v0.2
git push origin master    # 推送master分支代码到远端
git push origin --tags    # 推送tag到远端
```
3. 这里可以继续develop分支，并不断push到远端。此时如果团队成员增加，多人需要开发不同的功能，这里就会用到feature分支。团队中的每个人都从Github克隆一个项目，然后新建自己的feature分支。
```
git clone xxxx.git
git checkout develop
git checkout -b feature-xx develop    # 从develop分支新建并检出feature分支
```