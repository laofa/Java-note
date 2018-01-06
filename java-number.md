## java数据类型和数据封装对象的一些笔记
#### 1.好奇出发点
  这次让我有兴趣写这个笔记的原因是自己在写一个java项目的时候，我需要将字符串类型的数据转换为整数，浮点数和科学计数的时候发现int和double类型可以
选用的函数竟然都有两个，分别是Integer.parseInt(String s),Integer.valueOf(String s)和Double.parseDouble(String s)和Double.valueOf(String s)
这两个函数，所以就很好奇这两种转换的函数有什么区别，仔细查看资料和阅读源码(IDEA无敌)才发现他们的返回值是不同的类型，我们看源码：  
```
public static double parseDouble(String s) throws NumberFormatException {  
    return FloatingDecimal.readJavaFormatString(s).doubleValue();  
}  

public static Double valueOf(String s) throws NumberFormatException {  
    return new Double(FloatingDecimal.readJavaFormatString(s).doubleValue());  
}  
```
  可以看出来parseDouble返回的值是一个基本数据类型double，然而valueOf返回的值是一个封装对象Double，Integer的转换函数也是类似的。正如我刚才描述的
那样子可以看出来基本数据类型在java里面还有一层对象封装，这些都有：  
boolean Boolean  
char Character  
byte Byte  
short Short   
int Integer  
long Long  
float Float  
我们仔细阅读源码和查相关的文档就可以知道里面的区别，举个例子：  
Integer是int的封装类，里面有很多进行处理的静态方法  
Integer是对象而int不是，内存的分配位置也不一样  

int是一种基本数据类型，而Integer是相应于int的类类型，称为对象包装。  
实现这种对象包装的目的主要是因为类能够提供必要的方法，用于实现基本数据类型的数值与可打印字符串之间的转换，以及一些其他的实用程序方法；另外，
有些数据结构库类只能操作对象，而不支持基本数据类型的变量，包装类提供一种便利的方式，能够把基本数据类型转换成等价的对象，从而可以利用数据结构
库类进行处理。

#### 2.数据类型转换测试  
```
import java.math.BigDecimal;

/**
 * Created by laofa on 2017/12/18.
 */
public class FuncTest {
    public FuncTest(){}

    public static void main(String[] args) {

        String s1 = "0.120";
        String s2 = "12";
        String s3 = "1.2e+14";

        double parseDouble = Double.parseDouble(s1);
        double valueOf1 = Double.valueOf(s1);
        int parseInteger = Integer.parseInt(s2);
        int valueOf2 = Integer.valueOf(s2);
        BigDecimal bigDecimal = new BigDecimal(s3);

        System.out.println("parseDouble : " + parseDouble);
        System.out.println("valueOf1 : " + valueOf1);
        System.out.println("parseInteger : " + parseInteger);
        System.out.println("valueOf2 : " + valueOf2);
        System.out.println("bigDecimal : " + bigDecimal.toString());
        System.out.println("bigDecimal : " + bigDecimal.toEngineeringString());
        System.out.println("bigDecimal : " + bigDecimal.toPlainString());
    }
}
```
输出结果为：
```
parseDouble : 0.12
valueOf1 : 0.12
parseInteger : 12
valueOf2 : 12
bigDecimal : 1.2E+14
bigDecimal : 120E+12
bigDecimal : 120000000000000
```
从结果我们可以得到几个结论：  
a.Double.parseDouble()和Double.valueOf()参数都是字符串，返回的结果打印出来都是double类型  
b.查资料后我们发现a结论可以参考：double和Double两种类型在JDK1.5以后的版本可以自由的转换，便于使用静态函数  
c.BigDecimal的toString()的三个方法输出结果的区别是：toString()有必要时使用科学计数法，toEngineeringString()3的倍数的科学技术，toPlainString()不用科学计数法  
#### 3.判断一个字符是不是数字
```
Character.isDigit(string.charAt(index))
>>return true or false 
```
