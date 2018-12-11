# 手把手教你学NB-IoT物联网开发之-影子设备开发

## 写在前面的话

物联网从本质上来讲，是一个将虚拟世界与物理世界联通的虚实结合的工具。这里的虚当然就是指虚拟的网络空间，实则指的是真实的物理设备。连接虚拟与真实则成了物联网领域开发的基础。而这里最基础的基础，则是将真实设备与虚拟设备映射起来。在这里，我们将这个虚拟设备称作**影子设备**。

**本教程将描述如何进行NB-IoT影子设备的开发**，在华为IoT平台的开发模型中，NB-IoT的影子设备由两部分组成：

- profile文件 - 主要用于定义设备模型，主要包括设备的属性定义及能力定义；
- 编解码插件 - 主要用于低带宽模式下，非格式化数据流的数据封装及解析工作；

## 第一章 基础上下行消息

目前上线的IoT平台开发者portal支持如下功能：

- 在线开发profile（即设备建模）；
- 在线开发编解码插件；
- 模拟应用管理设备；
- 模拟设备上报数据接收命令；
- 支持离线开发的profile和插件的上传部署；

**以上功能除了编解码插件相关功能只支持NB-IoT场景，其他功能通用（NB-IoT、智慧家庭、车联网等）**

### 场景说明

假设有一款烟感设备（NB设备）具备如下功能：

- 烟雾报警功能；
- 温度上报功能；
- 支持远程控制命令（远程打开报警功能，比如某大楼某房间着火，可以根据火势及火灾现场温度远程打开其他房间的烟雾报警，提醒住户疏散）

### Profile与编解码插件开发

1）创建产品

登录开发者portal，进入Profile开发->Profile在线开发->自定义产品->创建全新产品

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/182401yy933f8bg88r0sf8.png)

2）增加属性字段及命令字段

为新建产品增加属性字段及命令字段

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/094807rmsqnuhph2nhncqv.png)
这样，profile就开发完毕了。如果有保存按钮，记得点保存哦~

3）选择对应profile

登录开发者portal，进入插件开发->插件开发->添加插件->新建插件->选择对应的profile->点击确定。
可以在右边看到profile的内容：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191216jie5rzx8i8i80hbm.png)

4）新增消息：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191217tosqh8qvmquuhzv5.png)

5）添加一条数据上报消息：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191217zk0rbjqjkd8bdd1g.png)

6）为消息添加字段：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191217t7jeb9lzz7jzfew9.png)

7）新增上报消息字段一：

添加第一个字段，便是火险等级（需要一个字节）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/214215vca3ukyijld3waj5.png)

8）新增上报消息字段二：

添加第二个字段，表示温度（需要2个字节）：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/214220hnij898ju8n4ni5z.png)

9）映射编解码插件与profile

把右边profile的**属性一一**拖曳过来与字段关联起来：**请务必仔细看图**
![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191219gg17pao0pii7pbdo.png)

10）新增命令消息

首先，点击左侧边上的新增消息按钮：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191230qpp8pbiiqmm6fpni.png)

然后，添加一条命令下发消息：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191231de2clzddsii1eusa.png)

12）新增下发命令消息字段

同样为命令下发消息添加字段，添加一个value字段，表示告警的开关：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191231my3prin23thpnhez.png)

13）映射编解码插件与profile

把右边profile的**命令字段一一**拖曳过来与字段关联起来：

**请务必仔细看图**

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191231j902wwjmnj9kyxkb.png)

14）保存并部署编解码插件

这样插件编写好了，点击右上边的部署按钮：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191232h3f5fje0i3ffuuv0.png)

15）等待部署成功：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191232g9nk8tkuks292bg9.png)

### 使用模拟器调测

1）注册设备

先进入我的设备->注册设备->选择对应的profile，填写设备名称和验证码，注册设备：
![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191233syywhkyhzbhhzwgh.png)

2）绑定设备

再到模拟器->NB设备模拟器->绑定设备：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191233rt8212n8r2oyytn8.png)

3）模拟上报数据

上报业务码流：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191233x4rvif56fj7vvb7l.png)

4）查看数据

到我的设备->点击具体设备进入设备详情->切到历史数据页签：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191242vnbf055nhlh5mg6d.png)

5）模拟下发命令

**注意**：使用模拟器测试，请在下发命令前先上报一条数据，然后再马上下发命令。
在我的设备列表点击对应设备的命令下发按钮，填写参数值，点击发送：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191242xmc0lwxm7mke1lem.png)

