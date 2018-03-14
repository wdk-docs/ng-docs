# 应用程序中

## 配置可用的环境

`.angular-cli.json`包含**environments**部分。默认情况下，这看起来像：

``` json
"environments": {
    "dev": "environments/environment.ts",
    "prod": "environments/environment.prod.ts"
}
```

您可以根据需要添加其他环境。  添加**staging**环境, 你的配置看起来像这样：

``` json
"environments": {
    "dev": "environments/environment.ts",
    "staging": "environments/environment.staging.ts",
    "prod": "environments/environment.prod.ts"
}
```

## 添加特定于环境的文件

环境特定的文件如下所示：

```bash
└── src
    └── environments
        ├── environment.prod.ts
        └── environment.ts
```

如果你想为**staging**添加另一个环境，你的文件结构将变成：

```bash
└── src
    └── environments
        ├── environment.prod.ts
        ├── environment.staging.ts
        └── environment.ts
```

## 修改环境特定的文件

`environment.ts`包含默认设置。  如果你看一下这个文件，它应该看起来像这样：

``` TypeScript
export const environment = {
  production: false
};
```

如果你将它与`environment.prod.ts`进行比较， 这看起来像：

``` TypeScript
export const environment = {
  production: true
};
```

您可以添加更多变量，或者作为`environment`对象的附加属性， 或作为单独的对象，例如：

``` TypeScript
export const environment = {
  production: false,
  apiUrl: 'http://my-api-url'
};
```

## 在应用程序中使用特定于环境的变量

鉴于以下应用程序结构：

```bash
└── src
    └── app
        ├── app.component.html
        └── app.component.ts
    └── environments
        ├── environment.prod.ts
        ├── environment.staging.ts
        └── environment.ts
```

在`app.component.ts`内使用环境变量可能如下所示：

``` TypeScript
import { Component } from '@angular/core';
import { environment } from './../environments/environment';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  constructor() {
    console.log(environment.production); // Logs false for default environment
  }
  title = 'app works!';
}
```

## 特定于环境的构建

运行:

```bash
ng build
```

将使用`environment.ts`中的默认值

运行:

```bash
ng build --env=staging
```

将使用`environment.staging.ts`中的值
