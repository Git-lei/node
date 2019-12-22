# JavaScript:

JavaScript是一种小型的、轻量级的、面向对象的、跨平台的客户端脚本语言。

是嵌入到浏览器软件当中去的。

## \1.    核心（ECMAscript）描述了该语言的语法和基本对象。

## \2.    文档对象模型（DOM）描述了与网页进行交互的对象和接口。

## \3.    浏览器对模型（BOM）描述与浏览器进行交互的对象和接口。

## \4.    作用：控制web前端标准的前两者：结构和样式；给网页添加一些功能、动画特效、交互；对数据进行验证。

## \5.    参数定义：

函数小括号里面填写的值称之为函数的参数；初学阶段参数用引号引起来（建议单引号）,参数之间用逗号隔开。

## \6.    书写规范：

js代码要放在script标签中，并且要在页面最后位置。

## \7.    目的：用js去做CSS和HTML的工作，起操控作用。

## \8.    文档对象：

定义：document在js中代表文档对象；对象就是一堆功能（函数，方法）的集合体。

搜索函数：

通过document.getElementById()来实现在页面中寻找元素。

## \9.    变量：

变量就是一个容器，内部可以储存任何的数据，用变量的目的是减少代码量，让代码看起来更简洁。

声明变量：

var 变量名称，然后通过等号给变量赋值。

变量名称可以自定义，但不能与JS自带的命名冲突，且不能用数字开头。

## \10.  命名规范：

一般使用驼峰命名法（第一个单词首字母小写，之后每个字母首字母大写）

## \11.  JS控制HTML：

控制HTML标签，理论上我们可以通过“点”语法，访问标签上的任意属性，属性名和标签的属性名一致，只有class例外用className访问。

控制HTML内容：innerHTML = ‘内容’;

## \12.  事件的定义：

当什么时候做什么事。

事件作用：

可以捕获用户的行为。

事件三要素：

##### （1）    事件源：就是这个事件加给谁。

##### （2）    事件类型：就是指这个事件是什么时候发生的。

##### （3）    执行的指令：匿名方法function(){命令行}

使用时间的基本结构：事件源 . 事件类型 = 匿名函数（匿名方法）

 

事件类型：

##### onclick：表示鼠标单击时触发。

##### ondblclick：表示鼠标双击时触发。

##### onmouseover：表示鼠标移入的时候触发。

##### onmouseout：表示鼠标移出的时候触发。

事件的一个小特点：在JS中以on开头。

## \13.  border设置none和0的区别：

none代表不设置相对应的边框属性。

0代表把边框属性设置为0（看不到，但是存在）。

设置属性为none会让程序运行更快。

## \14.  JS设置CSS的复合属性中的其中一个，只需定义要修改的属性即可。

## \15.  JS的书写位置：

（1）    内嵌JS：可以写在一对script标签里。

（2）    外链JS：可以在单独的JS文件里，通过script标签引用到页面中。

（3）    行内JS：还可以写在标签的属性里，这个属性必须是时间属性。（任何标签都有时间属性）

注意：对于初学者来说，JS的执行顺序是由上至下的。

## \16.  变量的类型：

### （1）number  数字类型，可带小数点可不带

### （2）string   字符串类型

### （3）undefined   undefined类型，变量未定义时的值，这个值自己是一种类型。

### （4）boolean    布尔类型，仅有两个值true和false，if语句中有大用处

### （5）null        null类型，这个值自己是一种类型。

undefined表示变量不含有值

可以通过将变量的值设置为null来清空变量。

 

### typeof关键字：

检测数据的变量类型。

 

###    声明变量类型：

​    当声明新变量时，可以使用关键词”new”来声明其类型：

​    var carname = new String;

​    var x = new Number;

​    var y = new Boolean;

​    var cars = new Array;

​    var person = new Object;

 

###     JS算数运算符：

 可通过小括号来改变计算先后顺序，注意没有中括号和大括号，一律用小括号：

var a = 4 * (3 +(1 + 2) * 3);

alert(a);

 乘方如3的4次方的算法：

Math.pow(3,4);

  var a = Math.pow(3,2+Math.pow(3,6));

 根号就是：

var a = Math.sqrt(81);

 

数字运算的隐式转换：所有带字符串的运算都会尽可能地转为数字进行计算，加号特殊，数字与字符串做加法运算会被看做连字符。

数字运算中，只有纯数字字符串、布尔值、null能够帮你进行隐式转换。

console.log(3 * **null**); //0  隐式转换的时候**null****将被转为****0**

console.log(3 * **false**); //0 隐式转换的时候**false****将被转为****0**

console.log(3 * **true**);  //3 隐式转换的时候**true****将被转为****1**

不纯的字符串和undefined是不能帮你进行隐式转换的，结果都是NaN。

console.log(3 * **"8****天****"**); //NaN 数学运算中，不纯的字符串没法隐式转换

console.log(3 * **undefined**); //NaN 数学运算中，undefined不能进行隐式转换

总结：

不论哪种运算，只要出现了undefined参与，结果都是NaN

“4”、false、true、null都能进行隐式转换。

加号比较特殊，面对”4”没有隐式转换。

面对特殊数值的计算，有如下例子：

1   Infinity + 1000  //Infinity

2   Infinity - 1000 //Infinity

3   Infinity / 1000 //Infinity 

4   Infinity - Infinity //NaN

5   Infinity /Infinity //NaN

6   Infinity * Infinity //Infinity

7   0 / 0       //NaN

8   6 / 0       //Infinity

9      NaN / 8       //NaN

 

###     JS赋值运算符：

  

赋值运算的参与者一定是变量。

var a = 1;

a += 2;          //相当于a=a+2

console.log(a);     //3

 

var b = 6;

b /= 3;         //相当于b=b/3

console.log(b);   //2

 

### 关系运算符：

​    比较和逻辑运算符用于测试true或false。

​      

关系运算符的正统，number和number进行数学运算，得到的答案为boolean。

console.log(8>5);   //true

console.log(7<4);     //false

boolean类型只有两个值：true和false，表示真和假。

关系运算中等于运算（==）会进行隐式转换。

### 非正统运算：

####     （1）string和string进行关系运算：

1   "a" < "b" //true

2   "A" < "B" //true

3   "A" < "a" // true ，大写字母在字符集里面是在小写字母前面

4   "1" < "A" //true ，数字在字母前端

5   "blank" < "blue" //true  因为一位一位比，直到比出大小

6      "25678" < "3"  //true 因为是string和string比，比的是字符编码顺序

### 逻辑运算符：

#### （1）  与数字进行关系运算时，纯数字字符串被转为数字，null转换为0，true为1，false为0，null不能和0进行相等判定：

 

null < 0.00001 //true

null > -0.0001 //true

null == 0 //false 具体原因，我们后面讲解Object的时候介绍

false == 0 //true

true == 1 //true

#### （2）  NaN不等于自己，不全等于自己：

NaN == NaN //false

NaN === NaN //false

NaN != NaN //true