6）查看历史命令

到我的设备->点击具体设备进入设备详情->切到历史命令页签：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/24/191242fu2220qf22866qqv.png)
这样，使用模拟器的调测完成了，平台的业务已调通。

## 第二章 多条上下行消息

### 场景说明

- 假设一：有一款烟感设备（NB设备），具有烟雾报警功能和温度上报功能，也支持远程控制命令（远程打开报警功能，比如某大楼某房间着火，可以根据火势及火灾现场温度远程打开其他房间的烟雾报警，提醒住户疏散）
- 假设二：烟感设备可以同时上报烟雾报警和温度，也能单独上报温度（如温度每增加20度上报一次等）

### Profile与插件开发

**前文描述profile保持不变**

见下图： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/144429xmovw0vvvzs0wlvv.png)   

1）添加第一条上报消息，上报报警和温度（前面的基本操作步骤已省略）：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/144505x7ann7jonl22ox4a.png)



2）添加messageId（**由于上行消息有两种，所以得用messageId来标志是哪种消息，这是在线开发插件的规定，看图中文字说明**）: 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/145441alvfrfpbove8s65p.png)

3）添加level属性字段：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/145442emirr98o8s94o7rd.png)

4）添加temerature属性字段：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/163032az2w5ilwqzwiwuel.png)

5）关联属性：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/145444tn7p72y288j4ggvd.png)

6）添加第二条上报消息（单独上报温度）：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/153035t282784szoz656d6.png) 7）添加messageId:

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/153040b9xl3385ul9ewlot.png)

8）添加temperature属性：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/163032az2w5ilwqzwiwuel.png)

9）关联字段：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/160441lneh1fws1zvwbnej.png)  

10）命令下发：

与之前保持一致，由于下行消息只有一条，不需要使用messageId区分（如果有两条或两条以上的下行消息，则要加上messageId）：

 ![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/160543r4oisc08sniv8jil.png)  

### 使用模拟器调测

**部署插件、添加设备、绑定等步骤与前文类似，已省略。**

具体调测步骤如下：

1）根据业务场景上报数据**（messagId的值必须与默认值一致，所以是固定值）**：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/162347je1817kp1jj8v7st.png)

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/162347x0oxhewjoq0bvvqw.png)

2）查看设备历史数据：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201803/26/162348x76w3r65673w0vv5.png)

## 第三章 字符串 及 可变长度字符串

### 数据上报Profile和插件开发

1）添加一个string类型的属性：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134432mpff2b973q2pqooq.png)

2）在插件里添加一条数据上报消息：（已添加一个messageId，值为0x02）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134432k6urq9qljblc4l7j.png)

3）再添加一个固定长度的字符串型字段，长度为**6个字节**：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134433hngj9bpm9pngnmsb.png)

4）与profile里的属性关联起来： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134433rtgj8hjgghqwqgmn.png)

5）再添加一条数据上报消息：（**已添加一个messageId，值为0x03**） 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134935xyv82eywk55b4385.png)

6）再添加一个长度字段： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134434k4i3c1pa3b8f535z.png)

7）添加一个可变长度字符串，并关联长字段： 

![](https://forum-img.huaweicloud.com/data/attachment/forum/201812/11/095430qtb2vzlzqbpqsvbs.png)

8）与profile里的属性关联起来： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/135701mw0uzpfsmwlnf0wn.png)

9）最后部署插件即可。  

### 使用模拟器调测数据上报

1）注册一个新设备： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134434ezw8wcnvlv8bujbj.png)

2）使用NB设备模拟器，绑定后上报数据：此处上报了4条数据，都是02开头的码流 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134435jnvzbrwpgr55v0rt.png)

3）查看设备历史数据：上报数据时，string字段使用ascii码进行解码（见本帖最后的总结）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134435wyu4au5fauqu7i87.png)

4）再上报03开头的码流： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134436vru680awhwz1rra8.png)

5）查看设备历史数据： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134436y3fpxgppn5knp3gn.png)

