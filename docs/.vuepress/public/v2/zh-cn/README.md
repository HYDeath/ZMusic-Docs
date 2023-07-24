# ZMusic

![][java]
![][kotlin]
![][license]
![][release]
![][downloads]
![][players]
![][servers]
![][tested-versions]

欢迎查看 ZMusic 帮助文档，这里有所有您需要的帮助，如果您需要排查无法播放声音等问题，请点[此处](#faq)。

## 简介

这是一个功能强大的音乐系统，支持以下功能。

- 全服点歌
- 单独播放
- 歌词显示
- 歌词翻译显示
- 多搜索源(网易云/哔哩哔哩)
- 关键词搜索
- 个人歌单
- 全服歌单
- 歌单播放(网易云)
- 音量调节(1.12 及以上支持)
- 支持 BungeeCord

## 客户端 Mod 说明

本插件需要客户端安装配套 Mod 才能正常播放

- 对于 1.8-1.11 的客户端 请安装 [AudioBuffer](https://www.mcbbs.net/thread-832205-1-1.html) Mod
- 对于 1.12.2-1.19 的客户端 请安装 [ZMusic](https://github.com/RealHeart/ZMusic-Mod/releases) Mod

## BungeeCord 说明

- 只有 BungeeCord 端需要安装 ZMusic-Plugin 插件（子服不需要安装）
- BungeeCord 目前仅支持 1.9-1.19 的服务端
- BungeeCord 暂不支持经济系统
- 对于子服显示 Papi 变量 进度提示等功能 只需要对子服安装 ZMusic-Addon 插件

## 视频

[点击前往哔哩哔哩查看演示视频](https://www.bilibili.com/video/av92156922)

## 反馈

- 前往 [码云](https://gitee.com/realheart/ZMusic) 或 [Github](https://github.com/RealHeart/ZMusic) 提交 Issues
- 加入交流群：[1032722724](https://jq.qq.com/?_wv=1027&k=5oIs7cc) 反馈

# 命令

## 主命令

`/zm` 主命令
`/zm help` 查看帮助
`/zm play` 播放音乐
`/zm music` 全服点歌
`/zm search` 搜索音乐
`/zm playlist` 歌单系统

## 播放

通过歌名搜索一个音乐，直接播放

### 命令

`/zm play [搜索源] [歌名]`

[搜索源说明](#搜索源说明)

### 示例

`/zm play netease 你的猫咪`

## 点歌

通过歌名搜索一个音乐，全服发送后，玩家点击播放

### 命令

`/zm music [搜索源] [歌名]`

[搜索源说明](#搜索源说明) [歌名 ID 化说明](#歌名ID化说明)

### 示例

`/zm music netease 你的猫咪`

## 搜索

通过歌名搜索一个音乐，返回十首音乐的列表

### 命令

`/zm search [搜索源] [歌名]`

[搜索源说明](#搜索源说明) [歌名 ID 化说明](#歌名ID化说明)

### 示例

`/zm search netease 你的猫咪`

## 歌单

通过导入歌单存储在服务器，方便播放歌单。

### 命令

`/zm playlist [平台] [子命令]`

目前支持以下平台

- netease/163 - 网易云音乐

如果平台为 type 则为设置歌单播放方式.
目前支持

- normal - 顺序播放
- loop - 循环播放
- random - 随机播放

示例:
`/zm playlist type random`

如果平台为 global 则为全局歌单模式.

- 子命令与普通模式相同

示例:
`/zm playlist global netease list`

`子命令` 对应平台的子命令

- `import` 通过歌单链接导入歌单
  - 参数
    - `歌单链接` 对应平台的歌单链接
- `list` 检索指定平台的歌单列表
- `play` 通过歌单 ID 播放歌单(可用 list 获取)
  - 参数
    - `歌单ID` 指定平台的歌单 ID

### 示例

导入:

- `/zm playlist 163 import https://music.163.com/#/playlist?id=363046232`

播放:

- `/zm playlist 163 play 363046232`

## 管理员

管理员相关操作，全服强制播放，重载配置等

### 命令

`/zm palyall [搜索源] [歌名]` 强制全服播放
`/zm stopAll` 强制停止全服播放
`/zm reload` 重载配置文件

[搜索源说明](#搜索源说明) [歌名 ID 化说明](#歌名ID化说明)

### 示例

`/zm playAll netease 你的猫咪`

# 权限

## 普通玩家权限

`zmusic.use` 可使用 play,stop 等普通指令`

## 管理员权限

`zmusic.admin` 可使用 playAll,stopAll 等管理员指令

# 配置文件

```json
{
  /// 配置文件版本(请勿修改)
  "version": 9,
  /// 是否自动下载插件更新
  "update": false,
  /// 插件提示信息显示前缀
  "prefix": "&bZMusic &e>>> &r",
  /// 是否开启调试模式
  "debug": false,
  /// API设置
  "api": {
    /// 网易云音乐API地址
    ///
    /// 使用开源项目NeteaseCloudMusicApi
    /// 推荐自行部署，需Node.js环境
    /// 地址: https://github.com/Binaryify/NeteaseCloudMusicApi
    "netease": "https://netease.api.zhenxin.xyz/"
  },
  /// 账号设置
  "account": {
    /// 网易云音乐
    /// 账号登录请使用 /zm login
    "netease": {
      /// 是否关注作者的网易云音乐账号
      "follow": true
    },
    /// 哔哩哔哩
    "bilibili": {
      /// 由于哔哩哔哩为m4a音频格式
      /// 需要服务器用来转换
      /// 因此哔哩哔哩播放功能收费5元/永久
      /// 联系作者获取授权
      ///
      /// 授权QQ
      "qq": "1307993674",
      /// 授权Key
      "key": "none"
    }
  },
  /// 点歌设置
  "music": {
    /// 点歌扣除的金币(设置为0则不扣除)
    /// 拥有zmusic.bypass的玩家无视扣除
    "money": 10,
    /// 点歌的冷却时间(设置为0则无冷却)
    /// 拥有zmusic.bypass的玩家无视冷却
    "cooldown": 5
  },
  /// 歌词设置
  "lyric": {
    /// 是否启用歌词
    "enable": true,
    /// 是否显示歌词翻译
    "showLyricTr": true,
    /// 歌词颜色
    "color": "&b",
    /// 以下为显示方式设置，可同时启用
    /// 是否使用BossBar显示歌词(不支持1.8及以下)
    "bossBar": true,
    /// 是否使用ActionBar显示歌词
    "actionBar": false,
    /// 是否使用Title显示歌词
    "subTitle": false,
    /// 是否使用聊天信息显示歌词
    "chatMessage": false,
    /// Hud 设置(仅支持1.12及以上)
    "hud": {
      /// 是否启用Hud
      "enable": true,
      /// 信息的X坐标
      "infoX": 2,
      /// 信息的Y坐标
      "infoY": 12,
      /// 歌词的X坐标
      "lyricX": 2,
      /// 歌词的Y坐标
      "lyricY": 72
    }
  }
}
```

# 变量

`%zmusic_playing_name%` 获取当前播放的音乐歌名
`%zmusic_playing_singer%` 获取当前播放的音乐歌手
`%zmusic_playing_lyric%` 获取当前时间显示的歌词
`%zmusic_time_current%` 获取当前播放的音乐的时间
`%zmusic_time_max%` 获取当前播放的音乐的最大时间
`%zmusic_playing_platform%` - 获取当前播放的音乐平台
`%zmusic_playing_source%` - 获取当前播放的音乐来源

# 前置插件

## 全版本使用

[`PlaceholderAPI`](https://www.spigotmc.org/resources/placeholderapi.6245/) [可选] 如需使用上方变量 请安装
[`Vault`](https://www.spigotmc.org/resources/vault.34315/) [可选] 如果需要使用点歌扣费 请安装

## 1.5,1.6 版本使用

~~[`AudioBuffer`](https://www.mcbbs.net/thread-832205-1-1.html) [必须] 用于播放音乐，贴内有配套 Mod 客户端需安装~~

## 1.4 及以下版本使用

~~[`AudioBuffer`](https://www.mcbbs.net/thread-832205-1-1.html) [必须] 用于播放音乐，贴内有配套 Mod 客户端需安装~~
~~[`BossBarAPI`](https://www.mcbbs.net/thread-729531-1-1.html) [可选] 如需使用 BossBar 显示歌词 请安装~~
~~[`ActionBarAPI`](https://www.spigotmc.org/resources/actionbarapi-1-8-1-14-2.1315/) [可选] 如需使用 ActionBar 显示歌词 请安装~~

# 搜索源说明

`搜索源` 为你要搜索音乐的平台
目前支持以下平台

- netease/163 - 网易云音乐
- kuwo - 酷我音乐
- bilibili - 哔哩哔哩音乐

**QQ 音乐 API 已经完全移除，酷狗音乐播放时会出现问题**

# 歌名 ID 化说明

将歌名替换为 `-id:音乐ID` 即可
目前支持 网易云 哔哩哔哩音乐
示例: `/zm play bilibili -id:374305`

<span id="faq"></span>

# 常见问题

## 可能会遇到的问题

### 播放时没有声音

如果您使用的是`KCaldron`，那么很抱歉，我们不支持此服务器。

但如果您非要想使用模组服的话，这里有两种解决方案：

- 使用 [BungeeCord](https://www.spigotmc.org/wiki/bungeecord) 或者 [WaterFall](https://papermc.io/downloads#Waterfall)
  等群组服服务端。
- 使用 Arclight, LoliServer, Mohist, Uranium 等**可能**支持本插件的模组服核心。

如果您使用的是 **Spigot, Paper, Yatopia, Sugarcane 等原版插件服核心**，那么请检查您是否满足以下条件：

- 您的客户端已经安装了 AllMusic(1.7.10, 1.12 或以上版本) 或者 AudioBuffer(1.12 及以下版本)
- 您的服务端已正常安装了 ZMusic 插件
- 您在服务器插件文件夹安装的是 ZMusic 系列插件而不是 AllMusic 模组(模组需要在客户端进行安装)
- 您的客户端是 Fabric 或者 Forge 而**不是**纯净版，并且已经安装了 AudioBuffer **或者** AllMusic 模组
- 您的网络环境良好
- 您点歌时使用的平台是网易云音乐！！！

如果你未满足以上条件中的其中一个的话，请进行进一步调整。

当然，如果您全部满足以上条件的话，还是无法播放音乐，我们建议您在未配置外置 API 的情况下使用**网易云音乐**进行播放。

实际上，我们建议您使用自己拥有的服务器开服。

### 服务器载入成功后，使用`/zm`相关指令时，会提示“错误：请等待插件载入完毕”

如果您遇到本问题的话，请升级 ZMusic 插件到最新版本即可解决问题。

### 插件无法载入，提示“请卸载 AllMusic/AudioBuffer 插件”

请在服务器插件文件夹删除 AllMusic/AudioBuffer 插件即可。
在新版本的 ZMusic 中，我们弃用了 BossBarAPI, ActionBarAPI 依赖插件与 AudioBuffer 前置插件，为了防止服务器模组通讯频道冲突，我们不得不采取本措施。

### 播放音乐成功后，客户端提示耗时时间很长（但是实际却很短）。

导致此问题的原因可能是连续点击同一个点歌按钮间隔时间过短。导致内部线程调用尚未处理过来，显示了错误的耗时时间，不影响实际使用。

## 可能会遇到的后台异常

### 登录网易云音乐时，出现`java.net.UnknownHostException` 异常

您的配置文件在配置外置 API 的时候域名配置错误，请检查域名是否有效。
如果域名有效的话，请检查您服务器的 DNS 是否正常或者刷新 DNS 缓存。
面板服用户一般不会发生此种问题。

### 载入插件时，出现`java.lang.NoClassDefFoundError com/google/gson/xxx` 错误

您的服务端未内置 gson 库，安装带 gson 库的插件即可。（不会吧不会吧，竟然真有不支持 gson 的吧！）

### 点歌成功后，后台刷屏报黄色错误

从 2.5 开始，旧版的进度调用方案已被停用，请更新到最新版本。

### 安装 AllMusic 之后，客户端无法启动 (Fabric)

- 请检查您安装的模组版本是否对应，如您的客户端使用的是 Fabric 模组加载器，但是您下载的是 `[Forge-1.16.5]-AllMusic-x.x.x.jar`
- 如果您下载的是 Fabric 版本模组，请检查您是否安装了 `Fabric-API` 前置模组
- 本模组与`CardBoard`不兼容

~~(所以我一个 ZMusic 使用文档为什么要回答 AllMusic 的问题，AllMusic 插件用户请退群)~~

### 插件加载后出现报错：“错误：请等待插件加载完毕”

出现此种问题，请检查以下情况。

- 检查您安装的插件版本是否为最新。
- 检查`ZMusic`插件文件夹是否有权限写入（特别是基于 Linux 的系统， ~~建议直接暴力 chmod 777~~ 实际上，设置 777 是非常危险的行为）
- 检查您的服务端是否支持异步线程(一般基于`Bukkit`的都支持，~~别问我关于`Mohist`的问题辣！焯！~~)
- 手动修复插件文件夹，在`ZMusic`文件夹中新建一个叫`language`的文件夹，之后从我们的仓库中的`master`分支找到`language`文件夹，并下载`zh_cn.json`文件，放入`language`
  文件夹中，然后重载或者重启服务器。

## 是否支持 `1.7.10`

我们并不推荐您使用`1.7.10`版本, 如果您坚持使用, 请确保如下说明.

- 仅支持 `Mohist/Uranium` 服务端
- `Uranium` 仅在 `dev-4-b210` 测试成功
- `Mohist` 仅在 `1.7.10-42` 测试成功
- 除 `聊天信息` 外, 其他全部歌词显示均无效(除 Uranium)
- 使用 `Uranium` 配套模组, 可实现 Title/ActionBar 显示
- 我们不接受任何 `1.7.10` 版本的问题反馈

## 插件卡服吗？

<font size="25">不卡服！</font>如果出现卡服问题，一般是服务器内其他插件导致的卡服，并且某位用户点歌的时候正好碰到了卡服的时刻。（不服？不服就贴出 timings 报告！）
碎碎念：听说点大悲咒会崩服（bushi
![img_1.png](img_1.png)
![img_2.png](img_2.png)
如果您在点歌的时候确信发生了上述崩服的情况，请让腐竹将崩服之前爆出的红色 Stacktrace 发给我们，我们会尽快解决。
为了您的人身安全，我们建议有群组服的将 ZMusic 丢进群组服插件文件夹内。

## 插件命令无法被 DeluxeMenu/TrMenu 等菜单插件调用 (BungeeCord/WaterFall)

这是群组服的通病，因为 ZMusic 的指令是注册在群组服核心内，而插件只能调用 Spigot/Paper 侧的指令。
这边想出了一个折中的方法，就是让用户自己输入，虽然这样做对用户来说不太友好，但是自己动手，丰衣足食！

## [zmusic 插件一直提示没有 zmusic.use 权限，确保权限组已经加入了](https://www.mcbbs.net/forum.php?mod=viewthread&tid=1310665)

如果您使用的是蹦极端(BungeeCord/Waterfall)，请在跨服端的插件目录内添加 LuckPerms-Bungee 插件，然后通过`/lpb`指令进行赋予权限。

## [[Sponge]服务端 ZMusic 在线音乐加载不上去](https://www.mcbbs.net/forum.php?mod=viewthread&tid=1048579)

本插件不支持 Sponge 平台，请等待 3.0 发布。（当前的 3.0 测试版对 Sponge 为半支持状态）

~~干啥啥不行，自搜第一名！~~

### 我找不到以上描述的任何错误

您可以加入我们的交流群，如果有报错信息的话，请上传后台报错信息至[WhkSoft PasteBin](https://paste.whksoft.cn/)
然后通过链接的形式反馈给我们。
帮助手册仍在进一步完善中！

## ~~彩蛋环节：死亡不掉落用什么插件？~~

~~![img.png](img.png)~~
~~你需要安装下北泽式死亡不掉落插件，首先排除可以使用`/gamerule`改死亡不掉落，这怎么可能是原版的指令呢，对吧！再说了，百度是什么咱也完全不知道！~~

[java]: https://img.shields.io/badge/java-1.8-blue
[kotlin]: https://img.shields.io/badge/kotlin-1.5.30-blue
[license]: https://img.shields.io/github/license/RealHeart/ZMusic?color=blue
[players]: https://img.shields.io/bstats/players/7291
[servers]: https://img.shields.io/bstats/servers/7291
[tested-versions]: https://img.shields.io/spiget/tested-versions/83027
[release]: https://img.shields.io/github/v/release/RealHeart/ZMusic
[downloads]: https://img.shields.io/github/downloads/RealHeart/ZMusic/total?color=blue
