# ie8-problems-and-solution
ie8_problems and solution

  昨天做一个页面时，页面需要兼容到ie6+,在虚拟机下的ie6中，一个按钮点击时发送对应的ajax都是正常的，chrome,firefox等浏览器都是可以的，但是放在本机上的ie8浏览器上，却不可以。

  排查了各种原因，找了部门的前端老大一起解决了半个小时，终于解决了。

**问题1是：自己所写的js方法根本就没有加载，后来写了最简单的js,alert(11)；也不执行！**

   原来是js文件没有执行！！

  在ie8里进入淘宝页面后，再输入搜寻的商品时，跳不出对应的商品页面，但是却跳出这样的页面，即解决方法：可以去看一下链接：[https://s.bbs.taobao.com/detail.html?postId=2370973](https://s.bbs.taobao.com/detail.html?postId=2370973)

  下面就是自己最后解决的方法：

## Internet Explorer(IE)  ##

  1、先看看有没有禁用弹出框，如果禁用，点击工具-》弹出窗口阻止程序-》启用弹出窗口阻止程序。

  2、菜单栏中“工具”中选择“Internet选项”–>“安全”选项卡–>选择“Internet”（蓝色的小地球）–>“自定义级别”–>

![](http://om4hi8hop.bkt.clouddn.com/17-3-17/25480547-file_1489719582047_5f6c.png)


  3、将红线圈出来的进行勾选

![](http://om4hi8hop.bkt.clouddn.com/17-3-17/35032561-file_1489719474222_1a6.png)

  4、重启一下浏览器，再次键入网址，如果页面出现这样的

![](http://om4hi8hop.bkt.clouddn.com/17-3-17/13368026-file_1489719633713_251.png)

  即上面有淡黄色的提示，表示设置成功，这时不要管提示信息，点击关闭，隐藏此信息，再按ctrl+f5强制刷新一下要进入的页面，

  *之后就成功啦~~*

**问题2：如何获取select下选中的option值**

    用jquery很好解决：
	$('#select option:selected').val();
	

	但是对于ie低版本来说是不支持伪类的写法的，所以这里采用原生的js:
	var sel = document.getElementById('select');
	var selectIndex = sel.selectedIndex;
	var selectedValue；
	if(selectIndex){ //如果option有被选中，则获取对应的value值
	  selectedValue = sel.options[selectIndex].value;
	}else{ //如果option未被选中，则获取默认的value值
	  selectedValue = document.getElementByName('myselect')[0].value;
	}
