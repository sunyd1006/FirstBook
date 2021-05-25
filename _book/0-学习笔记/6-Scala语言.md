
# Scala 语言 
## 测试 时间 转换 

import java.util.Date
import java.text.SimpleDateFormat

object test {

  def tranTimeToString(tm:Long) :String={
    val fm = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss")
    val tim = fm.format(new Date(tm))
    tim
  }

   def tranTimeToLong(tm:String) :Long={
    val fm = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss")
    val dt = fm.parse(tm)
    val aa = fm.format(dt)
    val tim: Long = dt.getTime()
    tim
  }
}

var time=System.currentTimeMillis()/(10 * 60 * 1000) * (10 * 60 * 1000).toString
test(time)
val fm = new SimpleDateFormat("yyyyMMdd")
val dt = fm.parse(time)
val aa = fm.format(dt)
val tim: Long = dt.getTime()

time = time - 24*3600
test.tranTimeToString(time)

## 常见示例 时间戳转换 规约分钟
scala> System.currentTimeMillis()
res4: Long = 1617332186888

scala> System.currentTimeMillis()/(10 * 60 * 1000) * (10 * 60 * 1000)
res5: Long = 1617331800000

scala> test.tranTimeToString(res4)
res6: String = 2021-04-02 10:56:26

scala> test.tranTimeToString(res5)
res7: String = 2021-04-02 10:50:00

## 常见示例 时间戳转换 倒计时一天
scala> test.tranTimeToString(time)
res11: String = 2021-04-02 10:48:33

scala> time = time - 24*3600*1000
time: Long = 1617245313600

scala> test.tranTimeToString(time)
res12: String = 2021-04-01 10:48:33


## 去乱码
(0 until 3).map(index =>{
  println(index)
  if(index>3) println("haha")
})

## 测试 Scala HashSet ConcurrentHashMap 遍历
import java.util.concurrent.ConcurrentHashMap
import java.util

val sidSetMap = new ConcurrentHashMap[String, util.HashSet[String]]
sidSetMap.put("123", new util.HashSet[String]())
sidSetMap.get("123").add("v1")
sidSetMap.get("123").add("v2")
sidSetMap.get("123").add("v3")

// 一定要导入转换类
import scala.collection.JavaConversions._
sidSetMap.entrySet().foreach(entry=>{
    entry.getValue.foreach(sid=>{
        println(sid)
    })
})


// 一定要导入转换类
import scala.collection.JavaConversions._
val set = new util.HashSet[String]()
set.add("a")
set.add("b")
set.add("c")

set.foreach(one=>{
    println(one)
})


## Map foreach
https://www.geeksforgeeks.org/scala-map-foreach-method-with-example/