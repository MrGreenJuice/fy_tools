#### Discord工具盒使用教程

使用前建议先阅读该说明或者观看讲解视频

讲解视频：

基本功能 - https://www.youtube.com/watch?v=TBG0hbVKVUo

基本功能 - https://www.youtube.com/watch?v=Q_q6i_eXV9E

普通邀请 - https://www.youtube.com/watch?v=cZa5Ymo95iw

高级邀请 - https://www.youtube.com/watch?v=yu5T-dYN6_8&t=556s

随着功能的新增与改进，视频中展示的界面也当前系统界面有些许出入，有任何问题可以联系我

-----

#### 功能说明

- [x] 自动聊天及回复
- [x] 邀请及进群验证
- [ ] 一键抽奖



#### 1.自动聊天及回复

作为用户使用最为频繁的功能，也作为市场上同类工具基本都具有的功能，客观分析下现状

|                             |      客户端脚本型      |  平台型  |
| :-------------------------: | :--------------------: | :------: |
|    是否需要本地安装环境     |           是           |    否    |
| 多discord账号之间IP是否独立 |           否           |    是    |
|    机器指纹信息是否一致     |       大部分一致       |   独立   |
|        更新版本方式         | 重新下载安装软件或脚本 | 刷新页面 |
|  可否在移动端查看进行情况   |        一般不能        |   可以   |

作为开发人员，客户端脚本的开发工作量相较于平台型是小许多的，因为在一定程度上，它将开发成本转嫁了用户

##### 1.1使用前准备 - 导入discord账户

<img src="https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/create-discord-user.jpg" alt="image-20220216141513675" style="zoom:50%;" />

如图所示，**账号管理**中导入discord账号

|   参数   |                          含义                           | 是否必填 |                示例                 |
| :------: | :-----------------------------------------------------: | :------: | :---------------------------------: |
|  平台ID  | discord账户ID，开启**开发者**模式后点击头像右键可复制ID |    是    |         931513420178661396          |
|   账号   |             discord账户登录名，便于区别账户             |    否    |         buou163@outlook.com         |
|   密码   |         discord账户登录密码，启用改名功能时需要         |    否    |               xxxxxxx               |
| 登录凭证 |         获取方式参见视频，通过该凭证可操作账户          |    是    | OTMNjYxMzk2.YfTEwQ.F8NuiJ_ls1jtpOuk |
|   备注   |        给账户一个说明，比如该账户用来肝白名单等         |    否    |           肝xxx项目白名单           |

表格中有一列**账号状态**，只需要关注其状态是否为**需登录**即可，平台检测账号时是延迟检测的（用到才会去检测登录状态）



##### 1.2使用前准备 - 创建话术

![image-20220216143033038](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/create-chat.jpg)

如图所示，在**数据中心**中创建话术

在本系统内，为话术做了两个类别

- 普通发言话术 - 自动发言、回复非管理员时使用的话术
- 回复管理员专用话术 - 需要回复管理员时使用的话术

上传话术文件格式如下，每一行就是发言时的原文

```
寥落古行宫，宫花寂寞红
曾经富丽堂皇的古行宫已是一片荒凉冷落
皇帝在京城之外的宫殿
```

这边建议多建一些话术，至少建3种，因为本系统可以支持多种场景的发言，所以不同话术应对不同场景，会让其看起来更像是真人在发言

- 普通发言话术 - 自动发言话术
- 普通发言话术 - 回复普通成员话术
- 回复管理员专用话术 - 舔管理员用的话术



##### 1.3使用前准备 - 导入昵称

![nickname-collect](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/nickname-collect.jpg)

如图所示，在**数据中心**中创建昵称

目的是创建任务时，可以进行配置，打到发言n次后改变昵称的效果

上传昵称文件格式如下，每一行就是要修改的昵称前缀（任务配置时，可添加固定后缀）

```
路飞
悟空
比克
```

若不需要修改昵称，则可以不进行该配置



##### 1.4创建聊天任务

![create-task](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/create-task.jpg)

如图所示，在**任务管理**中创建聊天任务

|    参数    |             含义             | 是否必填 |        示例        |
| :--------: | :--------------------------: | :------: | :----------------: |
|  任务名称  |       标识该任务的目的       |    是    |   xxx项目白名单    |
|  服务器ID  |       项目方的服务器ID       |    否    | 905382875183054859 |
| 聊天频道ID | 项目方服务器内的具体聊天频道 |    是    | 907877461948243968 |

