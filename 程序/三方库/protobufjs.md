# 安装
1. 初始化 package.json 文件
```
npm init
```
在项目根目录下创建 package.json 文件。

2. 安装 protobufjs
```
npm install protobufjs@5 --save
```
使用 npm 安装 protobufjs 包至项目工程目录，指定 5.x 版本。

3. 安装 protobufjs-cli
```
npm install protobufjs-cli -g
```
使用 npm 全局安装 protobufjs-cli 最新版本包，方便命令行操作。

# 使用
1. 定义 .proto 文件
```
syntax = "proto3";

message Person {
  string name = 1;
  int32 id = 2;
  string email = 3;
}
```
定义一个 Person 类型，包含 name、id、email 三个字段。

2. 编译 .proto 文件并生成 TypeScript 声明文件
```
pbjs -t static-module -w commonjs -o message.js message.proto
pbts -o message.d.ts message.js
```
编译 message.proto 文件，生成 message.js 文件，并生成 message.d.ts 文件。