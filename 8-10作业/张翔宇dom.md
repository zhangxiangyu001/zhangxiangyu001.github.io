# JavaScript DOM参考手册  
***  
它定义了访问和操作HTML 文档的标准和方法
### 你应该具备的基础知识  
  
  #### 在学习之前，你需要了解以下内容：  
   . HTML  
   . CSS  
   . JavaScript    
***  

#### dom 按照层级的方式来划分：  
1，父节点  
2，子节点  
3，兄弟节点  
#### 按照节点类型划分：  
1元素节点  
2属性节点  
3文本节点  
8注释节点  
9document节点  
***  
    nodeType 返回节点的类型  
    ndeName 返回节点的名称  
    nodeValue 返回节点的值  
    typeof 查看变量类型  
    **查看节点名称 ： nodeName 属性**  
    元素节点的 nodeName : 元素的本身  
    属性节点的 nodeName : 属性名本身  
    文本节点的 nodeName : #text    
    注释节点的 nodeName : #comment  
    document的 nodeName : #document  
    **查看节点的值： nodeValue 属性**  
    元素节点的 nodeValue : null  
    属性节点的 nodeValue : 属性值  
    文本节点的 nodeValue : 文本内容   
    注释节点的 nodeValue : 注释的内容  
    document的 nodeValue : null   
***  

# DOM 方法  
#### children 和  childNodes  
children 不会造成文本空白文本解析，获取到真实的子节点，不支持IE6，7，8浏览器  
childNodes 会造成解析空白文本  
### 获取节点方法  
#### firstChild/firstElementChild   
	两者区别：firstChild 获取第一个元素的子节点，在标准浏览器和IE9以上能获取到，   
	 
	firstElementChild 标准获取第一个元素子节点，IE6,7,8不支持。
	    
***  
#### lastChild/lastElementChild   
	两者区别：lastChild  获取最后一个子节点，在标准浏览器和IE9以上能获取到， 会获取到空白文本节点  
	 
	lastElementChild  标准获取最后一个元素子节点，IE6,7,8不支持。
	    
 ***   
#### nextSibling/nextElementSibling
    两者区别：nextSibling 获取下一个兄弟节点 在标准和IE9会获取到空白文本节点    
    
    nextElementSibling 标准获取下一个兄弟元素节点,IE6,7,8不支持。 
 ***  
 
#### previousSibling/previousElementSibling  
     两者区别：previousSibling 获取上一个兄弟节点，在标准和IE9会获取到空白文本节点。    
     
     previousElementSibling 标准获取上一个兄弟元素节点，IE6,7,8不支持。  
 ***   
#### parentNode  
     parentNode 获取指定元素的父节点。列子：  
     <ul>  
     	<li id="one"></li>  
     	<li></li>  
     	<li></li>  
     	<li></li>  
     </ul>  
     console.log(one.parentNode);  
***  
#### offsetParent  
     offsetParent 获取离指定元素最近的具有定位属性的祖先节点.列子：  
      <div id="one">  
      		<div id="two">  
      			<div id="three"></div>
      		</div>
      </div>  
      console.log(three.offsetParent);  
***  
#### document.createElement（“标签名”）  
     document.createElement 创建节点。‘列子：’   
     
     	var mant = document.createElement('span');
     	
      创建一个div标签，任何标签都可以  
***  
#### appendChild()  
     appendChild（）给指定元素添加子节点。‘列子：’  
     
     document.getElmentByTagName('body').appendChild(span);
       
     这就把span标签添加到body中了，不仅可以添加在body中摸一个标签中也是可以的。  
***  
#### insertBefore（）  
     insertBefore（插入的元素，参照的元素）。'列子：'  
     
     body.insertBefore(span,body.lastElementChild.previousElementSibling)；  
     
     将span标签插入到最后一个节点上一个兄弟节点处  
***  
#### removeChild()  
     removeChild 移除节点。‘列子：’  
     
     body.removeChild(body.firstElementChild.previousElementSibling)；  
     
     移除body中第一个节点的兄弟节点
*** 
#### replaceChild()  
     replaceChild(替换的元素，被替换的元素)。‘替换子节点’  
    
     body.replaceChild(span,body.firstElementChild);  
     
     将body中的第一个子节点替换成span标签  
*** 
##### cloneNode()  
     cloneNode()。克隆节点，
     接受一个布尔值作为参数，单参数为true时，回获取元素的innerHTML，false不会，默认是false  
***  
#### hasChildNodes（）  
     hasChildNodes（）判定元素是否拥有子节点，返回的是布尔值true和false  
***  
# 获取元素属性的方式  
1，元素属性名。获取不到非标准属性  
2，[“属性名”]  
以上两者获取元素的class的话，写的时候必须是className  
3，getAttribute（“属性名”）获取元素属性可以获取到元素的自定义属性    

**可以直接写class不能用calssName**

4，setAttribute （“属性名”，“属性值”）设置元素的自定义属性  
5，removeAttribute （“属性名”）移除元素属性  
6，attributes 能访问到所有元素属性，返回一个数组，可以通过下标的形式拿到每一个属性  
***
# 获取窗口可视区域的宽高  
####console.log(document.documentElementclienWidth)  
获取浏览器窗口可视区域宽度  
####console.log(document.documentElementclienHeight)  
获取浏览器窗口可视区域高度  
页面滚动时触发的事件    
    window.onscroll = function(){  
    	console.log(document.body.scrollTop);		}  
 
#### window.onload `页面加载完成后触发的事件`  

#### window.onresize `页面调整大小时触发的事件`  

#### window.onscroll `页面滚动时触发的事件`     
 获取页面滚动高度 谷歌和Safari用以下：  
 document.body.onscrollTop   
 其他浏览器 document.documentElement.crollTop    
 *** 
# img对象  
#### var img = new Image();  
**接受两个参数，分别代表图片的宽高,直接传数值，不需要加单位,如果只传一个参数，这个参数表示图片的宽度**
#### 图片对象事件有三种：  
	1，onload 图片加载成功时触发的事件  
	2，onerror 图片加载失败时触发的事件  
	3，onabort 当用户放弃加载时触发的事件  
#### 三种形式：
    1，hspace 图片左右的空间（留白）  
    2，vspace 图片上下的空白（留白）  
    3，complete 返回浏览器是否已经完成图像的加载 
#### 强调：
	因为图片是在给定src之后就开始加载，为了避免图片已经加载出来，
    但是事件还没来得及执行的极端情况，所以要把图片src赋值最好放到所有事件之后  
*** 