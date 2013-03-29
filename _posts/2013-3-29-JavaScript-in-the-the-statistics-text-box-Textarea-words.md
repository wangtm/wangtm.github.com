---

layout : post

category : manage

tags : [JavaScript 实现统计文本框]

title :JavaScript中实现统计文本框Textarea字数

---

#JavaScript中实现统计文本框Textarea字数

   <!-- To view this file, download free mind mapping software FreeMind from http://freemind.sourceforge.net -->
<node CREATED="1364527076438" ID="ID_1091852651" MODIFIED="1364527224964" TEXT="javascript">
<node CREATED="1364527094893" ID="ID_766240568" MODIFIED="1364527106271" POSITION="right" TEXT="&#x5148;&#x589e;&#x52a0;&#x4e00;&#x4e2a;span&#xff0c;&#x7528;&#x4e8e;&#x663e;&#x793a;&#x5269;&#x4f59;&#x7684;&#x5b57;&#x6570;&#xff0c;&#x7136;&#x540e;&#x5728;Textarea&#x4e2d;&#xff0c;&#x52a0;&#x5165;&#x4e00;&#x4e2a;onkeydown&#x548c;onkeyup&#x7684;&#x4e8b;&#x4ef6;&#xff0c;&#x8c03;&#x7528;&#x53e6;&#x4e00;&#x6bb5;JavaScript&#x51fd;&#x6570;&#xff0c; &#x51fd;&#x6570;&#x8c03;&#x7528;&#x7684;&#x53c2;&#x6570;&#x4e3a;span&#x7684;id&#x548c;textarea&#x7684;id&#xff0c;&#x7136;&#x540e;&#x518d;JavaScript&#x4e2d;&#x4f7f;&#x7528;innerHTML&#x8fd4;&#x56de;&#x8ba1;&#x7b97;&#x51fa;&#x6765;&#x7684;&#x5269;&#x4f59;&#x5b57;&#x6570;&#x3002;"/>
<node CREATED="1364527096284" ID="ID_904004433" MODIFIED="1364527117509" POSITION="right" TEXT="&lt;script language=&quot;javascript&quot;&gt;   function countChar(textareaName,spanName) {    document.getElementById(spanName).innerHTML = 140 - document.getElementById(textareaName).value.length; }   &lt;/script&gt;   &#x53ef;&#x4ee5;&#x8f93;&#x5165;&lt;span id=&quot;counter&quot;&gt;140&lt;/span&gt;&#x5b57;&lt;br/&gt; &lt;textarea id=&quot;status&quot;  name=&quot;status&quot; rows=&quot;6&quot; cols=&quot;40&quot; onkeydown=&apos;countChar(&quot;status&quot;,&quot;counter&quot;);&apos; onkeyup=&apos;countChar(&quot;status&quot;,&quot;counter&quot;);&apos;&gt;&lt;/textarea&gt;"/>
</node>
</map>
