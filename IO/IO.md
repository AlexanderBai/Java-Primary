## 一、I/O文件对象

文件夹和文件都是用File表示

####1、创建一个文件对象

使用相对路径和绝对路径创建文件对象

> ①相对路径创建文件
>
> ```java
> package testfile;
> 
> import java.io.File;
> 
> /**
>  * @Author AlexanderBai
>  * @data 2019/3/13 20:09
>  */
> public class TestFile {
>     public static void main(String[] args) {
>         File file=new File("test");
>         File file1 = new File("demo/d");
>         if (!file.exists()) {
>             System.out.println(file.mkdir());//创建由此抽象路径名命名的目录
>         }else {
>             System.out.println("file.delete() = " + file.delete());
>         }
> 
>         if (!file1.exists()) {
>             //创建由此抽象路径名命名的目录，包括任何必需但不存在的父目录
>             System.out.println("file1.mkdirs() = " + file1.mkdirs());
>         }else{
>             System.out.println("file1.delete() = " + file1.delete());
>         }
>     }
> }
> 
> ```
>
> 





②绝对路径创建文件

> ```
> 
> ```
>
> 

####2、文件常用方法1

####3、文件常用方法2

####4、遍历文件夹

####5、遍历子文件夹