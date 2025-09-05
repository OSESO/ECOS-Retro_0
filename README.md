## 编译流程
建议将编译环境配置为如下结构
```
.
├── README.md
├── src
└── tools   // 放置编译工具链
```
### 配置依赖
本工程依赖RISCV交叉编译工具链，建议下载仓库提供的[工具链](https://github.com/OSESO/ECOS-Retro_0/releases/tag/v0.1)进行配置。

下载完成之后需要将``riscv/bin``添加到环境变量`` PATH``中,示例如下：
```
export PATH=$PATH:/home/timmo/ECOS_env/tools/riscv/bin
```
### 编译
完成环境配置之后，只需要在``./src``路径下执行``Make``指令,即可生成对应的可执行文件


## 致谢
- 【代码编写】 [maksyuki](https://github.com/maksyuki/maksyuki)
- 【整理维护】 [XHTimmo](https://github.com/XHTimmo)