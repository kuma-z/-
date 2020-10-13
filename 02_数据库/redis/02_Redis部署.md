# Redis部署

## 服务器部署

`docker run --name redis -p 6379:6379 -d redis`



## 客户端链接

`docker run -it --net=host -rm redis redis-cli`