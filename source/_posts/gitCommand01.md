---
title: Git常用指令
date: 2020-01-03 10:46:13
tags: git
---

## 基础指令

### 初始化仓库

<pre style='background:#e6e6e6;padding=10px;'>

    git init

</pre>

### 添加文件到缓冲区

<pre style='background:#e6e6e6;padding=10px;'>
    
    git add filename

</pre>

### 添加所有文件到缓冲区

<pre style='background:#e6e6e6;padding=10px;'>
    
    git add .
    git add --all

</pre>

### 清除缓冲区

<pre style='background:#e6e6e6;padding=10px;'>
    
    git rm -r --cached

</pre>

### 删除文件

<pre style='background:#e6e6e6;padding=10px;'>
    
    git rm filename

</pre>

### 提交备注

<pre style='background:#e6e6e6;padding=10px;'>
    
    git comment -m '备注内容'

</pre>

<code style='background:#ff3385;color:white;padding:5px;'>注意：git add或git comment失败将不会提交。所以，comment必须有备注内容</code>

### 查看状态

<pre style='background:#e6e6e6;padding=10px;'>
    
    git status

</pre>

### 查看差异

<pre style='background:#e6e6e6;padding=10px;'>
    
    git diff filename

</pre>

### 版本回退

<pre style='background:#e6e6e6;padding=10px;'>
    
    git reset
    git reset --hard HEAD^
    git reset --hard version

</pre>

### 日志查看

<pre style='background:#e6e6e6;padding=10px;'>
    
    git log
    git reflog

</pre>

## 分支管理

### 查看当前分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git branch

</pre>

### 创建分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git branch branchName

</pre>

### 切换分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git checkout branchName

</pre>

### 创建并切换分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git checkout -b branchName

</pre>

### 删除分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git branch -d branchName

</pre>

### 合并某分支到当前分支

<pre style='background:#e6e6e6;padding=10px;'>
    
    git merge branchName

</pre>

## 标签操作

### 创建标签

<pre style='background:#e6e6e6;padding=10px;'>
    
    git tag tagName version

</pre>

### 查看标签

<pre style='background:#e6e6e6;padding=10px;'>
    
    git tag

</pre>

### 查看标签详情

<pre style='background:#e6e6e6;padding=10px;'>
    
    git show tagName

</pre>

### 推送某个tag

<pre style='background:#e6e6e6;padding=10px;'>
    
    git push origin v1.0

</pre>

### 推送所有tag

<pre style='background:#e6e6e6;padding=10px;'>
    
    git push origin --tags

</pre>

## 远端库相关

### 添加远端库

<pre style='background:#e6e6e6;padding=10px;'>
    
    git remote add origin git://xxx/abc.git

</pre>

### 移除远端库

<pre style='background:#e6e6e6;padding=10px;'>
    
    git remote remove origin git://xxx/abc.git

</pre>

### 推送到远端

<pre style='background:#e6e6e6;padding=10px;'>
    
    git push -u origin master

</pre>

### 更新远端的内容到本地

<pre style='background:#e6e6e6;padding=10px;'>
    
    git pull

</pre>

## 组合提交指令

<pre style='background:#e6e6e6;padding=10px;'>
    
    git rm -r --cached
    git add .
    git comment -m 'update'
    git push origin master

</pre>