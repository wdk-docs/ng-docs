# 链接库

在库工作时， 通常使用[`npm link`](https://docs.npmjs.com/cli/link)来避免在每个版本上重新安装库。

虽然这非常有用，但有一些注意事项需要注意。

## 该库需要兼容AOT

Angular CLI即使没有`--aot`标志也会进行静态分析，以便检测懒惰路由。
如果你的库不兼容AOT，你可能会得到一个静态分析错误。

## 库仍然需要在每次更改时重建

Angular库通常使用TypeScript构建，因此需要在发布前进行构建。
对于简单的情况，即使没有构建步骤，链接库也可能工作，但这是例外而不是常规。

如果库不是使用自己的构建步骤构建的， 那么它正在由Angular CLI构建系统进行编译，并且不能保证它将被正确构建。
即使它适用于开发，它在部署时也可能无法运行。

When linking a library remember to have your build step running in watch mode and the library's `package.json` pointing at the correct entry points (e.g. 'main' should point at a `.js` file, not a `.ts` file).

## 使用TypesScript路径映射进行对等关系

Angular库应该列出所有`@angular/*`依赖关系[Peer Dependencies](https://nodejs.org/en/blog/npm/peer-dependencies/).
这确保了当模块要求Angular时，它们都得到完全相同的模块。
如果一个库在`dependencies`中列出`@angular/core`而不是`peerDependencies`，那么它可能会得到一个*不同的* Angular模块，这会导致你的应用程序中断。

在开发一个库时，你需要通过`devDependencies`来安装所有的同级依赖，否则你将无法编译。
然后，链接库将拥有它自己的一组Angular库，它用于构建，位于它的`node_modules`文件夹中。
这可能会在构建或运行应用程序时造成问题。

为了解决这个问题，你可以使用TypeScript[路径映射](https://www.typescriptlang.org/docs/handbook/module-resolution.html#path-mapping).
有了它，你可以告诉TypeScript它应该从特定位置加载一些模块。

您应该在`./tsconfig.json`中列出您的库使用的所有对等项依赖项，并将它们指向应用程序`node_modules`文件夹中的本地副本。
这可以确保您始终会加载您的库要求的模块的本地副本。

```json
{
  "compilerOptions": {
    // ...
    // Note: these paths are relative to `baseUrl` path.
    "paths": {
      "@angular/*": [
        "../node_modules/@angular/*"
      ]
    }
  }
}
```