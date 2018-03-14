# Angular CLI 配置架构

## 选项

- **project**: 该项目的全局配置。
    - *name* (`string`): 项目的名称。
    - *ejected*(`boolean`): 这个项目是否被推出。 默认是`false`。

- **apps** (`array`): 此项目中不同应用程序的属性。
    - *name* (`string`): 应用的名称。
    - *root* (`string`): 应用程序的根目录。
    - *outDir* (`string`): 生成结果的输出目录。 默认是`dist/`.
    - *assets* (`array`): 应用程序资产列表。
    - *deployUrl* (`string`): 将部署文件的URL。
    - *index* (`string`): 开始HTML文件的名称。 默认是`index.html`
    - *main* (`string`): 主入口点文件的名称。
    - *polyfills* (`string`): polyfills入口点文件的名称。 在应用之前加载。
    - *test* (`string`): 测试入口点文件的名称。
    - *tsconfig* (`string`): TypeScript配置文件的名称。 默认是`tsconfig.app.json`.
    - *testTsconfig* (`string`): 单元测试的TypeScript配置文件的名称。
    - *prefix* (`string`): 要应用于生成的选择器的前缀。
    - *serviceWorker* (`boolean`): 来自@angular/service-worker的服务工作者的实验支持。 默认是`false`.
    - *showCircularDependencies* (`boolean`): 在构建上显示循环依赖关系警告。 默认是`true`.
    - *styles* (`string|array`): 全局样式将包含在构建中。
    - *stylePreprocessorOptions* : 传递给样式预处理器的选项。
      - *includePaths* (`array`): 包含的路径。 路径将被解析为项目根目录。
    - *scripts* (`array`): 全局脚本包含在构建中。
    - *environmentSource* (`string`): 环境配置的源文件。
    - *environments* (`object`): 环境配置的名称和相应的文件。

- **e2e**: 端到端测试的配置。
    - *protractor*
        - *config* (`string`): 配置文件的路径。

- **lint** (`array`): 要传递给TSLint的属性。
    - *files* (`string|array`): File glob(s) to lint.
    - *project* (`string`): tsconfig.json项目文件的位置。 如果'files'属性不存在，也将使用文件作为lint。
    - *tslintConfig* (`string`): tslint.json配置的位置。 默认是`tslint.json`.
    - *exclude* (`string|array`): File glob(s) to ignore.


- **test**: 单元测试的配置。
    - *karma*
        - *config* (`string`): 业务配置文件的路径。
    - *codeCoverage*
        - *exclude* (`array`): 从代码覆盖范围中排除的Globes。

- **defaults**: 指定生成的默认值。
    - *styleExt* (`string`): 用于样式文件的文件扩展名。
    - *poll* (`number`): 多久检查一次文件更新。
    - *class*: 生成类的选项。
        - *spec* (`boolean`): 指定是否生成规格文件。默认是`false`.
    - *component*: 生成组件的选项。
        - *flat* (`boolean`): 标记以指示是否创建了dir。默认是`false`.
        - *spec* (`boolean`): 指定是否生成规格文件。默认是`true`.
        - *inlineStyle* (`boolean`): 指定样式是否在ts文件中。 默认是`false`.
        - *inlineTemplate* (`boolean`): 指定样式是否在ts文件中。 默认是`false`.
        - *viewEncapsulation* (`string`): 指定视图封装策略。 可以是`Emulated`，`Native`或`None`之一。
        - *changeDetection* (`string`): 指定更改检测策略。 可以是`Default`或`OnPush`之一。
    - *directive*: 生成指令的选项。
        - *flat* (`boolean`): 标记以指示是否创建了dir。 默认是`true`.
        - *spec* (`boolean`): 指定是否生成规格文件。 默认是`true`.
    - *guard*: 生成警卫的选项。
        - *flat* (`boolean`): 标记以指示是否创建了dir。 默认是`true`.
        - *spec* (`boolean`): 指定是否生成规格文件。 默认是`true`.
    - *interface*: 生成界面的选项。
        - *prefix* (`string`): 应用于接口名称的前缀。 (即 I)
    - *module*: 生成模块的选项。
        - *flat* (`boolean`): 标记以指示是否创建了dir。 默认是`false`.
        - *spec* (`boolean`): 指定是否生成规格文件。 默认是`false`.
    - *pipe*: 生成管道的选项。
        - *flat* (`boolean`): 标记以指示是否创建了dir。 默认是`true`.
        - *spec* (`boolean`): 指定是否生成规格文件。 默认是`true`.
    - *service*: Options for generating a service.
        - *flat* (`boolean`): 标记以指示是否创建了dir。 默认是`true`.
        - *spec* (`boolean`): 指定是否生成规格文件。 默认是`true`.
    - *build*: 要传递给构建命令的属性。
        - *sourcemaps* (`boolean`): 输出源地图。
        - *baseHref* (`string`): 正在构建的应用程序的基础URL。
        - *progress* (`boolean`): 构建时将进度记录到控制台。 默认是`true`.
        - *poll* (`number`): 启用并定义文件观看轮询时间段（毫秒）。
        - *deleteOutputPath* (`boolean`): 生成之前删除输出路径。 默认是`true`.
        - *preserveSymlinks* (`boolean`): 解析模块时请勿使用真实路径。 默认是`false`.
        - *showCircularDependencies* (`boolean`): 在构建上显示循环依赖关系警告。 默认是`true`.
        - *namedChunks* (`boolean`): 使用懒惰加载块的文件名。
    - *serve*: 要传递给serve命令的属性
        - *port* (`number`): 应用程序将被提供的端口。默认是`4200`.
        - *host* (`string`): 应用程序将被提供给主机。默认是`localhost`.
        - *ssl* (`boolean`): 为应用程序启用ssl。默认是`false`.
        - *sslKey* (`string`): 服务器使用的ssl密钥。默认是`ssl/server.key`.
        - *sslCert* (`string`): 服务器使用的ssl证书。默认是`ssl/server.crt`.
        - *proxyConfig* (`string`): 代理配置文件。

- **packageManager** (`string`): 指定使用哪个软件包管理器工具。 选项包括`npm`，`cnpm`和`yarn`。

- **warnings**: 允许用户禁用控制台警告。
    - *nodeDeprecation* (`boolean`): 当节点版本不兼容时显示警告。 默认是`true`.
    - *packageDeprecation* (`boolean`): 当用户安装角度cli时显示警告。 默认是`true`.
    - *versionMismatch* (`boolean`): 当全局版本比本地版本更新时显示警告。 默认是`true`.
