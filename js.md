http://blog.csdn.net/skyjie6/article/details/38659407
前端js速成自制笔记
##HTML和JS
###1超文本文件中,JavaScript程序代码位于<script></script>之间.
###2script 的type 属性值一定是 javascript/text.
###3如果script属性引入了js文件,那么起始标签与结束标签之间的内容将被忽略.

	例子
	           html:  	<scrpit type="text/javascript" src="tom.js"">  
	    					alert("abc");  
					</script>  
			   tom.js:  alert("tom file");
			   
			   output: tom file
				
##数据类型
###1js是不分定义类型的，只要用了var都是定义了一个变量，没有赋值时是一个Undefined类型（var a=20;这时是数字类型, a=true;这时又为了逻辑类型）
###2可以使用typeof 获取类型
###3标识符:只能有字母,数字   _  和 $ 这四种组成,同时开头不能是数字.
###4字符串类型:用一对(')或者(")的就是
	注意换行符(\n),制表符(\t),回车符(\r).,反斜杠(\\),单引号(\'),双引号(\").
	可以使用+进行连接.
###5函数:function ( ...)  { .....   }
	可当成变量看: 假如有function add() ... 然后var tom=add;  那么tom也是一个和add一样功能的函数
	

####使用arguments重构: 
		 function average()
		{ if(arguments.length==1) return arguments[0];   //一个参数
		   if(arguments.length==2)return (arguments[0]+arguments[1])/2 ;  //两个参数
		   ....
		}
###对象
####构造函数

		function Persom(xm,sf){  
	  		this.name=xm;  
	  		this.id=sf;  
	  		this.speak=function(){  
	        docunment.writenln("我的名字是:"+this.name+"<br/>");  
	 		}  
		} 
		然后是实例化对象:var tom=new Person("汤姆猫","13254");
		使用对象: tom.speak(); 
###object()是js里面预定义的一个对象,可以直接拿来用
##运算表达式
###1运算符（+-×÷）,a++和++a运算优先级比前面的高
###2如果两个字符串比较,那么比的就是每个字母大小("d">"a"),如果相等,比较下一个字母
如果不同类型比较.转化为数字类型比较.其中"52"可以转化为52,但是"52a"转为为NaN,true转化为1
###3这里多了个严格相等(===)和不严格相等(!==),指的是不自动转化下的比较.
###4逻辑表达: &&与  ||或  !非 
###5条件运算:  a:b?c.
   	     	if/else  , switch.

			循环:for, while, do while.  -------break,continue,return
			其他运算:new,typeof, instanceof(判断某对象是否某类型)
##字符串对象

			创建：	var str=new String("とある字符串");
###1使用 == 逻辑比较字符串对象的话,比较的是引用值而不是内容本身

			例：var str1=new String("哈哈哈!");   //建立了一个哈哈哈的对象  
				var str2=new String("哈哈哈!");   
				//再次建立了一个哈哈哈的对象,与前一个对象不同的  
				var boo1=(str1== str2);             
				//boo1=false~因为两个对象不是指向同一个的 
				
				比较内容本身应该使用localeCompare();
				var boo2=str1.locateCompare(str2;   //大于返回1,等于返回0,小于返回-1;  

###连接
####concat() ,或者直接用  +

###检索
使用charAt();   //charCodeAt();则是把检索结果转化为编码

			[javascript] view plain copy
			var string =new String("SD卡路公交受得了柑橘味儿");  
			var ch=string.charAt(5);    //ch结果是"公"  

###查找
使用indexOf();  返回的是第一次找到字符串的位置,找不到返回-1

			indexOf("bcd");  //表示从头开始查找
			indexOf("bcd",5);  //表示从第六个字母开始找
			lastIndexOf(  ) ;    //向前查找.

###获取子串

			使用substring();  //小的数字为起始位置,大的数字为末位.首字下标是0.结尾不算入其中
			var s=new String("123456789");
			var sub=s.sub(3,6);    //sub=456  , 7的下标虽然是6,但结尾不算进去
			使用slice(a,b);   //左边的数是起始位置右边是末位.同时负数表示从尾倒数过来.-1表示最后一个

###替换
			replace(); 把第一个找到的,替换成新的
			[javascript] view plain copy
			var s=new String("tom@sohu.com");  
			var ss=s.replace("om","eacher");    //替换后s并没有改变  

大小写切换:
			toLowerCase(); 全部变成小写
			toUpperCase();全部变成大写

与数字转换:

			toString();  数字变成字符串,默认变为10进制的.
			toString(2);  //变成2进制的,如  5 变成  101
			toString(16); //变成16进制
			parseInt();  //字符串转换为整型,可识别10,8,16进制
			parseFloat();  //转化为浮点型
			Number();  //转化为数字类型
			以上如果转化失败都是返回NaN;