NaN !== NaN //true

#### （3）  string和number比，string会被隐式转换为number：

"25" < 3  //false

注意：不能连续使用关系运算符，当多个关系运算符在同一个算式中还是由从左向右进行计算的，就会导致前面计算的boolean值参与之后的比较产生错误。

 

逻辑运算符：

  

正统来说，参与逻辑运算的是boolean和boolean，得到的结果也是boolean。

多个逻辑运算符在同一算式中运算顺序为非>与>或。

短路语法：

如果计算一个&&运算的时候，比如a&&b，如果a是false，那么就不会管b是什么，直接输出false，等于说直接输出a。

如果计算一个&&运算的时候，比如a&&b，如果a是true，那么不用管b是什么，直接把b当做结果输出。

也就是说，本质上计算机进行a&&b运算的时候，不是进行逻辑分析，如果a是负性的直接扔出a；如果a是正性的，直接扔出b。

负性的：false,null,0,NaN,空字符串（””），undefined

正性的：除了以上的全是。

false && 8   //false 因为计算机发现，且运算a已经是false了，直接输出false

null && 8  //null 因为计算机发现，且运算a已经是false性的了，直接扔出来null

true && 13  //13  因为计算机发现，且运算a是true，所以总结果就是看b，直接扔出b

12 && 13  //13  因为计算机发现，12当做true，所以总结果看b，直接扔出b

13 && 12  //12  因为计算机发现，13当做true，所以总结果看b，直接扔出b

undefined && 哈哈 //undefined 不报错，因为a已经是负性的了，所以直接扔出a，哈哈不管

哈哈 && undefined //报错

true && NaN  //NaN 扔后面

 

||逻辑或的短路运算类似，a||b

计算机发现a是真，那么扔a；如果a是假则扔b。

0 || 18  //18 前面假，扔后面

18 || 0  //18 前面真，扔前面

undefined || NaN  //NaN 前面假，扔后面

NaN || undefined  //undefined 前面假，扔后面

 

条件运算符：

语法：variablename=(condition)?value1:value2

例子：greeting=(visitor==”PRES”)?”Dear President”:”Dear”;

总结：

a&&b，计算机要么执行a要么执行b。a真则执行b，a假则执行a。

a||b，计算机要么执行a，要么执行b。a真执行a，a假执行b。

 

运算符的计算顺序：贴身的（++、--、！）>数学>比较>逻辑>赋值

有一个Boolean公式简化运算：

(a && b) || (a && c)=a && (b || c)

 

三元运算符：

唯一：条件 ? val1 : val2;

表达式的值看条件的结果，如果条件是true那么表达式的值是val1，如果条件是false那么表达式的值是val2。

 

 

## \17.  var关键字：

对变量进行声明，且可在var中声明多个变量（用逗号隔开）并赋值。

## \18.  prompt语句：

prompt用于弹出一个输入框来让用户输入，基本语法如下：

prompt(“提示文本”,”默认值”); 默认值可省略，可以将用户输入的值存入变量：

var a = prompt(“请输入你的电话”,”139”);

alert(“哈哈，你输入的电话是”+a);

用prompt接收的任何东西都是字符串，哪怕用户输入了一个数字，也是字符串的数字。

## \19.  类型转换：

有一些方法可以将内存中表示一个数字的字符串转换为对应的数字：

parseInt()和parseFloat()。

parseInt就是将一个string转为一个整数，不四舍五入，直接截取整数部分。如果这个string有乱七八糟的东西，那么就截取前面数字的部分。

var a = “123”;

var b = parseInt(a);

console.log(b);

console.log(typeof b);

  

例如这种输出的也是123：

parseInt(“123年11月”);

parseInt()不仅仅能够进行整数转换，还能进行尽职转换：把任何进制的数字都换为10进制。进制和要转换的字符串要用逗号隔开。

如下列运算的结果均为15：

parseInt(15,10)

parseInt(17,8)

parseInt(1111,2)

parseInt("0xf",16)

parseInt("f",16)

parseInt(16,9)

parseInt("15e6",10)

parseInt("15*6",10)

如果parseInt()不能转换，则返回NaN

得到NaN的方法又多了一种，之前是6/0得到Infinite。0/0得到NaN。

 

parseFloat就是将字符串转为浮点数，尽可能地将一个字符串转换为浮点数，如果浮点数之后又乱七八糟的内容直接舍弃。

var a = “123.67.88”;

var b = parseFloat(a);

console.log(b);

结果为123.67

同时可以得出，数字类型都是number，不分整数和浮点数，但是进行转换时是分的。

 

number→string：

将一个数字，与一个空字符串进行连字符计算，这样就可以将number类型转为string类型：

var a = 123;

var b =a + “”;

console.log(b);

console.log(typeof b);

  

 

## \20.  条件分支语句：

（1）    if语句：

如果...否则... ，让程序出现分支。 语法：

if(测试表达式){

​    测试表达式为真执行的语句;

}else{

​    测试表达式为假执行的语句；

}

其中可以没有else部分。

 

多分支的if，语法如下：

if(测试表达式1){

  测试表达式1为真的时候做的事情

}else if(测试表达式2){

  测试表达式1为假，且测试表达式2为真的时候做的事情

}else if(测试表达式3){

  测试表达式1为假，测试表达式2为假，且测试表达式3为真的时候做的事情

}

……

嵌套中else只能有一个。else if可以有多个。

（2）  switch case语句：

语法：

  **switch**(待检测值){

  **case** 值1 :

​    值1 与 待检测值 相同时做的事情

​    **break**;

  **case** 值2 :

​    值2 与 待检测值 相同时做的事情

​    **break**;

  **case** 值3 :

​    值3 与 待检测值 相同时做的事情

​    **break**;

  **default** :

​    默认要做的

​      **break**;

}

值得注意的是switch进行相同判断用的是“===”，会连类型一同比较。

如果不写break，那么switch语句除了会执行这个case里面的语句之外，还会无条件地执行下面的case语句，知道break拦截。

（3）    三元运算符：

唯一：条件 ? val1 : val2;

表达式的值看条件的结果，如果条件是true那么表达式的值是val1，如果条件是false那么表达式的值是val2。

 

## \21.  循环语句：

（1）    for循环语句：

  

系统遇见for循环结构，会先执行语句1，此时声明了一个变量i，赋值为1.

系统会立即检测是否满足2表达式的值，如果是真的执行3，如果是假的则跳出循环执行5。

执行完3后会立即执行语句4，然后再次检测语句2，如果为真则做3，为假则做5，以此循环。

注意：如果循环变量在循环外已经定义了，那么就不需要在1号位上重新定义，写一个空的 ; 即可。

break：

在for循环中如果遇到了break语句，那么这个循环就会立即终止，不再进行迭代。break只能跳出当前所在的最内层的循环。如果这个break想终止所有循环，JS中允许给循环语句加label，即直接在最内层加入 break labelName; 即可。

continue：

