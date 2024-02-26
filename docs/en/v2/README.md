# V2 Usage Docs

![][java]
![][kotlin]
![][license]
![][release]
![][downloads]
![][players]
![][servers]
![][tested-versions]

> The current page is generated by Google Translate

## Introduction

This is a powerful music system that supports the following functions.

- Full server song
- Play alone
- Lyrics display
- Lyrics translation display
- Multiple search sources (Netease Cloud/Kuwo/Bilibili)
- Keyword search
- Personal playlist
- Full server playlist
- Playlist play (NetEase Cloud)
- Volume adjustment (1.12 and above support)
- Support BungeeCord

## Client Mod Description

This plug-in requires the client to install the supporting Mod to play normally

- For 1.8-1.11 clients, please install [AudioBuffer](https://www.mcbbs.net/thread-832205-1-1.html) Mod
- For 1.12.2-1.19 clients, please install [ZMusic](https://github.com/RealHeart/ZMusic-Mod/releases) Mod

## BungeeCord description

- BungeeCord currently only supports 1.9-1.16 server
- BungeeCord does not currently support economic systems
- For subservers to display Papi variables, progress prompts and other functions, the ZMusic-Addon plug-in needs to be installed

## Video

[Click to go to Bilibili to view the demo video](https://www.bilibili.com/video/av92156922)

## Feedback

- Go to [Gitee](https://gitee.com/realheart/ZMusic) or [Github](https://github.com/RealHeart/ZMusic) to submit Issues
- Join the exchange group: [1032722724](https://jq.qq.com/?_wv=1027&k=5oIs7cc) feedback

# Command

## Main command

`/zm` main command
`/zm help` View help
`/zm play` play music
`/zm music` All server order songs
`/zm search` Search music
`/zm playlist` playlist system

## Play

Search for a music by song name and play it directly

### Command

`/zm play [search source] [song name]`

[Search source description](#Search source description)

### Example

`/zm play netease your cat`

## Song

Search for a piece of music by song name, after sending it to the whole server, the player clicks to play

### Command

`/zm music [search source] [song name]`

[Search source description](#Search source description) [Song name ID description](#歌名ID化说明)

### Example

`/zm music netease your cat`

## search for

Search for a music by song name, return a list of ten music

### Command

`/zm search [search source] [song title]`

[Search source description](#Search source description) [Song name ID description](#歌名ID化说明)

### Example

`/zm search netease your cat`

## song list

By importing the playlist and storing it on the server, it is convenient to play the playlist.

### Command

`/zm playlist [platform] [subcommand]`

Currently supports the following platforms

- netease/163-Netease Cloud Music

If the platform is type, set the playlist play mode.
Currently supports

- normal-play in sequence
- loop-loop playback
- random-random play

Example:
`/zm playlist type random`

If the platform is global, it is the global playlist mode.

- The subcommand is the same as the normal mode

Example:
`/zm playlist global netease list`

`Subcommand` corresponds to the subcommand of the platform

- `import` Import playlist via playlist link
  - Parameters
    - `Playlist link` corresponds to the playlist link of the platform
- `list` retrieve the playlist list of the specified platform
- `play` plays the playlist through the playlist ID (available from list)
  - Parameters
    - `Playlist ID` Specify the playlist ID of the platform

### Example

Import:

- `/zm playlist 163 import https://music.163.com/#/playlist?id=363046232`

Play:

- `/zm playlist netease play 1937967578`
- `/zm playlist 163 play 363046232`

## Administrator

Administrator-related operations, full server mandatory playback, reload configuration, etc.

### Command

`/zm palyall [search source] [song name]` Mandatory full server play
`/zm stopAll` Force stop all server playback
`/zm reload` reload configuration file

[Search source description](#Search source description) [Song name ID description](#歌名ID化说明)

### Example

`/zm playAll netease your cat`

# Permission

## Ordinary player permissions

`zmusic.use` can use ordinary commands such as play and stop`

## Administrator permissions

`zmusic.admin` can use playAll, stopAll and other administrator commands

# Configuration file

```json
{
  /// Configuration file version (do not modify)
  "version": 9,
  /// Whether to automatically download plugin updates
  "update": false,
  /// Plug-in prompt message display prefix
  "prefix": "&bZMusic &e>>> &r",
  /// Whether to enable debugging mode
  "debug": false,
  /// API settings
  "api": {
    /// NetEase Cloud Music API address
    ///
    /// Use the open source project NeteaseCloudMusicApi
    /// Self-deployment is recommended, Node.js environment is required
    /// Address: https://github.com/Binaryify/NeteaseCloudMusicApi
    "netease": "https://netease.api.zhenxin.xyz/"
  },
  /// Account Settings
  "account": {
    /// NetEase Cloud Music
    /// Please use /zm login to login your account.
    "netease": {
      /// Whether to follow the author's NetEase Cloud Music account
      "follow": true
    },
    /// Bilibili
    "bilibili": {
      /// Because Bilibili is m4a audio format
      /// The server is required for conversion
      /// So Bilibili playback function charges 5 yuan/permanent
      /// Contact the author for authorization
      ///
      /// Authorize QQ
      "qq": "1307993674",
      /// Authorization Key
      "key": "none"
    }
  },
  /// VOD settings
  "music": {
    /// Gold coins deducted from song (set to 0, no deduction)
    /// Players with zmusic.bypass ignore the deduction
    "money": 10,
    /// The cooling time of song (set to 0, no cooling)
    /// Players with zmusic.bypass ignore the cooldown
    "cooldown": 5
  },
  /// Lyrics settings
  "lyric": {
    /// Whether to enable lyrics
    "enable": true,
    /// Whether to display lyrics translation
    "showLyricTr": true,
    /// Lyric color
    "color": "&b",
    /// The following are display mode settings, which can be enabled at the same time
    /// Whether to use BossBar to display lyrics (1.8 and below are not supported)
    "bossBar": true,
    /// Whether to use ActionBar to display lyrics
    "actionBar": false,
    /// Whether to use Title to display lyrics
    "subTitle": false,
    /// Whether to use chat information to display lyrics
    "chatMessage": false,
    /// Hud settings (only support 1.12 and above)
    "hud": {
      /// Whether to enable Hud
      "enable": true,
      /// X coordinate of information
      "infoX": 2,
      /// Y coordinate of information
      "infoY": 12,
      /// X coordinate of lyrics
      "lyricX": 2,
      /// The Y coordinate of the lyrics
      "lyricY": 72
    }
  }
}
```

# Variable

`%zmusic_playing_name%` Get the name of the currently playing music
`%zmusic_playing_singer%` Get the currently playing music singer
`%zmusic_playing_lyric%` Get the lyrics displayed at the current time
`%zmusic_time_current%` Get the time of the currently playing music
`%zmusic_time_max%` Get the maximum time of the currently playing music
`%zmusic_playing_platform%`-Get the currently playing music platform
`%zmusic_playing_source%`-Get the currently playing music source

# Front plugin

## Use all versions

[`PlaceholderAPI`](https://www.spigotmc.org/resources/placeholderapi.6245/) [Optional] If you want to use the above variables, please install
[`Vault`](https://www.spigotmc.org/resources/vault.34315/) [Optional] If you need to use song deduction, please install

## 1.5, 1.6 version use

~~[`AudioBuffer`](https://www.mcbbs.net/thread-832205-1-1.html) [Required] It is used to play music, there is a matching Mod client in the sticker, which needs to be installed~~

## 1.4 and below version use

~~[`AudioBuffer`](https://www.mcbbs.net/thread-832205-1-1.html) [Required] It is used to play music, there is a matching Mod client in the sticker, which needs to be installed~~
~~[`BossBarAPI`](https://www.mcbbs.net/thread-729531-1-1.html) [Optional] If you want to use BossBar to display lyrics, please install~~
~~[`ActionBarAPI`](https://www.spigotmc.org/resources/actionbarapi-1-8-1-14-2.1315/) [Optional] If you want to use ActionBar to display lyrics, please install~~

# Search source description

`Search Source` is the platform you want to search for music
Currently supports the following platforms

- netease/163-Netease Cloud Music
- kuwo-Kuwo Music
- bilibili-Bilibili music

# Song name ID description

Replace the song name with `-id:music ID`
Currently supports Netease Cloud Bilibili Music
Example: `/zm play bilibili -id:374305`

[java]: https://img.shields.io/badge/java-1.8-blue
[kotlin]: https://img.shields.io/badge/kotlin-1.5.30-blue
[license]: https://img.shields.io/github/license/RealHeart/ZMusic?color=blue
[players]: https://img.shields.io/bstats/players/7291
[servers]: https://img.shields.io/bstats/servers/7291
[tested-versions]: https://img.shields.io/spiget/tested-versions/83027
[release]: https://img.shields.io/github/v/release/RealHeart/ZMusic
[downloads]: https://img.shields.io/github/downloads/RealHeart/ZMusic/total?color=blue