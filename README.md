# 雀魂Ex
Majsoul Ex

## 免责声明
在您使用`雀魂Ex`进行游戏时造成的`包含但不局限于限制登录、封号等`后果`均由用户自行承担`, `雀魂Ex`不对此承担任何责任!

## 开发进度
- iOS: `3.1.6 正式版`  
- Android: `1.1.0 正式版`

## 开发语言
- iOS: `Swift & Objective-C`  
- Android: `Kotlin & Java`

## 安装
### 安卓
点击 `==>` [下载安卓版本](https://github.com/moxcomic/majsoul-ex/releases/download/iOS%2FAndroid/majsoulex_android_1.1.0.apk) `<==`
### iOS
点击 `==>` [下载iOS版本](https://github.com/moxcomic/majsoul-ex/releases/download/iOS%2FAndroid/majsoulex_ios_3.1.6.ipa) `<==`
#### 注意事项
iOS由于系统原因`不能直接使用iPhone/iPad下载安装`, 需要使用签名方式安装, 具体方式请自行百度
### 其他
- [雀Ex项目地址](https://github.com/moxcomic/majsoul-ex)
- [最新发布版本](https://github.com/moxcomic/majsoul-ex/releases/tag/iOS%2FAndroid)  

## 新增功能
- 复制友人房链接、雀口令后会弹窗提示是否加入房间, 点击确定后一键加入
    - 该功能需要登录到游戏主页面才会弹窗
- 复制牌谱链接后会弹窗提示是否查看牌谱, 点击确定后一键进入牌谱
    - 该功能需要登录到游戏主页面才会弹窗
- 友人房链接`复制链接`功能修改
- 牌谱`分享`功能修改

## 雀口令
雀口令是在雀魂友人房链接上发展出来的新型分享链接方式, 可以自定义更多的分享内容
### 雀口令支持变量列表
- \[token\]: 雀口令本体  
- \[roomid\]: 房间号  
- \[roomlink\]: 雀魂友人房原链接内容  
- \[maxplayer_d\]: 房间最大人数, 阿拉伯数字 3/4  
- \[maxplayer_s\]: 房间最大人数, 大写 三/四  
- \[roommode\]: 房间模式, 东/南  

## 制作扩展
`待更新...`
### 图片资源替换部分
1. 直接替换`/Android/data/com.yuuki.majsoulex/files/Cache`路径下的文件
2. `待更新`

## 制作扩展源
### GitHub部署部分
1. Github IO Pages
2. 主体文件 src.ex
3. 参考 [src.ex](https://moxcomic.github.io/src.ex)文件编写
    - 点击后会下载到本地
    - 下载完成后使用文本方式打开

### src.ex文件字段解释
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

## 快捷指令
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

## 联系方式
- B站ID: [神崎·H·亚里亚](https://space.bilibili.com/898411/)  
- B站ID: [关野萝可](https://space.bilibili.com/612462792/)
- QQ交流群: [991568358](https://jq.qq.com/?_wv=1027&k=3gaKRwqg)
- Twitter: @MajsoulEx

## 赞助
如果对您有所帮助，欢迎您的赞赏
<figure class="third">
    <img src="https://moxcomic.github.io/wechat.png" width=300>
    <img src="https://moxcomic.github.io/alipay.png" width=300>
    <img src="https://moxcomic.github.io/qq.png" width=300>
</figure>