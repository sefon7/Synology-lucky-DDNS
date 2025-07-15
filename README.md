# Synology-lucky-Cloudflare-DDNS
如何使用lucky在群晖实现DDNS并且映射相关服务,同时部署Cloudflare防护服务


## 群晖安装Lucky 插件
Lucky 官网：https://lucky666.cn/

使用Docker 部署lucky/SSL/反向代理/HTTPS 等，参考：https://blog.aliluya.com/archives/GzxQ6QUf

也可通过安装矿神插件中的lucky直接部署，矿神源网站：https://imnks.com/1780.html

## Cloudflare 域名注册相关
官网：https://www.cloudflare.com/zh-cn/products/registrar/

 <ins>同时可以将阿里云或者腾讯云域名通过更改DNS转移到Cloudflare，但是不如直接在cloudflare直接注册方便</ins>

 部署和配置API相关：https://www.ioiox.com/archives/105.html



## 如果配置合理，在cloudflare的DNS解析记录中应显示如下图（代理小黄云一栏应显示灰色“未代理”），并且已经可以通过域名在外网访问

![屏幕截图 2025-05-22 174517](https://github.com/user-attachments/assets/24873752-9a6c-445f-81b6-77dda61a0087)


### 因为cloudflare不支持自定义端口，因此如果需要使用cloudflare代理，需要用到lucky web服务中的反向代理功能
