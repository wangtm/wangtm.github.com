---

layout : post

category : manage

tags : [js 正则表达式 search方法]

title : js正则表达式之search方法讲解

---



 #   js正则表达式之search方法讲解

返回与正则表达式查找内容匹配的第一个子字符串的位置
功能：返回与正则表达式查找内容匹配的第一个子字符串的位置 

语法：stringObj.search(rgExp) stringObj 必选项 rgExp正则表达式 

返回值：search 方法指明是否存在相应的匹配。如果找到一个匹配，search方法将返回一个整数值，指明这个匹配距离字符串开始的偏移位置。如果没有找到匹配，则返回 
   代码如下:

<html> 
<script language="javascript" type="text/javascript"> 
//search 方法指明是否存在相应的匹配。如果找到一个匹配，search 方法将返回一个整数值，指明这个匹配距离字符串开始的偏移位置。如果没有找到匹配，则返回 -1 
var re=/(/d)(/d)/d/2/1/;//设置正则表达式 
var ostr="11010111";//所要匹配的字符串，字符串第一个位置从0开始 
var pos=ostr.search(re);//进行字符串匹配 
if(pos==-1){//如果没有找到匹配 
document.write("没有找到任何匹配"); 
} 
else{ 
arr=ostr.match(re);//进行match找出匹配的内容 
document.write("在"+pos+"找到第一个匹配，匹配内容为："); 
document.write(arr[0]);//输出匹配的内容 
} 
</script> 
</html> 