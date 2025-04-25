> 前言： 如果没有自己的服务器，如何实现接口去获取图片呢？我们可以使用图床的形式。

#### 图床的概念

> 图床就是存储图片的服务器

**由来：**使用Typora，图片都默认保存在本地，共享笔记，需要将笔记图片同步（同时确保路径正确），才能确保他人完整查看笔记。
**解决：**这时候我们想到如果把图片放在互联网上，这时候任何人都可以看见并且能下载，就完美解决了。那么我们把别人也可以访问到图片的服务器叫做图床。

**GitHub创建图床服务器**

步骤：

1）新建仓库

>点击+号->New repository->填写相关信息-> Create repository

2）生成Token令牌

>点击右上角头像->Settings->下拉，直到左侧到底，选择Developer settings（开发人员设置）->Personal Access tokens（个人访问令牌） -> Tokens(classic) -> Generate New Token(classic， 一定要选择 classic 方式)-> 配置相关信息 -> Generate token
>
>Token令牌用于个人身份验证，不需要密码也可以直接访问你的仓库内容。
>
>
>
>在创建页面中，填写 Note 为“图床”，Expiration（过期时间）为 No expiration（永久）,也可以自定义过期时间，在下面的Select scopes（选择权限范围）如下图勾选 repo。最后点击 generate token 生成令牌即可。
>
>
>
>务必将令牌保存起来，放在一个安全的地方，页面关掉后就看不到了。

3）创建img分支和该分支下的img文件夹(可选)

>创建img分支：点击自己的仓库->main->View all branches->New branch->分支名->Create new branch
>
>
>
>创建img文件夹：Add file -> Create new file -> 填写 img/test -> Commit changes

**使用PicGo软件上传图片**

- 下载PicGo软件:

> PicGo是一个用于上传图片的客户端，支持拖拽上传、剪贴板上传，功能十分方便。

- 配置PicGo->选择图床设置->Github

> 这里需要配置GitHub仓库地址、分支名、AccessToken等基础信息。
> 自定义域名需要配置为：https://cdn.jsdelivr.net/gh/用户名/仓库名，这样就才可以通过cdn访问图片
>
> 仓库名：GitHub用户名/GitHub仓库地址
> 分支名：GitHub的分支名称
> Token：GitHub中设定的AccessToken
> 自定义域名：https://fastly.jsdelivr.net/gh/用户名/仓库名

- 用PicGo实现上传：直接拖拽上传即可

> 上传完成会在相册中查看到或者直接在GitHub仓库中查看

- Typora实现自动上传

> Typora通过PicGo软件自动上传图片到GitHub仓库中。
>
> 文件 ->偏好设置 -> 图像 -> 上传图片 -> 配置PicGo路径
