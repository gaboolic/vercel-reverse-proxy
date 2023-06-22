# vercel-reverse-proxy
[English README](./README_EN.md)

本项目是vercel反向代理。完全免费，万能代理，可代理全网一切接口，包括openai、github、google等等。http和https接口、单页面均可代理，在网络环境不好的情况下均可用。（直接浏览器打开代理页面的情况下，由于某些js和css的路径可能会不对造成访问不到，页面样式有点小问题。）

vercel现在每月有100GB的免费流量。本人又基于[cloudflare](https://www.cloudflare.com/)搞了一个反向代理，仓库地址：[cloudflare-reverse-proxy](https://github.com/gaboolic/cloudflare-reverse-proxy)供大家参考，也作为一个备份吧。

## 部署
[![Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/gaboolic/vercel-reverse-proxy)


## 使用方法
1 部署。部署有两种方法，一是直接点击上方按钮一键部署，二是可以先fork本项目，再登录[vercel](https://vercel.com/)网站新建。vercel可以通过github一键注册只需要绑定手机号支持cn
![新建项目](img/newproject.png)

2 绑定自己的域名(不是必须，使用vercel自带的子域名也可以，但是自带的域名vercel.app在国内网络环境不好的情况下不可用) 可以申请[tk免费域名](http://www.dot.tk/)或者薅小域名注册商首年免费羊毛
![绑定域名](img/domain.png)
绑定域名时按照vercel上的说明配置即可，其实就是在你的域名上配了一个子域名，cname到vercel服务器

3 访问 域名/proxy/url  或者/httpproxy/url即可。
映射规则为/proxy/url映射到https接口，/httpproxy/url映射到http接口

## 示例
例1 访问https://替换为你自己的域名.com/proxy/api.openai.com/v1/chat/completions 
实际上会替换为https://api.openai.com/v1/chat/completions
![demo1](img/demo1.png)

如何在一些常见的开源项目中使用？
一般开源项目都是引用的openai的库，可以看到里面有一个属性是api_base = os.environ.get("OPENAI_API_BASE", "https://api.openai.com/v1")

所以使用的时候只需要设置一下openai.api_base="https://你的域名/proxy/api.openai.com/v1" 就可以了

例2 访问https://替换为你自己的域名.com/proxy/raw.githubusercontent.com/gaboolic/vercel-reverse-proxy/main/vercel.json
实际上会替换为https://raw.githubusercontent.com/gaboolic/vercel-reverse-proxy/main/vercel.json
![demo2](img/demo2.png)
映射规则为/proxy/url映射到https接口，/httpproxy/url映射到http接口

也可用于github下载加速。假如原始链接是https://objects.githubusercontent.com/github-production-release-asset-2e65be/xxxxxx 
改为https://替换为你自己的域名.com/proxy/objects.githubusercontent.com/github-production-release-asset-2e65be/xxxxxx 就可以加速了。下图是github原始链接和加速后对比。可以看到效果杠杠的，每秒50kb小水管变成了每秒2mb的大水管
![github-download](img/github-download.png)

例3 访问https://替换为你自己的域名.com/proxy/www.google.com/search?q=vercel-reverse-proxy
实际上会替换为https://www.google.com/search?q=vercel-reverse-proxy
![demo3](img/demo3.png)
代理google搜索结果页面
