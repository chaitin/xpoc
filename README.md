<h1 align="center">
	<img src="https://docs.xray.cool/assets/xpoc/xpoc-logo.svg" alt="xpoc" width="200px">
	<br>
</h1>

<h3 align="center">为供应链漏洞扫描设计的快速应急响应工具</h3>

<p align="center">
  <img src="https://img.shields.io/github/release/chaitin/xpoc.svg" />
  <a href="https://docs.xray.cool/#/xpoc">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
</p>

<p align="center">
  <a href="#-快速开始">快速开始</a> •
  <a href="#-特点">特点</a> •
  <a href="#-安装使用">使用</a> •
  <a href="#-贡献-poc">贡献</a> •
  <a href="https://github.com/chaitin/xpoc/releases">下载</a> •
  <a href="https://docs.xray.cool/xpoc">使用文档</a> 
</p>

---

<img src="https://docs.xray.cool/assets/eme.gif" />

## 🚀 快速使用

**在使用之前，请务必阅读并同意 [License](./LICENSE.md) 文件中的条款，否则请勿安装使用本工具。**

1. 拉取所有云端POC并扫描指定目标

   - `./xpoc -t https://example.com -html result.html`

2. 查看所有云端的POC

   - `./xpoc list -a`

3. 批量扫描

   - `./xpoc < targets.txt`
   - ` cat targets.txt | ./xpoc`
   - `./xpoc -i targets.txt`

## 🪟 特点

1. 支持云端获取POC，可以以最快的速度进行应急响应
2. 使用xray yaml poc脚本格式，支持TCP/UDP协议的插件的编写和加载，并可以使用golang自定义插件实现功能增强
3. 自定义golang插件，支持更多种的漏洞检测，支持加载工具插件等
   - 漏洞扫描
   - 向yaml脚本注入新功能
   - 自定义爬虫
   - 网页截图
   - ...

## 📦 安装使用