遇到continue语句，for会立即终止后面的语句，进入下一次迭代。同样continue只能用于最内层的for循环，用于外层for要加label。

（2）    do while语句：

语法：

do {

  语句1

}while(条件表达式2)

程序开始就会执行一次1，然后验证2是否为真，如果是真，继续执行1。

这是一个后置验证语句，无论如何都会执行一次。

若验证条件恒为true，那么这就是一个死循环。

do...while语句中没有循环变量，适合没有循环变量的情况，经常用来写死循环。

（3）    while语句：

while语句是一个前置验证语句，其余和do...while一样

由于没有循环变量，和do...while一样经常用于做死循环。

## \22.  随机数Math.random()

能够产生（0,1）的一个数字，若想产生在[a,b]之间的随机数，公式如下：

parseInt(Math.random()*(b-a+1))+a;

## \23.  数组：数组是一个有序的数据集合。

var arr = [16,33,23,12,53];

数组的字面量就是方括号，这是定义数组最简单的方式。

变量arr就是一个数组变量，里面存储的不是一个数字，而是一组数。可以使用下标或索引值index来精确访问数组中的某一个项，下标从0开始。

console.log(arr[0]);        //输出16

数组中并不规定保存相同类型的项，但实际应用中还是将相同类型的保存在其中。

数组有一个length属性来表示这个数组的项的个数，如刚才那个数组有：

alert(arr.length);      //数组里面一共有5项

数组有几项就会弹出几。数组最后一项的下标就是length-1，即数组最大下标为length-1，尝试比length-1还要大的下标得到的输出就是undefined。

arr[arr.length-1];

 

数组的遍历：

数组里面放的是一组数，我们经常使用for循环来对数组中的元素进行操作等：

for(var i = 0; i <= arr.length; i++){

​    对arr[i]进行操作、判断等;

}

 

数组是一个引用类型：

用typeof arr来检测，会发现数组输出object，因此数组是对象。

保存数组的变量，实际上保存的是数组的内存地址。

如果a里面存储的是基本类型，那么语句b = a 就是把a的值赋值一份给b，相当于复制。如果a里面存储的是引用类型，b将指向a的内存地址，此时a、b都是指向同一个内存地址。

 

数组的常见方法：

  

数组的头尾操作pop()、push()、shift()、unshift()

push()方法就是在数组末尾添加一个或多个项目：

var arr = ["东","西","南","北"];

arr.push("中","发","白");  //在数组最后添加项

console.log(arr);

  

pop()方法是删除数组的最后一项，只能删除最后一项，不能删除多项，能返回被删除的元素。

push()的返回值是数组的新长度。

pop()的返回值是数组删除的元素。

shift()的返回值也是删除的元素。

unshift()的返回值也是数组的新长度

push()尾部插入、pop()尾部删除、unshift()头部插入、shift()头部删除

数组的合并与拆分concat()、slice()

concat()方法用于合并两个数组：

var arr1 = ["东","西","南","北"];

var arr2 = ["一条","二条"];

arr1.concat(arr2);  //这里有一个超级大坑，concat是把arr1和arr2合并为一个新数组返回

console.log(arr1);  //不变

因此必须用arr1 = concat(arr2);才可以将arr1变为合并后的数组。

concat()的参数非常灵活，可以是数组变量、数组字面量、散的值也可以。

concat()拼接数组，返回新数组，不会对原数组产生影响。

slice()方法可以从已有的数组中返回选定的元素。arr.slice(start,end);

var arr = ["东","西","南","北","中","发","白"];

var arr2 = arr.slice(1,4); //截取下标为1、2、3的为一个新数组返回

console.log(arr2);  //["西", "南", "北"]

arr.slice(start,end)返回一个新的数组，包含从start到end（不包括end）的元素。若只给出start则会截取从start往后所有元素。slice(a,b)取出b-a项。

start和end可以为负值，此时就是指倒数。

多功能splice()插入、删除、替换：

首先，一旦应用splice()方法，arr立即改变，不需要重新复制，即这个方法不返回新的数组。

若arr.splice(3,2);指的是从下标为3的元素开始删除2个元素，开始下标可以为负值，那么就是倒数，注意倒数的时候没有0。

var arr = ["A","B","C",**"D","E"**,"F","G"];

arr.splice(3,2,"X","Y","Z","思密达"); //从数组下标为3开始这项，连数2项，改为……

  

// ***************插入一些项 ***************

var arr = ["A","B","C","D","E","F","G"];

arr.splice(2,**0**,"嘻嘻","哈哈");    /**/****插入到下标为****2****的项前，不删除项目**

console.log(arr);

console.log(arr);

  

splice依据参数的多少和参数是什么，会出现不同的功能。

删除数组最后8项：

arr.splice(-8);

逆序reverse():

reverse()方法就是立即让数组倒置：

var arr = ["A","B","C","D","E","F","G"];

**arr.reverse();  //****不需要赋值**

console.log(arr); //["G", "F", "E", "D", "C", "B", "A"]

  

排序sort()：

sort()方法排序：

var arr = ["G","A","C","B","I","H","G","I","B"];

**arr.sort();**

console.log(arr);

  

sort函数默认是按照字符顺序排列的，隐式将数字转为string，并通过比较字符编码顺序来排序。

sort()里面有一个参数，这个参数是一个函数：

arr.sort(function(a,b){

​      //如果a要放在b前面，那么返回负数

​      //如果a要放在b后面，那么返回正数

​      //如果a和b不区分大小，那么返回0

​      if(a < b){

​       return -1;

​      }else if(a > b){

​       return 1;

​      }else if(a == b){

​       return 0;

​      }

  });

如果想让数组从小到大排列：

 arr.sort(function(a,b){

  return a-b;

});

从大到小就改变return中a、b的位置即可。

转为字符串：

arr.join(分隔符);方法可将数组转化为字符串形式，不写分隔符默认是用逗号分隔，如果什么都不想要在分隔符出写一个空的字符串（’’）即可。

数组的创建：

var cars = new Array();

cars[0] = “Audi”;

cars[1] = “BMW”;

cars[2] = “Volvo”;

或者:

var cars = new Array(“Audi”,”BMW”,”Volvo”);

或者:

var cars = [“Audi”,”BMW”,”Volvo”];

数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。

## \24.  字符串的常见属性和方法：

属性length就是字符串的长度。

中文、数字、英文字母、空格，都是一个长度。

常见方法：

charAt();用于返回在指定位置的字符。

‘abcdef’.charAt(0);    //’a’

和数组下标类似

var str = ‘abcdefg’;

for(var i = 0; i <= str.length; i++) {

​        console.log(str.charAt(i));

}

​    concat()连接字符串

indexOf()检索字符串

​    ‘我爱你亲爱的祖国的人民币’.indexOf(‘的’);    //5

​    replace()替换：

​    ‘abcdefgaa’.replace(‘a’,’0’);        //’0abcedfgaa’

​    slice()提取：

​    ‘我爱你亲爱的祖国的人民币’.slice(-3,-1);        //人民

