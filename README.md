<p align="center" >
    <img src="https://www.xuxueli.com/doc/static/xxl-job/images/xxl-logo.jpg" width="150">
    <h3 align="center">XXL-JOB</h3>
    <p align="center">
        XXL-JOB, a distributed task scheduling framework.
        <br>
        <a href="https://www.xuxueli.com/xxl-job/"><strong>-- Home Page --</strong></a>
        <br>
        <br>
        <a href="https://github.com/xuxueli/xxl-job/actions">
            <img src="https://github.com/xuxueli/xxl-job/workflows/Java%20CI/badge.svg" >
        </a>
        <a href="https://maven-badges.herokuapp.com/maven-central/com.xuxueli/xxl-job/">
            <img src="https://maven-badges.herokuapp.com/maven-central/com.xuxueli/xxl-job/badge.svg" >
        </a>
        <a href="https://github.com/xuxueli/xxl-job/releases">
         <img src="https://img.shields.io/github/release/xuxueli/xxl-job.svg" >
        </a>
        <a href="https://github.com/xuxueli/xxl-job/">
            <img src="https://img.shields.io/github/stars/xuxueli/xxl-job" >
        </a>
        <a href="https://hub.docker.com/r/xuxueli/xxl-job-admin/">
            <img src="https://img.shields.io/docker/pulls/xuxueli/xxl-job-admin" >
        </a>
        <a href="http://www.gnu.org/licenses/gpl-3.0.html">
         <img src="https://img.shields.io/badge/license-GPLv3-blue.svg" >
        </a>
        <a href="https://www.xuxueli.com/page/donate.html">
           <img src="https://img.shields.io/badge/%24-donate-ff69b4.svg?style=flat" >
        </a>
    </p>
</p>


## Introduction
XXL-JOB is a distributed task scheduling framework. 
It's core design goal is to develop quickly and learn simple, lightweight, and easy to expand. 
Now, it's already open source, and many companies use it in production environments, real "out-of-the-box".

XXL-JOB是一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。


