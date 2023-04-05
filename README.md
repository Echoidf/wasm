# wasm
Build Java code and compile to wasm file to support javascript on a browser

参考：
- [wasm 中文网](http://webassembly.org.cn/)
- [wasm for java | blog](http://blog.dmitryalexandrov.net/webassembly-for-java-developers/)
- [Teavm](https://www.teavm.org/docs/tooling/idea.html)


根据维基百科，WebAssembly（通常简称为 Wasm）是一种开放标准，它定义了可执行程序的可移植二进制代码格式、相应的文本汇编语言，以及用于促进此类程序与其宿主环境之间交互的接口。WebAssembly 的主要目标是在网页上启用高性能应用程序，但该格式也旨在在其他环境中执行和集成。

Wasm 代码（二进制或字节码）旨在在便携式虚拟堆栈机 (VM) 上运行。VM 的设计速度比 JavaScript 更快，可以解析和执行，并具有紧凑的代码表示。Wasm 程序被设计成一个单独的模块，包含各种 wasm 定义的值和程序类型定义的集合，这些定义以二进制或文本格式（两者具有共同的结构）表示。

除了在虚拟机中，wasm 还可以编译为本机二进制文件（使用 3rd 方编译器），这是一种将通常不是本机的东西发布为本机的简单方法，只要它不需要大量的运行时库。


## Teavm

TeaVM 是 Java 字节码到 JavaScript 的提前编译器。依赖于现有的编译器，例如 javac、kotlinc 和 scalac。这些编译器生成字节码（*.class或*.jar文件），然后 TeaVM 使用该字节码并生成 JavaScript 代码。

## 项目启动流程

1. 确保 maven 依赖已成功导入
2. IDEA 需要添加扩展 TeaVM Integration
3. 配置 Tomcat 并启动 【可以按照 Teavm 官网中介绍进行配置】
4. 配置 teavm-dev-server 并启动，**注意**：Proxy 配置项设置为 tomcat 服务器运行地址 【teavm 相当于代理服务器，默认启动在 9090 端口，会从Proxy配置中访问 tomcat 的资源】
5. mvn package 指令生成 wasm文件
6. 浏览器访问 http://localhost:9090
