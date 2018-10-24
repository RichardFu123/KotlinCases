# Kotlin Cases
> Shawn
* IDE: IntelliJ IDEA 2018.2.3
* Kotlin: 1.2.71
* JDK: 1.8.0_161
----
**强烈推荐[Kotlin官方文档](https://www.kotlincn.net/docs/reference/)**
**代码见[github](https://github.com/RichardFu123/KotlinCases)**
**注: 本文中实例部分参考于 [runoobJava实例](http://www.runoob.com/java/java-examples.html)**

----

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

### 2.2 添加元素 ArraysInsert
* 功能: 生成ArrayList并向其中添加元素.
* 介绍: 如果函数返回为空,可以声明Unit(也可以什么都不写)
```kotlin
fun main(args: Array<String>) {
    var array = arrayListOf(1,2,3,4,"dog")
    array.add(2.3)
    array.add(true)
    printArrayList(array)
}

public fun printArrayList(arrayList: ArrayList<out Any>):Unit{
    for(i in arrayList){
        println(i.toString())
    }
}
```

### 2.3 数组长度 ArraysLength
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

### 2.4 数组反转 ArraysReverse
* 功能: 反转数组
* 介绍: reverse可以直接将ArrayList反转.
```kotlin
fun main(args: Array<String>) {
    var array = arrayListOf<Any>(1,2,3,4,5)
    array.reverse()
    printArrayList(array)//from ArraysInsert.kt
}
```

### 2.5 数组极值 ArraysMaxAndMin
* 功能: 获得数组的极值
* 介绍: 数组的max和min可以直接获得.
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(2,3,1,6,-1,6,99)
    println("The maximum of array is "+array.max())
    println("The minimum of array is "+array.min())
}
```

### 2.6 数组合并 ArraysMerge
* 功能: 将两个数组合并
* 介绍: array和list可以直接用相加进行合并
```kotlin
fun main(args: Array<String>) {
    var array1 : Array<String> = arrayOf("S","h","a")
    var array2 : Array<String> = arrayOf("w","n")
    var list = array1.asList()
    list+=array2.asList()
    println(list)
    array1+=array2
    printArray(array1)
}

public fun printArray(array:Array<out Any>){
    for (i in array){
        println(i)
    }
}
```

### 2.7 数组填充 ArraysFill
* 功能: 初始化一个指定大小的数组,并用指定数字填充
* 介绍: printIntArray见ArraysSortAndSearch
```kotlin
fun main(args: Array<String>) {
    var array = IntArray(6)
    array.fill(2)
    printIntArray(array)
}
```

### 2.8 数组扩展 ArraysExtend
* 功能: 扩展数组
* 介绍: 创造一个容量合适的新数组,然后将需要的数据拷进去.
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(1,2,3)
    var arrayExtended = IntArray(5)
    printIntArray(arrayExtended)
    arrayExtended[3] = 4
    arrayExtended[4] = 5
    System.arraycopy(array,0,arrayExtended,0,array.size)
    printIntArray(arrayExtended)
}
```
### 2.9 查找数组中的重复元素 ArraysDuplicates
* 功能: 查找重复元素
* 介绍: kotlin的in操作可以很轻松胜任这个工作
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(1,1,2,3,4,4,5,5,5,5,6,7,8,8,1,1,9,9)
    var dup = ArrayList<Int>()
    for (i in 0 until array.size-1){
        for(j in i+1 until array.size){
            if (array[i]==array[j] && !(array[i] in dup)){
                println("Find duplicate: "+array[i])
                dup.add(array[i])
            }
        }
    }
}
```

### 2.10 删除元素 ArraysRemove
* 功能: 删除指定位置的元素
* 介绍: 用removeAt可以删除指定索引的元素
```kotlin
fun main(args: Array<String>) {
    var arrayList = ArrayList<String>()
    arrayList.add("The first element")
    arrayList.add("The second element")
    arrayList.add("The third element")
    arrayList.removeAt(1)
    printArrayList(arrayList)
}
```

### 2.11 差集 ArraysRemoveAll
* 功能: 获得差集
* 介绍: removeAll会将找到的全部元素都删掉,而不是删去相应的数量
```kotlin
fun main(args: Array<String>) {
    var arrayList1 = arrayListOf(1,2,2,3,4,4)
    var arrayList2 = arrayListOf(1,2,5,3,3)
    arrayList1.removeAll(arrayList2)
    printArrayList(arrayList1)
}
```

### 2.12 交集 ArraysRetainAll
* 功能: 获得交集
* 介绍: retainAll会将找到的元素保留,为找到的舍弃
```kotlin
fun main(args: Array<String>) {
    var arrayList1 = arrayListOf("Shawn","Doge","Doge","XueBi","NiShiLong","NiShiLong")
    var arrayList2 = arrayListOf("Shawn","Doge","Biu","WoShiLong","WoShiLong")
    arrayList1.retainAll(arrayList2)
    printArrayList(arrayList1)
}
```

### 2.13 查找元素 ArraysSearch
* 功能: 查找指定元素是否存在于集合中
* 介绍: 有很多种方法实现,用in是最省事的一种
```kotlin
fun main(args: Array<String>) {
    var arrayList = arrayListOf(1,3,5,2,4,6,"DFWill","Boom!")
    println("DFWill in the list? "+("DFWill" in arrayList))
    println("1 in the list? "+arrayList.contains(1))
}
```

### 2.14 数组相等 ArraysEquals
* 功能: 判断两个数组内容是否相等
* 介绍: 使用contentEquals来进行比较.
```kotlin
fun main(args: Array<String>) {
    var array1 = intArrayOf(1,2,3,4)
    var array2 = intArrayOf(1,2,3,4)
    var array3 = intArrayOf(1,2)
    println("array1 equals array2? "+array1.contentEquals(array2))
    println("array1 equals array3? "+array1.contentEquals(array3))
}
```

### 2.15 并集 ArraysUnionSet
* 功能: 获得两个数组的并集
* 介绍:
    * set中不存在重复元素,所以可以用来去重.
    * set的交并补等运算更贴近实际逻辑.
```kotlin
fun main(args: Array<String>) {
    var array1 = intArrayOf(1,2,2,3)
    var array2 = intArrayOf(3,4,4,5)
    var unionSet = emptySet<Int>()
    unionSet+=array1.toSet()
    unionSet+=array2.toSet()
    printSet(unionSet)
}
public fun printSet(s:Set<out Any>){
    for(i in s){
        print(i.toString()+" ")
    }
    println()
}
```

## 3 时间

### 格式化时间
* 功能: 格式化输出时间
* 介绍: 直接调用java的相关模块即可.
```kotlin
import java.text.SimpleDateFormat
import java.util.*

fun main(args: Array<String>) {
    val data = Date()
    val dateFormat = "yyyy-MM-dd HH:mm:ss"
    val simpleDateFormat = SimpleDateFormat(dateFormat)
    println(simpleDateFormat.format(data))
}
```

## 4 类与对象

### 4.1 创建类 ClassInit
* 功能: 构建并实例一个类
* 介绍:
    * 类的可以有一个主构造函数及一个或多个次构造函数,在类头的是主构造函数(constructor)
    * 类中可以有多个初始化块(init)
    * 所有类集成自超类Any(与java的Object不同)
```kotlin
class ClassInit constructor(info:String){
    init{
        println(info+" in the initializer block 1")
    }
    var str1 = "var str1".also(::println)
    init{
        println(info+" in the initializer block 2")
        this.str1 = info
    }
    fun printstr1(){
        println("str1: "+str1)
    }
    val str2 = "val str2".also(::println)
}

fun main(args: Array<String>) {
    println("Begin")
    var classInit = ClassInit("New")
    var classInit2 = ClassInit("New2")
    classInit.printstr1()
    classInit2.printstr1()
}
```

### 4.2 次构造函数 ClassSecondaryConstructor
* 功能: 次构造函数
* 介绍:
    * 如果既有主构造函数,又有次构造函数,则次构造函数需要委托给主构造函数
    * 主构造函数中可以直接声明类中的变量(var)
    * 多个次构造函数可以实现多级调用
    * 次级构造函数会在所有变量初始化\initBlock调用完后再进行调用
    * 调用次级函数会先调用委托的部分
    * 可以指定默认参数值是一件很幸福的事情
```kotlin
class ClassSecondaryConstructor constructor(var name:String){
    init{
        println("Init block "+name)
    }
    var age = 0
    var father = "father of ${name}".also(::println)
    constructor(name:String,age:Int):this(name){
        this.age = age
        println("First secondary constructor "+name)
    }
    constructor(name:String,age:Int = 18,father:String):this(name,age){
        this.father = father
        println("Second secondary constructor "+name)
    }
    init{
        println("Init block2 "+name)
    }
}

fun main(args: Array<String>) {
    var a = ClassSecondaryConstructor("Shawn")
    var b = ClassSecondaryConstructor("XiaoMing",24)
    var c = ClassSecondaryConstructor("Me",father = "Father")
}
```

### 4.3 继承 ClassDerived
* 功能: 继承父类
* 介绍:
    * 如果没有主构造函数,次构造函数不需要委托
    * 可继承的类,可覆写的方法,属性都要用open修饰
    * 覆写前要用override声明
    * 可以用var覆写val,反之不行
    * 用super同样可以调用父类
```kotlin
open class Father{
    public var age = 18
    private var name = ""
    constructor(name: String){
        this.name = name
    }
    open public fun printName(){
        println(name)
    }
    public fun printAge(){
        println(age)
    }
}

class Boy(name:String,age:Int):Father(name){
    init{
        this.age = age
    }
    override fun printName(){
        super.printName()
        println("from Boy")
    }

}

fun main(args: Array<String>) {
    var father = Father("Father")
    var boy = Boy("Boy",5)
    father.printName()
    father.printAge()
    boy.printName()
    boy.printAge()
}
```

### 4.4 抽象与接口 ClassAbstractAndInterface
* 功能: 继承抽象类,满足接口
* 介绍:
    * 抽象与接口的规则老一套
    * super<父类>可以实现对多个父亲的选择
```kotlin
abstract class ClassAbstract(){
    var i: Int? = null
    abstract fun a()
    abstract fun b()
}
interface ClassAbstractA{
    fun a(i: Int):Int{
        return i
    }
}
interface ClassAbstractB{
    fun b(s: String):String{
        return s
    }
}
class ClassAbstractClass:ClassAbstract(),ClassAbstractA,ClassAbstractB{
    override fun a(){
        println("a")
    }
    override fun a(i:Int):Int{
        println("a"+i)
        return i+1
    }
    override fun b(){
        println("b")
    }
    override fun b(s: String): String {
        println("b"+s)
        return super<ClassAbstractB>.b(s)
    }
}

fun main(args: Array<String>) {
    var abstract = ClassAbstractClass()
    abstract.a()
    abstract.a(1)
    abstract.b()
    abstract.b("test")
}
```

### 4.5 getter和setter ClassGetterAndSetter
* 功能: 重写类属性的set和get
* 介绍:
    * 通过重写这两个访问器,可以更灵活地实现功能
    * val只支持get重写
```kotlin
fun main(args: Array<String>) {
    var get = GetAndSet()
    for(i in 0..5){
        get.answer = i
        println(get.answer)
    }
}

class GetAndSet(){
    var data = 0
    var answer : Int
        get() {
            if(data!=0)return 42
            else return data
        }
        set(value) {data = value%2}
    }
```

### 4.6 幕后字段 ClassField
* 功能: 用Field访问属性自身
* 介绍:
    * 由于在类属性的set和get内访问自身会进行递归最后导致栈溢出,所以kotlin提供了yield标识符.
    * yield不需要声明,在变量初始化后自动提供.
```kotlin
fun main(args: Array<String>) {
    var get = ClassField()
    for(i in 0..5){
        get.answer = i
        println(get.answer)
    }
}

class ClassField(){
    var answer : Int = 0
        set(value){
            field = value-1
        }
        get() {
            if(field==0)return 42
            else return field
        }
}
```

### 4.7 扩展函数 ClassExtend
* 功能: 使用扩展方法对类进行扩展
* 介绍:
    * 可以通过在类外定义函数来扩展类本身.
    * 扩展的函数不能访问类的私有属性
```kotlin
class ClassExtend{
    var str: String?= null
}
fun ClassExtend.printStr(){
    println(str)
}
fun ClassExtend.setStr(str:String){
    this.str = str
}

fun main(args: Array<String>) {
    var CE = ClassExtend()
    CE.printStr()
    CE.setStr("input something")
    CE.printStr()
}
```

### 4.8 伴生对象(静态成员) ClassCompanion
* 功能: 通过伴生对象来实现静态方法
* 介绍:
    * Kotlin中没有静态成员声明,但是有伴生方法可以实现
    * 虽然看起来像静态成员,但是伴生方法仍然是真是的实例成员,并且可以实现接口
```kotlin
class ClassCompanion{
    companion object {
        fun printHello(){
            print("Hello!")
        }
        val Dio: String = "Dio"
    }
}

fun main(args: Array<String>) {
    ClassCompanion.printHello()
    print(" "+ClassCompanion.Dio)
}
```

### 4.9 枚举类 ClassEnum
* 功能: 使用枚举类
* 介绍: 与Java中的枚举类区别不大
```kotlin
enum class ClassEnum(val rgb:Int,var stuff:String){
    RED(0xFF0000,"apple"){
        override fun print() {
            println(this.stuff)
        }
    },
    GREEN(0x00FF00,"Your hat"){
        override fun print() {
            println("That is ok "+this.stuff)
        }
    },
    BLUE(0x0000FF,"Sky"){
        override fun print() {
            println("I need some towers")
        }
    };
    abstract fun print()
}

fun main(args: Array<String>) {
    ClassEnum.RED.print()
    ClassEnum.GREEN.print()
    println(ClassEnum.BLUE.rgb)
    println(ClassEnum.BLUE.stuff)
    ClassEnum.BLUE.stuff = "Sea"
    println(ClassEnum.BLUE.stuff)
}
```

## 5 流程控制

### 5.1 分支流程 ControlSwitch
* 功能: 用if/when来控制程序流程
* 介绍:
    * if-else如常
    * when语句取代了switch
    * when语句不会依次执行,所以不需要额外的break
```kotlin
fun main(args: Array<String>) {
    var a = 1
    var b = 2
    if(a>b)
    {
        println(a)
    }
    else
    {
        println(b)
    }
    var max = if(a>b) a else b
    println(max)
    fun max(a:Int,b:Int) = when(a>b){
        true -> a
        false -> b
        else -> null
    }
    fun isString(a:Any) = when(a){
        is String -> println("That is a string")
        !is String -> println("That is not a string")
        else -> println("I have no idea")
    }
    println(max(233,666))
    isString("Fish!")
}
```

### 5.2 循环 ControlLoop
* 功能: while循环与java相同,主要介绍for循环
* 介绍:
    * 0..5 包括5
    * 0 until 5 不包括5
    * 5 downTo 0 包括5和0
```kotlin
fun main(args: Array<String>) {
    var array = intArrayOf(1,2,3,4,5,6,7)
    for(i in array) print(i)
    println()
    for(i:Int in array) print(i)
    println()
    for(i in 0..5) print(i)
    println()
    for(i in 0 until 5) print(i)
    println()
    for(i in 0 until 5 step 2)print(i)
    println()
    for(i in 5 downTo 0)print(i)
    println()
    for(i in 5 downTo 0 step 2) print(i)
}
```

### 5.3 转跳 ControlJump
* 功能: break以及continue
* 介绍:
    * break未指定标签,则终止最近一个循环
    * continue未指定标签,则跳过最近一个循环的当次循环
    * 用标签可为以上两个命令指定控制的循环
    * 标签也同样可以用于return,最常见于直接从lambda返回到函数主体
```kotlin
fun main(args: Array<String>) {
    loop@ for(i in 0..5){
        loop2@ for(j in 6..10){
            println(""+i+" and "+j)
            if (i == 5) {
                println("loop break")
                break@loop
            }
            if (j == 9) {
                println("loop2 continue")
                continue@loop2
            }
            if ((i==0) and (j==7)) {
                println("loop continue")
                continue@loop
            }

        }
    }
}
```

## 6 异常 Exception
* 功能: Kotlin中的异常处理与Java相似
* 介绍:
    * 用try-catch来捕捉异常
    * 可以用多个catch针对多个异常
    * 接finally来运行无论是否发生异常均可执行的程序
```kotlin
import java.lang.Exception

fun main(args: Array<String>) {
    var list = intArrayOf(0)
    for (i in 0..1){
        try {
            list[i] = 1 / i
            println(list[i])
        }catch(e: ArithmeticException){
            e.printStackTrace()
        }catch(e: ArrayIndexOutOfBoundsException){
            e.printStackTrace()
        }catch(e: Exception){
            e.printStackTrace()
        }finally {
            println("Finally "+i)
        }
    }

}
```

