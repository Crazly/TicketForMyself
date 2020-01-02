# J12306抢票助手
12306抢票程序JAVA版，自动登录-验证-查票-购票/自动候补。只需简单的配置即可运行进行快捷抢票。

### 使用说明
##### 引入jar依赖
* 手动添加项目lib文件夹中的依赖包
##### 配置文件config.yml
```
# 请修改相关配置

# 12306账号密码配置（暂时没用到）
j12306:
  user: 182xxxx
  password: 123456

  ticket:
    queryspeed: 2000 # 刷票速度（单位毫秒）。默认2秒。温馨提示：刷票频率不要过快，避免封IP（暂未测试过）
    alternate: true # 开启自动候补
    queryp: Z # 查票默认接口（可选值：A、Z）。说明：由于12306官方查票接口经常在A和Z两个接口中变更，所以为了方便，在此处加了默认接口配置。

  # 通知配置
  notice:
    # 电子邮件配置
    email:
      sender:
        from: hutool@yeah.net   # 发件人（必须正确，否则发送失败）
        host: smtp.yeah.net    # 邮件服务器的SMTP地址，可选，默认为smtp.<发件人邮箱后缀>
        port: 25    # 邮件服务器的SMTP端口，可选，默认25
        user: hutool    # 用户名
        pass: qlw2e3    # 密码（注意，某些邮箱需要为SMTP服务单独设置密码，详情查看相关帮助）
      receiver: 1481397688@qq.com   # 接收人邮箱
```

##### 配置抢票信息
* Main.java中，直接配置用户名密码及乘车相关信息即可
##### 开始抢票
* 直接运行Main函数开始抢票。就是这么简单粗暴！

##### 程序运行log
```
[2019-09-22 12:42:33] [INFO] com.kalvin.J12306.api.Login: 进入12306登录页，状态码：200
[2019-09-22 12:42:36] [INFO] com.kalvin.J12306.AI.Easy12306AI: 验证码：3,4
[2019-09-22 12:42:37] [INFO] com.kalvin.J12306.api.Login: 验证码通过，开始密码登录
[2019-09-22 12:42:37] [INFO] com.kalvin.J12306.api.Login: 登录成功
[2019-09-22 12:42:40] [INFO] com.kalvin.J12306.api.Ticket: 进入查询车票页面，开始查票...
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2804，出发时间：07:06，到达时间：08:10，座席：一等座1、二等座12、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D1849，出发时间：07:23，到达时间：08:37，座席：一等座4、二等座有、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D7551，出发时间：09:23，到达时间：11:02，座席：一等座有、二等座有、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2962，出发时间：09:35，到达时间：10:41，座席：一等座8、二等座14、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2812，出发时间：10:05，到达时间：11:11，座席：一等座无、二等座2、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D1822，出发时间：11:00，到达时间：12:06，座席：一等座3、二等座无、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2948，出发时间：11:34，到达时间：12:42，座席：一等座无、二等座无、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2834，出发时间：15:15，到达时间：16:27，座席：一等座2、二等座2、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2980，出发时间：17:19，到达时间：18:25，座席：一等座2、二等座20、无座有
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.CheckOrderInfo: 车票提交通过，正在尝试排队...
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.GetQueueCount: 排队成功，你当前排在6位，当前余票还有101张
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.ConfirmSingleForQueue: 不需要订单验证码，直接提交
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.ConfirmSingleForQueue: 开始正式下单...
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 下单ing...正在第1次排队ing...
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 订票成功！
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 恭喜您订票成功，订单号为：EF71508610, 请立即打开浏览器登录12306，访问‘未完成订单’，在30分钟内完成支付!
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 以邮件方式通知抢票人
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.Go12306: 抢票程序结束：STOP
```
### 更新日志
##### 2019-12-24
* 新增座席选择，现在支持座席【商务特等座(P)、一等座(M)、二等座(O)、无座(N)、软卧(4)、硬卧(3)、软座(2)、硬座(1)】
* 优化抢票逻辑及代码
##### 2019-12-22 
* 更改刷票频率（config.yml[j12306.ticket.queryspeed]）粒度为毫秒（ms）， 原秒（s）。
* config.yml新增配置项：[j12306.ticket.queryp]；由于12306官方查票接口经常在A和Z两个接口中变更，
现在支持配置默认查票接口（不是必要的），另外程序也会自动识别无法访问的查票接口，并自动切换，如：queryZ -> queryA
* 更新错误日志输出级别
### 问题反馈
如有疑问，可在项目上issues！
### 常见问题解决
* RAIL_EXPIRATION值已失效<br>
有时候网络原因导致的，请务必多重试几次，如果还是这种情况就更新下logdevice接口的参数；更新步骤：
    * 以下顺序一定要对，不然找不到logdevice
    * 1.浏览器访问：https://kyfw.12306.cn/otn/login/init
    * 2.按f12进入调试模式并点击Network选项
    * 3.清除浏览器缓存的有关12306.cn和kyfw.12306.cn的Cookie（谷歌浏览器点击浏览器地址栏的小锁）
    * 4.按f5重新刷新(只有第1次刷新才有出现，所以不要刷新2次)
    * 5.在Network选项下找到logdevice请求，点击它，在Headers选项下拉到最下面就可以找到如下几个参数，复制替换它即可
* 其它情况登录失败或验证码验证失败<br>
可能的解决方案：
    * 请重试登录多次
    * 确保更新到最新的代码
* 线程【main】无法获取车票信息，状态码：302<br>
可能的解决方案：
    * 确保你IP没被封（在浏览器上12306官网是否能正常查票）
    * 更新最新代码


