# Angular CLI

> 本文档整理翻译自 Angular CLI GitHub [Wiki](https://github.com/angular/angular-cli.wiki.git) 页面

> 工具使用：以下是文档制作工具，如果有更好的文档制作方法，欢迎在[Issues](https://github.com/wohugb/ng-docs/issues)中留言

> * 编辑器 VS Code, 插件修改自[chun.vscode-translate]作为即时翻译用
> * 文档语言markdown
> * 文档生成器mkdocs,使用mkdocs-material模板
> * 寄存于gh-page

## 概述

Angular CLI是初始化，开发，支撑和维护[Angular](https://angular.io)应用程序的工具

## 入门

要安装Angular CLI：

```bash
npm install -g @angular/cli
```

通过开发服务器生成并提供Angular项目[创建](new)和[运行](serve)新项目：

```bash
ng new my-project
cd my-project
ng serve
```

导航到http://localhost:4200/. 如果您更改任何源文件，该应用程序将自动重新加载。

## 捆绑

所有版本都使用捆绑， 并在`ng build --prod`或`ng serve --prod`中使用`--prod`标志也将利用`uglifying`和`tree-shaking`摇晃功能。

## 单元测试

```bash
ng test
```

测试将在通过[Karma](http://karma-runner.github.io/0.13/index.html)执行构建之后执行, 它会自动监视你的文件的变化。 您可以通过`--watch = false`或`--single-run`运行一次测试。

## 端到端测试

```bash
ng e2e
```

在运行测试之前，请确保您通过“ng serve”服务应用程序。
端到端测试通过[量角器](https://angular.github.io/protractor/)运行.

## 其他命令

* [ng new](new)
* [ng serve](serve)
* [ng generate](generate)
* [ng lint](lint)
* [ng test](test)
* [ng e2e](e2e)
* [ng build](build)
* [ng get/ng set](config)
* [ng doc](doc)
* [ng eject](eject)
* [ng xi18n](xi18n)
* [ng update](update)

## 配置架构

* [配置架构](angular-cli)

## 附加信息

有几个[故事](stories)会引导您设置Angular应用程序的其他方面。
