### 构建镜像
``` shell
$ docker build -t swagger-hub:1.0 .
```

### 运行容器
- 使用默认端口号8080
``` shell
$ docker run -d --name api-docs -p 8080:8080 swagger-hub:1.0
```
- 环境变量覆盖默认端口号
``` shell
$ docker run -d --name api-docs -p 7777:7777 -e SWAGGER_HUB_PORT=7777 swagger-hub:1.0
```
- 命令行选项覆盖默认端口号
``` shell
$ docker run -d --name api-docs -p 7777:7777 swagger-hub:1.0 --port 7777
```
- 将本地[OpenAPI](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md)文档目录挂载至容器
``` shell
$ docker run -d --name api-docs -v /Users/voidint/api:/opt/swagger-hub/web/api -p 7777:7777 swagger-hub:1.0 --port 7777
```