服务器ID跟聊天频道ID经常有用户是弄错，这里特做下解释

一个discord频道的链接如：https://discord.com/channels/905382875183054859/907877461948243968

可以看到在链接的后面后两串数字

前者905382875183054859 - 即为服务器ID

后者907877461948243968 - 即为聊天频道ID

创建完成后的任务处于**暂停状态**，此时还需要进行一些配置，才能使任务正常开始运行（需手动开启任务）

##### 1.5配置聊天任务 - 基础配置

<img src="https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/task-base-config.jpg" alt="task-base-config" style="zoom:50%;" />

|      参数       |                       含义                       | 是否必填 | 示例 |
| :-------------: | :----------------------------------------------: | :------: | :--: |
|    聊天话术     |               自动聊天时使用的话术               |    是    |      |
|  回复聊天话术@  | 非管理员@你时使用的话术，若配置则会@该用户并回复 |    否    |      |
| 回复聊天话术非@ | 非管理员回复你时使用的话术，若配置则会回复该用户 |    否    |      |
|  删除消息概率   |            消息发出后删除的概率0-100             |    否    |  60  |
|    顺序发言     |               按照话术进行顺序发言               |    否    |      |

删除消息概率 - 0表示不删除，100表示每条都删除，如有需求建议配置60-70；若每条消息都删除，且一直在该频道内发言，可能会触发风控，因为这明显不是一个正常人该有的行为

顺序发言 - 正常情况下，发言是随机的，也就是从话术里随机挑取一条；若用户对话术有比较高的设计能力，可使用该功能进行顺序发言

##### 1.6配置聊天任务 - 配置任务成员

![task-user-config](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/task-user-config.jpg)

|     参数     |          含义          | 是否必填 | 示例 |
| :----------: | :--------------------: | :------: | :--: |
| 任务执行间隔 | 每次发言间隔时长（秒） |    是    |  60  |
|              |                        |          |      |

讲解视频里也说过，我们经过大量账号的测试得出的结论

发言频率30秒 - 5~10分钟内必被踢

发言频率60秒配合删除消息 - 在相对活跃的频道内往往能存活1-2天以上

发言频率60秒配合删除消息以及管理员监控 - 在相对活跃的频道内往往能存活3-5天以上

本系统内置时间为至少60秒发言间隔，加上一定的随机等待

##### 1.7配置聊天任务 - 高级配置

![task-advance-config](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/task-advance-config.jpg)

**这是一块非常重要的配置，耐心理解**

高级配置类型分为三种，我们分别讲解

- 管理员筛查机器人
- 回复管理员@
- 回复管理员非@



> 管理员筛查机器人

![manager-avoid](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/manager-stop-chat.jpg)

|     参数     |         含义         |       是否必填       | 示例 |
| :----------: | :------------------: | :------------------: | :--: |
|    话术ID    |                      | 该类型下不用选择话术 |      |
| 暂停发言时长 | 任务暂停时长（分钟） |          是          |  10  |
|    优先级    |  判定顺序，建议填1   |          是          |  1   |
|    关键词    |   触发判定的关键词   |          是          | 禁言 |

关键词可以多配几个，例如常见的 扫地、禁言、机器人、木头人等等

**杀手锏** - 现在有些管理员玩的花里胡哨，比如要扫地了，他不发文字，发个图片，图片内容是'非机器人禁言'等等；应对措施为进入该频道后，先往上翻一番，看看管理员有没有扫地过，如果管理员喜欢玩的花里胡哨的，那么我们**不要设置关键词**，这样做的含义即为

**只要管理员说话了，那么我就停止发言，暂停任务**



> 回复管理员@

<img src="https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/reply-manager.jpg" alt="reply-mnanager-@" style="zoom:50%;" />

|  参数  |       含义       | 是否必填 | 示例 |
| :----: | :--------------: | :------: | :--: |
| 话术ID | 回复管理员的话术 |    是    |      |
| 优先级 |    判定优先级    |    是    |      |
| 关键词 | 触发回复的关键词 |    否    | 在吗 |
|        |                  |          |      |

这里解释下优先级与关键词的使用

现有三条**回复管理员@**设置