J12306抢票助手
12306抢票程序JAVA版，自动登录-验证-查票-购票/自动候补。只需简单的配置即可运行进行快捷抢票。

使用说明
引入jar依赖
手动添加项目lib文件夹中的依赖包
配置文件config.yml
# 请修改相关配置

# 12306账号密码配置（暂时没用到）
j12306:
  user: 182xxxx
  password: 123456

  ticket:
    queryspeed: 2000 # 刷票速度（单位毫秒）。默认2秒。温馨提示：刷票频率不要过快，避免封IP（暂未测试过）
    alternate: true # 开启自动候补
    queryp: Z # 查票默认接口（可选值：A、Z）。说明：由于12306官方查票接口经常在A和Z两个接口中变更，所以为了方便，在此处加了默认接口配置。

  # 通知配置
  notice:
    # 电子邮件配置
    email:
      sender:
        from: hutool@yeah.net   # 发件人（必须正确，否则发送失败）
        host: smtp.yeah.net    # 邮件服务器的SMTP地址，可选，默认为smtp.<发件人邮箱后缀>
        port: 25    # 邮件服务器的SMTP端口，可选，默认25
        user: hutool    # 用户名
        pass: qlw2e3    # 密码（注意，某些邮箱需要为SMTP服务单独设置密码，详情查看相关帮助）
      receiver: 1481397688@qq.com   # 接收人邮箱
配置抢票信息
Main.java中，直接配置用户名密码及乘车相关信息即可
开始抢票
直接运行Main函数开始抢票。就是这么简单粗暴！
程序运行log
[2019-09-22 12:42:33] [INFO] com.kalvin.J12306.api.Login: 进入12306登录页，状态码：200
[2019-09-22 12:42:36] [INFO] com.kalvin.J12306.AI.Easy12306AI: 验证码：3,4
[2019-09-22 12:42:37] [INFO] com.kalvin.J12306.api.Login: 验证码通过，开始密码登录
[2019-09-22 12:42:37] [INFO] com.kalvin.J12306.api.Login: 登录成功
[2019-09-22 12:42:40] [INFO] com.kalvin.J12306.api.Ticket: 进入查询车票页面，开始查票...
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2804，出发时间：07:06，到达时间：08:10，座席：一等座1、二等座12、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D1849，出发时间：07:23，到达时间：08:37，座席：一等座4、二等座有、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D7551，出发时间：09:23，到达时间：11:02，座席：一等座有、二等座有、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2962，出发时间：09:35，到达时间：10:41，座席：一等座8、二等座14、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2812，出发时间：10:05，到达时间：11:11，座席：一等座无、二等座2、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D1822，出发时间：11:00，到达时间：12:06，座席：一等座3、二等座无、无座无
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2948，出发时间：11:34，到达时间：12:42，座席：一等座无、二等座无、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2834，出发时间：15:15，到达时间：16:27，座席：一等座2、二等座2、无座有
[2019-09-22 12:42:42] [INFO] com.kalvin.J12306.Go12306: 可预订车票信息：发车日期：2019-09-26，车次：D2980，出发时间：17:19，到达时间：18:25，座席：一等座2、二等座20、无座有
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.CheckOrderInfo: 车票提交通过，正在尝试排队...
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.GetQueueCount: 排队成功，你当前排在6位，当前余票还有101张
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.ConfirmSingleForQueue: 不需要订单验证码，直接提交
[2019-09-22 12:42:46] [INFO] com.kalvin.J12306.api.ConfirmSingleForQueue: 开始正式下单...
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 下单ing...正在第1次排队ing...
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 订票成功！
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 恭喜您订票成功，订单号为：EF71508610, 请立即打开浏览器登录12306，访问‘未完成订单’，在30分钟内完成支付!
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.api.QueryOrderWaitTime: 以邮件方式通知抢票人
[2019-09-22 12:42:48] [INFO] com.kalvin.J12306.Go12306: 抢票程序结束：STOP
更新日志
2019-12-24
新增座席选择，现在支持座席【商务特等座(P)、一等座(M)、二等座(O)、无座(N)、软卧(4)、硬卧(3)、软座(2)、硬座(1)】
优化抢票逻辑及代码
2019-12-22
更改刷票频率（config.yml[j12306.ticket.queryspeed]）粒度为毫秒（ms）， 原秒（s）。
config.yml新增配置项：[j12306.ticket.queryp]；由于12306官方查票接口经常在A和Z两个接口中变更， 现在支持配置默认查票接口（不是必要的），另外程序也会自动识别无法访问的查票接口，并自动切换，如：queryZ -> queryA
更新错误日志输出级别
问题反馈
如有疑问，可在项目上issues！

常见问题解决
RAIL_EXPIRATION值已失效
有时候网络原因导致的，请务必多重试几次，如果还是这种情况就更新下logdevice接口的参数；更新步骤：
以下顺序一定要对，不然找不到logdevice
1.浏览器访问：https://kyfw.12306.cn/otn/login/init
2.按f12进入调试模式并点击Network选项
3.清除浏览器缓存的有关12306.cn和kyfw.12306.cn的Cookie（谷歌浏览器点击浏览器地址栏的小锁）
4.按f5重新刷新(只有第1次刷新才有出现，所以不要刷新2次)
5.在Network选项下找到logdevice请求，点击它，在Headers选项下拉到最下面就可以找到如下几个参数，复制替换它即可
其它情况登录失败或验证码验证失败
可能的解决方案：
请重试登录多次
确保更新到最新的代码
线程【main】无法获取车票信息，状态码：302
可能的解决方案：
确保你IP没被封（在浏览器上12306官网是否能正常查票）
更新最新代码
