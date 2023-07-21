---
title: 配置文件
---

```yaml
# 是否开启检查更新
check-update: true
# 插件使用的语言
language: 'zh_CN'
# 消息前缀
prefix: '&bZMusic &e>>> &r'
# 是否开启调试模式
debug: false

# 代理设置
proxy:
  # 是否启用代理
  enable: false
  # 主机名
  hostname: 127.0.0.1
  # 端口
  port: 8080

# API设置
#
# 使用开源API项目 推荐自行搭建
# 网易云: https://github.com/Binaryify/NeteaseCloudMusicApi
api:
  # 网易云音乐
  # 账号登录请使用 /zm login netease
  netease:
    # API链接
    link: 'https://zm.armoe.cn'

# ZMusic VIP设置
vip:
  # 授权QQ
  qq: ''
  # 授权Key
  key: ''

# 点歌设置
music:
  # 点歌后执行的指令
  # 拥有zmusic.bypass的玩家无视
  commands:
    - 'money take %player_name% 10' # 扣除10金币
  # 点歌的冷却时间(设置为0则无冷却)
  # 拥有zmusic.bypass的玩家无视
  cooldown: 5

# 歌词设置
lyric:
  # 是否启用歌词
  enabled: true
  # 是否显示歌词翻译
  show-translation: true
  # 歌词颜色
  color: '&b'
  # 以下为显示方式设置，可同时启用
  # 是否使用BossBar显示歌词(不支持1.8及以下)
  boss-bar: true
  # 是否使用ActionBar显示歌词(不支持1.8以下)
  action-bar: false
  # 是否使用聊天信息显示歌词
  chat: false

# Hud 设置(仅支持1.12及以上)
hud:
  # 是否启用Hud
  enabled: true
  # 信息设置
  info:
    # 是否启用
    enabled: true
    # 信息的X坐标
    x: 2
    # 信息的Y坐标
    y: 12
  # 歌词设置
  lyric:
    enabled: true
    x: 2
    y: 72
```
