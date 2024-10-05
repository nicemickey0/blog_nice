---
title: python农历与公历转换
categories: Python文章
tags: 
  - 技术
  - Python
top_img: https://www.helloimg.com/i/2024/10/05/6700dfd43dabb.png
date: 2024-10-2 14:32:48
updated: 2024-10-3 14:23:03
cover: https://www.helloimg.com/i/2024/10/05/6700dfd43dabb.png
description: python农历与公历转换
keywords: python
swiper_index: 1
top_group_index: 2
highlight_shrink: # 配置代码框是否展开
sticky: 6 # 文章置顶
--- 


一般的日历库是顶多支持1800年到2200年，但是sxtwl支持BC722到9999年之间的所有日期。
如果有需要做古人八字，祖先八字、考古日历参考, 古代的农历阳历转换 这些需要的，强烈推荐。下面是一些常用功能的介绍。


## 1. 安装sxtwl库


```python
pip install sxtwl
```


## 2. 公历转农历

```python
day = sxtwl.fromSolar(2022, 2, 6)
s = "农历:%d年%s%d月%d日" % (day.getLunarYear(), '闰' if day.isLunarLeap() else '', day.getLunarMonth(), day.getLunarDay())
print(s)
```

![image](https://www.helloimg.com/i/2024/10/05/6700dee8a299d.png)



## 3.农历转公历

```python
# 定义农历日期
day = sxtwl.fromLunar(2022, 1, 6)
# 公历的年月日
s = "公历:%d年%d月%d日" % (day.getSolarYear(), day.getSolarMonth(), day.getSolarDay())
s
```

![image](https://www.helloimg.com/i/2024/10/05/6700def38c0c9.png)

## 其他用法


```python
import sxtwl
 
## 一些常量文字的定义。
jqmc = ["冬至", "小寒", "大寒", "立春", "雨水", "惊蛰", "春分", "清明", "谷雨", "立夏", "小满", "芒种", "夏至", "小暑", "大暑", "立秋", "处暑", "白露", "秋分", "寒露", "霜降", "立冬", "小雪", "大雪"]
Gan  = ["甲", "乙", "丙", "丁", "戊", "己", "庚", "辛", "壬", "癸"];
Zhi =  ["子", "丑", "寅", "卯", "辰", "巳", "午", "未", "申", "酉", "戌", "亥"]
ShX =  ["鼠", "牛", "虎", "兔", "龙", "蛇", "马", "羊", "猴", "鸡", "狗", "猪"]
WeekCn = ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六"]
XiZ = ('摩羯', '水瓶', '双鱼', '白羊', '金牛', '双子', '巨蟹', '狮子', '处女', '天秤', '天蝎', '射手')
 
 
# 从公历年月日获取一天的信息
day = sxtwl.fromSolar(2021, 11, 7)
 
# 从农历年月日获取一天的信息
# day = sxtwl.fromLunar(2020, 12, 1)
 
# 公历的年月日
s = "公历:%d年%d月%d日" % (day.getSolarYear(), day.getSolarMonth(), day.getSolarDay())
print(s)
 
# 星期几
print(WeekCn[day.getWeek()])
 
# 这个月的第几周
print('该日属于这个月的第%d周'%(day.getWeekIndex(),))
 
# 星座(有bug?待修复)
print("星座:", XiZ[day.getConstellation()])
 
# 以春节为界的农历(注getLunarYear如果没有传参，或者传true，是以春节为界的)
s = "农历:%d年%s%d月%d日" % (day.getLunarYear(), '闰' if day.isLunarLeap() else '', day.getLunarMonth(), day.getLunarDay())
print(s)
 
# 不以立春为界的农历
s = "农历:%d年%s%d月%d日" % (day.getLunarYear(False), '闰' if day.isLunarLeap() else '', day.getLunarMonth(), day.getLunarDay())
print(s)
 
 
# 以春节为界的天干地支 
yTG = day.getYearGZ(True)
print("以春节为界的年干支", Gan[yTG.tg] + Zhi[yTG.dz]) 
print("以春节为界的生肖:", ShX[yTG.dz])
 
# 以立春为界的天干地支 （注，如果没有传参，或者传false，是以立春为界的。刚好和getLunarYear相反）
yTG = day.getYearGZ()
print("以立春为界的年干支", Gan[yTG.tg] + Zhi[yTG.dz]) 
print("以立春为界的生肖:", ShX[yTG.dz])
 
#月干支
mTG = day.getMonthGZ()
print("月干支", Gan[mTG.tg] + Zhi[mTG.dz]) 
 
#日干支
dTG  = day.getDayGZ()
print("日干支", Gan[dTG.tg] + Zhi[dTG.dz]) 
 
#时干支
for hour in range(24):
    # 第一个参数为该天的天干，第二个参数为小时
    hTG  = sxtwl.getShiGz(dTG.tg, hour)
    print("%d时天干地支:"%(hour), Gan[hTG.tg] + Zhi[hTG.dz])
 
 
# 当日是否有节气
if day.hasJieQi():
    print('节气：%s'% jqmc[day.getJieQi()])
    #获取节气的儒略日数
    jd = day.getJieQiJD()
    # 将儒略日数转换成年月日时秒
    t = sxtwl.JD2DD(jd )
    
    # 注意，t.s是小数，需要四舍五入
    print("节气时间:%d-%d-%d %d:%d:%d"%(t.Y, t.M, t.D, t.h, t.m, round(t.s)))
else:
    print("当天不是节气日")
 
 
# 四注反查 分别传的是年天干，月天干，日天干，时天干， 开始查询年，结束查询年  返回满足条件的儒略日数
jds = sxtwl.siZhu2Year(yTG, mTG, dTG, sxtwl.GZ(5, 5), 2003, 2029);
for jd in jds:
    t = sxtwl.JD2DD(jd )
    print("符合条件的时间:%d-%d-%d %d:%d:%d"%(t.Y, t.M, t.D, t.h, t.m, round(t.s)))
 
 
# 获取一年中的闰月
year = 2020
month = sxtwl.getRunMonth(year)
if month >= 0:
    print("%d年的闰月是%d"%(year, month) )
else:
    print("没有闰月")
 
 
# 一个农历月的天数
year = 2020 #农历年
month  = 4 #农历月
isRun = False #是否是闰月
daynum = sxtwl.getLunarMonthNum(year, month, isRun)
print("农历%d年%s%d月的天数:"%(year, '闰'if isRun else '', month), daynum)
 
 
#儒略日数转公历
jd = sxtwl.J2000
t = sxtwl.JD2DD(jd )
 
#公历转儒略日
jd = sxtwl.toJD(t)
 
# 获取某天的后面几天
num = 1    #你喜欢写多少天 也多少天，可以写负数，相当于往前
day = day.after(num)  #获取num天后的日信息
s = "公历:%d年%d月%d日" % (day.getSolarYear(), day.getSolarMonth(), day.getSolarDay())
print(s)
 
# 同上
day = day.before(num)
s = "公历:%d年%d月%d日" % (day.getSolarYear(), day.getSolarMonth(), day.getSolarDay())
print(s)
 
 
# 查找某日前后的节气
while True:
    # 这里可以使用after或者before，不用担心速度，这里的计算在底层仅仅是+1这么简单
    day = day.after(1)
    # hasJieQi的接口比getJieQiJD速度要快，你也可以使用getJieQiJD来判断是否有节气。
    if day.hasJieQi():
        print('节气：%s'% jqmc[day.getJieQi()])
        #获取节气的儒略日数， 如果说你要计算什么时间的相距多少，直接比对儒略日要方便，相信我。
        jd = day.getJieQiJD()
    
        # 将儒略日数转换成年月日时秒
        t = sxtwl.JD2DD(jd )
        
        # 注意，t.s是小数，需要四舍五入
        print("节气时间:%d-%d-%d %d:%d:%d"%(t.Y, t.M, t.D, t.h, t.m, round(t.s)))
        
        break


```