- 优先级1，关键词：在吗
- 优先级2，关键词：吃饭
- 优先级5，关键词未配置

当管理员@你时，并输入'在吗，吃饭了吗'

虽然同时命中配置1，配置2的关键词，但是由于配置1优先级高，所以会先判定，于是会根据配置1的话术ID进行回复



当管理员@你时，并输入'你是机器人吗'

未命中配置1，配置2的关键词，但是有配置3的存在，配置3中没有配置关键词，即**只要管理员@你，你就会对其进行回复**，是一个兜底措施



> 回复管理员非@

与**回复管理员@**一样，只是回复管理员的方式不一样，这里不做多赘述



##### 1.8聊天任务配置 - 昵称修改配置

![nickname-config](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/nickname-config.jpg)



|      参数      |         含义         | 是否为空 | 示例 |
| :------------: | :------------------: | :------: | :--: |
|    昵称集合    |    上传的昵称列表    |   非空   |      |
|    昵称后缀    | 改变昵称时的固定后缀 |   非空   |      |
| 触发改名发言数 |  发言n次后触发改名   |   非空   |      |

修改昵称需要在**1.1导入discord账户**中配置密码

改昵称是有限制的，改的太快会被系统拒绝，这边建议发言10-20分钟改名一次，根据你设置的发言间隔来定**触发改名发言次数**

比如 15分钟/1分钟 = 15 即，将触发改名发言数设置为15

当然，如果不需要修改昵称，则不可以进行配置，该项配置不是必须的，只是为了更好的避免被识别出来



##### 1.9聊天任务 - 其他配置

![other-config](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/other-config.jpg)

频道管理员 - 在监控消息时，无法判定发言的用户是否为管理员，需要在这里对任务进行配置，将管理员ID配置后，方可判定

通知配置 - 若任务暂停，用户被管理员@，登录过期等等场景出现，会发送通知到指定邮箱，建议配置



##### 1.9聊天任务 - 任务执行详情

![task-execute](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/task-execute.jpg)

这里可以看到任务的执行情况

状态分为

- 成功
- 失败
- 已删除

失败的任务会在备注中标明失败原因，诸如网络异常，频道慢模式发言，无权发言等等

其中网络异常是较为常见的，因为我们再任务中的每个用户都是使用全球独立IP，独立设备信息，保证不会触发风控；但是于此同时，并不能保证IP的可用性，所以会偶尔出现网络异常；不用担心，出现异常后我们会对发言进行更换IP重试



##### 1.10聊天任务 - 昵称修改记录

![nickname-update-record](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/nickname-update-record.jpg)

这里会展示对应任务，对应成员的昵称修改记录，包括成功与失败

方便用户查看各账号昵称情况



---

至此，自动聊天功能讲解完毕，如有疑问，可在群里留言

顺便多提一句，虽然上述配置较多，但也是为了大家能更好的拿到白名单，而不是进去10分钟就被踢了，发言频率不要太快，一次进去个15个号，这效果不比你冒着大风险10秒钟发言一次来的好嘛



#### 2.邀请任务

为配合聊天任务，当你账号变多时，每个账号一个个进群就是件比较麻烦的事情，所以我们开发了邀请任务

需要注意的是，使用邀请任务时，discord账号最好是双绑的，因为很多好的项目方的服务器进入会要求双绑号；同时双绑号使用起来安全程度是更好的

在测试过程中，我们的账号出现过被封禁的情况，因为我们在某个服务器频繁进出，触发风控，被判定为异常账号；所以使用该功能会出现一定风险，因而建议**主账号手动进入频道，因为主账号如果被封禁，损失比较大**

**我们承诺**，若是因为邀请功能被封禁的，经核实后，会赔一个同样绑定状态的账号（双绑号赔双绑号）

---

##### 2.1使用前准备 - 导入discord用户

这个步骤与聊天任务的导入discord用户相同，不做赘述



##### 2.2创建邀请任务

![invite-task](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/invite-task.jpg)



