# Kotlin Cases
> Shawn
* IDE: IntelliJ IDEA 2018.2.3
* Kotlin: 1.3.0-release-IJ2018.2-1
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
    * field不需要声明,在变量初始化后自动提供.
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

### 4.10 数据类 ClassData
* 功能: 用数据类来记录数据
* 介绍:
    * 数据类被设计来储存数据
    * 数据类的主构造函数至少要有一个参数
    * 主构造函数的多有参数必须有var或val修饰
    * 如果不特别实现,编译器会自动推导equals(),hashCode()和toString()
    * 用copy()可以快速实现同一份数据的复制\微调
```kotlin
data class ClassData(var aString: String,val bString: String){
    init {
        var sString = bString
    }
    fun print(){
        println("Print in ${this.javaClass}")
    }
}

fun main(args: Array<String>) {
    var banana = ClassData("aBanana","bBanana")
    var Banana = banana.copy(bString = "cBanana")
    println(banana)
    banana.print()
    println(Banana)
    Banana.print()
}
```

### 4.11 密封类 ClassSealed
* 功能: 使用密封类来让程序更顺眼
* 介绍:
    * 密封类自身是抽象的,不能直接实例化
    * 其构造函数为private类型的,且不允许有其他类型的构造函数
    * 密封类实现了一个有限的类集合
    * 密封类与when的结合非常严谨
    * when中使用密封类如果覆盖了全部的情况,则不需要定义else子句
    * when中使用了密封类,如果指明验证了其类型,则可以直接调用相应的方法.
```kotlin
sealed class ClassSealed
data class SealedA(var seal:String):ClassSealed()
class SealedB:ClassSealed(){
    fun print(){
        println("I am a little seal.")
    }
}
object SealedC:ClassSealed()

fun main(args: Array<String>) {
    var list = listOf<ClassSealed>(SealedB(),SealedA("I am here for basking."),SealedC)
    for (seal:ClassSealed in list){
        when(seal){
            is SealedA -> println(seal.seal)
            is SealedB -> seal.print()
            is SealedC -> println("And disappear again.")
        }
    }
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

## 7 运算符重载

### 7.1 一元运算符 OperatorOverloadUnary
* 功能: 重载类的一元运算符
* 介绍:
    * 类的运算符可以重载
    * 重载后的返回值与运算符原定义无关
    * 重载运算符要标注operator

```kotlin
class OperatorOverloadUnary(var i:Int){
    operator fun unaryPlus():Int{
        println("UnaryPlus: $i")
        return i
    }
    operator fun unaryMinus():Int{
        println("UnaryMinus: $i")
        return i-1
    }
    operator fun not():Int{
        println("not: $i")
        return i-2
    }

}

fun main(args: Array<String>) {
    val i = OperatorOverloadUnary(9)
    println(+i)
    println(-i)
    println(!i)
}
```

### 7.2 自运算 OperatorOverloadIncAndDec
* 功能: 重载自运算符
* 介绍:
    * 自运算如i++,i--的实现过程是:获取i初始值,获取i.inc()或i.dec()并赋给i,返回i初始值.
    * 自运算++i,--i的实现过程相似,只是返回的是i.inc()或i.dec()的值
```kotlin
class OperatorOverloadIncAndDec(var i:Int){
    init {
        println("Here is $i")
    }

    override fun toString(): String {
        return "toString: $i"
    }
    operator fun inc():OperatorOverloadIncAndDec{
        println("INC $i")
        return OperatorOverloadIncAndDec(i+10)
    }
    operator fun dec():OperatorOverloadIncAndDec{
        println("DEC $i")
        return OperatorOverloadIncAndDec(i-10)
    }
}

fun main(args: Array<String>) {
    var i = OperatorOverloadIncAndDec(42)
    i++
    i--
}
```

### 7.3 二元运算 OperatorOverloadBinary
* 功能: 重载二元运算符
* 介绍: 二元运算符要求有一个参数传入,类型不限
```kotlin
class OperatorOverloadBinary(var i: Int){
    operator fun plus(j:Int){
        println("plus $i and $j")
    }
    operator fun minus(s:String){
        println("minus $i and $s")
    }
    operator fun times(j:Int){
        println("times $i and $j")
    }
    operator fun div(j:Int){
        println("div $i and$j")
    }
    operator fun rem(j:Int){
        println("rem $i and $j")
    }
    operator fun rangeTo(s:String){
        println("rangeTo $i and $s")
    }
}

fun main(args: Array<String>) {
    var i = OperatorOverloadBinary(9527)
    i+1
    i-"Banana"
    i*3
    i/4
    i%5
    i.."Banana!"
}
```

### 7.4 赋值运算 OperatorOverloadAssign
* 功能: 重载赋值运算符
* 介绍: 如果相应函数不可用,则会尝试去调用二元运算
```kotlin
class OperatorOverloadAssign(var i: Int){
    operator fun plusAssign(s:String){
        println("plusAssign $i and $s")
    }
    operator fun minusAssign(i:Int){
        println("minusAssign ${this.i} and $i")
    }
    operator fun timesAssign(s:String){
        println("timesAssign $i and $s")
    }
    operator fun divAssign(i:Int){
        println("divAssign ${this.i} and $i")
    }
    operator fun remAssign(s:String){
        println("remAssign $i and $s")
    }
}