### 总结

 1）字符串类型的数据是按Ascii码进行编解码的，上报时将16进制码流转为对应字符（如21转为叹号!，31转为1，41转为A）；下发命令时则反过来，把字符转为对应的16进制码流（如叹号！转为21，1转为31，A转为41）；

 2）可变长度字符串要关联长度字段，长度字段必须为int型；

 3）命令下发直接使用固定长度的字符串即可，下发的长度以实际下发数据为准；

 4）[ASCII码表](https://baike.baidu.com/item/ASCII/309296?fr=aladdin)直接百度即可找到，使用**16进制的标准表**，不在标准表里的无法编解码。解码时（数据上报）**如果解析出来的字符无法使用具体字符表示**，如标题开始、正文开始、正文结束等，则使用\u+2字节码流值表示（例如01转为\u0001，02转为\u0002）；有具体字符的则使用具体字符，详见本总结第1条。 

附上部分ASCII码表： 

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/19/144430ttncu55ygwyzont5.png)

## 第四章 数组 及 可变长度数组

### 数据上报Profile和插件开发

1）添加一个string类型的属性： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134432mpff2b973q2pqooq.png)

2）在插件里添加一条数据上报消息：（已添加一个messageId，值为0x02） 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134432k6urq9qljblc4l7j.png)

3）再添加一个固定长度的数组型字段，长度为5个字节： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/152621rdpydyhobpomupu0.png)

4）与profile里的属性关联起来： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134433rtgj8hjgghqwqgmn.png)

5）再添加一条数据上报消息：（已添加一个messageId，值为0x03） 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134935xyv82eywk55b4385.png)

6）再添加一个长度字段： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134434k4i3c1pa3b8f535z.png)

7）添加一个可变长度数组，并关联长字段： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/152622cw30bykesys3re3x.png)

8）与profile里的属性关联起来： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/135701mw0uzpfsmwlnf0wn.png)

9）最后部署插件即可。  

### 使用模拟器调测数据上报

1）注册一个新设备： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/08/134434ezw8wcnvlv8bujbj.png)

2）使用NB设备模拟器，绑定后上报数据：先上报3条02开头的码流 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/195951rn6kpueercp62ax2.png)

3）查看设备历史数据：

<!--说明：数组类型使用base64进行编解码。数据上报是平台使用base64进行编码，所以应用收到推送消息后，如要知道原始码流是什么，得使用base64解码。base64编解码规则见本帖后面的介绍和总结-->

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/11/174653n5kvmr2zremm66er.png)

4）上报03开头的码流： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/195952lwnt19jueeutjont.png)

5）查看设备历史数据： 

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/195953jffowo325f4o7n42.png)

### 命令下发Profile和插件开发

1）在profile里添加一个命令和命令字段 

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143908rwhw6d55iudc969y.png)

2）插件中添加一个命令下发消息，其中messageId为04 

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143909q5zh6jksc5xv57cp.png)

info字段内容如下：

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143908un0ksy11thtn1n3t.png)

3）部署插件后。

### 使用模拟器调测命令下发

1）先上报两个数据： 

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143910c5z5qx8qdqor5j51.png)

2）上报的消息转码后结果如下：

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143910kqycmgynqvjvo11y.png)

3）将收到的other_info的内容作为命令下发字段的参数值下发给设备：

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143911avhb8555khc5kokh.png)

4）设备模拟器收到的数据如下：

![img](https://developer.huawei.com/ict/forum/data/attachment/forum/201810/23/143912u7j1nijwjl4jxiuu.png)

### Base64编解码介绍

我们以上面的03开头的消息为例进行说明，找一个base64在线编解码器，将other_info的值进行解码（注意勾选解码结果以16进制显示）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/201600euxfq00o6d8q6gg5.png)

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/201600e2e8mgmmp9m88g41.png)

那么反过来编码的结果会是什么样的呢？

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/202049zccdycmm88jmc78k.png)

为什么得到的结果不是AQ==呢？原因很简单，因为这里是按照字符编码的，而不是按数值进行编码的。我们可以按照base64编码原理手动计算一下。
base64编码说明：Base64编码要求把3个8位字节（3\*8=24）转化为4个6位的字节（4*6=24），之后在6位的前面补两个0，形成8位一个字节的形式。 如果剩下的字符不足3个字节，则用0填充，输出字符使用'='，因此编码后输出的文本末尾可能会出现1或2个'='。