​    split()把字符串转换为数组，参数就是拆分的地方

​    ‘我爱你亲爱的祖国的人民币’.split(‘的’);

  

​    substr()截取字串：

​    ‘abcdefghijklmn’.substr(3,5);    从下标为3的地方开始取5个字符。

  

substring()截取子串：

‘abcdefghijklmn’.substring(3,5);  从下标为3的地方截取到下标为5的地方的字符，不包括5

toLowerCase()、toUpperCase();转换大小写

## \25.  对象:

JS中所有的事物都是对象：字符串、数字、数组、日期等等，在JS中，对象是拥有属性和方法的数据。

JS对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式(name:value)来定义。属性由逗号分隔：

var person = {firstname:”Bill”,lastname:”Gates”,id:5566};

上面例子中的对象（person）有三个属性：firstname、lastname、以及id。

对象属性的寻址方式：

name = person.lastname;

name = person[“lastname”];

 

属性和方法：

属性是与对象相关的值；方法是能够在对象上执行的动作。

实例：

person = new Object();

person.firstname = ”Bill”;

person.lastname = ”Gates”;

person.age = 56;

person.eyecolor = “blue”;

## \26.  访问对象的方法：

可通过下面的语法调用方法：

 objectName.methodName()

 

这个例子使用String对象的toUpperCase()方法来把文本转换为大写：

var message = “Hello world”;

var x=message.toUpperCase();

console.log(x);

输出结果为HELLO WORLD

## \27.  JS函数：

函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。

JS函数语法：

函数就是包裹在花括号中的代码块，前面使用了关键词function来定义：

function functionname() 

{

执行的代码

}

可在某事件发生时直接调用函数，并且可由JS在任何位置进行调用。

调用函数直接用   函数名();  即可。

当大量程序相同时，可直接封装一个函数function，这样只调用一次就能执行很多语句。

 

函数的参数：

定义函数时，内部语句可能有一些变量，这些变量我们要求在定义的时候罗列在小括号中。调用的时候要把这个变量的真实的值写在括号里，这样随着函数的调用这个值也传递给了a。罗列在function小括号中的参数我们称为形参；调用时传递的数值我们称为实参。

  

参数可以有很多个，用逗号隔开即可。

若定义函数的时候，形参的类型没有声明，那么调用的时候实参是什么类型在函数中使用的就是什么类型

  

如果调用时传进去的参数少于声明时的参数，那么就会将未传递的参数隐式 var ，所以那时候的值为undefined；多于声明时的参数的时候只会接收前几个和形参个数相同的参数，后面的参数被忽略。

函数的返回值：

函数可以通过参数来接收东西，更可以通过return语句来返回值，即吐出东西。

函数只能有唯一的return，有if的语句除外。

程序遇见了return将立即返回结果，返回调用它的地方，二不执行函数内剩余的语句。

函数有一个return的值，那么现在这个函数实际上就是一个表达式，换句话说这个函数就是一个值，所以这个函数可以当做其他函数的参数。

函数可以接收很多值，但只能有一个返回值。

 

递归：

函数自己调用自己就是递归

 

函数表达式：

定义函数除了使用function外，还可以使用函数表达式。此时函数没有名字称为匿名函数，为了以后调用这个匿名函数，就把这个函数直接复制给一个变量

var haha = function(a,b){

​    return a + b;

}

以后想调用这个函数的时候，就可以直接使用haha变量来调用。

console.log(haha(1,3));

注意：定义函数只能用function直接定义或者将匿名函数赋值给一个变量，两种方法不能糅杂，否则报错。

 

函数声明的提升（预解析）：

JS执行前会有一个预解析的过程，将所有的函数声明提到最最开头，然后再执行第一行语句。所以function定义在哪不重要，程序总能找到这个函数。

注意：函数声明会被提升，但是函数表达式不会被提升，因此，没有特殊情况不建议采用匿名函数赋值给变量这种方法来定义函数。

 

函数是一个引用类型：

基本类型：number、string、boolean、undefined、null

引用类型有：object、function、array、RegExp、Math、Date

需要注意的是，基本类型保存值，引用类型保存地址。

比如变量a=6；那么这个a变量里面存储的是6这个数值；

而a = function(){} 那么这个a标签里面存储的是function的内存地址。

arguments对象：

每一个函数内部，都可以使用一个arguments这个类数组对象，此对象涵盖了所有的实参。比如：

fun(45,436,457,34,23,12);

arguments[0];    //45

如果函数里面有形参列表，那么和arguments是同步的：

function fun(a,b){

​    arguments[0] = 8;

​    alert(a);         //8

}

arguments的功能是模拟函数的重载，使同一个函数根据参数个数的不同有不同的作用。

如设计一个函数，如果传进来一个参数就得到这个数字加一；如果是两个参数那么返回两个数字的和。这种情况可以通过arguments.length来判断实参个数分段写代码块。

闭包：

一个函数可以把它自己内部的语句和自己声明时所处的作用域一起封装成一个密闭环境，我们称为“闭包”。

若想在全局作用域下运行outer内部的inner，可用以下方法：

function outer(){

​      var a = 333;

​      function inner(){

​       console.log(a);

​      }

​      **return inner;** //outer返回了inner的引用

​    }

 

​    var **inn** = outer();  //inn就是inner函数了

​    inn();    //执行inn，全局作用域下没有a的定义

//但是函数闭包，能够把定义函数的时候的作用域一起记忆住

​         //能够输出333

说明了inner函数能够持久保存自己定义时的所处环境，并且即使自身在其他环境被调用的时候，依然可以访问自己定义时所处环境的值。

一个函数可以把它自己内部的语句和声明时所处的作用域一起封装成一个密闭环境，我们称为“闭包”。

每个函数都是闭包，每个函数天生都能够记忆自己定义时所处的作用域环境。

每次重新引用函数的时候，闭包都是全新的。

无论在何处被调用，它总能访问它定义时所处作用域中的全部变量。

 

  

 

## \28.  变量的作用域：

（1）    局部JS变量：

在JS函数内部声明的变量时局部变量，所以只能在函数内部访问它（该变量的作用域是局部的）。

可以在不同的函数中使用名称相同的局部变量，只有声明过该变量的函数才能识别出该变量。

只要函数运行完毕，本地变量就会被删除。

（2）    全局JS 变量：

在函数外声明的变量是全局变量，网页上的所有脚本和函数都能访问它

（3）    JS变量的生存期：

JS变量的生命期从它们被声明的时间开始。

局部变量会在函数运行后被删除。

全局变量会在页面关闭后被删除。

（4）    向未声明的JS变量来分配值：

如果把值赋给尚未声明的变量，该变量将自动被认为是全局变量的声明。

​    总结：定义在function里面的变量叫做局部变量，只能在function里面有定义，出了function是没有定义的。定义在全局范围内的，没写在任何function里面的叫做全局变量，在整个程序中都可以调用。

