//闭包理解
/* * javascript闭包 * 假设实现一个计数器 * */ //第一种方法 
var counter = 0; 
function add() { 
return ++counter;//计数器加1 } 
add();//counter为1 
add();//counter为2 
//但是这样的问题是其它函数也可以修改counter的值，因为counter是全局变量 
//第二种方法 
function add2() { 
var counter2 = 0;//定义局部变量counter2 
return ++counter2;//计数器加1 
} 
add2();//counter2为1 
add2();//counter2为1 
//可是这样每次调用都是counter的值都是1，这就有点尴尬了 
//那么其实闭包就可以很好地解决这个问题，什么事闭包？ 
//通俗点说闭包就是函数内部又定义了函数，并且定义的子函数又使用了其父函数作用域的变量
//第三种方法 
function add3() { 
var counter3 = 0;//定义计数器 
return function()//定义闭包函数 
{ return ++counter3;//计数器加1 
} 
} 
var raise = add3();//外部接收闭包函数 
raise();//counter3为1 
raise();//counter3为2 
//这样只有raise能够改变计数器counter3的值了 
//不但实现了功能，而且对counter3这种私有变量（不能被外部访问）实现了很好地封装 
//这就是闭包
