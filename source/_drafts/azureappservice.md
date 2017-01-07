## 使用 Azure APP Service 搭建 Wordpress 站点

搭建Wordpress平台的过程中，大家往往会选择使用VPS或者网络主机等服务。然而在服务稳定性和体系化方面，独立的信息服务商会逊色于由微软提供的Azure云平台。其中Azure在2015年推出了APP Service，可以快速的搭建包括Wordpress在内的服务。

现在Azure国内运营需要1000RMB的预付费，而国外只需要绑定信用卡即可。而且国际版的Azure在服务的更新方面会更快。因此，本文使用国际版的Azure选择东亚节点，搭建Wordpress应用。

### 使用 Godaddy 自定义域名并绑定 Azure APP

需要两步操作：

### HTTPS 安全证书配置

我们可以为自己的站点加入对于https安全协议的支持，也可以使站点更安全和专业。

本文通过腾讯云提供的[免费证书](https://console.qcloud.com/ssl)进行操作：

![腾讯云免费证书](https://ww3.sinaimg.cn/large/006tNbRwgw1fbii23m781j30u20py0u5.jpg)



## 性能优化

### CDN 静态资源浏览器缓存优化





### DNS 解析优化
	
如果使用 Godaddy 注册的域名，在中国国内会发现域名解析的速度非常的慢。相对于 Azure APP Service 提供的默认地址来说，对比尤其明显。因此，我们可以替换 Godaddy 的默认的 DNS 解析服务。这里我们推荐使用 DNSPOD 免费的解析服务。

#### 打开 www.dnspod.cn 并登陆，添加要解析的域名



#### 添加要解析的记录

dnspod 可能会自动自动导入现有Godaddy的解析记录，但可能不全，需要手工补全。



注意，这里的线路类型都应该选择默认。如果选择国外，那么只有国外的用户才会被解析。

#### 到Godaddy通过修改NS记录，切换域名解析到Dnspod




### 增大 Wordpress 的内存使用限制



### 使用 Azure CDN 优化访问速度

对于

### 打开Azure APP Service的Always On

### 使用Wordpress插件优化访问速度

### 使用Google Chrome工具优化访问速度

#### 处理在CDN中 .woff 与 .ttf 的CORS访问限制




## Wordpress 内容

### 组织架构与板块
	- 首页 -> page
	- 发现 -> page
		• 精选小程序
		• 编辑筛选人工推荐
		○ 效率
		○ 购物
		○ 教育
		○ 媒体
		○ 餐饮
		○ 交通
		○ 旅游
		○ 科技
		○ 健康
	- 资讯 -> page
		○ 观点
		○ 动向
	- 教程 -> page
		○ 官方教程
		○ 系列教程
	- 服务 -> page
		• 第三方云服务
		• 腾讯云
		• Azure
		• 阿里云
	- 资源 -> page
		• 工具
		○ 开源组件
		○ 在线服务
		○ GitHub 开源组件
			§ 榜单
	- 人才 -> page
		○ 手工搜罗
		○ 社区
			§ qq群
			§ 微信群
			§ 论坛
	- 关于
		○ 联系
		○ 
