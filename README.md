# 关于雀魂Ex
&emsp;&emsp;雀魂Ex是一款基于WebView(网页浏览器)的第三方移动平台(iOS & Android)客户端,本客户端(iOS & Android)双端均由`神崎·H·亚里亚`一人独立开发,由于本人只会iOS开发故Android版本在一年后终于完成了编写(~~期间也因为各种情况咕咕了许久~~),编写该客户端的初中只是因为2019年在贴吧中看到了雀魂魔改的帖子并且对此产生了兴趣(~~虽然现在已经弃坑不打雀了~~),在搜索到了PC端的魔改客户端`雀魂Plus`后由于其没有移动平台(iOS & Android)客户端便想着自己写一个移动平台的魔改客户端(~~其实是因为那时候天气冷就想着窝在被窝里用手机玩~~)。

&emsp;&emsp;时过境迁,雀魂Ex从2019年开发到现在已经`2周年`了,在这两年里经过不断的踩坑和咕咕,雀魂Ex终于成长为了现在的亚子;由于雀魂Ex(iOS & Android)双端均由一人独自开发与维护,因时间有限后续的开发维护可能不会那么及时,但至少保证在能够使用的程度。

# 免责声明
在您使用`雀魂Ex`进行游戏时造成的`包含但不局限于限制登录、封号等`后果`均由用户自行承担`, `雀魂Ex`不对此承担任何责任!

# 开发进度
- iOS: `3.1.6 正式版`  
- Android: `1.0.1 正式版`

# 开发语言
- iOS: `Swift & Objective-C`  
- Android: `Kotlin & Java`

# 下载地址
- 最新发布版本: [点我进入最新版本页面](https://github.com/moxcomic/majsoul-ex/releases/tag/iOS%2FAndroid)  
- 安卓版本下载: [点我下载最新安卓版本](https://github.com/moxcomic/majsoul-ex/releases/download/iOS%2FAndroid/majsoulex_android_1.0.2.apk)  
- iOS版本下载: [点我下载最新iOS版本](https://github.com/moxcomic/majsoul-ex/releases/download/iOS%2FAndroid/majsoulex_ios_3.1.6.ipa)

# 制作扩展
`待更新...`

# 制作扩展源
1. Github IO Pages
2. 主体文件 src.ex
3. 参考 [src.ex](https://moxcomic.github.io/src.ex)文件编写
    - 点击后会下载到本地
    - 下载完成后使用文本方式打开

## src.ex文件字段解释
- info -> 源的介绍部分
    - id: String -> 用于识别源的ID
    - name: String -> 源的名称, 用于显示在源列表上的名称
    - author: String -> 作者名
    - description: String -> 源的介绍
    - icon: String -> 源的图标, 用于显示在源列表上的图标
        - 可以是http地址
        - 如果只指定名称则默认指向src文件所在的仓库目录下同名文件
- release -> 源的扩展部分
    - id: String -> 用于识别插件的ID
    - name: String -> 插件的名称
    - description: String -> 插件的简介
    - author: String -> 插件作者
    - version: String -> 插件版本
    - preview: String -> 插件的图标
        - 可以是http地址
        - 如果只指定名称则默认指向homepage所在的仓库目录下同名文件
    - homepage: String -> 插件所在的仓库git地址
        - 必须以.git结尾的链接
    - update: [Key: Value] -> 暂时未使用
        - time: String -> 暂时未使用
        - message: String -> 暂时未使用
    - source: [Key: Value] -> 用于指定插件下载方式, 如不指定默认archive模式下载
        - type: String -> 插件下载模式
            - archive -> 下载git仓库下对应version的tag包(zip包)
            - release -> 下载git仓库手动发布版本的file文件
            - http -> 下载指定地址的http文件
            - raw -> 下载仓库下的指定file
        - tag: String -> 用于release下载模式指定tag
        - file: String -> 用于release/http/raw下载模式指定下载文件名

## 插件仓库
### Archive方式
```
    假设插件的`版本`为`1.0.0`
    git add .
    git git commit -m "update"
    git push origin master
    git tag 1.0.0
    git push --tags
```
### Release方式
```
    git add .
    git git commit -m "update"
    git push origin master
    手动在Github打Release包上传文件
    Tag和File即为你手动填写的值
```
### Http方式
```
    手动上传至任意地方, 此模式必须使用可以直接下载的直链
```
### Raw方式
```
    将插件文件(.ex/.mspe/.mspm/.mspr)直接上传至仓库, 并填写file为该文件名即可
```

# 快捷指令
为了支持`雀魂Plus`雀Ex在`快捷指令`部分内容使用雀魂Plus的配置, 两者可通用。  
在`雀Ex`初始化时会出入`Majsoul_Plus`字段, 之后`每个插件被载入前`会在前面的字段中注册`以插件ID为字段的Key`, 之后只要`在JS中`使用`Majsoul_Plus["id"] = xxx`注册即可, 详细可参考`我全都要`插件的写法。

```
if (!window.wqdy) {
    window.wqdy = new WQDY();
    window.wqdy.readSetting();
    Majsoul_Plus["wqdy"] = {
        name: "我全都要",
        actions: {
            "手动保存配置": () => window.wqdy.writeSetting(),
            "切换表情显示": () => {
                args.isUseOriginEmoji = !args.isUseOriginEmoji;
                localStorage.setItem("isUseOriginEmoji", args.isUseOriginEmoji);
                return "应用成功，下一局游戏生效。"
            },
            "按性别排序角色": () => {
                args.isSexSort = !args.isSexSort;
                localStorage.setItem("isSexSort", isSexSort);
                return "应用成功，重新启动游戏后生效。"
            }
        }
    }
    console.log("我全都要 加载完毕");
} else {
    console.warn("")
}
```

# 联系方式
- B站ID: [神崎·H·亚里亚](https://space.bilibili.com/898411/)  
- B站ID: [关野萝可](https://space.bilibili.com/612462792/)
- QQ交流群: [991568358](https://jq.qq.com/?_wv=1027&k=3gaKRwqg)
- Twitter: @MajsoulEx

# 赞助
如果对您有所帮助，欢迎您的赞赏
<figure class="third">
    <img src="https://moxcomic.github.io/wechat.png" width=300>
    <img src="https://moxcomic.github.io/alipay.png" width=300>
    <img src="https://moxcomic.github.io/qq.png" width=300>
</figure>