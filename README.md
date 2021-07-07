# VLESS Heroku

## 概述

用于在 Heroku 上部署 vless+websocket+tls，每次部署自动选择最新的 alpine linux 和 v2ray core 。  
vless 性能更加优秀，占用资源更少。

## 镜像

经测试本镜像不会因为大量占用资源而被封号。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https%3A%2F%2Fgithub.com%2Fziiyc%2Fvlessheroku)

## 注意

### 路径

`WebSocket` 路径(配置文件中的 `path` )为 `/app` 。

### 端口

`端口` 为 `443` 。

### alterId

`alterId` 为 `0` 。

### UUID

`UUID` 默认为 `3a53a3e5-da83-48d2-aee9-d88a498eb3dd` 可自行设置。

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  

addEventListener(  
    "fetch",event => {  
        let url=new URL(event.request.url);  
        url.hostname="xx.xxxx.xx";//你的heroku域名    
        let request=new Request(url,event.request);  
        event. respondWith(  
            fetch(request)  
        )  
    }  
)  
