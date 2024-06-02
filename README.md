# Auto Msg & Title

**MCDR Plugin about Auto Show Title.**

## 插件说明

此插件可以为玩家自动弹出标题或消息，如同插件服进入主城后的标题

同时此插件可为一块区域提供自动的说明，如服务器被参观时，参观者进入某区域、机器之后自动弹出此区域、机器的制造者、名字、功能之类的；在玩家进入某一机器时自动为玩家弹出机器说明书……

这个插件时我写的第三个插件，如有技术力不足的地方请大佬多多包涵，如有BUG请向我提供issue！
此插件许多有关玩家坐标检测的代码我已经尽可能写的高效率了，如果有大佬能在此基础上优化我的代码，可以向我提供pr，非常感谢！

## 注意事项

插件命令前缀为`!!amt`，游戏内无法输入`§`符号，所以如果你需要**彩色**的**聊天栏消息**，可以修改`data.json`中的`msg`消息栏！

由于插件通过`RCON`执行`data`命令获取玩家坐标，所以**可能**会对服务器造成*额外的性能负担*，但经压测目前**50**名玩家同时在线**无法**导致服务器mspt额外提升
且插件在没有玩家在线或全为机器人时自动关闭玩家数据更新，所以我认为此插件对性能影响应该能忽略不计！

`RCON`执行`data`命令时无OP反馈，但执行`title`命令时**会有反馈**，所以可以关闭`server.properties`中的`broadcast-rcon-to-ops`以防当玩家多的时候会对op进行刷屏，但如果只有消息栏消息，则不会有OP消息！

## 配置说明

> `config.json` 配置项

| 配置项                              | 含义                     | 默认值                       | 注意事项                                   |
|----------------------------------|------------------------|---------------------------|----------------------------------------|
| `permission`                      | 权限列表                | `略`               | 插件命令的权限控制                  |
| `debug`                      | debug模式                | `false`                    | 是否打开测试模式，打开后会反馈玩家数据                  |
| `afk_time`                      | 判定挂机多久进入AFK                | `300`                 | 单位为秒            |
| `back_region`                      | 区域消息弹出冷却期                | `30`                    | 单位为秒            |
| `refresh_pos_time`                         | 刷新玩家数据间隔时间                    | `1`      | 单位为秒，由于Python代码效率关系，单次循环最快`0.12s`左右                                |
| `bot_prefix`                         | 机器人前缀                  | `bot_`      | Carpet机器人的名字前缀                                |

## 命令说明

`!!amt` 获取命令列表
`!!amt list` 获取区域列表，5个为一页
`!!amt add` 添加区域，2d为平面区域，3d为立体区域，前添加的区域触发优先级高于后添加的区域
`!!amt msg` 详细编辑区域聊天栏消息
`!!amt del` 删除区域
`!!amt move` 移动区域优先级

详细的区域配置可以在`data.json`中编辑，配置时请注意格式⚠️
