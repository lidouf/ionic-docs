---

---

# Ionic CLI

Ionic命令行接口([CLI](/docs/faq/glossary#cli))是用来开发Ionic应用的快捷工具。

## 安装

Ionic CLI可以使用npm进行全局安装：

```shell
$ npm install -g ionic
```

## 帮助

Ionic CLI自带了命令行方式的文档，可以使用`--help`选项进行访问。

```shell
$ ionic <command> --help
```

<!-- TODO: image? -->

## 架构

Ionic CLI使用[TypeScript](/docs/faq/glossary#typescript)和[Node.js](/docs/faq/glossary#node)进行构建。它支持Node 6+，但我们始终推荐最新版的Node LTS版本。关注<a href="https://github.com/ionic-team/ionic-cli" target="_blank">Github仓库</a>的开发。

## 问题解决

关于Ionic CLI使用的问题，下面这些方法可能有用：

- Make sure the latest version of the Ionic CLI is installed. Update with `npm install -g ionic@latest`.
- Make sure the latest Node LTS is installed. See [Node & npm](/docs/installation/environment#node-npm) environment setup.
- The `--verbose` flag prints debugging messages, which may narrow down the issue.
- Connection issues may be due to improperly configured proxy settings. See [Using a Proxy](/docs/cli/configuring#using-a-proxy) to configure request proxying.
- The global Ionic CLI configuration directory is `~/.ionic` on all platforms. It can safely be deleted and the Ionic CLI will repopulate it, but all configuration (including user sessions) will be lost. Configure this directory with [CLI environment variables](/docs/cli/configuration#environment-variables).
