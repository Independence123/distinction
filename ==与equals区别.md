摘自CSDN 博主 <a href="http://blog.csdn.net/xcysuccess3/article/details/6557771 ">原文链接</a>

//综合各类信息，个人认为该博主对== 与equals区别阐述比较全面，并且结合代码进行分析，很适合像本人这样基础薄弱的同学学习，因此对其作品进行引用
//不足之处还请老师不吝指教


# distinction
homework 2

public class EqualTest { 
public static void main(String[] args) { 

    //对于基本类型的变量"=="和"equal"的区别 
    int t1=57; 
    int t2=67; 
    int t3=124; 
    int t4=124; 
     
    //“==”对于基本数据类型，判断两个变量的值是否相等。 
    Boolean result1=(t1==t2); 
    Boolean result2=((t1+t2)==t3); 
    Boolean result3=(t3==t4); 
     
    System.out.println("/n/n-----【t1==t2】"+result1+"/n-----【(t1+t2)=t3】"+result2+"/n-----【t3=t4】"+result3); 
    //“equal”不能用于基本数据类型。只能用于类变量。对于基本数据类型要用其包装类。 
    Integer i1=new Integer(t1); 
    Integer i2=new Integer(t2); 
    Integer i3=new Integer(t3); 
    Integer i4=new Integer(t4); 
     
     
    Boolean ri1=i1.equals(i2); 
    Boolean ri2=i3.equals(i1+i2); 
    Boolean ri3=i3.equals(i4); 
     
    System.out.println("/n/n-----【i1.equals(i2)】"+ri1+"/n-----【i3.equals(i1+i2)】"+ri2+"/n-----【i3.equals(i4)】"+ri3); 
    
     //对于对象变量，"=="和"equal"的区别 
    String st1="wasiker "; 
    String st2="is super man"; 
    String st3="wasiker is super man"; 
    String st4="wasiker is super man"; 
     
    Boolean b1=(st1==st2); 
    Boolean b2=(st1+st2)==st3; 
    Boolean b3=(st3==st4); 
     
    System.out.println("/n/n-----【st1==st2】"+b1+"/n-----【(st1+st2)==st3】"+b2+"/n-----【st3==st4】"+b3); 

//因为对象变量的存储的是对象在内存中的路径，即内存地址。所以用“==”比较时，即使 
//对象的值相等，但是他们的内存地址不同，所以==的结果为false。故“==”用于比较两 
//个变量的值是否相等，而不是变量引用的对象是否相等 

    Boolean r1=st1.equals(st2); 
    Boolean r2=(st1+st2).equals(st3); 
    Boolean r3=st3.equals(st4); 
     
    System.out.println("/n/n-----【st1.equals(st2)】"+r1+"/n-----【(st1+st2).equals(st3)】"+r2+"/n-----【st3.equals(st4)】"+r3); 

//equal用于比较两个对象是否相同。 
} 
} 
运行结果为： 
-----【t1==t2】false 
-----【(t1+t2)=t3】true 
-----【t3=t4】true 

-----【i1.equals(i2)】false 
-----【i3.equals(i1+i2)】true 
-----【i3.equals(i4)】true 

-----【st1==st2】false 
-----【(st1+st2)==st3】false 
-----【st3==st4】true 

-----【st1.equals(st2)】false 
-----【(st1+st2).equals(st3)】true 
-----【st3.equals(st4)】true 

总之： 
“==”比较的是值【变量(栈)内存中存放的对象的(堆)内存地址】 
equal用于比较两个对象的值是否相同【不是比地址】 

【特别注意】Object类中的equals方法和“==”是一样的，没有区别，而String类，Integer类等等一些类，是重写了equals方法，才使得equals和“==不同”，所以，当自己创建类时，自动继承了Object的equals方法，要想实现不同的等于比较，必须重写equals方法。

"=="比"equal"运行速度快,因为"=="只是比较引用.
