## 项目概述

* 产品名称：weibo
* 项目代号：weibo
* 官方地址：未上线

weibo 是 Laravel 中文新手课程《L01 Laravel 教程 - Web 开发实战入门》的个人实现源代码，使用 Laravel5.8 编写而成。

## 功能如下

- 用户认证 —— 注册、登录、退出；
- 个人中心 —— 用户个人中心，编辑资料；
- 邮件发送 —— 注册邮件
- 微博管理 —— 个人发布微博管理，关注者微博
- 粉丝关系 —— 用户关注于被关注，查看数量

## 运行环境要求

- Nginx 1.8+
- PHP 7.1+
- Mysql 5.7+

## 开发环境部署/安装

本项目代码使用 PHP 框架 [Laravel 5.8](https://learnku.com/docs/laravel/5.8/) 开发，本地开发环境使用 [Laravel Homestead](https://learnku.com/docs/laravel/5.5/homestead)。

下文将在假定读者已经安装好了 Homestead 的情况下进行说明。如果您还未安装 Homestead，可以参照 [Homestead 安装与设置](https://learnku.com/docs/laravel/5.5/homestead#installation-and-setup) 进行安装配置。

### 基础安装

#### 1. 克隆源代码

克隆 `larabbs` 源代码到本地：

    > git clone https://github.com/KongWeiMin/weibo.git

#### 2. 配置本地的 Homestead 环境

1). 运行以下命令编辑 Homestead.yaml 文件：

```shell
homestead edit
```

2). 加入对应修改，如下所示：

```
folders:
    - map: ~/my-path/weibo/ # 你本地的项目目录地址
      to: /home/vagrant/weibo

sites:
    - map: weibo.test
      to: /home/vagrant/weibo/public

databases:
    - weibo
```

3). 应用修改

修改完成后保存，然后执行以下命令应用配置信息修改：

```shell
homestead provision
```

随后请运行 `homestead reload` 进行重启。

#### 3. 安装扩展包依赖

	composer install

#### 4. 生成配置文件

```
cp .env.example .env
```

你可以根据情况修改 `.env` 文件里的内容，如数据库连接、缓存、邮件设置等：

```
APP_URL=http://weibo.test
...
DB_HOST=localhost
DB_DATABASE=weibo
DB_USERNAME=homestead
DB_PASSWORD=secret
```

#### 5. 生成数据表及生成测试数据

在 Homestead 的网站根目录下运行以下命令

```shell
$ php artisan migrate --seed
```

初始的用户角色权限已使用数据迁移生成。

#### 7. 生成秘钥

```shell
php artisan key:generate
```

#### 8. 配置 hosts 文件

    echo "192.168.10.10   larabbs.test" | sudo tee -a /etc/hosts

### 前端框架安装

1). 安装 node.js

直接去官网 [https://nodejs.org/en/](https://nodejs.org/en/) 下载安装最新版本。

2). 安装 Yarn

请安装最新版本的 Yarn —— http://yarnpkg.cn/zh-Hans/docs/install

3). 安装 Laravel Mix

```shell
yarn install
```

4). 监控修改并自动编译

```shell
npm run watch-poll
```

### 链接入口

* 首页地址：http://weibo.test/
* 管理后台：没做

至此, 安装完成 ^_^。


## 扩展包使用情况

| 扩展包                                                       | 一句话描述     | 本项目应用场景 |
| ------------------------------------------------------------ | -------------- | -------------- |
| [overtrue/laravel-lang](https://github.com/overtrue/laravel-lang) | Laravel 多语言 | 报错信息本地化 |
