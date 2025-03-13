
# 引擎触发

&gt; **&lt;font color="#000000" style="font-family: Fixedsys;font-size: 15px;"&gt;cfg_game_data 配置ShareNpc=1可以将QM和机器人的触发事件全部转到QF&lt;/font&gt;**

&gt; **&lt;font color="#000000" style="font-family: Fixedsys;font-size: 15px;"&gt;引擎触发是通用的,TXT的所有触发转换成小写后在LUA中就可使用,如说明书中缺省可反馈至对接群&lt;/font&gt;**

&gt; **&lt;font color="#000000" style="font-family: Fixedsys;font-size: 15px;"&gt;三端引擎的触发主体只会是系统/玩家对象;如cfg_mongen表填入的触发回调,参数1是系统对象,参数2才是怪物对象&lt;/font&gt;**

| 引擎事件(QM)   | 说明                       |
| :------------- | -------------------------- |
| `startup`      | 服务端启动触发             |
| `login`        | 玩家登录触发               |
| `ontimer(X)`   | 个人定时器触发(X=触发器ID) |
| `ontimerex(X)` | 全局定时器触发(X=触发器ID) |
| `loadguild`    | 初始化行会触发             |

| 引擎事件(QF)           | 说明                                                                  |
| :--------------------- | --------------------------------------------------------------------- |
| `triggerchat`          | 聊天内容聊天触发                                                      |
| `privatechat`          | 收到私聊信息触发                                                      |
| `recharge`             | 充值触发                                                              |
| `clicknpc`             | 点击npc触发                                                           |
| `changemoneyout`       | 当货币超出21亿时触发[引擎23.08.30拓展为超出42亿时触发]                |
| `resetday`             | 跨天登录触发<br />[0点在线的玩家也会进入触发]                           |
| `setday`               | 每天登录触发                                                          |
| `setscreen`            | 修改分辨率触发                                                        |
| `closedbagitemclick`   | 点击背包未开启格子锁头触发                                            |
| `beginteleport`        | 传送戒指传送前触发                                                    |
| `addfriendrequest`     | 加好友前触发                                                          |
| `lookhuminfo`          | 查看别人装备触发                                                      |
| `addbagbefore`         | 物品进包前触发[无法阻止进包操作]                                      |
| `addbag`               | 物品进入背包触发                                                      |
| `addherobag`           | 进入英雄背包触发                                                      |
| `run`                  | 跑步触发                                                              |
| `walk`                 | 走路触发                                                              |
| `entermap`             | 人物切换地图触发                                                      |
| `leavemap`             | 人物离开地图触发                                                      |
| `heroentermap`         | 英雄切换地图触发                                                      |
| `playoffline`          | 人物大退触发                                                          |
| `playreconnection`     | 人物小退触发                                                          |
| `playlevelup`          | 人物升级触发                                                          |
| `herolevelup`          | 英雄升级触发                                                          |
| `slaveupgrade`         | 宝宝升级触发                                                          |
| `sendability`          | 人物属性改变时触发                                                    |
| `getexp`               | 人物获取经验触发                                                      |
| `itemexpired`          | 装备到期触发/过期触发                                                 |
| `heroitemexpired`      | 英雄装备到期触发/过期触发                                             |
| `itemdamage(X)`        | 装备持久消失触发(X=装备位置)                                          |
| `dropuseitems(X)`      | 参照装备投保已投保装备掉落触发(X=装备位置)                            |
| `makeweaponunluck`     | 武器诅咒前触发                                                        |
| `killplay`             | 杀死人物触发                                                          |
| `killmon`              | 杀死怪物触发                                                          |
| `onkillmob`            | 杀死怪物触发(需要在mapinfo地图参数增加onkillmon)                      |
| `scatterbagitems`      | 击杀目标爆物品触发                                                    |
| `startautoplaygame`    | 开始挂机触发                                                          |
| `stopautoplaygame`     | 停止挂机触发                                                          |
| `startmyshop`          | 摆摊触发                                                              |
| `startmyshopok`        | 摆摊成功触发                                                          |
| `bindwechat`           | 公众号获取key成功触发                                                 |
| `bindrewechat`         | 公众号成功验证触发                                                    |
| `bagusestoneitemok`    | 镶嵌宝石触发                                                          |
| `removestoneitem`      | 卸下宝石触发                                                          |
| `openbottomui`         | 展开聊天框时触发                                                      |
| `closebottomui`        | 隐藏聊天框时触发                                                      |
| `readmail`             | 邮件id阅读邮件触发                                                    |
| `getmailitem`          | 邮件id提取邮件触发                                                    |
| `opensndaitembox`      | 人物开启首饰盒触发(神佑/生肖)                                         |
| `heroopensndaitembox`  | 英雄开启首饰盒触发(神佑/生肖)                                         |
| `stdmodefunc(X)`       | 双击类道具触发(X=道具表anicount值,支持道具表stdmode[2、31、200` ] 类) |
| `beforeeatitem`        | 双击使用道具前触发                                                    |
| `getboxsitem(X)`       | 宝箱获得物品时触发 (X=道具表shape值)                                  |
| `canreopenbox(X)`      | 宝箱开启前触发 (X=道具表shape值)                                      |
| `moneychange(X)`       | 货币改变触发 (X=货币道具表idx)                                        |
| `userbuyitem`          | 系统npc商店购买前触发复古npc店铺,非商城与摆摊                         |
| `canbuyshopitem(X)`    | 商城购买前触发(X=商城表cfg_store的requestID字段)                      |
| `canshowshopitem(X)`   | 商城显示触发(X=商城表cfg_store的condisId字段)                         |
| `buyshopitem`          | 商城购买后触发                                                        |
| `groupitemoffex`       | 脱套装触发                                                            |
| `groupitemonex`        | 穿套装触发                                                            |
| `groupitemon(X)`       | 套装激活触发(X=套装编号,参照套装配置说明)                             |
| `takeonex`             | 人物穿戴任意装备触发                                                  |
| `takeoffex`            | 人物脱下任意装备触发                                                  |
| `takeonbefore(X)`      | 穿戴装备前触发(X=装备位置)                                            |
| `takeoffbefore(X)`     | 脱下装备前触发(X=装备位置)                                            |
| `takeonbeforee(X)`     | 穿戴任意装备前触发                                                    |
| `takeon(X)`            | 穿戴装备时触发(X=装备位置)                                            |
| `takeoff(X)`           | 脱下装备时触发(X=装备位置)                                            |
| `takeoffexchange`      | 脱下装备进入背包前触发                                                |
| `herologin`            | 召唤英雄触发                                                          |
| `heroluck`             | 英雄忠诚度改变触发                                                    |
| `herotakeonex`         | 英雄穿戴任意装备触发                                                  |
| `herotakeoffex`        | 英雄脱下任意装备触发                                                  |
| `herotakeonbefore(X)`  | 英雄穿戴装备前触发(X=装备位置)                                        |
| `herotakeoffbefore(X)` | 英雄脱下装备前触发(X=装备位置)                                        |
| `herotakeon(X)`        | 英雄穿戴装备触发(X=装备位置)                                          |
| `herotakeoff(X)`       | 英雄脱下装备触发(X=装备位置)                                          |
| `herotakeoffexchange`  | 英雄脱下任意装备前触发                                                |
| `dealend`              | 交易后触发                                                            |
| `dealbefore`           | 交易前触发                                                            |
| `checkbuildguild`      | 创建行会前触发                                                        |
| `inivitguild`          | 邀请入会前触发                                                        |
| `guildaddmember`       | 加入行会前触发                                                        |
| `guildaddmemberafter`  | 加入行会后触发                                                        |
| `guilddelmemberbefore` | 退出行会前触发                                                        |
| `guilddelmember`       | 退出行会触发                                                          |
| `updateguildnotice`    | 编辑行会公告前触发                                                    |
| `setrankname(X)`       | 行会编辑封号前触发（X=1-5个行会封号）                                 |
| `guildchiefdelmember`  | 掌门踢出行会成员前触发                                                |
| `guildclosebefore`     | 解散行会前触发                                                        |
| `guildclose`           | 解散行会前触发                                                        |
| `guildapplybefore`     | 请求行会联盟前触发                                                    |
| `setguildrank1`        | 任命掌门人前触发                                                      |
| `setguildrank2`        | 任命副掌门前触发                                                      |
| `setguildrank3`        | 任命成员3前触发                                                       |
| `setguildrank4`        | 任命成员4前触发                                                       |
| `setguildrank5`        | 任命成员5前触发                                                       |
| `carpathend`           | 镖车到达指定位置触发(配置详情参照押镖系统说明)                        |
| `leavedart`            | 镖车切换地图触发(配置详情参照押镖系统说明)                            |
| `carfindmaster`        | 镖车进入自动寻路范围触发(配置详情参照押镖系统说明)                    |
| `slavedamage`          | 镖车被攻击触发(配置详情参照押镖系统说明)                              |
| `hitslave`             | 攻击别人镖车触发(配置详情参照押镖系统说明)                            |
| `kuafuend`             | 跨服结束触发(参照跨服系统说明)                                        |
| `kflogin`              | 跨服成功触发(参照跨服系统说明)                                        |
| `kfsynvar(X)`          | 同步跨服变量触发(X=回调id,参照跨服系统说明)                           |
| `reboxtile`            | 盒子断线重连触发                                                      |
| `giftstatusok`         | 盒子礼包领取成功触发                                                  |
| `giftstatusfail`       | 盒子礼包领取失败触发                                                  |
| `invitegroup`          | 邀请组队前qf触发                                                      |
| `groupcreate`          | 创建队伍时触发(组队)                                                  |
| `startgroup`           | 创建队伍前触发(组队)                                                  |
| `leavegroup`           | 离开队伍时触发(退组)                                                  |
| `groupdelmember`       | 删除组队成员触发                                                      |
| `groupaddmember`       | 添加组队成员触发                                                      |
| `groupkillmon`         | 组队杀怪触发                                                          |
| `getgroupcount`        | 获取组队成员人数                                                      |
| `showfashion`          | 人物勾选外显时装生效触发                                              |
| `heroshowfashion`      | 英雄勾选外显时装生效触发                                              |
| `notshowfashion`       | 人物取消外显时装时候触发                                              |
| `heronotshowfashion`   | 英雄取消外显时装时候触发                                              |
| `pickupitem(X)`        | 玩家捡取物品后触发(X=物品idx)                                         |
| `pickupitemex`         | 玩家捡取任意物品后触发                                                |
| `pickupitemfront(X)`   | 玩家捡取物品前触发(X=物品idx)                                         |
| `pickupitemfrontex`    | 玩家捡取任意物品前触发                                                |
| `dropitem(X)`          | 玩家仍掉物品后触发(X=物品idx)                                         |
| `dropitemex`           | 玩家仍掉任意物品后触发                                                |
| `dropitemfront(X)`     | 玩家仍掉物品前触发(X=物品idx)                                         |
| `dropitemfrontex`      | 玩家仍掉任意物品前触发                                                |
| `herodropitem(X)`      | 英雄扔掉指定物品后触发(X=物品idx)                                     |
| `herodropitemex`       | 英雄扔掉任意物品后触发                                                |
| `herodropitemfront(X)` | 英雄扔掉指定物品前触发(X=物品idx)                                     |
| `herodropitemfrontex`  | 英雄扔掉任意物品前触发                                                |
| `picktask`             | 接取任务系统(参照任务系统)                                            |
| `clicknewtask`         | 点击任务触发(参照任务系统)                                            |
| `changetask`           | 刷新任务触发(参照任务系统)                                            |
| `completetask`         | 完成任务触发(参照任务系统)                                            |
| `deletetask`           | 删除任务触发(参照任务系统)                                            |
| `nextdie`              | 人物复活前触发                                                        |
| `revival`              | 人物复活时触发                                                        |
| `playdie`              | 人物死亡触发                                                          |
| `herodie`              | 英雄死亡触发                                                          |
| `selfkillslave`        | 宝宝死亡触发                                                          |
| `checkdropuseitems`    | 人物死亡装备掉落前触发                                                |
| `heronextdie`          | 英雄死亡之前复活触发                                                  |
| `cangetbackpaimaiitem` | 拍卖行下架、禁止架下触发(参照拍卖行系统)                              |
| `canpaimaiitem`        | 拍卖行上架、禁止上架触发(参照拍卖行系统)                              |
| `buypaimaiitem`        | 拍卖行购买时触发                                                      |
| `biddingpaimaiitem`    | 拍卖行竞价触发                                                        |
| `crittrigger`          | 暴击触发                                                              |
| `reboundhurt`          | 伤害反弹触发                                                          |
| `attackdamage`         | 人物攻击前触发                                                        |
| `heroattackdamage`     | 英雄攻击前触发                                                        |
| `attackdamagebb`       | 宝宝攻击前触发                                                        |
| `heroattackdamagebb`   | 英雄宝宝攻击前触发                                                    |
| `attack`               | 人物物理平砍攻击触发                                                  |
| `magicattack`          | 人物魔法攻击触发                                                      |
| `heroattack`           | 英雄物理攻击触发                                                      |
| `heromagicattack`      | 英雄魔法攻击触发                                                      |
| `magicattackpet`       | 宝宝魔法攻击触发                                                      |
| `heroattackpet`        | 英雄宝宝物理攻击触发                                                  |
| `heromagicattackpet`   | 英雄宝宝魔法攻击触发                                                  |
| `struckdamage`         | 人物被攻击前触发                                                      |
| `herostruckdamage`     | 英雄被攻击前触发                                                      |
| `struckdamagebb`       | 宝宝被攻击前触发                                                      |
| `herostruckdamagebb`   | 英雄宝宝被攻击前触发                                                  |
| `struck`               | 人物被物理攻击触发                                                    |
| `magicstruck`          | 人物被魔法攻击触发                                                    |
| `herostruck`           | 英雄被物理攻击触发                                                    |
| `heromagicstruck`      | 英雄被魔法攻击触发                                                    |
| `struckpet`            | 宝宝被物理攻击触发                                                    |
| `magicstruckpet`       | 宝宝被魔法攻击触发                                                    |
| `herostruckpet`        | 英雄宝宝被物理攻击触发                                                |
| `heromagicstruckpet`   | 英雄宝宝被魔法攻击触发                                                |
| `beginmagic`           | 使用技能前触发                                                        |
| `magselffunc(X)`       | 自身使用技能触发(X=技能ID)                                            |
| `magtagfunc(X)`        | 对目标人物使用技能时触发(X=技能ID)                                    |
| `magmonfunc(X)`        | 对目标怪物使用技能时触发(X=技能ID)                                    |
| `magtagfuncex(X)`      | 释放技能触发传递参数(X=技能ID)                                        |
| `mobtreachery`         | 宝宝叛变触发                                                          |
| `heromobtreachery`     | 英雄宝宝叛变触发                                                      |
| `slavebb`              | 获得宝宝触发                                                          |
| `heroslavebb`          | 英雄获得宝宝触发                                                      |
| `buffchange`           | buff操作触发                                                          |
| `herobuffchange`       | 英雄buff操作触发                                                      |
| `mirrormapend`         | 镜像地图销毁前触发                                                    |
| `beforeroute`          | 进入连接点(跳转点)前触                                                |
| `canpush`              | 推动技能(野蛮冲撞/抗拒火环/气波功/自定义推动技能)施法前触发           |
| `custommagicdamage(X)` | 自定义技能处理伤害前触发                                              |
| `titlechangedex`       | 人物称号改变触发                                                      |
| `untitledex`           | 人物称号取消触发                                                      |
| `titlechanged_(X)`     | 人物改变称号时触发 (X=装备表shape值)                                  |
| `herotitlechanged_(X)` | 英雄改变称号时触发 (X=装备表shape值)                                  |
| `untitled_(X)`         | 人物取消称号时触发 (X=装备表shape值)                                  |
| `herountitled_(X)`     | 英雄取消称号时触发 (X=装备表shape值)                                  |
| `collectmonex`         | 采集前触发                                                            |
| `collectmon(X)`        | 玩家点击采集怪物将会触发(X=怪物ID)                                    |
| `collectmonfail(X)`    | 超过采集范围触发(X=怪物ID)                                            |
| `qfloadbegin`          | QFunction-0重载前触发                                                 |
| `qfloadend`            | QFunction-0重载后触发                                                 |
| `inisort`              | 自定义排行榜刷新触发                                                  |
| `clicksortbutton`      | 自定义排行榜切换玩家和英雄的页签触发                                  |
| `clicksortno`          | 自定义排行榜点击排名触发                                              |
| `findpathbegin`        | 寻路开启                                                              |
| `findpathstop`         | 寻路中断                                                              |
| `findpathend`          | 寻路结束                                                              |
| `dropgoldfront`        | 丢弃金币前触发                                                        |
# 脚本触发



### 开启Lua脚本触发
触发脚本接口写在 **QFunction-0.lua** 文件中。触发接口跟原先脚本触发接口名一样，注意**小写**。
所有触发接口，默认提供 &lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 13;"&gt;参数1：玩家对象。&lt;/font&gt;

------------

### 聊天触发前置接口

`triggerchat`

| 参数    | 类型      | 空   | 默认 | 注释                                                                                                                                                                                  |
| :------ | :-------- | :--- | :--- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| self    | `object`  | 否   |      | 玩家对象                                                                                                                                                                              |
| sMsg    | `string`  | 否   |      | 说话内容                                                                                                                                                                              |
| chat    | `integer` | 否   |      | 聊天频道<br />1:系统<br />2:喊话<br />3:私聊<br />4:行会<br />5:组队<br />6:附近<br />7:世界<br />8:国家<br />9:联盟<br />40:行会通知                                                                     |
| msgType | `string`  | 否   |      | 消息类型<br />1:普通消息<br />2:坐标<br />3:装备<br />5:系统通知消息,需使用特定富文本解析<br />6:系统通知消息,需使用FColor特定富文本解析<br />7:系统通知消息,需使用SRText特定富文本解析<br />8:猜拳 |
| result  | `bool`    | 否   |      | 是否终止说话                                                                                                                                                                          |

```lua
function triggerchat(self, sMsg, chat,msgType)
    if tonumber(sMsg) ~= nil then
        say(self, "不允许说数字。".."频道："..chat,"类型:"..msgType)
        return false
    end
    return true
end

```

### 收到私聊信息触发

`privatechat`

| 参数   | 类型      | 空   | 默认 | 注释         |
| :----- | :-------- | :--- | :--- | :----------- |
| self   | `object`  | 否   |      | 玩家对象     |
| sMsg   | `string`  | 否   |      | 说话内容     |
| chat   | `integer` | 否   |      | 聊天频道     |
| result | `bool`    | 否   |      | 是否接收私信 |
------------

### 装备相关

#### 角色穿戴/脱下装备前触发

`takeonbeforeex`~`takeoffbeforeex`

| 参数      | 类型      | 空   | 默认                | 注释                                |
| :-------- | :-------- | :--- | :------------------ | :---------------------------------- |
| self      | `object`  | 否   |                     | 玩家对象                            |
| item      | `object`  | 否   |                     | 物品对象                            |
| where     | `integer` | 否   | 引擎64_23.10.24新增 | 装备位置                            |
| makeIndex | `integer` | 否   | 引擎64_23.10.24新增 | 装备唯一ID                          |
| result    | `bool`    | 否   |                     | true = 允许操作<br />false = 阻止操作 |

`takeonbefore(X)`~`takeoffbefore(X)`

&gt; X=装备位置

| 参数   | 类型     | 空   | 默认 | 注释                                |
| :----- | :------- | :--- | :--- | :---------------------------------- |
| self   | `object` | 否   |      | 玩家对象                            |
| item   | `object` | 否   |      | 物品对象                            |
| result | `bool`   | 否   |      | true = 允许操作<br />false = 阻止操作 |

#### 角色穿戴/脱下装备后触发

`takeonex`~`takeoffex`

| 参数      | 类型      | 空   | 默认 | 注释      |
| :-------- | :-------- | :--- | :--- | :-------- |
| self      | `object`  | 否   |      | 玩家对象  |
| item      | `object`  | 否   |      | 物品对象  |
| where     | `integer` | 否   |      | 穿/脱位置 |
| itemName  | `string`  | 否   |      | 物品名    |
| makeindex | `integer` | 否   |      | 唯一ID    |

`takeon(X)`~`takeoff(X)`

&gt; X=装备位置

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| self | `object` | 否   |      | 玩家对象 |
| item | `object` | 否   |      | 物品对象 |

#### 英雄角色穿戴/脱下装备前触发

`herotakeonbeforeex`~`herotakeoffbeforeex`

| 参数      | 类型      | 空   | 默认                | 注释                                |
| :-------- | :-------- | :--- | :------------------ | :---------------------------------- |
| self      | `object`  | 否   |                     | 玩家对象                            |
| item      | `object`  | 否   |                     | 物品对象                            |
| where     | `integer` | 否   | 引擎64_24.08.07新增 | 装备位置                            |
| makeIndex | `integer` | 否   | 引擎64_24.08.07新增 | 装备唯一ID                          |
| makeIndex | `integer` | 否   | 引擎64_24.08.07新增 | 英雄对象                            |
| result    | `bool`    | 否   |                     | true = 允许操作<br />false = 阻止操作 |

#### 英雄穿戴/脱下装备回调

`herotakeonex` ~ `herotakeoffex`

| 参数      | 类型      | 空   | 默认                | 注释      |
| :-------- | :-------- | :--- | :------------------ | :-------- |
| play      | `object`  | 否   |                     | 玩家对象  |
| item      | `object`  | 否   |                     | 物品对象  |
| where     | `integer` | 否   |                     | 穿/脱位置 |
| itemName  | `string`  | 否   |                     | 物品名    |
| makeindex | `integer` | 否   |                     | 唯一ID    |
| hero      | `object`  | 否   | 引擎64_23.08.30新增 | 英雄对象  |

#### 人物死亡装备掉落前触发

`checkdropuseitems`

| 参数    | 类型      | 空   | 默认 | 注释                                |
| :------ | :-------- | :--- | :--- | :---------------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                            |
| where   | `integer` | 否   |      | 装备位                              |
| itemIdx | `integer` | 否   |      | 装备idx                             |
| result  | `bool`    | 否   |      | true = 允许掉落<br />false = 阻止掉落 |

### 参照装备投保已投保装备掉落触发

`dropuseitems(X)`

&gt; X=装备位置

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.10.24新增 | 装备对象 |

#### 角色装备过期触发

`itemexpired`

&gt; 称号到期时不会传入物品对象,称号名称通过常量 `&lt;$ExpiredItemName&gt;` 获取

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.08.30新增 | 物品对象 |
| name  | `string` | 否   | 引擎64_23.08.30新增 | 物品名字 |

#### 英雄装备过期触发

`heroitemexpired`

&gt; 称号到期时不会传入物品对象,称号名称通过常量 `&lt;$H.ExpiredItemName&gt;` 获取

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.08.30新增 | 物品对象 |
| name  | `string` | 否   | 引擎64_23.08.30新增 | 物品名字 |
| hero  | `object` | 否   | 引擎64_23.08.30新增 | 英雄对象 |

#### 角色脱下装备进入背包前触发

`takeoffexchange`

| 参数      | 类型     | 空   | 默认                | 注释       |
| :-------- | :------- | :--- | :------------------ | :--------- |
| play      | `object` | 否   |                     | 玩家对象   |
| item      | `object` | 否   | 引擎64_23.08.30新增 | 装备对象   |
| where     | `string` | 否   | 引擎64_23.08.30新增 | 装备位置   |
| makeindex | `bool`   | 否   | 引擎64_23.08.30新增 | 装备唯一id |

#### 英雄脱下装备进入背包前触发

`herotakeoffexchange`

| 参数      | 类型     | 空   | 默认                | 注释       |
| :-------- | :------- | :--- | :------------------ | :--------- |
| play      | `object` | 否   |                     | 玩家对象   |
| item      | `object` | 否   | 引擎64_23.08.30新增 | 装备对象   |
| where     | `string` | 否   | 引擎64_23.08.30新增 | 装备位置   |
| makeindex | `bool`   | 否   | 引擎64_23.08.30新增 | 装备唯一id |
| hero      | `object` | 否   | 引擎64_23.08.30新增 | 英雄对象   |

### 装备持久消失触发

`itemdamage(X)`

&gt; X=装备位置

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.10.24新增 | 装备对象 |

### 武器加诅咒前触发

`makeweaponunluck`

| 参数   | 类型     | 空   | 默认 | 注释                            |
| :----- | :------- | :--- | :--- | :------------------------------ |
| actor  | `object` | 否   |      | 玩家对象                        |
| item   | `object` | 否   |      | 装备对象                        |
| result | `bool`   | 否   |      | true = 诅咒<br />false = 阻止诅咒 |

### 镶嵌宝石触发

`bagusestoneitemok`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.10.24新增 | 装备对象 |

### 卸下宝石触发

`removestoneitem`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   | 引擎64_23.10.24新增 | 装备对象 |

------------

### 双击类道具触发

`stdmodefunc(X)`

&gt; X=道具表第5列(Anicount),支持道具表stdmode[2、31、200]类

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| self   | `object` | 否   |      | 玩家对象     |
| item   | `object` | 否   |      | 物品对象     |
| result | `bool`   | 否   |      | 是否允许使用 |

```lua
function stdmodefunc100(actor, itemobj)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"50级后才可使用")
        return false
    end
end

```

#### 双击使用道具前触发

`beforeeatitem`

&gt; 注:引擎24.0118 补全参数2 - 物品对象

| 参数          | 类型      | 空   | 默认 | 注释                                |
| :------------ | :-------- | :--- | :--- | :---------------------------------- |
| actor         | `string`  | 否   |      | 玩家对象                            |
| itemobj       | `string`  | 否   |      | 道具对象                            |
| itemidx       | `integer` | 否   |      | 道具idx                             |
| itemMakeIndex | `integer` | 否   |      | 道具唯一id                          |
| itemNum       | `integer` | 否   |      | 道具数量                            |
| stdMode       | `integer` | 否   |      | 物品表stdMode参数                   |
| result        | `boolean` | 否   |      | 返回值<br />true=允许<br />false=不允许 |

### 货币改变触发

`moneychange(X)`

&gt; X=货币道具表idx

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

```lua
for moneyIdx = 1, 100 do
    _G["moneychange"..moneyIdx] = function (actor)
        local formernum = getconst(actor, "&lt;$OLDMONEY&gt;")
        local curnum = querymoney(actor, moneyIdx)
        local name = getstditeminfo(moneyIdx, 1)
        release_print("货币【"..name.."】改变：", moneyIdx, curnum, formernum)
    end
end

```

### 物品进包前触发

&gt; 无返回值,不能阻止进包操作

`addbagbefore`

| 参数          | 类型      | 空   | 默认 | 注释        |
| :------------ | :-------- | :--- | :--- | :---------- |
| self          | `object`  | 否   |      | 玩家对象    |
| item          | `object`  | 否   |      | 物品对象    |
| itemidx       | `integer` | 否   |      | 道具idx     |
| itemMakeIndex | `integer` | 否   |      | 道具唯一idx |

### 添加背包触发

`addbag`

&gt; 接口为异步，物品进入背包时可能与原有物品堆叠起来了

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| self | `object` | 否   |      | 玩家对象 |
| item | `object` | 否   |      | 物品对象 |

### 角色扔掉丢弃金币前触发

`dropgoldfront`

| 参数    | 类型      | 空   | 默认 | 注释                                            |
| :------ | :-------- | :--- | :--- | :---------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                        |
| goldNum | `integer` | 否   |      | 金币数量                                        |
| result  | `bool`    | 否   |      | 是否允许丢弃<br />true=允许丢弃<br />false=不允许丢弃 |

### 角色扔掉任意物品前触发

`dropitemfrontex`

| 参数     | 类型      | 空   | 默认                | 注释                                            |
| :------- | :-------- | :--- | :------------------ | :---------------------------------------------- |
| play     | `object`  | 否   |                     | 玩家对象                                        |
| dropItem | `object`  | 否   | 引擎64_23.08.30新增 | 掉落物品                                        |
| itemName | `string`  | 否   | 引擎64_23.08.30新增 | 物品名称                                        |
| model    | `integer` | 否   | 引擎64_23.08.30新增 | 行为id<br />0=扔掉触发<br />1=人物掉落触发          |
| result   | `bool`    | 否   |                     | 是否允许丢弃<br />true=允许丢弃<br />false=不允许丢弃 |

### 扔掉任意物品后触发

`dropitemex`

| 参数     | 类型     | 空   | 默认                | 注释     |
| :------- | :------- | :--- | :------------------ | :------- |
| play     | `object` | 否   |                     | 玩家对象 |
| dropItem | `object` | 否   | 引擎64_23.08.30新增 | 掉落物品 |
| itemName | `string` | 否   | 引擎64_23.08.30新增 | 物品名称 |

### 角色爆出物品前触发

`itemdropfrombagbefore`

| 参数     | 类型     | 空   | 默认 | 注释                                                |
| :------- | :------- | :--- | :--- | :-------------------------------------------------- |
| play     | `object` | 否   |      | 玩家对象                                            |
| dropItem | `object` | 否   |      | 掉落物品                                            |
| result   | `bool`   | 否   |      | 是否允许掉落<br />true=允许掉落<br />false=不允许掉落 |

### 角色扔掉物品前触发

`itemthrowfrombagbefore`

| 参数     | 类型     | 空   | 默认 | 注释                                          |
| :------- | :------- | :--- | :--- | :-------------------------------------------- |
| play     | `object` | 否   |      | 玩家对象                                      |
| dropItem | `object` | 否   |      | 掉落物品                                      |
| result   | `bool`   | 否   |      | 是否允许扔<br />true=允许扔<br />false=不允许扔 |

### 英雄爆出物品前触发

`heroitemdropfrombagbefore`

| 参数     | 类型     | 空   | 默认 | 注释                                                |
| :------- | :------- | :--- | :--- | :-------------------------------------------------- |
| play     | `object` | 否   |      | 玩家对象                                            |
| dropItem | `object` | 否   |      | 掉落物品                                            |
| result   | `bool`   | 否   |      | 是否允许掉落<br />true=允许掉落<br />false=不允许掉落 |

### 英雄扔掉物品前触发

`heroitemthrowfrombagbefore`

| 参数     | 类型     | 空   | 默认 | 注释                                          |
| :------- | :------- | :--- | :--- | :-------------------------------------------- |
| play     | `object` | 否   |      | 玩家对象                                      |
| dropItem | `object` | 否   |      | 掉落物品                                      |
| result   | `bool`   | 否   |      | 是否允许扔<br />true=允许扔<br />false=不允许扔 |

------------

### 添加英雄背包触发

`addherobag`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| self | `object` | 否   |      | 玩家对象 |
| item | `object` | 否   |      | 物品对象 |
| hero | `object` | 否   |      | 英雄对象 |

### 英雄扔掉物品前/后触发

`herodropitemfrontex`~`herodropitemex`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
| item  | `object` | 否   |      | 物品对象 |

### 英雄扔掉物品前/后触发

`herodropitemfront(X)` ~ `herodropitem(X)`

&gt; X=物品Idx

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| item  | `object` | 否   |                     | 物品对象 |
| hero  | `object` | 否   | 引擎64_23.08.30新增 | 英雄对象 |

------------

### 受击触发

#### 暴击触发

`crittrigger` 支持物理攻击、魔法攻击 暴击触发

| 参数    | 类型      | 空   | 默认 | 注释                 |
| :------ | :-------- | :--- | :--- | :------------------- |
| self    | `object`  | 否   |      | 玩家对象             |
| attack  | `object`  | 否   |      | 受击对象             |
| damage  | `integer` | 否   |      | 暴击后伤害值         |
| MagicId | `integer` | 否   |      | 技能ID               |
| result  | `integer` | 否   |      | 返回值，修改后的伤害 |

##### 伤害反弹触发

`reboundhurt`

| 参数    | 类型     | 空   | 默认 | 注释             |
| :------ | :------- | :--- | :--- | :--------------- |
| actor   | `object` | 否   |      | 玩家对象         |
| Hiter   | `object` | 否   |      | 伤害来源对象     |
| Damage  | `number` | 否   |      | 伤害值           |
| MagicId | `number` | 否   |      | 技能ID           |
| result  | `number` | 否   |      | 返回值<br />伤害值 |

#### 攻击前

##### 人物攻击前触发

`attackdamage` 

&gt; 参数6`Model`=3(切割) 新增于引擎64_23.12.07,触发需勾选m2的参数`选项-物品参数-新增属性-启用切割`

| 参数    | 类型      | 空   | 默认                | 注释                                                 |
| :------ | :-------- | :--- | :------------------ | :--------------------------------------------------- |
| self    | `object`  | 否   |                     | 玩家对象                                             |
| Target  | `object`  | 否   |                     | 受击对象                                             |
| Hiter   | `object`  | 否   |                     | 攻击对象                                             |
| MagicId | `integer` | 否   |                     | 技能ID                                               |
| Damage  | `integer` | 否   |                     | 伤害                                                 |
| Model   | `integer` | 否   | 引擎64_23.10.24新增 | 当前攻击模式<br />0=正常<br />1=暴击<br />2=格挡<br />3=切割 |
| result  | `integer` | 否   |                     | 返回值，修改后的伤害                                 |

`attackdamagebb` 宝宝攻击前触发
`heroattackdamage` 英雄攻击前触发
`heroattackdamagebb` 英雄宝宝攻击前触发

| 参数    | 类型      | 空   | 默认 | 注释                 |
| :------ | :-------- | :--- | :--- | :------------------- |
| self    | `object`  | 否   |      | 玩家对象             |
| Target  | `object`  | 否   |      | 受击对象             |
| Hiter   | `object`  | 否   |      | 攻击对象             |
| MagicId | `integer` | 否   |      | 技能ID               |
| Damage  | `integer` | 否   |      | 伤害                 |
| result  | `integer` | 否   |      | 返回值，修改后的伤害 |

#### 攻击后

`attack` 玩家物理攻击
`magicattack` 玩家魔法攻击
`attackpet` 宝宝物理攻击
`magicattackpet` 宝宝魔法攻击
`heroattack` 英雄物理攻击
`heromagicattack` 英雄魔法攻击
`heroattackpet` 英雄宝宝物理攻击
`heromagicattackpet` 英雄宝宝魔法攻击

| 参数    | 类型      | 空   | 默认 | 注释     |
| :------ | :-------- | :--- | :--- | :------- |
| self    | `object`  | 否   |      | 玩家对象 |
| Target  | `object`  | 否   |      | 受击对象 |
| Hiter   | `object`  | 否   |      | 攻击对象 |
| MagicId | `integer` | 否   |      | 技能ID   |
------------

### 受击触发

#### 受击前

`struckdamage` 玩家受击
`struckdamagebb` 宝宝受击
`herostruckdamage` 英雄受击
`herostruckdamagebb` 英雄宝宝受击

| 参数    | 类型      | 空   | 默认 | 注释                 |
| :------ | :-------- | :--- | :--- | :------------------- |
| self    | `object`  | 否   |      | 玩家对象             |
| Hiter   | `object`  | 否   |      | 攻击对象             |
| Target  | `object`  | 否   |      | 受击对象             |
| MagicId | `integer` | 否   |      | 技能ID               |
| Damage  | `integer` | 否   |      | 伤害                 |
| result  | `integer` | 否   |      | 返回值，修改后的伤害 |

#### 受击后

`struck` 玩家物理受击
`magicstruck` 玩家魔法受击
`struckpet` 宝宝物理受击
`magicstruckpet` 宝宝魔法受击
`herostruck` 英雄物理受击
`heromagicstruck` 英雄魔法受击
`heromagicstruckpet` 英雄宝宝魔法受击
`herostruckpet` 英雄宝宝物理受击

| 参数    | 类型      | 空   | 默认 | 注释     |
| :------ | :-------- | :--- | :--- | :------- |
| self    | `object`  | 否   |      | 玩家对象 |
| Hiter   | `object`  | 否   |      | 攻击对象 |
| Target  | `object`  | 否   |      | 受击对象 |
| MagicId | `integer` | 否   |      | 技能ID   |

------------

### 使用技能触发

#### 自身使用技能触发

`magselffunc(X)`   

&gt; X=触发技能ID

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| self | `object` | 否   |      | 玩家对象 |

#### 对目标人物使用技能时自身触发

`magtagfunc(X)` 

&gt; X=触发技能ID

| 参数       | 类型     | 空   | 默认                | 注释         |
| :--------- | :------- | :--- | :------------------ | :----------- |
| self       | `object` | 否   |                     | 玩家对象     |
| roleObject | `object` | 否   | 引擎64_23.06.28新增 | 受击玩家对象 |

#### 对目标怪物使用技能时自身触发

`magmonfunc(X)` 

&gt; X=触发技能ID

| 参数      | 类型     | 空   | 默认                | 注释         |
| :-------- | :------- | :--- | :------------------ | :----------- |
| self      | `object` | 否   |                     | 玩家对象     |
| monObject | `object` | 否   | 引擎64_23.06.28新增 | 受击怪物对象 |

#### 自身使用任意技能前触发

`beginmagic`玩家触发
`herobeginmagic`英雄触发

&gt; &lt;font color="#ff0000"&gt;magselffunc(X)触发优先级在beginmagic前,阻止释放并不会影响触发magselffunc(X)&lt;/font&gt;

| 参数         | 类型      | 空   | 默认 | 注释                                          |
| :----------- | :-------- | :--- | :--- | :-------------------------------------------- |
| self         | `object`  | 否   |      | 玩家对象                                      |
| maigicID     | `integer` | 否   |      | 技能id                                        |
| maigicName   | `string`  | 否   |      | 技能名字                                      |
| targetObject | `object`  | 否   |      | 受击对象                                      |
| x            | `integer` | 否   |      | 受击对象X坐标                                 |
| y            | `integer` | 否   |      | 受击对象Y坐标                                 |
| result       | `bool`    | 否   |      | 返回值<br />true/nil=允许施法<br />false=阻止施法 |

#### 推动技能(野蛮冲撞/抗拒火环/气波功/自定义推动技能)施法前触发

`canpush`玩家触发
`herocanpush`英雄触发
`petcanpush`宠物触发
`bbcanpush`宝宝触发
`herobbcanpush`英雄宝宝触发

| 参数    | 类型      | 空   | 默认 | 注释                                                                     |
| :------ | :-------- | :--- | :--- | :----------------------------------------------------------------------- |
| self    | `object`  | 否   |      | 玩家对象                                                                 |
| Target  | `object`  | 否   |      | 受击对象                                                                 |
| Hiter   | `object`  | 否   |      | 攻击对象                                                                 |
| MagicId | `integer` | 否   |      | 技能ID                                                                   |
| result  | `bool`    | 否   |      | 返回值<br />0=不执行推动<br />1=执行推动<br />2=根据M2上的推动条件判断是否执行 |

#### 自定义技能处理伤害前触发

`custommagicdamage(X)`

| 参数   | 类型     | 空   | 默认 | 注释                                                                                                         |
| :----- | :------- | :--- | :--- | :----------------------------------------------------------------------------------------------------------- |
| Hiter  | `object` | 否   |      | 施法对象                                                                                                     |
| Target | `object` | 否   |      | 受击对象                                                                                                     |
| result | `bool`   | 否   |      | 返回值<br />true=正常施法<br />false=阻止施法(将不走后续伤害触发)<br />可用于群攻类技能,阻止部分受击对象的伤害流程 |

------------

### 任意地图杀死怪物触发

`killmon`

| 参数       | 类型      | 空   | 默认                | 注释                                                                  |
| :--------- | :-------- | :--- | :------------------ | :-------------------------------------------------------------------- |
| self       | `object`  | 否   |                     | 攻击者对象                                                            |
| mon        | `object`  | 否   |                     | 怪物对象                                                              |
| killerType | `integer` | 否   |                     | 凶手类型<br />0=凶手是宝宝;<br />1=英雄;<br />2=人物;<br />4=全局触发(无归属) |
| mon        | `string`  | 否   |                     | 对象唯一ID                                                            |
| monName    | `string`  | 否   |                     | 怪物名字                                                              |
| mapID      | `string`  | 否   | 引擎64_24.08.07新增 | 当前地图编号                                                          |

### 怪物/宝宝 死亡触发

`selfkillslave` 宝宝死亡触发，触发对象 主人
`killslave` 杀掉宝宝触发，触发对象 攻击者
`onkillmob`   杀怪触发，触发对象 攻击者 (需要在mapinfo地图参数增加onkillmon)

| 参数 | 类型     | 空   | 默认 | 注释          |
| :--- | :------- | :--- | :--- | :------------ |
| self | `object` | 否   |      | 触发对象      |
| mon  | `object` | 否   |      | 宝宝/怪物对象 |
------------

### 玩家死亡触发

`killplay`  杀人触发，触发对象：攻击者

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| self | `object` | 否   |      | 触发对象 |
| play | `object` | 否   |      | 被杀玩家 |

`herodie`   英雄被杀，触发对象：被杀英雄玩家
`playdie`   玩家被杀，触发对象：被杀玩家

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| self  | `object` | 否   |      | 被杀玩家 |
| hiter | `object` | 否   |      | 攻击者   |

------------

### 怪物物品掉落回调接口

&gt; 触发接口为自己爆率设置，只提供常用参数

| 参数         | 类型     | 空   | 默认 | 注释                               |
| :----------- | :------- | :--- | :--- | :--------------------------------- |
| self         | `object` | 否   |      | 玩家对象                           |
| DropItemName | `string` | 否   |      | 掉落物品名字                       |
| mon          | `object` | 否   |      | 掉落怪物                           |
| result       | `bool`   | 否   |      | 是否掉落,true=允许掉落，false=不允许 |

------------

### 怪物掉落物品触发

`mondropitemex` 怪物掉落统一触发

| 参数     | 类型      | 空   | 默认 | 注释                               |
| :------- | :-------- | :--- | :--- | :--------------------------------- |
| self     | `object`  | 否   |      | 玩家对象                           |
| DropItem | `object`  | 否   |      | 掉落物品                           |
| mon      | `object`  | 否   |      | 掉落怪物                           |
| nX       | `integer` | 否   |      | 掉落坐标x                          |
| nY       | `integer` | 否   |      | 掉落坐标y                          |
| result   | `bool`    | 否   |      | 是否掉落,true=允许掉落，false=不允许 |

### 杀死怪物或人物，爆物品触发

`scatterbagitems`

| 参数     | 类型     | 空   | 默认 | 注释       |
| :------- | :------- | :--- | :--- | :--------- |
| self     | `object` | 否   |      | 玩家对象   |
| dropRole | `object` | 否   |      | 掉落者对象 |
------------

### 充值触发

`recharge`

&gt; 充值时玩家不在线,则会在下次登陆时触发

| 参数           | 类型      | 空   | 默认                | 注释                             |
| :------------- | :-------- | :--- | :------------------ | :------------------------------- |
| self           | `object`  | 否   |                     | 玩家对象                         |
| Gold           | `integer` | 否   |                     | 充值金额                         |
| ProductId      | `integer` | 否   |                     | 产品ID（来源客户端充值面板调用） |
| MoneyId        | `integer` | 否   |                     | 货币ID                           |
| isReal         | `integer` | 否   |                     | =1真实充值<br />=0扶持充值         |
| orderTime      | `integer` | 否   | 引擎64_24.03.14新增 | 订单时间(时间戳)                 |
| rechargeAmount | `integer` | 否   | 引擎64_24.03.14新增 | 实际到账货币金额                 |
| giftAmount     | `integer` | 否   | 引擎64_24.03.14新增 | 额外赠送金额<br />运营后台配置     |
| refundAmount   | `integer` | 否   | 引擎64_24.03.14新增 | 开启积分金额<br />运营后台配置     |

------------

### NPC点击触发

`clicknpc`

| 参数   | 类型      | 空   | 默认 | 注释                                 |
| :----- | :-------- | :--- | :--- | :----------------------------------- |
| actor  | `object`  | 否   |      | 玩家对象                             |
| npcID  | `integer` | 否   |      | NPC索引（NPC配置表中的ID）           |
| npcName  | `string` | 否   |      | NPC名称                           |
| result | `bool`    | 否   |      | false允许继续执行Txt脚本，true不允许 |
------------

### 玩家跳转地图触发

`entermap`

| 参数  | 类型      | 空   | 默认                | 注释       |
| :---- | :-------- | :--- | :------------------ | :--------- |
| actor | `object`  | 否   |                     | 玩家对象   |
| mapid | `string`  | 否   | 引擎64_24.05.23新增 | 进入地图id |
| x     | `integer` | 否   | 引擎64_24.05.23新增 | 进入地图X  |
| y     | `integer` | 否   | 引擎64_24.05.23新增 | 进入地图Y  |

### 玩家离开地图触发

`leavemap`

| 参数  | 类型      | 空   | 默认                | 注释       |
| :---- | :-------- | :--- | :------------------ | :--------- |
| actor | `object`  | 否   |                     | 玩家对象   |
| mapid | `string`  | 否   | 引擎64_24.05.23新增 | 离开地图id |
| x     | `integer` | 否   | 引擎64_24.05.23新增 | 离开地图X  |
| y     | `integer` | 否   | 引擎64_24.05.23新增 | 离开地图Y  |

### 镜像地图销毁前触发

`mirrormapend`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| sysobj | `object` | 否   |      | 系统对象 |
| mapid  | `string` | 否   |      | 地图id   |

### 进入连接点(跳转点)前触

`beforeroute`

| 参数   | 类型      | 空   | 默认 | 注释                                |
| :----- | :-------- | :--- | :--- | :---------------------------------- |
| actor  | `object`  | 否   |      | 玩家对象                            |
| mapid  | `string`  | 否   |      | 地图id                              |
| x      | `integer` | 否   |      | x坐标                               |
| y      | `integer` | 否   |      | y坐标                               |
| result | `boolean` | 否   |      | 返回值<br />true=允许<br />false=不允许 |
------------

### 捡取触发

`pickupitemex`

| 参数          | 类型      | 空   | 默认                | 注释       |
| :------------ | :-------- | :--- | :------------------ | :--------- |
| actor         | `object`  | 否   |                     | 玩家对象   |
| itemobj       | `object`  | 否   |                     | 物品对象   |
| itemidx       | `integer` | 否   | 引擎64_24.03.14新增 | 物品id     |
| itemMakeIndex | `integer` | 否   | 引擎64_24.03.14新增 | 物品唯一id |
------------

### 奔跑触发

`run`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 走路触发

`walk`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 升级触发

`playlevelup`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

### 宝宝升级触发

`slaveupgrade`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| mon   | `object` | 否   | 引擎64_23.12.07新增 | 宝宝对象 |
| level | `object` | 否   | 引擎64_23.12.07新增 | 当前等级 |
------------

### 小退出触发

`playreconnection`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 大退与关闭客户端触发

`playoffline`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 开始挂机触发

`startautoplaygame`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 停止挂机触发

`stopautoplaygame`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 属性变化时触发

`sendability`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

### 英雄属性变化时触发

`herosendability`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
| hero  | `object` | 否   |      | 英雄对象 |

------------

### 角色获取经验前触发

`getexp`

&gt; 注:脚本添加经验不会触发

| 参数   | 类型      | 空   | 默认 | 注释                   |
| :----- | :-------- | :--- | :--- | :--------------------- |
| actor  | `object`  | 否   |      | 玩家对象               |
| exp    | `integer` | 否   |      | 获取的经验值           |
| result | `integer` | 否   |      | 返回值，修改后的经验值 |

------------

###  拾取前触发

`pickupitemfrontex`

| 参数   | 类型     | 空   | 默认 | 注释                                |
| :----- | :------- | :--- | :--- | :---------------------------------- |
| actor  | `object` | 否   |      | 玩家对象                            |
| item   | `object` | 否   |      | 物品对象                            |
| result | `bool`   | 否   |      | true = 允许拾取<br />false = 阻止拾取 |
------------

### 角色/英雄获得宝宝触发

`slavebb`~`heroslavebb`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
| mon   | `object` | 否   |      | 宝宝对象 |

### 角色宝宝叛变触发

`mobtreachery`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   | 引擎64_23.10.24新增 | 玩家对象 |
| mon   | `object` | 否   | 引擎64_23.10.24新增 | 宝宝对象 |

### 英雄宝宝叛变触发

`heromobtreachery`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| hero  | `object` | 否   | 引擎64_23.10.24新增 | 英雄对象 |
| mon   | `object` | 否   | 引擎64_23.10.24新增 | 宝宝对象 |

------------

### 点击背包锁头触发

`closedbagitemclick`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 货币超出21/42亿触发

&gt; 引擎64_23.08.30货币上限突破至42亿,该触发同步拓展至42亿

`changemoneyout`

| 参数     | 类型      | 空   | 默认 | 注释     |
| :------- | :-------- | :--- | :--- | :------- |
| actor    | `object`  | 否   |      | 玩家对象 |
| moneyIdx | `integer` | 否   |      | 货币id   |
| moneynum | `integer` | 否   |      | 货币数量 |

------------

### 套装激活触发

`groupitemon(X)`

&gt; X=套装编号

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| actor | `object`  | 否   |      | 玩家对象 |
| idx   | `string` | 否   |      | 套装id   |

### 穿套装触发

`groupitemonex`

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| actor | `object`  | 否   |      | 玩家对象 |
| idx   | `string` | 否   |      | 套装id   |

### 脱套装触发

`groupitemoffex`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| actor  | `object`  | 否   |      | 玩家对象 |
| suitid | `string` | 否   |      | 套装id   |

### 英雄穿/脱套装触发

`herogroupitemonex`~`herogroupitemoffex`

| 参数   | 类型      | 空   | 默认                | 注释     |
| :----- | :-------- | :--- | :------------------ | :------- |
| actor  | `object`  | 否   |                     | 玩家对象 |
| suitid | `string` | 否   |                     | 套装id   |
| hero   | `object`  | 否   | 引擎64_23.10.24新增 | 英雄对象 |

### 英雄套装激活触发

`herogroupitemon(X)`

&gt; X=套装编号,参照套装配置说明

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| hero  | `object` | 否   | 引擎64_23.10.24新增 | 英雄对象 |

### 英雄开启首饰盒触发(神佑/生肖)

`heroopensndaitembox`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| hero  | `object` | 否   | 引擎64_23.10.24新增 | 英雄对象 |

### 英雄忠诚度改变触发

`heroluck`

| 参数    | 类型      | 空   | 默认                | 注释     |
| :------ | :-------- | :--- | :------------------ | :------- |
| actor   | `object`  | 否   |                     | 玩家对象 |
| hero    | `object`  | 否   | 引擎64_23.10.24新增 | 英雄对象 |
| luckNum | `integer` | 否   | 引擎64_23.10.24新增 | 忠诚度   |

------------

### 交易前触发

`dealbefore`

| 参数  | 类型     | 空   | 默认 | 注释             |
| :---- | :------- | :--- | :--- | :--------------- |
| actor | `object` | 否   |      | 接收交易请求对象 |
| actor | `object` | 否   |      | 发起交易请求对象 |

### 交易后触发

`dealend`

| 参数  | 类型      | 空   | 默认 | 注释                 |
| :---- | :-------- | :--- | :--- | :------------------- |
| actor | `object`  | 否   |      | 玩家对象             |
| item  | `object`  | 否   |      | 最后一个物品的唯一ID |
| num   | `integer` | 否   |      | 交易物品的数量       |
------------

### 摆摊触发

`startmyshop`

&gt; forbidmyshop 接口打断摆摊

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

```lua
function startmyshop(actor)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"50级后才可摆摊")
        forbidmyshop(actor)
        return
    end
end

```

### 摆摊成功触发

`startmyshopok`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

### 商城购买后触发

`buyshopitem`

| 参数     | 类型      | 空   | 默认                | 注释     |
| :------- | :-------- | :--- | :------------------ | :------- |
| actor    | `object`  | 否   |                     | 玩家对象 |
| itemobj  | `object`  | 否   | 引擎64_23.12.07新增 | 物品对象 |
| itemname | `string`  | 否   | 引擎64_23.12.07新增 | 物品名称 |
| itemnum  | `integer` | 否   | 引擎64_23.12.07新增 | 物品数量 |
| moneyid  | `integer` | 否   | 引擎64_23.12.07新增 | 货币id   |
| moneynum | `integer` | 否   | 引擎64_23.12.07新增 | 物品价格 |

------------

### 人物勾选/取消外显时装生效触发

`showfashion` ~ `notshowfashion`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

### 英雄勾选/取消外显时装生效触发

`heroshowfashion` ~ `heronotshowfashion`

| 参数  | 类型     | 空   | 默认                | 注释     |
| :---- | :------- | :--- | :------------------ | :------- |
| actor | `object` | 否   |                     | 玩家对象 |
| hero  | `object` | 否   | 引擎64_23.08.30新增 | 英雄对象 |

------------

### 加好友前触发

`addfriendrequest`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
------------

### 角色pk值变化触发
- 注:脚本设置pk值也会进入该触发,在触发中需要避免设置pk值造成死循环

`pkpointchanged`

| 参数    | 类型     | 空   | 默认 | 注释     |
| :------ | :------- | :--- | :--- | :------- |
| actor   | `object` | 否   |      | 角色对象 |
| pkpoint | `object` | 否   |      | pk值     |

### 英雄登陆触发

`herologin`

| 参数 | 类型     | 空   | 默认                | 注释     |
| :--- | :------- | :--- | :------------------ | :------- |
| play | `object` | 否   |                     | 玩家对象 |
| hero | `object` | 否   | 引擎64_23.08.30新增 | 英雄对象 |

------------

### 角色升级触发

`playlevelup`

| 参数  | 类型      | 空   | 默认                | 注释       |
| :---- | :-------- | :--- | :------------------ | :--------- |
| play  | `object`  | 否   |                     | 玩家对象   |
| level | `integer` | 否   | 引擎64_23.08.30新增 | 升级后等级 |

### 英雄升级触发

`herolevelup`

| 参数  | 类型      | 空   | 默认                | 注释       |
| :---- | :-------- | :--- | :------------------ | :--------- |
| play  | `object`  | 否   |                     | 玩家对象   |
| hero  | `object`  | 否   | 引擎64_23.08.30新增 | 英雄对象   |
| level | `integer` | 否   | 引擎64_23.08.30新增 | 升级后等级 |

------------

### 人物死亡之前

`nextdie`

| 参数   | 类型      | 空   | 默认 | 注释                             |
| :----- | :-------- | :--- | :--- | :------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                         |
| hiter  | `object`  | 否   |      | 击杀者对象                       |
| isplay | `integer` | 否   |      | 0=击杀者非玩家<br />1=击杀者是玩家 |

### 英雄死亡前触发

`heronextdie`

| 参数   | 类型      | 空   | 默认                | 注释                             |
| :----- | :-------- | :--- | :------------------ | :------------------------------- |
| play   | `object`  | 否   |                     | 玩家对象                         |
| hiter  | `object`  | 否   |                     | 击杀者对象                       |
| isplay | `integer` | 否   |                     | 0=击杀者非玩家<br />1=击杀者是玩家 |
| hero   | `object`  | 否   | 引擎64_23.08.30新增 | 英雄对象                         |

------------

### 公众号获取KEY成功触发

`bindwechat`

| 参数  | 类型     | 空   | 默认                | 注释      |
| :---- | :------- | :--- | :------------------ | :-------- |
| actor | `object` | 否   |                     | 玩家对象  |
| key   | `string` | 否   | 引擎64_23.08.30新增 | 公众号key |

### 公众号成功验证触发

`bindrewechat`

| 参数  | 类型     | 空   | 默认                | 注释          |
| :---- | :------- | :--- | :------------------ | :------------ |
| actor | `object` | 否   |                     | 玩家对象      |

```
    常量获取:
    输入的微信KEY：&lt;$REWECHATKEY&gt;
    微信ID：&lt;$REWECHATID&gt;
```

------------

### 查看别人装备触发

`lookhuminfo`

| 参数  | 类型     | 空   | 默认                | 注释           |
| :---- | :------- | :--- | :------------------ | :------------- |
| actor | `object` | 否   |                     | 玩家对象       |
| name  | `string` | 否   | 引擎64_23.08.30新增 | 被查看的玩家名 |

------------

### 阅读邮件触发

`readmail`

| 参数      | 类型      | 空   | 默认                | 注释     |
| :-------- | :-------- | :--- | :------------------ | :------- |
| actor     | `object`  | 否   |                     | 玩家对象 |
| mailID    | `integer` | 否   | 引擎64_23.08.30新增 | 邮件id   |
| mailTitle | `string`  | 否   | 引擎64_23.08.30新增 | 邮件标题 |

### 邮件提取触发

`getmailitem`

| 参数      | 类型      | 空   | 默认                | 注释           |
| :-------- | :-------- | :--- | :------------------ | :------------- |
| actor     | `object`  | 否   |                     | 玩家对象       |
| mailID    | `integer` | 否   | 引擎64_23.08.30新增 | 邮件id         |
| mailTitle | `string`  | 否   | 引擎64_23.08.30新增 | 邮件标题       |
| itemJson  | `string`  | 否   | 引擎64_23.08.30新增 | 提取物品的json |

------------

### 拍卖行相关

&gt; 拍卖行相关触发都可用`allowpaimai`接口阻止本次行为

#### 拍卖行上架触发

`canpaimaiitem`

| 参数          | 类型      | 空   | 默认                | 注释       |
| :------------ | :-------- | :--- | :------------------ | :--------- |
| actor         | `object`  | 否   |                     | 玩家对象   |
| itemIdx       | `integer` | 否   |                     | 物品id     |
| itemMakeIndex | `integer` | 否   |                     | 物品唯一id |
| moneyType     | `integer` | 否   |                     | 货币类型   |
| price1        | `integer` | 否   |                     | 竞拍价     |
| price2        | `integer` | 否   | 引擎64_24.05.23新增 | 一口价     |

```lua
function canpaimaiitem(actor,itemIdx,itemMakeIndex,moneyType,price1,price2)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"禁止上架物品")
        allowpaimai(actor,1)
        [[23.0830前引擎需要调用TXT命令打断,callscriptex(actor,"allowpaimai","1")]]
        return
    end
end

```

#### 拍卖行重新上架前触发

`canrepaimaiitem`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数          | 类型      | 空   | 默认 | 注释       |
| :------------ | :-------- | :--- | :--- | :--------- |
| actor         | `object`  | 否   |      | 玩家对象   |
| itemIdx       | `integer` | 否   |      | 物品id     |
| itemMakeIndex | `integer` | 否   |      | 物品唯一id |
| moneyType     | `integer` | 否   |      | 货币类型   |
| price1        | `integer` | 否   |      | 竞拍价     |
| price2        | `integer` | 否   |      | 一口价     |

```lua
function canrepaimaiitem(actor,itemIdx,itemMakeIndex,moneyType,price1,price2)
    if price2 &lt; 100 then
        say(actor,"一口价过低禁止上架!")
        allowpaimai(actor,1)
        return
    end
end

```

#### 拍卖行下架触发

`cangetbackpaimaiitem`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

#### 领取拍卖货币触发

`getpaimaiitem`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

#### 拍卖购买物品触发

`buypaimaiitem`

| 参数          | 类型      | 空   | 默认 | 注释       |
| :------------ | :-------- | :--- | :--- | :--------- |
| actor         | `object`  | 否   |      | 玩家对象   |
| itemIdx       | `integer` | 否   |      | 物品id     |
| itemMakeIndex | `integer` | 否   |      | 物品唯一id |
| moneyType     | `integer` | 否   |      | 货币类型   |
| price         | `integer` | 否   |      | 价格       |

```lua
function buypaimaiitem(actor,itemIdx,itemMakeIndex,moneyType,price)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"禁止购买物品")
        allowpaimai(actor,1)
        [[23.0830前引擎需要调用TXT命令打断,callscriptex(actor,"allowpaimai","1")]]
        return
    end
end

```

#### 拍卖行竞价触发

`biddingpaimaiitem`

| 参数          | 类型      | 空   | 默认 | 注释       |
| :------------ | :-------- | :--- | :--- | :--------- |
| actor         | `object`  | 否   |      | 玩家对象   |
| itemIdx       | `integer` | 否   |      | 物品id     |
| itemMakeIndex | `integer` | 否   |      | 物品唯一id |
| moneyType     | `integer` | 否   |      | 货币类型   |
| price         | `integer` | 否   |      | 价格       |

```lua
function buypaimaiitem(actor,itemIdx,itemMakeIndex,moneyType,price)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"禁止竞价物品")
        allowpaimai(actor,1)
        [[23.0830前引擎需要调用TXT命令打断,callscriptex(actor,"allowpaimai","1")]]
        return
    end
end

```

------------

### 采集怪相关

#### 采集前触发

`collectmonex`

| 参数         | 类型     | 空   | 默认 | 注释       |
| :----------- | :------- | :--- | :--- | :--------- |
| actor        | `string` | 否   |      | 玩家对象   |
| monIDX       | `number` | 否   |      | 怪物id     |
| monName      | `string` | 否   |      | 怪物名字   |
| monMakeIndex | `number` | 否   |      | 怪物唯一id |

#### 玩家点击采集怪物将会触发

`collectmon(X)`

&gt; X=怪物ID

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `string` | 否   |      | 玩家对象 |
| mon   | `string` | 否   |      | 怪物对象 |
------------

### 传送戒指传送前触发

`beginteleport`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `string` | 否   |      | 玩家对象 |
| X     | `number` | 否   |      | X坐标    |
| Y     | `number` | 否   |      | Y坐标    |


# 全局函数



## 消息公告

### 监听消息
需要在 **QFunction-0.lua** 文件中，注册监听函数
`handlerequest`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| self   | `object`  | 否   |      | 玩家对象 |
| msgid  | `integer` | 否   |      | 消息ID   |
| param1 | `integer` | 否   |      | 参数1    |
| param2 | `integer` | 否   |      | 参数2    |
| param3 | `integer` | 否   |      | 参数3    |
| sMsg   | `string`  | 否   |      | 消息体   |

### 发送消息
`sendluamsg`

&gt; sMsg消息体最大长度16000字节

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| self   | `object`  | 否   |      | 玩家对象 |
| msgid  | `integer` | 否   |      | 消息ID   |
| param1 | `integer` | 是   |      | 参数1    |
| param2 | `integer` | 是   |      | 参数2    |
| param3 | `integer` | 是   |      | 参数3    |
| sMsg   | `string`  | 是   |      | 消息体   |

```lua
function handlerequest(self, msgid, n1, n2, n3, sMsg)
    if (msgid == 10) then
        release_print("收到10号消息")
    else
        sendluamsg(self, msgid, n1, n2, n3, sMsg)
    end
end
```

### 发送视野内广播消息
`sendrefluamsg`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| self   | `object`  | 否   |      | 玩家对象 |
| msgid  | `integer` | 否   |      | 消息ID   |
| param1 | `integer` | 是   |      | 参数1    |
| param2 | `integer` | 是   |      | 参数2    |
| param3 | `integer` | 是   |      | 参数3    |
| sMsg   | `string`  | 是   |      | 消息体   |

### 发送聊天框消息

`sendmsg`

| 参数 | 类型      | 空   | 默认 | 注释                                                         |
| :--- | :-------- | :--- | :--- | :----------------------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                                     |
| type | `integer` | 否   |      | 发送对象：<br />1-自己，2-全服<br />3-行会，4-当前地图<br />5-组队 |
| msg  | `string`  | 否   |      | Json消息内容                                                 |

### 发送地图消息

`sendmapmsg`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| mapid | `string` | 否   |      | 地图id       |
| msg   | `string` | 否   |      | Json消息内容 |

- Json格式
```json
{"Msg":"xxx","FColor":255,"BColor":255,"Type":1,"Time":3,"SendName":"xxx","SendId":"123"}
```

| 参数     | 类型     | 描述                                                                                                                                                                                                                              |
| :------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Msg      | string   | 消息内容                                                                                                                                                                                                                          |
| FColor   | `number` | 前景色(可为空)                                                                                                                                                                                                                    |
| BColor   | `number` | 背景色(可为空)                                                                                                                                                                                                                    |
| Type     | `number` | 1=系统频道;2=行会频道;<br />3=组队频道;4=顶部跑马灯公告;<br />5=屏幕跑马灯公告,可控制Y轴;<br />6=聊天上方公告;8=固定聊天;<br />9=systemtips;<br />10=可控制xy坐标广播;<br />11=屏幕跑马灯公告,系统公告;<br />12=系统频道 带超链;<br />13=系统公告缩放 |
| Time     | `number` | 倒计时(秒) (可为空)                                                                                                                                                                                                               |
| SendName | `string` | 发送人(可为空)                                                                                                                                                                                                                    |
| SendId   | `string` | 发送ID（可为空）                                                                                                                                                                                                                  |
```lua
function main(self)
    sendmsg(self, 2, '{"Msg":"你好","FColor":255,"BColor":0,"Type":1,"Time":3,"SendName":"xxx","SendId":"123"}')
end
```

### 设置聊天前缀
`setchatprefix`

| 参数   | 类型      | 空   | 默认 | 注释                       |
| :----- | :-------- | :--- | :--- | :------------------------- |
| object | `object`  | 否   |      | 玩家对象                   |
| Prefix | `string`  | 否   |      | 前缀信息，空则清除聊天前缀 |
| color  | `integer` | 否   |      | 背景色                     |

### 打印消息到控制台
`release_print`

| 参数 | 类型  | 空   | 默认 | 注释     |
| :--- | :---- | :--- | :--- | :------- |
| arr  | `any` | 否   |      | 数组内容 |

* 引擎开发模式，会输出到控制台上，线上模式，会记录到ScriptXX文件里，可以用于排查错误
```lua
    release_print('aa','bb')
```

### 发送自定义颜色的文字信息
`guildnoticemsg`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                            |
| :----- | :-------- | :--- | :--- | :-------------------------------------------------------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                                                                        |
| FColor | `integer` | 否   |      | 前景色                                                                                                          |
| BColor | `integer` | 否   |      | 背景色                                                                                                          |
| Msg    | `string`  | 否   |      | 消息内容                                                                                                        |
| flag   | `string`  | 是   |      | 发送对象：<br />Self：只发给自己；<br />Group：发送给组队：Map：发送到当前地图中的人物；<br />省略参数四表示全服发送. |

### 发送屏幕中间大字体信息
`sendcentermsg`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                                           |
| :----- | :-------- | :--- | :--- | :----------------------------------------------------------------------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                                                                                       |
| FColor | `integer` | 否   |      | 前景色                                                                                                                         |
| BColor | `integer` | 否   |      | 背景色                                                                                                                         |
| Msg    | `string`  | 否   |      | 消息内容                                                                                                                       |
| flag   | `string`  | 否   |      | 发送对象：<br />0=发送给自己；<br />1=发送所有人物；<br />2=发送行会；<br />3=发送国家；<br />4=发送当前地图；<br />5=替换模式；<br />7=组队 |
| time   | `integer` | 是   |      | 显示时间                                                                                                                       |
| func   | `string`  | 是   |      | 倒计时结束后跳转的脚本位置，对应脚本需要放QFunction脚本中，使用跳转时，消息文字提示中必须包含%d，用于显示倒计时时间            |
```lua
[[显示30秒：]]
    sendcentermsg(actor,180,251,"这是一个居中显示的公告.",0,30)
    
[[执行倒计时标签(注意:文字提示中必须包含%d)：]]
    sendcentermsg(actor,180,251,"还剩余%d发放新手奖励.",0,30,"@givenewhumanitem")
```
### 发送聊天框固顶信息
`sendtopchatboardmsg`

| 参数     | 类型      | 空   | 默认 | 注释                                                             |
| :------- | :-------- | :--- | :--- | :--------------------------------------------------------------- |
| player   | `object`  | 否   |      | 玩家对象                                                         |
| type     | `integer` | 否   |      | 发送对象<br />0-所有人<br />1-自己<br />2-行会<br />3-当前地图<br />4-组队 |
| FColor   | `integer` | 否   |      | 字体景色                                                         |
| BColor   | `integer` | 否   |      | 背景色                                                           |
| time     | `integer` | 否   |      | 显示时间，自动替换内容中的%d                                     |
| msg      | `string`  | 否   |      | 消息内容                                                         |
| showflag | `integer` | 否   |      | 是否显示人物名称<br />0-是<br />1-否                                 |

### 发送屏幕滚动信息
`sendmovemsg`

| 参数   | 类型      | 空   | 默认 | 注释                                                                   |
| :----- | :-------- | :--- | :--- | :--------------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                               |
| type   | `integer` | 否   |      | 模式，发送对象<br />0-自己<br />1-所有人<br />2-行会<br />3-当前地图<br />4-组队 |
| FColor | `integer` | 否   |      | 字体景色                                                               |
| BColor | `integer` | 否   |      | 背景色                                                                 |
| Y      | `integer` | 否   |      | Y坐标                                                                  |
| scroll | `integer` | 否   |      | 滚动次数                                                               |
| msg    | `string`  | 否   |      | 消息内容                                                               |

### 屏幕任意坐标发送公告信息
`sendcustommsg`

| 参数   | 类型      | 空   | 默认 | 注释                                                           |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                       |
| type   | `integer` | 否   |      | 消息类型<br />0-全服<br />1-自己<br />2-组队<br />3-行会<br />4-当前地图 |
| msg    | `string`  | 否   |      | 消息内容                                                       |
| FColor | `integer` | 否   |      | 前景色                                                         |
| BColor | `integer` | 否   |      | 背景色                                                         |
| X      | `integer` | 否   |      | X坐标                                                          |
| Y      | `integer` | 否   |      | Y坐标                                                          |

### 主屏幕弹出公告
`sendmsgnew`

| 参数   | 类型      | 空   | 默认 | 注释                                                                   |
| :----- | :-------- | :--- | :--- | :--------------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                               |
| FColor | `integer` | 否   |      | 前景色                                                                 |
| BColor | `integer` | 否   |      | 背景色                                                                 |
| msg    | `string`  | 否   |      | 公告内容                                                               |
| type   | `integer` | 否   |      | 模式，发送对象<br />0-自己<br />1-所有人<br />2-行会<br />3-当前地图<br />4-组队 |
| time   | `integer` | 否   |      | 显示时间                                                               |

### 显示倒计时信息提示
`senddelaymsg`

| 参数      | 类型      | 空   | 默认 | 注释                                 |
| :-------- | :-------- | :--- | :--- | :----------------------------------- |
| player    | `object`  | 否   |      | 玩家对象                             |
| msg       | `string`  | 否   |      | 消息内容                             |
| time      | `integer` | 否   |      | 时间，秒                             |
| FColor    | `integer` | 否   |      | 字体景色                             |
| mapdelete | `integer` | 否   |      | 换地图是否删除<br />0-不删除<br />1-删除 |
| tag       | `string`  | 否   |      | 跳转的函数字段                       |
| X         | `integer` | 否   |      | X坐标                                |

### 过滤全服提示信息
`filterglobalmsg`

| 参数   | 类型      | 空   | 默认 | 注释                           |
| :----- | :-------- | :--- | :--- | :----------------------------- |
| player | `object`  | 否   |      | 玩家对象                       |
| flag   | `integer` | 否   |      | 是否过滤<br />0-不过滤<br />1-过滤 |

```
开启过滤全服提示信息，不再接受如SENDMSG、GuildNoticeMsg等等脚本命令发送的全服提示信息。
```

### 弹出窗口消息
`messagebox`

| 参数   | 类型     | 空   | 默认 | 注释             |
| :----- | :------- | :--- | :--- | :--------------- |
| player | `object` | 否   |      | 玩家对象         |
| info   | `string` | 否   |      | 弹出内容         |
| flag1  | `string` | 否   |      | 确定后跳转的接口 |
| flag2  | `string` | 否   |      | 取消后跳转的接口 |
```lua
messagebox(actor,"系统消息\\待填写的文本..","@func_ok,1,2,3","@func_no,4,5,6")

function func_ok(actor,...)
    release_print("func_ok",...)
end

function func_no(actor,...)
    release_print("func_no",...)
end
```

### 调用触发
`gotolabel`

| 参数   | 类型      | 空   | 默认                                     | 注释                                                                                                                  |
| :----- | :-------- | :--- | :--------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
| player | `object`  | 否   |                                          | 玩家对象                                                                                                              |
| type   | `integer` | 否   | 8:当前国家人物触发<br />引擎64_23.0628新增 | 触发模式：<br />0小组成员触发<br />1行会成员触发<br />2当前地图的人物触发<br />3当前角色范围的人物触发<br />8当前国家的人物触发 |
| label  | `string`  | 否   |                                          | 跳转后的接口                                                                                                          |
| range  | `integer` | 否   |                                          | 触发模式=3时<br />指定的范围大小                                                                                            |

```lua
    gotolabel(actor,2,"gotolabelfunc,1,2,3")

    function gotolabelfunc(actor,...)
        release_print("gotolabelfunc",getbaseinfo(actor,1),...)
    end
```

##  其他

### 刷新血量/蓝量
`healthspellchanged`

| 参数   | 类型     | 空   | 默认 | 注释          |
| :----- | :------- | :--- | :--- | :------------ |
| object | `object` | 否   |      | 玩家/怪物对象 |

### 新手界面引导功能
`navigation`

| 参数   | 类型      | 空   | 默认 | 注释       |
| :----- | :-------- | :--- | :--- | :--------- |
| player | `object`  | 否   |      | 玩家对象   |
| NPCIdx | `integer` | 否   |      | 界面ID     |
| BtnIdx | `integer`/`string` | 否   |      | 按钮索引   |
| sMsg   | `string`  | 否   |      | 显示的内容 |
```lua
[[
参数2：界面ID(主界面ID;0=NPC面板;1=角色背包;2= 角色界面;3=英雄背包;40=英雄头像;200=PC端下方3个按钮;任务主窗口引导=任务的ID  9-12=商城面板 201=右下角切换按钮 202=玩家主面板 203=英雄主面板)
参数3：按钮ID(每个界面自己定义的ID)  例如：&lt;Text|id=221|x=25|y=20|color=255|size=18|text=NPC面板提示|link=@NPC面板提示&gt;  id=221就是NPC按钮ID
        当参数2=（9-12=商城面板）   参数3=商城序号ID
        当参数2=（202=玩家主面板）  参数3=人物1-6装备界面页签
        当参数2=（203=英雄主面板）  参数3=英雄1-6装备界面页签
参数4：文字内容
]]

例子一:
local str = "&lt;Text|id=221|x=25|y=20|color=255|size=18|text=NPC面板提示|link=@NPC面板提示&gt;"
say(actor,str)
navigation(actor,0,221,"引导文本")

例子二:
navigation(actor,202,1,"测试提示2")
```

### 查看别人面板信息
`viewplayer`

| 参数   | 类型      | 空   | 默认 | 注释                                  |
| :----- | :-------- | :--- | :--- | :------------------------------------ |
| player | `object`  | 否   |      | 玩家对象                              |
| userid | `string`  | 否   |      | 其他玩家的UserID                      |
| winID  | `integer` | 否   |      | 面板ID：101-装备，106-称号，1011-时装 |

### 查看自己面板
`openwindows`

| 参数   | 类型      | 空   | 默认 | 注释                                                            |
| :----- | :-------- | :--- | :--- | :-------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                        |
| winID  | `integer` | 否   |      | 101=装备 102=状态 103=属性 104=技能 105=生肖 106=称号 1011=时装 |

------------

### 调用TXT脚本命令
`callscript`

&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;"&gt;**特殊：该接口为异步调用,且消耗大,推荐使用callscriptex**&lt;/font&gt;

| 参数     | 类型      | 空   | 默认 | 注释     |
| :------- | :-------- | :--- | :--- | :------- |
| player   | `object`  | 否   |      | 玩家对象 |
| filename | `string`  | 否   |      | 文件名   |
| label    | `integer` | 否   |      | 标签     |
```lua
    [[表示调用执行“测试.txt”文件中的[@测试]标签内容
    “测试.txt”默认读取 Mir200\Envir\Market_def\ 文件夹下，如果有子文件夹，则加载文件名之前]]
    callscript(actor, '测试'， '@测试') 

    [["测试.txt" 位于 Mir200\Envir\Market_def\盟重\ 文件夹下]]
    callscript(actor, '盟重/测试'， '@测试') 
```

### 调用传奇脚本命令
`callscriptex`

| 参数       | 类型     | 空   | 默认 | 注释         |
| :--------- | :------- | :--- | :--- | :----------- |
| player     | `object` | 否   |      | 玩家对象     |
| scriptname | `string` | 否   |      | 脚本接口     |
| arr        | `any`    | 否   |      | 参数1~参数10 |

```lua
function main(self)
  callscriptex(self, "SENDMSG", 0, "缝合怪")
end
```

`callcheckscriptex`

| 参数       | 类型     | 空   | 默认 | 注释           |
| :--------- | :------- | :--- | :--- | :------------- |
| player     | `object` | 否   |      | 玩家对象       |
| scriptname | `string` | 否   |      | 脚本接口       |
| arr        | `any`    | 否   |      | 参数1~参数10   |
| result     | `bool`   | 是   |      | 返回值，布尔值 |

------------

### 根据唯一id获取视野内的目标对象

`getvisibleactor`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口,替换引擎:[996M2.rar](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=6994fd675e9a3598850b552923623aff "[996M2(2024.08.07.0_64位)[20241106].rar")&lt;/font&gt;**

&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;"&gt;**特殊：该接口只能获取玩家[参数1]视野内的目标,用于解决TXT调用LUA时获取对象困难问题**&lt;/font&gt;

| 参数       | 类型     | 空   | 默认 | 注释           |
| :--------- | :------- | :--- | :--- | :------------- |
| player     | `object` | 否   |      | 玩家对象       |
| userID     | `string` | 否   |      | 目标唯一ID       |
| result     | `object`   | 否   |      | 返回值，目标对象 |

```lua
    -- userID 可以是玩家/英雄/怪物/宠物/人形怪的
    function main(actor,userID)
        local objcet = getvisibleactor(actor,userID)
        release_print("根据唯一id获取视野内的目标对象",userID,getbaseinfo(objcet,1))
    end
```
# 全局信息



### 获取全局信息
`globalinfo` 或 `grobalinfo`
* 说明 id 对应值
0: 全局玩家信息
1: 部署时间开始 开发天数 **开区天数建议获取常量`&lt;$KFDAY&gt;`**
2: 部署时间开始 开服时间 **开服时间建议获取常量`&lt;$showtime&gt;`**
3: 合服次数
4: 合服时间
5: 服务器IP
6: 玩家数量
7: 背包最大数量
8: 引擎版本号（以线上版本为准,测试版、本地版可能存在差异）
9：游戏id
~~10：服务器名称~~**获取异常,用常量`&lt;$SERVERNAME&gt;`**
11：服务器id

```lua
    function main(self)
        say(self,"当前开服天数"..globalinfo(1).."在线玩家数:"..globalinfo(6))
    end
```

### 获取Envir文件夹下文件列表
`getenvirfilelist`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|result       |`object`        |否   |    |   文件列表（含相对路径）    |

### 获取服务器上64位时间戳
`gettcount64`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|result       |`int`       |否   |    |  64位整数，单位毫秒   |
```
系统启动时间,非Unix时间戳;需要获取Unix时间戳使用 os.time()
```

## 操作Ini文件

### 读取Ini文件中的字段值
`readini`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |
|result       |`string`        |否   |    |  配置项值   |

### 写入Ini文件中的字段值
`writeini`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |
|value    |`string`        |否   |    |  配置项值   |

### 删除Ini文件配置区
`delinisection`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |

### 删除Ini文件配置项
`deliniitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |

## 操作Ini文件命令(带Cache,引擎关闭才会保存)
```
操作速度会比不带cache的快很多，问题就是，在M2运行过程中，只能用脚本操作，手动操作的无效。
如果ini文件不存在手动操作的情况下，就用带Cache命令操作。
带Cache的特点是，对ini的操作只打开一次，然后一直在内存缓存，所以只命令操作才有效，手动操作无效。
关闭引擎时候才会保存到INI文件内，引擎运行期间一直内存中运行，所以启动引擎后手动修改INI文件信息是无效的。

在没有手动操作ini的情况下，推荐用带cache的。不带cache的比较耗时。
比如提现：操作会删除提现记录属于手动操作，所以需要使用不带cache的命令；但计算战斗力属于内部引擎操作无手动干预，可以使用带cache的！
```

### 读取Ini文件中的字段值（带Cache）
`readinibycache`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |
|result       |`string`        |否   |    |  配置项值   |
```lua
    local str = readinibycache("QuestDiary/test.ini","Setup","temp1")
    release_print("str",str)
```
### 写入Ini文件中的字段值（带Cache）
`writeinibycache`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |
|value    |`string`        |否   |    |  配置项值   |

### 删除Ini文件配置区（带Cache）
`delinisectionbycache`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |

### 删除Ini文件配置项（带Cache）
`deliniitembycache`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|section      |`string`        |否   |    |  配置项区   |
|item     |`string`        |否   |    |  配置项   |

## 操作csv文件

- Lua里面限制了起始路径,所以文件名有填写有些不同。

### 加载csv表格内容
`newreadcsv`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
```lua
    newreadcsv("QuestDiary\\test.csv")
    release_print("csv表预加载成功")
```
### 读取表里面的第几行第几列内容(0行0列开始)
`newdqcsv`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|row      |`int`       |否   |    |  行数   |
|col      |`int`       |否   |    |  列数   |
|result       |`string`        |否   |    |  表内数据   |
```lua
    local str = newdqcsv("QuestDiary\\test.csv",4,0)
    release_print("第4行,第0列",str)
```

### 获取当前表格最大行数、和获取表格最大列数
`gethlcsv`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|type     |`int`       |否   |    |  读取目标：0-行数，1-列数   |
```lua
    local w = gethlcsv("QuestDiary\\test.csv",0)
    local h = gethlcsv("QuestDiary\\test.csv",1)
    release_print("行数",w)
    release_print("列数",h)
```
### 取字符串在csv表格中的行号
`getgjcsv`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|filename     |`string`        |否   |    |  文件名   |
|str      |`string`        |否   |    |  字符串   |
|rowlimit     |`string`        |否   |    |  行数限制，格式：开始行号-结束行号   |
|col      |`int`       |否   |    |  查找的列数   |
|findtype     |`int`       |否   |    |  查找类型：<br />0-在开始哪行;<br /> 1-在最后哪行;    |

```lua
    local param = getgjcsv("QuestDiary\\test.csv","2","0-5",0,0)
    release_print("字符串'2'在0列开始第"..param.."行")
```

------------

### 读取表格

`readexcel`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释                 |
| :----- | :------- | :--- | :--- | :------------------- |
| path   | `string` | 否   |      | 表格路径             |
| result | `table`  | 否   |      | 返回表格所有数据内容 |

```lua
    local readPath = "../DATA/cfg_npclist.xls"
    local config = readexcel(readPath)
    release_print("readexcel",readPath,type(config))
    for i, cfg in ipairs(config or {}) do
        release_print("============================")
        -- if i &gt; 10 then return end
        if type(cfg) == "table" then
            for j, value in ipairs(cfg) do
                release_print("config",i,j,value)
            end
        end
    end
```

------------

### 接口删除Envir目录下的指定文件

`delfile`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| path   | `string` | 否   |      | 文件路径     |

```lua
	delfile("../QuestDiary/abc.txt")
```
# 引擎变量



## 引擎系统变量

| 变量 | 类型           | 说明                                                                |
| :--- | :------------- | :------------------------------------------------------------------ |
| `A`  | 字符型系统变量 | 重启服务器保存.500个(A0 - A499)  存放在Mir200/GlobalVal.ini文件里面 |
| `G`  | 数字型系统变量 | 重启服务器保存.500个(G0 - G499)  存放在Mir200/GlobalVal.ini文件里面 |
| `I`  | 数字型系统变量 | 重启服务器不保存.100个(I0 - I99)                                    |

### 获取系统变量

`getsysvar`

| 参数    | 类型               | 空   | 默认 | 注释   |
| :------ | :----------------- | :--- | :--- | :----- |
| varName | `string`           | 否   |      | 变量名 |
| result  | `string`/`integer` |      |      | 变量值 |

### 设置系统变量

`setsysvar`

| 参数    | 类型               | 空   | 默认 | 注释   |
| :------ | :----------------- | :--- | :--- | :----- |
| varName | `string`           | 否   |      | 变量名 |
| value   | `string`/`integer` |      |      | 变量值 |

```lua
    --系统变量示例
    setsysvar("A1","996abc")
    say(actor, "系统字符变量A1变量="..getsysvar("A1"))

    setsysvar("G2",996)
    say(actor, "系统数字变量G2变量="..getsysvar("G2"))

    setsysvar("I3",666)
    say(actor, "系统数字变量I3变量="..getsysvar("I3"))
```

------------

## 引擎玩家变量

| 变量       | 类型           | 说明                                                                                          |
| :--------- | :------------- | :-------------------------------------------------------------------------------------------- |
| `S`        | 字符型个人变量 | 下线不保存.100个(S0 - S99)                                                                    |
| `P`        | 数字型个人变量 | 仅在当前NPC有效.当Close对话时.所有P变量归零.100个(P0 - P99)                                   |
| `D`        | 数字型个人变量 | 下线不保存.100个(D0 - D99)摇骰子变量                                                          |
| `N`        | 数字型个人变量 | 下线不保存.100个(N0 - N99)                                                                    |
| `M`        | 数字型个人变量 | 下线不保存.100个(M0 - M99)切换地图清空                                                        |
| `U`        | 数字型个人变量 | 可保存.255个(U0 - U254)（存放在SQL角色数据库）最大值21亿                                      |
| `T`        | 字符型个人变量 | 可保存.255个(T0 - T254)（存放在SQL角色数据库）最大长度8000字符串以内                          |
| `J`        | 数字型个人变量 | 可保存.每晚自动12点重置,合区或关停服务器请错开00:00点.500个(J0 - J499)（存放在SQL角色数据库） |
| `Z`        | 字符型个人变量 | 可保存.每晚自动12点重置,合区或关停服务器请错开00:00点.500个(Z0 - Z499)（存放在SQL角色数据库） |
| `B`        | 数字型个人变量 | 可保存.最高支持19位数,适用大数值操作.100个(B0 - B99)（存放在SQL角色数据库）                   |
| `个人标记` | 整数型个人变量 | 可保存,该变量只有0和1的两种状态                                                               |

### 获取玩家变量

`getplaydef`

| 参数    | 类型               | 空   | 默认 | 注释     |
| :------ | :----------------- | :--- | :--- | :------- |
| actor   | `object`           | 否   |      | 玩家对象 |
| varName | `string`           | 否   |      | 变量名   |
| result  | `string`/`integer` |      |      | 变量值   |

### 设置玩家变量

`setplaydef`

| 参数    | 类型               | 空   | 默认 | 注释     |
| :------ | :----------------- | :--- | :--- | :------- |
| actor   | `object`           | 否   |      | 玩家对象 |
| varName | `string`           | 否   |      | 变量名   |
| value   | `string`/`integer` |      |      | 变量值   |

> **支持自定义临时变量**
 格式：1.自定义数字变量，以`N$`为头标志；
 2.自定义字符变量，以`S$`为头标志
 
```lua
  --玩家变量示例
    setplaydef(actor, "U1",1)
    say(actor, "玩家数字变量U1变量="..getplaydef(actor,"U1"))

  --临时玩家变量示例
    setplaydef(actor, "N$变量1",1)
    say(actor, "自定义数字变量N$变量1="..getplaydef(actor,"N$变量1"))
```

```lua
    [[lua获取TXT命令设置的高效率版键值对,仅作参考,可根据自身需求修改]]
    function getVarCache(actor,varName,key)
        local str = getplaydef(actor,varName)
        local result = {}
        for k, v in string.gmatch(str, "([^=]+)=([^,]+)") do
            k = k:gsub(",", "")
            result[k] = v
        end
        return result[tostring(key)] or ""
    end

    local value = getVarCache(actor,"T1",1)
```

### 获取人物标记/标识值

`getflagstatus`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| play   | `object`  | 否   |      | 玩家对象      |
| nIndex | `integer` | 否   |      | 索引（1-800） |
| result | `integer` | 否   |      | 对应属性值    |

### 设置人物标记/标识值

`setflagstatus`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| play   | `object`  | 否   |      | 玩家对象      |
| nIndex | `integer` | 否   |      | 索引（1-800） |
| nvalue | `integer` | 否   |      | 对应属性值(0/1)    |
# 自定义变量



## 系统自定义变量

> **系统自定义变量需要初始化后才能使用**
> **引擎每次启动都需要初始化**
> **一个变量名不允许初始化两种变量类型**

### 初始化自定义变量

`inisysvar`

| 参数      | 类型     | 空   | 默认 | 注释                     |
| :-------- | :------- | :--- | :--- | :----------------------- |
| varType   | `string` | 否   |      | 变量类型(integer/string) |
| varName   | `string` | 否   |      | 变量名                   |
| mergeType | `integer` | 是   | 0    | 合服类型                 |

```lua
-- 引擎启动触发
function startup(sysobj)
    inisysvar("integer","系统变量_1",0)  --声明合区时 保留主区
    inisysvar("integer","系统变量_2",1)  --声明合区时 保留副区
    inisysvar("integer","系统变量_3",2)  --声明合区时 取大
    inisysvar("integer","系统变量_4",3)  --声明合区时 取小
    inisysvar("integer","系统变量_5",4)  --声明合区时 相加
    inisysvar("string","系统变量_6",5)   --声明合区时 相连
    inisysvar("string","系统变量_7",6)   --声明合区时 删除
end
```

### 获取自定义变量

`getsysvarex`

| 参数    | 类型               | 空   | 默认 | 注释   |
| :------ | :----------------- | :--- | :--- | :----- |
| varName | `string`           | 否   |      | 变量名 |
| result  | `string`/`integer` |      |      | 变量值 |

### 设置自定义变量

`setsysvarex`

| 参数    | 类型               | 空   | 默认 | 注释                                 |
| :------ | :----------------- | :--- | :--- | :----------------------------------- |
| varName | `string`           | 否   |      | 变量名                               |
| value   | `string`/`integer` | 否   |      | 变量值                               |
| isSave  | `integer`          | 是   | 0    | 是否保存数据库<br>0=不存储<br>1=存储 |

```lua
    --系统变量示例
    local varName = "系统自定义变量_1"
    inisysvar("integer",varName,0)
    setsysvarex(varName,996,1)
    release_print("系统自定义变量[integer]",varName,getsysvarex(varName))

    local varName = "系统自定义变量_2"
    inisysvar("string",varName,0)
    setsysvarex(varName,"996abc",1)
    release_print("系统自定义变量[string]",varName,getsysvarex(varName))
```

------------

## 玩家自定义变量

> **玩家自定义变量需要初始化后才能使用**
> **玩家每次登陆都需要初始化**
> **一个变量名不允许初始化两种变量类型**

### 初始化自定义变量

`iniplayvar`

| 参数      | 类型     | 空   | 默认 | 注释                         |
| :-------- | :------- | :--- | :--- | :--------------------------- |
| actor     | `object` | 否   |      | 玩家对象                     |
| varType   | `string` | 否   |      | 变量类型(integer/string)     |
| varScope  | `string` | 否   |      | 变量范围(HUMAN/GUILD/NATION) |
| varName   | `string` | 否   |      | 变量名                       |

```lua
-- 角色登陆触发
function login(actor)
    iniplayvar(actor, "integer", "HUMAN", "玩家变量_1")
    iniplayvar(actor, "string", "HUMAN", "玩家变量_2")
end
```

### 获取自定义变量

`getplayvar`

| 参数     | 类型               | 空   | 默认    | 注释                         |
| :------- | :----------------- | :--- | :------ | :--------------------------- |
| actor    | `object`           | 否   |         | 玩家对象                     |
| varScope | `string`           | 是   | `HUMAN` | 变量范围(HUMAN/GUILD/NATION) |
| varName  | `string`           | 否   |         | 变量名                       |
| result   | `string`/`integer` |      |         | 变量值                       |

### 设置自定义变量

`setplayvar`

| 参数     | 类型               | 空   | 默认 | 注释                                 |
| :------- | :----------------- | :--- | :--- | :----------------------------------- |
| actor    | `object`           | 否   |      | 玩家对象                             |
| varScope | `string`           | 否   |      | 变量范围(HUMAN/GUILD/NATION)         |
| varName  | `string`           | 否   |      | 变量名                               |
| value    | `string`/`integer` | 否   |      | 变量值                               |
| isSave   | `integer`          | 是   | 0    | 是否保存数据库<br>0=不存储<br>1=存储 |

```lua
    --系统变量示例
    local varName = "玩家自定义变量_1"
    iniplayvar(actor, "integer", "HUMAN", varName)
    setplayvar(actor,"HUMAN",varName,996,1)
    release_print("玩家自定义变量[integer]",varName,getplayvar(actor,varName))

    local varName = "玩家自定义变量_2"
    iniplayvar("string",varName,0)
    setplayvar(actor,"HUMAN",varNamem,"996abc",1)
    release_print("玩家自定义变量[string]",varName,getplayvar(actor,varName))
```

------------

## 行会自定义变量（由行会对象操作自定义变量）

### 初始化行会自定义变量

`iniguildvar`

| 参数    | 类型     | 空   | 默认 | 注释                     |
| :------ | :------- | :--- | :--- | :----------------------- |
| guild   | `object` | 否   |      | 行会对象                 |
| varType | `string` | 否   |      | 变量类型(integer/string) |
| varName | `string` | 否   |      | 变量名                   |

### 设置自定义变量

`setguildvar`

| 参数    | 类型               | 空   | 默认 | 注释                                 |
| :------ | :----------------- | :--- | :--- | :----------------------------------- |
| guild   | `object`           | 否   |      | 行会对象                             |
| varName | `string`           | 否   |      | 变量名                               |
| value   | `string`/`integer` | 否   |      | 变量值                               |
| isSave  | `integer`          | 是   | 0    | 是否保存数据库<br>0=不存储<br>1=存储 |

### 获取自定义变量

`getguildvar`

| 参数    | 类型               | 空   | 默认 | 注释     |
| :------ | :----------------- | :--- | :--- | :------- |
| guild   | `object`           | 否   |      | 行会对象 |
| varName | `string`           | 否   |      | 变量名   |
| result  | `string`/`integer` |      |      | 变量值   |

```lua
function main(actor) 
    guild = getmyguild(actor)
    iniguildvar(guild, "integer", "N变量1")
    setguildvar(guild, "N变量1", 997)
    say(self, "自定义变量 N变量1="..getguildvar(guild, "N变量1"))
end
```
```lua
function main(actor) 
    guild = getmyguild(actor)
    iniguildvar(guild, "string", "S变量1|S变量2")
    setguildvar(guild, "S变量1", "引擎", 1)
    say(self, "自定义变量 S变量1="..getguildvar(guild, "S变量1"))
end
```

------------

## 变量操作

### 自定义变量排序

`sorthumvar`

| 参数     | 类型     | 空   | 默认 | 注释                                                      |
| :------- | :------- | :--- | :--- | :-------------------------------------------------------- |
| var      | `string` | 否   |      | 排序变量名                                                |
| playflag | `int`    | 否   |      | 0-所有玩家 1-在线玩家 2-行会                              |
| sortflag | `int`    | 否   |      | 0-升序，1-降序                                            |
| count    | `int`    | 否   |      | 获取的数据量<br>为空或0取所有，取前几名                   |
| result   | `table`  |      |      | 获取的列表，<br>{人物名称，变量值，人物名称，变量值，...} |

```lua
    local ranking = sorthumvar(varname,0,1,0)
    local index = 0
    for i = 1, #ranking, 2 do
        index = index + 1
        release_print("榜",index,ranking[i],ranking[i + 1])
    end
```

### 取自定义数字变量名位置

`humvarrank`

| 参数     | 类型     | 空   | 默认 | 注释                  |
| :------- | :------- | :--- | :--- | :-------------------- |
| actor    | `object` | 否   |      | 人物对象              |
| var      | `string` | 否   |      | 排序变量名            |
| playflag | `int`    | 否   |      | 0-所有玩家 1-在线玩家 |
| sortflag | `int`    | 否   |      | 0-升序，1-降序        |
| result   | `int`    |      |      | 人物的名次            |

### 清理个人自定义变量

`clearhumcustvar`

| 参数  | 类型     | 空   | 默认 | 注释                                        |
| :---- | :------- | :--- | :--- | :------------------------------------------ |
| actor | `object` | 否   |      | 要清理的人物对象<br>传入 * 表示清理所有玩家 |
| var   | `string` | 否   |      | 变量名, <br> * -所有变量                    |
```lua
    -- 多个变量用|分隔
    clearhumcustvar("*","*")
    clearhumcustvar(actor,"S变量1|S变量2")
```

### 清理自定义系统变量

`clearglobalcustvar`

| 参数 | 类型     | 空   | 默认 | 注释                |
| :--- | :------- | :--- | :--- | :------------------ |
| var  | `string` | 否   |      | 变量名, * -所有变量 |
```lua
    -- 多个变量用|分隔
    clearglobalcustvar("*")
    clearglobalcustvar("S变量1|S变量2")
```

### 清理自定义行会变量

`clearguildcustvar`

| 参数      | 类型     | 空   | 默认 | 注释                       |
| :-------- | :------- | :--- | :--- | :------------------------- |
| guildName | `string` | 否   |      | 行会名称, <br> * -所有行会 |
| var       | `string` | 否   |      | 变量名, <br> * -所有变量   |
```lua
    -- 多个行会用|分隔，多个变量用|分隔
    clearguildcustvar("*","*")
    clearguildcustvar("行会名称","S变量1|S变量2")
```
# 拓展变量



## 物品变量

&gt; 物品变量若要通知前端,需在cfg_game_data.xls表中配置 `UseItemIntParamsToClient`/`UseItemParamsToClient`
&gt; `M2-GameData表配置-物品变量设置`中也可以配置

| 字段                       | 参数                   | 说明                                      |
| :------------------------- | :--------------------- | :---------------------------------------- |
| `UseItemIntParamsToClient` | `1,2,3,4,5,6,7,8,9,10` | 需要下发给前端的integer型物品变量id(1~50) |
| `UseItemParamsToClient`    | `1,2,3,4,5,6,7,8,9,10` | 需要下发给前端的string型物品变量id(1~20)  |

```lua
    --前端获取物品变量
    local value = SL:GetMetaValue("ITEM_CUSTOM_ATTR",itemData.MakeIndex)
    SL:dump(value,"元变量")

    --前端监听物品变量改变时间
    SL:RegisterLUAEvent("LUA_EVENT_ITEM_CUSTOM_ATTR", "GUIUtil", function(data)
        SL:dump(data,"触发回调",5)
    end)
```

#### 存储物品str变量[拓展]

`setitemparam`

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                       |
| where   | `integer` | 否   |      | 装备位置<br />(-2则传入物品对象) |
| idx     | `integer` | 否   |      | 变量位置(1-20)                 |
| value   | `string`  | 否   |      | 变量值                         |
| itemobj | `object`  | 是   |      | 物品对象(参数2传入-2时有效)    |

#### 获取物品str变量[拓展];

`getitemparam`

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                       |
| where   | `integer` | 否   |      | 装备位置<br />(-2则传入物品对象) |
| idx     | `integer` | 否   |      | 变量位置(1-20)                 |
| itemobj | `object`  | 是   |      | 物品对象(参数2传入-2时有效)    |
| result  | `string`  | 否   |      | 变量值                         |

#### 存储物品int变量[拓展]

`setitemintparam`

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                       |
| where   | `integer` | 否   |      | 装备位置<br />(-2则传入物品对象) |
| idx     | `integer` | 否   |      | 变量位置(1-50)                 |
| value   | `integer` | 否   |      | 变量值(Int64)                  |
| itemobj | `object`  | 是   |      | 物品对象(参数2传入-2时有效)    |

#### 获取物品int变量[拓展];

`getitemintparam`

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                       |
| where   | `integer` | 否   |      | 装备位置<br />(-2则传入物品对象) |
| idx     | `integer` | 否   |      | 变量位置(1-50)                 |
| itemobj | `object`  | 是   |      | 物品对象(参数2传入-2时有效)    |
| result  | `integer` | 否   |      | 变量值                         |

#### 更新物品变量到数据库[拓展]

`updatecustitemparam`

&gt; **若不使用该接口,则物品变量为临时变量,不会存储数据库也不会通知前端**

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                       |
| where   | `integer` | 否   |      | 装备位置<br />(-2则传入物品对象) |
| itemobj | `object`  | 是   |      | 物品对象(参数2传入-2时有效)    |

```lua
local itemobj = linkbodyitem(actor,1)

--存str变量
setitemparam(actor,1,1,"996ItemValue_1")
setcustitemparam(actor,-2,1,"996ItemValue_-2",itemobj)
--存int变量
setitemintparam(actor,1,1,"996ItemValue_1")
setitemintparam(actor,2,1,"996ItemValue_1")
local itemobj = linkbodyitem(actor,1)
setcustitemparam(actor,-2,1,"996ItemValue_-2",itemobj)

--更新变量
updatecustitemparam(actor,1)
local itemobj = linkbodyitem(actor,1)
updatecustitemparam(actor,-2,itemobj)
```

------------
## 怪物/NPC变量

#### 设置对象int变量

&gt; 临时变量,NPC重载后变量丢失

`setobjintvar`

| 参数  | 类型      | 空   | 默认 | 注释          |
| :---- | :-------- | :--- | :--- | :------------ |
| obj   | `object`  | 否   |      | 怪物/NPC对象  |
| idx   | `integer` | 否   |      | 变量位置(1-5)|
| value | `integer` | 否   |      | 变量值        |

#### 获取对象int变量

`getobjintvar`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| obj    | `object`  | 否   |      | 怪物/NPC对象  |
| idx    | `integer` | 否   |      | 变量位置(1-5)|
| result | `integer` | 否   |      | 变量值        |

```lua
    -- 给怪物对象设置变量
    local mapID,x,y = getMapXY(actor)
    local mons = getobjectinmap(mapID,x,y,10,2)
    for i, mon in ipairs(mons or {}) do
        setobjintvar(mon,1,996 + i)
    end

    -- 给NPC对象设置变量
    local npc = getnpcbyindex(10001)
    setobjintvar(npc,1,996)
    release_print("npc变量",i,getobjintvar(npc,1))
```

#### 设置对象str变量

&gt; **临时变量,不会存储数据库,重载NPC后变量丢失**

`setobjstrvar`

| 参数  | 类型      | 空   | 默认 | 注释          |
| :---- | :-------- | :--- | :--- | :------------ |
| obj   | `object`  | 否   |      | 怪物/NPC对象  |
| idx   | `integer` | 否   |      | 变量位置(1-5)|
| value | `string`  | 否   |      | 变量值        |

#### 获取对象str变量

`getobjstrvar`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| obj    | `object`  | 否   |      | 怪物/NPC对象  |
| idx    | `integer` | 否   |      | 变量位置(1-5)|
| result | `string`  | 否   |      | 变量值        |

```lua
    -- 给怪物对象设置变量
    local mapID,x,y = getMapXY(actor)
    local mons = getobjectinmap(mapID,x,y,10,2)
    for i, mon in ipairs(mons or {}) do
        setobjstrvar(mon,1,"996monValue_" .. i)
        release_print("怪物变量",i,getobjstrvar(mon,1))
    end

    -- 给NPC对象设置变量
    local npc = getnpcbyindex(10001)
    setobjstrvar(npc,1,"996npcValue")
    release_print("npc变量",i,getobjstrvar(npc,1))
```

------------
## 地图变量

&gt; **临时变量,不会存储数据库**

#### 设置地图int变量

`setenvirintvar`

| 参数  | 类型      | 空   | 默认 | 注释           |
| :---- | :-------- | :--- | :--- | :------------- |
| mapid | `string`  | 否   |      | 地图编号       |
| idx   | `integer` | 否   |      | 变量位置(1-50) |
| value | `integer` | 否   |      | 变量值         |

#### 获取地图int变量

`getenvirintvar`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| mapid  | `string`  | 否   |      | 地图编号       |
| idx    | `integer` | 否   |      | 变量位置(1-50) |
| result | `integer` | 否   |      | 变量值         |

#### 设置地图str变量

`setenvirstrvar`

| 参数  | 类型      | 空   | 默认 | 注释           |
| :---- | :-------- | :--- | :--- | :------------- |
| mapid | `string`  | 否   |      | 地图编号       |
| idx   | `integer` | 否   |      | 变量位置(1-50) |
| value | `string`  | 否   |      | 变量值         |

#### 获取地图str变量

`getenvirstrvar`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| mapid  | `string`  | 否   |      | 地图编号       |
| idx    | `integer` | 否   |      | 变量位置(1-50) |
| result | `string`  | 否   |      | 变量值         |
# 通用操作



### 解析文本
`parsetext`
- 可以直接替换传奇脚本里的标记符，可以获取对应的常量，如果say面板里有很多变量需要取，不想自己挨个取，可以直接调用此方法处理文本

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| text   | `string` | 否   |      | 文本内容 |
| object | `object` | 是   |      | 玩家对象 |

### 获取人物/怪物 相关信息

`getbaseinfo`

| 参数   | 类型      | 空   | 默认 | 注释                      |
| :----- | :-------- | :--- | :--- | :------------------------ |
| object | `object`  | 否   |      | 玩家/怪物 对象            |
| nID    | `integer` | 否   |      | 类型(详见说明)            |
| param3 | `integer` | 是   |      | 参数3<br />(仅ID=1/51时，可用) |
```lua
say(actor, "您的名字是："..getbaseinfo(actor,1))
```
- 说明
nID对应值分别为：
-1=是否玩家 (true:玩家)
0=是否死亡 (true:死亡状态)
1=对象名称 (返回值字符型)，当对象为怪物时，param3=0/nil，返回怪物显示名(即去除了尾部的数字)，param3=1时返回怪物默认名(怪物表中配置的名字)，param3=2时返回怪物实际名(游戏内实际展示的名字,新增于引擎64_23.08.30)
2=对象唯一ID ?(返回值字符型) = userid
3=对象当前地图ID (返回值字符型)
4=对象当前X坐标
5=对象当前Y坐标
6=对象当前等级
7=对象当前职业 (0-战 1-法 2-道)
8=对象当前性别
9=对象当前血量(HP)
10=对象当前血量上限(MAXHP)
11=对象当前蓝量(MP)
12=对象当前蓝量上限(MAXMP)
13=对象当前经验(Exp)
14=对象当前经验上限(MaxExp)
15=对象物防下限
16=对象物防上限
17=对象魔防下限
18=对象魔防上限
19=对象物攻下限
20=对象物攻上限
21=对象魔攻下限
22=对象魔攻上限
23=对象道攻下限
24=对象道攻上限
25=对象幸运值
26=对象HP恢复
27=对象MP恢复
28=对象中毒恢复
29=毒物躲避
30=对象魔法躲避
//31=对象准确(无法设置)
32=对象敏捷
33=发型
34=背包物品数量(仅人物)
35=队伍成员数量(仅人物)
36=行会名(仅人物)
37=是否会长(仅人物)
38=宠物数量
39=转生等级(仅人物)
40=杀怪经验倍数(仅人物)
41=杀怪经验时间(仅人物)
42=显示延时TIMERECALL还剩多少秒(仅人物)
43=人物杀怪爆率倍数(仅人物)
44=复活时间
45=地图名MAPTITLE
46=PK点
47=是否新人(仅人物)
48=是否安全区
49=是否摆摊中(仅人物)
50=是否交易中(仅人物)
51=对象att属性值，需要提供 参数3:属性ID(cfg_att_score.xls设置：1~129，200~249)**自定义属性在24.0807引擎拓展到200~399**
52=穿人/怪方式 0=恢复/1=穿人/2=穿怪/3=穿人穿怪
53=登录状态，0：正常，1：断线重连(仅人物)
54=主人UserId
55=Idx
56=颜色(0~255)
57=最后杀死的怪物Index(仅人物)
~~57=爆怪次数(等同之前 MonItems 功能)~~
58=时装显示状态(仅人物)
59=主人对象
60=是否在攻沙/攻城区域(bool)
61=是否为离线挂机状态(bool)
62=获取怪物表自定义常量(25列)
63=人物背包大小
64=获取对象当前的身体颜色值
65=获取对象的回城地图
67=获取对象的攻击对象
68=怪物归属对象
69=获取对象当前的方向(新增于引擎64_23.08.30)

### 设置人物/怪物相关信息
`setbaseinfo`

| 参数   | 类型      | 空   | 默认 | 注释             |
| :----- | :-------- | :--- | :--- | :--------------- |
| object | `object`  | 否   |      | 玩家/怪物 对象   |
| nID    | `integer` | 否   |      | 类型（详见说明） |
| value  | `integer` | 否   |      | 属性值           |
- 说明
nID对应值分别为：
6：设置等级
7: 职业
8: 性别
9: 当前HP
11: 当前MP
15=物防下限
16=物防上限
17=魔防下限
18=魔防上限
19=物攻下限
20=物攻上限
21=魔攻下限
22=魔攻上限
23=道攻下限
24=道攻上限
25=幸运值
26=HP恢复
27=MP恢复
28=中毒恢复
29=毒物躲避
30=魔法躲避
31=准确
32=敏捷
33: 发型
39：转生等级（仅人物）
40：杀怪经验倍数（仅人物）
41：杀怪经验时间（仅人物）
43：人物杀怪爆率倍数（仅人物）
46：人物PK点（仅人物）
50=行为方式，只针对宠物，包含多个行为时，求和（1：禁止攻击玩家，2：不可被攻击，4：优先攻击 玩家攻击对象，8：优先攻击 玩家受击对象，16：不可被玩家攻击，允许被怪攻击 ）
51=叛变（仅怪物）
52=穿人/怪方式 0=恢复/1=穿人/2=穿怪/3=穿人穿怪
56=颜色（0~255）
~~57=爆怪次数（等同之前 MonItems 功能）~~
57=设置时装显示状态(仅人物)
58=设置对象的身体颜色
67=设置对象的攻击对象，参数3为对象，空，0，为清空目标 （object为玩家时无效）
68=怪物归属对象(新增于引擎64_24.03.14)
69=设置对象当前的方向(新增于引擎64_24.03.14)

### 对象是否存在
`isnotnull`

| 参数   | 类型     | 空   | 默认 | 注释                                  |
| :----- | :------- | :--- | :--- | :------------------------------------ |
| object | `object` | 否   |      | 玩家/怪物 对象                        |
| result | `bool`   | 否   |      | 返回值<br />true：存在<br />false：不存在 |

### 判断对象是否为玩家
`isplayer`

&gt; **特殊:系统对象为0号玩家,所以也会返回true**

| 参数   | 类型     | 空   | 默认 | 注释                          |
| :----- | :------- | :--- | :--- | :---------------------------- |
| object | `object` | 否   |      | 判断对象                      |
| result | `bool`   | 否   |      | true=是玩家<br />false=不是玩家 |

### 判断对象是否为人形怪
`isplaymon`

| 参数   | 类型     | 空   | 默认 | 注释                              |
| :----- | :------- | :--- | :--- | :-------------------------------- |
| object | `object` | 否   |      | 判断对象                          |
| result | `bool`   | 否   |      | true=是人形怪<br />false=不是人形怪 |

### 判断对象是否为宝宝
`ismob`

| 参数   | 类型     | 空   | 默认 | 注释                          |
| :----- | :------- | :--- | :--- | :---------------------------- |
| object | `object` | 否   |      | 判断对象                      |
| result | `bool`   | 否   |      | true=是宝宝<br />false=不是宝宝 |

### 判断对象是否为怪物
`ismon`

| 参数   | 类型     | 空   | 默认 | 注释                          |
| :----- | :------- | :--- | :--- | :---------------------------- |
| object | `object` | 否   |      | 判断对象                      |
| result | `bool`   | 否   |      | true=是怪物<br />false=不是怪物 |

### 改变 人/怪物 状态

`makeposion`

| 参数   | 类型      | 空   | 默认                | 注释                                                                    |
| :----- | :-------- | :--- | :------------------ | :---------------------------------------------------------------------- |
| object | `object`  | 否   |                     | 玩家/怪物 对象                                                          |
| id     | `integer` | 否   |                     | 状态id(其他id无效)<br />0=绿毒;1=红毒<br />3=紫毒;5=麻痹<br />12=冰冻;13=蛛网 |
| time   | `integer` | 否   |                     | 时间(秒)                                                                |
| value  | `integer` | 是   |                     | 威力，只针对绿毒有用                                                    |
| model  | `integer` | 是   | 引擎64_23.08.30新增 | 0=不进行防护的判断<br />1=判断防全毒、防麻痹、防冰冻、防蛛网状态<br />只针对套装特殊属性,而非属性表中的属性          |
```lua
    --绿毒
    makeposion(mon, 0, 10, 10)
    --紫毒,需自己在buff表配置颜色
    makeposion(actor,3,10)
```

### 检测 人/怪物 状态

`checkhumanstate`

| 参数    | 类型      | 空   | 默认                | 注释                                                                                                                                                                                              |
| :------ | :-------- | :--- | :------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| object  | `object`  | 否   |                     | 玩家/怪物 对象                                                                                                                                                                                    |
| type    | `integer` | 否   |                     | 类型:<br />1.魔法盾 <br />2.护体神盾 <br />3.无极真气 <br />4.幽灵盾 <br />5.神圣战甲术 <br />6.隐身术 <br />7.冰冻 <br />8.麻痹 <br />9.锁定 <br />10.蛛网 <br />11.中毒<br />12.禁止行为                                |
| param   | `integer` | 否   |                     | 参数2=11,传入毒类型<br />0=全毒;1=绿毒;2=红毒;<br />==============<br />参数2=12,传入禁止行为<br />1=禁止走<br />2=禁止跑<br />3=禁止攻击<br />4=禁止施法<br />5=禁止使用物品<br />6=禁止说话<br />7=禁止飞<br />8=锁血 |
| result1 | `bool`    | 否   |                     | 返回值1<br />true：存在<br />false：不存在                                                                                                                                                            |
| result2 | `integer` | 否   | 引擎64_23.08.30新增 | 返回值2<br />状态的剩余时间(禁止行为无法获取剩余时间)                                                                                                                                               |
```lua
local bool,endTime = checkhumanstate(actor,11,1)
if bool then
    release_print("绿毒剩余时间", endTime)
end

local config = {
    [1] = "禁止走",
    [2] = "禁止跑",
    [3] = "禁止攻击",
    [4] = "禁止施法",
    [5] = "禁止使用物品",
    [6] = "禁止说话",
    [7] = "禁止飞",
    [8] = "锁血",
}
for i, state in ipairs(config) do
    --获取禁止行为,新增于引擎64_24.03.14,且只有一个返回值,无法获取剩余时间
    local bool = checkhumanstate(actor,12,i)
    LOGPrint("检测角色的禁止行为",bool,state)
end
```

### 使用脚本命令解毒（红绿毒）
`detoxifcation`

| 参数   | 类型      | 空   | 默认 | 注释                                                   |
| :----- | :-------- | :--- | :--- | :----------------------------------------------------- |
| object | `object`  | 否   |      | 玩家/怪物 对象                                         |
| opt    | `integer` | 否   |      | -1，解所有毒;0,绿毒;1,红毒;3,紫毒;5,麻痹;6,冰冻;7,蛛网 |

### 回到最近经过的城市安全区
`gohome`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 在线泡点经验
`setautogetexp`

| 参数       | 类型      | 空   | 默认 | 注释                                            |
| :--------- | :-------- | :--- | :--- | :---------------------------------------------- |
| play       | `object`  | 否   |      | 玩家对象                                        |
| evetime    | `integer` | 否   |      | 时间                                            |
| experience | `integer` | 否   |      | 经验                                            |
| isSafe     | `integer` | 否   |      | 是否安全区<br />(0为任何地方)                     |
| mapid      | `string`  | 否   |      | 地图号（任何地图使用`"*"`）                     |
| opt        | `integer` | 否   |      | 聚灵珠是否能获取经验<br />(0=不可以 1= 可以)      |
| alltime    | `integer` | 否   |      | 泡点获得经验的时间<br />时间：秒<br />上限2100000秒 |
| level      | `integer` | 否   |      | 等级(多少级以下获得经验)                        |
```lua
    --地图3安全区内每1秒种得到10个经验点 泡经验时间为60秒 100级以下才可以泡经验
    setautogetexp(actor,1,10,1,"3",1,60,100)
```

### 播放音乐声音
`playsound`

| 参数  | 类型      | 空   | 默认 | 注释                                                                              |
| :---- | :-------- | :--- | :--- | :-------------------------------------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                                                          |
| index | `integer` | 否   |      | 播放文件的索引<br />对应声音配置表id(cfg_sound.xls)                                 |
| times | `integer` | 否   |      | 循环播放次数                                                                      |
| flag  | `integer` | 否   |      | 播放模式:<br />0.播放给自己<br />1.播放给全服<br />2.播放给同一地图<br />4.播放给同屏人物 |

### 停止执行
`stop`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

```
stop可以停止执行相应的操作：
canopenbox, stdmodefunc, updateguildnotice, getexp,triggerchat, magselffunc(合击技能)

案例：
function stdmodefunc10(actor, item)
    if gethumability(actor, 20) = 0 then
        stop(actor)
    else
        changemoney(actor, 7, "+", 10000, "10000元宝", true)
    end
end
```
---

###~~cJson库~~
使用 tbl2json 与 json2tbl代替

### 表格转换成字符串
`tbl2json`
```lua
    local cfg = {"a","b","c"}
    local str = tbl2json(cfg)
```

### 字符串转换成表格
`json2tbl`
```lua
    local cfg = json2tbl(str)
    for k, v in ipairs(cfg) do
        release_print(k,v)
    end
```

---

### sqlite库
sqlite3.dll文件下载 [Mir200.rar](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=9c3082ef89f7f144dffe2dee2cbf0513 "[Mir200.rar")
```lua
[[引擎默认加载sqlite库,请先确认 MirServer\Mir200\clibs\luasql 路径有 sqlite3.dll 文件]]
function main(self)
    local env = sqlite3.sqlite3()
    local db = env:connect("db.sqlite")
    db:execute([[
      CREATE TABLE task(
        "id" INTEGER,
        "key" TEXT,
        "value" TEXT
      )
    ]])
    db:execute([[INSERT INTO task values("1", "任务名字1", "任务内容1")]])
    db:execute([[INSERT INTO task values("2", "任务名字2", "任务内容2")]])
    local results = db:execute([[SELECT * from task]])
    local key, value, value2 = results:fetch()
    while key do
      release_print(key ..': '.. value .."|"..tostring(value2))
      key, value, value2 = results:fetch()
    end
    results:close()
    db:close()
    env:close()
end
```

---

### iconv库

iconv.dll文件下载 [Mir200.rar](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=9c3082ef89f7f144dffe2dee2cbf0513 "[Mir200.rar")

```lua
[[引擎默认加载iconv库,请先确认 MirServer\Mir200\clibs 路径有 iconv.dll 文件]]
local toutf8 = iconv.new("UTF-8", "GBK")
function GBK2UTF8(str)
    local s, err = toutf8:iconv(str)
    if err then
        release_print("err:"..tostring(err))
        return str
    end
    return s
end
local togbk = iconv.new("GBK", "UTF-8")
function UTF82GBK(str)
    local s, err = togbk:iconv(str)
    if err then
        release_print("err:"..tostring(err))
        return str
    end
    return s
end
```

---

### 拉取客户端充值接口
`pullpay`

| 参数   | 类型      | 空   | 默认 | 注释                                           |
| :----- | :-------- | :--- | :--- | :--------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                       |
| money  | `integer` | 否   |      | 金额                                           |
| type   | `integer` | 否   |      | 充值方式：<br />1-支付宝，<br />2-花呗，<br />3-微信 |
| flagid | `integer` | 否   |      | 充值货币ID                                     |
```
比如:你后台配置的flagid为  1:10元宝，对应的ID为2，那么下面的拉起充值填写flagid 必须为2
```

### 执行GM命令
`gmexecute`

| 参数    | 类型     | 空   | 默认 | 注释         |
| :------ | :------- | :--- | :--- | :----------- |
| player  | `object` | 否   |      | 玩家对象     |
| GM      | `string` | 否   |      | GM命令       |
| parma1  | `string` | 否   |      | GM命令参数1  |
| parma2  | `string` | 否   |      | GM命令参数2  |
| parma3  | `string` | 否   |      | GM命令参数3  |
| parma4  | `string` | 否   |      | GM命令参数4  |
| parma5  | `string` | 否   |      | GM命令参数5  |
| parma6  | `string` | 否   |      | GM命令参数6  |
| parma7  | `string` | 否   |      | GM命令参数7  |
| parma8  | `string` | 否   |      | GM命令参数8  |
| parma9  | `string` | 否   |      | GM命令参数9  |
| parma10 | `string` | 否   |      | GM命令参数10 |

### 播放屏幕特效
`screffects`

| 参数     | 类型      | 空   | 默认 | 注释                           |
| :------- | :-------- | :--- | :--- | :----------------------------- |
| player   | `object`  | 否   |      | 玩家对象                       |
| id       | `integer` | 否   |      | 创建的特效编号                 |
| effectid | `integer` | 否   |      | 特效ID                         |
| X        | `integer` | 否   |      | 在屏幕上的X坐标                |
| Y        | `integer` | 否   |      | 在屏幕上的Y坐标                |
| speed    | `integer` | 否   |      | 播放速度                       |
| times    | `integer` | 否   |      | 播放次数，0-持续播放           |
| type     | `integer` | 否   |      | 播放模式<br />0-自己<br />1-所有人 |

### 关闭屏幕特效
`deleffects`

| 参数   | 类型      | 空   | 默认 | 注释                           |
| :----- | :-------- | :--- | :--- | :----------------------------- |
| player | `object`  | 否   |      | 玩家对象                       |
| id     | `integer` | 否   |      | 创建的特效编号                 |
| type   | `integer` | 否   |      | 播放模式<br />0-自己<br />1-所有人 |

### 获取常量
`getconst`

| 参数    | 类型     | 空   | 默认 | 注释                                                 |
| :------ | :------- | :--- | :--- | :--------------------------------------------------- |
| player  | `object` | 否   |      | 玩家对象                                             |
| varname | `string` | 否   |      | 常量名称，支持带尖括号和不带尖括号<br />&lt;$Name&gt;或$Name |
| result  | `string` | 否   |      | 常量值                                               |

### 屏幕震动
`scenevibration`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                      |
| :----- | :-------- | :--- | :--- | :-------------------------------------------------------------------------------------------------------- |
| player | `object`  | 否   |      | 玩家对象                                                                                                  |
| type   | `integer` | 否   |      | 模式(0~4)<br />0.仅自己;<br />1.在线所有人;<br />2屏幕范围内人物;<br />3.当前地图上所有人;<br />4.指定地图上所有人; |
| level  | `integer` | 否   |      | 震级(1~3)                                                                                                 |
| num    | `integer` | 否   |      | 次数                                                                                                      |
| mapid  | `string`  | 是   |      | 地图ID(模式等于4时，需要该参数)                                                                           |
```
scenevibration(actor,0,1,1)
```

### 客户端复制
`mircopy`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| player | `object` | 否   |      | 玩家对象 |
| string | `string` | 否   |      | 文本内容 |

### 游戏中打开网站
`openwebsite`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| player | `object` | 否   |      | 玩家对象 |
| web    | `string` | 否   |      | 网站     |

### MD5加密
`md5str`

| 参数   | 类型     | 空   | 默认 | 注释           |
| :----- | :------- | :--- | :--- | :------------- |
| str    | `string` | 否   |      | 需要加密的文本 |
| result | `string` | 是   | 0    | MD5加密值      |

### 等概率或者按权限随机获取分割字符串

`ransjstr`

| 参数    | 类型      | 空   | 默认 | 注释                                                                                                               |
| :------ | :-------- | :--- | :--- | :----------------------------------------------------------------------------------------------------------------- |
| str     | `string`  | 否   |      | 需要获取随机的字符串                                                                                               |
| param1  | `integer` | 否   |      | 0=系统权重随机,有几个字符串就是几份之一<br />1=按#位权重随机总权重为各项位权重的总和                                 |
| param2  | `integer` | 否   |      | 0=返回值都显示#权重数字<br />1=返回值都不显示#权重数字<br />2=返回值1显示,返回值2不显示<br />3=返回值2显示,返回值1不显示 |
| result1 | `srtring` | 否   |      | 随机到的字符串                                                                                                     |
| result2 | `srtring` | 否   |      | 剩余的字符串                                                                                                       |

```lua
local result1, result2 = ransjstr("测试1#2000|测试2#10000|测试3#5000", 1, 3)
release_print("result1", result1, ", result2", result2)
```

### 自定义日志

- 说明: 配置自定义日志对应后台查看

`logact`

| 参数    | 类型      | 空   | 默认 | 注释                         |
| :------ | :-------- | :--- | :--- | :--------------------------- |
| play    | `object`  | 否   |      | 玩家对象                     |
| logAct  | `integer` | 否   |      | 日志ID<br />大于等于10000以上  |
| loginfo | `string`  | 否   |      | 日志内容<br />支持变量,常量等  |
| nParam1 | `integer` | 否   |      | 整数型(可空)<br />最大支持21亿 |
| nParam2 | `integer` | 否   |      | 整数型(可空)<br />最大支持21亿 |
| nParam3 | `integer` | 否   |      | 整数型(可空)<br />最大支持21亿 |
| nParam4 | `integer` | 否   |      | 整数型(可空)<br />最大支持21亿 |
| nParam5 | `integer` | 否   |      | 整数型(可空)<br />最大支持21亿 |

```lua
logact(actor,10001,"玩家：&lt;$username&gt;通过日志测试扣除100元宝获得屠龙*1",1,2,3,4,5)
```
![后台上传表格格式](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=41626a76cfe8f49ab0a80f948b891ea8)

### 日志上报接口

`senddiymsg`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数    | 类型     | 空   | 默认 | 注释                                                               |
| :------ | :------- | :--- | :--- | :----------------------------------------------------------------- |
| play    | `object` | 否   |      | 玩家对象                                                           |
| jsonStr | `string` | 否   |      | 日志json[[详情]](http://engine-doc.996m2.com/web/#/44/7489 "详情") |

### 打印脚本总耗时(微秒)

- 需要角色游戏权限为10,且需退出管理员模式(GM命令)

`printusetime`

| 参数   | 类型      | 空   | 默认 | 注释                                     |
| :----- | :-------- | :--- | :--- | :--------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                 |
| on/off | `integer` | 否   |      | 1=开始计时<br />2=结束计时，并打印耗时信息 |

```lua
printusetime(actor,1)
for i = 1, 100, 1 do
    release_print("打印耗时",i)
end
printusetime(actor,2)
```

### 前端勾选面板控制命令

`clientswitch`

| 参数 | 类型      | 空   | 默认 | 注释                                                                                         |
| :--- | :-------- | :--- | :--- | :------------------------------------------------------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                                                                     |
| type | `integer` | 否   |      | 0=允许组队<br />1=允许添加好友<br />2允许交易<br />3=允许挑战<br />4允许查看<br />5=允许添加为行会成员 |
| time | `integer` | 否   |      | 1=允许(勾选)<br />0=不允许(不勾选)(秒)                                                         |

```lua
for i = 0, 5 do
    clientswitch(actor,i,1)
end
```

### 拉起微信和qq等功能

`sendforqqwx`

| 参数   | 类型      | 空   | 默认 | 注释                                     |
| :----- | :-------- | :--- | :--- | :--------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                 |
| model  | `integer` | 否   |      | 1=拉起QQ<br />2=QQ好友<br />3=QQ群<br />4=微信 |
| param1 | `integer` | 否   |      | 参数2=2,填入QQ号<br />参数2=3,填入QQ群号   |
| param2 | `string`  | 否   |      | 参数2=3,填入QQ群key                      |
```lua
--拉起QQ
sendforqqwx(actor,1)

--拉起QQ好友
sendforqqwx(actor,2,2881xxxx84)

--拉起QQ群,参数3为qq群号,参数4位qq群key(KEY获取地址： https://qun.qq.com/join.html)
sendforqqwx(actor,3,2881xxxx84,"https://qm.qq.com/cgi-bin/qm/qr?k=W_xxxx&amp;jump_from=webapi&amp;authKey=xxxx")

--拉起微信
sendforqqwx(actor,4)
```


# 引用文件



### 加载文件
`include`/`require`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|path     |`string`      |否   |    |   文件名<br>两种加载接口起始路径不同 |
`QManage.lua`
```lua
ssrNetMsgCfg = include("QuestDiary/net/NetMsgCfg.lua")
ssrNetMsgCfg = require("Envir/QuestDiary/net/NetMsgCfg.lua")
function login(actor)
    --vip
    release_print("main_VipLevelResponse",ssrNetMsgCfg.main_VipLevelResponse)
end
```

`Envir/QuestDiary/net/NetMsgCfg.lua`

```lua
local ssrNetMsgCfg = {
    init        = 10,
    main                                = "main",
    main_VipLevelResponse               = 100,                      --vip等级
}

return ssrNetMsgCfg
```
# 人物相关操作



## 人物属性

### 修改人物名称

`changehumname`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                               |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                                                                           |
| name   | `string`  | 否   |      | 要查询的名字                                                                                       |
| result | `integer` |      |      | 执行结果：<br />0-改名成功<br />1、2、6-名称被过滤<br />3-名字已经存在<br />5-长度不符合要求<br />7-改名失败 |
```lua
1. 会先执行查询人物名称操作，并触发：queryinghumname;
2. 会根据查询结果情况触发：humnamefilter（名称被过滤）、namelengthfail（长度不符合要求）、humnameexists（名称已经存在）;
3. 执行改名操作前触发：changeinghumname，根据改名结果触发：changehumnameok(改名成功)、changehumnamefail(改名失败)。
	
--正在查询玩家名称
function queryinghumname(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;正在查询请稍后。。。&lt;/font&gt;","Type":9}')
end

--名称被过滤
function humnamefilter(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;名称被过滤。。。&lt;/font&gt;","Type":9}')
end

--长度不符合要求
function namelengthfail(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;长度不符合要求&lt;/font&gt;","Type":9}')
end

--名称已经存在
function humnameexists(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;名称已经存在&lt;/font&gt;","Type":9}')
end

--正在执行改名操作
function changeinghumname(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;正在修改请稍后。。。&lt;/font&gt;","Type":9}')
end

--改名成功
function changehumnameok(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;'..parsetext("你的名字修改成功，旧名称：&lt;$USERNAME&gt; 新名称：&lt;$USERNEWNAME&gt;！",actor)..'&lt;/font&gt;","Type":9}')
end

--改名失败
function changehumnamefail(actor)
    sendmsg(actor, 1, '{"Msg":"&lt;font color=\'#ff0000\'&gt;修改名称失败&lt;/font&gt;","Type":9}')
end
```

### 修改人物名字颜色
`changenamecolor`

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| play  | `object`  | 否   |      | 玩家对象 |
| color | `integer` | 否   |      | 颜色索引 |

### 刷新人物属性
`recalcabilitys`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 获取人物属性
`gethumability`

| 参数   | 类型      | 空   | 默认 | 注释                 |
| :----- | :-------- | :--- | :--- | :------------------- |
| play   | `object`  | 否   |      | 玩家对象             |
| id     | `integer` | 否   |      | 属性ID（1-20）       |
| result | `integer` | 否   |      | 返回值，对应的属性值 |

### 调整人物属性
`changehumability`

| 参数  | 类型      | 空   | 默认 | 注释           |
| :---- | :-------- | :--- | :--- | :------------- |
| play  | `object`  | 否   |      | 玩家对象       |
| id    | `integer` | 否   |      | 属性ID（1-20） |
| value | `integer` | 否   |      | 属性值         |
| time  | `integer` | 否   |      | 时间(秒)       |
* 属性ID
1=防御下限 
2=防御上限 
3=魔御下限 
4=魔御上限 
5=攻击下限 
6=攻击上限 
7=魔法下限 
8=魔法上限
9=道术下限 
10=道术上限 
11=MaxHP 
12=MaxMP 
13=HP恢复 
14=MP恢复
15=毒恢复 
16=毒躲避 
17=魔法躲避 
18=准确 
19=敏捷 
20= 幸运

### 修改人物临时属性（带有效期）
`changehumnewvalue`

| 参数   | 类型      | 空   | 默认 | 注释                          |
| :----- | :-------- | :--- | :--- | :---------------------------- |
| play   | `object`  | 否   |      | 玩家对象                      |
| nWhere | `integer` | 否   |      | 位置 对应cfg_att_score 属性ID |
| nValue | `integer` | 否   |      | 对应属性值                    |
| nTime  | `integer` | 否   |      | 有效时间，秒                  |

```lua
function main(self)
    changehumnewvalue(self,10,10,10)
end
```

### 获取人物临时属性
`gethumnewvalue`

| 参数   | 类型      | 空   | 默认 | 注释                          |
| :----- | :-------- | :--- | :--- | :---------------------------- |
| play   | `object`  | 否   |      | 玩家对象                      |
| nWhere | `integer` | 否   |      | 位置 对应cfg_att_score 属性ID |
| result | `integer` | 否   |      | 对应属性值                    |

### 获取人物永久属性
`getusebonuspoint`

| 参数   | 类型      | 空   | 默认 | 注释       |
| :----- | :-------- | :--- | :--- | :--------- |
| play   | `object`  | 否   |      | 玩家对象   |
| nIndex | `integer` | 否   |      | 索引       |
| result | `integer` | 否   |      | 对应属性值 |

### 设置人物永久属性
`setusebonuspoint`

| 参数   | 类型      | 空   | 默认 | 注释       |
| :----- | :-------- | :--- | :--- | :--------- |
| play   | `object`  | 否   |      | 玩家对象   |
| nIndex | `integer` | 否   |      | 索引       |
| nvalue | `integer` | 否   |      | 对应属性值 |

nIndex 取值
1：攻击下限（0~65535）
2：攻击上限（0~65535）
3：魔法下限（0~65535）
4：魔法上限（0~65535）
5：道术下限（0~65535）
6：道术上限（0~65535）
7：防御下限（0~65535）
8：防御上限（0~65535）
9：魔防下限（0~65535）
10：魔防上限（0~65535）
11：生命值（支持21亿）
12：魔法值（支持21亿）
13：准确（支持21亿）
14：躲避（支持21亿）
15：防御下限（支持21亿）
16：防御上限（支持21亿）
17：魔防下限（支持21亿）
18：魔防上限（支持21亿）

------------

### 通过字符串增加对应属性值(参照cfg_equip.xls属性字段)

`addattlist`

| 参数    | 类型      | 空   | 默认 | 注释                                                                                                     |
| :------ | :-------- | :--- | :--- | :------------------------------------------------------------------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                                                                                 |
| attridx | `string`  | 否   |      | 自定义属性组名称                                                                                         |
| opt     | `string`  | 否   |      | 操作符 +、-、=                                                                                           |
| attrStr | `string`  | 否   |      | 属性字符串                                                                                               |
| type    | `integer` | 是   | 0    | 0=计算套装属性增加;<br />1=增加固定值;不计算套装属性(属性加成类无效)<br />2=全部属性计算完后<br />最后增加属性 |

```lua
    --加属性
    addattlist(actor,"属性组1","+","3#1#100|3#2#100|3#3#10|3#4#10")
```

### 获取字符串属性

`getattlist`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**
 

| 参数    | 类型     | 空   | 默认 | 注释             |
| :------ | :------- | :--- | :--- | :--------------- |
| play    | `object` | 否   |      | 玩家对象         |
| attridx | `string` | 否   |      | 自定义属性组名称 |
| result  | `string` | 否   |      | 属性字符串       |
```lua
    local attr_str = getattlist(actor,"自定义属性组1")
    release_print("attr_str",attr_str)
```

### 清除字符串属性
`delattlist`

| 参数    | 类型     | 空   | 默认 | 注释             |
| :------ | :------- | :--- | :--- | :--------------- |
| play    | `object` | 否   |      | 玩家对象         |
| attridx | `string` | 否   |      | 自定义属性组名称 |

```lua
    --删属性
    delattlist(actor,"属性组1")
```

------------

### 设置装备部位属性加成(万分比)

 `setequipaddvalue`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**
 
| 参数  | 类型      | 空   | 默认 | 注释          |
| :---- | :-------- | :--- | :--- | :------------ |
| play  | `object`  | 否   |      | 玩家对象      |
| where | `integer` | 否   |      | 装备部位      |
| sFlag | `string`  | 否   |      | 操作符(=,+,-) |
| pro   | `integer` | 是   |      | 倍数(万分比)  |
```lua
setequipaddvalue(actor,1 ,"+", 15000)
say(actor,"武器部位的属性加成".. getequipaddvalue(actor,1))
```

### 获取装备部位属性加成(万分比)

 `getequipaddvalue`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**
 
| 参数   | 类型      | 空   | 默认 | 注释         |
| :----- | :-------- | :--- | :--- | :----------- |
| play   | `object`  | 否   |      | 玩家对象     |
| where  | `integer` | 否   |      | 装备部位     |
| result | `bool`    | 是   |      | 倍数(万分比) |

------------

### 设置人物经验值
`changeexp`

| 参数   | 类型      | 空   | 默认 | 注释               |
| :----- | :-------- | :--- | :--- | :----------------- |
| play   | `object`  | 否   |      | 玩家对象           |
| opt    | `char`    | 否   |      | 操作符 + - =       |
| count  | `integer` | 否   |      | 数量               |
| addexp | `bool`    | 否   |      | 是否增加聚灵珠经验 |

### 调整人物等级
`changelevel`

| 参数  | 类型      | 空   | 默认 | 注释         |
| :---- | :-------- | :--- | :--- | :----------- |
| play  | `object`  | 否   |      | 玩家对象     |
| opt   | `char`    | 否   |      | 操作符 + - = |
| count | `integer` | 否   |      | 数量         |

### 设置等级锁

`setlocklevel`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                                                                       |
| :---- | :-------- | :--- | :--- | :----------------------------------------------------------------------------------------- |
| actor | `object`  | 否   |      | 玩家对象                                                                                   |
| itype | `integer` | 否   |      | 0:解除锁定<br />1锁定到达最大等级时并且不获取怪物经验<br />2:锁定到达最大等级时累积经验(int64) |
| level | `integer` | 否   |      | 锁住最大等级                                                                               |
```lua
[[
    特殊*：设置等级锁后 ,changeexp 仍然可以加经验, setbaseinfo 仍然可以突破等级限制
    特殊*：重进游戏需要重新设置
]]
    setlocklevel(actor,1,99)
```

------------

### 改变人物模式

`changemode`

| 参数   | 类型      | 空   | 默认 | 注释                                           |
| :----- | :-------- | :--- | :--- | :--------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                       |
| mode   | `integer` | 否   |      | 模式1~24                                       |
| time   | `integer` | 否   |      | 状态时间(秒,1-65535)                           |
| param1 | `integer` | 否   |      | 参数1,12,13,18,20,21代表几率<br />其余代表属性值 |
| param2 | `integer` | 否   |      | 参数2                                          |

- 具体参考脚本命令说明
//说明: 1=无敌 2=隐身 3=HP 4=MP 5=攻击力 6=魔法力 7=道术力 8=攻击速度 9=禁止攻击 10=锁定
//如果是禁锢时，第三个参数表示禁锢范围
//11 禁锢[释放一个类似困魔咒的光圈，敌对人物只能在这个圈子里移动，无法走出圈子外面，所有传送失效，不能小退] param1:禁锢范围 param2:1表示不禁锢自己;2表示禁锢自己;0或空按之前的
//12 冰冻[设置后可以使攻击目标冰冻] param1:几率 param2:冰冻时间(秒)
//13 蛛网[设置后可以使攻击目标中蛛网] param1:几率 param2:蛛网时间(秒)
//14 防麻痹
//15 防禁锢
//16 防冰冻
//17 防蛛网
//18 麻痹[设置后可以使攻击目标麻痹]param1:几率 param2:麻痹时间(秒)
//19 护身 param1:掉蓝比例 param2:伤害吸收(设置数值除以100)
//20 吸血 param1:吸血几率(百分比) param2:吸血点数(万分比)
//21 吸蓝 param1:吸蓝几率(百分比) param2:吸蓝点数(万分比)
//22 隐身(类似隐身戒指)
//23 复活
//24 破复活

```lua
    --角色无敌，无敌时长60秒
    changemode(actor, 1, 60)

    --禁锢自身10秒,范围3格
    changemode(actor,11, 10, 3, 0)

    --禁锢自身10秒,范围3格(禁锢的是他人，没有禁锢自己)
    changemode(actor,11, 10, 3, 1)

    --可以使目标冰冻，冰冻机率1/100(数字越大机率越低)，冰冻时长3秒 
    changemode(actor,12,100,1,3)

    --可以使目标中蛛网，中网机率1/10(数字越大机率越低)，蛛网时长3秒 
    changemode(actor,13,10,1,3)

    --10秒内可以防麻痹
    changemode(actor,14,10)

    --可以使目标麻痹，麻痹机率1/1(数字越大机率越低)，麻痹时长3秒
    changemode(actor,18,1,1,3)

    --10秒内攻击目标，可以吸血，吸血机率100(数字越大机率越高 100表示每次都会吸血)，5000代表吸血百分比50%(比如攻击伤害值是10000，50%的吸血比例，可以吸血5000) 
    changemode(actor,20,10,100, 5000)
```

------------

### 顶戴花翎
`seticon`

| 参数     | 类型      | 空   | 默认               | 注释                                                    |
| :------- | :-------- | :--- | :----------------- | :------------------------------------------------------ |
| play     | `object`  | 否   |                    | 玩家对象                                                |
| where    | `integer` | 否   |                    | 位置 0-9                                                |
| effType  | `integer` | 否   |                    | 播放效果<br />0 = 图片名称<br />1 = 特效ID<br />-1 = 取消顶戴 |
| resName  | `string`  | 否   |                    | 图片名或者特效ID                                        |
| x        | `integer` | 否   |                    | X坐标 (为空时默认X=0)                                   |
| y        | `integer` | 否   |                    | Y坐标 (为空时默认Y=0)                                   |
| autoDrop | `integer` | 否   |                    | 自动补全空白位置0,1(0=掉 1=不掉)                        |
| selfSee  | `integer` | 否   |                    | 是否只有自己看见<br />0=所有人都可见;<br />1=仅仅自己可见;  |
| posM     | `integer` | 否   | 引擎64_23.0628新增 | 播放位置(不填默认为0)<br />0=在角色之上;<br />1=在角色之下; |
```lua
 --添加顶戴效果
 seticon(actor, 0, 1, 200, -30, 100, 0, 0, 1)

 --移除顶戴效果
 seticon(actor, 0, -1)
```

### 在人物身上播放特效
`playeffect`

| 参数     | 类型      | 空   | 默认 | 注释                                       |
| :------- | :-------- | :--- | :--- | :----------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                   |
| effectid | `integer` | 否   |      | 特效ID                                     |
| offsetX  | `integer` | 否   |      | 相对于人物偏移的X坐标                      |
| offsetY  | `integer` | 否   |      | 相对于人物偏移的Y坐标                      |
| times    | `integer` | 否   |      | 播放次数<br />0-一直播放                     |
| behind   | `integer` | 否   |      | 播放模式<br />0-前面<br />1-后面               |
| selfshow | `integer` | 否   |      | 仅自己可见<br />0-否，视野内均可见，<br />1-是 |

### 清除人物身上播放的特效
`clearplayeffect`

| 参数     | 类型      | 空   | 默认 | 注释     |
| :------- | :-------- | :--- | :--- | :------- |
| play     | `object`  | 否   |      | 玩家对象 |
| effectid | `integer` | 否   |      | 特效ID   |

```
注：已经指定播放数量的特效，不能用此命令清除
```

------------

### 修改人物当前血量

`humanhp`

| 参数    | 类型      | 空   | 默认                          | 注释                                                                |
| :------ | :-------- | :--- | :---------------------------- | :------------------------------------------------------------------ |
| play    | `object`  | 否   |                               | 玩家(怪物)对象                                                      |
| operate | `string`  | 否   |                               | 操作符号<br />"+" 增加<br />"-" 减少<br />"=" 等于                        |
| nvalue  | `integer` | 否   |                               | HP点数                                                              |
| effid   | `integer` | 否   |                               | 素材ID                                                              |
| delay   | `integer` | 否   | 引擎64_23.03.23后<br />支持小数 | 延时时间(秒)                                                        |
| hiter   | `object`  | 是   | 引擎64_23.06.28新增           | 伤害来源对象                                                        |
| isSend  | `integer` | 是   | 引擎64_23.10.24新增           | 释放广播飘血<br />0/nil=不广播<br />1=广播                              |
| isRob   | `integer` | 是   | 引擎64_24.03.14新增           | 是否强制修改归属<br />0/nil=强制修改归属;<br />1=已有归属的情况不抢归属 |
```
    参数4[素材ID] effid = cfg_damage_number表中的ID编号，ID可自行增加和配置
```

### 修改人物当前MP

`humanmp`

| 参数    | 类型      | 空   | 默认 | 注释                                         |
| :------ | :-------- | :--- | :--- | :------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                     |
| operate | `string`  | 否   |      | 操作符号<br />'+'-增加<br />'-'-减少<br />'='-等于 |
| nvalue  | `integer` | 否   |      | MP点数                                       |

### 调整HP(血量)的百分比

`addhpper`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| player | `object`  | 否   |      | 玩家(怪物)对象 |
| opt    | `string`  | 否   |      | 控制符(=,+,-)  |
| value  | `integer` | 否   |      | 数值           |

### 调整MP(蓝量)的百分比

`addmpper`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| player | `object`  | 否   |      | 玩家对象      |
| opt    | `string`  | 否   |      | 控制符(=,+,-) |
| value  | `integer` | 否   |      | 数值          |

### 设置人物伤害吸收
`setsuckdamage`

| 参数    | 类型      | 空   | 默认 | 注释                                         |
| :------ | :-------- | :--- | :--- | :------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                     |
| operate | `string`  | 否   |      | 操作符号<br />'+'-增加<br />'-'-减少<br />'='-等于 |
| sum     | `integer` | 否   |      | 总吸收量                                     |
| rate    | `integer` | 否   |      | 吸收比率，千分比<br />1=0.1%，100=10%          |
| success | `integer` | 否   |      | 吸收成功率                                   |

### 获取人物伤害吸收
`getsuckdamage`

| 参数   | 类型      | 空   | 默认 | 注释       |
| :----- | :-------- | :--- | :--- | :--------- |
| play   | `object`  | 否   |      | 玩家对象   |
| result | `integer` | 否   |      | 伤害吸收值 |
```lua
    setsuckdamage(actor,"=",1000,200,95)
    local damage = getsuckdamage(actor)
    release_print("伤害吸收值",damage)
```

------------

### 人物变色
`setbodycolor`

| 参数  | 类型      | 空   | 默认 | 注释                                                                     |
| :---- | :-------- | :--- | :--- | :----------------------------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                                                 |
| color | `integer` | 否   |      | 颜色(0~255); 255时清除颜色;     -1则为转生设置的颜色在人物身体上进行变色 |
| time  | `integer` | 否   |      | 改变时长(秒)                                                             |

### 播放光环效果
`mobfireburn`

| 参数     | 类型      | 空   | 默认 | 注释                                                         |
| :------- | :-------- | :--- | :--- | :----------------------------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                                     |
| mapid    | `string`  | 否   |      | 地图id                                                       |
| x        | `integer` | 否   |      | 坐标x                                                        |
| y        | `integer` | 否   |      | 坐标y                                                        |
| type     | `integer` | 否   |      | 光环类型<br />1=僵尸钻的地洞<br />3=碎石块<br />4=困魔光<br />5=火墙 |
| time     | `integer` | 否   |      | 时间（秒）                                                   |
| behind   | `integer` | 否   |      | 播放模式-0-前面-1-后面                                       |
| selfshow | `integer` | 否   |      | 仅自己可见0-否，视野内均可见，1-是                           |

------------

### 脚本设置防秒杀功能
`killedprotect`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |
```
说明：当前你血量100%的时候敌方第一刀伤害打掉你多少血量，如果你血量不是100%的时候防秒杀功能不生效
```

### 立即杀死角色
`kill`

| 参数      | 类型     | 空   | 默认 | 注释       |
| :-------- | :------- | :--- | :--- | :--------- |
| play      | `object` | 否   |      | 角色的对象 |
| strKiller | `object` | 否   |      | 凶手的对象 |

------------

## 人物货币

### 查询人物货币
`querymoney`

| 参数   | 类型      | 空   | 默认 | 注释            |
| :----- | :-------- | :--- | :--- | :-------------- |
| play   | `object`  | 否   |      | 玩家对象        |
| id     | `integer` | 否   |      | 货币ID（1-100） |
| result | `integer` | 否   |      | 对应货币值      |

### 设置人物货币
`changemoney`

| 参数   | 类型      | 空   | 默认 | 注释                        |
| :----- | :-------- | :--- | :--- | :-------------------------- |
| play   | `object`  | 否   |      | 玩家对象                    |
| id     | `integer` | 否   |      | 货币ID（1-100）             |
| opt    | `char`    | 否   |      | 操作符 + - =                |
| count  | `integer` | 否   |      | 数量                        |
| msg    | `string`  | 否   |      | 备注内容                    |
| send   | `bool`    | 否   |      | 是否推送到客户端，true-更新 |
| result | `bool`    | 否   |      | 是否成功                    |

### 获取人物通用货币数量(多货币计算)
`getbindmoney`

| 参数      | 类型      | 空   | 默认 | 注释       |
| :-------- | :-------- | :--- | :--- | :--------- |
| play      | `object`  | 否   |      | 玩家对象   |
| moneyname | `string`  | 否   |      | 货币名称   |
| result    | `integer` | 否   |      | 对应货币值 |

```
表：cfg_item.xls表，设置方法：Reserved字段 
货币组分类(数字)#优先扣除顺序，如：22#1 22#2 22#3
这3个货币是一个类别的，后面的1 2 3 代表扣除的顺序，数字越小越优先扣除。
```

### 扣除人物通用货币数量(多货币依次计算)

`consumebindmoney`

| 参数      | 类型      | 空   | 默认                | 注释       |
| :-------- | :-------- | :--- | :------------------ | :--------- |
| play      | `object`  | 否   |                     | 玩家对象   |
| moneyname | `string`  | 否   |                     | 货币名称   |
| count     | `integer` | 否   |                     | 对应货币值 |
| msg       | `string`  | 否   | 引擎64_23.08.30新增 | 备注内容   |
| result    | `bool`    | 否   | 引擎64_23.12.07新增 | 是否成功   |

------------

## 人物装备

### 设置人物背包格子数
`setbagcount`

| 参数  | 类型      | 空   | 默认 | 注释                                |
| :---- | :-------- | :--- | :--- | :---------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                            |
| count | `integer` | 否   |      | 格子大小<br />（不小于46，不大于126） |

### 获取背包剩余空格数
`getbagblank`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| result | `integer` | 否   |      | 背包剩余格子数 |

### 遍历背包勾选物品
`selectbagitems`

| 参数      | 类型     | 空   | 默认 | 注释                                  |
| :-------- | :------- | :--- | :--- | :------------------------------------ |
| play      | `object` | 否   |      | 玩家对象                              |
| makeindex | `string` | 否   |      | 选中的物品唯一ID<br />多个物品用“,”分隔 |

------------

### 穿戴装备
`takeonitem`

| 参数      | 类型      | 空   | 默认 | 注释       |
| :-------- | :-------- | :--- | :--- | :--------- |
| play      | `object`  | 否   |      | 玩家对象   |
| where     | `integer` | 否   |      | 位置       |
| makeindex | `integer` | 否   |      | 物品唯一ID |

### 脱下装备
`takeoffitem`

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| play  | `object`  | 否   |      | 玩家对象 |
| where | `integer` | 否   |      | 位置     |

------------

### 开/关首饰盒
`setsndaitembox`

| 参数   | 类型      | 空   | 默认 | 注释             |
| :----- | :-------- | :--- | :--- | :--------------- |
| play   | `object`  | 否   |      | 玩家对象         |
| bState | `integer` | 否   |      | 0：关闭，1：开启 |

### 修改武器、衣服外观

`changeitemshape`

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| play  | `object`  | 否   |      | 玩家对象 |
| item  | `object`  | 否   |      | 物品对象 |
| looks | `integer` | 否   |      | 外观值   |

### 修改武器、衣服特效
`changedresseffect`

| 参数    | 类型      | 空   | 默认 | 注释                                            |
| :------ | :-------- | :--- | :--- | :---------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                        |
| where   | `integer` | 否   |      | 位置 0，1                                       |
| EffId   | `integer` | 否   |      | 特效ID                                          |
| selfSee | `integer` | 否   |      | 是否只有自己看见(1=所有人都可见 0=仅仅自己可见) |

### 修改角色外观(武器、衣服、特效)

`setfeature`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                            |
| :----- | :-------- | :--- | :--- | :-------------------------------------------------------------------------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                                                                                        |
| type   | `integer` | 否   |      | 0=衣服;1=武器;<br />2=衣服特效(翅膀);<br />3武器特效;<br />4=盾牌;5=盾牌特效<br />6=左手武器;7=左手武器特效             |
| shape  | `integer` | 否   |      | 外观的shape(角色模型ID),-1表示清除                                                                              |
| time   | `integer` | 否   |      | 时间 (秒)                                                                                                       |
| param1 | `integer` | 否   |      | 仅在参数1位置为0时有效<br />0=覆盖时装外观<br />1=时装外观优先                                                      |
| param2 | `integer` | 否   |      | 仅在参数1位置为0时有效<br />0-斗笠、头发不变<br />1-隐藏斗笠<br />2-隐藏头发<br />3-隐藏斗笠和头发 4-隐藏盾牌和盾牌特效 |
```lua
    setfeature(actor,0,2,65535,0,3)

    --翅膀特效
    setfeature(actor,2,3,65535,0,0)
```

------------

### 检测装备的元素属性
`checknewitemvalue`

| 参数   | 类型      | 空   | 默认 | 注释                                             |
| :----- | :-------- | :--- | :--- | :----------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                         |
| where  | `integer` | 否   |      | 装备位置：<br />-1-OK框中的装备<br />0~55-身上的装备 |
| iAttr  | `integer` | 否   |      | 属性                                             |
| sFlag  | `string`  | 否   |      | 比较符（=&lt;&gt;）                                    |
| iValue | `integer` | 否   |      | 数值(1-100)，百分比                              |
```
(0)暴击几率增加 1~100%
(1)增加攻击伤害 1~100%
(2)物理伤害减少 1~100%
(3)魔法伤害减少 1~100%
(4)忽视目标防御 1~100%
(5)所有伤害反弹 1~100%
(6)增加目标暴率 1~100%
(7)人物体力增加 1~100%
(8)人物魔力增加 1~100%
(11)暴击伤害增加 1~100%
```

### 给人物装备面板加特效
`updateequipeffect`

| 参数     | 类型      | 空   | 默认 | 注释                    |
| :------- | :-------- | :--- | :--- | :---------------------- |
| play     | `object`  | 否   |      | 玩家对象                |
| effectid | `integer` | 否   |      | 特效ID， 0-删除特效     |
| position | `integer` | 否   |      | 显示位置：0-前面 1-后面 |

------------

## 技能魔法

### 获取技能信息
`getskillinfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid | `integer`    |否   |    |   技能ID  |
|type     | `integer`       |否   | 4:熟练度上限<br />引擎64_23.0628新增   |   获取类型:<br />1:等级;<br />2:强化等级;<br />3:熟练度;<br />4:熟练度上限;    |
|result       | `integer`       |否   |   |   返回值(对应属性值) ,没有技能，返回nil   |

### 添加技能
`addskill`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid | `integer`    |否   |    |   技能ID  |
|level    | `integer`       |否   |    |   等级   |

### 删除技能
`delskill`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid | `integer`    |否   |    |   技能ID  |

```lua
function main(self)
    local lv = getskillinfo(self,11,1)
    if lv and lv &gt;0 then
        delskill(self, 11)
        say(self,"删除雷电术")
    else
        addskill(self, 11, 3)
        say(self,"获得雷电术") 
    end
end
```

### 清空所有技能
`clearskill`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |

### 删除非本职业技能
`delnojobskill`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |

### 设置技能等级
`setskillinfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid     | `integer`    |否   |    |   技能ID |
|flag     | `integer`    |否   |    |   类型：<br />1-技能等级<br />2-强化等级<br />3-熟练度 |
|point     | `integer`    |否   |    |   等级或点数 |

### 接口获取角色所有技能

`getallskills`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| actor  | `object` | 否   |      | 玩家对象 |
| result | `table`  | 否   |      | 技能列表 |
```lua
    local skill_list = getallskills(actor)
    for _, skillID in ipairs(skill_list or {}) do
        release_print("技能", skillID )
    end
```

------------

### 用脚本命令释放技能

`releasemagic`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid     | `integer`    |否   |    |   技能ID |
|type     | `integer`    |否   |    |   类型：<br />1-普通技能<br />2-强化技能 |
|level     | `integer`    |否   |    |  技能等级 |
|target     | `integer`    |否   |    | 技能对象：<br />1-攻击目标，<br />2-自身|
|flag     | `integer`    |否   |    |   是否显示施法动作：<br />0-不显示，1-显示 |

### 对目标释放技能

`releasemagic_target`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                                   |
| :------ | :-------- | :--- | :--- | :------------------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                               |
| skillID | `integer` | 否   |      | 技能ID                                 |
| sType   | `integer` | 否   |      | 类型<br />1-普通技能<br />2-强化技能       |
| sLevel  | `integer` | 否   |      | 技能等级                               |
| target  | `object`  | 否   |      | 目标对象                               |
| data    | `integer` | 是   | 0    | 是否显示施法动作<br />0-不显示<br />1-显示 |
```lua
    releasemagic_target(actor,skill_id,1,skill_lv,mon,0)
```

### 对坐标释放技能

`releasemagic_pos`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                                   |
| :------ | :-------- | :--- | :--- | :------------------------------------- |
| actor   | `object`  | 否   |      | 玩家对象                               |
| skillID | `integer` | 否   |      | 技能ID                                 |
| sType   | `integer` | 否   |      | 类型<br />1-普通技能<br />2-强化技能       |
| sLevel  | `integer` | 否   |      | 技能等级                               |
| X       | `integer` | 否   |      | 目标点X坐标                            |
| Y       | `integer` | 否   |      | 目标点Y坐标                            |
| data    | `integer` | 是   | 0    | 是否显示施法动作<br />0-不显示<br />1-显示 |
```lua
    releasemagic_pos(actor,skill_id,1,skill_lv,pos_X,pos_Y,0)
```

------------

### 设置人物攻击力倍数
`powerrate`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|rate     | `integer`    |否   |    |  攻击威力比率，100=100% |
|time     | `integer`    |否   |    |  有效时间，超过时间恢复正常 |

### 减少技能CD冷却时间
`setskilldeccd`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillname     |`string`    |否   |    |  技能名称 |
|char     |`string`    |否   |    |  操作符(+/-/=) <br />=0就是还原技能CD|
|time     | `integer`    |否   |    | 时间（秒) |

### 获取技能初始冷却时间
`getskillcscd`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|skillname     |`string`    |否   |    |  技能名称 |
|result     | `integer`    |否   |    |  冷却时间(毫秒) |

### 获取当前技能冷却时间
`getskilldqcd`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillname     |`string`    |否   |    |  技能名称 |
|result     | `integer`    |否   |    |  冷却时间(毫秒) |

### 重置技能冷却时间

`skillrestcd`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数              | 类型               | 空   | 默认                    | 注释                               |
| :---------------- | :----------------- | :--- | :---------------------- | :--------------------------------- |
| actor             | `string`           | 否   |                         | 玩家对象                           |
| skillName/skillID | `string`/`integer` | 否   |                         | 技能名称/技能ID                    |
| time              | `integer`          | 是   | 引擎64_24.05.23新增参数 | 减免的cd时间<br />传入0则重置技能CD  |
| timeType          | `integer`          | 是   | 引擎64_24.08.07新增参数 | 0=时间单位为秒<br />1=时间单位为毫秒 |

### 获取技能等级
`getskilllevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid     | `integer`    |否   |    |   技能ID |

### 获取技能强化等级
`getskilllevelup`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid     | `integer`    |否   |    |   技能ID |

### 获取技能熟练度
`getskilltrain`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillid     | `integer`    |否   |    |   技能ID |

### 增加技能威力
`setmagicpower`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillname     |`string`    |否   |    |  技能名称 |
|value     | `integer`    |否   |    |  威力值 |
|type     | `integer`    |否   |    |  计算方式(0按点数计算,1按百分比计算) |

### 增加技能防御力
`setmagicdefpower`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`    |否   |    |   玩家对象 |
|skillname     |`string`    |否   |    |  技能名称 |
|value     | `integer`    |否   |    |  抵消威力值 |
|type     | `integer`    |否   |    |  计算方式(0按点数计算,1按百分比计算) |
```lua
    setmagicdefpower(play,"雷电术",500,0)
```

### 根据技能id获取技能名字
`getskillname`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|skillid     | `integer`    |否   |    |  技能id |
|result     |`string`    |否   |    |  技能名称 |

### 根据技能名字获取技能id
`getskillindex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|skillname     |`string`    |否   |    |  技能名称 |
|result     | `integer`    |否   |    |  技能id |

### 改变技能特效

`setmagicskillefft`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数      | 类型      | 空   | 默认 | 注释                                                    |
| :-------- | :-------- | :--- | :--- | :------------------------------------------------------ |
| play      | `object`  | 否   |      | 玩家对象                                                |
| skillName | `string`  | 否   |      | 技能名称                                                |
| effectID  | `integer` | 否   |      | 特效id,=0为关闭<br />(cfg_skill_present.xls表id)          |
| effectID2 | `integer` | 否   |      | 持续性ID(魔法盾BUFF表id/火墙/群体雷电术/其他的技能无效) |
```lua
    setmagicskillefft(actor,"雷电术", 33)
```

------------

## 获取玩家对象

### 根据玩家名
`getplayerbyname`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| name   | `string` | 否   |      | 玩家名字 |
| result | `object` | 否   |      | 玩家对象 |

### 根据玩家唯一ID
`getplayerbyid`

| 参数   | 类型     | 空   | 默认 | 注释       |
| :----- | :------- | :--- | :--- | :--------- |
| id     | `string` | 否   |      | 玩家唯一id |
| result | `object` | 否   |      | 玩家对象   |

------------

### 完美封号系统
`setranklevelname`

| 参数      | 类型     | 空   | 默认 | 注释                     |
| :-------- | :------- | :--- | :--- | :----------------------- |
| play      | `object` | 否   |      | 玩家对象                 |
| levelname | `string` | 否   |      | 称号文本，和名字一起显示 |
```lua
--显示在名字上方
setranklevelname(actor,"%s\\[击杀xx人]")

--显示在名字后方
setranklevelname(actor,"%s[击杀xx人]")
```

## 攻击模式

### 修改攻击模式
`changeattackmode`

| 参数       | 类型      | 空   | 默认 | 注释                                                                                                                                     |
| :--------- | :-------- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------------------------- |
| play       | `object`  | 否   |      | 玩家对象                                                                                                                                 |
| attackmode | `integer` | 否   |      | 攻击模式：<br />0-全体攻击<br />1-和平攻击<br />2-夫妻攻击<br />3-师徒攻击<br />4-编组攻击<br />5-行会攻击<br />6-红名攻击<br />7-国家攻击<br />8-阵营攻击 |

### 强制修改攻击模式
`setattackmode`

| 参数       | 类型      | 空   | 默认 | 注释                            |
| :--------- | :-------- | :--- | :--- | :------------------------------ |
| play       | `object`  | 否   |      | 玩家对象                        |
| attackmode | `integer` | 否   |      | 攻击模式<br />-1-提前结束强制状态 |
| time       | `integer` | 否   |      | 强制切换时间时间                |

### 获取当前攻击模式
`getattackmode`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                                                     |
| :----- | :-------- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                                                                                                                 |
| result | `integer` | 否   |      | 攻击模式：<br />0-全体攻击<br />1-和平攻击<br />2-夫妻攻击<br />3-师徒攻击<br />4-编组攻击<br />5-行会攻击<br />6-红名攻击<br />7-国家攻击<br />8-阵营攻击 |

## 仓库

### 打开仓库面板

`openstorage`

| 参数     | 类型      | 空   | 默认                | 注释                         |
| :------- | :-------- | :--- | :------------------ | :--------------------------- |
| play     | `object`  | 否   |                     | 玩家对象                     |
| isOpenUI | `integer` | 是   | 引擎64_24.05.23新增 | 0/nil=打开UI<br />1=只下发数据 |

### 新解锁仓库格子

&gt; 最大支持240格 ,cfg_game_data.xls表 字段：warehouse_max_num 设置最大总仓库格子数

`changestorage`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| nCount | `integer` | 否   |      | 新解锁的格子数 |

### 获取仓库剩余格子数
`getsblank`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| result | `integer` | 否   |      | 仓库剩余格子数 |

### 获取玩家仓库最大格子数
`getssize`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| result | `integer` | 否   |      | 仓库最大格子数 |

------------

### 获取所有玩家对象列表(遍历玩家列表)

`getplayerlst`

| 参数    | 类型      | 空   | 默认                | 注释                                           |
| :------ | :-------- | :--- | :------------------ | :--------------------------------------------- |
| offline | `integer` | 是   | 引擎64_24.05.23新增 | 是否剔除离线挂机玩家<br />0/nil=不剔除<br />1=剔除 |

```lua
    local player_list = getplayerlst(0)
    for i, player  in ipairs(player_list or {}) do
        release_print("在线玩家",i,getbaseinfo(player,1),"角色是否离线挂机:",getbaseinfo(player,61))
    end
```

------------

### 获取玩家GM权限值
`getgmlevel`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| result | `integer` | 否   |      | GM权限值 |

### 设置玩家GM权限值
`setgmlevel`

| 参数    | 类型      | 空   | 默认 | 注释     |
| :------ | :-------- | :--- | :--- | :------- |
| play    | `object`  | 否   |      | 玩家对象 |
| gmlevel | `integer` | 否   |      | GM权限值 |

------------

### 复活
`realive`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 人物强制掉线(踢人下线)
`kick`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

------------

### 延时跳转
`delaygoto`

| 参数 | 类型      | 空   | 默认 | 注释                                          |
| :--- | :-------- | :--- | :--- | :-------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                      |
| time | `integer` | 否   |      | 时间(毫秒)                                    |
| func | `string`  | 否   |      | 触发函数                                      |
| del  | `integer` | 否   |      | 换地图是否删除此延时(0或为空时=不删除 1=删除) |

```lua
    delaygoto(actor,1000,"test_jump,ceshi,44",0)

    --QFunction-0.lua
    function test_jump(actor,...)
        release_print(getbaseinfo(actor,1),...)
    end
```

### 删除延迟

`cleardelaygoto`

| 参数 | 类型     | 空   | 默认                | 注释                                 |
| :--- | :------- | :--- | :------------------ | :----------------------------------- |
| play | `object` | 否   |                     | 玩家对象                             |
| func | `string` | 否   | 引擎64_23.08.30新增 | 需要删除的延时函数<br />不填为清除全部 |
```lua
delaygoto(actor,1000,"test_jump1",0)
cleardelaygoto(actor,"test_jump1")

delaygoto(actor,1000,"test_jump2,1,2,3",0)
cleardelaygoto(actor,"test_jump2,1,2,3")
```

### 添加系统延时回调

`grobaldelaygoto`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数     | 类型      | 空   | 默认 | 注释       |
| :------- | :-------- | :--- | :--- | :--------- |
| time     | `integer` | 否   |      | 时间(毫秒) |
| funcName | `string`  | 否   |      | 触发函数   |

### 删除系统延时回调

`grobalcleardelaygoto`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数     | 类型     | 空   | 默认 | 注释                                                                       |
| :------- | :------- | :--- | :--- | :------------------------------------------------------------------------- |
| funcName | `string` | 是   |      | 需要删除的延时函数<br />不填为清除全部                                       |
| value    | `string` | 是   | 0    | 是否忽视标签参数<br />0=不忽视,要完整填写添加时的参数<br />1=忽视,只判断函数名 |
```lua
    grobaldelaygoto(1000,"grobal_jump,a,b,c")

    grobalcleardelaygoto("grobal_jump,a,b,c",0)
    grobalcleardelaygoto("grobal_jump",1)
```

### 延时消息跳转
`delaymsggoto`

| 参数 | 类型      | 空   | 默认 | 注释       |
| :--- | :-------- | :--- | :--- | :--------- |
| play | `object`  | 否   |      | 玩家对象   |
| time | `integer` | 否   |      | 时间(毫秒) |
| func | `string`  | 否   |      | 触发函数   |
通过消息机制实现延时跳转，允许触发函数内嵌跳转，实现多次跳转，需要传递参数，将参数与函数名使用“,”连接。
本延时跳转不支持删除。
```lua
    delaymsggoto(actor, 2000, "@test_jump,ceshi,55")

    --QFunction-0.lua
    function test_jump(actor,...)
        release_print(getbaseinfo(actor,1),...)
    end
```

------------

### 增加附加伤害效果
`rangeharm`

| 参数       | 类型      | 空   | 默认               | 注释                                                                                                                                                                                                                                                       |
| :--------- | :-------- | :--- | :----------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| play       | `object`  | 否   |                    | 玩家对象                                                                                                                                                                                                                                                   |
| targetX    | `integer` | 否   |                    | X坐标                                                                                                                                                                                                                                                      |
| targetY    | `integer` | 否   |                    | Y坐标                                                                                                                                                                                                                                                      |
| range      | `integer` | 否   |                    | 影响范围                                                                                                                                                                                                                                                   |
| power      | `integer` | 否   |                    | 攻击力                                                                                                                                                                                                                                                     |
| addtype    | `integer` | 否   |                    | 附加类型：<br />0.无,1.击退,2.冻结,<br />3.麻痹,4.吸血,5.吸蓝,<br />6.真实伤害数值,7.蛛网效果,8.红毒,<br />9.绿毒,10.定身,11.防禁锢,<br />12.最大hp百分比真实伤害,<br />13.当前hp百分比真实伤害                                                                        |
| addvalue   | `integer` | 否   |                    | 附加属性值：<br />1.击退距离;2.冻结时间;<br />3.麻痹时间;4.吸血值;<br />5.吸蓝值;6.真实伤害值;<br />7.蛛网时间;8;红毒时间;<br />9.绿毒时间;<br />10.定身时间(定身时间单位是毫秒);<br />11.防禁锢时间(秒);<br />12.最大hp百分比真实伤害的值;<br />13.当前hp百分比真实伤害的值 |
| checkstate | `integer` | 否   |                    | 是否检查防冻结/麻痹/石化/冰冻/蛛网/红毒/绿毒属性<br />0=直接设置状态;1=检查后设置状态)                                                                                                                                                                       |
| targettype | `integer` | 否   |                    | 目标类型(0或空=所有目标;1=仅人物;2=仅怪物)                                                                                                                                                                                                                 |
| effectid   | `integer` | 否   |                    | 目标身上播放的特效ID                                                                                                                                                                                                                                       |
| harmNum    | `integer` | 否   | 引擎64_23.0628新增 | 群体伤害目标个数                                                                                                                                                                                                                                           |

### 人物飘血飘字特效
`sendattackeff`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                                                                              |
| :----- | :-------- | :--- | :--- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| target | `object`  | 否   |      | 飘血飘字的主体，一般为受攻击者                                                                                                                                    |
| type   | `integer` | 否   |      | 显示类型<br /> 1- 伤害，<br />2- 暴击伤害，<br />4- 加HP，<br />5- 格挡，<br />8- 扣减HP和MP，<br />9- 伤害，<br />10-扣减MP，<br />11- 致命一击<br />对应cfg_damage_number表里的ID |
| damage | `integer` | 否   |      | 显示的点数                                                                                                                                                        |
| hitter | `object`  | 否   |      | 可看到飘血飘字的主体，一般为攻击者                                                                                                                                |

```lua
[[
    参数1[target]可以为玩家对象、怪物对象
    参数4[hitter]可以传入字符串“*”表示该飘血飘字特效为广播特效，即视野范围内玩家均可见
]]
sendattackeff(monobj,1,999,"*")
```

### 设定人物攻击飘血飘字类型
`setattackefftype`

| 参数 | 类型      | 空   | 默认 | 注释                                                                                                                                                              |
| :--- | :-------- | :--- | :--- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                                                                                                                                          |
| type | `integer` | 否   |      | 显示类型<br /> 1- 伤害，<br />2- 暴击伤害，<br />4- 加HP，<br />5- 格挡，<br />8- 扣减HP和MP，<br />9- 伤害，<br />10-扣减MP，<br />11- 致命一击<br />对应cfg_damage_number表里的ID |

```
设定人物飘血飘字类型，传入参数为攻击者，当前攻击飘血时有效，一次设定后，即返回默认值
```

------------

### 采集挖矿等进度条操作

`showprogressbardlg`

| 参数    | 类型      | 空   | 默认 | 注释                                 |
| :------ | :-------- | :--- | :--- | :----------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                             |
| time    | `integer` | 否   |      | 进度条时间，秒                       |
| succ    | `string`  | 否   |      | 成功后跳转的函数                     |
| msg     | `string`  | 否   |      | 提示消息                             |
| canstop | `integer` | 否   |      | 能否中断<br />0-不可中断<br />1-可以中断 |
| fail    | `string`  | 否   |      | 中断触发的函数                       |
```lua
showprogressbardlg(actor,5,"@func_1","进度条测试..", 1,"@func_2")

[[注:跳转函数不能附带参数]]
function func_1(actor)
    release_print("func_1",getbaseinfo(actor,1))
end

function func_2(actor)
    release_print("func_2",getbaseinfo(actor,1))
end
```

### 改变玩家速度
`changespeed`

| 参数  | 类型      | 空   | 默认 | 注释                                                                      |
| :---- | :-------- | :--- | :--- | :------------------------------------------------------------------------ |
| play  | `object`  | 否   |      | 玩家对象                                                                  |
| type  | `integer` | 否   |      | 速度类型：<br />1-移动速度<br />2-攻击速度<br />3-施法速度                      |
| level | `integer` | 否   |      | 速度等级 -10~10<br />0-原始速度，<br />-1时间间隔减少10%<br />+1时间间隔增加10% |

### 百分比修改速度

`changespeedex`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                               |
| :---- | :-------- | :--- | :--- | :------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                           |
| model | `integer` | 否   |      | 计算方式<br />1=移动速度<br />2=攻击速度<br />3=魔法速度 |
| value | `integer` | 否   |      | 速度值<br />0=原速度(大于0=加速 -=减速)              |
| time  | `integer` | 否   |      | 有效时间秒<br />(为空=表示不限制时间,最大值65535)    |
```lua
    changespeedex(actor,1,50,65535)
```

### 设置玩家穿人穿怪
`throughhum`

| 参数    | 类型      | 空   | 默认 | 注释                                         |
| :------ | :-------- | :--- | :--- | :------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                     |
| type    | `integer` | 否   |      | 模式：0-恢复默认；1-穿人；2-穿怪；3-穿人穿怪 |
| time    | `integer` | 否   |      | 时间(秒)                                     |
| objtype | `integer` | 否   |      | 对象 ：0-玩家；1-宝宝                        |

### 设置当前攻击目标
`settargetcert`

| 参数   | 类型     | 空   | 默认 | 注释                         |
| :----- | :------- | :--- | :--- | :--------------------------- |
| Hiter  | `object` | 否   |      | 攻击者<br />(玩家/英雄/怪物)   |
| Target | `object` | 否   |      | 被攻击者<br />(玩家/英雄/怪物) |
```
    将Hiter当前的攻击目标设定为Target
    注意：玩家实际攻击目标由客户端锁定，以修改当前玩家攻击目标为目的会失效。
```

### 判断对象是否可被攻击
`ispropertarget`

| 参数   | 类型      | 空   | 默认 | 注释                                          |
| :----- | :-------- | :--- | :--- | :-------------------------------------------- |
| Hiter  | `object`  | 否   |      | 攻击对象<br />(玩家/英雄/怪物)                  |
| Target | `object`  | 否   |      | 被攻击对象<br />(玩家/英雄/怪物)                |
| Result | `boolean` | 否   |      | 返回值<br />true:可以被攻击<br />false:不可被攻击 |

### 增加气泡
`addbutshow`

| 参数 | 类型      | 空   | 默认 | 注释                     |
| :--- | :-------- | :--- | :--- | :----------------------- |
| play | `object`  | 否   |      | 玩家对象                 |
| ID   | `integer` | 否   |      | ID                       |
| name | `string`  | 否   |      | 显示名称                 |
| fun  | `fun`     | 否   |      | 函数名(多参数用逗号分割) |
```lua
addbutshow(actor,1,"测试气泡","@testjump,参数1,参数2,参数3")

function testjump(actor,...)
    release_print(...)
end

```
### 删除气泡
`delbutshow`

| 参数 | 类型      | 空   | 默认 | 注释     |
| :--- | :-------- | :--- | :--- | :------- |
| play | `object`  | 否   |      | 玩家对象 |
| ID   | `integer` | 否   |      | ID       |

### 获取对面人物的名字
`getoppositeobj`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |
```lua
    local otherPlayer = getoppositeobj(actor)
    release_print("对面玩家",getbaseinfo(otherPlayer,1))
```

### 调用游戏面板

`openhyperlink`

| 参数    | 类型      | 空   | 默认                | 注释                                                                                                      |
| :------ | :-------- | :--- | :------------------ | :-------------------------------------------------------------------------------------------------------- |
| play    | `object`  | 否   |                     | 玩家对象                                                                                                  |
| nId     | `integer` | 否   |                     | 面板ID                                                                                                    |
| nState  | `integer` | 否   |                     | 0=打开<br />1=打开面板重复点按钮不会关闭,除非主动点关闭按钮(一般做任务配合新手引导用到)<br />2=关闭当前面板ID |
| rankWnd | `integer` | 否   | 引擎64_23.08.30新增 | 面板ID(新排行榜用)                                                                                        |
| isHero  | `integer` | 否   | 引擎64_23.08.30新增 | 0/nil=玩家<br />1=英雄(新排行榜用)                                                                          |

*跳转面板ID参考如下: *
```
        Equip               = 1,            -- 角色-装备
        State               = 2,            -- 角色-状态
        Attri               = 3,            -- 角色-属性
        Skill               = 4,            -- 角色-技能
        Title               = 5,            -- 角色-装备
        BestRing            = 6,            -- 角色-首饰盒
        Bag                 = 7,            -- 背包
        Stall               = 8,            -- 摆摊
        StoreHot            = 9,            -- 商城-热销
        StoreBeauty         = 10,           -- 商城-装饰
        StoreEngine         = 11,           -- 商城-功能
        StoreFestival       = 12,           -- 商城-节日
        GuildMain           = 13,           -- 行会-主界面
        GuildMember         = 14,           -- 行会成员列表
        GuildList           = 15,           -- 行会列表
        Mail                = 16,           -- 邮件
        Team                = 17,           -- 组队
        NearPlayer          = 18,           -- 附近玩家

        Setting             = 23,           -- 设置
        MiniMap             = 24,           -- 小地图
        SkillSetting        = 25,           -- 技能设置
        StoreRecharge       = 26,           -- 充值
        Auction             = 27,           -- 拍卖行
        Friend              = 28,           -- 好友
        ExitToRole          = 29,           -- 小退
        GuildCreate         = 30,           -- 行会创建
        Guild               = 31,           -- 智能行会界面
        Rank                = 32,           -- 排行榜
        Trade               = 33,           -- 面对面交易 请求
        ForceExitToRole     = 34,           -- 强制小退
        TradingBank         = 35,           -- 交易行
        GuideEnter          = 36,           -- 引导进入
        SuperEquip          = 37,           -- 角色-神装
        HeroEquip           = 41,           -- 英雄-装备
        HeroState           = 42,           -- 英雄-状态
        HeroAttri           = 43,           -- 英雄-属性
        HeroSkill           = 44,           -- 英雄-技能
        HeroTitle           = 45,           -- 英雄-称号
        HeroBestRing        = 46,           -- 英雄-首饰盒
        HeroBag             = 47,           -- 英雄-背包
        HeroSuperEquip      = 48,           -- 英雄-神装
        ReinAttrPoint       = 51,           -- 转生属性点
        Chat                = 52,           -- 聊天
        PCPrivate           = 53,           -- PC 私聊记录页

        MagicJointAttack    = 99,           -- 释放合击

        AssistChange        = 110,          -- 主界面-任务栏
        Box996              = 111,          -- 盒子称号
        MainMiniMapChange   = 112,          -- 小地图伸缩
        PCResolution        = 113,          -- PC 分辨率设置
        ChatExtendEmoj      = 114,          -- 角色-表情
        ChatExtendBag       = 115,          -- 聊天小框-背包
        MainNear            = 116,          -- 主界面-附近列表
        CallPay             = 117,          -- 调用-支付

        SettingBasic        = 300,          -- 基础设置
        SettingWindowRange  = 301,          -- 视距
        SettingFight        = 302,          -- 战斗
        SettingProtect      = 303,          -- 保护
        SettingAuto         = 304,          -- 挂机
        SettingHelp         = 305,          -- 帮助

        KeFu                = 310,          -- 调用客服界面
        Compound            = 2201,         -- 合成
```

### 开启自动挂机
`startautoattack`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 停止自动挂机
`stopautoattack`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

------------

### 离线挂机

`offlineplay`

&gt; 使用离线挂机功能，一定要在玩家退出游戏时候关闭所有定时器！
&gt; 本地环境使用离线挂机接口,重新登录时会出现无法登录情况,线上环境不会出现!

| 参数 | 类型      | 空   | 默认 | 注释           |
| :--- | :-------- | :--- | :--- | :------------- |
| play | `object`  | 否   |      | 玩家对象       |
| time | `integer` | 否   |      | 离线时间（分） |

### 剔除离线挂机角色

`tdummy`

| 参数  | 类型     | 空   | 默认 | 注释                                          |
| :---- | :------- | :--- | :--- | :-------------------------------------------- |
| mapID | `string` | 否   |      | 地图号, <br />“\*”表示全部地图                  |
| level | `string` | 否   |      | 剔除等级<br />低于此等级均剔除<br /> “\*”表示所有 |
| count | `string` | 否   |      | 最大剔除玩家数<br /> “\*”表示所有               |

### 获取玩家好友列表
`getfriendnamelist`

| 参数   | 类型     | 空   | 默认 | 注释           |
| :----- | :------- | :--- | :--- | :------------- |
| play   | `object` | 否   |      | 玩家对象       |
| result | `table`  | 否   |      | 好友的名字列表 |
```lua
    local list = getfriendnamelist(actor)
    for key, value in pairs(list or {}) do
        release_print(key,value)
    end
```

---

### 人物转生控制

`renewlevel`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                 |
| :----- | :-------- | :--- | :--- | :----------------------------------------------------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                                                             |
| rlevel | `integer` | 否   |      | 转生次数<br />一次转多少级(数值范围为1-255)                                            |
| level  | `integer` | 否   |      | 转生后等级<br />代表转生后人物的等级，0为不改变人物当前等级                            |
| num    | `integer` | 否   |      | 分配点数<br />转生后可以得到的点数，此点数可能按比例换成人物属性点(数值范围 1 - 20000) |

### 调整人物转生属性点

`bonuspoint`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释         |
| :---- | :-------- | :--- | :--- | :----------- |
| play  | `object`  | 否   |      | 玩家对象     |
| sFlag | `string`  | 否   |      | 操作符(=,+)  |
| value | `integer` | 否   |      | 点数(0-1000) |

### 获取人物转生属性点

`getbonuspoint`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| result | `integer` | 否   |      | 属性点数 |

### 复位属性点数

`restbonuspoint`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

---

### 获取玩家pk等级
`getpklevel`

| 参数   | 类型      | 空   | 默认 | 注释                                      |
| :----- | :-------- | :--- | :--- | :---------------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                                  |
| result | `integer` | 否   |      | pk等级<br />0.白名;1.黄名;2.红名;<br />3.灰名 |

------------

### 给按钮增加红点

`reddot`

| 参数          | 类型      | 空   | 默认 | 注释                                             |
| :------------ | :-------- | :--- | :--- | :----------------------------------------------- |
| play          | `object`  | 否   |      | 玩家对象                                         |
| win_id        | `integer` | 否   |      | 窗口ID                                           |
| btn_id        | `integer` | 否   |      | 按钮ID/任务栏填任务ID                            |
| x             | `integer` | 否   |      | X坐标                                            |
| y             | `integer` | 否   |      | Y坐标                                            |
| type          | `integer` | 否   |      | 红点模式<br />0=图片<br />1=特效                     |
| path/effectID | `integer` | 否   |      | 红点模式=0(填图片路径)<br />红点模式=1(填特效编号) |

```lua
reddot(actor, 104, 7, 15, 15, 1, 5055)
```

### 给按钮删除红点

`reddel`

| 参数   | 类型      | 空   | 默认 | 注释                  |
| :----- | :-------- | :--- | :--- | :-------------------- |
| play   | `object`  | 否   |      | 玩家对象              |
| win_id | `integer` | 否   |      | 窗口ID                |
| btn_id | `integer` | 否   |      | 按钮ID/任务栏填任务ID |

```lua
reddel(actor, 104, 7)
```

------------

### 拾取道具飞入背包按钮动作

`setpickitemtobag`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| win_id | `integer` | 否   |      | 窗口ID   |
| btn_id | `integer` | 否   |      | 按钮ID   |

```lua
setpickitemtobag(actor,104,7)
```

------------

### 吸怪功能

`monmove`

| 参数     | 类型      | 空   | 默认 | 注释                                                                       |
| :------- | :-------- | :--- | :--- | :------------------------------------------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                                                   |
| max      | `integer` | 否   |      | 最大范围                                                                   |
| min      | `integer` | 否   |      | 最小范围                                                                   |
| monLevel | `integer` | 否   |      | 怪物等级<br />=0则嘲讽/吸引所以级别怪物                                      |
| type     | `integer` | 否   |      | 0=不嘲讽玩家<br /> 1=嘲讽玩家                                                |
| isMove   | `integer` | 否   |      | 0=怪物漂移到人物边<br />1=怪物瞬移到目前人物坐标<br />2=怪物瞬移到目前人物面前 |
| unLimit  | `integer` | 否   |      | 0=无限制<br />1=怪物/人物攻击目标不归属自己的不可被吸                        |

```lua
monmove(actor,10, 2, 0, 0, 2, 0)
```

------------

### 人物显示一个放大的虚影

`showphantom`

| 参数    | 类型      | 空   | 默认 | 注释          |
| :------ | :-------- | :--- | :--- | :------------ |
| play    | `object`  | 否   |      | 玩家对象      |
| opacity | `integer` | 否   |      | 透明度(0~255) |
| time    | `integer` | 否   |      | 显示时间(秒)  |

```lua
showphantom(actor,100,3)
```

------------

### 绑定背包满触发

`bindevent`

| 参数         | 类型      | 空   | 默认 | 注释                       |
| :----------- | :-------- | :--- | :--- | :------------------------- |
| play         | `object`  | 否   |      | 玩家对象                   |
| bindingType  | `object`  | 否   |      | 绑定类型(1：背包满通知)    |
| isOpen       | `integer` | 否   |      | 是否开启(0：关闭，1：开启) |
| callbackFunc | `string`  | 否   |      | 回调函数(QF)               |

```lua
bindevent(actor,1,1,"@on_bag_full_lua")

--QFunction-0.lua
function on_bag_full_lua(actor,...)
end
```

------------

### 获取角色所有属性

`attrtab`

| 参数   | 类型     | 空   | 默认 | 注释       |
| :----- | :------- | :--- | :--- | :--------- |
| play   | `object` | 否   |      | 玩家对象   |
| result | `table`  | 否   |      | 所有属性值 |
```lua
    local attr = attrtab(actor)
    for key, value in pairs(attr or {}) do
        release_print("attr",key,value)
    end
```

------------

## 骑马相关

### 是否在骑马

`checkonhorse`

| 参数   | 类型     | 空   | 默认 | 注释        |
| :----- | :------- | :--- | :--- | :---------- |
| play   | `object` | 否   |      | 玩家对象    |
| result | `bool`   | 否   |      | true:在骑马 |

### 上马

`ridehorse`

| 参数        | 类型      | 空   | 默认 | 注释                               |
| :---------- | :-------- | :--- | :--- | :--------------------------------- |
| play        | `object`  | 否   |      | 玩家对象                           |
| HorseAppr   | `integer` | 否   |      | 坐骑外观                           |
| HorseEff    | `integer` | 否   |      | 坐骑特效外观                       |
| HorseFature | `integer` | 否   |      | 人物骑马外观                       |
| Type        | `integer` | 否   |      | 坐骑类型  0=单人   1=双人   2=连体 |

### 下马

`dismounthorse`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

------------

### 添加足迹特效

`setmoveeff `

| 参数     | 类型      | 空   | 默认 | 注释                                     |
| :------- | :-------- | :--- | :--- | :--------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                 |
| effectID | `integer` | 否   |      | 特效id                                   |
| modle    | `integer` | 否   |      | 播放模式<br />0/nil=两步播放<br />1=单步播放 |
```lua
    setmoveeff(actor,17,1)
```

------------

### 给视野内玩家发送自定义广播消息

`setotherparams`

| 参数     | 类型      | 空   | 默认 | 注释        |
| :------- | :-------- | :--- | :--- | :---------- |
| play     | `object`  | 否   |      | 玩家对象    |
| varIdx   | `integer` | 否   |      | 属性id(1~5) |
| varValue | `integer` | 否   |      | 属性值      |
```lua
    [[服务端]]
    setotherparams(actor,1,3)
    -- setotherparams(actor,2,256)
    setotherparams(actor,2,414)

    [[客户端]]
    SL:RegisterLUAEvent(LUA_EVENT_ACTOR_GMDATA_UPDATE, "ACTOR_GM_DATA", function (tab)
        SL:dump(tab,"自定义数据改变")
        SL:dump(SL:GetMetaValue("ACTOR_GM_DATA",tab.id),"获取actor的GM自定义数据")
    end)
    [[足迹示例]]
    local function moveEvent(data)
        local actorID = data and data.id
        if actorID then
            local posX = SL:GetMetaValue("ACTOR_POSITION_X", actorID)
            local posY = SL:GetMetaValue("ACTOR_POSITION_Y", actorID)
            local dir = SL:GetMetaValue("ACTOR_DIR", actorID)
            local effectModel = SL:GetMetaValue("ACTOR_GM_DATA", actorID)[1]
            local effectID = SL:GetMetaValue("ACTOR_GM_DATA", actorID)[2]
            if effectID ~= 0 and posX and posY then
                local actBegin = data.act
                if actBegin == 1 or actBegin == 6 or actBegin == 17 then
                    local eff = GUI:Effect_Create(GUI:Attach_SceneB(), string.format("foot_effect%s_%s%s", actorID, posX, posY), posX, posY, effectModel, effectID, 0,0 , dir, 0.8)
                    GUI:setScale(eff, 0.3)
                    if eff then
                        GUI:Effect_addOnCompleteEvent(eff, function()
                            GUI:removeFromParent(eff)
                        end)
                    end
                end
            end
        end
    end
    SL:RegisterLUAEvent(LUA_EVENT_PLAYER_ACTION_BEGIN, "GUIUtil", moveEvent)
    SL:RegisterLUAEvent(LUA_EVENT_NET_PLAYER_ACTION_BEGIN, "GUIUtil", moveEvent)
```

------------

### 收摊

`stopmyshop`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| player | `object` | 否   |      | 玩家对象 |

------------

### 骰子功能

`playdice`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数     | 类型      | 空   | 默认 | 注释                                   |
| :------- | :-------- | :--- | :--- | :------------------------------------- |
| player   | `object`  | 否   |      | 玩家对象                               |
| num      | `integer` | 否   |      | 动画数量<br />比如3就是会出现3个骰子转动 |
| funcName | `string`  | 否   |      | 动画结束触发                           |
```lua
    [[骰子的显示顺序和点数 对应 私人变量 D0 D1 D2 D3 D4 D5]]
    setplaydef(actor, "D0",1)
    setplaydef(actor, "D1",2)
    setplaydef(actor, "D2",3)
    setplaydef(actor, "D3",4)
    setplaydef(actor, "D4",5)
    setplaydef(actor, "D5",6)
    playdice(actor,1,"@test_jump,传参")

    -- QFunction-0.lua
    function test_jump(actor,...)
        release_print("test_jump,qf",getbaseinfo(actor,1),...)
    end
```

------------

### 开启宝箱

`opendragonbox`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释                                |
| :----- | :-------- | :--- | :--- | :---------------------------------- |
| actor  | `string`  | 否   |      | 玩家对象                            |
| boxidx | `integer` | 否   |      | 宝箱ID                              |
| num    | `integer` | 否   |      | 次数(不读数据表次数,只认这里的次数) |

------------

### 立即推送前端变量

`sendredvartoclient`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

------------

### 设置人物照亮范围（光照）

`setcandlevalue`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                |
| :---- | :-------- | :--- | :--- | :---------------------------------- |
| actor | `object`  | 否   |      | 玩家对象                            |
| value | `integer` | 否   |      | 人物照亮范围值<br />-1=读装备的光照值 |

```
    注:黑夜模式需在`M2-假人设置-光照系统-是否免蜡`中开启
```
# 称号相关





## 称号说明

- StdMode=70
- Name 称号的名称，该名称外观是否显示，由Reserved字段控制
- Shape 称号编号，触发用的(shape 编号从1开始)
- Color 颜色 0~255
- Reserved 显示DB中的名字(0默认显示名字+图标 1不显示数据库的称号名字 2不显示数据库的称号名字和头顶图标)
- Anicount 大于0时，无需设置为当前称号，属性就可以叠加到人物。等于0时，需要设置为当前称号，该称号的属性才会叠加到人物
- Looks 称号图片的开始位置路径：stab\res\private\title_icon
- DuraMax 可使用时间，单位小时
- 其他就等同于装备属性

- 称号改变属性及时刷新
- 称号物品DuraMax=0时，称号可以无限时间使用
- 赋予新称号，将标注为未使用状态，激活称号后才开始计时

------------

## 触发

### 称号改变触发

`titlechangedex`

| 参数     | 类型     | 空   | 默认 | 注释     |
| :------- | :------- | :--- | :--- | :------- |
| actor    | `string` | 否   |      | 玩家对象 |
| titleIdx | `number` | 否   |      | 称号索引 |

### 称号取消触发

`untitledex`

| 参数     | 类型     | 空   | 默认 | 注释     |
| :------- | :------- | :--- | :--- | :------- |
| actor    | `string` | 否   |      | 玩家对象 |
| titleIdx | `number` | 否   |      | 称号索引 |

------------

## 接口

### 添加称号
`confertitle`

| 参数   | 类型      | 空   | 默认 | 注释            |
| :----- | :-------- | :--- | :--- | :-------------- |
| play   | `object`  | 否   |      | 玩家对象        |
| name   | `string`  | 否   |      | 称号物品名称    |
| use    | `integer` | 否   |      | 开启激活，1激活 |
| result | `bool`    | 否   |      | 是否成功        |

```lua
function main(self)
    if confertitle(self, '君临天下') then
        say(self,"添加成功")
    else
        say(self,"添加失败")
    end
end
```

### 删除称号

`deprivetitle`

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| play   | `object` | 否   |      | 玩家对象     |
| name   | `string` | 否   |      | 称号物品名称 |
| result | `bool`   | 否   |      | 是否成功     |
```lua
function main(play)
    if deprivetitle(play, '君临天下') then
        say(play,"删除成功")
    else
        say(play,"删除失败")
    end
end
```

### 检测人物称号

`checktitle`

| 参数   | 类型     | 空   | 默认 | 注释                 |
| :----- | :------- | :--- | :--- | :------------------- |
| play   | `object` | 否   |      | 玩家对象             |
| title  | `string` | 否   |      | 称号                 |
| result | `bool`   | 否   |      | 返回值，是否有该称号 |

### 获取人物所有称号

`newgettitlelist`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| play   | `object` | 否   |      | 玩家对象     |
| result | `table`  | 否   |      | 返回称号列表<br />[称号id]=时间戳 |

```lua
    local titlelist = newgettitlelist(actor)
    for titleID, endTime in pairs(titlelist or {}) do
        local titleName = getstditeminfo(titleID,1)
        release_print("称号",titleName,titleID,os.date("%Y-%m-%d %H:%M:%S",endTime))
    end
```

### 改变称号时间

`changetitletime`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数      | 类型      | 空   | 默认 | 注释                                   |
| :-------- | :-------- | :--- | :--- | :------------------------------------- |
| actor     | `string`  | 否   |      | 玩家对象                               |
| titleName | `string`  | 否   |      | 称号名称                               |
| operation | `string`  | 否   |      | 操作符（+,-,=）                        |
| cour      | `integer` | 否   |      | 时间(+,-传入操作时间(秒), =传入时间戳) |

```lua
    changetitletime(actor,titleName,"+",cour)
```

------------

### ~~获取人物所有称号[已废弃]~~

~~`gettitlelist`~~


# 物品操作


### 物品规则计算方式
1.禁止扔 2.禁止交易 4.禁止存 8.禁止修 16.禁止出售 32.禁止爆出 64.丢弃消失 128.死亡必爆 256.禁止拍卖 512.禁止挑战 1024.爆出消失
* 很多设置物品规则的地方，可以根据业务需要，优先定义好。
例如：（绑定属性为 禁止扔，禁止交易，禁止出售）
那么对应的物品规则为：1+2+16 = 19，在后面需要传物品规则地方，只要传19进去即可

### 给物品

 `giveitem`

| 参数     | 类型      | 空   | 默认                | 注释                                                                                                                                   |
| :------- | :-------- | :--- | :------------------ | :------------------------------------------------------------------------------------------------------------------------------------- |
| play     | `object`  | 否   |                     | 玩家对象                                                                                                                               |
| itemname | `string`  | 否   |                     | 物品名称                                                                                                                               |
| qty      | `integer` | 是   | 1                   | 数量                                                                                                                                   |
| bind     | `integer` | 是   | 0                   | 物品规则                                                                                                                               |
| desc     | `string`  | 是   | 引擎64_24.05.23新增 | 描述                                                                                                                                   |
| result   | `object`  | 否   |                     | 返回值(最后一个物品对象)，不建议使用在叠加物品，一次性给多个物品的情况，此物品在添加背包触发后，注意可能被回收的情况 生成失败则返回nil |

```lua
    local item = giveitem(actor,"木剑",1,128,"测试")
```

### 给物品直接装备

`giveonitem`

| 参数     | 类型      | 空   | 默认                | 注释                                                            |
| :------- | :-------- | :--- | :------------------ | :-------------------------------------------------------------- |
| play     | `object`  | 否   |                     | 玩家对象                                                        |
| where    | `integer` | 否   |                     | [装备位置](http://engine-doc.996m2.com/web/#/9/5041 "装备位置") |
| itemname | `string`  | 否   |                     | 物品名称                                                        |
| qty      | `integer` | 是   | 1                   | 数量                                                            |
| bind     | `integer` | 是   | 0                   | 物品规则                                                        |
| desc     | `string`  | 是   | 引擎64_24.05.23新增 | 描述                                                            |
| result   | `bool`    | 否   |                     | 返回值(是否成功)                                                |

---

### 拿物品

 `takeitem`

&gt; **&lt;font color="#FF0000" style="font-size: 13px;"&gt;注:务必判断返回值,是否扣除物品成功,引擎锁定的物品并不会被扣除!&lt;/font&gt;**

 
| 参数     | 类型      | 空   | 默认                | 注释                                       |
| :------- | :-------- | :--- | :------------------ | :----------------------------------------- |
| play     | `object`  | 否   |                     | 玩家对象                                   |
| itemName | `string`  | 否   |                     | 物品名称                                   |
| itemNum  | `integer` | 是   |                     | 数量                                       |
| IgnoreJP | `integer` | 是   |                     | 忽略极品<br />0：所有都扣除<br />1：极品不扣除 |
| desc     | `string`  | 是   | 引擎64_24.05.23新增 | 描述                                       |
| result   | `bool`    | 是   |                     | true：成功<br />false：失败                  |
```lua
if not takeitem(actor,"木剑",2) then
    return say(actor,"物品扣除失败")
end
```

### 拿物品(拓展)

 `takeitemex`

&gt; **&lt;font color="#FF0000" style="font-size: 13px;"&gt;注:务必判断返回值,是否扣除物品成功,引擎锁定的物品并不会被扣除!&lt;/font&gt;**

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**
 
| 参数     | 类型      | 空   | 默认 | 注释                                         |
| :------- | :-------- | :--- | :--- | :------------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                     |
| itemName | `string`  | 否   |      | 物品名称                                     |
| itemNum  | `integer` | 是   |      | 数量                                         |
| bind     | `integer` | 是   |      | 0=忽略<br />1=扣除非绑定物品<br />2=扣除绑定物品 |
| desc     | `string`  | 是   |      | 描述                                         |
| result   | `bool`    | 是   |      | true：成功<br />false：失败                    |
```lua
if not takeitemex(actor, "木剑", 3,1,"奖励") then
    return say(actor,"物品扣除失败")
end
```

### 通过物品唯一id拿走物品

`delitembymakeindex`

&gt; **&lt;font color="#FF0000" style="font-size: 13px;"&gt;注:务必判断返回值,是否扣除物品成功,引擎锁定的物品并不会被扣除!&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认                | 注释                                                                   |
| :----- | :-------- | :--- | :------------------ | :--------------------------------------------------------------------- |
| play   | `object`  | 否   |                     | 玩家对象                                                               |
| ids    | `string`  | 否   |                     | 物品唯一ID，逗号(,)串联                                                |
| count  | `integer` | 否   |                     | 叠加物品扣除数量，<br />不填此参数，默认全部扣除<br />不可叠加物品全部扣除 |
| desc   | `string`  | 否   | 引擎64_24.03.14新增 | 描述                                                                   |
| result | `bool`    | 否   |                     | 是否扣除成功                                                           |

### 使用物品（吃药、使用特殊物品等）

`eatitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemname     |`string`        |否   |    |  物品名称   |
|count  |`integer`         |是   |1    |   数量    |

### 根据物品唯一ID获得物品对象

`getitembymakeindex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|makeindex     | `integer`      |否   |    |物品唯一ID |
|result     |`object`      |否   |    |物品对象 |
```
    会根据makeindex检索玩家装备和背包，返回对应的物品对象，如果检索不到，返回'0'
```

### 根据唯一ID删除仓库物品
 `delstorageitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid     |`integer`      |否   |    |   删除唯一ID物品 |

### 根据idx删除仓库物品
 `delstorageitembyidx`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemidx     |`integer`      |否   |    |   删除所有Idx物品 |

### 物品关联
#### ~~正在操作物品关联~~
`linkpickupitem`   --废弃，以后会在触发参数里，传递过来
&gt; 关联正在操作的物品，捡取，丢弃

#### 关联装备物品
`linkbodyitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|play     |`object`      |否   |    |   玩家对象 |
|where    |`integer`       |否   |    |   [装备位置](http://engine-doc.996m2.com/web/#/9/5041 "装备位置")  |
|result       |`object`        |否   |   |   返回物品对象    |

### 获取物品信息
`getiteminfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |   物品对象   |
|id       |`integer`       |否   |    |   1:唯一ID <br />2:物品ID<br />3:剩余持久<br />4:最大持久<br />5:叠加数量<br />6:绑定状态<br />7:物品名称(引擎64_23.08.30新增)<br />8:物品改名后的名称(引擎64_24.08.07新增)    |
|result |`integer`         |是   |0    |   对应数值，不存在为0    |

### 获取物品基础信息
`getstditeminfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|itemid/itemName      |`integer`/`string`      |否   |    |   物品ID/物品名称    |
|id       |`integer`       |否   | 13:物品颜色<br />引擎64_23.0628新增   |0:idx <br /> 1:名称 <br />2:StdMode<br />3:Shape<br />4:重量<br />5:AniCount <br />6:最大持久 <br />7:叠加数量<br />8:价格（price）<br />9:使用条件 <br />10:使用等级<br />11:自定义常量(29列)<br />12:自定义常量(30列)<br />13:道具颜色 |
|result |`integer`         |是   |0    |   对应数值，不存在为0    |

### 获取物品基础属性
`getstditematt`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|itemid       |`integer`       |否   |    |   物品ID    |
|id       |`integer`       |否   |    |对应属性表的属性ID |
|result |`integer`         |是   |0    |   对应数值，不存在为0    |

 ```lua
function main(self)
    local item=linkbodyitem(self,0)
    if item then
        local itemid = getiteminfo(self,item,2)
        say(self, "关联物品0成功，唯一ID：" .. getiteminfo(self,item,1) .."\\物品名称："
        ..getstditeminfo(itemid,1)
        .."\\基础防御下限："..getstditematt(itemid,9)
        .."\\基础防御上限："..getstditematt(itemid,10)
        )
    else
        say(self, "关联物品0失败")
    end
end
```

### 获取当前唯一ID物品的星星数量
`getitemstars`
**&lt;font color="#ff0000"&gt;只支持脱下装备获取，不支持穿戴获取星星&lt;/font&gt;**

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid       |`integer`       |否   |    |   物品唯一ID    |

## 物品记录信息

### 获取-getitemaddvalue

`getitemaddvalue`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |   物品对象   |
|type     |`integer`       |否   |    |[1,2,3] |
|position     |`integer`       |否   |    |当type=1,取值范围[0..49] <br /> type=2,取值范围[0..19]|
|model     |`integer`       |否   |   引擎64_23.10.24新增 |当type=1,<br />0=附加属性;<br />1=基础属性+附加属性|
|result |`integer`         |是   |0    |   返回位置对应值    |

* type=1对应位置定义（范围：0~49）
   0.AC
   1.MAC
   2.DC
   3.MC
   4.SC
   5.幸运
   6.准确
   7.敏捷
   8.攻击速度
   9.魔法躲避
   10.毒物躲避
   11.体力恢复
   12.魔法恢复
   13.中毒恢复
   15.沙巴克武器升级标记
   16.强化的星数 
   17.失败的星数
   18.炼魂等级
   19.是否有自定义名称
   20.物理伤害减少
   21.魔法伤害减少
   22.忽视目标防御
   23.所有伤害反弹
   24.人物体力增加
   25.人物魔力增加
   26.增加目标爆率
   27.神       圣
   28.强       度
   29.诅       咒
   30.暴击率
   31.暴击伤害
   32.攻击伤害
   33.神秘戒指 神秘手镯 神秘头盔 三个装备是否被穿戴过 ==&gt; 在 祝福罐, 聚灵珠 这个位置表示是否重置 当前持久为 0
   34~39.宠物相关
   **40~44. 脚本使用**
   45.投保次数
   46.限时道具激活方式
   47~48.背包特效与装备内观特效
   49.拍卖行相关
* type=2对应位置定义（范围：0~19）
   0:用来记录剩余时间(秒)，到期后，自动销毁，只针对穿着装备/称号
   1:物品规则。1.禁止扔 2.禁止交易 4.禁止存 8.禁止修 16.禁止出售 32.禁止爆出 64.丢弃消失 128.死亡必爆 256.禁止拍卖 512.禁止挑战 1024.爆出消失;
   2:物品名字颜色
   3.装备升级次数或星星数量
   4~6.装备初始时，附带特殊属性（Word+Word）共6个
   7~17.引擎使用
   18.装备自定义属性标记 1代表有自定义属性
   19.装备标记，脚本使用，一共32个标记，位运算，注意使用转换成无符号的，当设定值=0，相当于清空所有标记。
* type=3对应位置定义（范围：0~31）
   **装备标记，脚本使用**，一共32个标记。设置时，只有识别2进制最低位有效，即设定值=5时，相当于设定值=1。
   例如：setitemaddvalue(self,item,3,1,5)，设定值=5，支取5的二进制最低位1，相当于setitemaddvalue(self,item,3,1,1)
* 如果物品对象获取失败，返回-1

### 设置-setitemaddvalue
`setitemaddvalue`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |   物品对象   |
|type     |`integer`       |否   |    |[1,2,3] |
|position     |`integer`       |否   |    |当type=1,取值范围[0..49] <br /> type=2,取值范围[0..19]|
|value |`integer`      |否   |    |   设置物品对应位置值    |

## 刷新物品信息到前端
`refreshitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |

```lua
function main(self)
    local item = linkbodyitem(self, 0)
    if item then
        local itemid = getiteminfo(self, item, 2)
        local str
        str = ""
        for i = 0, 49 do
            str = str .. "," .. getitemaddvalue(self, item, 1, i)
        end
        str = str .. "\\"
        for i = 0, 19 do
            str = str .. "," .. getitemaddvalue(self, item, 2, i)
        end
        say(self, str);
        setitemaddvalue(self, item, 1, 1, math.random(100));
        refreshitem(self, item);
        recalcabilitys(self)
    else
        say(self, "关联物品0失败")
    end
end
```
## 自定义属性
### 获取-getitemcustomabil
`getitemcustomabil`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|result |`string`      |是   |0    |   Json字符串，自定义属性内容，如果获取物品对象失败，则返回空字符串    |

### 清理物品自定义属性-clearitemcustomabil
`clearitemcustomabil`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|group  |`integer`         |否   |0    | 组别，-1：所有组，0~5：对应组别  |

### 设置-setitemcustomabil
`setitemcustomabil`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|value  |`string`      |是   |0    |   Json字符串，自定义属性内容    |

- Json内容参考
```json
{"abil":[{"i":0,"t":"[锻造属性]","c":251,"v":[[0,3,1,0,1,0,1],[0,4,1,0,1,0,2],[0,5,1,0,9,2,3],[0,6,1,0,9,2,4],[0,7,1,0,10,3,5],[0,8,1,0,10,3,6],[0,25,0,1,2,4,7]]}],"name":""}
```
- 示例
```lua
            local tbl = {
                ["abil"] = {
                    {
                        ["i"] = 0,
                        ["t"] = "[星级测试]\\&lt;IMG:3&gt;\\星级:3",
                        ["c"] = 251,
                        ["v"] = {
                            {0,3,1,0,1,0,1},
                            {0,4,1,0,1,0,2},
                            {0,5,1,0,9,2,3},
                            {0,6,1,0,9,2,4},
                            {0,6,1,0,9,2,4},
                            {0,7,1,0,10,3,5},
                            {0,8,1,0,10,3,6},
                            {0,25,0,1,2,4,7},
                        },
                    },
                },
                ["name"] = itemName .. "[锻造 + 1]",
            }
            setitemcustomabil(actor,itemobj,tbl2json(tbl))
            refreshitem(actor,itemobj)
```

| 参数   | 类型   | 描述                                            |
| :----- | :----- | :---------------------------------------------- |
| - abil | object | 自定义属性（0~5）                               |
| i      | number | 索引                                            |
| t      | string | 标题名                                          |
| c      | number | 颜色                                            |
| - - v  | object | 属性条目                                        |
| 1      | number | 颜色                                            |
| 2      | number | 属性ID                                          |
| 3      | number | 属性值                                          |
| 4      | number | 类型 0 数值  1 百分比                           |
| 5      | number | 显示自定义类名称(cfg_custpro_caption表里面的ID) |
| 6      | number | 所在行                                          |
| 7      | number | 索引                                            |
| name   | string | 自定义物品名                                    |

### 绑定自定义装备属性
`changecustomitemabil`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|attrindex  |`integer`         |是   |0    |  属性位置(0~9)每个装备可以自定义10个属性    |
|bindindex  |`integer`         |是   |0    |  绑定类型(0~4)  |
|bindvalue  |`integer`         |是   |0    |  绑定的值    |
|group  |`integer`         |是   |0    |  显示分类位置<br />(0~5 ;为空默认为0)    |

```
    绑定类型(0~4):
    0=标识该属性绑定的颜色值默认读取(属性表:cfg_custpro_caption.xls)里面的颜色
    1=表示该绑定属性表(属性ID:cfg_att_score.xls的属性ID),必须绑定，否则该属性无效，游戏也不会显示
    2=标示该属性绑定自定义属性表:cfg_custpro_caption.xls里面的属性ID
    3=表示该属性是否是百分比属性(0,1) 0不是百分比 1是百分比
    4=属性显示位置(0~9) 如果一行有多个属性,这里位置就写同一行
    
    绑定的值:
    参数4(绑定类型)=0时 绑定属性颜色(0~255) 默认读取(属性表:cfg_custpro_caption.xls)里面的颜色
    参数4(绑定类型)=1时 绑定属性表:cfg_att_score.xls里面的属性ID
    参数4(绑定类型)=2时 绑定自定义属性表:cfg_custpro_caption.xls里面的属性ID
    参数4(绑定类型)=3时 绑定的值(0~1)
    参数4(绑定类型)=4时 显示位置(0~9)
```
```lua
    local itemobj = linkbodyitem(actor,1)
    local itemidx = getiteminfo(actor,itemobj,2)
    local itemName = getstditeminfo(itemidx,1)
    local weizhi = 0
    local attrIndex = 4
    local attrValue = 100
    release_print(itemName,"修改属性",attrIndex .."+" .. attrValue)
    changecustomitemtext(actor, itemobj, "[自定义属性测试]：", 0)
    changecustomitemtextcolor(actor, itemobj, 253, 0)
    changecustomitemabil(actor,itemobj,weizhi,0,214,0)
    changecustomitemabil(actor,itemobj,weizhi,1,attrIndex,0)
    -- changecustomitemabil(actor,itemobj,weizhi,2,1,0)
    -- changecustomitemabil(actor,itemobj,weizhi,3,0,0)
    changecustomitemabil(actor,itemobj,weizhi,4,weizhi,0)
    changecustomitemvalue(actor,itemobj,weizhi,"+",attrValue,0)
    refreshitem(actor,itemobj)
```

### 修改自定义属性值
`changecustomitemvalue`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|attrindex  |`integer`         |是   |0    |  属性位置(0~9)每个装备可以自定义10个属性    |
|operate  |`string`        |是   |    |  操作符：+、-、=  |
|value  |`integer`         |是   |0    |  属性值    |
|group  |`integer`         |是   |0    |  显示分类位置<br />(0~5 ;为空默认为0)    |

### 增加和修改自定义属性分类名称
`changecustomitemtext`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|typename  |`string`       |是   |0    |  分类名称(-1为清空)      |
|group  |`integer`         |是   |0    |  显示分类位置<br />(0~5 ;为空默认为0)    |

### 增加和修改分类名称颜色
`changecustomitemtextcolor`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|color  |`integer`         |是   |0    |  分类颜色(0~255)    |
|group  |`integer`         |是   |0    |  显示分类位置<br />(0~5 ;为空默认为0)    |

### 将物品唯一ID转换成道具表里对应的IDX物品
`changeitemidx`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid       |`integer`       |否   |    |  唯一ID   |
|itemidx  |`integer`       |否   |    |  道具ID    |

### 增加限次使用物品的次数
`addfunitemdura`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid       |`integer`       |否   |    |  唯一ID   |
|num  |`integer`       |否   |    |  次数    |

### 获取物品持久度
`getdura`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid       |`integer`       |否   |    |  唯一ID   |
|result       |`integer`        |否   |    |  持久度  |

### 修改物品持久度
`setdura`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemmakeid       |`integer`       |否   |    |  唯一ID   |
|char  |`string`      |否   |    |  操作符(+ - =)    |
|dura  |`integer`      |否   |    |  持久度    |
```lua
    setdura(actor,itemmakeid,"=",1000)
```

### 修改装备内观Looks值

`setitemlooks`

| 参数    | 类型      | 空   | 默认                | 注释                     |
| :------ | :-------- | :--- | :------------------ | :----------------------- |
| play    | `object`  | 否   |                     | 玩家对象                 |
| itemPos | `integer` | 否   |                     | 装备位置(-2操作物品对象) |
| char    | `string`  | 否   |                     | 操作符(+ - =)            |
| pictrue | `integer` | 否   |                     | 内观图片                 |
| item    | `object`  | 否   | 引擎64_23.08.30新增 | 物品对象                 |
```lua
--根据装备位设置内观Looks值
setitemlooks(actor,1,"=",85)

--根据装备对象设置内观Looks值
setitemlooks(actor,-2,"=",85,itemobj)
```

### 设置物品来源
`setthrowitemly`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|source     |`string`      |否   |    |   json字符串 |
```
source格式
{
    map: "0", //地图号
    source: 5,  //来源：1-GM生成，2-NPC，3-商城，4-NPC商店, 5-怪物掉落，6-系统给与，7-挖矿，8-批量生成，9-宝箱
    mon:"白野猪",  //掉落的怪物
    player:"玩家人物名称",  
    time:"2021-11-11 00:00:00"  //掉落或生成的时间，为空时，设置为系统时间
}
设置来源接口调用后，会将生成的来源数据保存到后端，脚本中给与物品时，会自动绑定。
```

### 设置物品来源（使用物品对象）
`setthrowitemly2`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象  |
|source     |`string`      |否   |    |   json字符串 |
```
source格式同setthrowitemly
```

### 获取物品来源（使用物品对象）
`getthrowitemly`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  物品对象  |
|result     |`string`      |否   |    |   json字符串 |
```
source格式同setthrowitemly
```

------------
## 刀魂系统

### 设置自定义进度条参数
`setcustomitemprogressbar`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|index  |`integer`         |否   |    |   装备精度条索引（0~2）    |
|json  |`string`       |否   |    |   进度条内容，json字符串    |
```lua
    [[
        // json格式，json中各项参数均可以为空：
        {
            open:1,  //0-关闭，1-打开
            show:1,  //0-不显示数值，1-百分比，2-数字
            name:"锻造",  //进度条文本
            color:3,  //进度条颜色，0~255
            imgcount:1,  //图片张数，填1即可
            cur:0,  //当前值
            max:100,  //最大值
            level:0  //级别(0~65535)
        }
    ]]
    local itemobj = linkbodyitem(actor,1)
    local tbl = {
        ["open"] = 1,
        ["show"] = 2,
        ["name"] = "经验值",
        ["color"] = 253,
        ["imgcount"] = 1,
        ["cur"] = 2500,
        ["max"] = 5000,
        ["level"] = 0,
    }
    setcustomitemprogressbar(actor,itemobj,0,tbl2json(tbl))
    refreshitem(actor,itemobj)
```

### 获取自定义进度条参数
`getcustomitemprogressbar`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|index  |`integer`         |否   |    |   装备精度条索引（0~2）    |
|result  |`string`         |否   |    |   进度条内容，json字符串    |

------------

### 装备批量增加附加属性

`setaddnewabil`

| 参数    | 类型      | 空   | 默认 | 注释                     |
| :------ | :-------- | :--- | :--- | :----------------------- |
| play    | `object`  | 否   |      | 玩家对象                 |
| where   | `integer` | 否   |      | 装备位置(-2操作物品对象) |
| opt     | `string`  | 否   |      | 运算符(+,-,=)            |
| attrStr | `string`  | 否   |      | 属性组                   |
| item    | `object`  | 否   |      | 物品对象                 |
```lua
--根据装备位加属性
setaddnewabil(actor,1,"+","3#3#2|3#4#10|3#4#2|3#5#10|3#23#2|3#74#10")

--根据物品对象加属性
setaddnewabil(actor,-2,"+","3#3#2|3#4#10|3#4#2|3#5#10|3#23#2|3#74#10",itemobj)
```

### 获取人物身上装备属性值命令

`getitemattidvalue`

| 参数   | 类型      | 空   | 默认 | 注释                                  |
| :----- | :-------- | :--- | :--- | :------------------------------------ |
| play   | `object`  | 否   |      | 玩家对象                              |
| model  | `integer` | 否   |      | 类型(1，装备表里基础数据 2，附加属性) |
| attrID | `integer` | 否   |      | 属性ID                                |
| where  | `integer` | 否   |      | 装备位置(-2操作物品对象)              |
| item   | `object`  | 否   |      | 物品对象                              |
```lua
--根据装备位获取属性
local attr_str = getitemattidvalue(actor,2,4,1)

--根据物品对象获取属性
local attr_str = getitemattidvalue(actor,2,4,-2,itemobj)
```

------------

## 宝石相关
### 装备开孔
`drillhole`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|holejson  |`string`       |否   |    |  开孔相关，json字符串，支持0~9共10个孔    |
```lua
    local config = {}
    for i = 0, 9 do
        config["hole"..i] = 1 -- 0-不开孔，1-开孔
    end
    drillhole(actor,itemobj,tbl2json(config))
    release_print("开孔信息1",getdrillhole(actor,itemobj))

    -- * 不要求所有空数据都传送，允许只传指定孔的字符串，例如：
    local config = {}
    config.hole0 = 1 -- 0-不开孔，1-开孔
    drillhole(actor,itemobj,tbl2json(config))
    release_print("开孔信息2",getdrillhole(actor,itemobj))
```

### 获取装备开孔数据
`getdrillhole`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|result   |`string`        |否   |    |  开孔相关，json字符串，支持0~9共10个孔    |
```
返回的json字符串参考装备开孔
```

### 装备镶嵌钻石
`socketableitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|hole     |`integer`       |否   |    |  装备开孔序号，0~9   |
|item     |`integer`       |否   |    |  镶嵌钻石的index（装备表总的Index）   |

### 获取装备钻石镶嵌情况
`getsocketableitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|item     |`object`        |否   |    |  装备对象   |
|result   |`string`        |否   |    |  开孔相关，json字符串，支持0~9共10个孔    |
```json
socketableitem 镶嵌宝石，传入json
getsocketableitem 返回镶嵌宝石的json
{
    socket0: 20333,  //第0个孔位置，20333-对应宝石的Index，
    socket1: 0,  //第1个孔位置，0-未镶嵌宝石
    socket2: 0,
    socket3: -1,  //第3个孔位置，-1-未打孔
    socket4: -1,
    socket5: -1,
    socket6: 0,
    socket7: -1,
    socket8: -1,
    socket9: -1
}

```
### 设置物品特效

`setitemeffect`

| 参数        | 类型      | 空   | 默认                | 注释                      |
| :---------- | :-------- | :--- | :------------------ | :------------------------ |
| play        | `object`  | 否   |                     | 玩家对象                  |
| itemPos     | `integer` | 否   |                     | 装备位置(-2操作物品对象)  |
| bageffectid | `integer` | 否   |                     | 背包特效编号              |
| ineffectid  | `integer` | 否   |                     | 内观特效编号              |
| order1      | `integer` | 否   |                     | 背包特效层级<br />0=前;1=后 |
| order2      | `integer` | 否   |                     | 内观特效层级<br />0=前;1=后 |
| item        | `object`  | 否   | 引擎64_23.08.30新增 | 物品对象                  |
```lua
--根据装备位设置特效
setitemeffect(actor,1,5111,6063,1,1)

--根据物品对象设置特效
setitemeffect(actor,-2,6307,6063,nil,nil,itemobj)
```

------------

## 根据物品获取Json

`getitemjson`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|item     |`object`      |否   |    |  物品对象 |
|result     |`string`        |否   |    |  json字符串   |

```json
{
    "MakeIndex":xxxx,
    "Idx":xxxx,
    "Name":xxxx,
    "Dura":xxxx,
    "DuraMax":xxxx,
    "Overlap":xxxx,
    "AddValue0":xxxx,
    "AddValue1":xxxx,
    "ExAbil":xxxx
}
```
```lua
    local json = getitemjson(item)
```

## 根据json字符串给物品
`giveitembyjson`

| 参数   | 类型     | 空   | 默认                | 注释           |
| :----- | :------- | :--- | :------------------ | :------------- |
| actor  | `object` | 否   |                     | 玩家对象       |
| json   | `string` | 否   |                     | json字符串     |
| desc   | `string` | 是   | 引擎64_24.05.23新增 | 描述           |
| result | `object` | 否   |                     | 生成的物品对象 |

```json
{
    "MakeIndex":xxxx,
    "Idx":xxxx,
    "Name":xxxx,
    "Dura":xxxx,
    "DuraMax":xxxx,
    "Overlap":xxxx,
    "AddValue0":xxxx,
    "AddValue1":xxxx,
    "ExAbil":xxxx
}
*注 : 根据json字符串给的物品，将会生成新的MakeIndex
```

## 根据物品获取前端显示的Json

`getitemjsonex`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释       |
| :----- | :------- | :--- | :--- | :--------- |
| item   | `object` | 否   |      | 物品对象   |
| result | `string` | 否   |      | json字符串 |
```lua
function main(actor)
    local itemobj = linkbodyitem(actor,1)
    local itemjson = getitemjsonex(itemobj)
    str = [[&lt;ItemShow|x=0.0|y=0.0|width=70|height=70|itemdata=]]..itemjson..[[|showtips=1|bgtype=1|color=250&gt;]]
    say(actor,itemobj)
end
```

------------

### 关闭指定装备对比提示
`nothintitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|actor     |`object`      |否   |    |  玩家对象 |
|order     |`integer`      |否   |    |  1=物品唯一ID 2=物品IDX 3=物品名称 |
|str      |`string`        |否   |    |  参数1的值   |
```
    nothintitem(actor,3,"木剑")
```

### 设置物品绑定状态

`setitemstate`

| 参数  | 类型      | 空   | 默认 | 注释                           |
| :---- | :-------- | :--- | :--- | :----------------------------- |
| item  | `object`  | 否   |      | 物品对象                       |
| bind  | `integer` | 否   |      | 绑定类型(0-8,21)               |
| state | `integer` | 否   |      | 绑定状态<br />0=不绑定<br />1=绑定 |
```lua
local config = {
    [0] = "禁止扔",
    [1] = "禁止交易",
    [2] = "禁止存",
    [3] = "禁止修",
    [4] = "禁止出售",
    [5] = "禁止爆出",
    [6] = "丢弃消失",
    [7] = "死亡必爆(死亡爆出来后，该属性就会删除，在捡起来戴上，就没有死亡必爆了)",
    [8] = "禁止摆摊或上架拍卖行",
    [21] = "爆出消失[引擎64_24.03.14新增]",
}
-- 捡取任意物品前触发
function pickupitemfrontex(actor, itemobj)
    for i, v in pairs(config) do
        setitemstate(itemobj,i,1)
        local state1 = getiteminfo(actor,itemobj,6)
        local state2 = checkitemstate(itemobj,i)
        release_print("状态:",i,v,state1,state2)
    end
end
```

### 判断绑定状态
`checkitemstate`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释                           |
| :----- | :-------- | :--- | :--- | :----------------------------- |
| item   | `object`  | 否   |      | 物品对象                       |
| bind   | `integer` | 否   |      | 绑定类型(0-8,21)               |
| result | `bool`    | 否   |      | true = 绑定<br /> false = 非绑定 |

### 判定物品是否极品

`isitemjp`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|item     |`object`      |否   |    |  物品对象 |
|result     |`bool`      |否   |    | true = 是极品<br /> false = 不是极品 |

### 判断角色是否有该物品
`hasitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|actor     |`object`      |否   |    |  玩家对象 |
|itemMakeIndex     |`object`      |否   |    |  物品唯一id |
|result     |`integer`      |否   |    |返回值<br /> 0-装备，1-背包<br />2-仓库, -1-不存在 |

### 设置装备的元素属性

`setnewitemvalue`

| 参数    | 类型      | 空   | 默认                | 注释                     |
| :------ | :-------- | :--- | :------------------ | :----------------------- |
| play    | `object`  | 否   |                     | 玩家对象                 |
| itemPos | `integer` | 否   |                     | 装备位置(-2操作物品对象) |
| iAttr   | `integer` | 否   |                     | 属性                     |
| sFlag   | `string`  | 否   |                     | 比较符(=+-)              |
| iValue  | `integer` | 否   |                     | 数值(1-100)，百分比      |
| item    | `object`  | 否   | 引擎64_23.08.30新增 | 物品对象                 |
```lua
--根据装备位设置元素属性
setnewitemvalue(actor,1,1,"+",1)

--根据物品对象设置元素属性
setnewitemvalue(actor,-2,1,"+",100,itemobj)
```

### 获取物品的附加属性
`getnewitemaddvalue`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|itemobj     |`object`      |否   |    |  物品对象 |
|value    |`integer`       |否   |    |  元素属性<br /> 0:暴击几率<br /> 1攻击伤害<br /> 2:物理伤害减少<br /> 3:魔法伤害减少<br /> 4:忽视目标防御<br /> 5:所有伤害反弹<br /> 6:目标爆率<br /> 7:人物体力增加<br /> 8:人物魔力增加<br /> 11:暴击伤害<br />    |

### 修复所有装备
`repairall`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |  玩家对象 |

```lua
    [[
        需要在npc脚本中使用,且文件头需设置itemstype表储存需要修复的装备位置
        Mir200\Envir\Market_Def\第一大陆\装备修复-3.lua
    ]]
    itemstype = {1,2,3,4,5,6,7,8,9,10}
    function main(actor)
        local msg =[[&lt;设置持久/@chijiu&gt;\&lt;一键修复/@xiufu&gt;]]
        say(actor,msg)
    end
    function chijiu(actor)
        local itemobj = linkbodyitem(actor,1)
        local itemMakeId = getiteminfo(actor,itemobj,1)
        setdura(actor,itemMakeId,"=",2000)
    end
    function xiufu(actor)
        repairall(actor)
    end
```

### 调整人物身上物品装备名字颜色
`changeitemnamecolor`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|item     |`object`        |否   |    |  物品对象   |
|color     |`integer`      |否   |    |颜色(0-255)颜色=0时恢复默认颜色 |

### 检测装备名字的颜色
`getitemnamecolor`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|item     |`object`        |否   |    |  物品对象   |
|result |`integer`         |是   |0    |   返回颜色值    |

### 修改物品/装备名称

`changeitemname`

| 参数     | 类型      | 空   | 默认                | 注释                     |
| :------- | :-------- | :--- | :------------------ | :----------------------- |
| play     | `object`  | 否   |                     | 玩家对象                 |
| itemPos  | `integer` | 否   |                     | 装备位置(-2操作物品对象) |
| itemName | `string`  | 否   |                     | 装备名字                 |
| item     | `object`  | 否   | 引擎64_23.08.30新增 | 物品对象                 |
```lua
--根据装备位改名
changeitemname(actor,1,"装备改名1")

--根据物品对象改名
changeitemname(actor,-2,"装备改名2",itemobj)

--怪物物品掉落回调接口
function mondropitemex(actor, itemobj, monobj, x, y)
    [[引擎64_23.10.24支持刷新地面物品的名字,之前引擎需要调用TXT命令]]
    changeitemname(actor,-2,"测试道具_lua22",itemobj)
    changeitemnamecolor(actor,itemobj,199)
    refreshitem(actor,itemobj)
    
    [[之前的引擎需要调用TXT命令]]
    -- callscriptex(actor,"LINKPICKUPITEM")
    -- callscriptex(actor,"ChangeItemName",-1,"测试道具_txt2")
    -- callscriptex(actor,"changeitemnamecolor",-1,200)
    -- callscriptex(actor,"SENDUPGRADEITEM")
end
```

### 获取物品原始各项数据库字段值参数

`getdbitemfieldvalue`

| 参数             | 类型               | 空   | 默认 | 注释            |
| :--------------- | :----------------- | :--- | :--- | :-------------- |
| itemIdx/itemName | `integer`/`string` | 否   |      | 物品ID/物品名称 |
| fieldName        | `string`           | 否   |      | 字段名          |

```lua
    local config = {
        {"Name", "1列"},
        {"StdMode", "2列"},
        {"Shape", "3列"},
        {"Weight", "4列"},
        {"Anicount", "5列"},
        {"Source", "6列"},
        -- {"Reserved", "7列"},      --接口无法获取,服务器不读取
        {"Looks", "8列"},
        {"DuraMax", "9列"},
        {"Attribute", "10列"},
        {"Need", "11列"},
        {"NeedLevel", "12列"},
        {"NeedLevelParam", "12列","NeedLevel#后的数据"},
        {"Price", "13列"},
        {"Color", "14列"},
        {"OverLap", "15列"},        --装备无法获取堆叠数量,固定返回值为0
        -- {"Suit", "16列"},        --当前引擎已取消16列
        {"Article", "17列"},
        {"Job", "18列"},
        {"effectParam", "19列"},
        -- {"Desc", "20列"},        --接口无法获取,服务器不读取
        -- {"pickset", "21列"},     --接口无法获取,服务器不读取
        -- {"guangzhu", "22列"},    --接口无法获取,服务器不读取
        -- {"auctionby", "23列"},   --接口无法获取,服务器不读取
        {"sEffect", "24列"},
        {"bEffect", "25列"},
        {"rizhi", "27列"},          --引擎2024.03.14修复无法获取问题
        {"zblmtkz", "28列"},        --引擎2024.03.14修复无法获取问题
        {"ITEMPAEAM1", "29列"},
        {"ITEMPAEAM2", "30列"},
        -- {"Comparison", "31列"},  --接口无法获取,服务器不读取
        {"suit", "32列"},           --32列的suitid更名为suit
        {"Insurance", "33列"},
        -- {"pickCondition", "34列"},--接口无法获取,服务器不读取
    }
    for _, v in ipairs(config) do
        release_print("对应item/equip表",v[2],v[1]..(v[3] or ""),getdbitemfieldvalue("20000元宝", v[1]))
    end
```

### 获取背包物品数量

`getbagitemcount`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|itemname     |`string`      |否   |    |  物品名称 |
|model     |`string`      |否   |  引擎64_23.10.24新增  | 物品绑定状态<br />0=忽略;<br />1=非绑定;<br />2=绑定; |
|result     |`integer`      |否   |    |   返回值，对应物品的数量 |
```lua
    local itemNum = getbagitemcount(actor,"木剑")
    release_print("itemNum",itemNum)
```

## 根据索引返回背包物品信息

&gt; 删物品需判断是否成功

`getiteminfobyindex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|index    |`integer`       |否   |    |    索引号,0开始   |
|result       |`object`        |否   |    |  物品对象  |

### 整理背包里的物品

`refreshbag`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 获取仓库所有物品

`getstorageitems`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|result     |`table`      |否   |    |   物品对象列表 |

### 获取背包物品列表

`getbagitems`

| 参数     | 类型      | 空   | 默认                | 注释                                     |
| :------- | :-------- | :--- | :------------------ | :--------------------------------------- |
| player   | `object`  | 否   |                     | 玩家对象                                 |
| itemName | `string`  | 否   | 引擎64_23.10.24新增 | 道具名字                                 |
| isbind   | `integer` | 否   | 引擎64_23.10.24新增 | 是否绑定<br />0=忽略<br />1=非绑定<br />2=绑定 |
| result   | `table`   | 是   |                     | 道具列表                                 |
```lua
    local items
    if sMsg == "1" then
        release_print("获取背包所有物品")
        items = getbagitems(actor)
    elseif sMsg == "2" then
        release_print("获取背包所有非绑定物品")
        items = getbagitems(actor,nil,1)
    elseif sMsg == "3" then
        release_print("获取背包所有绑定物品")
        items = getbagitems(actor,nil,2)
    elseif sMsg == "4" then
        release_print("获取背包非绑定木剑")
        items = getbagitems(actor,"木剑",1)
    elseif sMsg == "5" then
        release_print("获取背包绑定木剑")
        items = getbagitems(actor,"木剑",2)
    elseif sMsg == "6" then
        release_print("获取背包所有木剑")
        items = getbagitems(actor,"木剑")
    end
    if type(items) ~= "table" then return end
    for i, itemobj in pairs(items or {}) do
        local isBind = getiteminfo(actor,itemobj,6)
        local itemName = getiteminfo(actor,itemobj,7)
        release_print("item["..i.."]",itemName,isbind)
    end
```

------------

### 从装备位扣除物品

`delbodyitem`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认                | 注释                            |
| :----- | :-------- | :--- | :------------------ | :------------------------------ |
| player | `object`  | 否   |                     | 玩家对象                        |
| where  | `integer` | 否   |                     | 装备位                          |
| desc   | `string`  | 是   | 引擎64_24.05.23新增 | 描述                            |
| result | `bool`    | 是   |                     | true=扣除成功<br />false=扣除失败 |

### 根据StdMode获取装备位

`getposbystdmode`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释        |
| :------ | :-------- | :--- | :--- | :---------- |
| stdMode | `integer` | 否   |      | 道具StdMode |
| result  | `integer` | 是   |      | 装备位      |

### 批量检测背包物品

`checkitems`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                                                        |
| :------ | :-------- | :--- | :--- | :---------------------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                                    |
| itemStr | `string`  | 否   |      | 物品名称#物品数量&amp;物品名称#物品数量 (&amp;=和的意思)            |
| isBind  | `integer` | 否   |      | 0=不检测;<br /> 1.非绑定<br />2.绑定                            |
| model   | `integer` | 否   |      | 参数2中的物品名称是ID还是道具名称<br />0=道具名称<br />1=道具ID |
| result  | `bool`    | 否   |      | 是否满足条件                                                |
```lua
    local item_str = "屠龙#3&amp;木剑#4"
    if checkitems(actor,item_str ,0 ,0) then
        local bool = takes(actor,item_str,0,0)
        LOGPrint("是否扣除成功,takes",bool)
    end
```

### 批量拿走背包物品

`takes`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认                | 注释                                                         |
| :------ | :-------- | :--- | :------------------ | :----------------------------------------------------------- |
| play    | `object`  | 否   |                     | 玩家对象                                                     |
| itemStr | `string`  | 否   |                     | 物品#物品数量&amp;物品#物品数量 (&amp;=和的意思)                     |
| varName | `string`  | 否   |                     | 存入变量名,判断扣除道具中是否有绑定的<br />0=非绑定<br /> 1=绑定 |
| model   | `integer` | 否   |                     | 参数2中的传入的物品代表名称还是ID<br />0=道具名称<br />1=道具ID  |
| order   | `integer` | 否   |                     | 0=按照默认顺序<br />1=优先扣除绑定道具                         |
| desc    | `string`  | 是   | 引擎64_24.05.23新增 | 描述                                                         |
| result  | `bool`    | 否   |                     | 是否扣除成功                                                 |

```lua
    local varName = "N0"
    local bool = takes(actor,item_str,varName,0,0,"GM删物品")
    release_print("takes是否扣除成功:",bool)
    release_print("判断扣除道具中是否有绑定",getplaydef(actor, varName))
```

### 扣除角色穿戴的装备

`takew`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数     | 类型      | 空   | 默认                | 注释                                                                            |
| :------- | :-------- | :--- | :------------------ | :------------------------------------------------------------------------------ |
| play     | `object`  | 否   |                     | 玩家对象                                                                        |
| itemName | `string`  | 否   |                     | 装备名称                                                                        |
| num      | `integer` | 否   |                     | 扣除物品数量                                                                    |
| desc     | `string`  | 是   | 引擎64_24.05.23新增 | 描述                                                                            |
| result   | `bool`    | 否   |                     | 是否扣除成功<br />传入数量大于1时返回值不准确<br />使用前注意先判断是否满足扣除条件 |
```lua
    local bool = takew(actor,"力量戒指",2)
    LOGPrint("是否扣除成功,takew",bool)
```

### 批量给予物品

`gives`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型     | 空   | 默认 | 注释                                                      |
| :------ | :------- | :--- | :--- | :-------------------------------------------------------- |
| actor   | `object` | 否   |      | 玩家对象                                                  |
| itemStr | `string` | 否   |      | 物品参数<br />物品名称#数量#绑定状态&amp;物品名称#数量#绑定状态 |
| desc    | `string` | 否   |      | 描述                                                      |
```lua
    local itemStr = "木剑#1#128&amp;开天#1"
    gives(actor,itemStr,"[gives]刷物品测试")
```

### 检测身上佩戴的装备

`checkitemw`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数      | 类型      | 空   | 默认 | 注释     |
| :-------- | :-------- | :--- | :--- | :------- |
| actor     | `object`  | 否   |      | 玩家对象 |
| item_name | `string`  | 否   |      | 装备名称 |
| item_num  | `integer` | 是   | 1    | 检测数量 |
| result    | `bool`    | 否   |      | 是否穿戴 |
```lua
    if not checkitemw(actor,"金手镯",2) then
        say(actor,"请先佩戴两个金手镯~")
        return
    end
```

### 返回前端面板消息[合成系统]

`sendactionofjson`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数  | 类型     | 空   | 默认 | 注释      |
| :---- | :------- | :--- | :--- | :-------- |
| actor | `object` | 否   |      | 玩家对象  |
| idx   | `string` | 否   |      | 合成表idx |
| json  | `string` | 否   |      | json信息  |
```lua
function g_compounditem10000(actor,idx)
    local data_json = string.format('{"action":"event","data":{"recog":%s,"param1":%s}}',"-2",idx)
    sendactionofjson(actor,idx,data_json)
end
```
# 行会操作


## 触发

### 创建行会前触发
`checkbuildguild`

| 参数   | 类型     | 空   | 默认 | 注释                            |
| :----- | :------- | :--- | :--- | :------------------------------ |
| play   | `object` | 否   |      | 玩家对象                        |
| name   | `string` | 否   |      | 行会名                          |
| result | `bool`   | 是   |      | true=允许创建<br />false=阻止创建 |

### 创建行会时触发
`loadguild`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| play  | `object` | 否   |      | 玩家对象 |
| guild | `object` | 否   |      | 行会对象 |

### 加入行会前触发

`guildaddmember`

&gt; 需要申请入会的情况,会触发两次:申请时触发一次,会长同意申请后再触发一次

| 参数   | 类型     | 空   | 默认 | 注释                            |
| :----- | :------- | :--- | :--- | :------------------------------ |
| play   | `object` | 否   |      | 玩家对象                        |
| guild  | `object` | 否   |      | 行会对象                        |
| name   | `stirng` | 否   |      | 行会名称                        |
| result | `bool`   | 是   |      | true=允许加入<br />false=阻止加入 |

### 加入行会后触发

`guildaddmemberafter`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| play  | `object` | 否   |      | 玩家对象 |
| guild | `object` | 否   |      | 行会对象 |
| name  | `stirng` | 否   |      | 行会名称 |

### 退出行会前触发

`guilddelmemberbefore`

| 参数   | 类型     | 空   | 默认 | 注释                            |
| :----- | :------- | :--- | :--- | :------------------------------ |
| play   | `object` | 否   |      | 玩家对象                        |
| result | `bool`   | 是   |      | true=允许退出<br />false=阻止退出 |

### 退出行会时触发
`guilddelmember`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 解散行会前
`guildclosebefore`

| 参数   | 类型     | 空   | 默认 | 注释                            |
| :----- | :------- | :--- | :--- | :------------------------------ |
| play   | `object` | 否   |      | 玩家对象                        |
| result | `bool`   | 是   |      | true=允许解散<br />false=阻止解散 |

### 解散行会

`guildclose`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |

### 请求行会联盟前触发

`guildapplybefore`

| 参数      | 类型      | 空   | 默认 | 注释                              |
| :-------- | :-------- | :--- | :--- | :-------------------------------- |
| play      | `object`  | 否   |      | 发起请求玩家对象                  |
| guildName | `string`  | 否   |      | 行会名字                          |
| time      | `integer` | 否   |      | 结盟时长(小时)                    |
| moneyType | `integer` | 否   |      | 货币类型                          |
| moneyNum  | `integer` | 否   |      | 货币数量                          |
| result    | `bool`    | 是   |      | true=允许发起<br />false=不允许发起 |
```lua
function guildapplybefore(actor,guildName,time,moneyType,moneyNum)
    return true
end
```

### 掌门踢出行会成员前触发

`guildchiefdelmember`

| 参数   | 类型     | 空   | 默认 | 注释                          |
| :----- | :------- | :--- | :--- | :---------------------------- |
| play   | `object` | 否   |      | 玩家对象                      |
| userID | `string` | 否   |      | 被踢玩家userID                |
| result | `bool`   | 是   |      | true=允许踢<br />false=不允许踢 |
```lua
function guildchiefdelmember(actor,userID)
    return true
end

```

## 接口

### 创建行会
`buildguild`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| play | `object` | 否   |      | 玩家对象 |
| name | `string` | 否   |      | 行会名   |

### 获取人物所在行会成员数量
`getguildmembercount`

| 参数   | 类型      | 空   | 默认 | 注释                 |
| :----- | :-------- | :--- | :--- | :------------------- |
| play   | `object`  | 否   |      | 玩家对象             |
| result | `integer` | 否   |      | 人物所在行会成员数量 |

### 设置行会成员人数上限
`changeguildmemberlimit`

| 参数  | 类型      | 空   | 默认 | 注释            |
| :---- | :-------- | :--- | :--- | :-------------- |
| guild | `object`  | 否   |      | 行会对象        |
| char  | `string`  | 否   |      | (操作符 + - = ) |
| num   | `integer` | 否   |      | 数量            |

### 获取玩家所在的行会对象
`getmyguild`

| 参数   | 类型     | 空   | 默认 | 注释                          |
| :----- | :------- | :--- | :--- | :---------------------------- |
| play   | `object` | 否   |      | 玩家对象                      |
| result | `object` | 否   |      | 行会对象<br />没有行会返回`"0"` |

### 搜索行会
`findguild`

| 参数   | 类型      | 空   | 默认 | 注释                             |
| :----- | :-------- | :--- | :--- | :------------------------------- |
| index  | `integer` | 否   |      | 搜索关键词：0-行会ID，1-行会名称 |
| key    | `string`  | 否   |      | 搜索关键词                       |
| result | `object`  | 否   |      | 行会对象                         |

### 获取行会信息
`getguildinfo`

| 参数   | 类型      | 空   | 默认 | 注释       |
| :----- | :-------- | :--- | :--- | :--------- |
| guild  | `object`  | 否   |      | 行会对象   |
| index  | `integer` | 否   |      | 索引       |
| result | `string`  | 否   |      | 获取的结果 |

```
索引含义:
0-行会ID
1-行会名称
2-行会公告
3-行会成员名单（返回table）
4-行会掌门人名称
5-获取行会人数上限[引擎64_23.10.24新增]
```

### 设置行会信息
`setguildinfo`

| 参数  | 类型      | 空   | 默认 | 注释         |
| :---- | :-------- | :--- | :--- | :----------- |
| guild | `object`  | 否   |      | 行会对象     |
| index | `integer` | 否   |      | 索引         |
| value | `string`  | 否   |      | 要设置的内容 |

```
索引含义：
  0-行会公告
```

### 获取所有行会对象
`getallguild`

| 参数   | 类型  | 空   | 默认 | 注释         |
| :----- | :---- | :--- | :--- | :----------- |
| return | `tbl` | 否   |      | 返回行会列表 |

### 加入行会
`addguildmember`

| 参数       | 类型     | 空   | 默认 | 注释     |
| :--------- | :------- | :--- | :--- | :------- |
| player     | `object` | 否   |      | 玩家对象 |
| guild_name | `string` | 否   |      | 行会名   |

### 退出行会
`delguildmember`

|参数|类型|空|备注|注释|
|:----    |:-------    |:--- |---|------      |
|any     |`object/string`      |否   |    |玩家对象/玩家名/唯一ID |
|guild_name     |`string`      |否   |    |   行会名 |
|type     |`integer`      |否   |   引擎64_23.06.28新增 |   参数1类型:<br />0 = 参数1填玩家对象;<br />1 = 参数1填玩家名字;<br />2 = 参数1填玩家唯一ID;<br />唯一id可用于踢离线玩家,不填默认为0 |

### 设置行会成员在行会中的职位
`setplayguildlevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player     |`object`      |否   |    |玩家对象 |
|pos     |`integer`      |否   |    |   在行会中的职位<br />1：会长;<br />2：副会长;<br />3：行会成员1;<br />4：行会成员2;<br />5：行会成员3;<br /> |
|return     |`boolean `    |否   |    | true:设置成功<br />false:设置失败 |

### 获取行会成员在行会中的职位
`getplayguildlevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player     |`object`      |否   |    |玩家对象 |
|return     |`integer`      |否   |    |   在行会中的职位<br />1：会长;<br />2：副会长;<br />3：行会成员1;<br />4：行会成员2;<br />5：行会成员3;<br />-1:获取失败; |

### 改变行会名称

`changeguildname`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数         | 类型     | 空   | 默认 | 注释             |
| :----------- | :------- | :--- | :--- | :--------------- |
| actor        | `string` | 否   |      | 玩家对象         |
| guildName    | `string` | 否   |      | 需要改名的行会名 |
| newGuildName | `string` | 否   |      | 新的行会名字     |

```lua
--行会改名成功
function changeguildnameok(...)
    LOGPrint("changeguildnameok,成功",...)
end
--行会改名失败,model:0=参数错误;1=原行会找不到;2=名字不合法;3=新名字重复
function changeguildnamefail(guild,model,...)
    LOGPrint("changeguildnamefail,失败",getbaseinfo(guild,1),"model:"..model,...)
end

changeguildname(actor,guildName,newName)
```

### 接口发起行会战

`setguildwar`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数       | 类型      | 空   | 默认 | 注释         |
| :--------- | :-------- | :--- | :--- | :----------- |
| guildName1 | `string`  | 否   |      | 宣战行会名字 |
| guildName2 | `string`  | 否   |      | 敌对行会名字 |
| time       | `integer` | 否   |      | 时间(分)     |
| result     | `bool`    | 否   |      | 是否发起成功 |
```lua
    local bool = setguildwar(guildName_1,guildName_2,30)
```

### 判断行会之间是否宣战

`iswarguild`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数       | 类型     | 空   | 默认 | 注释              |
| :--------- | :------- | :--- | :--- | :---------------- |
| guildName1 | `string` | 否   |      | 行会名字/行会对象 |
| guildName2 | `string` | 否   |      | 行会名字/行会对象 |
| result     | `bool`   | 否   |      | 是否宣战          |
```lua
    --传入行会对象
    local bool_1 = iswarguild(guild_1,guild_2)
    --传入行会名称
    local bool_2 = iswarguild(guildName_1,guildName_2)
    LOGPrint("是否是宣战关系",bool_1,bool_2)
```

### 判断行会之间是否结盟

`isallyguild`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数       | 类型     | 空   | 默认 | 注释              |
| :--------- | :------- | :--- | :--- | :---------------- |
| guildName1 | `string` | 否   |      | 行会名字/行会对象 |
| guildName2 | `string` | 否   |      | 行会名字/行会对象 |
| result     | `bool`   | 否   |      | 是否宣战          |
```lua
    local bool_1 = isallyguild(guild_1,guild_2)
    local bool_2 = isallyguild(guildName_1,guildName_2)
    LOGPrint("是否是结盟关系",bool_1,bool_2)
```
# 组队操作



## 触发

### 创建组队前触发

`startgroup`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| actor1 | `object` | 否   |      | 玩家对象 |
```lua
[[创建组队前,使用creategroupfail接口阻止创建]]
function startgroup(actor)
    if getbaseinfo(actor,6) &lt; 50 then
        say(actor,"50级后才可组队")
        creategroupfail(actor)
        [[23.08.30前需要调用TXT命令打断,callscriptex(actor,"creategroupfail")]]
        return
    end
end
```

### 创建组队后触发

`groupcreate`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| actor1 | `object` | 否   |      | 玩家对象 |

### 添加组队成员触发

`groupaddmember`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| actor1 | `object` | 否   |      | 玩家对象 |
```lua
--允许主动申请加入队伍成员入队
function groupaddmember(actor)
    say(actor,"被允许进组的玩家"..getplaydef(actor,"S0"))
end
```

### 邀请组队前触发

`invitegroup`

| 参数   | 类型      | 空   | 默认 | 注释         |
| :----- | :-------- | :--- | :--- | :----------- |
| actor1 | `object`  | 否   |      | 发起邀请对象 |
| actor2 | `object`  | 否   |      | 被邀请对象   |
| result | `integer` | 否   |      | 是否允许邀请 |
```lua
function invitegroup(actor,role)
    if getbaseinfo(role,6) &lt; 50 then
        say(actor,"被邀请玩家等级不到50级")
        return false
    end
    return true
end
```

### 离开队伍时触发(退组)

`leavegroup`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 退组玩家对象 |

### 删除组队成员触发

`groupdelmember`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 队长对象 |
```lua
--队长删除小组成员
--actor     队长人物对象
function groupdelmember(actor)
    say(actor,"被踢玩家名"..getplaydef(actor,"S0"))
end
```

### 组队杀死怪物时触发

`groupkillmon`

| 参数    | 类型     | 空   | 默认                | 注释     |
| :------ | :------- | :--- | :------------------ | :------- |
| actor   | `object` | 否   |                     | 玩家对象 |
| monName | `string` | 否   | 引擎64_24.08.07新增 | 怪物名字 |
```lua
--组队杀死怪物(同地图内成员每人触发一次)
function groupkillmon(actor,monName)
    say("组队杀死怪物时触发", getbaseinfo(actor, 1),monName)
end
```

------------

## 接口

### 创建队伍
`creategroup`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | ---- | -------- |
| play | `object` | 否   |      | 玩家对象 |

### 添加队员
`addgroupmember`

| 参数     | 类型     | 空   | 默认 | 注释       |
| :------- | :------- | :--- | ---- | ---------- |
| play     | `object` | 否   |      | 玩家对象   |
| memberId | `string` | 否   |      | 组员UserId |

### 删除队员
`delgroupmember`

| 参数     | 类型     | 空   | 默认 | 注释       |
| :------- | :------- | :--- | ---- | ---------- |
| play     | `object` | 否   |      | 玩家对象   |
| memberId | `string` | 否   |      | 组员UserId |

### 获取队员列表
`getgroupmember`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | ---- | -------- |
| play   | `object` | 否   |      | 玩家对象 |
| result | `table`  | 否   |      | 队员列表 |


# 怪物相关


### 刷怪
`genmon`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mapid     |`string`      |否   |    |   地图id |
|x     |`integer`      |否   |    |  坐标X |
|y     |`integer`      |否   |    |   坐标Y |
|monname     |`string`      |否   |    |   怪物名称 |
|range     |`integer`      |否   |    |   范围 |
|count     |`integer`      |否   |    |   数量 |
|color     |`integer`      |否   |    |   颜色(0~255) |
|result     |`table`      |否   |    |   返回怪物列表 |
```lua
    genmon(0,289,613,"稻草人",10,10)
```

### 刷怪(拓展)
`genmonex`

| 参数        | 类型             | 空   | 默认                | 注释                                               |
| :---------- | :--------------- | :--- | :------------------ | :------------------------------------------------- |
| mapid       | `string`         | 否   |                     | 地图id                                             |
| x           | `integer`        | 否   |                     | 坐标X                                              |
| y           | `integer`        | 否   |                     | 坐标Y                                              |
| monname     | `string`         | 否   |                     | 怪物名称                                           |
| range       | `integer`        | 否   |                     | 范围                                               |
| count       | `integer`        | 否   |                     | 数量                                               |
| owner       | `integer/object` | 否   |                     | 归属对象<br />填0则无指定归属                        |
| color       | `integer`        | 否   |                     | 颜色(0~255)                                        |
| showName    | `string`         | 否   |                     | 怪物自定义名称                                     |
| isFilt      | `integer`        | 否   |                     | 是否过滤数字<br />0过滤，1不过滤                     |
| countryName | `string`         | 否   | 引擎64_23.12.07新增 | 国家名称                                           |
| nAttack     | `integer`        | 否   | 引擎64_23.12.07新增 | 是否可攻击同国家的玩家<br />0=不可以<br />1=可以       |
| nNatMonPk   | `integer`        | 否   | 引擎64_23.12.07新增 | 不同国家怪物是否可PK<br />0=不可以<br />1=可以         |
| nPlayerPk   | `integer`        | 否   | 引擎64_23.12.07新增 | 人物是否可以攻击相同国家怪物<br />0=可以<br />1=不可以 |
| nNg         | `integer`        | 否   | 引擎64_23.12.07新增 | 是否是内功怪<br />0=普通怪<br />1=内功怪               |
| result      | `table`          | 否   |                     | 返回怪物列表                                       |
```lua
    genmonex(3,333,333,"神兽",1,2,0,255,"神兽\\(新)",1)

    local countryName = "华夏"
    local mons = genmonex(mapID,x,y,"练功稻草人",10,5,0,255,string.format("稻草人[%s]",countryName),1,countryName,1,1,1,1)
    for _, mon in ipairs(mons or {}) do
        release_print("========================")
        release_print("monName",getbaseinfo(mon,1,0))
        release_print("monPosM",getbaseinfo(mon,1,4),getbaseinfo(mon,1,5))
    end
```

### 杀怪1
`killmonsters`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mapid     |`string`      |否   |    |   地图id |
|monname     |`string`      |否   |    |怪物全名，空 或者 * 杀死全部 |
|count     |`integer`      |否   |    |   数量，0所有 |
|drop     |`bool`      |否   |    |   是否掉落物品，true掉落 |

```lua
function main(self)
    killmonsters(0,"*",5,true)
end
```

### 杀怪2
`killmonbyobj`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|mon     |`object`      |否   |    |   怪物对象 |
|drop     |`bool`      |否   |    |   是否掉落物品，true掉落 |
|trigger     |`bool`      |否   |    |   是否触发killmon |
|showdie     |`bool`      |否   |    |   是否显示死亡动画<br />=false视为系统杀怪,将不会掉落物品与经验 |

### 清掉地图某范围的怪物

`killmapmon`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                      |
| :------ | :-------- | :--- | :--- | :------------------------ |
| MapId   | `string`  | 否   |      | 地图ID                    |
| X       | `integer` | 否   |      | 坐标X                     |
| Y       | `integer` | 否   |      | 坐标Y                     |
| range   | `integer` | 否   |      | 范围                      |
| monName | `string`  | 否   |      | 怪物名<br />`*`表示所有怪物 |
| isDrop  | `integer` | 是   | 0    | 是否爆物品<br />0=不爆;1=爆 |
| isClear | `integer` | 是   | 0    | 是否清尸体<br />0=不清;1=清 |
```lua
    killmapmon( mapID,x,y, 10, "*", 0,1)
```

---

### 杀怪物品再爆
`monitems`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player     |`object`      |否   |    |玩家对象 |
|count     |`integer`      |否   |    |   怪物物品掉落增加次数 |

### 指定怪物的爆出

`monitemsex`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数      | 类型      | 空   | 默认 | 注释                       |
| :-------- | :-------- | :--- | :--- | :------------------------- |
| actor     | `object`  | 否   |      | 玩家对象                   |
| monItem   | `string`  | 否   |      | 怪物名称                   |
| value     | `integer` | 否   |      | 可爆出次数<br />最大多爆20次 |
| delayTime | `integer` | 是   | 0    | 延迟毫秒数                 |
```lua
--接口需要杀怪触发[killmon]中使用
function killmon(actor, monobj)
    if getbaseinfo(monobj,1) == "食人花" then
        monitemsex(actor,"练功稻草人",2,5000)
    end
end
```

---

### 召唤宝宝
`recallmob`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player     |`object`      |否   |    |玩家对象 |
|monName     |`string`      |否   |    |   怪物名称 |
|level     |`integer`      |否   |    |宝宝等级(最高为7) |
|time     |`integer`      |否   |    |叛变时间(分钟) |
|param1     |`integer`      |否   |    |预留(填0) |
|param2     |`integer`      |否   |    |预留(填0) |
|param3     |`integer`      |否   |    |设置大于0，检测时不计算该宝宝数量(仅M2控制的召唤数量) |
|result     |`object`      |否   |    |   宝宝对象 |
```lua
    local mon = recallmob(actor,"神兽",7,30,1)
    release_print("成功召唤",getbaseinfo(mon,1))
```

### 召唤宝宝2

`recallmobex`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数                 | 类型      | 空   | 默认 | 注释                         |
| :------------------- | :-------- | :--- | :--- | :--------------------------- |
| actor                | `string`  | 否   |      | 玩家对象                     |
| monster_name         | `string`  | 否   |      | 怪物名称                     |
| x                    | `integer` | 否   |      | 怪物当前地图出生点X          |
| y                    | `integer` | 否   |      | 怪物当前地图出生点Y          |
| level                | `integer` | 否   |      | 怪物等级                     |
| quantity             | `integer` | 否   |      | 数量                         |
| rebellion_time       | `integer` | 是   | 10   | 叛变时间(秒)<br />最低10秒     |
| auto_change_color    | `integer` | 否   |      | 是否自动变色                 |
| count                | `integer` | 否   |      | 检测时不计算该宝宝数量       |
| upgrade              | `integer` | 否   |      | 宝宝不升级                   |
| hide_master_name     | `integer` | 否   |      | 隐藏主人名                   |
| inherit_attr_percent | `integer` | 否   |      | 继承人物伤害百分比           |
| hp_value             | `integer` | 否   |      | 宝宝血量数值                 |
| buff_id              | `string`  | 否   |      | BUFF ID 多个BUFF ID用#号连接 |
```lua
    local mons = recallmobex(actor, "练功稻草人", x, y, 0, 5, 65535, 0, 1, 1, 1)
    for i, mon in ipairs(mons or {}) do
        release_print("宝宝系统",i,getbaseinfo(mon,ConstCfg.gbase.x),getbaseinfo(mon,ConstCfg.gbase.y))
    end
```

### 把怪物设置成宝宝
`setmonmaster`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mon     |`object`      |否   |    |   怪物对象 |
|player     |`object`      |否   |    |玩家对象 |

```lua
function main(self)
   local mon =  genmon(0,289,613,"黑野猪",10,1)
   setmonmaster(mon[1],self);
   say(self,"你获得了黑野猪宝宝")
end
```

### 遍历宠物(宝宝)列表
`getslavebyindex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nIndex     |`integer`      |否   |    |   索引(0开始) |
|result     |`object`      |否   |    |   怪物对象 |

```lua
function main(actor)
    local ncount=getbaseinfo(actor,38)
    for i = 0 ,ncount-1 do
        local mon = getslavebyindex(actor, i)
        if mon and isnotnull(mon) then
            setbaseinfo(mon,20,getbaseinfo(mon,20)+10)
        end
    end
    say(actor,'你的所有宝宝增加10点攻击')
end
```

### 修改宝宝名称
`changemonname`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mob |`object`      |否   |    | 宝宝对象 |
|name |`string`      |否   |    | 宝宝新名字 |

### 修改宝宝属性值
`changemobability`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |
|mob |`object`      |否   |    | 宝宝对象 |
|attr |`integer`      |否   |    | 属性位置 |
|method |`char`      |否   |    | 操作符(+ - =)  |
|value |`integer`      |否   |    | 属性值 |
|time |`integer`      |否   |    | 有效时间 |

```
属性位置：
1=防御下限 
2=防御上限 
3=魔御下限 
4=魔御上限 
5=攻击下限 
6=攻击上限 
7=魔法下限 
8=魔法上限
9=道术下限 
10=道术上限 
11=MaxHP 
12=MaxMP 
13=攻击加速(百分比)
14=移动加速(百分比)
```

### 获取宝宝等级
`getslavelevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mon     |`object`      |否   |    |   宝宝对象 |
|result     |`object`      |否   |    |宝宝等级 |

### 修改宝宝等级
`changeslavelevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|mon     |`object`      |否   |    |   宝宝对象 |
|operate     |`string`      |否   |    |   操作符号(+,-,=) |
|nLevel     |`integer`      |否   |    |   等级 |

---
### 根据唯一id获取怪物对象
`getmonbyuserid`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mapid     |`string`      |否   |    |   地图id |
|monUserId     |`string`      |否   |    |怪物唯一id(UserID) |
|result     |`object`      |否   |    |返回怪物对象 |

---
### 返回怪物基础信息
`getmonbaseinfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|idx     |`integer`      |否   |    |   怪物的IDX |
|id     |`integer`      |否   |    |id |
|result     |`variant`      |否   |    |返回值 |

- id取值：
1-怪物名称；
2-怪物名字颜色；
3-杀死怪物获得的经验值；

```lua
function main(self)
   local monname =  getmonbaseinfo(10001,1)
   say(self,monname)
end
```

### 检测范围内怪物数量
`checkrangemoncount`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|mapid     |`string`      |否   |    |   地图Id |
|monName     |`string`      |否   |    |怪物名，为空 or * 为检测所有怪 |
|nx     |`integer`      |否   |    |坐标X |
|nx     |`integer`      |否   |    |坐标Y |
|nRange     |`integer`      |否   |    |范围 |
|result     |`integer`      |否   |    |返回值，数量 |

```lua
function main(self)
   say(self,'该范围有'..checkrangemoncount('0','',285,612,10)..'只怪')
end
```
### 拾取小精灵
#### 召唤
`createsprite`cfg_monster.xls怪物表格式:Race=216 

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |
|monName     |`string`      |否   |    |精灵名称 |

#### 检测
`checkspritelevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |
|monName     |`string`      |否   |    |精灵名称,为空 则检测全部 |
|result     |`bool`      |否   |    |返回值，是否有小精灵 |

#### 回收
`releasesprite`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |

#### 拾取模式
`pickupitems`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |
|mode     |`integer`      |否   |    |模式<br />0=以人物为中心捡取<br />1=以小精灵为中心捡取<br />3=以小精灵为中心小精灵一个个捡取<br />4=以人物为中心小精灵一个个捡取 |
|Range     |`integer`      |否   |    |范围 |
|interval  |`integer`      |否   |    |间隔，最小500ms |

#### 停止拾取
`stoppickupitems`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |

### 在指定位置优先打指定打怪
`killmobappoint`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player |`object`      |否   |    | 玩家对象 |
|map |`string`      |否   |    | 地图 |
|X |`integer`      |否   |    | X坐标 |
|Y |`integer`      |否   |    | Y坐标 |
|MonName |`string`      |否   |    | 优先攻击的怪物名称 |
```
MonName支持多个怪物名称，怪物名称中间用 | 分隔
```

### 设置标记值
`setcurrent`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|obj |`object`      |否   |    | 人物、怪物对象 |
|index |`string`      |否   |    | 下标ID（0-9） |
|value |`string`      |否   |    | 标记值 |

### 获取标记值
`getcurrent`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|obj |`object`      |否   |    | 人物、怪物对象 |
|index |`string`      |否   |    | 下标ID（0-9） |
|result |`string`      |   |    | 标记值 |

### 临时增加怪物爆出物品
`additemtodroplist`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|obj |`object`      |否   |    | 人物、怪物对象 |
|mon |`object`      |否   |    | 怪物对象 |
|itemname |`string`      |   |    | 物品名称|
```
    多个物品使用|分隔；
    增加爆出物品，需要在KillMon触发中使用，仅一次有效。
```

### 嘲讽怪物
`dotaunt`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play |`object`      |否   |    | 玩家对象 |
|distance |`integer`      |否   |    | 距离人物格子数 |
|grade |`integer`      |  否 |    | 受嘲讽影响的怪物等级上限（不大于指定等级均会被吸引）|

### 宝宝嘲讽

`mobdotaunt`

| 参数     | 类型      | 空   | 默认 | 注释                                                 |
| :------- | :-------- | :--- | :--- | :--------------------------------------------------- |
| play     | `object`  | 否   |      | 玩家对象                                             |
| idx      | `integer` | 否   |      | 第几个宝宝（第一个宝宝为0）                          |
| rang     | `integer` | 否   |      | 距离格子数                                           |
| levelMax | `integer` | 否   |      | 受嘲讽影响的怪物等级上限（不大于指定等级均会被吸引） |
```lua
    mobdotaunt(actor,0 ,20 ,1000)
```

### 调整宝宝攻击人物的威力倍率

`changeslaveattackhumpowerrate`

| 参数    | 类型      | 空   | 默认 | 注释                                                             |
| :------ | :-------- | :--- | :--- | :--------------------------------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                                         |
| petName | `string`  | 否   |      | 宝宝名称(带数字和不带数字都可以)                                 |
| pro     | `integer` | 否   |      | 攻击人物威力倍率(威力倍数为0时不攻击人物, 110=攻击人物倍数1.1倍) |
```lua
    changeslaveattackhumpowerrate(actor,"神兽",3000)
```

------------

### 怪物寻路/巡逻

`monmission`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释                                    |
| :----- | :-------- | :--- | :--- | :-------------------------------------- |
| player | `object`  | 否   |      | 怪物对象                                |
| posX   | `string`  | 否   |      | x坐标集<br />多坐标`;`分割<br />最多传入9个 |
| posY   | `string`  | 否   |      | y坐标集<br />多坐标`;`分割<br />最多传入9个 |
| modle  | `integer` | 否   |      | 0=寻路<br />1=巡逻                        |
```lua
    local mons = genmon(3,333,333,"练功稻草人",1,2)
    for _, mon in ipairs(mons or {}) do
        -- monmission(mon,"340;340;333;333","333;340;340;333",0)   -- 寻路[寻路结束后触发missionend]
        monmission(mon,"340;340;333;333","333;340;340;333",1)   -- 巡逻
    end

    --QFunction-0.lua
    function missionend(sysobj,monobj)
        release_print("missionend,寻路结束",getbaseinfo(monobj,ConstCfg.gbase.name))
    end
```

### 怪物寻路

`mission`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数                    | 类型      | 空   | 默认 | 注释                      |
| :---------------------- | :-------- | :--- | :--- | :------------------------ |
| mapID                   | `string`  | 否   |      | 地图id                    |
| x                       | `string`  | 否   |      | x坐标串联                 |
| y                       | `string`  | 否   |      | y坐标串联                 |
| mob                     | `string`  | 否   |      | 刷怪坐标x                 |
| moby                    | `string`  | 否   |      | 刷怪坐标y                 |
| count                   | `integer` | 否   |      | 数量                      |
| range                   | `integer` | 否   |      | 范围                      |
| mobName                 | `string`  | 否   |      | 怪物名字                  |
| target                  | `string`  | 否   |      | 目标                      |
| country                 | `string`  | 否   |      | 国家                      |
| attackSelfPlayer        | `integer` | 否   |      | 是否攻击本国玩家(0,1)     |
| attackPVP               | `integer` | 否   |      | 不同国家怪物是否PK(0,1)   |
| mobNameColor            | `string`  | 否   |      | 怪物名字颜色              |
| disableSelfPlayerAttack | `integer` | 否   |      | 是否禁止本国玩家攻击(0,1) |

```lua
    mission(mapID,"333","333",x,y,10,10,"练功稻草人",nil,countName,1,1,255,1)
```

### 命令移动怪物

`movemontopos`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释     |
| :------ | :-------- | :--- | :--- | :------- |
| monName | `string`  | 否   |      | 怪物名字 |
| mapID   | `string`  | 否   |      | 地图ID   |
| posX1   | `integer` | 否   |      | 老坐标X  |
| posY1   | `integer` | 否   |      | 老坐标Y  |
| posX2   | `integer` | 否   |      | 新坐标X  |
| posY2   | `integer` | 否   |      | 新坐标Y  |
```lua
    movemontopos("练功稻草人",3,300,300,333,333)
```

------------

### 获取怪物原始各项数据库字段值参数

`getdbmonfieldvalue`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.10.24新增接口&lt;/font&gt;**

| 参数           | 类型               | 空   | 默认 | 注释               |
| :------------- | :----------------- | :--- | :--- | :----------------- |
| monIdx/monName | `integer`/`string` | 否   |      | 怪物ID/怪物名称    |
| fieldName      | `string`           | 否   |      | 字段名(看下方示例) |
| result         | `string`           | 否   |      | 表格数据           |
```lua
    local config = {
        {"idx","0列"},
        {"name","1列"},
        {"race","2列"},
        {"raceimg","3列"},
        {"appr","4列"},
        {"level","5列"},
        {"lifeattrib","6列"},
        {"cooleye","7列"},
        {"exp","8列"},
        {"hp","9列","生命值"},
        {"mp","9列","魔法值"},
        {"dc","9列","攻击下限"},
        {"maxdc","9列","攻击上限"},
        {"mc","9列","魔法"},
        {"sc","9列","道术"},
        {"ac","9列","物防下限"},
        {"ac1","9列","物防上限"},
        {"mac","9列","魔防下限"},
        {"mac1","9列","魔防上限"},
        {"speed","10列"},
        {"hitpoint","11列"},
        {"walkspeed","12列"},
        {"walkstep","13列"},
        {"walkwait","14列"},
        {"attackspeed","15列"},
        {"attribute","16列"},
        {"color","17列"},
        {"rehealthcd","18列"},
        {"type","19列"},
        {"viewrange","20列"},
        {"droptype","21列"},
        {"through","22列"},
        {"isboss","23列"},
        {"homerate","24列"},
        {"monparam1","25列"},
        {"attacklist","26列"},
        {"bigtipid","27列"},
        {"noshow","28列"},
        {"isngmon","29列"},
        {"bodyleathery","30列"},
        {"butchrate","30列"},
    }
    for _, v in ipairs(config) do
        release_print("对应monster表",v[2],v[1]..(v[3] or ""),getdbmonfieldvalue("[BOSS]沃玛教主3",v[1]))
    end
```

------------

### 重置怪物生成计时器

`resetmongentick`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;** [***接口示例代码.zip***](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=ed7b486b404e607c9a620fe9ab5d544d "demo.zip")

| 参数    | 类型      | 空   | 默认 | 注释      |
| :------ | :-------- | :--- | :--- | :-------- |
| mapID   | `string`  | 否   |      | 地图ID    |
| monPosX | `integer` | 否   |      | 怪物X坐标 |
| monPosY | `integer` | 否   |      | 怪物Y坐标 |
| monName | `string`  | 否   |      | 怪物名称  |

------------

### 让怪物释放自定义技能

`mon_docustommagic`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**
&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;注：只支持自定义怪物（race=156，RaceImg=19）&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释         |
| :------ | :-------- | :--- | :--- | :----------- |
| actor   | `object`  | 否   |      | 怪物对象     |
| skillID | `integer` | 否   |      | 自定义技能id |
| X       | `integer` | 否   |      | 目标点X坐标  |
| Y       | `integer` | 否   |      | 目标点Y坐标  |
| target  | `object`  | 否   |      | 目标对象     |

```lua
    mon_docustommagic(mon,skill_id,pos_X,pos_Y,actor)
```

### 添加自定义怪物攻击表现

`addmonattack`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                              |
| :------ | :-------- | :--- | :--- | :-------------------------------- |
| mon     | `object`  | 否   |      | 怪物对象                          |
| skillID | `integer` | 否   |      | 攻击表现id<br />对应cfg_monattack表 |

```lua
    addmonattack(mon,11)
```


# 地图相关



## 移动

### 跳转地图（随机坐标）
`map`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| play  | `object` | 否   |      | 玩家对象 |
| mapID | `string` | 否   |      | 地图ID   |

### 飞地图（指定坐标）
`mapmove`

| 参数   | 类型      | 空   | 默认                    | 注释                                   |
| :----- | :-------- | :--- | :---------------------- | :------------------------------------- |
| play   | `object`  | 否   |                         | 玩家对象                               |
| mapID  | `string`  | 否   |                         | 地图ID                                 |
| nX     | `integer` | 否   |                         | X坐标                                  |
| nY     | `integer` | 否   |                         | Y坐标                                  |
| nRange | `integer` | 否   |                         | 范围                                   |
| effect | `integer` | 是   | 引擎64_24.08.07新增接口 | 是否播放传送特效<br />0=播放<br />1=不播放 |

### 导航玩家到指定位置

&gt; 自动寻路到指定坐标

`gotonow`

| 参数 | 类型      | 空   | 默认 | 注释     |
| :--- | :-------- | :--- | :--- | :------- |
| play | `object`  | 否   |      | 玩家对象 |
| X    | `integer` | 否   |      | X坐标    |
| Y    | `integer` | 否   |      | Y坐标    |

```lua
gotonow(actor,330, 330) 

--QFunction-0.lua

--寻路开启
function findpathbegin(actor)
     release_print("findpathstop",getbaseinfo(actor,1),getconst(actor, "&lt;$ToPointX&gt;"),getconst(actor, "&lt;$ToPointY&gt;"))
end
--寻路中断
function findpathstop(actor)
    release_print("findpathstop",getbaseinfo(actor,1))
end
--寻路结束
function findpathend(actor)
    release_print("findpathend",getbaseinfo(actor,1))
end
```

## 镜像地图

### 添加-addmirrormap
`addmirrormap`

| 参数      | 类型      | 空   | 默认               | 注释                                   |
| :-------- | :-------- | :--- | :----------------- | :------------------------------------- |
| oldMap    | `string`  | 否   |                    | 原地图ID                               |
| NewMap    | `string`  | 否   |                    | 新地图ID                               |
| NewName   | `string`  | 否   |                    | 新地图名                               |
| time      | `integer` | 否   |                    | 有效时间(秒)                           |
| BackMap   | `string`  | 否   |                    | 回城地图(有效时间结束后，传回去的地图) |
| miniMapID | `integer` | 否   | 引擎64_23.0628新增 | 小地图编号                             |
| posmX     | `integer` | 否   | 引擎64_23.0628新增 | 返回地图的X坐标                        |
| posmY     | `integer` | 否   | 引擎64_23.0628新增 | 返回地图的Y坐标                        |
| result    | `bool`    |      |                    | 是否成功创建                           |

```lua
[[
MapInfo.txt
[0 比奇]
[01|0 比奇-1]
[02|0 比奇-2]
[03|0 比奇-3]

这个配置的意思是 地图代码 01、02、03的地图都镜像地图代码为0的地图，
这样你就可以拥有3个比奇了，而玩家客户端上调用的都只是0.map文件

注意：被镜像的原地图必须先被服务器读取，因为MapInfo.txt读取方式是从上到下
所以被镜像的原地图应该在镜像地图的上面。

注意：用addmirrormap接口创建的镜像地图不能以01、02、03为原地图ID,需要以0为原地图ID。
]]
function main(actor)
    name_1 = name_1 and name_1 + 1 or 1
    --地图
    local oldMapId  = "0"
    local newMapId  = "0" .. getbaseinfo(actor, 2).. name_1  --新地图
    local mapName   = string.format("比奇[%d]",name_1)
    local mapTime   = 10   --地图持续时间
    --删除地图
    delmirrormap(newMapId)
    --创建镜像地图
    addmirrormap(oldMapId, newMapId, mapName, mapTime, 3,1,333,333)
    --刷怪
    genmon(newMapId,14,14,"练功稻草人",10,10)
    --进入地图
    map(actor, newMapId)
end
```

### 删除-delmirrormap
`delmirrormap`

| 参数  | 类型     | 空   | 默认 | 注释   |
| :---- | :------- | :--- | :--- | :----- |
| MapId | `string` | 否   |      | 地图ID |

### 获取/设置 镜像地图剩余时间
`mirrormaptime`

| 参数   | 类型      | 空   | 默认 | 注释             |
| :----- | :-------- | :--- | :--- | :--------------- |
| MapId  | `string`  | 否   |      | 地图ID           |
| time   | `integer` | 是   | 0    | 设置地图有效时间 |
| result | `integer` |      |      | 返回地图有效时间 |

### 检测镜像地图是否存在
`checkmirrormap`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| MapId  | `string` | 否   |      | 地图ID   |
| result | `bool`   |      |      | 是否存在 |

## 地图特效
### 添加地图特效

`mapeffect`

| 参数        | 类型      | 空   | 默认                | 注释                                                                    |
| :---------- | :-------- | :--- | :------------------ | :---------------------------------------------------------------------- |
| Id          | `integer` | 否   |                     | 特效播放ID，用于区分多个地图特效                                        |
| MapId       | `string`  | 否   |                     | 地图ID                                                                  |
| X           | `integer` | 否   |                     | 坐标X                                                                   |
| Y           | `integer` | 否   |                     | 坐标Y                                                                   |
| effId       | `string`  | 否   |                     | 特效ID                                                                  |
| time        | `integer` | 否   |                     | 持续时间（秒）<br />0/-1不限时间                                          |
| mode        | `integer` | 否   |                     | 模式:(0~4，0所有人可见，1自己可见，2组队可见，3行会成员可见，4敌对可见) |
| play        | `object`  | 否   | 引擎64_24.03.14新增 | 玩家对象<br />模式1~4需填                                                 |
| effectModel | `integer` | 是   | 引擎64_24.03.14新增 | 特效播放模式<br />0=在人物/怪物后面<br />1=在人物/怪物前面                  |

### 删除-delmapeffect
`delmapeffect`

| 参数 | 类型      | 空   | 默认 | 注释       |
| :--- | :-------- | :--- | :--- | :--------- |
| Id   | `integer` | 否   |      | 特效播放ID |

## 地图物品

### 在地图上放置物品

`throwitem`

| 参数      | 类型      | 空   | 默认               | 注释                                                           |
| :-------- | :-------- | :--- | :----------------- | :------------------------------------------------------------- |
| play      | `object`  | 否   |                    | 玩家对象                                                       |
| MapId     | `string`  | 否   |                    | 地图ID                                                         |
| X         | `integer` | 否   |                    | 坐标X                                                          |
| Y         | `integer` | 否   |                    | 坐标Y                                                          |
| range     | `integer` | 否   |                    | 范围                                                           |
| itemName  | `string`  | 否   |                    | 物品名                                                         |
| count     | `integer` | 否   |                    | 数量                                                           |
| time      | `integer` | 否   |                    | 时间（秒）                                                     |
| hint      | `bool`    | 否   |                    | 是否掉落提示                                                   |
| take      | `bool`    | 否   |                    | 是否立即拾取                                                   |
| onlyself  | `bool`    | 否   |                    | 仅自己拾取                                                     |
| xyinorder | `bool`    | 否   |                    | 是-按位置顺序，<br />否-随机位置                                 |
| overlap   | `integer` | 否   | 引擎64_23.0830新增 | 单个物品叠加数量，装备无效                                     |
| isAuto    | `bool`    | 否   | 引擎64_23.0830新增 | true=可自动拾取<br />false=不可自动拾取<br />(onlyself=true时生效) |

### 在地图上生成掉落物品

`gendropitem`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认               | 注释                                                 |
| :----- | :-------- | :--- | :----------------- | :--------------------------------------------------- |
| mapid  | `string`  | 否   |                    | 地图id                                               |
| actor  | `object`  | 是   |                    | 归属对象<br />填nil则无归属<br />且拾取cd时间会被设置为0 |
| X      | `integer` | 否   |                    | x坐标                                                |
| Y      | `integer` | 否   |                    | y坐标                                                |
| json   | `string`  | 否   |                    | 掉落json                                             |
| data   | `string`  | 否   |                    | 物品来源(参考设置物品来源)                           |
| range  | `integer` | 是   | 引擎64_24.0807新增 | 范围                                                 |
| result | `table`   | 否   |                    | 物品makeindex列表                                    |
```lua
    local items = {
        ["木剑"] = 100,
        ["金币"] = 996,
    }
    local data = {
        ["map"] =  mapID, --地图号
        ["source"] =  5,  --来源：1-GM生成，2-NPC，3-商城，4-NPC商店, 5-怪物掉落，6-系统给["与，7-挖矿，8-批量生成，9-宝箱
        ["mon"] = "白野猪",  --掉落的怪物
        ["player"] = "玩家人物名称qf",
        -- ["time"]=os.date("%Y-%m-%d %H:%M:%S", os.time()),  --掉落或生成的时间，为空时，设置为系统时间
    }
    local itemList = gendropitem(mapID,actor,x,y,tbl2json(items),tbl2json(data))
    -- local itemList = gendropitem(mapID,nil,x,y,tbl2json(items),tbl2json(data))
```

### 清理地图上指定名字的物品

`clearitemmap`

| 参数     | 类型      | 空   | 默认 | 注释                      |
| :------- | :-------- | :--- | :--- | :------------------------ |
| MapId    | `string`  | 否   |      | 地图ID                    |
| X        | `integer` | 否   |      | 坐标X                     |
| Y        | `integer` | 否   |      | 坐标Y                     |
| range    | `integer` | 否   |      | 范围                      |
| itemName | `string`  | 否   |      | 物品名<br />清理所有用`"*"` |

## 地图定时器

### 设定地图定时器
`setenvirontimer`

| 参数   | 类型      | 空   | 默认 | 注释                             |
| :----- | :-------- | :--- | :--- | :------------------------------- |
| MapId  | `string`  | 否   |      | 地图ID                           |
| Idx    | `integer` | 否   |      | 计时器ID                         |
| second | `integer` | 否   |      | 时长（秒）                       |
| func   | `string`  | 否   |      | 触发跳转的函数(多参数用逗号分割) |

```lua
 setenvirontimer(0,1,10,"@test_jump,aaa,bbb")

[[跳转函数参数1为系统对象,传递的参数从参数2开始]]
function test_jump(sysobj,...)
    release_print(...)
end
```

### 关闭地图定时器
`setenvirofftimer`

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| MapId | `string`  | 否   |      | 地图ID   |
| Idx   | `integer` | 否   |      | 计时器ID |

### 判断地图定时器是否存在

`hasenvirtimer`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数    | 类型     | 空   | 默认 | 注释                      |
| :------ | :------- | :--- | :--- | :------------------------ |
| mapID   | `string` | 否   |      | 地图id                    |
| timerid | `string` | 否   |      | 计时器id                  |
| result  | `bool`   | 否   |      | true=存在<br />false=不存在 |

## 动态地图连接

### 增加动态地图连接
`addmapgate`

| 参数    | 类型      | 空   | 默认 | 注释                       |
| :------ | :-------- | :--- | :--- | :------------------------- |
| name    | `string`  | 否   |      | 连接名称                   |
| Mapfrom | `string`  | 否   |      | 地图ID                     |
| X1      | `integer` | 否   |      | X(小于0时随机坐标)         |
| Y1      | `integer` | 否   |      | Y(小于0时随机坐标)         |
| range   | `integer` | 否   |      | 范围                       |
| Mapto   | `string`  | 否   |      | 到达地图号                 |
| X2      | `integer` | 否   |      | 到达地图X(小于0时随机坐标) |
| Y2      | `integer` | 否   |      | 到达地图Y(小于0时随机坐标) |
| time    | `integer` | 否   |      | 有效时间秒                 |

### 获取动态地图连接
`getmapgate`

| 参数    | 类型     | 空   | 默认 | 注释                                                                                                                                                                         |
| :------ | :------- | :--- | :--- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name    | `string` | 否   |      | 连接名称                                                                                                                                                                     |
| Mapfrom | `string` | 否   |      | 地图ID                                                                                                                                                                       |
| result  | `table`  | 否   |      | 返回table结果：<br /> result[1]-X坐标（int）<br /> result[2]-Y坐标（int）<br /> result[3]-目标地图（string）<br /> result[4]-目标地图X坐标（int）<br /> result[5]-目标地图Y坐标（int） |

## 其他

### 删除动态地图连接
`delmapgate`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| name  | `string` | 否   |      | 连接名称 |
| MapId | `string` | 否   |      | 地图ID   |

### 根据名称获取地图基础信息
`getmapinfo`

| 参数   | 类型      | 空   | 默认 | 注释                   |
| :----- | :-------- | :--- | :--- | :--------------------- |
| mapID  | `string`  | 否   |      | 地图ID                 |
| nIndex | `integer` | 否   |      | 0：地图宽<br />1：地图高 |
| result | `integer` | 否   |      | 返回地图基础信息       |

### 判断地图坐标是否为空
`isemptyinmap`

| 参数   | 类型      | 空   | 默认 | 注释                 |
| :----- | :-------- | :--- | :--- | :------------------- |
| mapID  | `string`  | 否   |      | 地图ID               |
| nX     | `integer` | 否   |      | 地图x坐标            |
| nY     | `integer` | 否   |      | 地图y坐标            |
| result | `bool`    | 否   |      | 返回地图坐标是否为空 |

### 获取地图指定范围内的怪物对象列表
`getmapmon`

参数同 CheckRangeMonCount

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| mapid   | `string`  | 否   |      | 地图Id                         |
| monName | `string`  | 否   |      | 怪物名，为空 or * 为检测所有怪 |
| nx      | `integer` | 否   |      | 坐标X                          |
| nx      | `integer` | 否   |      | 坐标Y                          |
| nRange  | `integer` | 否   |      | 范围                           |
| result  | `tab`     | 否   |      | 返回值，怪物对象               |

### 获取地图玩家对象列表

`getplaycount`

| 参数         | 类型           | 空   | 默认 | 注释                                      |
| :----------- | :------------- | :--- | :--- | :---------------------------------------- |
| MapId        | `string`       | 否   |      | 地图ID                                    |
| bIgnoreDied  | `integer`      | 否   |      | 是否忽略死亡角色<br />1:忽略<br />0:不忽略    |
| bIgnoreDummy | `integer`      | 否   |      | 是否忽略假人<br />1:忽略<br />0:不忽略        |
| result       | `table/string` | 否   |      | 存在玩家返回玩家列表<br />地图内无人返回"0" |

```lua
    local players = getplaycount("0",1,1)
    release_print("players",type(players))
    for index, player in ipairs(type(players) == "table" and players or {}) do
        release_print("player",index, getbaseinfo(player,1))
    end
```

### 获取指定地图玩家数量
`getplaycountinmap`

| 参数      | 类型      | 空   | 默认 | 注释                                         |
| :-------- | :-------- | :--- | :--- | :------------------------------------------- |
| play      | `object`  | 否   |      | 玩家对象<br />可传入系统对象`"0"`              |
| MapId     | `string`  | 否   |      | 地图ID                                       |
| isAllgain | `integer` | 否   |      | 是否全部获取<br />0=全部获取<br />1=排除已死亡的 |
| result    | `integer` | 否   |      | 返回值，玩家数量                             |
```lua
    local playerNum = getplaycountinmap("0","3",0)
    release_print("playerNum",playerNum)
```

### 获取指定地图怪物数量
`getmoncount`

| 参数     | 类型      | 空   | 默认 | 注释                                        |
| :------- | :-------- | :--- | :--- | :------------------------------------------ |
| MapId    | `string`  | 否   |      | 地图ID                                      |
| MonId    | `integer` | 否   |      | 怪物id<br />传入-1获取所有怪物                |
| isAllMon | `boolean` | 否   |      | 是否忽略宝宝<br /> true:忽略<br /> false:不忽略 |
| result   | `integer` | 否   |      | 返回值，怪物数量                            |

### 把某个地图中的玩家全部移动到另外一个地图
`movemapplay`

| 参数   | 类型      | 空   | 默认               | 注释         |
| :----- | :-------- | :--- | :----------------- | :----------- |
| play   | `object`  | 否   |                    | 玩家对象     |
| aMapId | `string`  | 否   |                    | 移动前地图Id |
| bMapId | `string`  | 否   |                    | 移动后地图Id |
| x      | `integer` | 否   |                    | x坐标        |
| y      | `integer` | 否   |                    | y坐标        |
| range  | `integer` | 否   | 引擎64_23.0830新增 | 范围         |
```lua
movemapplay(actor,0,3,333,333,5)
```

### 设置地图杀怪经验倍数
`mapkillmonexprate`

| 参数  | 类型      | 空   | 默认 | 注释                                                                                                   |
| :---- | :-------- | :--- | :--- | :----------------------------------------------------------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                                                                               |
| MapId | `string`  | 否   |      | 地图id( * 号表示所有地图)                                                                              |
| much  | `integer` | 否   |      | 倍率 为杀怪经验倍数，倍数除以100为真正的倍率(200 为 2 倍经验，150 为1.5倍,0表示关闭地图的杀怪经验倍数) |

### 随机杀死地图中的怪物
`randomkillmon`

| 参数        | 类型      | 空   | 默认 | 注释                           |
| :---------- | :-------- | :--- | :--- | :----------------------------- |
| mapid       | `string`  | 否   |      | 地图Id                         |
| monstername | `string`  | 否   |      | 怪物名字                       |
| num         | `integer` | 否   |      | 数量(1-255)                    |
| obj         | `integer` | 否   |      | 掉落物品(0,1)  0=掉落 1=不掉落 |

### 编组地图传送
`groupmapmove`

| 参数  | 类型      | 空   | 默认 | 注释                                                       |
| :---- | :-------- | :--- | :--- | :--------------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                                   |
| MapId | `string`  | 否   |      | 地图ID                                                     |
| x     | `integer` | 否   |      | x坐标                                                      |
| y     | `integer` | 否   |      | y坐标                                                      |
| level | `integer` | 否   |      | 可以传送最低等级(可以为空，为空时不检测队员的等级直接传送) |
| value | `integer` | 否   |      | 传送范围。（以队长为中心传送队友，0为不需要范围）          |
| obj   | `object`  | 是   |      | 触发字段(可以为空)                                         |
```lua
    groupmapmove(actor,3,333,333,nil,0,"testjump")
    function testjump(actor)
        release_print("testjump",getbaseinfo(actor,1))
    end
```

### 根据地图id返回地图名
`getmapname`

| 参数   | 类型     | 空   | 默认 | 注释           |
| :----- | :------- | :--- | :--- | :------------- |
| mapid  | `string` | 否   |      | 地图Id         |
| result | `string` | 否   |      | 返回值，地图名 |

### 检测地图逻辑格
`gridattr`

| 参数   | 类型      | 空   | 默认 | 注释                                                                    |
| :----- | :-------- | :--- | :--- | :---------------------------------------------------------------------- |
| mapid  | `string`  | 否   |      | 地图Id                                                                  |
| x      | `integer` | 否   |      | x坐标                                                                   |
| y      | `integer` | 否   |      | y坐标                                                                   |
| type   | `integer` | 否   |      | 逻辑格类型:<br />1.能否到达;<br />2.安全区; <br />3.攻城区;                   |
| result | `boolean` | 否   |      | 地图逻辑格的实际属性是否与指定属性类型相同<br />true:相同<br />false:不相同 |

### 获取当前地图行会成员数量

`maphanghcyguild`

| 参数      | 类型     | 空   | 默认 | 注释                              |
| :-------- | :------- | :--- | :--- | :-------------------------------- |
| mapID     | `string` | 否   |      | 地图编号                          |
| guildName | `string` | 否   |      | 行会名字或 * (等于未加入行会角色) |

```lua
local num = maphanghcyguild(3,"*")
```

### 获取当前地图怪物状态

`mapbossinfo`

| 参数    | 类型      | 空   | 默认 | 注释                                                       |
| :------ | :-------- | :--- | :--- | :--------------------------------------------------------- |
| mapID   | `string`  | 否   |      | 地图编号                                                   |
| monName | `string`  | 否   |      | 怪物名称，*表示所有怪物                                    |
| model   | `integer` | 否   |      | 怪物名字格式<br />0=显示名称(不带数字)<br />1=表内名称(带数字) |
| param   | `integer` | 否   |      | 0=获取表格内刷的怪物状态<br />1=获取表格内和脚本刷的怪物状态 |
| result  | `table`   | 否   |      | 地图怪物状态                                               |
```lua
[[
    注意:
    刷怪表cfg_mongen.xls 第7列第10列字段必须填1，(脚本刷的怪剩余刷新时间都为0，多只相同名字的怪死亡后 只能获取到一只的信息)
    cfg_monster.xls表23列是否是boss字段必须填1

    返回值说明:
    怪物名称#剩余HP百分比#剩余刷新时间（单位秒，存在的怪物刷新时间为0）#当前X坐标#当前Y坐标#归属玩家名字
]]
local info = mapbossinfo(mapID,"*",1)
release_print("地图怪物状态",tbl2json(info))
```

### 开启/关闭地图参数

`setmapmode`

| 参数     | 类型     | 空   | 默认 | 注释                                                                                     |
| :------- | :------- | :--- | :--- | :--------------------------------------------------------------------------------------- |
| mapID    | `object` | 否   |      | 地图编号                                                                                 |
| mapEvent | `string` | 否   |      | 地图参数,参考mapinfo.txt配置说明                                                         |
| model1   | `string` | 是   |      | 不填表示关闭此地图参数，填地图参数里的需要的参数<br />不需要传参的地图事件也需要传入一个值 |
| param2   | `string` | 是   |      | 地图参数里的需要的参数                                                                   |
```lua
--开启地图事件,3号地图全局每5秒加100点
setmapmode(3,"INCHP","5" ,"-100")
--关闭间隔扣血地图事件
setmapmode(3,"INCHP")

--开启地图事件,3号地图禁止喊话
setmapmode(3,"QUIZ","这代表任意值")
--关闭禁止喊话地图事件
setmapmode(3,"QUIZ")
```

### 增加天气

`setweathereffect`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                               |
| :---- | :-------- | :--- | :--- | :------------------------------------------------- |
| mapID | `string`  | 否   |      | 地图ID                                             |
| model | `integer` | 否   |      | 天气效果<br />1=黄沙效果<br />2=花瓣效果<br />3=下雪效果 |
| time  | `integer` | 否   |      | 有效时间(秒)                                       |

### 删除天气

`delweathereffect`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                                                 |
| :---- | :-------- | :--- | :--- | :------------------------------------------------------------------- |
| mapID | `string`  | 否   |      | 地图ID                                                               |
| model | `integer` | 否   |      | 天气效果<br />0=关闭所有效果<br />1=黄沙效果<br />2=花瓣效果<br />3=下雪效果 |

### 获取地图上指定范围内的对象
`getobjectinmap`

| 参数   | 类型      | 空   | 默认                                    | 注释                                                                                                         |
| :----- | :-------- | :--- | :-------------------------------------- | :----------------------------------------------------------------------------------------------------------- |
| MapId  | `string`  | 否   |                                         | 地图ID                                                                                                       |
| X      | `integer` | 否   |                                         | 坐标X                                                                                                        |
| Y      | `integer` | 否   |                                         | 坐标Y                                                                                                        |
| range  | `integer` | 否   |                                         | 范围                                                                                                         |
| flag   | `integer` | 否   | 64-英雄 128-分身<br />引擎64_23.06.28新增 | 标记值，二进制位表示：<br />1-玩家，2-怪物<br />4-NPC，8-物品<br />16-地图事件<br />32-人形怪<br />64-英雄<br />128-分身 |
| result | `table`   | 否   |                                         | 对象列表                                                                                                     |

### 获取怪物位置及复活时间(仅支持小地图上提示的怪物)

`getmonrefresh`

| 参数   | 类型      | 空   | 默认               | 注释                       |
| :----- | :-------- | :--- | :----------------- | :------------------------- |
| mapId  | `string`  | 否   |                    | 地图ID                     |
| model  | `integer` | 否   | 引擎64_23.0830新增 | 0=屏蔽数字<br />1=不屏蔽数字 |
| result | `string`  | 否   |                    | 怪物Json数据               |
```json
// 返回结果示例：
{"mon":[{"name":"火龙神","x":476,"y":484,"time":0},{"name":"火龙神","x":359,"y":409,"time":0}],"count":2}
// 其中time=0时表示，怪物已经复活，大于0时表示怪物将于N秒后复活
```


# 定时器相关



### 全局定时器
#### 添加-setontimerex
`setontimerex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|id     |`integer`      |否   |    |   定时器ID |
|tick |`integer`  |否 | |执行间隔，秒|
```lua
        setontimerex(23, 5)

        --触发函数为ontimerex 拼接 定时器id
        function ontimerex23()
        end
```
#### 移除-setofftimerex
`setofftimerex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|id     |`integer`      |否   |    |   定时器ID |
```lua
    setofftimerex(23)
```

#### 判断全局定时器是否存在

`hastimerex`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.03.14新增接口</font>**

| 参数    | 类型     | 空   | 默认 | 注释                      |
| :------ | :------- | :--- | :--- | :------------------------ |
| timerid | `string` | 否   |      | 计时器id                  |
| result  | `bool`   | 否   |      | true=存在<br>false=不存在 |

------------

### 个人定时器
#### 添加-setontimer
|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|id     |`integer`      |否   |    |   定时器ID |
|RunTick     |`integer`      |否   |    |  执行间隔，秒  |
|RunTime     |`integer`      |是  |  0 |  执行次数，>0执行完成后，自动移除  |
|kf     |`integer`      |是  |  0 |  跨服是否继续执行 1：继续  |
```lua

        setontimer(actor, 1, 5, 1)

        --触发函数为ontimer 拼接 定时器id
        function ontimer1(actor)
        end
```

#### 移除-setofftimer

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|id     |`integer`      |否   |    |   定时器ID |

```lua
    setofftimer(actor, 1)
```

#### 判断玩家定时器是否存在

`hastimer`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.03.14新增接口</font>**

| 参数    | 类型     | 空   | 默认 | 注释                      |
| :------ | :------- | :--- | :--- | :------------------------ |
| actor   | `string` | 否   |      | 玩家对象                  |
| timerid | `string` | 否   |      | 计时器id                  |
| result  | `bool`   | 否   |      | true=存在<br>false=不存在 |


# 攻城相关



## 攻城战说明

- 注:勾选M2设置来确定是引擎开启攻城战还是脚本控制:`M2-参数设置-城堡设置-取消M2攻城设置` 勾选后申请攻城天数、攻城开始\结束时间\攻城时长及攻城触发不再受M2控制;
- **建议在本地修改电脑时间来测试攻城战**

### 使用GM命令强制开关攻城战

```lua
    [[开启前需要把所有行会添加到攻城列表]]
    addtocastlewarlistex("*")
    gmexecute("0","ForcedWallConQuestwar")

    [[攻城战开启状态下再次调用ForcedWallConQuestwar命令即可关闭攻城战]]
    if castleinfo(5) then
        gmexecute("0","ForcedWallConQuestwar")
    end
```

## 触发

### 攻城开始时触发

`castlewarstart`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | ---- | -------- |
| sysobj | `object` | 否   |      | 系统对象 |

### 攻城结束时触发
`castlewarend`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | ---- | -------- |
| sysobj | `object` | 否   |      | 系统对象 |

### 占领沙巴克触发

`getcastle0`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| sysobj | `object` | 否   |      | 系统对象 |

------------

## 接口

### 获取玩家沙巴克身份
`castleidentity`

| 参数   | 类型     | 空   | 默认 | 注释                                                     |
| :----- | :------- | :--- | ---- | -------------------------------------------------------- |
| play   | `object` | 否   |      | 玩家对象                                                 |
| result | `int`    | 否   |      | 返回值<br />0-非沙巴克成员<br />1-沙巴克成员<br />2-沙巴克老大 |

------------

### 沙巴克基本信息
`castleinfo`

| 参数   | 类型  | 空   | 默认 | 注释     |
| :----- | :---- | :--- | ---- | -------- |
| nID    | `int` | 否   |      | 信息索引 |
| result | `int` | 否   |      | 返回值   |

- 说明
nID对应值分别为：
1=沙城名称，返回string
2=沙城行会名称，返回string
3=沙城行会会长名字，返回string
4=占领天数，返回number
5=当前是否在攻沙状态，返回Bool
6=沙城行会副会长名字列表，返回table

------------

### 脚本命令设置沙巴克归属

`setcastleguild`

| 参数  | 类型     | 空   | 默认 | 注释                                              |
| :---- | :------- | :--- | ---- | ------------------------------------------------- |
| guildName  | `string` | 否   |      | 行会名称                                          |
| param | `int`    | 否   |      | 是否忽略触发@beforgetcastle<br />0=不忽略<br />1=忽略 |
```lua
setcastleguild("对对对", 0)

--QFunction-0.lua
function beforgetcastle(sysObj,guildName)
    release_print("行会名",guildName)
end
```

------------

### 获取攻城列表

`getcastlewarlist`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

```lua
    local guild_list = getcastlewarlist()
    release_print("guild_list",tbl2json(guild_list))
```

### 把行会添加到攻城列表
`addtocastlewarlist`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|name     |`string`    |否   |    |   行会名 |
|day     |`integer`    |否   |    |   天数 |

### 强制把行会添加到攻城列表
`addtocastlewarlistex`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|name     |`string`    |否   |    |   行会名<br />传入`"*"`所有行会 |

### 所有行会在当晚同时攻城
`addattacksabukall`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|无参数     |    |   |    |    |  |

------------

### 修复城门,城墙等

&gt; 攻沙期间无法修复城门/城墙

`repaircastle`

### 雇佣沙巴克弓箭手/卫士

`castlearchergen`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数    | 类型      | 空   | 默认 | 注释                           |
| :------ | :-------- | :--- | :--- | :----------------------------- |
| monID   | `integer` | 否   |      | 弓箭手/卫士ID                  |
| monType | `integer` | 是   | 0    | 类型<br />0/nil=弓箭手<br />1=卫士 |

&gt; 注:**雇佣弓箭手/守卫需要消耗城堡金币,可以在[M2-参数设置-城堡参数]中设置雇佣弓箭/卫士=0**
&gt; 注:**弓箭手/守卫的尸体消失后才能进行**

```lua
-- monID对应的是SabukW.txt配置中的Archer/Guard的id
-- 示例:1号弓箭手信息
-- Archer_1_X=662
-- Archer_1_Y=333
-- Archer_1_Name=弓箭手
-- Archer_1_HP=2000
-- 示例:2号护卫信息
-- Guard_2_X=649
-- Guard_2_Y=301
-- Guard_2_Name=护卫
-- Guard_2_HP=1000
function main(actor)
    for i = 1,24 do
        castlearchergen(i)
        release_print("雇佣弓箭手",i)
    end
    for i = 1,8 do
        castlearchergen(i,1)
        release_print("雇佣护卫",i)
    end
end
```
# NPC相关



### 创建临时NPC
`createnpc`

| 参数 | 类型      | 空   | 默认 | 注释                  |
| :--- | :-------- | :--- | ---- | --------------------- |
| map  | `string`  | 否   |      | 地图编号              |
| X    | `integer` | 否   |      | X坐标                 |
| Y    | `integer` | 否   |      | Y坐标                 |
| NPC  | `string`  | 否   |      | NPC信息<br>json字符串 |

```lua
[[
    注意：自定义NPC的Idx不允许与配置表中的NPCID重复。
    Idx重复的NPC不会被创建出来。
]]
local npcInfo = {
    ["Idx"] =  npcidx,  -- 自定义NPC的Idx，NPC点击触发时，触发参数会传回Idx值
    ["npcname"] =  "测试", -- NPC名称
    ["appr"] =   7,  -- NPC外形效果
    ["script"] =   'NewNPC'  -- NPC相关脚本名称，表示Envir\Market_def\NewNPC.txt
    ["limit"] = 5, -- 生命周期 (秒) 引擎64_24.05.23新增
}
createnpc(mapID,x,y,tbl2json(npcInfo))

```

### 删除NPC
`delnpc`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | ---- | -------- |
| name | `string` | 否   |      | NPC名称  |
| map  | `string` | 否   |      | 地图编号 |

### 根据ID获取NPC对象
`getnpcbyindex`

| 参数     | 类型     | 空   | 默认 | 注释                       |
| :------- | :------- | :--- | ---- | -------------------------- |
| NPCIndex | `int`    | 否   |      | NPC索引（NPC配置表中的ID） |
| npc      | `object` | 否   |      | NPC对象                    |

### 打开指定NPC面板
`opennpcshow`

| 参数     | 类型     | 空   | 默认 | 注释                       |
| :------- | :------- | :--- | ---- | -------------------------- |
| play     | `object` | 否   |      | 玩家对象                   |
| NPCIndex | `int`    | 否   |      | NPC索引（NPC配置表中的ID） |
| nRange   | `int`    | 否   |      | 范围值，在此范围内允许打开 |

### 移动到指定NPC附近
`opennpcshowex`

| 参数     | 类型     | 空   | 默认 | 注释                                    |
| :------- | :------- | :--- | ---- | --------------------------------------- |
| play     | `object` | 否   |      | 玩家对象                                |
| NPCIndex | `int`    | 否   |      | NPC索引（NPC配置表中的ID）              |
| nRange   | `int`    | 否   |      | 范围值，<br>不在此范围内则移动到NPC附近 |
| nRange2  | `int`    | 否   |      | 范围值2，移动到NPC附近的范围内          |
```
1. NPC不在当前地图时: nRange>0: 瞬移传送到NPC附近; nRange=0: 不传送;
2. NPC在当前地图时: nRange>0: 瞬移传送到NPC附近; nRange=0: 导航到NPC附近;
```

### 获取当前NPC对象
`getcurrnpc`

| 参数   | 类型     | 空   | 默认 | 注释                  |
| :----- | :------- | :--- | ---- | --------------------- |
| player | `object` | 否   |      | 玩家对象              |
| result | `object` | 否   |      | 返回值，当前的NPC对象 |

### 设置NPC特效
`setnpceffect`

| 参数     | 类型     | 空   | 默认 | 注释                               |
| :------- | :------- | :--- | ---- | ---------------------------------- |
| player   | `object` | 否   |      | 玩家对象                           |
| NPCIndex | `int`    | 否   |      | NPC索引（NPC配置表中的ID）         |
| Effect   | `int`    | 否   |      | 特效ID<br>5055-感叹号<br>5056-问号 |
| X        | `int`    | 否   |      | X坐标                              |
| Y        | `int`    | 否   |      | Y坐标                              |

```
当X、Y<0时，默认取NPC的坐标
```

### 删除NPC特效
`delnpceffect`

| 参数     | 类型     | 空   | 默认 | 注释                       |
| :------- | :------- | :--- | ---- | -------------------------- |
| player   | `object` | 否   |      | 玩家对象                   |
| NPCIndex | `int`    | 否   |      | NPC索引（NPC配置表中的ID） |

### 关闭当前的NPC对话框
`close`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | ---- | -------- |
| player | `object` | 否   |      | 玩家对象 |

### 给NPC注册Lua消息
`regnpcmsg`

| 参数     | 类型  | 空   | 默认 | 注释                       |
| :------- | :---- | :--- | ---- | -------------------------- |
| msgId    | `int` | 否   |      | 消息ID                     |
| NPCIndex | `int` | 否   |      | NPC索引（NPC配置表中的ID） |

```
给NPC注册LUA消息后，当服务器接收到Lua消息，如果有对应的NPC且玩家在NPC有效区域（同地图且在NPC附近）内，则激活NPC脚本内容（相当于点击了NPC）
```

### 获取NPC对象的Idx
`getnpcindex`

| 参数   | 类型     | 空   | 默认 | 注释                       |
| :----- | :------- | :--- | ---- | -------------------------- |
| npc    | `object` | 否   |      | NPC对象                    |
| result | `int`    | 否   |      | NPC索引（NPC配置表中的ID） |

### 调用其他NPC的lua函数
`callfunbynpc` 注意：如果开启多线程，会导致执行失败

| 参数      | 类型     | 空   | 默认 | 注释                                                                                                |
| :-------- | :------- | :--- | ---- | --------------------------------------------------------------------------------------------------- |
| play      | `object` | 否   |      | 玩家对象                                                                                            |
| npcidx    | `int`    | 否   |      | NPC索引（NPC配置表中的ID），特殊npcid:QF=999999999,QM=999999996,LuaCond=999999995,LuaFunc=999999994 |
| delaytime | `int`    | 否   |      | 延迟时间ms,0立即执行                                                                                |
| func      | `string` | 否   |      | 函数名                                                                                              |
| sParam    | `string` | 否   |      | 参数                                                                                                |

```
callfunbynpc(self, 999999999, 1000, 'test', 'abc=1')
  
function test(self, p1)
    release_print(self, p1)     
end
```

### 打开NPC大窗口
`openmerchantbigdlg`

| 参数   | 类型  | 空   | 默认 | 注释                        |
| :----- | :---- | :--- | ---- | --------------------------- |
| path   | `str` | 否   |      | 路径                        |
| pos    | `int` | 否   |      | 显示位置                    |
| x      | `int` | 否   |      | X坐标                       |
| y      | `int` | 否   |      | Y坐标                       |
| height | `int` | 否   |      | 高度                        |
| width  | `int` | 否   |      | 宽度                        |
| bool   | `int` | 否   |      | 是否显示关闭按钮            |
| closeX | `int` | 否   |      | 关闭按钮X坐标               |
| closeY | `int` | 否   |      | 关闭按钮Y坐标               |
| isMove | `int` | 否   |      | 是否可以移动(0不移动 1移动) |

### 获取当前虚拟机id[npcid]

`getsysindex`

> **<font color="#808080" style="font-size: 13px;">引擎64_23.12.07新增接口</font>**

| 参数   | 类型      | 空   | 默认 | 注释                                                                                                |
| :----- | :-------- | :--- | :--- | :-------------------------------------------------------------------------------------------------- |
| result | `integer` | 否   |      | npcID（NPC配置表中的ID）<br>特殊npcid:QF=999999999,QM=999999996,LuaCond=999999995,LuaFunc=999999994 |


# NPC界面



### NPC界面文本发送
`say`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|actor     |`object`      |否   |    |   玩家对象 |
|msg     |`string`      |否   |    |  界面文本内容  |

```lua
function main(actor)
    local msg = [[
        <Button|a=0|x=180.0|y=2.0|tips={点击查看【金钻服务】/FCOLOR=250}|tipsx=10|tipsy=110|nimg=public/00000361.png|color=255|size=18|pimg=public/00000362.png|link=@linkclick,参数1,参数2,3>
    ]]
    say(actor,msg)
end

[[
    注意:如果需要传递参数到脚本接口，只需要在后面接 逗号 参数
    不支持老传奇传递参数的方式，lua里全部通过 @xxxx,1,2,3 这种方式传递参数
]]
function linkclick(actor,...)
    release_print("传入参数",...)
end
```
- **注意：一定小写**

### 增加自定义按钮
`addbutton`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|actor     |`object`      |否   |    |   玩家对象 |
|windowid     |`integer`      |否   |    |  主窗口ID  |
|buttonid     |`integer`      |否   |    |   按钮ID |
|icon     |`string`      |否   |    |  图标内容  |

```
参数1:主窗口ID
101 主界面左上 建议开始微调坐标 0 0
102 主界面右上 建议开始微调坐标 -65 0
103 主界面左下 建议开始微调坐标 0 -92
104 主界面右下 建议开始微调坐标 -62 -92
105 主界面左中 建议开始微调坐标 0 0
106 主界面上中 建议开始微调坐标 0 0
107 主界面右中 建议开始微调坐标 -62 0
108 主界面下中 建议开始微调坐标 0 -92
109 主界面切换按钮
110 主界面任务界面
1101 主界面最顶左上
1102 主界面最顶右上
1103 主界面最顶左下
1104 主界面最顶右下

2 角色-外框主面板-(切换页签按钮也会在)

3    角色-装备-上层
3001 角色-装备-下层

301  别人装备界面-上层
3002 别人装备界面-下层

4    角色-状态
5    角色-属性
6    角色-技能
7    角色-背包
8    小地图
9    行会 行会列表
10   行会 行会创建
11   行会 主面板
12   行会 行会成员
14   邮件 
15   好友

16   大仓库面板
19   设置 保护
20   设置 拾取
21   设置 战斗
22   设置 操作
23   角色-称号
29   拍卖行 主面板
30   拍卖行 世界拍卖
31   拍卖行 行会拍卖
32   拍卖行 我的竞拍
33   拍卖行 我的上架
34   拍卖行 竞价
35   拍卖行 一口价
36   拍卖行 上架
37   拍卖行 下架
38   拍卖行 超时
39   角色-时装
3901 角色-查看别人时装

3902  时装界面-下层
40   充值界面
41   首饰盒
42   合成面板
43   怪物大血条
44   答题验证界面
45   自定义排行榜
46   图形验证界面

300  新内挂-基础
305  新内挂-视距
302  新内挂-战斗
303  新内挂-保护
304  新内挂-挂机

701  商城-装饰
702  商城-补给
703  商城-强化
704  商城-好友

2301 他人称号

3903  时装界面-下层
4101 查看他人首饰盒

7001 背包第一页
7002 背包第二页
7003 背包第三页
112  PC端聊天栏
50002 英雄-角色外框主面板(二合一面板不支持挂靠)
50003 英雄-装备 上层
53001 英雄-装备 下层
50301 英雄-查看别人装备-上层
53002 英雄-查看别人装备-下层
50004  英雄-状态
50005  英雄-属性
50006  英雄-技能
50007  英雄-背包
50023  英雄-称号
52301  查看他人英雄称号
50039  英雄-时装
53901  查看他人英雄时装
50041  英雄-首饰盒
54101  查看他人英雄首饰盒

401    内功状态
402    内功技能
403    内功经络
40301    经络-冲脉
40302    经络-阴跷
40303    经络-阴维
40304    经络-任脉
40305    经络-奇经
404    内功连击 
501    英雄内功状态
502    英雄内功技能
503    英雄内功经络
50301    英雄经络-冲脉
50302    英雄经络-阴跷
50303    英雄经络-阴维
50304    英雄经络-任脉
50305    英雄经络-奇经
504    英雄内功连击

参数2：图标ID  (1~XX不限制,不可重复)

参数3：图标内容
<Button|a=0|x=180.0|y=2.0|tips={点击查看【金钻服务】/FCOLOR=250}|tipsx=10|tipsy=110|nimg=custom/zdy/tubiao/jzhuiyuan1.png|color=255|size=18|pimg=custom/zdy/tubiao/jzhuiyuan1.png|link=@会员服务>
```

### 删除自定义按钮
`delbutton`

| 参数     | 类型      | 空   | 默认 | 注释     |
| :------- | :-------- | :--- | :--- | :------- |
| actor    | `object`  | 否   |      | 玩家对象 |
| windowid | `integer` | 否   |      | 主窗口ID |
| buttonid | `integer` | 否   |      | 按钮ID   |

### 打开OK框
`openupgradedlg`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |
| title | `string` | 否   |      | OK框标题 |

### 回收OK框物品
`takedlgitem`

| 参数  | 类型      | 空   | 默认 | 注释                   |
| :---- | :-------- | :--- | :--- | :--------------------- |
| actor | `object`  | 否   |      | 玩家对象               |
| count | `integer` | 否   |      | 数量(针对叠加物品有效) |

### 返回OK框物品到背包
`reclaimitem`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |

------------

### 自定义OK框
```lua
function main(actor)
    local msg = [[<Img|a=0|x=0.0|y=0.0|width=600|height=250|scale9t=100|scale9r=220|img=public/bg_npc_11.jpg|scale9l=10|scale9b=100|bg=1>
    <Button|a=0|x=596.0|y=1.0|size=18|color=255|nimg=public/1900000510.png|pimg=public/1900000511.png|link=@exit>
    <Text|a=0|x=385.0|y=50.0|size=16|color=251|text=自动放入木剑到OK框|link=@takeonfunc>
    <Text|a=0|x=385.0|y=100.0|size=16|color=251|text=返回OK框内物品到包裹|link=@backbagfunc>
    <Text|a=0|x=385.0|y=150.0|size=16|color=251|text=删除OK框内物品|link=@delitemfunc>
    <Text|a=0|x=385.0|y=200.0|size=16|color=251|text=获取ok框内的对象|link=@getfunc>
    <ITEMBOX|x=49.0|y=50.0|width=70|height=70|tips=<只能放入\武器/FCOLOR=249>|boxindex=1|stdmode=*|tipsx=4|tipsy=100|img=public/1900000651_3.png>]]
    say(actor,msg)
end

function delitemfunc(actor)
    delboxitem(actor,1,2)
end

function backbagfunc(actor)
    returnboxitem(actor,1)
end

function takeonfunc(actor)
    bagitemintobox(actor,"木剑",1)
end

function getfunc(actor)
    local itemobj = getboxitem(actor,1)
    local itemName = getiteminfo(actor,itemobj,7)
    release_print("物品框内道具",itemName)
end
```

### 把包裹中的物品放入自定义OK框中

`bagitemintobox`

| 参数  | 类型               | 空   | 默认 | 注释                |
| :---- | :----------------- | :--- | :--- | :------------------ |
| actor | `object`           | 否   |      | 玩家对象            |
| item  | `string`/`integer` | 否   |      | 物品名称<br>物品唯一id |
| idx   | `integer`          | 否   |      | OK框编号(0~99)      |

### 把自定义OK框物品返回到包裹
`returnboxitem`

| 参数  | 类型      | 空   | 默认 | 注释           |
| :---- | :-------- | :--- | :--- | :------------- |
| actor | `object`  | 否   |      | 玩家对象       |
| idx   | `integer` | 否   |      | OK框编号(0~99) |

### 删除自定义OK框中的物品
`delboxitem`

| 参数  | 类型      | 空   | 默认 | 注释                                                  |
| :---- | :-------- | :--- | :--- | :---------------------------------------------------- |
| actor | `object`  | 否   |      | 玩家对象                                              |
| idx   | `integer` | 否   |      | OK框编号(0~99)                                        |
| num   | `integer` | 否   |      | 删除数量;参数只有是叠加物品时才会有效，为空则全部删除 |

### 获取自定义OK框中的物品对象
`getboxitem`

| 参数  | 类型      | 空   | 默认 | 注释           |
| :---- | :-------- | :--- | :--- | :------------- |
| actor | `object`  | 否   |      | 玩家对象       |
| idx   | `integer` | 否   |      | OK框编号(0~99) |

### 更新OK框物品

`updateboxitem`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.03.14新增接口</font>**

| 参数  | 类型      | 空   | 默认 | 注释     |
| :---- | :-------- | :--- | :--- | :------- |
| actor | `string`  | 否   |      | 玩家对象 |
| boxID | `integer` | 否   |      | OK框编号 |


# 跨服设置



&lt;font color="#FF0000" style="font-family: Fixedsys;font-size: 40px;"&gt;必读：&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;1.MapInfo.txt配置必须有0和3号地图，引擎部分操作需要有这两张地图的存在。 &lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;2.跨服服务器,跨服QF 不支持 修改物品与人物属性！！(没有实体npc都属于QF)&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;3.跨服服务器,不支持 人物背包掉落物品&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;4.跨服服务器,不保存 自定义全局变量&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;5.跨服服务器,T变量不支持同步,需要使用变量传递功能传递,字符串变量(Str)只支持100个字符&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;6.跨服服务器,不支持对称号进行操作(跨服QF里保存在数据库的数据都不能修改)&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;7.跨服服务器,不支持地图操作检测(进入跨服后地图变量将固定为进入的地图,返回本服才会刷新)&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;8.跨服服务器,不支持拍卖行,交易,邮件,交易行&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;9.跨服服务器,支持 1：捡取物品到背包 2：掉落身上装备&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;10.退出跨服服务器,读取的是本服 Mir200\Market_Def\QFunction-0.lua 函数名:kuafuend 跨服结束触发&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;11.进入跨服服务器,读取的是跨服 Mir200-KF\Market_Def\QFunction-0.lua 函数名:kflogin 跨服成功触发&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;12.进入跨服服务器,读取的是跨服 Mir200-KF\Envir\cfg_mongen.xls&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;13.进入跨服服务器,读取的是本地 Mir200\MapInfo.txt 地图参数：Kuafu&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;14.进入跨服服务器,部分GM命令不支持&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;15.加载跨服脚本,必须同步到本服后再加载,重读跨服NPC脚本或主服NPC脚本 需要使用主服引擎重读&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;16.进入跨服服务器,定时器 新增参数是否跨服继续执行&lt;/font&gt;<br />
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 18px;"&gt;17.进入跨服服务器,机器人脚本 新增参数空=本服执行 1=跨服执行 2=本服和跨服一起执行 &lt;/font&gt;

```
    #AutoRun NPC SEC 5 @shili2 2
```

<br />

-------------

<br />

##跨服说明：

&lt;font color="#00BFFF" style="font-family: Fixedsys;font-size: 15px;"&gt;1.特别注意:跨服地图里面的NPC执行是脚本是返回到本服的，所以如果想在跨服执行NPC功能&lt;/font&gt;
&lt;font color="#00BFFF" style="font-family: Fixedsys;font-size: 15px;"&gt;2.建议做到跨服QFunction-0.lua  函数名:kflogin  跨服成功触发里面 比如拾取小精灵 个人定时器等等&lt;/font&gt;
&lt;font color="#00BFFF" style="font-family: Fixedsys;font-size: 15px;"&gt;3.跨服NPC里的变量常量为本服的, 跨服QF,QM里的变量常量为跨服的(部分功能跨服QF不支持)&lt;/font&gt;

<br />

第一步：例如本地版本目录为：D:\Mirserver  复制一份Mir200命名Mir200-KF

第二步：修改Mir200-KF\!Setup.txt [Share]项 下面的路径为：D:\Mirserver\Mir200-KF\ (如果不修改，会读取到本服脚本内容了)

第三步：打开引擎控制器--配置向导--勾选开启跨服--点击保存

第四步：打开Mir200-KF文件m2server.exe程序(跨服需要打开2个M2程序)

注:跨服需要清空MapQuest.txt文件,不然M2会卡在加载任务地图

<br />

-------------

###跨服需要的文件:
cfg_kuafuval.xls（私人变量同步文件,U变量全部支持  标识全部支持  自定义HUMAN类型变量 字符串(String) 整型(Integer) 各50个）
注:T变量与全局变量不支持同步,需要使用变量传递功能传递,字符串变量(String)只支持100个字符
MonGen.txt  （跨服刷怪根据地图参数带：Kuafu参数的自动会刷到跨服服务器，本服就不会刷新了） 

Mapinfo.txt （跨服地图根据地图参数带：Kuafu参数跨服服务器自动加载

cfg_npclist.xls 需要在该表中第17列配置显示（跨服NPC根据地图参数带：Kuafu跨服服务器自动加载）

<br />

-------------

##跨服接口

### 跨服通知触发本服QF

`kfbackcall`

| 参数   | 类型      | 空   | 默认 | 注释                                                                 |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------------------- |
| id     | `integer` | 否   |      | 消息id（1-99）                                                       |
| userid | `string`  | 否   |      | 玩家userid<br />填`"0"`则是以系统对象发送通知,通知所有连接跨服的服务器 |
| parama | `string`  | 否   |      | 传递的字符串1(字符串)                                                |
| paramb | `string`  | 否   |      | 传递的字符串2(字符串)                                                |
```lua
    local userID = getbaseinfo(actor, 2)
    kfbackcall(22,userID,"跨服发送1","跨服发送2")   --玩家对象发送
    -- kfbackcall(22,"0","跨服发送3","跨服发送4")        --系统对象发送

    --跨服通知触发本服QF
    function kfsyscall22(actor,arg1,arg2)
        local role_name = getbaseinfo(actor, 1)
        release_print("跨服通知触发本服QF",role_name,arg1,arg2)
    end

```

<br />

### 本服通知触发跨服QF

`bfbackcall`

| 参数   | 类型      | 空   | 默认 | 注释                                        |
| :----- | :-------- | :--- | :--- | :------------------------------------------ |
| id     | `integer` | 否   |      | 消息id（1-99）                              |
| userid | `string`  | 否   |      | 玩家userid<br />填`"0"`则是以系统对象发送通知 |
| parama | `string`  | 否   |      | 传递的字符串1(字符串)                       |
| paramb | `string`  | 否   |      | 传递的字符串2(字符串)                       |
```lua
    local userID = getbaseinfo(actor, 2)
    bfbackcall(22,userID,"本服发送1","本服发送2")   --玩家对象发送
    -- bfbackcall(22,"0","本服发送3","本服发送4")        --系统对象发送

    function bfsyscall22(actor,arg1,arg2)
        local role_name = getbaseinfo(actor, 1)
        release_print("本服通知触发跨服QF",role_name,arg1,arg2)
    end
```

<br />

### 跨服变量传递

`synzvar`

| 参数    | 类型      | 空   | 默认 | 注释                                                                     |
| :------ | :-------- | :--- | :--- | :----------------------------------------------------------------------- |
| itype   | `integer` | 否   |      | 变量类型<br />1=全局G变量<br />2=全局A变量<br />3=全局自定义变量<br />4=行会变量 |
| astr    | `string`  | 否   |      | 变量名<br />itype=4的时传入:`行会名称/变量名`                              |
| bstr    | `string`  | 否   |      | 存入本服全局变量名                                                       |
| func_id | `integer` | 否   |      | 同步成功后触发函数id<br />如传入1则同步成功后触发`kfsynvar1`函数           |

```lua
    -- 同步全局G/A/自定义变量
    local varName_1 = "G15"
    local varName_2 = "G16"
    if checkkuafuserver() then
        setsysvar(varName_1, getsysvar(varName_1) + 1)
        release_print("跨服",varName_1, "valValue" .. getsysvar(varName_1))
    else
        if not kfsynvar1 then
            function kfsynvar1()
                release_print("同步成功",getsysvar(varName_2))
            end
        end
        synzvar(1,varName_1,varName_2,1)
    end

    -- 同步行会变量
    local varName_1 = "行会自定义变量"
    local varName_2 = "A10"
    if checkkuafuserver() then
        local guild = getmyguild(actor)
        if guild ~= "0" then
            iniguildvar(guild, "integer", varName_1)
            local value = getguildvar(guild, varName_1) + 1
            setguildvar(guild, varName_1, value)
        end
    else
        local guild = getmyguild(actor)
        if guild ~= "0" then
            local guild_name = getguildinfo(guild,1)
            if not kfsynvar996 then
                function kfsynvar996()
                    LOGPrint("同步成功,行会变量",getsysvar(varName_2))
                end
            end
            synzvar(4,guild_name.."/"..varName_1,varName_2,996)
        end
    end
```

### 检测当前服务器是否为跨服服务器

`checkkuafuserver`

```lua
    local isKuafuSever = checkkuafuserver()
    release_print("当前服务器是否为跨服服务器",type(isKuafuSever),tostring(isKuafuSever))
```

<br />

### 检测当前人物是否在跨服的地图

`checkkuafu`

| 参数  | 类型  | 空   | 默认 | 注释     |
| :---- | :---- | :--- | :--- | :------- |
| actor | `obj` | 是   |      | 玩家对象 |
```lua
        local isKuafuMap = checkkuafu(actor)
        release_print("当前人物是否在跨服的地图",type(isKuafuMap),tostring(isKuafuMap))
```

<br />

### 检查跨服连接是否正常连接

`checkkuafuconnect`

```lua
    local isKuafuSuc = checkkuafuconnect()
    release_print("跨服连接是否正常连接",type(isKuafuSuc),tostring(isKuafuSuc))
```

<br />

### 所有跨服玩家回本服 根据执行区服自行处理

`kuafuusergohome`

```lua
    kuafuusergohome()
    release_print("所有跨服玩家回本服")
```


# 国家系统

###### 更新时间：引擎64_23.03.23



## 说明

1. 合区后只保留主服的国家人员和ID其他国家不会合并在一起,可通过脚本命令自行全部删除;
2. 国家战争地图参数：FIGHT6 默认不掉落 （FIGHT6(0)，不掉落，FIGHT6(1) 掉落）国家战争地图 进入该地图人物颜色会变色 杀人不加PK值;
3. 系统默认职位编号配置路径：`Mir200\Envir\Nations\Nations.ini`;
4. 国家攻击模式开启:`M2 - 参数设置 - 状态控制 - 允许国家攻击模式`;
5. 国家基础设置:`M2 - 功能设置 - 其他设置 - 国家设置`;

## 常量

国家名称：`&lt;$NATIONNAME&gt;`
国家人数：`&lt;$NATIONPEOPLE&gt;`
国家ID常量：`&lt;$NATIONID&gt;`
国家职位名称常量：`&lt;$nationjob1&gt;` ~ `&lt;$nationjob10&gt;`
玩家职位ID常量：`&lt;$NATIONJOBID&gt;`

## 接口

### 创建国家
`createnation`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| nIdx   | `integer` | 否   |      | 国家ID (1~100) |
| name   | `string`  | 否   |      | 国家名称       |
| maxNum | `integer` | 否   |      | 限制人数       |
```lua
    createnation(actor,5,'华夏',100)
```
### 删除国家
`delnation`

| 参数 | 类型      | 空   | 默认 | 注释   |
| :--- | :-------- | :--- | :--- | :----- |
| nIdx | `integer` | 否   |      | 国家ID |

### 检查国家是否创建
`checkation`

| 参数 | 类型      | 空   | 默认 | 注释   |
| :--- | :-------- | :--- | :--- | :----- |
| nIdx | `integer` | 否   |      | 国家ID |

### 设置当前人物在国家的职位格式
`setnationking`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| jobIdx | `integer` | 否   |      | 职位编号 |

### 修改国家职位名称
`setnationrank`

| 参数    | 类型      | 空   | 默认 | 注释           |
| :------ | :-------- | :--- | :--- | :------------- |
| play    | `object`  | 否   |      | 玩家对象       |
| nIdx    | `integer` | 否   |      | 国家ID (1~100) |
| jobIdx  | `integer` | 否   |      | 职位编号       |
| jobName | `string`  | 否   |      | 职位名称       |
```lua
    setnationrank(actor,5,3,'汉奸')
```

### 加入/退出国家
`joinnational`

&gt; 异步接口

| 参数   | 类型      | 空   | 默认 | 注释                         |
| :----- | :-------- | :--- | :--- | :--------------------------- |
| play   | `object`  | 否   |      | 玩家对象                     |
| nIdx   | `integer` | 否   |      | 国家ID (1~100),填0退出国家   |
| jobIdx | `integer` | 否   |      | 职位编号（0-9 不填 默认为0） |
```lua
    joinnational(actor,5,9) --加入国家
    joinnational(actor,0)   --退出国家
```

### 检测加入国家
`checknational`

| 参数   | 类型      | 空   | 默认 | 注释                              |
| :----- | :-------- | :--- | :--- | :-------------------------------- |
| play   | `object`  | 否   |      | 玩家对象                          |
| nIdx   | `integer` | 否   |      | 国家编号 0~100  0代表没有加入国家 |
| result | `bool`    | 是   |      | 返回值，布尔值                    |

### 检查国家人物总数
`checknationhumcount`

| 参数   | 类型      | 空   | 默认 | 注释           |
| :----- | :-------- | :--- | :--- | :------------- |
| play   | `object`  | 否   |      | 玩家对象       |
| sFlag  | `string`  | 否   |      | 比较符（=&lt;&gt;）  |
| iValue | `integer` | 否   |      | 人数           |
| result | `bool`    | 是   |      | 返回值，布尔值 |
```lua
    checknationhumcount(actor,'&gt;',100)
```

### 国家宣战
`nationswar`

| 参数   | 类型      | 空   | 默认 | 注释                      |
| :----- | :-------- | :--- | :--- | :------------------------ |
| play   | `object`  | 否   |      | 玩家对象                  |
| nIdx   | `integer` | 否   |      | 国家ID                    |
| iValue | `integer` | 否   |      | 时间,单位小时(0=立即关闭) |
```lua
    nationswar(actor,5, 2000)
```

### 监测国家战争状态
`isnationswar`

| 参数   | 类型     | 空   | 默认 | 注释           |
| :----- | :------- | :--- | :--- | :------------- |
| play   | `object` | 否   |      | 玩家对象       |
| result | `bool`   | 是   |      | 返回值，布尔值 |

### 判断国家之间是否宣战

`iswarnation`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数       | 类型      | 空   | 默认 | 注释     |
| :--------- | :-------- | :--- | :--- | :------- |
| nationIDX1 | `integer` | 否   |      | 国家ID   |
| nationIDX2 | `integer` | 否   |      | 国家ID   |
| result     | `bool`    | 否   |      | 是否宣战 |
```lua
    local bool = iswarnation(countID_1,countID_2)
    LOGPrint("国家宣战",bool)
```

### 国家宣战

`setnationwar`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数       | 类型      | 空   | 默认 | 注释         |
| :--------- | :-------- | :--- | :--- | :----------- |
| nationIDX1 | `integer` | 否   |      | 国家ID       |
| nationIDX2 | `integer` | 否   |      | 国家ID       |
| result     | `bool`    | 否   |      | 是否宣战成功 |
```lua
    local bool = iswarnation(countID_1,countID_2)
    LOGPrint("是否宣战成功",bool)
```

### 获取国家人数

`getnationmembercount`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数      | 类型      | 空   | 默认 | 注释     |
| :-------- | :-------- | :--- | :--- | :------- |
| nationIDX | `integer` | 否   |      | 国家ID   |
| result    | `integer` | 否   |      | 国家人数 |
```lua
    local count = getnationmembercount(countID_1)
    LOGPrint("国家人数",count)
```
# HTTP请求

###### 更新时间：引擎64_23.06.28

外部工具推荐：需要架设 Httppost自定义数据传输推荐使用：[http://httppost.cn/](http://httppost.cn/ "http://httppost.cn/") (非官方).
(相关产品由第三方提供，996引擎方不负责售前售后服务，请用户自行甄别选择)

------------

### HTTP请求

`httppost`
> 注意：不提供回调函数与返回值

## 参数
|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|url |是  |str | 链接地址|
|suffix |是  |str | 请求信息|
|head |是  |json字符串格式 | 请求头|
## 返回值
<span class="hljs-string">类型：无返回值</span>

## 示例代码
```php
<?php
    // echo json_encode(['a'=>123]);
    $_data = [];
    $_data['server'] = $_SERVER;
    $_data['files'] = $_FILES;
    $_data['post'] = $_POST;
    $_data['tokenn'] = '996633';
    $_data['get'] = $_GET;
    $_data['input'] = json_decode(file_get_contents('php://input'),true);
    echo json_encode($_data, JSON_UNESCAPED_UNICODE);
```

```lua
示例
    httppost("http://localhost/php/test.php",'{token:mir200post}','{Host:system}')

debug日志
{
    "server":{
        "PATH":"C:\\Program Files (x86)\\Common Files\\Oracle\\Java\\javapath;F:\\VMware\\bin\\;C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files\\TortoiseSVN\\bin;C:\\Microsoft VS Code\\bin;C:\\Program Files (x86)\\GtkSharp\\2.12\\bin;C:\\Program Files (x86)\\Windows Kits\\8.1\\Windows Performance Toolkit\\;C:\\Program Files\\Microsoft SQL Server\\110\\Tools\\Binn\\;C:\\Program Files (x86)\\Microsoft SDKs\\TypeScript\\1.0\\;C:\\Program Files\\Microsoft SQL Server\\120\\Tools\\Binn\\;C:\\Users\\admin\\AppData\\Local\\Programs\\Python\\Python39\\Scripts\\;C:\\Users\\admin\\AppData\\Local\\Programs\\Python\\Python39\\;C:\\Cocos\\Cocos2d-x\\Cocos2d-x-3.10\\templates;C:\\Cocos\\Cocos2d-x\\Cocos2d-x-3.10\\tools\\cocos2d-console\\bin;C:\\Users\\admin\\AppData\\Local\\Microsoft\\WindowsApps",
        "SYSTEMROOT":"C:\\Windows",
        "COMSPEC":"C:\\Windows\\system32\\cmd.exe",
        "PATHEXT":".COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC",
        "WINDIR":"C:\\Windows",
        "PHPRC":"F:\/php\/phpstudy_pro\/Extensions\/php\/php7.3.4nts",
        "_FCGI_SHUTDOWN_EVENT_":"8968",
        "HTTP_CONNECTION":"close",
        "SCRIPT_NAME":"\/php\/test.php",
        "REQUEST_URI":"\/php\/test.php",
        "QUERY_STRING":"",
        "REQUEST_METHOD":"POST",
        "SERVER_PROTOCOL":"HTTP\/1.1",
        "GATEWAY_INTERFACE":"CGI\/1.1",
        "REMOTE_PORT":"49742",
        "SCRIPT_FILENAME":"F:\/php\/phpstudy_pro\/WWW\/php\/test.php",
        "SERVER_ADMIN":"admin@example.com",
        "CONTEXT_DOCUMENT_ROOT":"F:\/php\/phpstudy_pro\/WWW",
        "CONTEXT_PREFIX":"",
        "REQUEST_SCHEME":"http",
        "DOCUMENT_ROOT":"F:\/php\/phpstudy_pro\/WWW",
        "REMOTE_ADDR":"::1",
        "SERVER_PORT":"80",
        "SERVER_ADDR":"::1",
        "SERVER_NAME":"system",
        "SERVER_SOFTWARE":"Apache\/2.4.39 (Win64) OpenSSL\/1.1.1b mod_fcgid\/2.3.9a mod_log_rotate\/1.02",
        "SERVER_SIGNATURE":"",
        "SystemRoot":"C:\\Windows",
        "HTTP_CACHE_CONTROL":"no-cache",
        "CONTENT_LENGTH":"16",
        "HTTP_USER_AGENT":"Microsoft Internet Explorer",
        "HTTP_HOST":"system",
        "CONTENT_TYPE":"application\/x-www-form-urlencoded",
        "FCGI_ROLE":"RESPONDER",
        "PHP_SELF":"\/php\/test.php",
        "REQUEST_TIME_FLOAT":1688001980.321139,
        "REQUEST_TIME":1688001980
    },
    "files":[

    ],
    "post":{
        "token":"mir200post"
    },
    "tokenn":"996633",
    "get":[

    ],
    "input":null
}
```

------------

`httpget`

## 参数
|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|url |是  |str | 链接地址|
## 返回值
<span class="hljs-string">类型：无返回值</span>

```lua
示例
	httpget("http://localhost/php/test.php")

debug日志
{
    "server":{
        "PATH":"C:\\Program Files (x86)\\Common Files\\Oracle\\Java\\javapath;F:\\VMware\\bin\\;C:\\Windows\\system32;C:\\Windows;C:\\Windows\\System32\\Wbem;C:\\Windows\\System32\\WindowsPowerShell\\v1.0\\;C:\\Windows\\System32\\OpenSSH\\;C:\\Program Files\\TortoiseSVN\\bin;C:\\Microsoft VS Code\\bin;C:\\Program Files (x86)\\GtkSharp\\2.12\\bin;C:\\Program Files (x86)\\Windows Kits\\8.1\\Windows Performance Toolkit\\;C:\\Program Files\\Microsoft SQL Server\\110\\Tools\\Binn\\;C:\\Program Files (x86)\\Microsoft SDKs\\TypeScript\\1.0\\;C:\\Program Files\\Microsoft SQL Server\\120\\Tools\\Binn\\;C:\\Users\\admin\\AppData\\Local\\Programs\\Python\\Python39\\Scripts\\;C:\\Users\\admin\\AppData\\Local\\Programs\\Python\\Python39\\;C:\\Cocos\\Cocos2d-x\\Cocos2d-x-3.10\\templates;C:\\Cocos\\Cocos2d-x\\Cocos2d-x-3.10\\tools\\cocos2d-console\\bin;C:\\Users\\admin\\AppData\\Local\\Microsoft\\WindowsApps",
        "SYSTEMROOT":"C:\\Windows",
        "COMSPEC":"C:\\Windows\\system32\\cmd.exe",
        "PATHEXT":".COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC",
        "WINDIR":"C:\\Windows",
        "PHPRC":"F:\/php\/phpstudy_pro\/Extensions\/php\/php7.3.4nts",
        "_FCGI_SHUTDOWN_EVENT_":"8860",
        "SCRIPT_NAME":"\/php\/test.php",
        "REQUEST_URI":"\/php\/test.php",
        "QUERY_STRING":"",
        "REQUEST_METHOD":"GET",
        "SERVER_PROTOCOL":"HTTP\/1.1",
        "GATEWAY_INTERFACE":"CGI\/1.1",
        "REMOTE_PORT":"54798",
        "SCRIPT_FILENAME":"F:\/php\/phpstudy_pro\/WWW\/php\/test.php",
        "SERVER_ADMIN":"admin@example.com",
        "CONTEXT_DOCUMENT_ROOT":"F:\/php\/phpstudy_pro\/WWW",
        "CONTEXT_PREFIX":"",
        "REQUEST_SCHEME":"http",
        "DOCUMENT_ROOT":"F:\/php\/phpstudy_pro\/WWW",
        "REMOTE_ADDR":"::1",
        "SERVER_PORT":"80",
        "SERVER_ADDR":"::1",
        "SERVER_NAME":"localhost",
        "SERVER_SOFTWARE":"Apache\/2.4.39 (Win64) OpenSSL\/1.1.1b mod_fcgid\/2.3.9a mod_log_rotate\/1.02",
        "SERVER_SIGNATURE":"",
        "SystemRoot":"C:\\Windows",
        "HTTP_CONNECTION":"close",
        "HTTP_HOST":"localhost",
        "HTTP_USER_AGENT":"Mozilla\/4.0 (compatible; MSIE 7.0; Windows NT 10.0; Win64; x64; Trident\/7.0; .NET4.0C; .NET4.0E; .NET CLR 2.0.50727; .NET CLR 3.0.30729; .NET CLR 3.5.30729)",
        "HTTP_ACCEPT_ENCODING":"gzip, deflate",
        "HTTP_UA_CPU":"AMD64",
        "HTTP_ACCEPT_LANGUAGE":"zh-cn",
        "HTTP_ACCEPT":"*\/*",
        "FCGI_ROLE":"RESPONDER",
        "PHP_SELF":"\/php\/test.php",
        "REQUEST_TIME_FLOAT":1687748512.883079,
        "REQUEST_TIME":1687748512
    },
    "files":[

    ],
    "post":[

    ],
    "tokenn":"996633",
    "get":[

    ],
    "input":null
}
```

# 英雄相关

###### 更新时间：引擎64_23.03.23

## 触发

### 英雄登陆触发
`herologin`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 英雄创建触发
`createherook`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 英雄取名成功触发
`checkusernameok`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 英雄取名失败触发
`checkusernameno`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

```lua
    local role_name = getbaseinfo(actor,1)
    local hero_name = role_name.."A英雄"
    checkheroname(actor,hero_name)

    [[英雄取名成功触发]]
    function checkusernameok(actor)
        release_print("英雄取名成功触发,之后去创建英雄")
        local job,sex = getbaseinfo(actor,7),getbaseinfo(actor,8)
        local role_name = getbaseinfo(actor,1)
        local hero_name = role_name.."A英雄"
        createhero(actor, hero_name, job, sex)
    end
    
    [[英雄取名失败触发]]
    function checkusernameno(actor)
        sendmsg(actor, 1, '{"Msg":"<font color=\'#ff0000\'>英雄名字已经存在</font>","Type":9}')
    end

    [[英雄创建触发]]
    function createherook(actor)
        release_print("创建成功,召唤英雄")
        recallhero(actor)
    end

    [[英雄登陆触发]]
    function herologin(actor)
        release_print("英雄登陆")
    end
```

## 接口

### 获取英雄对象
`gethero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|result |`object`      |否   |   |    返回英雄对象 不存在返回"0"   |

### 是否有英雄
`hashero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|result |`object`      |否   |   |    true=有英雄<br>false=没有英雄   |

### 判断对象是否为英雄
`ishero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|object     |`object`      |否   |    |判断对象 |
|result |`bool`      |否   |   |    true=是英雄<br>false=不是英雄  |

### 判断英雄是否为唤出状态
`isherorecall`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 设置英雄名称
`checkheroname`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|name     |`string`      |否   |    |英雄名称 |

### 创建英雄
`createhero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|name     |`string`      |否   |    |英雄名称 |
|job     |`integer`      |否   |    |职业(0-战 1-法 2-道) |
|sex     |`integer`      |否   |    |性别(0-男 1-女) |

### 删除英雄
`delhero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 召唤英雄
`recallhero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

### 收回英雄
`unrecallhero`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |

------------

### 英雄改名接口

`changeheroname`

> **<font color="#808080" style="font-size: 13px;">引擎64_23.10.24新增接口</font>**

| 参数     | 类型     | 空   | 默认 | 注释       |
| :------- | :------- | :--- | :--- | :--------- |
| player   | `object` | 否   |      | 玩家对象   |
| heroName | `string` | 否   |      | 英雄新名字 |
```lua
    changeheroname(player,role_name.."AA英雄")

    --QFunction-0.lua
    function queryingheroname(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>正在查询请稍后。。。</font>","Type":9}')
    end
    function queryheronameok(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>查询成功，该名称可以使用</font>","Type":9}')
    end
    function changeingheroname(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>正在修改请稍后。。。</font>","Type":9}')
    end
    function changeheronameok(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>你的名字修改成功</font>","Type":9}')
    end
    function heronameLengthfail(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>名字长度不允许超过30个字符！</font>","Type":9}')
    end
    function heronamefilter(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>该名字存在非法字符！</font>","Type":9}')
    end
    function heronameexists(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>该名字已经被其他玩家占用，请选择其他名字</font>","Type":9}')
    end
    function changeheronamefail(player)
        sendmsg(player, 1, '{"Msg":"英雄<font color=\'#ff0000\'>改名失败！</font>","Type":9}')
    end
```

------------

### 获取英雄模式

`getherosta`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.05.23新增接口</font>**

| 参数   | 类型      | 空   | 默认 | 注释                                    |
| :----- | :-------- | :--- | :--- | :-------------------------------------- |
| actor  | `object`  | 否   |      | 玩家对象                                |
| result | `integer` | 否   |      | 英雄模式<br>0=攻击<br>1=跟随<br>2= 休息 |

### 设置英雄模式

`setherosta`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.05.23新增接口</font>**

| 参数  | 类型      | 空   | 默认 | 注释                                    |
| :---- | :-------- | :--- | :--- | :-------------------------------------- |
| actor | `object`  | 否   |      | 玩家对象                                |
| model | `integer` | 否   |      | 英雄模式<br>0=攻击<br>1=跟随<br>2= 休息 |

------------

### 英雄传送到主体身边

`herofollow`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.05.23新增接口</font>**

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `object` | 否   |      | 玩家对象 |


# 镖车系统




## 触发

### 镖车到达指定位置触发

`carpathend`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 镖车主人对象 |

### 镖车切换地图触发

`leavedart`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 镖车主人对象 |

### 镖车进入自动寻路范围触发

`carfindmaster`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 镖车主人对象 |

### 丢失镖车触发

`losercar`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 镖车主人对象 |
| car   | `object` | 否   |      | 镖车对象     |

### 镖车死亡触发

`cardie`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 攻击镖车对象 |
| car   | `object` | 否   |      | 镖车对象     |

### 镖车被攻击触发

`slavedamage`

| 参数  | 类型     | 空   | 默认                | 注释         |
| :---- | :------- | :--- | :------------------ | :----------- |
| actor | `object` | 否   |                     | 镖车主人对象 |
| hiter | `object` | 否   | 引擎64_23.08.30新增 | 攻击者对象   |
| car   | `object` | 否   | 引擎64_23.08.30新增 | 镖车对象     |

### 攻击别人镖车触发

`hitslave`

| 参数   | 类型     | 空   | 默认                | 注释         |
| :----- | :------- | :--- | :------------------ | :----------- |
| actor  | `object` | 否   |                     | 攻击者对象   |
| master | `object` | 否   | 引擎64_23.08.30新增 | 镖车主人对象 |
| car    | `object` | 否   | 引擎64_23.08.30新增 | 镖车对象     |

## 接口

### 镖车自动寻路到指定坐标
`dartmap`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|aimX     |`integer`      |否   |    |   目标X坐标 |
|aimY     |`integer`      |否   |    |   目标Y坐标 |
|range     |`integer`      |否   |    |  人物离镖车距离内自动寻路<br />取值范围：0-12<br />0-不检测  |

### 人物下线，镖车存活设置

`darttime`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|time     |`integer`      |否   |    |   镖车存活时间，秒 |
|isDie     |`integer`      |否   |    |   下线是否消失<br />0-消失，1-时间到达消失 |


# 宠物系统

###### 更新时间：引擎64_23.03.23


## 宠物说明
```
1.支持宠物蛋生成宠物， 宠物蛋类别是StdMode=201，Anicount字段填对应怪物表里宠物的IDX
2.cfg_petlevel.xls为宠物等级表，配置宠物经验和不同等级宠物属性
2.支持宠物变成道具宠物蛋
3.宠物穿戴装备只支持装备表里的装备，自定义属性 套装等装备不支持，宠物没有装备格子，可以用命令可以获取宠物身上装备清单，显示到面板
4.宠物序号重0开始，删除一个序号的宠物，后面的序号自动补齐上一个序号。比如0-4，共5个宠物，删除3号宠物，4号宠物序号就变成3了
5.召唤宠物方式1：1双击宠物蛋获得宠物功能，然后执行RECALLPET命令召唤出来宠物，宠物死亡后需要用复活命令复活，复活后再用RECALLPET命令召唤
  召唤宠物方式2：无需宠物蛋CREATEPET命令直接得宠物功能，然后执行RECALLPET命令召唤出来宠物，宠物死亡后需要用复活命令复活，复活后再用RECALLPET命令召唤
6.宠物目前不支持跨服

【宠物相关M2设置】：
  M2-宠物设置-开启宠物系统

【宠物相关表格设置】：
【cfg_monster.xls怪物表】      （宠物race类型必须是156 19，怪物表Custommonster字段必现填至少一种攻击形式）
表格范例：
1459 小狐狸 156 19 320 80 1 100 3000 3#1#1000|3#3#500|3#4#500 60 45 700 1 0 800  7 11

【cfg_petlevel.xls宠物等级表】
表格范例：
1 1459 小狐狸 1 100 1#100|3#10  21 90 500 500

【cfg_monattack.xls自定义怪物表】
 表格范例：                       11 20011 30#100#100 0 1 0 0 1 0 100#500 0 1#100#5#100|2#100#1#300
```

## 触发
### 宠物升级触发
`petlevelup`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`integer`      |否   |    |宠物编号 |
|level     |`integer`      |否   |    |等级 |
|zslevel     |`integer`      |否   |    |转生等级 |

### 获得宠物触发[人物上线首次加载宠物时也会触发]
`getnewpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`integer`      |否   |    |宠物编号 |

### 使用宠物蛋触发
`usepetitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|makeIndex     |`integer`      |否   |    |物品唯一id |
|itenIdx     |`integer`      |否   |    |物品id |

### 宠物死亡触发
`petdie`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`integer`      |否   |    |宠物编号 |

### 宠物变蛋触发
`pettoitem`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|makeIndex     |`integer`      |否   |    |物品唯一id |

### 宠物攻击触发
`attackbypet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`integer`      |否   |    |宠物编号 |
|target     |`object`      |否   |    |目标对象 |
|magicID     |`integer`      |否   |    |技能id |
|isImportant     |`integer`      |否   |    |是否主目标 |

### 宠物攻击伤害前触发
`attackdamagepet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|target     |`object`      |否   |    |目标对象 |
|petObj     |`object`      |否   |    |宠物对象 |
|magicID     |`integer`      |否   |    |技能id |
|damage     |`integer`      |否   |    |伤害值 |
|isImportant     |`integer`      |否   |    |是否主目标 |
|result       |`integer`       |否   |    |   返回值<br>修改后的伤害 |

### 宠物被攻击前触发
`struckdamagepet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|hiter     |`object`      |否   |    |攻击者对象 |
|petIdx     |`object`      |否   |    |宠物编号 |
|magicID     |`integer`      |否   |    |技能id |
|damage     |`integer`      |否   |    |伤害值 |
|result       |`integer`       |否   |    |   返回值<br>修改后的伤害 |

### 宠物被物理攻击触发
`struckofpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`object`      |否   |    |宠物编号 |
|hiter     |`object`      |否   |    |攻击者对象 |
|magicID     |`integer`      |否   |    |技能id |

### 宠物被魔法攻击触发
`magicstruckofpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|petIdx     |`object`      |否   |    |宠物编号 |
|hiter     |`object`      |否   |    |攻击者对象 |
|magicID     |`integer`      |否   |    |技能id |

## 接口

### 获取宠物
`getpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号或'X'表示当前宠物 |
|result     |`object`      |否   |    |   返回宠物对象 |

### 获取宠物蛋信息
`getpetegglevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|itemmakeid     |`integer`    |否   |    |   物品MakeIndex |
|type     |`integer`    |否   |    |   需要返回的数值<br>1-转生等级;<br>2-等级;<br>3-经验;<br>0-同时返回三个值|

### 设置宠物蛋等级
`setpetegglevel`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|itemmakeid     |`integer`    |否   |    |   物品MakeIndex |
|level     |`integer`    |否   |    |   等级，-1表示不修改值|
|zlevel     |`integer`    |否   |    |   转生等级，-1表示不修改值|
|exp     |`integer`    |否   |    |   经验值，-1表示不修改值|

### 创建宠物

`createpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|monname     |`string`      |否   |    |自定义怪物名称 |
|level     |`integer`      |否   |    |   怪物等级 |

### 召唤宠物
`recallpet`

> 召唤idx号宠物，如宠物不存在或已经召唤出，系统会自动提示

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |

### 收回宠物
`unrecallpet`

> 收回idx号宠物，如宠物不存在或已经收回，系统会自动提示

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |

### 返回复活的宠物对象
`realivepet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |
|nHp     |`integer`    |否   |    |   复活后的HP量 |
|type     |`integer`    |否   |    |   0-绝对值，1-百分比 |

### 删除宠物

`delpet`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |

### 收回宠物为物品

`retractpettoitem`

> 存入背包，如背包满则删除宠物

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |

### 宠物穿装备
`pettakeon`

> 此接口不会增加物品，仅将物品的属性添加到宠物身上，并保存到数据库。

| 参数 | 类型      | 空   | 默认 | 注释                      |
| :--- | :-------- | :--- | :--- | :------------------------ |
| play | `object`  | 否   |      | 玩家对象                  |
| idx  | `integer` | 否   |      | 宠物序号                  |
| item | `string`  | 否   |      | 装备名称，多个装备用#分隔 |

### 宠物脱装备

`pettakeoff`

> 此接口不扣减物品，仅扣减宠物身上对应装备属性。

| 参数 | 类型      | 空   | 默认 | 注释                                          |
| :--- | :-------- | :--- | :--- | :-------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                      |
| idx  | `integer` | 否   |      | 宠物序号                                      |
| item | `string`  | 否   |      | 装备名称，多个装备用#分隔，-1表示脱下全部装备 |

### 获取宠物身上装备列表

`getpetbodyitem`

| 参数 | 类型      | 空   | 默认 | 注释     |
| :--- | :-------- | :--- | :--- | :------- |
| play | `object`  | 否   |      | 玩家对象 |
| idx  | `integer` | 否   |      | 宠物序号 |

### 置换宠物属性

`petmon`
- 只置换基础属性:形象、怪物表配置，原宠物其它属性全部保留，包括序号

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| idx    | `integer` | 否   |      | 宠物序号 |
| monidx | `integer` | 否   |      | 怪物IDX  |

### 设置宠物模式

`setpetmode`
- 注：设置宠物是针对所有宠物同时生效，如果主人有宝宝，则宝宝同步生效（宝宝也支持此命令）

| 参数 | 类型      | 空   | 默认 | 注释                                                                     |
| :--- | :-------- | :--- | :--- | :----------------------------------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                                                 |
| mode | `integer` | 否   |      | 宠物模式:<br>1-跟随;<br>2-攻击;<br>3-被动(被攻击时才设定目标);<br>4-休息 |

### 获取宠物状态

`petstate`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`    |否   |    |   玩家对象 |
|idx     |`integer`    |否   |    |   宠物序号 |
|result     |`integer`      | 否  |    |宠物状态：<br>0-收回状态，<br>1-召唤出状态，<br>2-死亡状态

### 增加宠物属性

`addpetattlist`

| 参数     | 类型               | 空   | 默认 | 注释           |
| :------- | :----------------- | :--- | :--- | :------------- |
| play     | `object`           | 否   |      | 玩家对象       |
| idx      | `integer`          | 否   |      | 宠物序号       |
| attrName | `integer`/`string` | 否   |      | 自定义属性组名 |
| opt      | `string`           | 否   |      | 操作符 + - =   |
| attr     | `string`           | 否   |      | 属性字符串     |

### 清除宠物属性

`delpetattlist`

| 参数     | 类型               | 空   | 默认 | 注释                                       |
| :------- | :----------------- | :--- | :--- | :----------------------------------------- |
| play     | `object`           | 否   |      | 玩家对象                                   |
| idx      | `integer`          | 否   |      | 宠物序号                                   |
| attrName | `integer`/`string` | 否   |      | 清空对应属性组的属性;<br>nil清除所有属性组 |

### 增加宠物攻击表现

`addpetskill`

| 参数    | 类型      | 空   | 默认 | 注释                                      |
| :------ | :-------- | :--- | :--- | :---------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                  |
| idx     | `integer` | 否   |      | 宠物序号或'X'表示当前宠物                 |
| skillid | `integer` | 否   |      | 增加的攻击表现ID，为cfg_monattack表中的ID |

### 删除宠物攻击表现

`delpetskill`

| 参数    | 类型      | 空   | 默认 | 注释                                      |
| :------ | :-------- | :--- | :--- | :---------------------------------------- |
| play    | `object`  | 否   |      | 玩家对象                                  |
| idx     | `integer` | 否   |      | 宠物序号或'X'表示当前宠物                 |
| skillid | `integer` | 否   |      | 增加的攻击表现ID，为cfg_monattack表中的ID |

### 获取宠物数量

`getpetcount`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.03.14新增接口</font>**

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| play   | `object`  | 否   |      | 玩家对象 |
| result | `integer` | 否   |      | 宠物数量 |

### 改变宠物外观

`setpetappr`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.05.23新增接口</font>**

| 参数   | 类型               | 空   | 默认 | 注释                           |
| :----- | :----------------- | :--- | :--- | :----------------------------- |
| actor  | `string`           | 否   |      | 玩家对象                       |
| petIdx | `string`/`integer` | 否   |      | 宠物序号,X表示当前宠物         |
| appr   | `integer`          | 是   |      | 怪物外观ID(怪物Appr)<br>0=还原 |


# 分身相关



###### 更新时间：引擎64_23.06.28


### 召唤自身分身

`recallself`

| 参数         | 类型      | 空   | 默认                | 注释                                       |
| :----------- | :-------- | :--- | :------------------ | :----------------------------------------- |
| play         | `object`  | 否   |                     | 玩家对象                                   |
| time         | `string`  | 否   |                     | 分身有效时间(秒)                           |
| num          | `integer` | 否   |                     | 数量                                       |
| attrPro      | `integer` | 否   |                     | 继承人物属性百分比                         |
| color        | `integer` | 是   |                     | 分身颜色<br />0-255;0不改变颜色              |
| dressLook    | `integer` | 是   |                     | 改变分身衣服外观(0或空为不改变)            |
| weaponLook   | `integer` | 是   |                     | 改变分身武器外观(0或空为不改变)            |
| dressEffect  | `integer` | 是   |                     | 改变分身衣服外观特效(0或空为不改变)        |
| weaponEffect | `integer` | 是   |                     | 改变分身武器外观特效(0或空为不改变)        |
| hpMax        | `integer` | 是   | 引擎64_24.05.23新增 | 分身血量数值（填0表示按参数4的继承百分比） |
| buffID       | `string`  | 是   | 引擎64_24.05.23新增 | BUFFID<br />多个BUFF用#号连接                |

### 获取角色所有分身
`clonelist`

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| play   | `object` | 否   |      | 玩家对象     |
| result | `table`  |      |      | 玩家分身列表 |
```lua
        local selflist = clonelist(actor)
        for i, _self in ipairs(selflist or {}) do
            release_print("分身列表",i,getbaseinfo(_self,1))
        end
```

### 杀死角色所有分身
`killcopyself`

| 参数   | 类型     | 空   | 默认 | 注释         |
| :----- | :------- | :--- | :--- | :----------- |
| play   | `object` | 否   |      | 玩家对象     |
# 文本操作类



###### 更新时间：引擎64_23.08.30



### 创建文本文件

`createfile`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| path | `string` | 否   |      | 文件路径 |
```lua
--在Envir\QuestDiary目录中建立了一个文件.
createfile('..\\QuestDiary\\abc.txt')
```

### 写入指定文本文件

`addtextlist`

| 参数 | 类型     | 空   | 默认 | 注释              |
| :--- | :------- | :--- | :--- | :---------------- |
| path | `string` | 否   |      | 文件路径          |
| str  | `string` | 否   |      | 写入文本          |
| line | `integer` | 否   |      | 写入行数(0~65535) |
```lua
addtextlist('..\\QuestDiary\\abc.txt','aaa',0)
addtextlist('..\\QuestDiary\\abc.txt','bbb',1)
addtextlist('..\\QuestDiary\\abc.txt','ccc',2)
addtextlist('..\\QuestDiary\\abc.txt','ddd',3)
addtextlist('..\\QuestDiary\\abc.txt','eee',4)
addtextlist('..\\QuestDiary\\abc.txt','aaa|bbb|ccc|ddd|eee',5)
```

### 从文件中随机获取一行字符串

`getrandomtext`

| 参数 | 类型     | 空   | 默认 | 注释           |
| :--- | :------- | :--- | :--- | :------------- |
| path | `string` | 否   |      | 文件路径       |
| line | `integer` | 是   |  0    | 指定行(0~1000)<br />传入-1随机取某一行的字符串 |
```lua
local str = getrandomtext('..\\QuestDiary\\abc.txt',-1)
release_print('getrandomtext',str)
```

### 获取文本文件指定行的内容

`getliststring`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| path   | `string` | 否   |      | 文件路径 |
| line   | `integer` | 否   |      | 指定行   |
| result | `string` | 否   |      | 字符串 |
| result | `string` | 否   |      | 返回值2<br />当有内容中存在`:`时,会将`:`号后的字符分割返回 |
```lua
    abc.txt中的文本内容,当行内有`:`号时,
    [[
        aaa:99999
        bbbvvv
    ]]
    local line = 0
    local res1,res2 = getliststring('..\\QuestDiary\\abc.txt',line)
    release_print('getliststring',line,res1,res2)

    -- M2打印结果
    `getliststring,0,aaa,99999`

    local line = 1
    local res1,res2 = getliststring('..\\QuestDiary\\abc.txt',line)
    release_print('getliststring',line,res1,res2)

    -- M2打印结果
    `getliststring,1,bbbvvv,`
```

### 获取文本文件指定行的内容[根据符号分割]

`getliststringex`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| path   | `string` | 否   |      | 文件路径 |
| line   | `integer` | 否   |      | 指定行   |
| symbol | `string` | 否   |      | 符号     |
```lua
local tbl = getliststringex('..\\QuestDiary\\abc.txt',5,'|')
for i,v in ipairs(tbl or {}) do
    release_print("文本",i,v)
end
```

### 取字符串在列表中的下标

`getstringpos`

| 参数   | 类型      | 空   | 默认 | 注释                          |
| :----- | :-------- | :--- | :--- | :---------------------------- |
| path   | `string`  | 否   |      | 文件路径                      |
| str    | `string`  | 否   |      | 字符串                        |
| result | `integer` | 否   |      | 字符串所在行<br />未找到返回9999999 |
```lua
local pos = getstringpos('..\\QuestDiary\\abc.txt','aaa')
release_print('getstringpos',type(pos),pos)
```

### 删除文本文件的内容

`deltextlist`

| 参数  | 类型      | 空   | 默认 | 注释                                                        |
| :---- | :-------- | :--- | :--- | :---------------------------------------------------------- |
| path  | `string`  | 否   |      | 文件路径                                                    |
| line  | `integer`  | 否   |      | 指定行                                                      |
| model | `integer` | 否   |      | 删除模式<br />0=删除行<br />1=清空行<br />2=删除随机行(参数2失效) |
```lua
--删除第0行
deltextlist('..\\QuestDiary\\abc.txt',1,0)
--清空第0行
deltextlist('..\\QuestDiary\\abc.txt',1,1)
--随机删除一行
deltextlist('..\\QuestDiary\\abc.txt',nil,2)
```

### 清除列表内容

`clearnamelist`

| 参数 | 类型     | 空   | 默认 | 注释     |
| :--- | :------- | :--- | :--- | :------- |
| path | `string` | 否   |      | 文件路径 |
```lua
clearnamelist('..\\QuestDiary\\abc.txt')
```

### 检查字符串是否在指定文件中

- 注:不区分大小写

`checktextlist`

| 参数   | 类型     | 空   | 默认 | 注释                              |
| :----- | :------- | :--- | :--- | :-------------------------------- |
| path   | `string` | 否   |      | 文件路径                          |
| str    | `string` | 否   |      | 字符串                            |
| result | `bool`   | 否   |      | true=在文件中<br />false=不在文件中 |
```lua
local res1 = checktextlist('..\\QuestDiary\\abc.txt','ccc')
release_print('checktextlist',res1,res2)
```

### 检查字符串是否在指定文件中

- 注:包含检测,检测的字符串不需要完全相同,文件里的字符包含检测的字符,就会返回true

`checkcontainstextlist`

| 参数   | 类型      | 空   | 默认 | 注释                                                                                  |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------------------------------------ |
| path   | `string`  | 否   |      | 文件路径                                                                              |
| str    | `string`  | 否   |      | 字符串                                                                                |
| model  | `integer` | 否   |      | 检测模式<br />0=列表中,是否包含被检测的字符<br />1=被检测的字符是否包含列表中的某一行内容 |
| result | `bool`    | 否   |      | true=在文件中<br />false=不在文件中                                                     |
```lua
local res1 = checkcontainstextlist('..\\QuestDiary\\abc.txt','ddd',0)
local res2 = checkcontainstextlist('..\\QuestDiary\\abc.txt','ddddddd',0)
local res3 = checkcontainstextlist('..\\QuestDiary\\abc.txt','dd',1)
local res4 = checkcontainstextlist('..\\QuestDiary\\abc.txt','ddddddd',1)
release_print('checkcontainstextlist',res1,res2,res3,res4)
```
# 任务系统



## 触发

### 接取任务触发

`picktask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|taskID     |`integer`      |否   |    |任务id |

### 点击任务触发

`clicknewtask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|taskID     |`integer`      |否   |    |任务id |

### 刷新任务触发

`changetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|taskID     |`integer`      |否   |    |任务id |

### 完成任务触发

`completetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|taskID     |`integer`      |否   |    |任务id |

### 删除任务触发

`deletetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
|taskID     |`integer`      |否   |    |任务id |

----------

## 接口
### 新建任务
`newpicktask` 任务表:cfg_newtask.xls

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nId     |`integer`      |否   |    |   任务ID |
|param1   |`string`      |是   |    | 参数1，用来替换任务内容里的%s |
|param2   |`string`      |是   |    | 参数2，用来替换任务内容里的%s |
|param3   |`string`      |是   |    | 参数3，用来替换任务内容里的%s |
|param4   |`string`      |是   |    | 参数4，用来替换任务内容里的%s |
|param5   |`string`      |是   |    | 参数5，用来替换任务内容里的%s |
|param6   |`string`      |是   |    | 参数6，用来替换任务内容里的%s |
|param7   |`string`      |是   |    | 参数7，用来替换任务内容里的%s |
|param8   |`string`      |是   |    | 参数8，用来替换任务内容里的%s |
|param9   |`string`      |是   |    | 参数9，用来替换任务内容里的%s |
|param10   |`string`      |是   |    | 参数10，用来替换任务内容里的%s |

```lua
  参数替换任务内容文本，是依次替换的
function main(self)
    newpicktask(self,12,getplayvar(self,'S任务状态'),getplayvar(self,'N当前杀怪数量'))
end
```

### 刷新进行中任务状态
`newchangetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nId     |`integer`      |否   |    |   任务ID |
|param1   |`string`      |是   |    | 参数1，用来替换任务内容里的%s |
|param2   |`string`      |是   |    | 参数2，用来替换任务内容里的%s |
|param3   |`string`      |是   |    | 参数3，用来替换任务内容里的%s |
|param4   |`string`      |是   |    | 参数4，用来替换任务内容里的%s |
|param5   |`string`      |是   |    | 参数5，用来替换任务内容里的%s |
|param6   |`string`      |是   |    | 参数6，用来替换任务内容里的%s |
|param7   |`string`      |是   |    | 参数7，用来替换任务内容里的%s |
|param8   |`string`      |是   |    | 参数8，用来替换任务内容里的%s |
|param9   |`string`      |是   |    | 参数9，用来替换任务内容里的%s |
|param10   |`string`      |是   |    | 参数10，用来替换任务内容里的%s |

### 完成任务
`newcompletetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nId     |`integer`      |否   |    |   任务ID |

### 删除任务
`newdeletetask`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nId     |`integer`      |否   |    |   任务ID |

### 任务置顶显示
`tasktopshow`

- 客户端只支持1个人物置顶显示

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|nId     |`integer`      |否   |    |   任务ID |

------------
### 系统任务计时

##### 增加系统任务计时

`dsfuncall`

> **<font color="#808080" style="font-size: 13px;">引擎64_23.10.24新增接口</font>**

| 参数     | 类型      | 空   | 默认 | 注释                                       |
| :------- | :-------- | :--- | :--- | :----------------------------------------- |
| player   | `object`  | 否   |      | 玩家对象                                   |
| funcName | `string`  | 否   |      | 回调函数名<br>需以`dingshicf_`开头         |
| time     | `integer` | 否   |      | 倒计时时间(毫秒)                           |
| model    | `integer` | 否   |      | 0=上线需重新开启否则消失<br>1=上线直接执行 |
| isClear  | `integer` | 否   |      | 0=开启新的<br>1=上线刷新当前时间           |
```lua
 --QFunction-0.lua
function dingshicf_1(actor)
end

dsfuncall(actor,"dingshicf_1",10 * 1000 ,1 ,1)
```

##### 删除系统任务计时

`deldsfuncall`

> **<font color="#808080" style="font-size: 13px;">引擎64_23.10.24新增接口</font>**

| 参数     | 类型     | 空   | 默认 | 注释       |
| :------- | :------- | :--- | :--- | :--------- |
| player   | `object` | 否   |      | 玩家对象   |
| funcName | `string` | 否   |      | 回调函数名 |

##### 改变系统任务计时

`cngdsfuncallstate`

> **<font color="#808080" style="font-size: 13px;">引擎64_23.10.24新增接口</font>**

| 参数     | 类型     | 空   | 默认 | 注释             |
| :------- | :------- | :--- | :--- | :--------------- |
| player   | `object` | 否   |      | 玩家对象         |
| funcName | `string` | 否   |      | 回调函数名       |
| model    | `integer` | 否   |      | 1=开启<br>0=停止 |


# 通区系统

###### 更新时间：引擎64_23.08.30



## 通区视频教程

http://engine-doc.996m2.com/web/#/38/6726

## 常量

**主区常量:`&lt;$MAINTONGSERVER&gt;` 如果未设置主区,常量为0**

## 接口

### 通区创建/删除文本

`tongfile`

| 参数     | 类型      | 空   | 默认 | 注释                     |
| :------- | :-------- | :--- | :--- | :----------------------- |
| model    | `integer` | 否   |      | 0=创建文件<br />1=删除文件 |
| fileName | `string`  | 否   |      | 文件名称                 |

### 通区同步文本

`updatetongfile`

| 参数     | 类型     | 空   | 默认 | 注释     |
| :------- | :------- | :--- | :--- | :------- |
| fileName | `string` | 否   |      | 文件名称 |

`updatetongfile`

| 参数           | 类型     | 空   | 默认 | 注释         |
| :------------- | :------- | :--- | :--- | :----------- |
| remoteFileName | `string` | 否   |      | 远程文件名称 |
| fileName       | `string` | 否   |      | 同步的文件名 |

### 更改文件内容

`changetongfile`

| 参数  | 类型     | 空   | 默认 | 注释                                                                                                        |
| :---- | :------- | :--- | :--- | :---------------------------------------------------------------------------------------------------------- |
| path  | `string` | 否   |      | 文本路径                                                                                                    |
| str   | `string` | 否   |      | 内容(最大64中文字符)                                                                                        |
| line  | `string` | 否   |      | 指定操作行                                                                                                  |
| model | `string` | 否   |      | 0=文件尾追加内容(快)<br />1 =插入内容到指定行<br />2=替换内容到指定行<br />3=删除指定行内容<br />4=清空整个文件内容 |

### 通区变量同步

`updatetongvar`

| 参数    | 类型     | 空   | 默认 | 注释                                                                                     |
| :------ | :------- | :--- | :--- | :--------------------------------------------------------------------------------------- |
| varName | `string` | 否   |      | 全局变量名<br />如果是全局自定义变量，这么写：GLOBAL(变量名)，如果是G，A变量，就正常写即可 |

### 增加创建文件

`maintongfile`

| 参数    | 类型      | 空   | 默认 | 注释                                         |
| :------ | :-------- | :--- | :--- | :------------------------------------------- |
| serverID | `string`  | 否   |      | 传入主区ID,在主区执行该命令无效              |
| model   | `integer` | 否   |      | 0=创建文件<br />1=删除文件                     |
| path    | `string`  | 否   |      | 文件路径<br />例 `'..\\QuestDiary\\996m2.txt'` |

### 写入指定 区服 配置

`writetongkey`

| 参数     | 类型     | 空   | 默认 | 注释                                         |
| :------- | :------- | :--- | :--- | :------------------------------------------- |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效              |
| path     | `string` | 否   |      | 文件路径<br />例 `'..\\QuestDiary\\996m2.txt'` |
| key      | `string` | 否   |      | 字段                                         |
| value    | `string` | 否   |      | 值                                           |

### 读取指定 区服 配置

&gt; 读取后由触发QF的`readtongok`函数

`readtongkey`

| 参数     | 类型     | 空   | 默认 | 注释                                         |
| :------- | :------- | :--- | :--- | :------------------------------------------- |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效              |
| path     | `string` | 否   |      | 文件路径<br />例 `'..\\QuestDiary\\996m2.txt'` |
| key      | `string` | 否   |      | 字段                                         |
| varName  | `string` | 否   |      | 变量                                         |
```lua
    local serverID = getcost("0","&lt;$MAINTONGSERVER&gt;")
    readtongkey(serverID,'..\\QuestDiary\\996m2.txt',"通区配置","A100")

    --QF触发
    function readtongok(sysobj)
        local msg = "QF触发:当前读取服务器&lt;$MAINTONGSERVER&gt;--时间戳--&lt;$UTCNOW8&gt;--读取值&lt;$str(A100)&gt;"
        release_print(parsetext(msg,sysobj))
    end
```

### 执行查询通区主服

`checktongsvr`

- 执行后触发qf 在线 - maintongline ; 离线 - maintongoff

| 参数     | 类型     | 空   | 默认 | 注释                            |
| :------- | :------- | :--- | :--- | :------------------------------ |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效 |

### 同步文件 将本地文件路径同步到服务器路径

`updatemaintongfile`

| 参数     | 类型     | 空   | 默认 | 注释                                         |
| :------- | :------- | :--- | :--- | :------------------------------------------- |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效              |
| path     | `string` | 否   |      | 文件路径<br />例 `'..\\QuestDiary\\996m2.txt'` |

`updatemaintongfile`

| 参数     | 类型     | 空   | 默认 | 注释                                             |
| :------- | :------- | :--- | :--- | :----------------------------------------------- |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效                  |
| filePath | `string` | 否   |      | 服务器文件路径`'..\\QuestDiary\\bbb.txt'`        |
| path     | `string` | 否   |      | 本地文件路径<br />例 `'..\\QuestDiary\\996m2.txt'` |

### 拉取文件(带主区命令)

`getmaintongfile`

| 参数     | 类型     | 空   | 默认 | 注释                                               |
| :------- | :------- | :--- | :--- | :------------------------------------------------- |
| serverID | `string` | 否   |      | 传入主区ID,在主区执行该命令无效                    |
| filePath | `string` | 否   |      | 本地文件路径`'..\\QuestDiary\\bbb.txt'`            |
| path     | `string` | 否   |      | 远程服务器路径<br />例 `'..\\QuestDiary\\996m2.txt'` |

### 通区变量操作

`settongvar`

| 参数  | 类型      | 空   | 默认 | 注释             |
| :---- | :-------- | :--- | :--- | :--------------- |
| varID | `string`  | 否   |      | 通区变量1-50     |
| opt   | `string`  | 否   |      | 操作符 +、-、=   |
| value | `integer` | 否   |      | 数值(可超过21亿) |


# 装备位置和相关常量

- 996引擎装备常量: 唯一ID<$USEITEM[XX]>;IDX<$USEITEMID[XX]>;名字<$USEITEMNAME[XX]>
- XX表示M2设置的装备位置支持（0-100)

- 英雄常量在原来常量基础上增加H.    如：<$H.DRESS>
- 改名字后常量在原来基础加G_   如：<$G_DRESS>

<table style="HEIGHT: 1203px; WIDTH: 919px; BORDER-COLLAPSE: collapse" bordercolor="#000000" cellspacing="0" cellpadding="2" width="919" border="1"><tbody><tr><td><p align="center"><strong><font face="宋体">道具类型</font></strong></p></td><td><p align="center"><strong><font face="宋体"> 数据库stdmode</font></strong></p></td><td><p align="center"><strong><font face="宋体"> 穿戴位置</font></strong></p></td><td><p align="center"><strong><font face="宋体"> 位置常量</font></strong></p></td><td><p align="center"><strong><font face="宋体"> 位置唯一ID常量(取下保留对应唯一ID)</font></strong></p></td></tr><tr><td><p align="center"><font color="#000000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">衣服(男)</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#000000" face="宋体"> 10</font></p></td><td><p align="center"><font color="#000000" face="宋体">0</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$DRESS></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$DRESSID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">衣服(女)</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体"> 11</font></p></td><td><p align="center"><font color="#800000" face="宋体">0</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$DRESS></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$DRESSID></font></p></td></tr><tr><td><p align="center"><font color="#000000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">武器(男)</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#000000" face="宋体"> 5、6</font></p></td><td><p align="center"><font color="#000000" face="宋体">1</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$WEAPON></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$WEAPONID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">武器(女)</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体"> 5、6</font></p></td><td><p align="center"><font color="#800000" face="宋体">1</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$WEAPON></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$WEAPONID></font></p></td></tr><tr><td><p align="center"><font color="#000000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">勋章</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#000000" face="宋体"> 30</font></p></td><td><p align="center"><font color="#000000" face="宋体">2</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$RIGHTHAND></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$RIGHTHANDID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">项链</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体"> 19、20、21</font></p></td><td><p align="center"><font color="#800000" face="宋体">3</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$NECKLACE></font></p></td><td><p align="center"><font color="#800000" face="宋体"> <$NECKLACEID></font></p></td></tr><tr><td><p align="center"><font color="#000000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">头盔</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#000000" face="宋体"> 15</font></p></td><td><p align="center"><font color="#000000" face="宋体">4</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$HELMET></font></p></td><td><p align="center"><font color="#000000" face="宋体"> <$HELMETID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">右手镯</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体"> 24、26</font></p></td><td><p align="center"><font color="#800000" face="宋体">5</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$ARMRING\_R></font></p></td><td><p align="center"><font color="#800000" face="宋体"> <$ARMRING\_RID></font></p></td></tr><tr><td><p align="center"><font color="#000000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">左手镯</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#000000" face="宋体"> 24、26</font></p></td><td><p align="center"><font color="#000000" face="宋体">6</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$ARMRING\_L></font></p></td><td><p align="center"><font color="#000000" face="宋体"> <$ARMRING\_LID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">右戒指</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体">22、23</font></p></td><td><p align="center"><font color="#800000" face="宋体">7</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$RING\_R></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$RING\_RID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">左戒指</font></p></td><td><p align="center"><font color="#000000" face="宋体">22、23</font></p></td><td><p align="center"><font color="#000000" face="宋体">8</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$RING\_L></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$RING\_LID></font></p></td></tr><tr><td><p align="center"><font color="#800000"><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt; mso-spacerun: 'yes'">符、毒药</span><span style="FONT-SIZE: 12pt; FONT-FAMILY: 宋体; mso-font-kerning: 0.0000pt"></span></font></p></td><td><p align="center"><font color="#800000" face="宋体">25</font></p></td><td><p align="center"><font color="#800000" face="宋体">9</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$BUJUK></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$BUJUKID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">腰带</font></p></td><td><p align="center"><font color="#000000" face="宋体">54、64</font></p></td><td><p align="center"><font color="#000000" face="宋体">10</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$BELT></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$BELTID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">靴子</font></p></td><td><p align="center"><font color="#800000" face="宋体">52、62</font></p></td><td><p align="center"><font color="#800000" face="宋体">11</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$BOOTS></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$BOOTSID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">宝石、血石</font></p></td><td><p align="center"><font color="#000000" face="宋体">53、63、7</font></p></td><td><p align="center"><font color="#000000" face="宋体">12</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$CHARM></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$CHARMID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">斗笠</font></p></td><td><p align="center"><font color="#800000" face="宋体">16</font></p></td><td><p align="center"><font color="#800000" face="宋体">13</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$HAT></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$HATID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">军鼓</font></p></td><td><p align="center"><font color="#000000" face="宋体">65</font></p></td><td><p align="center"><font color="#000000" face="宋体">14</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$DRUM></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$DRUMID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">马牌</font></p></td><td><p align="center"><font color="#800000" face="宋体">28</font></p></td><td><p align="center"><font color="#800000" face="宋体">15</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$HORSE></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$HORSEID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">盾牌</font></p></td><td><p align="center"><font color="#000000" face="宋体">48</font></p></td><td><p align="center"><font color="#000000" face="宋体">16</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHIELD></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHIELDID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">面巾</font></p></td><td><p align="center"><font color="#800000" face="宋体">50</font></p></td><td><p align="center"><font color="#800000" face="宋体">55</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$FTOWEL></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$FTOWELID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装衣服(男)</font></p></td><td><p align="center"><font color="#000000" face="宋体">66</font></p></td><td><p align="center"><font color="#000000" face="宋体">17</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SDRESS></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SDRESSID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装衣服(女)</font></p></td><td><p align="center"><font color="#800000" face="宋体">67</font></p></td><td><p align="center"><font color="#800000" face="宋体">17</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SDRESS></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SDRESSID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装武器(男)</font></p></td><td><p align="center"><font color="#000000" face="宋体">68</font></p></td><td><p align="center"><font color="#000000" face="宋体">18</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SWEAPON></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SWEAPONID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装武器(女)</font></p></td><td><p align="center"><font color="#800000" face="宋体">69</font></p></td><td><p align="center"><font color="#800000" face="宋体">18</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SWEAPON></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SWEAPONID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装斗笠</font></p></td><td><p align="center"><font color="#000000" face="宋体">71</font></p></td><td><p align="center"><font color="#000000" face="宋体">19</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHAT></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHATID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装项链</font></p></td><td><p align="center"><font color="#800000" face="宋体">75、76、77</font></p></td><td><p align="center"><font color="#800000" face="宋体">20</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SNECKLACE></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SNECKLACEID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装头盔</font></p></td><td><p align="center"><font color="#000000" face="宋体">78</font></p></td><td><p align="center"><font color="#000000" face="宋体">21</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHELMET></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SHELMETID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装左手镯</font></p></td><td><p align="center"><font color="#800000" face="宋体">79、80</font></p></td><td><p align="center"><font color="#800000" face="宋体">22</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SARMRING\_L></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SARMRING\_LID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装右手镯</font></p></td><td><p align="center"><font color="#000000" face="宋体">79、80</font></p></td><td><p align="center"><font color="#000000" face="宋体">23</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SARMRING\_R></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SARMRING\_RID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装左戒指</font></p></td><td><p align="center"><font color="#800000" face="宋体">81、82</font></p></td><td><p align="center"><font color="#800000" face="宋体">24</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SRING\_L></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SRING\_LID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装右戒指</font></p></td><td><p align="center"><font color="#000000" face="宋体">81、82</font></p></td><td><p align="center"><font color="#000000" face="宋体">25</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SRING\_R></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SRING\_RID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装勋章</font></p></td><td><p align="center"><font color="#800000" face="宋体">83</font></p></td><td><p align="center"><font color="#800000" face="宋体">26</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SRIGHTHAND></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SRIGHTHANDID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装腰带</font></p></td><td><p align="center"><font color="#000000" face="宋体">84、85</font></p></td><td><p align="center"><font color="#000000" face="宋体">27</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SBELT></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SBELTID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装靴子</font></p></td><td><p align="center"><font color="#800000" face="宋体">86、87</font></p></td><td><p align="center"><font color="#800000" face="宋体">28</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SBOOTS></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SBOOTSID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装宝石</font></p></td><td><p align="center"><font color="#000000" face="宋体">88、89</font></p></td><td><p align="center"><font color="#000000" face="宋体">29</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SCHARM></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SCHARMID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装马牌</font></p></td><td><p align="center"><font color="#800000" face="宋体">90</font></p></td><td><p align="center"><font color="#800000" face="宋体">42</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SHORSE></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SHORSEID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装符印</font></p></td><td><p align="center"><font color="#000000" face="宋体">91</font></p></td><td><p align="center"><font color="#000000" face="宋体">43</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SBUJUK></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SBUJUKID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装军鼓</font></p></td><td><p align="center"><font color="#800000" face="宋体">92</font></p></td><td><p align="center"><font color="#800000" face="宋体">44</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SDRUM></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SDRUMID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">时装盾牌</font></p></td><td><p align="center"><font color="#000000" face="宋体">93</font></p></td><td><p align="center"><font color="#000000" face="宋体">45</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SSHIELD></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$SSHIELDID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">时装面巾</font></p></td><td><p align="center"><font color="#800000" face="宋体">94</font></p></td><td><p align="center"><font color="#800000" face="宋体">46</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SFTOWEL></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$SFTOWELID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置1</font></p></td><td><p align="center"><font color="#000000" face="宋体">100</font></p></td><td><p align="center"><font color="#000000" face="宋体">30</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM1></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM1ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置2</font></p></td><td><p align="center"><font color="#800000" face="宋体">101</font></p></td><td><p align="center"><font color="#800000" face="宋体">31</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM2></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM2ID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置3</font></p></td><td><p align="center"><font color="#000000" face="宋体">102</font></p></td><td><p align="center"><font color="#000000" face="宋体">32</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM3></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM3ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置4</font></p></td><td><p align="center"><font color="#800000" face="宋体">103</font></p></td><td><p align="center"><font color="#800000" face="宋体">33</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM4></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM4ID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置5</font></p></td><td><p align="center"><font color="#000000" face="宋体">104</font></p></td><td><p align="center"><font color="#000000" face="宋体">34</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM5></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM5ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置6</font></p></td><td><p align="center"><font color="#800000" face="宋体">105</font></p></td><td><p align="center"><font color="#800000" face="宋体">35</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM6></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM6ID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置7</font></p></td><td><p align="center"><font color="#000000" face="宋体">106</font></p></td><td><p align="center"><font color="#000000" face="宋体">36</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM7></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM7ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置8</font></p></td><td><p align="center"><font color="#800000" face="宋体">107</font></p></td><td><p align="center"><font color="#800000" face="宋体">37</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM8></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM8ID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置9</font></p></td><td><p align="center"><font color="#000000" face="宋体">108</font></p></td><td><p align="center"><font color="#000000" face="宋体">38</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM9></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM9ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置10</font></p></td><td><p align="center"><font color="#800000" face="宋体">109</font></p></td><td><p align="center"><font color="#800000" face="宋体">39</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM10></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM10ID></font></p></td></tr><tr><td><p align="center"><font color="#000000" face="宋体">首饰盒位置11</font></p></td><td><p align="center"><font color="#000000" face="宋体">110</font></p></td><td><p align="center"><font color="#000000" face="宋体">40</font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM11></font></p></td><td><p align="center"><font color="#000000" face="宋体"><$GODBLESSITEM11ID></font></p></td></tr><tr><td><p align="center"><font color="#800000" face="宋体">首饰盒位置12</font></p></td><td><p align="center"><font color="#800000" face="宋体">111</font></p></td><td><p align="center"><font color="#800000" face="宋体">41</font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM12></font></p></td><td><p align="center"><font color="#800000" face="宋体"><$GODBLESSITEM12ID></font></p></td></tr></tbody></table>

------------

自定义装备配置方式：
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1378d975cb579f8f5b6d7d574b7e625c)
# BUFF相关

# BUFF说明

BUFFID必须配置10000以上

重读BUFF（线上版本：只允许新增重读，不要删除或修改对应参数后重读，如有修改或删除BUFF请务必做好检测删除再重新给予）
buff系统需要把表头内的所有字段复制到自身的版本中，否则会引擎报错导致无法启动引擎

该功能请各位注意查看所有对应的后续扩展的配置字段，有效减少一些属性计算和常规的定时器触发。

1. 不支持减属性，属性造成负数时会造成数据溢出！(0323引擎以后支持负数)

2. 英雄BUFF不支持永久挂接，需要召唤时重新给予！

3. 目前BUFF不支持配置负属性，加属性也不可以超过42Y限制（正负值溢出会出问题）

4. 10000ID之前的系统类BUFF说明：
&gt; ① BUFF图标显示：删除对应BUFFID图标字段配置编号即可
&gt; ② 第8列原有系统功能(如：麻痹、锁定、冰冻等)按需配置二进制行为
     例：锁定需要(1.禁止走，2.禁止跑，4.禁止攻击，8. 禁止施法，16.禁止使用物品 64.禁止飞，128.锁定当前血量)
     设置为1+2+4+8+16表格内填写31即可，原有-1配置需要重新配置，不可填写为-1

------

## 触发

&gt; QF触发字段：需配置BUFF表第20列(不配置则不会触发)根据对应需求填写所需的触发,若无功能需求则不填,减少引擎消耗

### 玩家/英雄buff操作触发

`buffchange`/`herobuffchange`

| 参数  | 类型     | 空   | 默认 | 注释         |
| :---- | :------- | :--- | :--- | :----------- |
| actor | `object` | 否   |      | 玩家对象 |
| buffid | `integer` | 否   |      | buffID |
| groupid | `integer` | 否   |      | 组id |
| model | `integer` | 否   |      | 操作类型<br />1=新增;<br />2=更新;<br />4=删除; |

```lua
[[
    23.0830引擎新增登陆状态常量 &lt;$LOGINSTEP&gt;
    =1表示登陆前;=2表示登陆中;=3表示登陆完成
]]
function buffchange(actor, buffid, groupid, model)
    release_print("打印常量",getconst(actor,"&lt;$LOGINSTEP&gt;"))
end
```

### buff触发血量改变时

`bufftriggerhpchange`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增触发&lt;/font&gt;**

&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;"&gt;特殊：该触发中不允许直接删除buff，包括buff组关系等影响的删除(会内存泄漏)&lt;/font&gt;
&lt;font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;"&gt;特殊：如果一定要删除请使用延时回调&lt;/font&gt;

| 参数      | 类型      | 空   | 默认 | 注释                                     |
| :-------- | :-------- | :--- | :--- | :--------------------------------------- |
| actor     | `object`  | 否   |      | 玩家对象<br />buff触发者为怪物时,该参数无效 |
| buffID    | `integer` | 否   |      | buffid                                   |
| buffGroup | `integer` | 否   |      | buff组                                   |
| HP        | `integer` | 否   |      | hp                                       |
| buffHost  | `object`  | 否   |      | 释放者对象                               |
| mon       | `object`  | 是   |      | 怪物对象<br />buff触发者为玩家时,该参数无效 |
| result    | `integer` | 否   |      | 本次扣血                                 |

```lua
    function bufftriggerhpchange(actor,buffID,buffGroup,hp,buffHost,mon)
        return hp
    end
```

------

## 接口

### 添加buff

`addbuff`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|base     |`object`        |否   |    |   玩家、怪物对象    |
|buffid       |`integer`       |否   |    |   buff id，10000以后   |
|time     |`integer`       |是   |    |   时间,对应buff表里维护的单位   |
|OverLap      |`integer`       |是   |    |  叠加层数，默认1    |
|objOwner     |`object`        |是   |    |  施放者    |
|Abil     |`table`     |是   |    |  属性表 {[1]=200, [4]=20}，属性id=值   |
|result       |`bool`      |否   |    |  是否添加成功    |

### 删除buff

`delbuff`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|base     |`object`        |否   |    |   玩家、怪物对象    |
|buffid       |`integer`       |否   |    |   buff id   |

### 是否有buff

`hasbuff`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|base     |`object`        |否   |    |   玩家、怪物对象    |
|buffid       |`integer`       |否   |    |   buff id   |
|result       |`bool`      |否   |    |  是否有    |

### 获取buff信息

`getbuffinfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|base     |`object`        |否   |    |   玩家、怪物对象    |
|buffid       |`integer`       |否   |    |   buff id   |
|type     |`integer`       |否   |  类型3/4新增于<br />引擎64_23.10.24  | 1=叠加层数 <br />2=剩余时间(单位跟配置一致)<br />3=获取施法者对象(对象离线返回nil)<br />4=获取额外属性   |
|result       |`integer`       |否   |    |   返回值    |

### 获取buff模板信息

`getstdbuffinfo`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|buffID/buffName      |`integer`/`string`      |否   |    |   buffID/buff名称    |
|id       |`integer`       |否   |    |0:idx <br /> 1:名称; <br />2.组别;<br />3.配置时间;<br />4.配置属性; |
|result |`integer`         |是   |0    |   对应数值，不存在为0    |

### 获取角色所有buff

`getallbuffid`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|player       |`object`        |否   |    |   玩家对象    |
|result |`table`       |是   |    |   buff列表    |
```lua
    local list_buff = getallbuffid(actor)
    for i, buffid in ipairs(list_buff) do
        release_print("buff",i,buffid)
    end
```

### 设置buff堆叠层数

`buffstack`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释                          |
| :----- | :-------- | :--- | :--- | :---------------------------- |
| actor  | `object`  | 否   |      | 对象                          |
| buffid | `integer` | 否   |      | buffid                        |
| opt    | `string`  | 否   |      | 操作符 "+" "-" "="            |
| stack  | `integer` | 否   |      | buff层数 不可超出表中最大层数 |
| itimer | `boolean` | 否   |      | 是否重置buff 时间             |
```lua
  buffstack(actor,10000,"+",1,true)
```
# 内功/连击系统

###### 更新时间：引擎64_23.10.24

## 触发

### 玩家/英雄穴位点击触发

`pulse(X)-(X)` ~ `heropulse(X)-(X)`

&gt; 第一个X为经络(0-4)，第二个X为穴位(1-5)

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
```lua
local function pulse(actor,param1,param2,...)
    release_print("穴位点击触发",getbaseinfo(actor,1),param1,param2,...)
end
for i = 0, 4 do
    for j = 1, 5 do
        _G[string.format("pulse%d-%d",i,j)] = function (actor,...)
            pulse(actor,i,j,...)
        end
    end
end
```

### 玩家/英雄修炼经络触发

`pulselvup(X)` ~ `heropulselvup(X)`

&gt; X为经络(0-4)

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |玩家对象 |
```lua
local function pulselvup(actor,param1,...)
    release_print("穴位点击触发",getbaseinfo(actor,1),param1,...)
end
for i = 0, 4 do
    _G[string.format("pulselvup%d",i)] = function (actor,...)
        pulselvup(actor,i,...)
    end
end
```

## 接口

### 学习内功

`readskillng`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| player | `object` | 否   |      | 玩家对象 |

### 获取内功等级

`getnglevel`

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| player | `object`  | 否   |      | 玩家对象 |
| result | `integer` | 是   |      | 内功等级 |

### 调整人物内功等级

`changenglevel`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| player | `object`  | 否   |      | 玩家对象      |
| opt    | `string`  | 否   |      | 控制符(=,+,-) |
| value  | `integer` | 否   |      | 等级          |

### 调整人物内功经验

`changengexp`

| 参数   | 类型      | 空   | 默认 | 注释          |
| :----- | :-------- | :--- | :--- | :------------ |
| player | `object`  | 否   |      | 玩家对象      |
| opt    | `string`  | 否   |      | 控制符(=,+,-) |
| value  | `integer` | 否   |      | 经验          |

### 开启经络页签

`setpulsestate`

| 参数   | 类型      | 空   | 默认 | 注释                                                    |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------ |
| player | `object`  | 否   |      | 玩家对象                                                |
| pulse  | `integer` | 否   |      | 经络<br />0=冲脉<br />1=阴跷<br />2=阴维<br />3=任脉3<br />4=奇经 |
| isOpen | `integer` | 否   |      | 0=关闭<br />1=开启                                        |

### 开启经络穴位

`openpulse`

| 参数     | 类型      | 空   | 默认 | 注释                                                    |
| :------- | :-------- | :--- | :--- | :------------------------------------------------------ |
| player   | `object`  | 否   |      | 玩家对象                                                |
| pulse    | `integer` | 否   |      | 经络<br />0=冲脉<br />1=阴跷<br />2=阴维<br />3=任脉3<br />4=奇经 |
| acupoint | `integer` | 否   |      | 穴位（1~5,经络的五个穴位）                              |

### 修改经络的修炼等级格式

`changepulselevel`

| 参数   | 类型      | 空   | 默认 | 注释                                                    |
| :----- | :-------- | :--- | :--- | :------------------------------------------------------ |
| player | `object`  | 否   |      | 玩家对象                                                |
| pulse  | `integer` | 否   |      | 经络<br />0=冲脉<br />1=阴跷<br />2=阴维<br />3=任脉3<br />4=奇经 |
| opt    | `string`  | 否   |      | 控制符(=,+,-)                                           |
| level  | `integer` | 否   |      | 等级                                                    |

### 学习内功/连击技能

`addskillex`

| 参数       | 类型      | 空   | 默认 | 注释     |
| :--------- | :-------- | :--- | :--- | :------- |
| player     | `object`  | 否   |      | 玩家对象 |
| skillName  | `string`  | 否   |      | 技能名称 |
| skillLevel | `integer` | 否   |      | 技能等级 |

### 设置杀怪内功经验倍数

`killpulseexprate`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数 | 类型      | 空   | 默认 | 注释                                                      |
| :--- | :-------- | :--- | :--- | :-------------------------------------------------------- |
| play | `object`  | 否   |      | 玩家对象                                                  |
| pro  | `integer` | 否   |      | 倍率<br />倍数除以100为真正的倍率(200为2倍经验，150为1.5倍) |
| time | `integer` | 否   |      | 有效时间(秒)                                              |
```lua
function main(actor)
    killpulseexprate(actor,1000 ,10)
    LOGPrint("您当前杀怪内功经验倍数为10倍，有效时间10秒。")
end
```

### 设置地图的杀怪内功经验倍数

`plusemapkillmonexprate`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                                                |
| :---- | :-------- | :--- | :--- | :-------------------------------------------------- |
| play  | `object`  | 否   |      | 玩家对象                                            |
| mapid | `string`  | 否   |      | 地图id(`"*"`代表所有地图)                           |
| pro   | `integer` | 否   |      | 倍率<br />倍数除以100为真正的倍率<br />例如200为2倍经验 |

### 调整人物的当前内力值

`addinternalforce`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_23.12.07新增接口&lt;/font&gt;**

| 参数  | 类型      | 空   | 默认 | 注释                           |
| :---- | :-------- | :--- | :--- | :----------------------------- |
| play  | `object`  | 否   |      | 玩家对象                       |
| sFlag | `string`  | 否   |      | 操作符(=,+,-)                  |
| value | `integer` | 否   |      | 内力值                         |
| model | `integer` | 否   |      | 计算方式<br />0=点数<br />1=万分比 |
```lua
    addinternalforce(actor,"+",1,0)
```
# 回收相关




## 触发

### 回收触发

`recycling`

| 参数     | 类型      | 空   | 默认 | 注释       |
| :------- | :-------- | :--- | :--- | :--------- |
| actor    | `object`  | 否   |      | 玩家对象 |

```lua
function recycling(actor, ...)
    release_print("======================")
    release_print("recycling", getbaseinfo(actor, 1), ...)
    release_print("回收输出常量", getconst(actor, "<$RECYITEMS>"))
    release_print("回收总数常量", getconst(actor, "<$RECYITEMSCNT>"))
    release_print("回收获得总物品", getconst(actor, "<$TOTALRECYITEMS>"))
end
```
------------

## 接口

###### 更新时间：引擎64_24.03.14

 ### 增加回收组别

`addrecyclingtype`

| 参数          | 类型     | 空   | 默认 | 注释                                                 |
| :------------ | :------- | :--- | :--- | :--------------------------------------------------- |
| actor         | `string` | 否   |      | 玩家对象                                             |
| recyclingType | `string` | 否   |      | 回收组别，对应表中group字段(支持多类别配置用“;”分割) |

### 删除回收组别

`delrecyclingtype`

| 参数  | 类型     | 空   | 默认 | 注释                             |
| :---- | :------- | :--- | :--- | :------------------------------- |
| actor | `string` | 否   |      | 玩家对象                         |
| idx   | `string` | 否   |      | 回收组别索引，-1表示清空回收组别 |

### 执行回收

`execrecycling`

| 参数  | 类型     | 空   | 默认 | 注释     |
| :---- | :------- | :--- | :--- | :------- |
| actor | `string` | 否   |      | 玩家对象 |

### 执行自动回收

`autorecycling`

| 参数          | 类型      | 空   | 默认 | 注释                     |
| :------------ | :-------- | :--- | :--- | :----------------------- |
| actor         | `string`  | 否   |      | 玩家对象                 |
| interval      | `integer` | 是   |      | 检测间隔时间（单位：秒） |
| max_bag_space | `integer` | 是   |      | 执行回收的背包空格       |
```lua
--执行自动回收,2(间隔2秒检测一次) 10(背包格子 <= 10)
autorecycling(actor,2, 10)

--关闭自动回收
autorecycling(actor)
```
# 自定义排行榜





###**排行榜配置可根据自定义变量进行排序(有排行榜的版本必须配置)**

自定义排行榜过滤文件,将玩家角色ID"<$USERID>"添加到该文本后,玩家将不参与排行统计

过滤文件路径:`Mir200\Envir\QuestDiary\SortFilter.txt`

cfg_game_data.xls配置字段：`SortConfig` `参数1#参数2#参数3|参数1#参数2#参数3|参数1#参数2#参数3`

`参数1`：面板ID---自定义ID，用于打开对应面板
`参数2`：职业------0战士，1法师，2道士，3全部主号 10英雄战士，11英雄法师，12英雄道士, 13英雄全部
`参数3`：类型------1转生，2等级，3变量#自定义变量名

`M2--功能设置--其他设置-排行榜设置`

------------

> [**自定义排行榜示例下载**](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7ae846b6b05d868125d21d2e08799a29 "[QFunction-0 - 自定义排行榜.zip")

## 自定义排行榜刷新触发

`inisort`

| 参数   | 类型     | 空   | 默认 | 注释     |
| :----- | :------- | :--- | :--- | :------- |
| sysobj | `string` | 否   |      | 系统对象 |

## 自定义排行榜切换玩家和英雄的页签触发

`clicksortbutton`

| 参数   | 类型     | 空   | 默认 | 注释                               |
| :----- | :------- | :--- | :--- | :--------------------------------- |
| actor  | `string` | 否   |      | 玩家对象                           |
| ishero | `number` | 否   |      | 0=打开玩家页签；<br>1=打开英雄页签 |

## 自定义排行榜点击排名触发

`clicksortno`

| 参数    | 类型     | 空   | 默认 | 注释       |
| :------ | :------- | :--- | :--- | :--------- |
| actor   | `string` | 否   |      | 玩家对象   |
| ranking | `number` | 否   |      | 排行榜名次 

## 获取自定义排行榜缓存数据

`getsortdata`

> **<font color="#808080" style="font-size: 13px;">引擎64_24.05.23新增接口</font>**

| 参数    | 类型     | 空   | 默认 | 注释                   |
| :------ | :------- | :--- | :--- | :--------------------- |
| rankidx | `object` | 否   |      | 自定义排行榜页签       |
| result  | `string` | 否   |      | 排行榜数据<br>json格式 |

```lua
    local rank_index = 1
    local rank_list = json2tbl(getsortdata(rank_index))
```
# 求购行




### **求购行说明**

关联`M2--功能设置--个人商店--求购设置`(默认货币格式:货币ID#货币ID)
调用面板ID:`openhyperlink(actor,601)`
装备表物品表36列QiugouGoldList字段设置求购物品货币最小限制:货币ID1#货币数值|货币ID2#货币数值
装备表物品表37列QiugouMaxCnt字段设置求购数量限制大于0为最大求购数量,-1为不允许上架

------------

#### 求购上架前触发

`beforeaddqiugou`

| 参数     | 类型      | 空   | 默认 | 注释                 |
| :------- | :-------- | :--- | :--- | :------------------- |
| actor    | `object`  | 否   |      | 玩家对象             |
| itemName | `string`  | 否   |      | 求购物品名称         |
| itemIdx  | `integer` | 否   |      | 求购物品idx          |
| needNum  | `integer` | 否   |      | 求购的物品数量       |
| price    | `integer` | 否   |      | 求购的货币金额(总值) |
| result   | `bool`    | 否   |      | 是否允许本次求购     |
```lua
---求购上架前触发
---@param actor userdata 玩家对象
---@param itemName string 求购物品名称
---@param itemIdx integer 求购物品idx
---@param needNum integer 求购的物品数量
---@param price integer 求购的货币金额(总值)
---@return boolean 是否允许本次求购
function beforeaddqiugou(actor,itemName,itemidx,needNum,price,...)
    release_print("求购上架前触发",getbaseinfo(actor,1),itemidx,needNum,price,...)
    if getbaseinfo(actor,6) < 50 then
        messagebox(actor,"角色等级小于50级,无法发起求购~")
        return false
    end
    return true
end
```

#### 求购上架成功触发

`addqiugou`

| 参数     | 类型      | 空   | 默认 | 注释                 |
| :------- | :-------- | :--- | :--- | :------------------- |
| actor    | `object`  | 否   |      | 玩家对象             |
| itemName | `string`  | 否   |      | 求购物品名称         |
| itemIdx  | `integer` | 否   |      | 求购物品idx          |
| needNum  | `integer` | 否   |      | 求购的物品数量       |
| price    | `integer` | 否   |      | 求购的货币金额(总值) |
| result   | `bool`    | 否   |      | 是否允许本次求购     |
```lua
---求购上架成功触发
---@param actor userdata 玩家对象
---@param itemName string 求购物品名称
---@param itemidx integer 求购物品idx
---@param needNum integer 求购的物品数量
---@param price integer 求购的货币金额(总值)
---@return boolean 是否允许本次求购
function addqiugou(actor,itemName,itemidx,needNum,price,...)
    release_print("求购上架成功触发",getbaseinfo(actor,1),itemidx,needNum,price,...)
end
```

#### 出售前触发

`beforesellqiugou`

| 参数     | 类型      | 空   | 默认 | 注释                 |
| :------- | :-------- | :--- | :--- | :------------------- |
| actor    | `object`  | 否   |      | 玩家对象             |
| itemName | `string`  | 否   |      | 出售物品名称         |
| itemIdx  | `integer` | 否   |      | 出售物品idx          |
| needNum  | `integer` | 否   |      | 出售的物品数量       |
| price    | `integer` | 否   |      | 出售的货币金额(总值) |
| result   | `bool`    | 否   |      | 是否允许本次出售     |
```lua
---出售前触发
---@param actor userdata 玩家对象
---@param itemName string 出售物品名称
---@param itemidx integer 出售物品idx
---@param num integer 出售的物品数量
---@param price integer 出售的货币金额(总值)
---@return boolean 是否允许本次出售
function beforesellqiugou(actor,itemName,itemidx,num,price,...)
    release_print("出售前触发",getbaseinfo(actor,1),itemidx,num,price,...)
    if getbaseinfo(actor,6) < 50 then
        messagebox(actor,"角色等级小于50级,无法出售道具~")
        return false
    end
    return true
end
```

#### 卖出成功触发

`sellqiugou`

| 参数     | 类型      | 空   | 默认 | 注释                 |
| :------- | :-------- | :--- | :--- | :------------------- |
| actor    | `object`  | 否   |      | 玩家对象             |
| itemName | `string`  | 否   |      | 卖出物品名称         |
| itemIdx  | `integer` | 否   |      | 卖出物品idx          |
| needNum  | `integer` | 否   |      | 卖出的物品数量       |
| price    | `integer` | 否   |      | 卖出的货币金额(总值) |
```lua
---卖出成功触发
---@param actor userdata 玩家对象
---@param itemName string 卖出物品名称
---@param itemidx integer 卖出物品idx
---@param num integer 卖出的物品数量
---@param price integer 卖出的货币金额(总值)
function sellqiugou(actor,itemName,itemidx,num,price,...)
    release_print("卖出成功触发",getbaseinfo(actor,1),itemidx,num,price,...)
end
```
# 机器人事件



## 添加机器人事件

`addscheduled`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数          | 类型     | 空   | 默认 | 注释       |
| :------------ | :------- | :--- | :--- | :--------- |
| scheduledName | `string` | 否   |      | 机器人名称 |
| executeMethod | `string` | 否   |      | 执行方式   |
| time          | `string` | 否   |      | 时间参数   |
| funcName      | `string` | 否   |      | 跳转标签   |

```lua
    [[ 
        注:增删机器人事件接口为异步操作,执行方式参考机器人脚本
        ;SEC：按秒运行

        ;MIN：按分运行

        ;HOUR：按小时运行

        ;DAY：按天运行

        ;RunOnDay：按每天什么时候运行

        ;RUNONWEEK：按星期几及时间运行
    ]]

    local scheduled_name = "机器人"
    local bool = hasscheduled(scheduled_name)
    release_print("hasscheduled",bool)

    -- 添加机器人
    addscheduled(scheduled_name,'SEC','5','@scheduled_backcall')

    -- 删除机器人
    delscheduled(scheduled_name)
```

## 删除机器人事件

`delscheduled`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数          | 类型     | 空   | 默认 | 注释       |
| :------------ | :------- | :--- | :--- | :--------- |
| scheduledName | `string` | 否   |      | 机器人名称 |

## 判断机器人事件

`hasscheduled`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.05.23新增接口&lt;/font&gt;**

| 参数          | 类型     | 空   | 默认 | 注释                        |
| :------------ | :------- | :--- | :--- | :-------------------------- |
| scheduledName | `string` | 否   |      | 机器人名称                  |
| result        | `bool`   | 否   |      | true=有事件<br />false=无事件 |


# 阵营系统




### **说明**

**
1.阵营地图设置：mapinfo文件 ，地图标签增加 CAMP，如[wqd 武器店] ONKILLMON NORECONNECT(3:330:335) SAFE1 CAMP
2.阵营攻击模式开启:`M2 - 参数设置 - 状态控制 - 允许阵营攻击模式`;
3.特殊:阵营ID离线清除;
**

------------

### 设置阵营ID

`setcamp`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| actor  | `object`  | 否   |      | 玩家/怪物对象 |
| campid | `integer` | 否   |      | 阵营id   |
```lua
    setcamp(actor,1)
```

### 获取阵营ID

`getcamp`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.08.07新增接口&lt;/font&gt;**

| 参数   | 类型      | 空   | 默认 | 注释     |
| :----- | :-------- | :--- | :--- | :------- |
| actor  | `object`  | 否   |      | 玩家/怪物对象 |
| result | `integer` | 否   |      | 阵营id   |
```lua
    local camp_id = getcamp(actor)
```
# 其他



## 邮件相关

### 发送邮件
`sendmail`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |---|------      |
|userid |`string`    |否   |    |   玩家UserId，如果是玩家名，需要在前面加#，如:#张三 |
|id |`integer`    |否   |    |自定义邮件ID |
|lable |`string`    |否   |    |邮件标题 |
|memo |`string`     |否   |     |邮件内容 |
|Rewards |`string`    |否   |    |附件内容：物品1#数量#绑定标记&amp;物品2#数量#绑定标记，&amp;分组，#分隔<br />绑定标记值参考物品帮助 |

```lua
function main(self)
    sendmail(getbaseinfo(self,2),1,"测试","物品发放","木剑#2")
end
```

## 商城相关

### 是否满足指定条件显示（canshowshopitem触发中使用）
`notallowshow`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|canshow     |`integer`      |否   |    | 1-不显示，0-显示 |

### 是否满足指定条件购买（canbuyshopitem触发中使用）
`notallowbuy`

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|play     |`object`      |否   |    |   玩家对象 |
|canbuy     |`integer`      |否   |    | 1-不允许购买，0-允许购买 |

## 敏感词汇检测
`exisitssensitiveword` 需要维护Envir目录下的 SensitiveWord.txt。  

|参数|类型|空|默认|注释|
|:----    |:-------    |:--- |----|------      |
|str     |`string`      |否   |    |   要检测的文本 |
|result1     |`bool`    |否   |    | true：有敏感词 |
|result2     |`string`  |否   |    |   敏感词 |

### 获取IP地址下所有的在线角色名称列表

`getplaylistbyip`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数          | 类型     | 空   | 默认 | 注释                                       |
| :------------ | :------- | :--- | :--- | :----------------------------------------- |
| IPAddress     | `string` | 否   |      | IP地址                                     |
| getAllPlayers | `number` | 否   | 0    | 是否获取全部玩家列表0/1(默认限制返回200个) |
```lua
    local varName = "S1"
    local ipstr = getconst(actor,"&lt;$IPADDR&gt;")
    -- callscriptex(actor,"getplaylistbyip",ipstr,varName)
    local list = getplaylistbyip(ipstr,0)
    -- local list = getplaydef(actor,varName)
    release_print("list",ipstr,tbl2json(list))
```

------------

### 发送登陆信息[[反外挂]](http://engine-doc.996m2.com/web/#/38/10299 "[反外挂]")

`sendloginmsg`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释       |
| :----- | :------- | :--- | :--- | :--------- |
| userID | `string` | 否   |      | 玩家唯一ID |

### 检测登陆信息[[反外挂]](http://engine-doc.996m2.com/web/#/38/10299 "[反外挂]")

`logincheckent`

&gt; **&lt;font color="#808080" style="font-size: 13px;"&gt;引擎64_24.03.14新增接口&lt;/font&gt;**

| 参数   | 类型     | 空   | 默认 | 注释       |
| :----- | :------- | :--- | :--- | :--------- |
| userID | `string` | 否   |      | 玩家唯一ID |
# 下载篇



#### &amp;bull; 资源下载:

|资源|介绍|更新时间|
|:----|-----|-----|
|[论坛三端lua底板](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=8a0097964b52142fe3ae0a32f18aedad "[单机演示服_24_0603.zip")|前端新框架/h5客户端|2024-06-03|
|[服务端代码提示](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=10056cc243b55464b8412a97b1e762a2 "[服务端代码提示[24.1111].rar")|服务端代码提示|2024-11-11|
|[客户端代码提示](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=6574fb7ff3d46bcba817aedcb0469f68 "[客户端代码提示[24.0729].zip")|客户端代码提示|2024-07-29|
|[功能示例](http://engine-doc.996m2.com/web/#/22/1357 "前端教学链接")|功能示例|2024-07-01|

#### &amp;bull; 三端LUA视频教学下载:

|资源|介绍|更新时间|
|:----|-----|-----|
|[第一课：本地单机搭建.mp4](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=03d664e2a3e7cac1dff74984af6ebee8 "lua本地单机架设教程.mp4")|本地数据库与引擎搭建|2023-05-29|
|[第二课：前后端交互.mp4](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=4f54fc3b14a270cc8d424d0f051acdf2 "前后端交互.mp4")|前后端交互教学|2023-06-05|
|[第三课：熟悉底板.mp4](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=d86720de966497351d1e7cd8052cc127 "熟悉底板.mp4")|熟悉底板|2023-07-28|

#### &amp;bull; 其他链接:

|资源|介绍|
|:----|-----|
|[其他视频教学](http://engine-doc.996m2.com/web/#/38/4981 "其他视频教学")|996引擎教学视频(全)|
|[TXT在线说明书](http://video-help.hgtny.cn:9999/shipin/web/index.html "TXT在线说明书")|在线说明书|
|[常用问答文档](http://engine-doc.996m2.com/web/#/42/5721 "常用问答文档")|常见Q&amp;A问答|

# 底板区服架设

### 1.下载996引擎·多端版 引擎包
[http://video-help.hgtny.cn:9999/shipin/web/index.html](http://video-help.hgtny.cn:9999/shipin/web/index.html)

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9a6f547778ffc467c169baa96761d26f)

---
### 2.论坛下载三端lua引擎底板
在三端lua说明书中下载最新的底板
[http://engine-doc.996m2.com/web/#/9/5026](http://engine-doc.996m2.com/web/#/9/5026)
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6dacdbb1623abdbead8d6dc5ba94d9e8)

---
### 3.开始更新程序
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2b87b9238e44f1bd566c63ef1e1cf6a6)

---

### 4.下载客户端版本，开发建议使用debug版本

http://engine-doc.996m2.com/web/#/22/159

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=79dd7dcffcffaf49f3e742fe175379d9)

---

### 5.将底板压缩包中的/dev文件夹,放于解压的客户端文件中

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=818b60c373373e2b267f41165eed74b2)

---
### 6.配置游戏服务器
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=3c578fb61bc8c8082d14dcbd24422804)


# 本地数据库配置

# 本地建库

## 1. 下载压缩包 [本地数据库.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=e8c30a94cc4180810e042b7360a12f80 "[SQLSERVER.zip")
## 2. 解压至D盘根目录（解压至其他目录的话，可修改struct.sql脚本的路径）。
### 注:压缩包内的是64_23.0323引擎包的数据库版本,其他版本需执行引擎包内的struct.sql脚本

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=3254eb232617b2ae801efb9e587c767a)

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0483d5e2d4ee1018621891facbfbcb61)

---
## 3.修改登陆端口信息。
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=405ec18cbf7e48ea4faaeafc54eaa15b)

---
## 4.启动本地数据库，并执行SQL脚本。
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a69d04c613d5c0017b4fe681339416ae)

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6ceb21987af00d583d58b88c27c86f06)

---
## 5.刷新数据库，并设置账号密码，最后将数据库配置信息填入M2中。

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=71db4fcb03129900775e846c7948a75d)

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=e4df0aa2599a3483f2911f0cb2bcc3c9)

------------

# 修改本地数据库开区时间

- 本地建库之后 ， 数据库中开服天数是null值，  需要手动修改 [[NavicatPremium.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=70e6bef5554574e94f5eaa3f9b2dd67a "[NavicatPremium.zip")]
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ade84637b07dcbe46a7387302ebc4bd9)

- 选择 sql server
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b9f831069376b8cd0f74b37b9a184295)

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=26b0fd77beaf62e171f5b96c1a2debef)

- 修改开区时间
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=cb314d82aa3a1a13b2fe97913757b58e)
# 前后端交互

## 1.首先在cfg_npclist.xls表中,配置一个npc,并根据文本路径和地图号添加对应的lua脚本;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=51a00cf169b07219a19dcded97eb219d)

------------

## 2.然后我们配置客户端,进入游戏世界会自动调用一下脚本,其中ssrmain为新老框架都调用,GUIUtil.lua只在3.40新框架调用,我们以GUIUtil为例,在脚本中加载了testOBJ.lua脚本

其中pcall函数主要用于抛出异常,具体用法可以自行百度
- dev/scripts/ssr/ssrgame/ssrmain.lua
- dev/GUILayout/GUIUtil.lua

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2a709600abb5a03c4c4473f744287701)

------------
## 3.在testOBJ.lua脚本中,我们注册一个100号消息的接收触发,并且在收到100号消息后去创建界面;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6c7b7fb6195e68eb685db2eb48f0a87d)

------------
## 4.GUI:LoadExport接口用于加载UI文件,UI文件在游戏内ctrl+F9可打开可视化编辑;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=74553174d5be2feb44ad232c7459b58a)

------------

## 5.用GUI:ui_delegate接口将ui快速化加载,返回值可用于快速调用控件,例子中给黑色背景和关闭按钮添加了关闭面板的按钮事件,又给Button按钮添加了给服务端发110号消息的事件;
- 注:使用这个方法需要避免子控件重名

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9c2f6d0907ebdd65be1248f886506d1e)

------------

## 6.QFunction-0.lua脚本中,handlerequest函数用于监听来自客户端的消息,我们监听101号消息并使用callfunbynpc接口调用到治疗师脚本的test函数中,并在函数中将参数2数值+1重新下发101号消息给客户端;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6cc4276e95489316029d3cb60181f4e8)

------------

## 7.在客户端中注册一个101号消息的接收触发,并且在收到101号消息后去修改界面文件中文本内容;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b268fb1c1b0b716630f2261a22046ff4)

## 8.所有都完成后,我们打开游戏查看实际效果;

![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=dc500a53f9338a0da2e2dfc5b3504f29)

------------

## 以下是案例代码
- 服务端 [Mir200.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=be3098bdd2c8a1de75e695f00fa3ab2e "[Mir200.zip")
- 客户端 [dev.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=835487e3cd00832994eecfad215b1c2e "[dev.zip")
# 问答篇



## 三端lua客户端如何获取服务端变量值？
- M2配置`功能设置-其他设置-前端变量推送`,客户端监听`LUA_EVENT_SERVER_VALUE_CHANGE`[服务器下发的变量改变事件],并通过元变量`SERVER_VALUE`获取；或者也可以通过网络消息自己通知给前端。
```lua
[[
	注意:人物标记的变量名是"{3}"而不是"[3]"
]]
SL:RegisterLUAEvent(LUA_EVENT_SERVER_VALUE_CHANGE, "GUIUtil",  function(data)
    SL:dump(data,"服务端属性下发")
    SL:GetMetaValue("SERVER_VALUE", data.key)
end)
```

------------

## 本地和线上PC客户端正常,但是手机客户端UI或者功能异常是什么原因?
- 手游客户端会区分大小写,需自己检查文件/代码/资源的大小写是否对应,可以自行下载adb(安卓日志工具)查看报错内容;
  adb流程: http://engine-doc.996m2.com/web/#/9/10326

------------

## 每次重启服务器后,math.random获取的前几个随机数都有一定规律是什么原因?
- 需要在QFunction-0.lua文件设置随机种子。参考底板：
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=e057145a386205b68ce5134377a7c72e)

------------

## 如果获取聚灵珠的经验值？
- 获取物品的持久度即可，矿石纯度，魔血石剩余，肉的品质也都是持久度（Dura）;
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&amp;sign=af6a6ad9730545d58ff8f3459f5891a1)

------------

## 无法登录游戏,在选角界面转圈是什么原因?
### 登录/创角界面转圈
- 检查M2控制台是否完全启动,启动失败看一下卡在哪步,并检查对应的配置;
- 检查游戏网关是否启动,未启动的话拿完整引擎包再覆盖后重试;
- 检查日志是否有异常,例如未配置紧急回城点会在日志中提示,并且无法进入游戏;
- 检查地图配置是否异常;
- 本地数据库的则新建或者更新数据库(引擎包内的`sql`/`SQL数据库脚本`文件夹的.sql文件都执行一下试试);

### 开门界面转圈
- 工具服检查和运营后台的配置是否对应,端口是否被其他程序或者引擎占用(特别注意 &lt;font color="#FF0000" style="font-size: 16px;"&gt;酷狗&lt;/font&gt; 会占用7000的端口);
- 本地单机服检查M2引擎配置是否是单机服的配置(游戏端口=7000,IP地址=127.0.0.1);
# adb流程

<span style="font-size:28px;">adb流程</span>

------------
###1.下载文件
[logview-0.20-SNAPSHOT.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=10e986c24c6a5ffa9ee23e3fa66122e8 "[logview-0.20-SNAPSHOT.zip")
安装java
[java8x64_8.0.1810.13.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=26bd5fdd309f8772c514f5c2e7c33176 "[java8x64_8.0.1810.13.zip")

###2.下载安装并打开雷电模拟器（这里以雷电模拟器为例）
。。。

###3.打开上面下载的文件
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ce9e34cf65957dd3e11226be2bce6a46)
<br>
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c829c152841b5ab19d59724b3f885242)
<br>
选择对应路径
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=8cc0e1e5018a469d09b5e68a5744ae40)
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ccd349850b88c3bade175153c3bb7d54)
###4.cmd
打开雷电模拟器里的对应路径
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=37f97e3e25ea715d3ddae26363d19b39)
<br>
输入cmd并按回车键
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d6398d8421d03d6e2817fc6b77c144b2)
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=5ac8f6a853572368e58a8f50c3712e7e)
<br>
输入 adb.exe connect 127.0.0.1:5555 (这里的5555是雷电模拟器端口号)
回车
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=f26e01874d90aacf2f81ae6637c0d059)
<br>

###5.模拟器中打开游戏
成功
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=26fd6399ab6f63d0240508dba162f684)
<br>
右键选择查看对应app的log
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=663388f33b5e1a8db8d6b60f2f42afd8)

