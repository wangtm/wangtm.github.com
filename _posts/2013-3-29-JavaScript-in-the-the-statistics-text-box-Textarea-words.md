---

layout : post

category : manage

tags : [JavaScript 实现统计文本框]

title :JavaScript中实现统计文本框Textarea字数

---

#JavaScript中实现统计文本框Textarea字数

先增加一个span，用于显示剩余的字数，然后在Textarea中，加入一个onkeydown和onkeyup的事件，调用另一段JavaScript函数，
函数调用的参数为span的id和textarea的id，然后再JavaScript中使用innerHTML返回计算出来的剩余字数。
<pre>
<script language="javascript">  
function countChar(textareaName,spanName)
{  
 document.getElementById(spanName).innerHTML = 140 - document.getElementById(textareaName).value.length;
}  
</script>  
可以输入<span id="counter">140</span>字<br/>
<textarea id="status"  name="status" rows="6" cols="40" onkeydown='countChar("status","counter");' onkeyup='countChar("status","counter");'></textarea>
<pre>