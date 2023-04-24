# vercel-reverse-proxy
vercel反向代理

## 部署
[![Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/gaboolic/vercel-reverse-proxy)


## 使用方法
1 部署。部署有两种方法，一是直接点击上方按钮一键部署，二是可以先fork本项目，再登录[!vercel](https://vercel.com/)网站新建

2 绑定自己的域名(不是必须，使用vercel自带的子域名也可以，但是自带的域名vercel.app在国内网络环境不好的情况下不可用)


3 访问 域名/proxy/url即可。例如访问https://替换为你自己的域名.com/proxy/api.openai.com/v1/chat/completions，实际上会替换为https://api.openai.com/v1/chat/completions