fun main(args: Array<String>) {
    var i = OperatorOverloadAssign(666)
    i+="banana"
    i-=2
    i*="Banana"
    i/=3
    i%="Banana!"
}
```

### 7.5 调用与访问 OperatorOverloadInvoke
* 功能: 重载调用与访问
* 介绍: 无
```kotlin
class OperatorOverloadInvoke(var i: Int){
    operator fun get(i:Int){
        println("get ${this.i} and $i")
    }
    operator fun set(i:Any,j:Any){
        println("set ${this.i} $i and $j")
    }
    operator fun invoke(i:Any){
        println("invoke ${this.i} and $i")
    }
}

fun main(args: Array<String>) {
    var i = OperatorOverloadInvoke(233)
    i[12]
    i["banana"] = "Banana"
    i("Banana!")
}
```

### 7.6 逻辑运算 OperatorOverloadLogic
* 功能: 重载逻辑运算符
* 介绍:
    * !in和!=是in和==与!的复合运算
    * 所有的大小比较其实都是compareTo()与0的比较
```kotlin
class OperatorOverloadLogic(var i: Int){
    operator fun contains(i:Any):Boolean{
        println("contains ${this.i} and $i")
        return false
    }
    override fun equals(other: Any?): Boolean {
        println("equals $i and $other")
        return true
    }
    operator fun compareTo(i:Any):Int{
        println("compareTo ${this.i} and $i")
        return 42
    }
}

fun main(args: Array<String>) {
    var i = OperatorOverloadLogic(450)
    println("banana" in i)
    println(i == OperatorOverloadLogic(12))
    println(i>1)
    println(i<2)
    println(i>=3)
    println(i<="Banana")
}
```

## 8 代码文档 KDoc
* 功能: 编写Kotlin代码文档
* 介绍:
    * Kotlin的代码文档KDoc和java的javaDoc区别不大.
    * 支持markdown的语法,但是现在md除了基础语法,高级功能的语法并不统一.
    * 所以并不推荐用特别炫酷的md语法去写文档,实用就可以了.
    * 生成文档还需要依赖[dokka](https://github.com/Kotlin/dokka)

```kotlin
/**
 * This is a KDoc Demo
 * *Here* you can write doc in a markdown way.
 *
 * @param  KDoc a param of class KDoc
 * @author Shawn
 */

class KDoc(var KDoc:String){
    /**
     * @property varA a property of [KDoc]
     */
    var varA = 1
    fun funA(paramA:String):String{
        /**
         * @param paramA a param of funA
         * @return return the paramA
         */
        return paramA
    }
}
```

## 9 并发

### 9.1 创建新线程 ThreadNew
* 功能: 创建新线程
* 介绍: 同java
```kotlin
class ThreadNew : Thread(){
    override fun run(){
        super.run()
        Thread.sleep(5000)
        println("Hello")
    }
}

fun main(args: Array<String>) {
    val mThread = ThreadNew()
    mThread.run()
}
```

### 9.2 实现runnable接口 ThreadRunnable
* 功能: 通过runnable接口来创建新线程
* 介绍: 同java
```kotlin
fun main(args: Array<String>) {
    val mRunnable = Runnable {
        run {
            Thread.sleep(3000)
            println("Hello")
        }
    }
    Thread(mRunnable).start()
}
```

## PLUS 小技巧

### P.1 可变长参数 TipsVarargs
* 功能: 用可变长参数来获取不定个数的参数
* 介绍: 无
```kotlin
fun tipsVarargs(vararg strings:String){
    for(s in strings){
        println(s)
    }
    for (i in 0 until strings.size){
        print(strings[i]+" ")
    }
}

fun main(args: Array<String>) {
    tipsVarargs("banana","Banana","banana","banana")
}
```

### P.2 常量 Constant
* 功能: 试用常量
* 介绍:
    * val定义运行期常量(普通常量)
    * const val定义编译期常量
    * 编译期常量不能是可变对象
    * 用by lazy可以将普通常量的初始化推迟到第一次调用的时候
```kotlin
fun main(args: Array<String>) {
    var fruit = "banana"
    val Fruit by lazy { fruit }
    println(fruit)
    fruit = "Banana"
    println(Fruit)
}
const val TipsConst = "Only primitives and String are allowed"
```

### P.3 获取class TipsGetClass
* 功能: 获得对象的class
* 介绍:
    * 用::class.java可以获取Java的class实例
    * 只用::class获取的是kotlin的class实例
    * 用实例的.javaClass也可以获取到class实例
```kotlin
class TipsGetClass