## Documentation
- [中文文档](https://www.xuxueli.com/xxl-job/)
- [English Documentation](https://www.xuxueli.com/xxl-job/en/)


## Communication    
- [社区交流](https://www.xuxueli.com/page/community.html)


## Features
- 1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；
- 2、动态：支持动态修改任务状态、启动/停止任务，以及终止运行中任务，即时生效；
- 3、调度中心HA（中心式）：调度采用中心式设计，“调度中心”自研调度组件并支持集群部署，可保证调度中心HA；
- 4、执行器HA（分布式）：任务分布式执行，任务"执行器"支持集群部署，可保证任务执行HA；
- 5、注册中心: 执行器会周期性自动注册任务, 调度中心将会自动发现注册的任务并触发执行。同时，也支持手动录入执行器地址；
- 6、弹性扩容缩容：一旦有新执行器机器上线或者下线，下次调度时将会重新分配任务；
- 7、路由策略：执行器集群部署时提供丰富的路由策略，包括：第一个、最后一个、轮询、随机、一致性HASH、最不经常使用、最近最久未使用、故障转移、忙碌转移等；
- 8、故障转移：任务路由策略选择"故障转移"情况下，如果执行器集群中某一台机器故障，将会自动Failover切换到一台正常的执行器发送调度请求。
- 9、阻塞处理策略：调度过于密集执行器来不及处理时的处理策略，策略包括：单机串行（默认）、丢弃后续调度、覆盖之前调度；
- 10、任务超时控制：支持自定义任务超时时间，任务运行超时将会主动中断任务；
- 11、任务失败重试：支持自定义任务失败重试次数，当任务失败时将会按照预设的失败重试次数主动进行重试；其中分片任务支持分片粒度的失败重试；
- 12、任务失败告警；默认提供邮件方式失败告警，同时预留扩展接口，可方便的扩展短信、钉钉等告警方式；
- 13、分片广播任务：执行器集群部署时，任务路由策略选择"分片广播"情况下，一次任务调度将会广播触发集群中所有执行器执行一次任务，可根据分片参数开发分片任务；
- 14、动态分片：分片广播任务以执行器为维度进行分片，支持动态扩容执行器集群从而动态增加分片数量，协同进行业务处理；在进行大数据量业务操作时可显著提升任务处理能力和速度。
- 15、事件触发：除了"Cron方式"和"任务依赖方式"触发任务执行之外，支持基于事件的触发任务方式。调度中心提供触发任务单次执行的API服务，可根据业务事件灵活触发。
- 16、任务进度监控：支持实时监控任务进度；
- 17、Rolling实时日志：支持在线查看调度结果，并且支持以Rolling方式实时查看执行器输出的完整的执行日志；
- 18、GLUE：提供Web IDE，支持在线开发任务逻辑代码，动态发布，实时编译生效，省略部署上线的过程。支持30个版本的历史版本回溯。
- 19、脚本任务：支持以GLUE模式开发和运行脚本任务，包括Shell、Python、NodeJS、PHP、PowerShell等类型脚本;
- 20、命令行任务：原生提供通用命令行任务Handler（Bean任务，"CommandJobHandler"）；业务方只需要提供命令行即可；
- 21、任务依赖：支持配置子任务依赖，当父任务执行结束且执行成功后将会主动触发一次子任务的执行, 多个子任务用逗号分隔；
- 22、一致性：“调度中心”通过DB锁保证集群分布式调度的一致性, 一次任务调度只会触发一次执行；
- 23、自定义任务参数：支持在线配置调度任务入参，即时生效；
- 24、调度线程池：调度系统多线程触发调度运行，确保调度精确执行，不被堵塞；
- 25、数据加密：调度中心和执行器之间的通讯进行数据加密，提升调度信息安全性；
- 26、邮件报警：任务失败时支持邮件报警，支持配置多邮件地址群发报警邮件；
- 27、推送maven中央仓库: 将会把最新稳定版推送到maven中央仓库, 方便用户接入和使用;
- 28、运行报表：支持实时查看运行数据，如任务数量、调度次数、执行器数量等；以及调度报表，如调度日期分布图，调度成功分布图等；
- 29、全异步：任务调度流程全异步化设计实现，如异步调度、异步运行、异步回调等，有效对密集调度进行流量削峰，理论上支持任意时长任务的运行；
- 30、跨语言：调度中心与执行器提供语言无关的 RESTful API 服务，第三方任意语言可据此对接调度中心或者实现执行器。除此之外，还提供了 “多任务模式”和“httpJobHandler”等其他跨语言方案；
- 31、国际化：调度中心支持国际化设置，提供中文、英文两种可选语言，默认为中文；
- 32、容器化：提供官方docker镜像，并实时更新推送dockerhub，进一步实现产品开箱即用；
- 33、线程池隔离：调度线程池进行隔离拆分，慢任务自动降级进入"Slow"线程池，避免耗尽调度线程，提高系统稳定性；
- 34、用户管理：支持在线管理系统用户，存在管理员、普通用户两种角色；
- 35、权限控制：执行器维度进行权限控制，管理员拥有全量权限，普通用户需要分配执行器权限后才允许相关操作；


## Development
于2015年中，我在github上创建XXL-JOB项目仓库并提交第一个commit，随之进行系统结构设计，UI选型，交互设计……

于2015-11月，XXL-JOB终于RELEASE了第一个大版本V1.0， 随后我将之发布到OSCHINA，XXL-JOB在OSCHINA上获得了@红薯的热门推荐，同期分别达到了OSCHINA的“热门动弹”排行第一和git.oschina的开源软件月热度排行第一，在此特别感谢红薯，感谢大家的关注和支持。

于2015-12月，我将XXL-JOB发表到我司内部知识库，并且得到内部同事认可。

于2016-01月，我司展开XXL-JOB的内部接入和定制工作，在此感谢袁某和尹某两位同事的贡献，同时也感谢内部其他给与关注与支持的同事。

于2017-05-13，在上海举办的 "[第62期开源中国源创会](https://www.oschina.net/event/2236961)" 的 "放码过来" 环节，我登台对XXL-JOB做了演讲，台下五百位在场观众反响热烈（[图文回顾](https://www.oschina.net/question/2686220_2242120) ）。

于2017-10-22，又拍云 Open Talk 联合 Spring Cloud 中国社区举办的 "[进击的微服务实战派上海站](https://opentalk.upyun.com/303.html)"，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。

于2017-12-11，XXL-JOB有幸参会《[InfoQ ArchSummit全球架构师峰会](http://bj2017.archsummit.com/)》，并被拍拍贷架构总监"杨波老师"在专题 "[微服务原理、基础架构和开源实践](http://bj2017.archsummit.com/training/2)" 中现场介绍。

于2017-12-18，XXL-JOB参与"[2017年度最受欢迎中国开源软件](http://www.oschina.net/project/top_cn_2017?sort=1)"评比，在当时已录入的约九千个国产开源项目中角逐，最终进入了前30强。

于2018-01-15，XXL-JOB参与"[2017码云最火开源项目](https://www.oschina.net/news/92438/2017-mayun-top-50)"评比，在当时已录入的约六千五百个码云项目中角逐，最终进去了前20强。

于2018-04-14，iTechPlus在上海举办的 "[2018互联网开发者大会](http://www.itdks.com/eventlist/detail/2065)"，我登台对XXL-JOB做了演讲，现场观众反响热烈并在会后与XXL-JOB用户热烈讨论交流。

于2018-05-27，在上海举办的 "[第75期开源中国源创会](https://www.oschina.net/event/2278742)" 的 "架构" 主题专场，我登台进行“基础架构与中间件图谱”主题演讲，台下上千位在场观众反响热烈（[图文回顾](https://www.oschina.net/question/3802184_2280606) ）。

于2018-12-05，XXL-JOB参与"[2018年度最受欢迎中国开源软件](https://www.oschina.net/project/top_cn_2018?sort=1)"评比，在当时已录入的一万多个开源项目中角逐，最终排名第19名。

于2019-12-10，XXL-JOB参与"[2019年度最受欢迎中国开源软件](https://www.oschina.net/project/top_cn_2019)"评比，在当时已录入的一万多个开源项目中角逐，最终排名"开发框架和基础组件类"第9名。

> 我司大众点评目前已接入XXL-JOB，内部别名《Ferrari》（Ferrari基于XXL-JOB的V1.1版本定制而成，新接入应用推荐升级最新版本）。
据最新统计, 自2016-01-21接入至2017-12-01期间，该系统已调度约100万次，表现优异。新接入应用推荐使用最新版本，因为经过数十个版本的更新，系统的任务模型、UI交互模型以及底层调度通讯模型都有了较大的优化和提升，核心功能更加稳定高效。

至今，XXL-JOB已接入多家公司的线上产品线，接入场景如电商业务，O2O业务和大数据作业等，截止最新统计时间为止，XXL-JOB已接入的公司包括不限于：
    
	- 1、大众点评【美团点评】
	- 2、山东学而网络科技有限公司；
	- 3、安徽慧通互联科技有限公司；
	- 4、人人聚财金服；
	- 5、上海棠棣信息科技股份有限公司
	- 6、运满满【运满满】
	- 7、米其林 (中国区)【米其林】
	- 8、妈妈联盟
	- 9、九樱天下（北京）信息技术有限公司
	- 10、万普拉斯科技有限公司【一加手机】
	- 11、上海亿保健康管理有限公司
	- 12、海尔馨厨【海尔】
	- 13、河南大红包电子商务有限公司
	- 14、成都顺点科技有限公司
	- 15、深圳市怡亚通
	- 16、深圳麦亚信科技股份有限公司
	- 17、上海博莹科技信息技术有限公司
	- 18、中国平安科技有限公司【中国平安】
	- 19、杭州知时信息科技有限公司
	- 20、博莹科技（上海）有限公司
	- 21、成都依能股份有限责任公司
	- 22、湖南高阳通联信息技术有限公司
	- 23、深圳市邦德文化发展有限公司
	- 24、福建阿思可网络教育有限公司
	- 25、优信二手车【优信】
	- 26、上海悠游堂投资发展股份有限公司【悠游堂】
	- 27、北京粉笔蓝天科技有限公司
	- 28、中秀科技(无锡)有限公司
	- 29、武汉空心科技有限公司
	- 30、北京蚂蚁风暴科技有限公司
	- 31、四川互宜达科技有限公司
	- 32、钱包行云（北京）科技有限公司
	- 33、重庆欣才集团
    - 34、咪咕互动娱乐有限公司【中国移动】
    - 35、北京诺亦腾科技有限公司
    - 36、增长引擎(北京)信息技术有限公司
    - 37、北京英贝思科技有限公司
    - 38、刚泰集团
    - 39、深圳泰久信息系统股份有限公司
    - 40、随行付支付有限公司
    - 41、广州瀚农网络科技有限公司
    - 42、享点科技有限公司
    - 43、杭州比智科技有限公司
    - 44、圳临界线网络科技有限公司
    - 45、广州知识圈网络科技有限公司
    - 46、国誉商业上海有限公司
    - 47、海尔消费金融有限公司，嗨付、够花【海尔】
    - 48、广州巴图鲁信息科技有限公司
    - 49、深圳市鹏海运电子数据交换有限公司
    - 50、深圳市亚飞电子商务有限公司
    - 51、上海趣医网络有限公司
    - 52、聚金资本
    - 53、北京父母邦网络科技有限公司
    - 54、中山元赫软件科技有限公司
    - 55、中商惠民(北京)电子商务有限公司
    - 56、凯京集团
    - 57、华夏票联（北京）科技有限公司
    - 58、拍拍贷【拍拍贷】
    - 59、北京尚德机构在线教育有限公司
    - 60、任子行股份有限公司
    - 61、北京时态电子商务有限公司
    - 62、深圳卷皮网络科技有限公司
    - 63、北京安博通科技股份有限公司
    - 64、未来无线网
    - 65、厦门瓷禧网络有限公司
    - 66、北京递蓝科软件股份有限公司
    - 67、郑州创海软件科技公司
    - 68、北京国槐信息科技有限公司
    - 69、浪潮软件集团
    - 70、多立恒(北京)信息技术有限公司
    - 71、广州极迅客信息科技有限公司
    - 72、赫基（中国）集团股份有限公司
    - 73、海投汇
    - 74、上海润益创业孵化器管理股份有限公司
    - 75、汉纳森（厦门）数据股份有限公司
    - 76、安信信托
    - 77、岚儒财富
    - 78、捷道软件
    - 79、湖北享七网络科技有限公司
    - 80、湖南创发科技责任有限公司
    - 81、深圳小安时代互联网金融服务有限公司
    - 82、湖北享七网络科技有限公司
    - 83、钱包行云(北京)科技有限公司
    - 84、360金融【360】
    - 85、易企秀
    - 86、摩贝（上海）生物科技有限公司
    - 87、广东芯智慧科技有限公司
    - 88、联想集团【联想】
    - 89、怪兽充电
    - 90、行圆汽车
    - 91、深圳店店通科技邮箱公司
    - 92、京东【京东】
    - 93、米庄理财
    - 94、咖啡易融
    - 95、梧桐诚选
    - 96、恒大地产【恒大】
    - 97、昆明龙慧
    - 98、上海涩瑶软件
    - 99、易信【网易】
    - 100、铜板街
    - 101、杭州云若网络科技有限公司
    - 102、特百惠（中国）有限公司
    - 103、常山众卡运力供应链管理有限公司
    - 104、深圳立创电子商务有限公司
    - 105、杭州智诺科技股份有限公司
    - 106、北京云漾信息科技有限公司
    - 107、深圳市多银科技有限公司
    - 108、亲宝宝
    - 109、上海博卡软件科技有限公司
    - 110、智慧树在线教育平台
    - 111、米族金融
    - 112、北京辰森世纪
    - 113、云南滇医通
    - 114、广州市分领网络科技有限责任公司
    - 115、浙江微能科技有限公司
    - 116、上海馨飞电子商务有限公司
    - 117、上海宝尊电子商务有限公司
    - 118、直客通科技技术有限公司
    - 119、科度科技有限公司
    - 120、上海数慧系统技术有限公司
    - 121、我的医药网
    - 122、多粉平台
    - 123、铁甲二手机
    - 124、上海海新得数据技术有限公司
    - 125、深圳市珍爱网信息技术有限公司【珍爱网】
    - 126、小蜜蜂
    - 127、吉荣数科技
    - 128、上海恺域信息科技有限公司
    - 129、广州荔支网络有限公司【荔枝FM】
    - 130、杭州闪宝科技有限公司
    - 131、北京互联新网科技发展有限公司
    - 132、誉道科技
    - 133、山西兆盛房地产开发有限公司
    - 134、北京蓝睿通达科技有限公司
    - 135、月亮小屋（中国）有限公司【蓝月亮】
    - 136、青岛国瑞信息技术有限公司
    - 137、博雅云计算（北京）有限公司
    - 138、华泰证券香港子公司
    - 139、杭州东方通信软件技术有限公司
    - 140、武汉博晟安全技术股份有限公司
    - 141、深圳市六度人和科技有限公司
    - 142、杭州趣维科技有限公司（小影）
    - 143、宁波单车侠之家科技有限公司【单车侠】
    - 144、丁丁云康信息科技（北京）有限公司
    - 145、云钱袋
    - 146、南京中兴力维
    - 147、上海矽昌通信技术有限公司
    - 148、深圳萨科科技
    - 149、中通服创立科技有限责任公司
    - 150、深圳市对庄科技有限公司
    - 151、上证所信息网络有限公司
    - 152、杭州火烧云科技有限公司【婚礼纪】
    - 153、天津青芒果科技有限公司【芒果头条】
    - 154、长飞光纤光缆股份有限公司
    - 155、世纪凯歌（北京）医疗科技有限公司
    - 156、浙江霖梓控股有限公司
    - 157、江西腾飞网络技术有限公司
    - 158、安迅物流有限公司
    - 159、肉联网
    - 160、北京北广梯影广告传媒有限公司
    - 161、上海数慧系统技术有限公司
    - 162、大志天成
    - 163、上海云鹊医
    - 164、上海云鹊医
    - 165、墨迹天气【墨迹天气】
    - 166、上海逸橙信息科技有限公司
    - 167、沅朋物联
    - 168、杭州恒生云融网络科技有限公司
    - 169、绿米联创
    - 170、重庆易宠科技有限公司
    - 171、安徽引航科技有限公司（乐职网）
    - 172、上海数联医信企业发展有限公司
    - 173、良彬建材
    - 174、杭州求是同创网络科技有限公司
    - 175、荷马国际
    - 176、点雇网
    - 177、深圳市华星光电技术有限公司
    - 178、厦门神州鹰软件科技有限公司
    - 179、深圳市招商信诺人寿保险有限公司
    - 180、上海好屋网信息技术有限公司
    - 181、海信集团【海信】
    - 182、信凌可信息科技（上海）有限公司
    - 183、长春天成科技发展有限公司
    - 184、用友金融信息技术股份有限公司【用友】
    - 185、北京咖啡易融有限公司
    - 186、国投瑞银基金管理有限公司
    - 187、晋松(上海)网络信息技术有限公司
    - 188、深圳市随手科技有限公司【随手记】
    - 189、深圳水务科技有限公司
    - 190、易企秀【易企秀】
    - 191、北京磁云科技
    - 192、南京蜂泰互联网科技有限公司
    - 193、章鱼直播
    - 194、奖多多科技
    - 195、天津市神州商龙科技股份有限公司
    - 196、岩心科技
    - 197、车码科技（北京）有限公司
    - 198、贵阳市投资控股集团
    - 199、康旗股份
    - 200、龙腾出行
    - 201、杭州华量软件
    - 202、合肥顶岭医疗科技有限公司
    - 203、重庆表达式科技有限公司
    - 204、上海米道信息科技有限公司
    - 205、北京益友会科技有限公司
    - 206、北京融贯电子商务有限公司
    - 207、中国外汇交易中心
    - 208、中国外运股份有限公司
    - 209、中国上海晓圈教育科技有限公司
    - 210、普联软件股份有限公司
    - 211、北京科蓝软件股份有限公司
    - 212、江苏斯诺物联科技有限公司
    - 213、北京搜狐-狐友【搜狐】
    - 214、新大陆网商金融
    - 215、山东神码中税信息科技有限公司
    - 216、河南汇顺网络科技有限公司
    - 217、北京华夏思源科技发展有限公司
    - 218、上海东普信息科技有限公司
    - 219、上海鸣勃网络科技有限公司
    - 220、广东学苑教育发展有限公司
    - 221、深圳强时科技有限公司
    - 222、上海云砺信息科技有限公司
    - 223、重庆愉客行网络有限公司
    - 224、数云
    - 225、国家电网运检部
    - 226、杭州找趣
    - 227、浩鲸云计算科技股份有限公司
    - 228、科大讯飞【科大讯飞】
    - 229、杭州行装网络科技有限公司
    - 230、即有分期金融
    - 231、深圳法司德信息科技有限公司
    - 232、上海博复信息科技有限公司
    - 233、杭州云嘉云计算有限公司
    - 234、有家民宿(有家美宿)
    - 235、北京赢销通软件技术有限公司
    - 236、浙江聚有财金融服务外包有限公司
    - 237、易族智汇(北京)科技有限公司
    - 238、合肥顶岭医疗科技开发有限公司
    - 239、车船宝(深圳)旭珩科技有限公司)
    - 240、广州富力地产有限公司
    - 241、氢课（上海）教育科技有限公司
    - 242、武汉氪细胞网络技术有限公司
    - 243、杭州有云科技有限公司
    - 244、上海仙豆智能机器人有限公司
    - 245、拉卡拉支付股份有限公司【拉卡拉】
    - 246、虎彩印艺股份有限公司
    - 247、北京数微科技有限公司
    - 248、广东智瑞科技有限公司
    - 249、找钢网
    - 250、九机网
    - 251、杭州跑跑网络科技有限公司
    - 252、深圳未来云集
    - 253、杭州每日给力科技有限公司
    - 254、上海齐犇信息科技有限公司
    - 255、滴滴出行【滴滴】
    - 256、合肥云诊信息科技有限公司
    - 257、云知声智能科技股份有限公司
    - 258、南京坦道科技有限公司
    - 259、爱乐优（二手平台）
    - 260、猫眼电影（私有化部署）【猫眼电影】
    - 261、美团大象（私有化部署）【美团大象】
    - 262、作业帮教育科技（北京）有限公司【作业帮】
    - 263、北京小年糕互联网技术有限公司
    - 264、山东矩阵软件工程股份有限公司
    - 265、陕西国驿软件科技有限公司
    - 266、君开信息科技
    - 267、村鸟网络科技有限责任公司
    - 268、云南国际信托有限公司
    - 269、金智教育
    - 270、珠海市筑巢科技有限公司
    - 271、上海百胜软件股份有限公司
    - 272、深圳市科盾科技有限公司
    - 273、哈啰出行【哈啰】
    - 274、途虎养车【途虎】
    - 275、卡思优派人力资源集团
    - 276、南京观为智慧软件科技有限公司
    - 277、杭州城市大脑科技有限公司
    - 278、猿辅导【猿辅导】
    - 279、洛阳健创网络科技有限公司
    - 280、魔力耳朵
    - 281、亿阳信通
    - 282、上海招鲤科技有限公司
    - 283、四川商旅无忧科技服务有限公司
    - 284、UU跑腿
    - 285、北京老虎证券【老虎证券】
    - 286、悠活省吧（北京）网络科技有限公司
    - 287、F5未来商店
    - 288、深圳环阳通信息技术有限公司
    - 289、遠傳電信
    - 290、作业帮（北京）教育科技有限公司【作业帮】
    - 291、成都科鸿智信科技有限公司
    - 292、北京木屋时代科技有限公司
    - 293、大学通（哈尔滨）科技有限责任公司
    - 294、浙江华坤道威数据科技有限公司
    - 295、吉祥航空【吉祥航空】
    - 296、南京圆周网络科技有限公司
    - 297、广州市洋葱omall电子商务
    - 298、天津联物科技有限公司
    - 299、跑哪儿科技（北京）有限公司
    - 300、深圳市美西西餐饮有限公司(喜茶)
    - 301、平安不动产有限公司【平安】
    - 302、江苏中海昇物联科技有限公司
    - 303、湖南牙医帮科技有限公司
    - 304、重庆民航凯亚信息技术有限公司（易通航）
    - 305、递易（上海）智能科技有限公司
    - 306、亚朵
    - 307、浙江新课堂教育股份有限公司
    - 308、北京蜂创科技有限公司
    - 309、德一智慧城市信息系统有限公司
    - 310、北京翼点科技有限公司
    - 311、湖南智数新维度信息科技有限公司
    - 312、北京玖扬博文文化发展有限公司
    - 313、上海宇珩信息科技有限公司
    - 314、全景智联（武汉）科技有限公司
    - 315、天津易客满国际物流有限公司
    - 316、南京爱福路汽车科技有限公司
    - 317、我房旅居集团
    - 318、湛江亲邻科技有限公司
    - 319、深圳市姜科网络有限公司
    - 320、青岛日日顺物流有限公司
    - 321、南京太川信息技术有限公司
    - 322、美图之家科技优先公司【美图】
    - 323、南京太川信息技术有限公司
    - 324、众薪科技（北京）有限公司
	- ……

> 更多接入的公司，欢迎在 [登记地址](https://github.com/xuxueli/xxl-job/issues/1 ) 登记，登记仅仅为了产品推广。

欢迎大家的关注和使用，XXL-JOB也将拥抱变化，持续发展。


## Contributing
Contributions are welcome! Open a pull request to fix a bug, or open an [Issue](https://github.com/xuxueli/xxl-job/issues/) to discuss a new feature or change.

欢迎参与项目贡献！比如提交PR修复一个bug，或者新建 [Issue](https://github.com/xuxueli/xxl-job/issues/) 讨论新特性或者变更。


## Copyright and License
This product is open source and free, and will continue to provide free community technical support. Individual or enterprise users are free to access and use.

- Licensed under the GNU General Public License (GPL) v3.
- Copyright (c) 2015-present, xuxueli.

产品开源免费，并且将持续提供免费的社区技术支持。个人或企业内部可自由的接入和使用。


## Donate
No matter how much the donation amount is enough to express your thought, thank you very much ：）     [To donate](https://www.xuxueli.com/page/donate.html )

无论捐赠金额多少都足够表达您这份心意，非常感谢 ：）      [前往捐赠](https://www.xuxueli.com/page/donate.html )
#   x x l - j o b - o r a c l e  
 