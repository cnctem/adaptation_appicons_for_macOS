# macOS 应用图标制作教程

## -1. 正道明示

根据[苹果设计规范](https://developer.apple.com/design/resources/)，Apple图标设计需要使用 [**Sketch**](https://sketch.com/s/0ee52d20-8daf-49ef-b335-14020af3b060) / **Photoshop** [**Illustrator**](https://devimages-cdn.apple.com/design/resources/download/iOS-26-Icon-Templates-Photoshop-Illustrator.dmg) / [**Figma**](https://www.figma.com/community/file/1514335373494164156/app-icon-template) 其一来完成

如果这条路不是你力所能及，那请往下看

## 0. 前言

- 很多全平台开发者为 macOS 打包了应用包（如通过 Flutter、Wails），但苦于没有测试环境，对 mac 开发也不大了解，无法为应用程序制作系统风格统一的图标。
- 也有些使用 mac 的个人开发者，没有足够的精力使用专业的设计软件设计图标，团队中也没有UI同学，也无法为应用配置优雅的图标

- 如果你也有这方面的困扰，请跟我来！

## 1. 明晰步骤

- 需要准备一个原始像素大于`1024x1024`的`.png`图片
- macOS 应用图标是一个有背景色的圆角正方形外缘有留白多尺寸版本和对应配置文件组成的`.icns`图集(老规范)或者`AppIcon.appiconset`目录(新规范)。
- 最终图标会以`*.icns`格式出现在`*.app/Resources`目录，并呈现在其该有的位置上

1. 原始图标制作（请各位八仙过海）
2. 圆角制作
3. 留白处理
4. 制作多尺寸版本和描述文件
5. 制作`.icns`

## 2. 圆角制作

- 如果你的原始图标是一个类符形图标，只需增添背景便可以，那请直接进入第三步xxx
- 如果你导出的是一个正方形图标，可以通过原制作圆角设计圆角，也可以通过ppt图片-裁剪为形状-圆角矩形 功能调节原始图片圆角，圆角曲率参考…
## 3. 留白处理

- 使用开源项目 [appicon-forge](https://github.com/zhangyu1818/appicon-forge) 的 [page](https://zhangyu1818.github.io/appicon-forge/)，上传图片，边框最细，调节主图尺寸，默认勾选留白，下载（没渲染成功随便再点几下重新下载）

## 4. 制作多尺寸版本和描述文件

### mac用户

在 AppStore 安装应用 appIconMaker 根据应用内指引导出`AppIcon.appiconset`

### 非mac

#### (1) 制作多尺寸版本

使用[在线工具](https://uiedtool.com/tools/design/icon-generator?sharetype=link)完成

#### (2) 制作描述文件

##### 文件样例

## 5. 制作`.icns`(可选)

有些框架(如 Flutter)的打包流程只需要`AppIcon.appiconset`就可以产出图标正常的应用包，无需压合`.icns`

### mac用户

1. 将 `AppIcon.appiconset`重命名为`AppIcon.iconset`
2. 打开终端 cd 到`AppIcon.iconset`所在目录
3. 输入指令`iconutil -c icns AppIcon.iconset`

### 非mac

- 用 Github Actions 参考上文指令解决
