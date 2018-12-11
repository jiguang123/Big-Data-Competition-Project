## Facebook广告投放策略数据分析项目实践
本项目数据来自于Kaggle上的一个Facebook广告投放策略数据，项目主页地址：
[Sales Conversion Optimization](https://www.kaggle.com/loveall/clicks-conversion-tracking/home)

项目使用的数据来自一个匿名组织的社交媒体广告活动,数据文件包含11个属性(列)，1143个观察值（行），下面是属性的描述：

1. ad_id: an unique ID for each ad.

>>即每个广告的唯一标识

2. xyz_campaign_id: an ID associated with each ad campaign of XYZ company.

>>即xyz公司的每次广告活动的唯一标识

3. fb_campaign_id: an ID associated with how Facebook tracks each campaign.

>>即facebook用来跟踪每次广告活动的唯一标识

4. age: age of the person to whom the ad is shown.

>>即广告展示对象的年龄

5. gender: gender of the person to whim the add is shown

>>即广告展示对象的性别

6. interest: a code specifying the category to which the person’s interest belongs (interests are as mentioned in the person’s Facebook public profile).

>>即facebook用户的兴趣标签，也就是facebook用户的个人主页所显示的兴趣标签。

7. Impressions: the number of times the ad was shown.

>>即广告曝光次数。

8. Clicks: number of clicks on for that ad.

>>即广告点击次数。

9. Spent: Amount paid by company xyz to Facebook, to show that ad.

>>即xyz公司为每次广告展示向facebook支付的费用。

10. Total conversion: Total number of people who enquired about the product after seeing the ad.

>>即用户看到广告之后向xyz公司咨询产品的次数。

11. Approved conversion: Total number of people who bought the product after seeing the ad.

>>即用户看到广告之后购买产品的次数。


---

社交媒体广告活动营销是销售转换的一个主要来源, 本次分析聚焦两个问题：

- 兴趣标签（interest code）取值为多少的人点击率最高？

- 哪个群体的转化率最高？

由于本次项目数据集不大，且数据质量很高，无需进行缺失值、异常值处理，故直接将其导入MySQL进行分析，本人使用的数据库软件是Mysql For Navicat Premium，分析内容分为两个部分：数据统计和投放效果分析。

---

### 一、数据统计

1、将数据集导入Mysql数据库，结果如下：
![1](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/yrapkc5xIrnCnqICQ4UqqhtSGpdN8WCYvbsAVlw0C0s!/b/dLYAAAAAAAAA&bo=wQOdAgAAAAARB20!&rf=viewer_4)



2、查看有多少个广告活得(compaign):
![2](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/*R9gxsbLPHOh3dt96uEiAsH37JCzRuLBRCUka9Vydgk!/b/dFIBAAAAAAAA&bo=.AIPAgAAAAARB8c!&rf=viewer_4)



3、计算每个广告活动（campaign）包含了多少个广告，按降序排列
![3](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/jDH*5itbngY5oBRbwT3PCBi8C5mK3oJLOF6gQaZ2PrU!/b/dAgBAAAAAAAA&bo=9gIOAgAAAAARB8g!&rf=viewer_4)



4、计算每个广告活动的总花费，按降序排列

![4](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/M5XckK*3KWyH5hB3dOSQTT.SWe36ecxX.rEH2EoUSvo!/b/dDYBAAAAAAAA&bo=9gIMAgAAAAARF9o!&rf=viewer_4)



5、以百分数形式显示xyz_campaign_id=916广告活动中每个广告的点击率CTR，并按降序排列，CTR=clicks/impressions
![5](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/GU8MN2N.wVmceRiE2L1VI*5SDT2baRQY4fR2*C*du5o!/b/dLYAAAAAAAAA&bo=.QIIAgAAAAARB8E!&rf=viewer_4)



6、以百分数形式显示xyz_campaign_id=916广告活动中每个广告的转化率CVR，并按降序排列，CVR= total_conversion/clicks
![6](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/h.z1qP1msT42MG8i2tTe0IRaIpWGRhwRKOmjVKZe6FM!/b/dLYAAAAAAAAA&bo=9QIQAgAAAAARF8U!&rf=viewer_4)

---

### 二、投放效果分析

1、 interest值为多少的人点击率最高？分别对3个不同的广告活动进行分析。

- 对于xyz_campaign_id=916, interest=21的人点击率最高，分析过程如下：
![7](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/2wogMG2q3rVRnLXy3WHUu2hwk7xgWQfrTVtsJHD164g!/b/dDEBAAAAAAAA&bo=9gIRAgAAAAARB9c!&rf=viewer_4)


- 对于xyz_campaign_id=936，interest=2的人点击率最高，分析过程同上，只需要将where语句中xyz_campain_code=916改为xyz_campain_code=936
![8](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/.B8FlbcfcpVnUsRixsu1Doizi3DYa.dcP4OmwOI4Y.A!/b/dLYAAAAAAAAA&bo=.AIMAgAAAAARF9Q!&rf=viewer_4)


- 同理，对于xyz_campain_code=1178，分析可得interest=26的人点击率最高。
![9](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/PycCiOj08nV.XghHE.nD2xaN5aQ5BDoasNPyxLmHhQw!/b/dLYAAAAAAAAA&bo=9QIQAgAAAAARF8U!&rf=viewer_4)

---

2.男性还是女性更有可能完成转化？分别对3个不同的广告活动进行分析。

- 对于xyz_campaign_code=916，男性更容易完成转化，分析过程如下：
![](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/Tlwowojpj7kO6Z*n71Y6drcXxbA1Ry*9tZtFgZCtJNg!/b/dDIBAAAAAAAA&bo=KAMUAgAAAAARBw0!&rf=viewer_4)



- 对于xyz_campaign_code=936，男性更容易完成转化，分析过程同上，只需要将where语句中xyz_campain_code=916改为xyz_campain_code=936
![](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/oWmXZY9NtZpLY.yRog.*vj068oDSz26hn3I6UT6FWY0!/b/dDUBAAAAAAAA&bo=KgMNAgAAAAARFwY!&rf=viewer_4)


- 同理，对于xyz_campain_code=1178，分析可得男性更容易完成转化。
![](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/oh2ZDQ3Tg.825WATCENsKiE4uz6Nf8jmYpS8.Q7UIZg!/b/dDQBAAAAAAAA&bo=JgMTAgAAAAARFxQ!&rf=viewer_4)


---

3、 进一步分析，哪个年龄段的男性转化率最高？分别对3个不同的广告活动进行分析。

- 对于xyz_campaign_code=916，30-34岁的男性转化率最高，分析过程如下：
![13](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/38i201zy*CssGbxNwsRAIi0rQaFrxxTCoUqlL3QWl4A!/b/dEYBAAAAAAAA&bo=8gIMAgAAAAARB84!&rf=viewer_4)



- 对于xyz_campaign_code=916，30-34岁的男性转化率最高，分析过程同上，只需要将where语句中xyz_campain_code=916改为xyz_campain_code=936。

![14](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/wDxsWB8TJupNTw2pTwiqGEdNjOr1onvt7Xp9q2pYHXQ!/b/dFQBAAAAAAAA&bo=9AISAgAAAAARF8Y!&rf=viewer_4)



- 同理，对于xyz_campain_code=1178，分析可得30-34岁的男性更容易完成转化。

![15](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/RaUtjKtPDa8O3G8YT6ywuHYhhIHUHFWydIfqWv*txF8!/b/dDEBAAAAAAAA&bo=9gIMAgAAAAAKF8E!&rf=viewer_4)



4、 通过前两项分析可以看出30-34岁男性是转化率最高的群体，那么该群体的点击率如何呢？

![16](http://m.qpic.cn/psb?/V10P3PxC0koPqQ/h09yipMdBbh97UBFg*q25Jq0LVDAzNSpGPimlR156y0!/b/dDYBAAAAAAAA&bo=JwMRAgAAAAARBwc!&rf=viewer_4)



由上图可知，30-34岁的男性虽然转化率很高，但是点击率并不高。这说明如果我们可以想办法提高这个群体的点击率的话，就能提高转化。比如针对这个群体设计更吸引他们的广告。






