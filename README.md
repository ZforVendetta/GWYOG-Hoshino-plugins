# 公主连结实用/娱乐插件 for HoshinoBot on Mirai

A repository for [HoshinoBot(V2)](https://github.com/Ice-Cirno/HoshinoBot) based [PCR](http://priconne-redive.jp/) plugins made by myself.


## 简介

一些基于 [HoshinoBot(V2)](https://github.com/Ice-Cirno/HoshinoBot) 开发的公主连结实用插件或有趣的娱乐插件，开发环境为Mirai(开发环境用的是cqhttp-mirai，插件在go-cqhttp上也可以正常使用)。

其他还有一些之前在酷Q Pro环境下开发的HoshinoBot插件，我没迁移到此仓库中，不过它们大部分都可直接装在Mirai的HoshinoBot上，它们是：

- **[轴管理插件](https://github.com/GWYOG/HoshinoBotTimelinePlugin)**：加入了向机器人录入图片或者文字轴的指令，之后可以方便地查询数据库中存放的轴。此插件可使公会在会战中更方便的查询、交流、优化轴，也可以让几个公会之间共享轴。

- **[box统计插件](https://github.com/GWYOG/HoshinoBotBoxCollectionPlugin)**：加入指令，在管理员设定好需要统计的角色星级后，机器人会自动私聊指定人员询问并统计汇总他们的角色星级。统计完毕后，在群内可以使用指令方便的查看分类汇总的统计结果；也可以自动生成统计结果的csv文件，或者把统计结果的表格以图片形式发送到群中(这个功能很实用!)。

- **[猜语音小游戏插件](https://github.com/GWYOG/HoshinoBotVoiceGuessPlugin)**：机器人会自动从干炸里脊资源站下载所有角色的打开游戏时说的的那句"cygames"语音。之后机器人会随机发送一句语音到群里，让群友猜猜是哪位角色说的，并在一定时间后公布正确答案和猜对的人。由于只有embedded版本的cqhttp-mirai支持发送语音，且只支持发送amr而非m4a格式的语音(go-cqhttp也是一样)，因此此插件暂时无法用在Mirai上。之后等cqhttp-mirai或go-cqhttp发送语音功能稳定后，会移植此插件到Mirai上。

- **[会战名次查询插件](https://github.com/GWYOG/HoshinoBotClanRankSearchPlugin)**：使用查询指令后，机器人会从镜华会战名次查询网获取数据，把需要查询的公会的会战当前名次或历史名次发送到群里。这个插件功能刚写到一半就开巨蟹座会战了，所以功能比较简陋。打完会战发现github上有不少同类型的功能更完善的插件，所以就弃坑了(笑)。
 
## 此仓库插件介绍(基于Mirai开发)
 #### 猜角色小游戏插件pcrdescguess
 注意：此插件的代码已被@Ice-Cirno 重构并即将并入HoshinoBot本体。此仓库中此插件的代码仅供归档用，不再额外开发新功能。
|指令|说明|
|-----|-----|
|猜角色|机器人会随机给出角色的一些描述，群友需要根据这些描述猜出是哪个角色|
|猜角色排行榜|显示猜角色小游戏猜对次数的群排行榜|

 #### 猜头像小游戏插件pcravatarguess
 注意：此插件的代码已被@Ice-Cirno 重构并即将并入HoshinoBot本体。此仓库中此插件的代码仅供归档用，不再额外开发新功能。
|指令|说明|
|-----|-----|
|猜头像|机器人会发送某个角色头像随机截取的一小部分，群友需要猜出它来自哪个角色头像|
|猜头像排行榜|显示猜头像小游戏猜对次数的群排行榜|

 #### B站搜索爬虫bilisearchspider
 这是B站视频搜索引擎的爬虫。在设定好爬取关键词后，每隔5分钟机器人会把这几分钟里以这些关键词搜索出来的新发布的视频推送到QQ群中。推送的内容包括：视频封面、视频标题、up主名字、链接。
 
 这个插件主要是为了会战而生，比如如果设定关键词为“狮子座公会战”，那么会战期间所有在B站发布的轴都会推送到QQ群里。此外，也可以设置一些其他的关键词供娱乐使用。
 
 需要注意的是，由于B站搜索引擎的特点，设定单一关键词“狮子座公会战”并不能把所有相关视频都搜出来。比如起名“狮子座工会战B2130W轴”的视频就没法靠这个关键词搜出来。这时需要再添加另一个关键词“狮子座会战”。插件支持任意多的关键词，这些关键词搜索出视频的并集会被推送到群里。
 
 只要存在关键词爬虫就会自动启动，如果想停用请使用指令把关键词全删掉。
|指令|说明|
|-----|-----|
|添加B站爬虫 <关键词>|添加爬取关键词。每次添加一个，可添加多次|
|查看B站爬虫|查看当前爬取关键词列表|
|删除B站爬虫 <关键词>|删除指定爬取关键词|

 #### nga会战爬虫ngaclanbattlespider
 顾名思义，这是爬取nga会战相关帖子的HoshinoBot爬虫插件。目前内置的关键词只会爬取一些有价值信息的帖子，包括但不限于会战轴。无意义的感叹帖、水贴不会爬取。目前暂不支持外部指令添加自定义关键词。
 
注意！安装此插件需先安装第三方库`selenium`，并配置好chrome和chromedriver，windows系统可参考[这篇文章](https://www.jianshu.com/p/64c92b1c05dd)。之后再使用通常方法安装此插件到HoshinoBot上。
 
|指令|说明|
|-----|-----|
|启用nga会战爬虫 [国服/日服/台服]|启用nga会战爬虫并设置爬取版块为:国服讨论/日服讨论/台服讨论，默认是国服讨论。每隔一段时间爬虫将自动爬取nga会战相关帖子|
|禁用nga会战爬虫|关闭nga会战爬虫服务|

#### 公主连结午间音乐pcrmiddaymusic
插件汇总了公主连结全活动ed、游戏主线op/ed以及一些角色歌。每日午间会随机推送一首音乐到群中。机器人首先会发送一些基本信息：包括音乐出处、相关图片、歌名和歌手名，如果是活动ed还会包含活动剧情简介。然后机器人会发送音乐的qq音乐/网易云音乐/B站视频卡片。
平时也可以使用以下指令直接请求机器人推送一首pcr音乐。（由于目前cqhttp-mirai或go-cqhttp在短时间大量发送xml格式的qq音乐卡片时会被腾讯风控，所以使用这个指令时机器人不会发送qq音乐卡片而是直接发送歌曲链接。）
|指令|说明|
|-----|-----|
|来点音乐|随机推送一首公主连结相关音乐|

## 安装方式

1. clone或者下载此仓库的代码

2. 将需要安装的插件文件夹放在`hoshino/modules/`文件夹中。比如如果想安装pcrdescguess插件，那么就把`pcrdescguess`文件夹放入。
  
3. 打开`hoshino/config/`文件夹中的`__bot__.py`文件，在`MODULES_ON`中加入插件的名称。比如如果想安装pcrdescguess插件，那么就加入一行`'pcrdescguess',`

4. 个别插件可能需要安装额外的第三方库。如果插件有需要安装的前置依赖，我在此README的插件介绍一节中注明。

## 注意事项
 最好事先下载全角色头像放在HoshinoBot的资源文件夹中。虽然机器人在发现需要发送的角色头像缺失时也会自动从干炸里脊资源站下载，不过这样机器人会变卡。