（5）    作用域链：遇见一个变量的时候，JS引擎会从其所在的作用域依次向外层查找，查找会在找到第一个匹配的标识符的时候停止，由此多层嵌套如果有同名变量就会产生屏蔽效应：

var a = 1;

function fn(){

  var a = 5;                  //屏蔽了外层的a，函数内部看不到外层的a。

  console.log(a);              //输出5，变量在当前作用域寻找。

}

fn();

console.log(a);                //输出1，变量在当前作用域寻找。

作用域链：一个变量在使用时的值会在当前层寻找它的定义，如果找不到就去上一层function，直到找到全局变量为止，如果全局变量也没有那么就会报错。

（6）    定义变量机制：

如果遇见一个标识符没有被var过并且被赋了值，那么就会自动帮你在全局范围内定义var。

（7）    函数的参数会默认定义为这个函数的局部变量。

（8）    全局变量的作用：

a)     通信，共同操作同一个变量。

b)    累加，重复调用函数的时候不会重置。

（9）    函数的定义也有作用域：

公式：

function 大 {

​     function 小 {}

​     小();        //可以运行

}

小();           //不能运行，因为小函数定义在了大函数内部，离开大函数没有作用域

 

## \29.  IIFE：

IIFE是即时调用函数表达式，如果一个函数在定义的时候，我们就想直接调用它，那么这个函数就是一个IIFE。

通常即时调用函数可以用如下语法来实现：

 

(function fun() {

​    alert(‘哈哈’);

})();

也可以在function前加上“+”、“-”来实现。

用这种方法定义的函数，名字是无效的，即匿名函数，若其他地方想调用这个函数就会报错。

设计一个函数，这个函数接收三个参数，它的返回值是前两个数字大的那个数字与第三个数字的和：

function sum(a,b,c){

  return *(function(a,b){*

​       *return a >= b ? a : b;*

*})(a,b)* + c; 

}

斜体部分就是一个IIFE，本质上是一个表达式，表达式计算后就是a和b中较大的那个数字与c的和。

## \30.   Object类型

#### （1）  对象的创建：

创建一个对象有两种方法：一种是字面量，一种是new Object()

字面量的创建方式：

var obj = {

 name : ‘树懒’,

 age : 18;

 gender : ‘男’

};

console.log(obj);

console.log(obj.name);

console.log(typeof obj);

*{}就是对象的界定符，就是对象的字面量*。对象有属性，所谓的属性就是这个对象的特点、特性，name、age、gender都是这个obj对象的属性(preperty)。

什么是对象？对象就是属性的无序集合

我们可以用.点语法、方括号来获得一个对象的属性，和数组相似，只不过数组的下标只能是数字0、1、2…，而我们的对象可以用任何的词来当做属性名。

公式：

{

 	k : v,

​	 k : v.

​	 k : v,

​	 k : v

}

JSON和对象字面量的区别：

JSON所有的k必须加引号，而字面量不需要加引号。

JSON = JavaScript Object Notation,JS对象表示法。JSON是一个用于交换的格式，所以JSON不仅仅是JavaScript用，后台语言比如PHP、Java、Asp等等都要识别JSON，为了最大的兼容，k必须加引号。也就是说JSON里面的k加引号不是因为JS，而是因为后台的语言。

但是当对象中的k是特殊字符、数字、空格、关键字或保留字时，k必须加引号。

同时上述情况也不能用点语法来访问属性，必须使用方括号：

var obj = {

 name : ‘树懒’

}

console.log(obj[‘name’]);

特殊形式的k必须加上引号，检索属性的时候必须使用方括号：

​     var obj = {

   	   **"**24&*$&#@@)@!**"** : "哈哈",

   	   **"**all name**"** : "树懒",

   	   **"**++++%%%%**"** : "嘻嘻",

​      	**"**var**"** : "么么哒",

​    	  **"**function**"** : "嘻嘻"

​    } 

​    console.log(obj**["24&\*$&#@@)@!"]**);

​    console.log(obj**["all name"]**);

​    console.log(obj**["++++%%%%"]**);

​    console.log(obj**["var"]**);

​    console.log(obj**["function"]**);

对象的属性访问，点语法是有局限的，它不能访问上面的特殊情况，也不能访问以变量形式保存的k。

 

```JS
new Object() //创建对象：

var obj = new Object();    //这是一个空对象，没有任何属性

obj.name = ‘树懒’;

obj.age = 18;

obj.gender = ‘男’;

console.log(obj);

console.log(obj.age);

console.log(typeof obj);
```



new是一个运算符，和+-*/一样，表示新创建一个对象，一会学习构造函数，实际上new是一个函数调用的方式。Object()大写字母O，这是一个系统内置的构造函数。

可以用obj.k = v;来追加属性

推荐使用字面量的形式来创建对象。不要糅杂。

#### （2）  对象的属性值：

对象属性值可以是任何东西。比如数字、字符串、布尔值、正则表达式、对象、数组、函数……

 var kaola = {

  		 name : ‘树懒’;

 		  age : 18;

 		  peiou : {

​    			 name : ‘母树懒’,

​    			 age : 19,

   	}

 };

console.log(kaola.peiou.age);

​	var obj = {

​	 a : 1,

​	 b : ‘哈哈’,

​	 c : true,

​	 d : /[A-Z]/g,

​	 e : function(){

 	  alert(1 + 2);

 },

​	 f : {

 		  p : 1

​	 }

};

特别的，当对象的属性值是一个函数的时候，我们称这个函数是对象的方法。

#### （3）  对象的方法：

方法就是一个对象能够做的事如：

var xiaoming = {

 name : ‘小明’,

 age : 18,

 gender : ‘男’;

 sayHello : function(){

 	  alert(‘你好，我是’ + this.name);

​	   alert(‘今年’ + this.age + ‘岁了’);

 	  alert(‘我是可爱的小’ + this.gender + ‘生’);

​	 }

};

xiaoming.sayHello();

比如上面的案例sayHello就是一个属性，只不过它的值是一个函数，所以我们就可以说xiaoming这个对象有sayHello方法。

一个对象方法函数里面的this指的就是拥有这个方法的对象。

现在说一下this都是什么：

直接用()运算符调用函数，那么函数里面的this指的是window对象。

函数如果绑定给了某个HTML元素的事件上，那么函数里面的this就是这个HTML对象。

用定时器调用函数，函数内部的this就是window对象。

用apply、call可以人工设置this指的是谁。

 

方法就是函数的一种调用形式，这个函数里面的this就是这个对象。函数里面的this到底是谁在函数定义的时候并不知道，要看函数如何被调用。

对象方法的哲学就是操作自己的属性。如果一个对象的方法不操作自己的属性那么这个方法就没卵用，zhangda方法就是让自己的age++：

 

var xiaoming = {

​		 name : ‘小明’,

​		 age : 18,

​		 gender : ‘男’,

​		 zhangda : function(){

 	 	 this.age++;

​	 }

};

#### （4）  构造函数：

JavaScript规定，一个函数可以用new关键字来调用。那么此时将按顺序发生四件事情：

