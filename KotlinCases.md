# Kotlin Cases
> Shawn
* IDE: IntelliJ IDEA 2018.2.3
* Kotlin: 1.2.71
* JDK: 1.8.0_161
----
**注: 本文中实例参考于 [runoobJava实例](http://www.runoob.com/java/java-examples.html)**

## 1 字符串

### 1.1 字符串比较 StringCompare
* 功能: 通过compareTo和equals比较两个字符串
* 介绍: compareTo会比较两个字符串的首字母(字典序),equals会比较两个字符串,两个方法均有可选忽视大小写的参数.
```kotlin
fun main(args: Array<String>) {
    var str : String = "Hello World"
    var str1 : String = "Hello World"
    var str2 : String = "hello World"
    println(str.compareTo(str1))
    println(str.compareTo(str2))
    println(str.compareTo(str2,true))
    println(str.equals(str1))
    println(str.equals(str2))
    println(str.equals(str2,true))
}
```

### 1.2 查找最后一次出现位置 StringLastIndexOf
* 功能: 通过lastIndexOf查找给定字符串在目标字符串最后一次出现的位置.
* 介绍:
    * lastIndexOf是从后向前查找的.
    * startIndex参数可以指定从哪里开始向前查找.
    * 传递参数可以按位置传递,也可以按参数名传递.
```kotlin
fun main(args: Array<String>) {
    var str : String = "Hello, handsome boy."
    var str1: String = "boy? I am not a boy!"
    var lastHandsome : Int = str.lastIndexOf("handsome")
    var lastBoy : Int = str.lastIndexOf("BoY",ignoreCase = true,startIndex = str.length)
    var lastBoyInStr1 : Int = str1.lastIndexOf("boy",str1.length-5,true)
    println("The last index of \"handsome\" is "+lastHandsome)
    println("The last index of \"boy\" is "+lastBoy)
    println("Now I ignore the last 5 chr in str1: "+lastBoyInStr1)
}
```

### 1.3 删除字符 StringRemoveChr
* 功能: 做一个函数来实现删除字符串给定位置的字符.
* 介绍:
    * 构建返回非空函数的时候最好先声明返回类型.
    * PHP可能不是最好的语言.
```kotlin
fun main(args: Array<String>) {
    var str : String = "PHP, the best language."
    println(removeCharAt(str,1))
}

fun removeCharAt(s:String,pos:Int): String{
    return s.substring(0,pos)+s.substring(pos+1)
}
```

### 1.4 反转字符串 StringReverse
* 功能: 反转字符串
* 介绍: 无
```kotlin
fun main(args: Array<String>) {
    var str : String = "Shawn"
    var strReversed : String = str.reversed()
    println(str)
    println(strReversed)
}
```

### 1.5 查找字符串 StringIndexOf
* 功能: indexOf搜索字符串出现的位置.
* 介绍: 正向搜索,参考1.2,若没找到则返回-1.
```kotlin
fun main(args: Array<String>) {
    var str : String = "Python CPP Java Ruby Kotlin"
    printPos(str.indexOf("python"))
    printPos(str.indexOf("python",ignoreCase = true))
    printPos(str.indexOf("Java"))
}

fun printPos(pos:Int){
    if(pos == -1){
        println("Do not find that string.")
    }
    else
    {
        println("Find that string in "+pos)
    }
}
```

### 1.6 字符串分割 StringSplit
* 功能: 通过split分割字符串
* 介绍:
    * split可以指定以特定标志等来分割字符串
    * kotlin在创建对象的时候有一定的猜测(类型)能力
```kotlin
fun main(args: Array<String>) {
    var str : String = "Shawn-handsome-python-best"
    var splited : List<String> = str.split("-")
    println(splited)
}
```

### 1.7 字符串大小写 StringUpperAndLower
* 功能: 通过upper和lower可以将字符串做大小写变换
* 介绍: 无
```kotlin
fun main(args: Array<String>) {
    var str = "Shawn"
    println(str.toUpperCase())
    println(str.toLowerCase())
}
```

### 1.8 字符串区域匹配 StringRegionMatch
* 功能: 通过regionMatches来确定两个字符串给定区域是否相同
* 介绍:
    * 第四行翻译一下: 从str1的第4位与str2的第4位开始数,2位是否都相等.
    * 同样支持ignoreCases
```kotlin
fun main(args: Array<String>) {
    var str1 = "php Is the best."
    var str2 = "who is your daddy?"
    println(str1.regionMatches(4,str2,4,2))
    println(str1.regionMatches(4,str2,4,2,true))
}
```

### 1.9 字符串格式化 StringFormat
* 功能: 使用字符串格式化
* 介绍: kotlin中直接调用java的函数也是ok的.
```kotlin
import java.util.*

fun main(args: Array<String>) {
    var e = Math.E
    System.out.format("%f%n",e)
    System.out.format(Locale.CHINA, "%-10.4f%n%n", e)
}
```

### 1.10 连接字符串 StringAppend
* 功能: 用+连接字符串
* 介绍: 无
```kotlin
fun main(args: Array<String>) {
    var str1 = "No gods "
    var str2 = "Or kings "
    var str3 = "Only man!"
    println(str1+str2+str3)
}
```

## 2 数组

### 2.1 数组排序以及二分查找 ArraysSortAndSearch
* 功能: 数组的排序\搜索
* 介绍:
    * kotlin中生成整数数组用intArrayOf
    * 生成Array<T>可以用arrayOf来进行.
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(1,5,2,3,9,1)
    print("Original: ")
    printIntArray(array)
    array.sort()
    print("Sorted: ")
    printIntArray(array)
    println("'5' in the position: "+array.binarySearch(5))

}

fun printIntArray(intArray: IntArray){
    for(i in intArray){
        print(" "+i)
    }
    println()
}
```

### 2.2 添加元素
* 功能: 生成ArrayList并向其中添加元素.
* 介绍: 如果函数返回为空,可以声明Unit(也可以什么都不写)
```kotlin
fun main(args: Array<String>) {
    var array = arrayListOf(1,2,3,4,"dog")
    array.add(2.3)
    array.add(true)
    printArrayList(array)
}

public fun printArrayList(arrayList: ArrayList<Any>):Unit{
    for(i in arrayList){
        println(i.toString())
    }
}
```

### 2.3 数组长度
* 功能: 获取数组的长度
* 介绍: 无
```kotlin
fun main(args: Array<String>) {
    var array : Array<Any> = Array<Any>(4,{9})
    array.set(0,1)
    array.set(1,"hop")
    for(i in array){
        println(i)
    }
    println("The length of array is "+array.size)
}
```

### 2.4 数组反转
* 功能: 反转数组
* 介绍: reverse可以直接将ArrayList反转.
```kotlin
fun main(args: Array<String>) {
    var array = arrayListOf<Any>(1,2,3,4,5)
    array.reverse()
    printArrayList(array)//from ArraysInsert.kt
}
```

### 2.5 数组极值
* 功能: 获得数组的极值
* 介绍: 数组的max和min可以直接获得.
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(2,3,1,6,-1,6,99)
    println("The maximum of array is "+array.max())
    println("The minimum of array is "+array.min())
}
```

