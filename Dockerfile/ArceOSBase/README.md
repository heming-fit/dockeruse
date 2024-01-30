# ArceOS Base Container
开箱即用的 ArceOS 编译环境主要用于学习和开发，基础镜像：ubuntu:22.04
> - ArceOS 是一个开源的、组件化的 Unikernel。以组合组件库的方式构建系统。
### 拉取镜像
```
docker pull zerounnet/arceos_base:latest
```
### 或本地构建镜像
```
git clone https://github.com/heming-fit/dockeruse
docker build ./dockeruse/Dockerfile/ArceOSBase/ -t zerounnet/arceos_base:latest 
```
### 启动镜像
```
docker run -it --name arceos zerounnet/arceos_base:latest bash
```
### 运行 helloworld unikernel
```
make ARCH=riscv64 A=apps/helloworld run
```
官方安装文档
> https://rcore-os.cn/arceos-tutorial-book/ch01-00.html