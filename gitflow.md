# Git Flow工作流

## Git Flow使用介绍

### 命令行
待续。。。
### SourceTree
待续。。。
## 项目开发流程
### Start Feature
```shell
git flow feature start bestpay
```
此命令相当于
```shell
git checkout -b feature/bestpay develop
```
### 开发
开发、自测
提交代码
```shell
git commit -am "..."
```
### 提交测试
开发自测完成后，将feature分支push到远程
```shell
git flow feature publish bestpay
```
此命令相当于
```shell
git push origin feature/bestpay
```
### 测试
从远程获取feature分支
```shell
git flow feature pull origin bestpay
```
此命令相当于
```shell
git checkout -b feature/bestpay origin/feature/bestpay
git pull
```
### 修复bug
重复前面3步

### 测试通过
```shell
git flow feature finish bestpay
```
此命令会将bestpay合并到本地develop，并删除本地bestpay分支

### 创建release
```shell
git flow release start v1.0
git flow release publish v1.0
```
### 集成测试
从远程获取release分支
```shell
git flow release pull origin v1.0
```
### 修复bug
应在release/v1.0分支上修复
```shell
git flow release pull origin v1.0
git commit -m "..."
git flow release publish origin v1.0
```
### 集成测试通过
```shell
git flow release finish v1.0
```
此命令将release/v1.0合并到本地develop和本地master
```shell
git push origin master
git push origin develop
```

## 紧急BUG修复流程
### Start Hotfix
```shell
git flow hotfix start alipay_notice_failed
```
此命令相当于
```shell
git checkout -b hotfix/alipay_notice_failed master
```
### 开发
开发、自测
提交代码
```shell
git commit -am "..."
```
### 提交测试
开发自测完成后，将hotfix分支push到远程
```shell
git flow hotfix publish alipay_notice_failed
```
此命令相当于
```shell
git push origin hotfix/alipay_notice_failed
```
### 测试
从远程获取hotfix分支
```shell
git flow hotfix pull origin alipay_notice_failed
```
此命令相当于
```shell
git checkout -b hotfix/alipay_notice_failed origin/hotfix/alipay_notice_failed
git pull
```
### 修复bug
重复前面3步

### 测试通过
```shell
git flow hotfix finish alipay_notice_failed
```
此命令会将alipay_notice_failed合并到本地develop和本地master
```shell
git push origin master
git push origin develop
```