在[releases](https://github.com/chaitin/xpoc/releases)中下载对应的系统的最新版即可，运行`xpoc -h`即可查看帮助

```bash
  __  /\    /\_.  ___.  _____
  | |/ /   / __.\/ __.\/ ____|
  |   /XRAY™/_/ / / / / /
 / . |   / .___/ /_/ / /___.
/ /|_|  / /    \____/\____/
\/v0.0.1\/cloud plugins: [3]
[INFO] 2023-05-18 19:31:51 use config at: C:\Users\77905\.xray\xpoc-config.yaml [strategy.go:30]
[INFO] 2023-05-18 19:31:51 load plugins form: [C:\Users\77905\.xray\xpoc\plugins] [loader.go:123]
NAME:
  xpoc - light poc scanner

USAGE:
  Scan single target:      xpoc -t https://example.com
   └>  multiple targets:   xpoc -t 192.168.0.1,192.168.0.1:443,tcp://192.168.1.1:8000
  Input from file:         xpoc -i targets.txt
   └>   from pipe:         cat targets.txt | xpoc
  Output to JSON:          xpoc -t https://example.com -json result.json
   └>    to HTML:          xpoc -t https://example.com -html result.html
  Run plugins form cloud:  xpoc -r 1 -t http://example.com
   └> plugins from local:  xpoc -r ./poc-yaml-example.yaml -t http://example.com
  List local plugins:      xpoc list
   └>  cloud plugins:      xpoc list -a
  Pull all cloud plugins:  xpoc pull
   └>  specific plugins:   xpoc pull -id 1

COMMANDS:
  add      将文件添加到插件仓库
  pull     下载及更新插件
  list     列出插件
  run      默认的PoC扫描策略（命令）：
           插件加载逻辑: 将默认加载 ~/.xray/xpoc/plugins(插件仓库) 和 ./tmp-plugin(默认的插件搜索路径,可通过path参数配置) 路径下的插件,
           插件启用逻辑: 按照该配置文件中 enable 的规则, 开启加载和内置插件中的部分插件;
             在命令行中使用 -e (-enable) 参数时，会在 enable 中补充;
             在命令行中使用 -r (-run) 参数时，会将 enable 置空，替换为-r指定的插件
  help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
  --run value, -r value      执行指定插件 多个插件间','分割
  --enable value, -e value   仅启用部分插件，支持glob语法
  --disable value, -d value  禁用部分插件，支持glob语法
  --config value, -c value   指定配置文件
  --debug                    debug (default: false)
  --quiet, -q                不显示banner (default: false)
  -o value                   结果输出: 指定保存结果的文件路径 (result-printer)
  -t value                   扫描目标: 可以为URL/IP/域名/Host:Port等多种形式的混合输入 (util-target-split)
  -i value                   目标文件: 指定含有扫描目标的文本文件 (util-target-split)
  --help, -h                 show help (default: false)
```

## ⚡️ 进阶

下列高级用法请查看 https://docs.xray.cool/ 使用。

 - 修改配置文件
 - go插件编写（施工中）
 - 反连平台的使用
 - ...

## 😘 贡献 POC

xray的进步离不开各位师傅的支持，秉持着互助共建的精神，为了让我们共同进步，xray也开通了“PoC收录”的渠道！在这里你将会得到：

### 提交流程

1. 贡献者以 PR 的方式向 github xray 社区仓库内提交， POC 提交位置: https://github.com/chaitin/xray/tree/master/pocs, 指纹识别脚本提交位置: https://github.com/chaitin/xray/tree/master/fingerprints
2. PR 中根据 Pull Request 的模板填写 POC 信息
3. 内部审核 PR，确定是否合并入仓库
4. 但需要注意，如果想要获得POC的奖励，需要将你的POC提交到[CT stack](https://stack.chaitin.com/poc/list)，才能获取到奖励

### 丰厚的奖励

- 贡献PoC将获得**丰厚的金币奖励**，成就感满满；
- **丰富的礼品**兑换专区，50余种周边礼品任你挑选；
- 定期更有京东卡上线兑换，离**财富自由**又近了一步；
- 进入核心社群的机会，领取特殊任务，赚取**高额赏金**；

### 完善的教程

- 完善的**PoC编写教程和指导**，让你快速上手，少走弯路；

### 学习与交流

- **与贡献者、开发者面对面**学习交流的机会，各项能力综合提高；
- 免笔试的**直通面试机会**，好工作不是梦；

如果你已经成功贡献过PoC但是还没有进群，请添加客服微信：

<img src="https://docs.xray.cool/assets/customer_service.png?cache=_none" height="200px">

提供平台注册id进行验证，验证通过后即可进群！

参照: https://docs.xray.cool/#/guide/contribute

## 🔧周边生态

### POC编写辅助工具

该工具可以辅助生成POC，且在线版支持**poc查重**，本地版支持直接发包验证

#### 在线版
- [**规则实验室**](https://poc.xray.cool)
- 在线版支持对**poc查重**
#### 本地版
- [**gamma-gui**](https://github.com/zeoxisca/gamma-gui)

### xray gui辅助工具

本工具仅是简单的命令行包装，并不是直接调用方法。在 xray 的规划中，未来会有一款真正的完善的 GUI 版 XrayPro 工具，敬请期待。

- [**super-xray**](https://github.com/4ra1n/super-xray)

## 📝 讨论区

提交误报漏报需求等等请务必先阅读 https://docs.xray.cool/#/guide/feedback

如有问题可以在 GitHub 提 issue, 也可在下方的讨论组里

1. GitHub issue: https://github.com/chaitin/xpoc/issues

2. 微信公众号：微信扫描以下二维码，关注我们

<img src="https://docs.xray.cool/assets/wechat.jpg?cache=_none" height="200px">

3. 微信群: 请添加微信公众号并点击“联系我们" -> "加群“，然后扫描二维码加群

4. QQ 群: 717365081