1) 隐秘的创建一个新的空对象。

2) 将这个函数里面的this绑定到刚才创建的对象上。

3) 执行函数体里面的语句。

4) 返回这个新的对象。

​    function People(){

​    this.name = ‘小明’;

​    this.age = 18;

​    this.gender = ‘男’;

  }

  var xiaoming = new People();

  console.log(xiaoming);

  console.log(xiaoming.age);

  console.log(typeof xiaoming);

  //People{name:’小明’,age:18,gender:’男’}

  //18

  //object

   函数机理：

  ![image-20191203111707550](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203111707550.png)

## \31.原型prototype:

先看一个例子：

```JS
function fun(){

 alert(‘你好’);

}

console.log(fun.prototype);

console.log(typeof fun.prototype);
```

![image-20191203111809254](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203111809254.png)

  

在JavaScirpt中，任何一个函数都有一个prototype属性，指向一个对象。我们输出了一个prototype属性，会发现是一个空对象。输出这个prototype的类型，发现是object类型。

prototype就是原型的意思，每个函数都有原型，原型是一个对象。

一个函数的原型，对于普通函数来说没有用处，但是对于构造函数来说用处极大。

//构造函数，构造函数里面没有任何语句，也就是说，这个构造函数在执行的时候，不会给创建出来的函数添加任何属性。

function People(){

}

//构造函数的原型，我们更改了构造函数的原型，为一个新的对象：

```JS
People.prototype = {

 name : ‘树懒’,

 age : 18,

 gender : ‘男’

}
```



//当一个对象被new出来的时候，不仅仅执行了构造函数里面的语句也会把这个对象的__proto__指向构造函数的prototype。

```JS
var xiaoming = new People();

console.log(xiaoming.__proto__);

console.log(xiaoming.__proto__ == People.prototype);
```

//当我们试图访问name、gender、age属性的时候，如果构造函数语句中没有，就会查找这个函数的原型，如果原型上有这个属性，那么就会将这个属性当做自己的属性返回。

```JS
console.log(xiaoming.name);

console.log(xiaoming.gender);

console.log(xiaoming.age);
```

prototype一定是函数的属性。当这个函数是构造函数时，它new出来的对象将以它的原型的那个对象为new出来的实例对象。

  ![image-20191203112455348](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203112455348.png)

注意，任何一个对象都有____proto____属性，这个属性是Chrome的属性，别的浏览器不兼容，但是别的浏览器也有原型对象，只不过不能通过__proto__进行访问。

这是属性指向自己的原型对象。

JavaScript有一个原型链查找机制

当我们试图访问一个对象身上的属性的时候，如果这个对象身上有这个属性，则返回它的值。如果它身上没有这个属性，那么将访问它的原型对象，检测它的原型对象身上是否有这个值，如果有就返回它原型对象身上的这个值。

也就是说我们讲了两个对象和一个函数的故事。任何一个函数都有原型，原型是一个对象，用prototype访问。当这个函数是构造函数的时候，new出来的对象它们的原型对象就是这个构造函数的原型：

prototype我们称为“原型”，只有函数有原型

____proto____ 我们称为“原型对象”，任何对象都有原型对象。

 ![image-20191203112506583](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203112506583.png)

 

原型的用途：

我们定义一个方法的时候，如果写在构造函数里面：

```JS
function People(name, age){

 this.name = name;

 this.age = age;

 this.sayHello = function(){

  alert(‘你好，我是’ + this.name + ‘我今年’ + this.age + ’岁了’);

 }

}

var xiaoming = new People(‘小明’,12);

var xiaohong = new People(‘小红’,11);

xiaoming.sayHello();

xiaohong.sayHello();
```



实际上这个函数被复制了两份，一份给了xiaoming，一份给了xiaohong。xiaoming和xiaohong这两个实例身上有了相同功能的函数，但是这个函数不是同一个函数。

二函数天生都要被复用：

```JS
alert(xiaoming.sayHello == xiaohong.sayHello);  //false
```

xiaoming身上的函数和xiaohong身上的函数不是同一个函数。

想要解决这个问题：

```JS
function People(name,age){

//构造函数里面负责定义一些属性，随着构造函数的执行，这些属性将绑定到new出来的对象身上

 this.name = name;

 this.age = age;

}

//把所有方法定义在原型对象上

People.prototype.sayHello = function(){

 alert(‘你好，我是’ + this.name + ‘我今年’ + this.age + ‘岁了’);

}

  

alert(xiaoming.sayHello == xiaohong.sayHello);
```

![image-20191203112757549](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203112757549.png)

  证明了xiaoming的sayHello方法和xiaohong的sayHello是一个函数，内存消耗小很多。

 

#### JavaScript的原型链机制：

先学一个属性constructor，函数的原型有constructor属性，指向构造函数。

  ![image-20191203112837724](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203112837724.png)

People.prototype.constructor //指向构造函数

我们之前说过，一个对象的原型身上有什么，那么实例对象就也可以打点调用什么，所以：

xiaoming.constructor //指向构造函数

只要是对象就一定有原型对象，就是说只要这个东西是对象，那么就一定有__proto__属性。世界上只有一个对象没有原型对象，这个对象就是Object.prototype。

Object是一个函数，是系统内置的构造函数，用于创造对象的。Object.prototype是所有对象的原型链终点。所以，当我们在一个对象上打点调用某个方法的时候，系统会沿着原型链去找它的定义，一直找到Object.prototype。

  

 ![image-20191203112847885](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20191203112847885.png)

## \32.继承：

继承和in运算符具体见代码。

 

hasOwnProterty方法，这个方法定义在Object.prototype上，所以任何一个对象都能拥有这个方法，这个方法返回true、false。表示自己是否拥有这个属性，不考虑原型链。就看自己身上有没有这个属性，不进行原型链查找。

for……in考虑原型链，因此我们可以内嵌一个判断，把自己身上的属性输出：

for (var k in obj){

 obj.hasOwnProperty(k) && console.log(k);

}

对象可以通过打点调用属性，遍历原型链，如果属性存在就返回值，不存在就返回undefined。但是当属性值为undefined时返回的也是undefined容易产生误会，因此判断属性最好使用上面的方法。

 

instanceof运算符：

用来验证一个对象是不是一个类的实例。如：

//类、构造函数

function Dog(){

 

}

//实例化一个对象

var d = new Dog();

//验证d是不是Dog的一个实例

console.log(d instanceof Dog); //true

在原型链上要注意下面这种情况：

//类

function Dog(){}

function Cat(){}

Cat.prototype = new Dog();  //继承

var helloKitty = new Cat(); //通过Cat实例一个对象

console.log(helloKitty.constructor);//Dog

console.log(helloKitty instanceof Cat);  //true

console.log(helloKitty instanceof Dog);  //true

instanceof运算符机理：遍访helloKitty这个对象的原型链上的每个原型对象（__proto__）如果遍访到这个原型对象是某个构造函数的prototype，那么就认为helloKitty是这个构造函数的实例，返回true。



