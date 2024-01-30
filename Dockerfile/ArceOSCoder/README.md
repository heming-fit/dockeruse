# ArceOS Coder Container
开箱即用的 ArceOS 编译环境主要用于学习和开发，基础镜像：ubuntu:22.04
> - ArceOS 是一个开源的、组件化的 Unikernel。以组合组件库的方式构建系统。
> - 在镜像中集成了 vscode 和 rust 编程环境，降低新手入门门槛
### 拉取镜像
```
docker pull zerounnet/arceos_coder:latest
```
### 或本地构建镜像
```
git clone https://github.com/heming-fit/dockeruse
docker build ./dockeruse/Dockerfile/ArceOSCoder/ -t zerounnet/arceos_coder:latest 
```
### 启动镜像
```
docker run -p 8080:8080 -d  --name coder zerounnet/arceos_coder:latest
```
### 访问开发环境
```
http://localhost:8080
```