|   参数   |                 含义                 | 是否必填 |        示例        |
| :------: | :----------------------------------: | :------: | :----------------: |
| 任务名称 |             简单描述任务             |    是    |    xxx项目邀请     |
| 任务类型 |            邀请任务的类别            |    是    |     表情验证型     |
| 目标频道 |         需要去肝的聊天频道ID         |    是    | 907877461948243968 |
|  服务器  |        目标频道所在的服务器ID        |    是    | 907877461948241214 |
| 主邀请人 | 已经在频道内的主账号，用来生成邀请码 |    是    |                    |
| 验证频道 |           表情验证的频道ID           |    否    | 905382875183054859 |

**任务类型**详细说明

- 无验证邀请
- 同意协议型
- 表情验证型
- 同意协议后验证表情型

我们把目前的邀请种类分为如上4种，实际情况根据你要进去的服务器来看

验证频道 - 我们需要在该频道内点击对应表情后方可通过验证，若任务类型为表情验证、同意协议后验证表情，则该字段必填

同样的，任务创建完毕后，会先处于暂停状态，需要一些配置后方可运行（需手动开启）

##### 2.2生成邀请码

点击**生成邀请码**按钮，等待一会后刷新页面即出出现邀请码

需要注意的是，邀请码是根据主账号生成的，也就是说主账号必须在服务器内（手动进入），否则无法生成邀请码



##### 2.3表情点击配置

![emoji-config](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/emoji-config.jpg)

该配置用来指定点击表情的序号

系统有两种验证表情的方式

- 自动匹配
- 用户指定点击

> 自动匹配

![verify](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/verify.jpg)

系统会检测到该频道内验证机器人的消息，然后获取消息下方的表情

逐一与消息进行匹配，若消息中包含该表情，则会被列入点击范围

**但是** 有些项目方不太靠谱，如上图，需要点击的是一辆小黄车，从肉眼上看，是第一个，第十个表情符合，对吧？

如果从获取到的消息来对比，第一个虽然与第十个表情看上去一直，但是实际代码不一致，且第十个才是跟消息中的小黄车匹配的，所以，如果安装自动匹配的规则，第十个会被点击...

因而，我们加上了补充规则，整理后如下

- 表情列表中匹配消息中表情的，纳入待点击
- 表情列表中点击数量最多的，纳入待点击
- 若表情列表只有1个表情，纳入待点击



> 用户指定点击序号

上图中，真正要点击的是第一个表情，那么再**表情点击配置**中配置序号1，则表示需要点击第一个表情

若系统检测到表情点击配置的存在，则优先执行，不会去自动匹配

这种方式的好处是，因为主号是手动进入频道的，所以一定是通过了验证，那么就知道要点哪个验证，配置后系统执行的更快捷



##### 2.4配置邀请用户

![invite-user](https://fy-content-image.oss-cn-hangzhou.aliyuncs.com/invite-user.jpg)



该操作的含义是，将需要被邀请的用户配置进来，任务开始执行后，会将这些自动拉进频道并通过验证

配置完毕后，手动打开任务，等待一会便会自动执行

为防止触发风控，我们每个步骤执行会有一定延迟，被邀请用户的具体状态可以在这里查看，若用户的状态在10分钟内没有发生改变，可尝试点击**手动执行** 或者咨询一下负责人

---

邀请任务的讲解也基本结束，我们当前总结的4种邀请类型，并不一定涵盖了全部验证方式，包括邀请流程；再系统发布1周之后，discord做过一次隐式修改，所以在使用过程中如果有任何问题

若是有新的验证方式，我们会及时开发，涵盖这种方式

若是discord进行流程更新，我们也会对应修改我们的流程

争取给用户最好的体验



#### 3.一键抽奖

当前频道内抽奖越来越多，且都只需要点击一些表情即可参与

应用户要求，已列入开发规划，预计2月底完成上线，使用教程后续更新



#### 4.其他事项

首先感谢大家能耐心看完教程

俗话说的好，磨刀不误砍柴工，看明白了教程更有利于使用软件，对我们肝白也是有帮助的

如有新的功能需求，可以在issue里提出，我们这边评估后会安排开发



#### 5.常见问题

> 开着代理，浏览器访问不了平台

https://zhuanlan.zhihu.com/p/414533145

可以参考这篇文章，有可能是因为浏览器版本升级后，提升的安全策略引起的

> 现在接受邀请进服务器经常会出现验证是否为机器人的按钮，我们的工具能搞定吗

更新于2.20

经了解，进群前需要验证机器人是discord新增防机器人的手段

我们已完美解决可执行验证，尽可放心