## \33.DOM:

DOM（Document Object Model，文档对象模型）描绘了一个层次化的节点树，允许开发人员添加、移除和修改页面中的某一部分。这使得JavaScript操作HTML不再是操作字符串，而是在操作节点，极大地降低了编程难度。

（1）    得到元素getElementById：

HTML负责页面布局、结构，JS要操作HTML标签，第一件事就是得到这个标签。

JS最基本的得到元素的方法有两个：

document.getElementById();

document.getElementByTagName();

JavaScript通过document对象表示文档，它表示整个页面。有很多属性和方法，包含了绝大多数页面的特征和操作。学习DOM说白了就是学习document对象。

document.getElementById();方法通过id得到元素

如果页面上没有匹配的id的HTML元素将返回null，null就是空对象。

页面中不能有多个元素的id相同，如果有相同的元素，那么只返回文档中第一次出现的元素。

注意id的大小写。

IE7及较低版本浏览器中，表单元素name特性也会被当做id，为避免这个问题，页面上的name最好不要和任何id相同。

document.getElementByTagName();不管这个标签有几个，得到的都是一个数组。

写的时候一定是如下：

divs[0].style.属性=属性值;

若想要获取的是页面中没有的标签，那么得到的会是一个空的数组。

可以通过连续打点来调用get如（如果是数组一定要加下标才能变成对象）：

document.getElementsByTagName("div")**[1]**.getElementsByTagName("p")**[2]**.getElementsByTagName("span")**[1]**.style.color = "red";

（2）    更改HTML属性：

HTML标签有很多属性，如src、href、title等。

JS可以更改HTML的任何属性，方法有两种：点语法和setAttribute()、getAttribute()。

得到一个元素后，直接打点调用它的属性名，救恩能够对HTML相应的属性进行更改。

注意class属性要用.className；for要写成.htmlFor；rowspan要写成.rowSpan；colspan要写成.colSpan。

 

还可以用setAttribute()、getAttribute();来得到属性和设置属性

setAttribute和点语法的区别：

所有的自定义属性都不能通过点语法得到；

所有行内样式点语法.style得到的是一个样式对象，我们可以通过.style.border继续得到小样式，但getAttribute()得到的是字符串；

getAttribute()不需要避讳，直接：

abce.getAttribute(‘class’);    //即可

点语法效率更高，所以除了要读取自定义属性，一般都使用点语法。

（3）    操作元素样式：

通过点语法.style能够得到所有样式的封装。注意只能得到行内样式，所有写在CSS内嵌的、外联的一律不能得到。需要学习后面的知识得到计算后样式。

我们可以通过语法：oBox.style.css样式名来的到某一个样式，所有css中有连字符的样式都要转为驼峰：

console.log(oBox.style.backgroundColor);

也可以通过=来更改css样式，所有更改的样式也是行内样式，设置的时候也是驼峰：

var oP = document.getElementById("pp");

oP.style.backgroundColor = "skyblue";

oP.style.fontSize = "100px";

等号右边就是CSS的写法，用引号引起来，通过点语法.style读、设都是在行内。

（4）  事件监听：

JavaScript制作交互效果离不开事件。所谓事件就是用户的某个行为，能够触发一个函数的执行。今天只学习DOM标准中0级事件的绑定方法：

//得到这个box

var oDiv = document.getElementById(‘box’);

//事件

oDiv.onclick = function(){

​     alert(‘你好’);

}

​        也可以：

​        oDiv.onclick = fun;

​        function fun(){

​    alert(‘你好’);

}

​     现在我们知道，一个函数可以当做一个事件的处理函数，当这个事件发生时，       函数也能执行

​     onclick   单击

   onmouseover 鼠标进入

   onmouseout   鼠标离开

   ondblclick   双击

   onfocus     得到焦点

   onblur     失去焦点，得到和失去焦点可以通过点击和tab键来实现

   onmousedown   鼠标按下

   onmouseup     鼠标按键抬起

 onload              当页面完全加载成功

 window.onload     表示页面中所有的代码都已经加载完毕了。

（5）    批量添加监听：

页面上所有的p，现在都要有click事件监听，就要用循环语法加：

for(var i = 0; i < ps ; i++){

  ps[i].onclick = function(){

​     alert(‘你好’);

  }

}

for循环包裹添加监听的语句会导致闭包的影响再次出现：

**var** ps = document.getElementsByTagName('p');
 **for** (**var** i = 0; i < ps.length; i++) {
   // (function (m) {
   //   ps[i].onclick = function () {
   //     console.log(m)
   //   }
   // })(i);    //IIFE
   ps[i].idx = i;     //自定义属性,令自定义属性为i
   ps[i].onclick = **function** () {
     console.log(**this**.idx); //this代表触发这个事件当前的元素
   }
 }
 //两种方式解决函数闭包问题

（6）    对应和排他：

对应：

**var** ps0 = document.getElementsByTagName('div')[0].getElementsByTagName('p');
 **var** ps1 = document.getElementsByTagName('div')[1].getElementsByTagName('p');
 **for** (**var** i = 0; i < ps0.length; i++) {
   //绑定自定义属性
   ps0[i].idx = i;
   ps0[i].onclick = **function** () {
     ps1[**this**.idx].style.background = 'red';
     console.log(**this**);   //触发该事件的元素
   }
 }

排他：

```JS
var ps = document.getElementsByTagName('p');
 for (var i=0;i<ps.length;i++){
   ps[i].onclick = function () {
     //把所有的改成原来的
     for (var j = 0; j < ps.length; j++) {
       ps[j].style.background = 'skyblue';
     }
     this.style.background = 'red'; //把自己变成想要的
   }
 }
```

（7）    计算后样式：

```JS
   var box = document.getElementById('idbox');
 // console.log(box.style.width);    //只能得到行内样式，输出为空
 // console.log(box.style.background); //red
 console.log(window.getComputedStyle(box));
 console.log(**typeof** window.getComputedStyle(box));  //Object对象
 console.log(window.getComputedStyle(box).getPropertyValue('width'));  //200px
 //window中的方法可以直接省略window
 console.log(getComputedStyle(box).getPropertyValue('height'));   //200px
 console.log(getComputedStyle(box)['background-color']);   //rgb(255,0,0)
```

 

​       低版本浏览器：

           ```JS
alert(box.currentStyle);     //Object

      alert(box.currentStyle.width);
    
      alert(box.currentStyle[‘width’]);
           ```



​           注意驼峰。

​       能力检测：

​           if(window.getComputedStyle){

​              alert(window.getComputedStyle[‘width’])

​           }else{

​              alert(box.currentStyle[‘width’]);

​           }

（9）    关于Opacity：

IE8和早期浏览器不支持opacity，通过style.opacity或者ele.currentStyle.opacity属性取值时，返回的依然是opacity值，即使浏览器完全忽略了opacity值。当我们能够保证opacity、filter中设置的属性是一致的，则Javascript读取opacity值就算是兼容的。

