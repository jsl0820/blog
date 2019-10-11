---
title: go语言入门到放弃之Time包常用方法
date: 2019-09-05 21:37:46
tags:
---

## 获取当前时间 
```go
   nowTime := time.Now() //这是一个时间类型
   timeUnix := time.Now().Unix() //获取时间戳
   dateTime := time.Now().Format("2006-01-02 15:04:05") //时间格式化之后的日期 返回字符串       
```
## 获取年月日
```go
   y := nowTime.Year()
   m := nowTime.Month()
   d := nowTime.Day()
   h := nowTime.Hour()
   s := nowTime.Minute()
   n := nowTime.Nanosecond() //纳秒
```

## 解析传入的时间字符串返回时间类型
```go
   //时间字符串转时间
   date := "2019-02-19"
   //注意改函数返回的时区是UTC
   time, _ := time.Parse("2006-01-02 15:04:05",date)
   //可以用这个返回本地时区时
   localTime, _ := time.ParseInLocation("2006-01-02 15:04:05", date, time.Local)
   
```

## 计算两个时间的时间差

```go
//当前时间
now := time.Now()
//目标时间
date, _ := time.ParseInLocation("2006-01-02 15:04:05", "2019-08-28", time.Local)
subTime := now.Sub(date) // now - date
//可以打印相差的时间
hours := subTime.Hours()


```
## 查看是否在某个时间点之前或之后
```go
//当前时间
now := time.Now()
//目标时间
timeEnd, _ :=  time.ParseInLocation("2006-01-02 15:04:05", date, time.Local)
now.Before(timeEnd) //之前
now.After(timeEnd)  //之后
//函数返回bool值
 ```
 ## 时间相加/减，以及2个时间的时间间隔
 ```go
 //第一种方法：加 年-月-日
 now := time.Now()
 y := 1
 m := 1
 d := 1
 // 注意这个方法中如果月份+1 而下个月没有对应的日期就会往后推
 now.AddDate(y, m, d) //给当前时间分别加上1年1月1天
 
 // 第二种方法:使用time.ParseDuration 和 Time.Add()
 h1, _ := time.ParseDuration("1h")  //如果值为-1h 对应之前
 h2, _ := time.ParseDuration("-1h") //
 h3 := now.Add(h1 * 8) //8小时之后 
 h4 := now.Add(h2 * 8) //8小时之前     
 ```

## 定时相关
### time.Sleep(d) 
```go
//暂停一段时间
//程序暂停5S后再执行下面的代码
time.Sleep(5 * time.Second)
fmt.Println("javelin")
```

### golang的定时器
创建定时器有多种方法， 他们的底层实现都指向一个叫==timer==的结构体
1. NewTimer(d Duration) 
```go
d  := time.Duration(2) * time.Second 
te := time.NewTimer(d)

for {
      t := <-te.C
      fmt.Println("当前时间:", t)
      //只能执行一次，每次都需要重置才能继续往下执行
      t.Reset(d)
   }
}


```

2. time.After(d Duration) 
该函数会定期向返回的chan发送当前时间 和 这个底层实现是和 NewTimer(d).C 一样的
```go
d := time.Duration(10) * time.Second 
//用for达到一直循环的效果
for {
   t:=<-time.After(d) //取出，阻塞取消 程序往下执行
   fmt.Println(t.Format("2006-01-02 15:04:05")) //打印发送时的时间
} 
```




 

