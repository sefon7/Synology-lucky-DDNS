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

动态域名列表可以写两个，一个是你的域名本身地址，另一个是*.你的地址（意思是CF可以代理NAS的其他服务，包括Jellyfin, komanga等服务）  
<img width="638" height="112" alt="Screenshot 2025-07-17 200117" src="https://github.com/user-attachments/assets/434a4cbf-81d6-45f5-b124-dd478a5ae229" />




## 端口转发相关
### 因为cloudflare不支持自定义端口，因此如果需要使用cloudflare代理，需要用到lucky web服务中的反向代理功能
web服务端口转发教程：https://www.bilibili.com/opus/945751949168345108  
https://blog.aliluya.com/archives/GzxQ6QUf  
https://zhuanlan.zhihu.com/p/671514074 （其中包括SSL证书/HTTPS 教程)  
Cloudflare支持的端口：https://chjina.com/archives/191  

以Https 端口 2053 为例， NAS代理规则如下：
<img width="787" height="99" alt="Screenshot 2025-07-17 195307" src="https://github.com/user-attachments/assets/f1a5a93c-d73d-4368-8bda-33305506f8dc" />    

<img width="418" height="518" alt="Screenshot 2025-07-17 200943" src="https://github.com/user-attachments/assets/354fbfe4-f4a7-492e-94cf-e00dc1e19f09" />    



## 将http反向代理到https中

如何让大多数nas的http服务走CF代理以确保家用网络安全？我们仍需要前面说到的lucky端口转发服务。我们以CF的https端口8443为例，


<img width="813" height="154" alt="Screenshot 2025-07-17 202107" src="https://github.com/user-attachments/assets/32e1ba8e-838a-4918-9e4e-d78a0d19eb03" />

**其中我们转发了nas中的mango,Komaga和Jellyfin服务，其中后面白色框的地址为在nas中的原始http地址加原始端口号。蓝色部分为转发到CF的https地址+代理8443端口号**













