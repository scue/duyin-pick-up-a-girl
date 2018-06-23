# 抖音撩妹Mac版

<img src="https://media-1256569450.cos.ap-chengdu.myqcloud.com/blog/15297410838729.jpg" alt="alt text" style="width:800px;">

<img src="https://media-1256569450.cos.ap-chengdu.myqcloud.com/blog/15297415494852.jpg" alt="alt text" style="width:600px;">

## Build Setup

``` bash
# install dependencies
yarn install

# build
yarn build

# run the bundled script
yarn start
```

For detailed explanation on how things work, consult the [Vuido documentation](https://vuido.mimec.org/).

## 打包App

- 先制作一个`heart.icns`图标文件

- 使用`launchui-packager`进行打包

```sh
launchui-packager --icon /tmp/heart.icns my-girlfirend 0.0.2 ./dist/main.js
```

输出的文件：

```txt
my-girlfirend-v0.0.2-darwin-x64
├── my-girlfirend.app/
├── LICENSE.launchui
├── LICENSE.libui
└── LICENSE.node
```

`my-girlfirend.app`就是我们想要的`.app`程序。

## 打包DMG

简要步骤：
- 新建空白镜像：磁盘工具→文件→新建映射→空白映像...
- 拷贝App的文件夹：`cp -av my-girlfirend.app /Volumes/Girl/`
- 链接应用程序：`ln -sv /Applications /Volumes/Girl/`
- 背景图片：`cp /tmp/bg-cover.jpg /Volumes/Girl/bg-cover.jpg`
- 调整镜像的背景为图片：在Finder空白处右击→查看显示选项→背景，将图片拖拽进来即可
- 隐藏背景图片：`chflags hidden /Volumes/Girl/bg-cover.jpg`
- 重新制作镜像：磁盘工具→映像→转换...→压缩

镜像实际存储的文件：

```txt
├── Applications -> /Applications/
├── my-project.app/
└── bg-cover.jpg
```