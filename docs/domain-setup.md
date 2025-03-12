# 停车宝网站自定义域名配置指南

## 前提条件

1. 已注册的域名
2. 域名服务商的管理权限
3. 已部署的GitHub Pages网站

## 配置步骤

### 1. 获取GitHub Pages网站地址

1. 进入GitHub仓库设置页面
2. 找到"Pages"选项
3. 记录当前的GitHub Pages URL

### 2. 配置DNS记录

在域名服务商的DNS管理面板中添加以下记录：

#### 方案A：Apex域名（example.com）

添加4条A记录，指向GitHub Pages的IP地址：
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

#### 方案B：子域名（www.example.com）

添加CNAME记录：
- 主机记录：www
- 记录类型：CNAME
- 记录值：您的GitHub Pages地址

### 3. 配置GitHub Pages自定义域名

1. 在仓库设置中找到"Pages"选项
2. 在"Custom domain"字段输入您的域名
3. 点击"Save"
4. 等待DNS生效（通常需要0-48小时）

### 4. 启用HTTPS

1. 等待DNS完全生效
2. 在GitHub Pages设置中勾选"Enforce HTTPS"
3. 等待SSL证书自动配置完成

## 验证配置

1. 使用以下命令验证DNS解析：
```bash
dig YOUR_DOMAIN +noall +answer
```

2. 在浏览器中访问您的自定义域名，确保：
- 网站正常加载
- 地址栏显示安全锁标志（HTTPS）
- 没有证书警告

## 常见问题

### DNS未生效
- 请耐心等待，DNS传播需要时间
- 使用dig命令检查DNS解析
- 确认DNS记录配置正确

### SSL证书问题
- 确保DNS完全生效后再启用HTTPS
- 如遇问题，可以尝试取消并重新启用HTTPS选项

### 404错误
- 确认仓库中存在index.html文件
- 检查GitHub Pages是否正确配置
- 验证分支设置是否正确

## 技术支持

如遇到配置问题，请联系：
- 技术支持邮箱：support@parkingvip.com
- 工作时间：周一至周五 9:00-18:00