这是什么意思呢？我们一起计算一下就明白了。 base64每3个8字节进行编码，每个8字节是一个字符，这里有两种转化方式，导致编码会有2种结果。 
1）把01当作字符，不足3个字符，补1个0，得到010，再转成8字节2进制表示。字符怎么用2进制表示的？在计算机里使用ascii码表示，查[ascii码表](https://baike.baidu.com/item/ASCII/309296?fr=aladdin&fromid=19660475&fromtitle=ascii%E7%A0%81%E8%A1%A8)，0的2进制ascii码为00110000，1的2进制ascii码为00110001，010就变成了001100000011000100110000（3\*8=24），转化为4个6位的字节（4*6=24）就变成001100、000011、000100、110000（每6位数一组，我在中间用、隔开），之后在6位的前面补两个0，形成8位一个字节的形式，00001100、00000011、00000100、00110000，这几个数转成10进制的值分别为12、3、4、48，再查base64的表，12为M，3为D，4为E，最后一位因为我们补了一个0才得到的010（如果剩下的字符不足3个字节，则用0填充，输出字符使用'='），所以使用=表示，就得到了MDE=   

2）把01当作数值（也就是1），不足3个字符，补2个0，得到100，转成8字节2进制表示，即0转成00000000，1转成00000001，于是100就是000000010000000000000000，转化为4个6位的字节（4\*6=24）就变成000000、010000、000000、000000，前面补两个0得到00000000、00010000、00000000、00000000，这几个数转成10进制的值分别为0、16、0、0，再查base64的表，0为A，16为Q，后面2个字符因为我们补了2个0所以都是=，就得到了AQ==。

### 总结

1）数组类型的数据是按Base64码进行编解码的，**比如在数据上报时01转为“AQ==”，命令下发时将“AQ==”（命令下发的参数值为AQ==）转为01。大家可以试试看。
2）可变长度数组要关联长度字段，长度字段必须为int型 
3）命令下发直接使用定长的数组即可，下发的字段长度是其实是以实际下发的数据为准。
4）平台使用的Base64编码是将码流当作数值型而非字符型（见上面的第二种转化方法）。

补充：

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/10/211228jez84yor7rtygsgs.png)

## 第五章命令的响应-命令结果的上报

### Profile和插件开发

1）命令中加入命令响应

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152050k50zy97105ii8tt8.png)

2）打开插件修改原来的命令，勾选上响应字段

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152052bco251sktyyksd7z.png)

3）编辑命令下发字段

删除messageId后的字段（如果是新增命令可跳过这步）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152053g3f93oa6eho9hka3.png)

4）添加mid

注：原消息中已有messageId，所以这里不用添加；如果是新增命令消息，需要添加messageId；

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152054er36llfclacmannz.png)

5）新增自定义业务字段即命令下发参数

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152858hwqlglgih88zxmww.png)

6）编辑命令响应字段：添加messageId（默认值为6，对应码流是06）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152056ir1pj4bp1bg1p4y6.png)

7）再添加errcode（表示命令执行结果的成功与失败）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152053svxan8qo734n9r44.png)

8）再添加mid

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152054er36llfclacmannz.png)

9）mid后面的字段是自定义的业务字段

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152057v1ei84hi1l880hrj.png)

10）与profile中的字段关联（务必看图中的说明）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152058ogdc4krp9nhkgn77.png)

11）关联完成后部署插件。

### 使用模拟器调测

1）注册一个新设备

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152058prsdpus0z0unssrn.png)

2）使用NB模拟器模拟设备，绑定成功后先上报一个业务码流

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152100f35yw23h505ms100.png)

3）下发一条命令（注意：使用模拟器模拟设备，上报数据后马上下发命令）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152101jgj34p0090lpygyl.png)

4）命令状态变成已送达

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152102n3yzo7m4k9xhhhzx.png)

5）再上报命令执行结果（06开头的码流表示SET_ALARM的命令执行结果）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152102mgsosfew1gn0e9ee.png)

6）命令状态变成执行成功

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152103t98c5b181rbnvv8k.png)

7）再下发3条命令

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152104bs8xchueexh05qo7.png)

8）上报2条命令执行结果（一条成功，一条失败）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152104vhinwb5zf4b24hnb.png)

9）命令状态进行相应变化（有一条保持不变）

![img](http://developer.huawei.com/ict/forum/data/attachment/forum/201804/12/152106i0xav000m0pb5kxb.png)

### 总结

1）插件中添加命令响应（命令执行结果上报），则上行消息必须使用mid（命令执行结果上报是上行消息）；
2）命令下发的mid是2个字节，对于每个设备来说，mid从1递增到65535，对应码流就是0001到FFFF；
3）设备执行完命令，命令执行结果上报中的mid要与收到命令中的mid保持一致，这样平台才能刷新对应命令的状态；