（10）  快捷位置和尺寸：

DOM已经提供给计算后的样式，又提供给了一些API：

ele.offsetLeft；ele.offsetTop；ele.offsetWidth；ele.offsetHeight；ele.clientWidth；ele.clientHeight。

 

offsetLeft属性和offsetTop属性：

这两个属性的兼容性比较差。适合IE9、IE9+、Chrome等高级浏览器

一个元素的setoffLeft值就是这个元素左边框外，到自己的offsetParent对象的左边框内的距离。

  

每一个元素天生都有一个属性叫做offsetParent，表示自己的“偏移参考盒子”。

offsetParent就是自己祖先元素中离自己最近的已经定位的元素，如果自己的祖先元素中没有任何盒子进行了定位，那么offsetParent对象就是body。

IE6、IE7：

IE6、7的offsetParent对象是谁，和高级浏览器有非常大的不同。

情形1：自己如果没有定位属性，那么自己的offsetParent对象就是自己的祖先元素中离自己最近的有width或者有height的元素：



 



情形2：自己如果有定位属性

那么自己的offsetParent就是自己祖先元素中离自己最近的有定位的元素。

 

数值就是自己的左外边框到offsetParent对象的左内边框的值。

IE8：

IE8的offsetParent是谁呢？和高级浏览器一致：

无论自己是否定位，自己的offsetParent就是自己祖先元素中，离自己最近的已经定位的元素。

这一点，没有任何兼容问题！

**但是，多算了一条边框**

  

​                            总结

|              | IE6、7                                                       | IE8              | IE9、IE9+、高级浏览器                      |      |
| ------------ | ------------------------------------------------------------ | ---------------- | ------------------------------------------ | ---- |
| offsetParent | 如果自己没有定位，那么就是自己父亲中有width或者有height或者有定位的元素。  如果自己有定位，那么就是和高级浏览器一致。 | 和高级浏览器一致 | 自己祖先元素中，离自己最近的已经定位的元素 |      |
| offsetLeft   | 和高级浏览器一致                                             | 多算一条border   | 自己的border外到offsetParet对象的border内  |      |
|              |                                                              |                  |                                            |      |

**要确保属性的使用条件**

**自定位，父无边**  **(****父亲也要定位，但是为了顺口，就不多说了)**

这样的话，所有浏览器的值都是一样的，offsetLeft、offsetTop值是number类型的，可以直接参与运算，不需要parseInt()

 

offsetWidth和offsetHeight：

全线兼容，和别的盒子无关。

一个盒子的offsetWidth值就是自己的width+左右padding和左右border的宽度。

  

如果盒子没有宽度，那么浏览器将把px值当做offsetWidth，而不是100%。

如果盒子没有高度，完全是用文字撑开的，所有浏览器都会把px值当做offsetHeight。

注意的是IE6、7、8下，盒子没有高度，文字撑的，用currentStyle.height是auto，体现了offsetHeight的好处。

 

​    clientWidth和clientHeight：

  

clientWidth就是自己的width+padding值，也就是说，比offsetWidth少了border。

如果盒子没有宽度，那么所有浏览器都会把px值当做clientWidth而不是100%。

如果盒子没有高度是文字撑开的，IE6 clientHeight是0，其他浏览器都是数值。

（11）  运动：

定时器：window对象有一个方法，叫做

window.setInterval(函数,间隔时间);

能够使每间隔时间，调用函数一次。我们习惯叫做定时器，按理说叫间隔器。如：

window.setInterval(function(){

   console.log(‘你好’);

},1000);

间隔单位是以毫秒为单位，1000ms就是1s。

第一个参数是一个函数，所以可以把一个匿名函数放在里面，更可以引用一个函数：

function fun(){

 console.log(‘你好’);

}

window.setInterval(fun,1000);

同时window对象可以不写：

setInterval(function(){

 console.log(Math.random());

},1000);

定时器没有start、begin方法，只要setInterval，定时器就开始运行了。

 

简单运动模型：

视觉暂留：把连续相关的画面连续播放就是运动：

var nowleft = 111;

//定时器

setInterval(function(){

 nowleft += 10;

 oDiv.style.left = nowleft + ‘px’;

},20);间隔时间是20ms，那么一秒钟执行函数50次。也就是说这个动画是每秒50帧，50fps。

如何让上述盒子运动得更快：

数值20是间隔时间，这个数字越小运动越快。

10叫做步长，每一步的变化量，这个数字越大运动越快。

 

定时器的停止：

setInterval的时候要给这个定时器一个变量引用，停止的时候只需要clearInterval(timer).

timer = setInterval(function(){},20);

clearInterval(timer);

 

简单运动要注意的：

为了防止盒子在点击后运动速度越来越快，要“设表先关”。

startbtn.onclick = function(){

   //设表先关

   clearInterval(timer);

   //设置定时器

   timer = setInterval(function(){

​     nowleft += 2;

​     oDiv.style.left = nowleft + ‘px’;

 },20);

}

还有到盒子终点自己停止，要拉终停表：

var timer = setInterval(function(){

   nowleft += 7;

   if(nowleft > 600){

​     nowleft = 600;

​     clearInterval(timer);

   }

   oDiv.style.left = nowleft + ‘px’;

   console.log(nowleft);

},20);

 

无缝连续滚动：

见代码。

（12）  JSON：JSON叫做javaScript object Notation,JavaScript对象表示法。

JSON示例：

 var obf = {

   “name” : “哈哈”,

   “age” : 18,

   “gender” : “不详”

};

console.log(obj.age);   //18

语法：

{

“” : v,

“” : v,

“” : v,

“” : v

}

之后就能用点语法访问某一个属性

obj.age;  //obj这个对象的age属性

如果不用点语法也可以使用[]来表示属性，需要注意的是[]里面是变量:

var a = “age”;

console.log(obj[a]);   //18

如果不想用变量必须加引号:

obj[“age”]   //18

 

JSON嵌套:

JSON里面的v可以又是一个JSON:

   var obj = {

​     “name” : “哈哈”,

​     “age” : 18,

​     “gender” : “不详”,

​     “shengao” : 193,

​     “peiou” : {

​      “name” : “Angelababy”,

​      “age” : 16,

​      “shengao” : 168

​     }

   };

所以想得到168这个数字：

obj.peiou.shengao   //168

Ajax大量用到JSON。

 

JSON项的添加和删除：

如果想增加obj里面的项，就用点语法赋值:

var obj = {

 “name” : “哈哈”,

 “age” : 18

};

obj.gender = “刚变完性”;

如果想删除某一个属性，使用delete关键字:

delete obj.age;

 

JSON的遍历：

for…in语句是专门用来遍历JSON的语法:

for(var k in obj){

   console.log(k + ’的值是’ + obj[k]);

}

k会依次等于我们obj里面的属性名，然后在循环语句里面，用obj[k]来读取这个值。

（13）  运动框架：

见代码

## \34.BOM：

