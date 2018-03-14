# 配置热模块加载

热模块替换（HMR）是一种WebPack功能，可在正在运行的应用程序中更新代码而无需重新构建代码。
这导致更快的更新和更少的完整页面重新加载。

您可以通过访问此[页面](https://webpack.js.org/guides/hot-module-replacement)阅读有关HMR的更多信息.

为了让HMR与Angular CLI协同工作，我们首先需要添加一个新环境并启用它。

接下来，我们需要更新我们的应用程序的启动过程以启用[`@angularclass/hmr`](https://github.com/AngularClass/angular-hmr)模块。

## 为HMR添加环境

使用以下内容创建一个名为`src/environments/environment.hmr.ts`的文件：

```typescript
export const environment = {
 production: false,
 hmr: true
};
```

更新`src/environments/environment.prod.ts`并将`hmr:false`标志添加到环境中：

```typescript
export const environment = {
 production: true,
 hmr: false
};
```

更新`src/environments/environment.ts`并将`hmr:false`标志添加到环境中:

```typescript
export const environment = {
 production: false,
 hmr: false
};
```

通过向现有环境对象添加新环境来更新`.angular-cli.json`:

```json
"environmentSource": "environments/environment.ts",
"environments": {
  "dev": "environments/environment.ts",
  "hmr": "environments/environment.hmr.ts",
  "prod": "environments/environment.prod.ts"
},
```

使用`--hmr -e=hmr`标志运行`ng serve`来启用hmr并选择新的环境：

```bash
ng serve --hmr -e=hmr
```

通过更新`package.json`并向脚本对象添加一个条目来为此创建一个快捷方式:

```json
"scripts": {
  ...
  "hmr": "ng serve --hmr -e=hmr"
}
```

## 为`@angularclass/hmr`添加依赖项并配置应用程序

为了让HMR工作，我们需要安装依赖项并配置我们的应用程序来使用它。

安装`@angularclass/hmr`模块作为dev-dependency

```bash
...
$ npm install --save-dev @angularclass/hmr
```

使用以下内容创建一个名为`src/hmr.ts`的文件：

```typescript
import { NgModuleRef, ApplicationRef } from '@angular/core';
import { createNewHosts } from '@angularclass/hmr';

export const hmrBootstrap = (module: any, bootstrap: () => Promise<NgModuleRef<any>>) => {
  let ngModule: NgModuleRef<any>;
  module.hot.accept();
  bootstrap().then(mod => ngModule = mod);
  module.hot.dispose(() => {
    const appRef: ApplicationRef = ngModule.injector.get(ApplicationRef);
    const elements = appRef.components.map(c => c.location.nativeElement);
    const makeVisible = createNewHosts(elements);
    ngModule.destroy();
    makeVisible();
  });
};
```

更新`src/main.ts`来使用我们刚创建的文件：

```typescript
import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';
import { environment } from './environments/environment';

import { hmrBootstrap } from './hmr';

if (environment.production) {
  enableProdMode();
}

const bootstrap = () => platformBrowserDynamic().bootstrapModule(AppModule);

if (environment.hmr) {
  if (module[ 'hot' ]) {
    hmrBootstrap(module, bootstrap);
  } else {
    console.error('HMR is not enabled for webpack-dev-server!');
    console.log('Are you using the --hmr flag for ng serve?');
  }
} else {
  bootstrap();
}
```

## 启用HMR启动开发环境

现在一切都已设好，我们可以运行新的配置:

```bash
...
$ npm run hmr
```

当启动服务器时，Webpack会告诉你它已经启用:

    注意为开发服务器启用热模块更换（HMR）。

现在，如果您对其中一个组件进行了更改，则应该在没有完整浏览器刷新的情况下自动显示更改。