fun main(args: Array<String>) {
    val tipsGetClass = TipsGetClass()
    val cls = TipsGetClass::class.java
    val kls = TipsGetClass::class
    val tcls = tipsGetClass.javaClass
}
```

### P.4 引用相等 TipsRefEqual
* 功能: 比较传统相等(\=\=)和引用相等(\=\=\=)
* 介绍:
    * 传统的相等很传统
    * 引用相等判断两个对象的引用是否是同一个
```kotlin
fun main(args: Array<String>) {
    var a = TipsRefEqual("You")
    var b = a
    var c = a
    var d = TipsRefEqual("You")
    println(a==b)
    println(b==c)
    println(a==d)
    println(a===b)
    println(b===c)
    println(a===d)
    println(b===d)
}

class TipsRefEqual(var name:String){
    override fun equals(other: Any?): Boolean {
        return this.name==other.toString()
    }
    override fun toString(): String {
        return this.name
    }
}
```

### P.5 中缀表示法 TipsInfix
* 功能: 用infix修饰的函数可以使用中缀表示法调用
* 介绍:
    * 被修饰的函数必须是成员函数或者扩展函数
    * 被修饰的函数只能有一个参数
    * 这个参数不能是可变长参数,也不能有默认值
    * 使用中缀表示法a Bala b等同于a.Bala(b)
    * 使用中缀表示法必须指定接收者,设banana(String)是x类的infix函数:
        * 在x类内直接调用banana "Banana"是错误的
        * x类内可以调用this banana "Banana"
        * 或者调用banana("Banana")
    * 中缀表示法的优先级低于算数运算符,类型转换,rangeTo,但是高于逻辑运算符
    * 搞不懂优先级就直接用括号括起来.
```kotlin
class TipsInfix(var i: Int){
    infix fun banana(i:Int){
        println("infix banana ${this.i} and $i")
    }
}
infix fun TipsInfix.poi(i:Int){
    println("infix poi ${this.i} and $i")
}

fun main(args: Array<String>) {
    var i = TipsInfix(12)
    i banana 450
    i poi 12
}
```

### P.6 类型别名 TipsTypealias
* 功能: 给类起别名
* 介绍:
    * typealias能够给类取别名.
    * 实际使用时类型仍是原类型,不会创造新的类型.
    * 注意: 无论如何,在起别名的时候一定要写好注释,不然忘了就很容易食翔.
```kotlin
typealias StrArrayList = ArrayList<String>
typealias SAL = StrArrayList


fun main(args: Array<String>) {
    var sal = SAL()
    sal.add("banana")
    sal.add("Banana")
    var strArrayList = StrArrayList()
    strArrayList.add("str")
    strArrayList.add("Str")
    println("The class of sal: "+sal.javaClass)
    println("The class of strArrayList: "+strArrayList.javaClass)
}
```

### P.7 关键字this TipsThis
* 功能: 用this指代类
* 介绍:
    * 单用this可以指代当前位置所在的类
    * 在嵌套类时指代最近一层的嵌套类
    * 扩展函数中的this指代被扩展的类
    * this后面也可以通过加标签来指明指代的类
```kotlin
class Outside{
    var inside = Inside()
    inner class Inside{
        fun function(){
            var outside = this@Outside
            var inside = this@Inside
            var func = this
            println(outside.javaClass)
            println(inside.javaClass)
            println(func.javaClass)
        }
    }
}
fun Outside.func(){
    println(this.javaClass)
}

fun main(args: Array<String>) {
    var This = Outside()
    This.Inside().function()
    This.func()
}
```

### P.8 闭包 TipsClosure
* 功能: 用闭包沟通函数内外
* 介绍:
    * 闭包最简单的一个例子就是"函数返回一个函数"
    * 通过这种方法,闭包可以获取函数的运行环境以及属性.
```kotlin
fun TipsClosure(init: Int): (Int)->Unit{
    var i = init
    return fun(add: Int){
        i+=add
        println("here the i is: "+i)
    }
}

fun main(args: Array<String>) {
    val add = TipsClosure(42)
    add(6)
    add(6)
    add(-11)
    add(18)
}
```

### P.9 解构 TipsComponent
* 功能: 用解构来同时创建多个量
* 介绍:
    * 用数据量可以直接为解构的量进行初始化.
```kotlin
fun main(args: Array<String>) {
    val (a,b) = tipsComponent()
    println(a.toString()+b)
}

data class TipsComponent(val res1: Int, val res2: String)
fun tipsComponent():TipsComponent{
    return TipsComponent(23,"Banana")
}
```

### P.10 空安全 TipsNull
* 功能: 介绍kotlin的空安全
* 介绍:
    * 声明量时在类型后加问号既是声明可空量(String?)
    * 安全调用可空量一般有三种方法:
        * 用?.调用是安全调用,在被调用的量为空时也返回null
        * 用!!.调用的是假定非空调用,在被调用的量为空时会发起空指针异常(NPE)
        * 或者直接用条件判断(if-else)来事先决定好空量的处理方案
    * 在转换类型的时候用as?可以进行安全转换,在转换失败时返回null而不是跳异常
```kotlin
fun main(args: Array<String>) {
    val a = "banana"
    val b: String? = null
    println(a)
    println(a?.length)
    println(b)
    println(b?.length)
    try{
        val c = b!!.length
    }catch (NPE: NullPointerException){
        NPE.printStackTrace()
    }
}
```