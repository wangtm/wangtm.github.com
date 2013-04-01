---

layout : post

category : 技术

tags : [wiki   浮动目录 ]

title : wiki创建目录

---

wiki创建目录
一个目录可以方便快速的了解一份文档或一本书的大致内容
由于最近在在整理wiki，上面的文档整理多了，看起来不方便，要是有一个目录就好了
这里分享几种建立目录的方法
第一种：可以创建左右列表
		
	{{toc}} => toc左对齐
	{{>toc}} => toc右对齐

h1. 内容列表演示 

	<pre>{{toc}}演示例子</pre>
	{{>toc}}
h2. 第一章 
h3. 第1节
h3. 第2节
h3. 第3节  
h3. 第4节  
h3. 第5节 
h2. 第二章 
h3. 第1节 
h3. 第2节  
h3. 第3节 
h2. 第三章 
h3. 第1节  
h3. 第2节
  
第二种：可以创建类似面包屑的导航
	
	{{Catnav|XXXXX|XXXCCC|DDDD}}
	{{Catnav|EEE|EEEESSSE|ESSSEE|ESSSE}}
			          
		
第一种方法要想做成浮动的目录需要导入下面GeaseMonkey.js脚本，下面是js脚本：

// ==UserScript== // @name            
MediaWiki TOC Floatable
 // @description    key "m" and "Ctrl+Left mouse" to show ,“ESC” to Hide 
// @source         http://userscripts.org/scripts/show/50864 
// @identifier      http://userscripts.org/scripts/source/50864.user.js
 // @version         0.1 
// @date            2009-06-05
 // @author          
 // @namespace       http://suflanker.blogbus.com/
 // @include          
// @exclude          
// ==/UserScript== //参数定义 var TOCX = 0; //TOC坐标 var TOCY = 0;  var Toc; 
 //事件响应  
function KeyPress(e) {    
    if (e.keyCode==27) { //Esc键隐藏Toc        
            hideTOC();		      
               return  
   }    	
if (e.charCode==109) { //'m'键显示TOC 		
if (!Toc) { 		
  showTOC();		 		  
return 		
}	 		
if(Toc.style.display=='block') { 			
hideTOC(); 			
return 		
}else { 			
showTOC();	 			
return 		
}       	    
 }   
  } //鼠标抬起响应
 function mouseupHandler(e){ 	
if (e == null)
 return;	 	
TOCX = e.layerX - 20 + document.body.scrollLeft;  	
TOCY = e.layerY - 40 + document.body.scrollTop;  	
if ( e.ctrlKey && e.button==0 ){ //Ctrl+鼠标左键弹出TOC		 		showTOC(); 		
return 	
} 
 }
 function mousemoveHandler(e) { 	
if (e == null) 
return;	 	
TOCX = e.layerX - 20 + document.body.scrollLeft;  	
TOCY = e.layerY - 40 + document.body.scrollTop;  
}  
 function TocClick(e) { 
    if (window.IsMouseOverToc) //点击Toc后将其隐藏 		
hideTOC(); 
   } 
document.addEventListener('keypress', KeyPress, false); document.addEventListener('mouseup',mouseupHandler,false); 
document.addEventListener('click', TocClick, false); document.addEventListener('mousemove',mousemoveHandler,false);  //以下是功能函数
 function hide(elm) {if (elm) elm.style.display='none'}	//隐藏元素 
function show(elm) {if (elm) elm.style.display='block'} //显示元素  //显示
Toc function showTOC() { 	
var visible = (Toc && (Toc.style.display != 'none'))	   
  if (!Toc) { 		
Toc = buildToc();		 		
show(Toc); 	
}else { 		
changePosition(); 		
show(Toc); 	
} 
 } //隐藏
Toc function hideTOC() {    
 hide(Toc); 
} //设置Toc位置
 function changePosition() { 	
if(!Toc) 
return; 	
Toc.setAttribute('style', 'top:' + TOCY + 'px;left:' + TOCX + 'px;position:absolute;'); 
}  //获取
Toc function buildToc() { 	
Toc = document.getElementById('toc'); 	
Toc.setAttribute('style', 'top:' + TOCY + 'px;left:' + TOCX + 'px;position:absolute;');  
   window.IsMouseOverToc = false; //点击Toc时将其隐藏   
  Toc.addEventListener('mouseover', function(e){window.IsMouseOverToc = true;
},
 false);  
   Toc.addEventListener('mouseout', function(e){window.IsMouseOverToc = false;}, false);   
  return Toc;  }

  
还有很多创建导航的方法！有兴趣的进http://www.wikilib.com/wiki/%E9%A6%96%E9%A1%B5网址里查看