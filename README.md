# 雀魂 Ex

雀魂 Ex（Majsoul Ex）是一款基于雀魂网页版进行二次开发的第三方客户端, 目前客户端支持 Windows/macOS/Linux/Android/iOS 五大平台, 由于本项目开发及维护者仅有一人故更新时间并不稳定。

## 统一发布/下载地址

[https://github.com/moxcomic/majsoul-ex/releases](https://github.com/moxcomic/majsoul-ex/releases)

## PC 端

### 开发语言

`Golang`、`HTML`、`JavaScript`、`Chromium`

### 使用方式

macOS、Linux 由于系统权限原因需要先使用`chmod +x`添加运行权限  
运行一次软件后软件会在当前目录创建各个功能不能的文件夹, 由于 GUI 暂时没有时间写所以请务必记住各个文件夹的使用方式, 后续有空了会添加 GUI 界面设置

### 文件夹用途介绍

- \[已废弃\]Cache: 在首次加载资源时会被备份到此目录一份, 原用途已废弃现仅作为查看资源使用
- Extensions: 可放置游戏插件（在雀魂 Plus 上扩展被分为`扩展`与`资源包`并且两个的清单文件分别为`extension.json`与`resourcepack.json`, 在雀魂 Ex 看来这俩完全没有必要区分并且统合为`插件`, 目前只要放入该文件夹里的不管是`扩展`还是`资源包`均会被正常读取加载, 并且由于雀魂 Plus 遗留问题较多后续雀魂 Ex 将会定义新的`插件开发方式`）
- Replace: 在该文件夹的资源文件在启动时会替换掉游戏内的对应资源（例如要替换/foo/bar/ui.png 就在该目录新建 foo 和 bar 文件夹并且路径为`/foo/bar`, 然后在该路径下放入要替换的`新ui.png`即可在启动后替换掉对应资源）
- UserData: Chromium 核心浏览器缓存

### config.json

chromium_browser_file_path: 如果系统没有查找到 chrome 浏览器请在此处手动指定浏览器地址, 必须指定 chromium 内核的浏览器, 否则不会生效  
not_cache_files: 已废弃  
special_cache_files: 已废弃  
proxy: 代理设置（仅支持 http/https）

- enable: true/false
- scheme: http/https
- url: 127.0.0.1
- port: 端口号

### FAQ

## Mobile 移动端

### 开发语言

Android: Kotlin、Java  
iOS: Swift、OC

### Android 安卓

没有特殊说明

### FAQ

Q: 为什么字体显示乱码？  
A: 请手动切换一次语言, 例如当前游戏语言为简体中文就手动切到繁体中文后再切回来.

Q: 为什么更新后没有新活动或者刷新不出资源?  
A: 请手动删除一次 Cache 文件夹, 路径为/Android/data/com.yuuki.majsoulex/files/Cache

Q: 为什么无法加载出源以及首页显示为空？  
A: 因为部署的服务器在海外, 如无法正常访问/下载请使用 VPN

Q: 如何安装插件?
A: 可以通过内置的插件源下载, 或者其他途径下载到的插件点击选择其他应用打开后往下滑找到雀魂 Ex 选择打开即可

### iOS 苹果

由于 iOS 系统特殊限制安装需要签名, 具体办法请自行解决, 如果赞助的多了后会考虑其他方案.

### FAQ

Q: 为什么无法签名?  
A: 开发者测试并没有任何问题可以正常签名, 请检查您的签名方式

Q: 签名提示 Arch 结构错误?  
A: 开发者测试签名正常, 请检查您的签名方式

Q: 如何安装插件?  
A: 由于系统限制原因只能通过内置插件源进行下载

## 联系方式

- B 站 ID: [神崎·H·亚里亚](https://space.bilibili.com/898411/)
- B 站 ID: [关野萝可](https://space.bilibili.com/612462792/)
- QQ 交流群: [991568358](https://jq.qq.com/?_wv=1027&k=3gaKRwqg)
- Twitter: @MajsoulEx

## 赞助

如果对您有所帮助，欢迎您的赞赏

<figure class="third">
    <img src="https://moxcomic.github.io/wechat.png" width=300>
    <img src="https://moxcomic.github.io/alipay.png" width=300>
    <img src="https://moxcomic.github.io/qq.png" width=300>
</figure>
