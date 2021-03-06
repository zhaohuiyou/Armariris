### 修改

（1）将Obfuscation pass在LLVM中由静态库(.a文件)修改为动态库(.dylib)，可以直接又opt加载启动，输入bitcode或者IR文件，混淆输出IR文件；

（2）增加了虚假控制流；

# Armariris
孤挺花（Armariris） --  由上海交通大学密码与计算机安全实验室维护的LLVM混淆框架

主要作者：f1ys0ar（https://github.com/flysoar/ ）

## 中文
孤挺花（Armariris）: 基于LLVM的支持多平台多语言的混淆器

本项目名取自细音启小说<黄昏色的咏使>以及<冰洁镜界的伊甸>中的人物孤挺花. 她即便无人理解依然守护着姐姐与世界. 

Armariris是作者自创语言Selahpheno中孤挺花的意思.

目前开放功能包括：
 - 字符串加密.
  ![sobf](sobf.png)
- 控制流扁平化+虚假控制流
  ![fla](fla.png)
- 指令替换
  ![sub](sub.png)

### 安装

```shell
mkdir obf
cd obf
clone git@github.com:gossip-sjtu/Armariris.git
cmake -DCMAKE_BUILD_TYPE:String=Release ./Armariris
make -j 4
```

### 用法
使用opt加载LLVMObfuscation.dylib

控制流扁平化+虚假控制流

```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -flattening test.ll -o out.bc -- [编译参数]
```
指令替换

```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -substitution test.ll -o out.bc -- [编译参数]
```
字符串加密

```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -GVDiv test.ll -o out.bc -- [编译参数]
```

## English

Armariris: an obfuscator based on LLVM project for multiple languages and platforms. 

Currently support:
 - string obfuscation
 - control flow flattening and bogus control flow
 - instruction substitutions


### Armariris
Armariris is the alias of Amaryllis in conlang Selahpheno in sazaneK's light novel. 
Amaryllis is a character in light novel <黄昏色の詠使い> and <氷結鏡界のエデン> written by 細音啓(sazaneK). 
Although nobody unserstands her, she still guards her sister and the world persistently.


### Install
```shell
mkdir obf
cd obf
clone git@github.com:gossip-sjtu/Armariris.git
cmake -DCMAKE_BUILD_TYPE:String=Release ./Armariris
make -j4
```

### Usage
string obfuscation. 
```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -GVDiv test.ll -o out.bc -- [compiler args]
```
control flow flattening and bogus control flow. 
```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -flattening test.ll -o out.bc -- [compiler args]
```
instruction substitutions. 
```shell
./bin/opt -load ./lib/LLVMObfuscation.dylib -substitution test.ll -o out.bc -- [compiler args]
```
