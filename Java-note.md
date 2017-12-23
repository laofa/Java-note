## A.命名规范
#### 1.项目名全部小写  
#### 2.包名全部小写  
#### 3.类名首字母大写，多个单词的每个单词首字母都要大写,如：  
```
public class MyFirstClass{}
```  
#### 4.变量名，方法名首字母小写，多个单词的后面每个单词首字母大写，如：  
 ```
int index = 0;  
public void toString(){}  
```
#### 5.常量名全部大写，如：  
```
public static final int NON_TAG = 0
```
#### 6.命名详细规则  
a.名字只能由字母，数字，下划线，$符号组成  
b.不能以数字开头  
c.名称不能够是JAVA中的关键字  
d.坚决不要出现中文及拼音命名  

## B.注释规范
#### 1.类注释  
每个类的前面必须加上类注释，模板如下：  
```
/**  
 * 类详细说明  
 *  
 *  
 * @author [Faming Wu]  
 * @version 1.00 (Last update: 2017/11/21)  
 */
 ```
#### 2.方法注释
每个方法前面必须加上方法注释，模板如下：  
```
/**  
 * 构造方法详细说明  
 *  
 *  
 * @para 参数的使用说明  
 * @return 返回结果说明  
 * @throws 异常类型，抛出异常说明  
 */
```
#### 3.方法内部注释
内部方法的注释单行或者多行根据情况而定,如：  
```
// 输入的表达式  
String myInput = input  
```

## C.源文件创建规则
#### 1.一个源文件中只能有一个public类
#### 2.一个源文件可以有多个非public类
#### 3.源文件的名称应该和public类名保持一致
如：源文件中public类的名称是Scanner，那么源文件命名为Scanner.java
#### 4.如果一个类定义在某个包中，那么package的语句应该放在源文件的首行
#### 5.如果源文件中包含import语句，那么应该放在package语句和类定义之间
#### 6.import语句和package语句对源文件中定义的所有类都有效，不能给不同的类不同的包声明

## D.IDEA和eclipse的区别
![difference](https://github.com/laofa/Java-note/blob/master/IDEAandECLIPSE.png)

## E.一些语法笔记
#### 1.键盘输入数据
```
// 从命令行得到信息
Scannersc=newScanner(System.in);  
System.out.println("Pleaseinputyoursalary:");  
doubleyourSalary=sc.nextDouble();  
````
#### 2.bat脚本写法（第三种）
```
@echo off  
    java -jar SocketAdapter.jar  
@pause  
```
来自<http://blog.csdn.net/futuredream2008/article/details/17142665> 
#### 4.Abstract类是抽象类，所有的方法不能实现,继承abstract必须实现所有的方法
#### 5.Alt+insert自动补充get和set函数
#### 6.super关键字用来引用父类的内容,子类的继续用this

