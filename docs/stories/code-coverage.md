# 代码覆盖率

使用Angular CLI，我们可以运行单元测试以及创建代码覆盖率报告。
代码覆盖率报告允许我们看到我们的代码库中的任何部分可能没有通过我们的单元测试进行正确测试。

要生成覆盖率报告，请在项目的根目录下运行以下命令

```bash
ng test --watch=false --code-coverage
```

一旦测试完成，一个新的`/ coverage`文件夹将出现在项目中。
在Finder或Windows资源管理器中打开`index.html`文件。
您应该看到一份包含您的源代码和代码覆盖率值的报告。

使用代码覆盖百分比，我们可以估计我们的代码有多少被测试。
由您的团队决定应该测试多少代码。

## 代码覆盖实施

如果您的团队决定将设定的最小数量作为单元测试，您可以使用Angular CLI强制执行此最小值。
例如，我们的团队希望代码库至少有80％的代码覆盖率。
要启用此功能，请打开`karma.conf.js`，并在`coverageIstanbulReporter：`键中添加以下内容

```javascript
coverageIstanbulReporter: {
  reports: [ 'html', 'lcovonly' ],
  fixWebpackSourcePaths: true,
  thresholds: {
    statements: 80,
    lines: 80,
    branches: 80,
    functions: 80
  }
}
```

在项目中运行单元测试时，`thresholds`属性将强制执行至少80％的代码覆盖率。