---
layout: post
title:  php class中self,parent,this的区别，以及实例
excerpt: this可以调用本类中的方法和属性，也可以调用父类中的可以调的方法和属性;self可以访问本类中的静态属性和静态方法，可以访问父类中的静态属性和静态方法;parent可以访问父类中的静态属性和静态方法。
published: true
---

一，this

1，要用this，你必有是一个对像的形势，不然它会报错的，Fatal error: Using $this when not in object context。
2，this可以调用本类中的方法和属性，也可以调用父类中的可以调的方法和属性

二，self

1，self可以访问本类中的静态属性和静态方法，可以访问父类中的静态属性和静态方法。
2，用self时，可以不用实例化的

三，parent

1，parent可以访问父类中的静态属性和静态方法。
2，用parent时，可以不用实例化的

四. 实例

{% highlight ruby %}
<?php 
     
    class test{ 
     public $public; 
     private $private; 
     protected $protected; 
     static $instance; 
     static $good = 'tankzhang <br>'; 
     public $tank = 'zhangying <br>'; 
     
     public  function __construct(){ 
     $this->public    = 'public     <br>'; 
     $this->private   = 'private    <br>'; 
     $this->protected = 'protected  <br>'; 
     
     } 
     public function tank(){                          //私有方法不能继承，换成public,protected 
     if (!isset(self::$instance[get_class()])) 
     { 
     $c = get_class(); 
     self::$instance = new $c; 
     } 
     return self::$instance; 
     }     
     
     public function pub_function() { 
     echo "you request public function<br>"; 
     echo $this->public; 
     } 
     protected  function pro_function(){ 
     echo "you request protected function<br>"; 
     echo $this->protected; 
     } 
     private function pri_function(){ 
     echo "you request private function<br>"; 
     echo $this->private; 
     } 
     static function sta_function(){ 
     echo "you request static function<br>"; 
     } 
    } 
     
    class test1 extends test{ 
     
     static $love = "tank <br>"; 
     private $aaaaaaa = "ying <br>"; 
     
     public function __construct(){ 
     parent::tank(); 
     parent::__construct(); 
     } 
     public function tank(){ 
     echo $this->public; 
     echo $this->protected; 
     echo $this->aaaaaaa; 
     $this->pro_function(); 
     } 
     
     public  function test1_function(){ 
     echo self::$love; 
     echo self::$good; 
     echo parent::$good; 
     echo parent::$tank;   //Fatal error: Access to undeclared static property: test::$tank 
     echo self::$tank;     //Fatal error: Access to undeclared static property: test::$tank 
     } 
     static function extends_function(){ 
     parent::sta_function(); 
     self::pro_function(); 
     echo "you request extends_private function<br>"; 
     } 
    } 
     
    error_reporting(E_ALL); 
    $test = new test1(); 
    $test->tank();            //子类和父类有相同名字的属性和方法，实例化子类时，会调用子类中的方法。 
    test1::test1_function(); 
    test1::extends_function();  //执行一部分后，报Fatal error: Using $this when not in object context in D:\xampp\htdocs\mytest\www4.php on line 32 
    ?>  
{% endhighlight %}

1，当我们调用$test->tank();这个方法时，tank里面的$this是一个对像，这个对像可以调用本类，父类中的方法和属性，

2，test1::test1_function();当我们用静态的方法去调用非静态方法时，会显示警告的，Non-static method test::test1_function() should not be called statically可以看出不，self可以调用本类，父类中的静态属性，parent可以调用父类中的静态属性，二者调用非静态属性会报错。代码中有注释

3，test1::extends_function();这一步会报错，报在非对像中使用$this。为什么会这样呢，test1::extends_function();只是调用了class中的一个方法，并没有实例化，所以根本不存在什么对像，当父类中用到$this时，就会报错
