<p align="center">
  <picture>
    <source srcset="./img/logo.svg">
    <img alt="xpoc" src="./img/logo.svg" width="352" height="59" style="max-width: 100%;">
  </picture>
</p>

<h3 align="center">
    XPOC 安全能力概念验证框架
</h3>

<p align="center">
    <a href="https://github.com/chaitin/xpoc/releases">
        <img alt="GitHub release" src="https://img.shields.io/github/release/chaitin/xpoc.svg?style=for-the-badge">
    </a>

</p>

<p align="center">简洁的命令行工具，快速发现安全问题</p>
<p align="center">提供精选插件和灵活的自定义能力</p>

```mermaid

flowchart
    plugin --> capabilities
    subgraph plugin [系统]
        go(Golang插件) -- 增强 --> yaml(YAML插件)
    end
    subgraph capabilities [能力]
        direction LR
        aaa(目标探活)
        aab(指纹识别)
        aac(漏洞扫描)
        aaa --> aab
        aab -- 辅助 --> aac
        aaaa(服务指纹识别)
        aaab(WEB指纹识别\nxmap-暂未发布)
        aaac(供应链漏洞发现)
        aaad(DAST漏洞发现\nxscan-暂未发布)
        aab --> aaaa
        aab --> aaab
        aac --> aaac
        aac --> aaad
    end
    classDef x fill: #FFFBC1, stroke: #FEBE8C, stroke-width: 4px;
    style plugin fill: #F7F7F7, stroke-width: 2px, stroke: #F7F7F7
    style capabilities fill: #F7F7F7, stroke-width: 20px, stroke: #F7F7F7
    class go,yaml,a,b,aa,ab,bb,aaa,aab,aac,aaaa,aaab,aaac,aaad,aaae,aaaf x;
```

## 一键安装

windows:

```

```

linux:

```

```

mac:

```

```

## 执行扫描

xpoc -t http://testtest.fun
