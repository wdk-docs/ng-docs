# 更改Autoprefixe的目标浏览器

Currently, the CLI uses [Autoprefixer](https://github.com/postcss/autoprefixer) to ensure compatibility
with different browser and browser versions. You may find it necessary to target specific browsers
or exclude certain browser versions from your build.

Internally, Autoprefixer relies on a library called [Browserslist](https://github.com/ai/browserslist)
to figure out which browsers to support with prefixing.

There are a few ways to tell Autoprefixer what browsers to target:

## 将一个browserslist属性添加到`package.json`文件中

```json
"browserslist": [
  "> 1%",
  "last 2 versions"
]
```

## 将一个新文件添加到名为`.browserslistrc`的项目目录中

```bash
### Supported Browsers

> 1%
last 2 versions
```

Autoprefixer will look for the configuration file/property to use when it prefixes your css.
Check out the [browserslist repo](https://github.com/ai/browserslist) for more examples of how to target
specific browsers and versions.

_Side note:_
Those who are seeking to produce a [progressive web app](https://developers.google.com/web/progressive-web-apps/) and are using [Lighthouse](https://developers.google.com/web/tools/lighthouse/) to grade the project will
need to add the following browserslist config to their package.json file to eliminate the [old flexbox](https://developers.google.com/web/tools/lighthouse/audits/old-flexbox) prefixes:

`package.json` config:

```json
"browserslist": [
  "last 2 versions",
  "not ie <= 10",
  "not ie_mob <= 10"
]
```
