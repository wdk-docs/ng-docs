# Angular CLI

> 本文档整理翻译自 Angular CLI GitHub [Wiki](https://github.com/angular/angular-cli.wiki.git) 页面

> 工具使用：以下是文档制作工具，如果有更好的文档制作方法，欢迎在[Issues](https://github.com/wohugb/ng-docs/issues)中留言

> * 编辑器 VS Code, 插件修改自[chun.vscode-translate]作为即时翻译用
> * 文档语言markdown
> * 文档生成器mkdocs,使用mkdocs-material模板
> * 寄存于gh-page

## 概述

The Angular CLI is a tool to initialize, develop, scaffold  and maintain [Angular](https://angular.io) applications

## 入门

To install the Angular CLI:

```bash
npm install -g @angular/cli
```

Generating and serving an Angular project via a development server [Create](new) and [run](serve) a new project:

```bash
ng new my-project
cd my-project
ng serve
```

Navigate to http://localhost:4200/. The app will automatically reload if you change any of the source files.

## 捆绑

All builds make use of bundling, and using the `--prod` flag in  `ng build --prod` or `ng serve --prod` will also make use of uglifying and tree-shaking functionality.

## 单元测试

```bash
ng test
```

Tests will execute after a build is executed via [Karma](http://karma-runner.github.io/0.13/index.html), and it will automatically watch your files for changes. You can run tests a single time via `--watch=false` or `--single-run`.

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
