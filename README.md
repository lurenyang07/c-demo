# 静态库与动态库的简单使用案例

## 生成动态库

```shell
gcc -fPIC -shared -o lib/libhello.so hello.c

# 等价于如下两句
gcc -fPIC -c hello.c
# 生成 hello.o
gcc -shared -o libhello.so hello.o
```

测试

```shell
# 编译
gcc -o main main.c -I./include -L./lib -lhello
# 临时设置动态链接库
export LD_LIBRARY_PATH=lib
# 运行
./main
```

## 生成静态库

```shell
gcc -c hello.c # hello.o
# 静态打包
ar -rcs lib/libhello.a hello.o # libhello.a
```

测试

```shell
gcc -o main main.c -Iinclude -Llib -lhello
# 运行
./main
```

