# github



## github网站访问

世界范围比较有影响力的，项目托管网站，大量的私人工程或企业级项目在此网站托管发布，里面也包含大量的开源内容，软件研发工程的工具类网站

* 常用工具栏

  * topic分类查看
* trending推送查看
  * 搜索栏

    * 关键词查询内容
* 按标签查询（sample,tutorial）例如：socket sample

## 项目结构

* 仓库：工程存储单位，一般一个仓库中存储一个独立项目，一个用户可以有若干个仓库

  * CODE：存储开源数据，开源代码，后续用户下载开源项目，下载就是code中的全部内容

  * ISSUES：问答板块，解决项目异常，提交bug

  * REDEME.md：工程自述文件，进行项目介绍，版本答疑，使用markdown语言编写

  * 许可证：GPL3.0   Aphache2.0  MIT  ，给使用者最小的限制，最大的权力（法务问题）

    

## git的配置，工程的上传下载

* 云端仓库（托管在github中）
  * 设备认证，生成密钥串，粘贴到github账户中，让设备受信任，后续可以完成内容上传
  * 创建本地仓库，出现（master）标志，标识仓库所在位置，默认.git仓库是隐藏文件，使用`git init`

* 关于（master）分支概念：
  * 分支：资源存储单位，仓库包含分支，默认情况下仓库都有主分支，默认所有数据都向主分支存储，一个仓库可以有多个分支
  * 多人协作开发，对分支进行管理或合并，一系列相关命令，创建分支，删除分支，分支选择等等

[负责人图流](https://i.imgs.ovh/2026/09/15/f945f6e4215c1e3ffc32dadde5509bd1.png)

后续上传时，分支名相同则合并，不同则在云端创建新分支，存储用户上传内容

## 配置相关命令

* `ssh -T git@github.com `   测试设备是否关联成功

* `git config --list `    查看git本地配置文件

* 在git配置文件中加入两条新配置

  * `git config --global user.email "my email"`

  * `git config --global user.name "my name"`

* 生成密钥文件，传输加密方式选择分非对称rsa加密（设备指纹）
  * ssh-keygen -t rsa -C "my email"  **记住密钥的生成位置，找到密钥文件，复制密钥串**
  * 根据提供的位置，打开.pub密钥文件，复制其中密钥字符串，粘贴到指定位置
    * 头像（menu）-->settings -->SSH and GPG key -->New SSH key -->粘贴密钥-->add SSH key
    * 再次使用`ssh -T git@github` 测试受否成功关联

## 本地数据上传过程，以及版本更新

相互依赖关系，本地为新版，云端为旧版（发行版），版本更新使用本地新内容同步给云端

* 本地数据到云端同步（增，删，改） **上传可以是以目录为单位，也可以是单个文件**
* 使用`git remote`命令创建ssh地址别名
  * `git remote add origin origin git@github.com:kskbl-zdjd/colinstudy.git`
  * `git remote remove origin`删除别名
* 从本地发送文件到云端，相关命令
  * `git add test.cpp` 从开发主机发送到git缓冲区
    * `git status` 查看缓冲区
    * `git rm file` 从缓冲区中删除
    * `git restore file` 如果本地磁盘删除，可以通过此命令恢复
  * `git commit -m "说明"` 通过提交命令，将数据提交到本地仓库
    * 用户的每次提交commit系统进行代码的备份，进行交叉对比，有一个提交列表，存储这些备份，可以通过提交功能，回溯到任意时刻删除或修改的位置
  * `git push origin master` 将本地master数据推送到origin指向的云端仓库中

[数据提交一图流](https://img.remit.ee/i/1cKdXytEZgeu)

<!--如果要进行删除的更新，那么逻辑是一样的，本地先删除，然后将这个删除同步到云端，如果push失败，大概率是本地数据与云端不一致导致，先pull拉回去，修正后再次push-->

## 下载开源项目

所有以git仓库为单位的操作都与开发有关，只是打包下载开源代码和资源文件而已

**命令下载：** `git clone 工程https地址`
