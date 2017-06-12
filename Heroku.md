# **部署到 Heroku**

* 创建 Heroku App，并同时命名

```
$ heroku create <项目名称>
```

* 重新命名 Heroku App

```
$ heroku apps:rename <新的项目名称>
```

* 把 master 进度部署到 Heroku

```
$ git push heroku master
```

* 把 branch 进度部署到 Heroku

```
$ git push <分支名称>:master
```

* 执行所有 Migration

```
$ heroku run rake db:migrate
```

<br/>

# **查看设置 & 日志**

- 查看项目的远端路径（ GitHub、Heroku）。

```
$ git remote -v
```

- 查看日志（Logs）

```
$ heroku logs
```

<br/>

# **Heroku 服务器端資料**

* 使用远端 Rails Console，可用于：新增或修改資料，操作方式和本地的 Rails Console 相同，輸入 `$ exit` 可以退出

```
$ heroku run rails console
```

* 利用 seed.rb 文件內容创建数据

```
$ heroku run rake db:seed
```

* 清空数据库

```
$ heroku pg:reset DATABASE
```

<br/>

# **Heroku 版本回退**

## **Step 1. 查看过去版本号**

輸入后，终端会列出所有的版本号（每一次推送部署到 Heroku 就有一个版本号），找到要回退的版本号

* 查看部署日志

```
$ heroku releases
```

从版本号日志，你可以看到这几个部分：
1. 版本号
1. 部署內容
1. 部署者
1. 日期 / 时间

## **Step 2. 將 Heroku App 回退至该版本**

接着只要根据指令，退回到该版本即可。

* 將 Heroku 回退到指定版本

```
$ heroku rollback <版本号>
```

<br/>

# **Heroku 多人协作**

多人协作時，要让其他开发者一起参与 Heroku 的部署，可以参照以下步骤：


## **Step 1. Heroku App 的拥有者（Owner）添加协作者（Collaborator）名单**

* 终端执行指令

```
$ heroku access:add <电子邮件账号地址>
```

## **Step 2. 协作者在本地设置 Heroku 远端路径。**

协作者会收到一封 Email，通知已经被加入协作名单。这时候只要为本地的项目添加 Heroku 的远端路径，就可以参与部署了。

- 新增项目的 Heroku 远端路径。

```
$ heroku git:remote -a <项目名称>
```

<br/>

## **补充：协作相关指令**

* 查看拥有权限的协作成员名单

```
$ heroku access
```

* 移除协作成员

```
$ heroku access:remove <电子邮件账号地址>
```

------

<完>
