angular-form
============

<br>
##<h1>angularjs表单基础</h1>
---

<div style="margin-top:30px">

angularjs在表单方面最明显也最实用的特点，就是扩展了很多校验方面的指令，结合一些其他内置指令，可以让表单基本交互的实现变得非常简单。下面一个最简单的例子，大家随意感受下：
</div>
<br>
<iframe width="100%" height="300" src="http://jsfiddle.net/ddcat1115/rLgY9/28/embedded/html,css,result" allowfullscreen="allowfullscreen" frameborder="0"></iframe>
<br>
<div style="margin-bottom:50px;">
可以看到，不用任何js，也能实现基本的校验，报错展示，防重复提交等表单所需的基本功能，这依赖于angular对form及其内部的表单控件的扩展。
</div>


###<div style="margin-bottom:20px;">（一）对form的扩展</div>
**<strong style="line-height:1.5;font-size:16px;">位于ng-app内部的form标签，已经被包装过，实际上是一个angular内置指令，它创建了一个FormController</strong>[^1]<strong style="line-height:1.5;font-size:16px;"> 实例 ，该对象（form）具有一些原生form不具备的属性和方法</strong>**

[^1]: <http://docs.angularjs.org/api/ng/type/form.FormController>

* <div>可嵌套</div>
* <div>具有的属性</div>
	* <div>$pristine——没有填写记录，bull</div>
	* <div>$dirty——有填写记录，bull</div>
	* <div>$valid——通过验证，bull</div>
	* <div>$invalid——未通过验证，bull</div>
	* <div>$error——错误信息，对象，主要包含以下几个属性，属性值为对应字段列表(貌似直接用form的$error属性的比较少)</div>
		* <div>email</div>
		* <div>max</div>
		* <div>maxlength</div>
		* <div>min</div>
		* <div>minlength</div>
		* <div>number</div>
		* <div>pattern</div>
		* <div>required</div>
		* <div>url</div>

<div>在html代码里用form的name值就可获取该对象，进一步可获取其属性（如：formName.$valid），结合ng-show,ng-disabled等指令即可实现报错展示，按钮置灰等基本效果</div>

	- <div>可以给form标签加上“novalidate”，用来禁掉html5内置校验</div>
	- <div>如果要用原生form，可以给form标签加上“ng-pristine”指令</div>
		

###<div style="margin-bottom:20px;">（二）对表单控件的扩展</div>

**<strong style="line-height:1.5;font-size:16px;">跟form一样，表单内的所有控件也不再是原生控件，而是NgModelController</strong>[^2] <strong style="line-height:1.5;font-size:16px;">的实例，它同样拥有上面form的五个属性</strong>**

[^2]: <http://docs.angularjs.org/api/ng/type/ngModel.NgModelController>

<div>angular对input的type属性进行了扩展，主要包含以下几种</div>

* <div>number，附带多了max ， min 属性</div>
* <div>url</div>
* <div>email</div>

<div>此外可用的控件属性主要有</div>

* <div>ng-model——绑定的数据</div>
* <div>required——是否必填</div>
* <div>ng-minlength——最小长度</div>
* <div>ng-maxlength——最大长度</div>
* <div>ng-pattern——匹配模式</div>
* <div>ng-change——值变化时的回调</div>

<div>在代码里用formName.inputName即可获取该控件对象，进一步可获取其各个属性，结合ng-show等指令即可实现大部分校验功能</div>

	- <div>控件必须加ng-model,否则无法校验</div>


###<div style="margin-bottom:20px;">（三）内置css</div>

<div>内置了四种动态类</div>

* <div>ng-valid——验证通过时自动添加</div>
* <div>ng-invalid——验证失败时自动添加</div>
* <div>ng-pristine——未填入任何数据前</div>
* <div>ng-dirty——填过数据后</div>

<div>可以通过设置类似 input.ng-valid{color:green;} 来实现表单样式的状态转换</div>

###<div style="margin-bottom:20px;">（四）自定义指令…</div>

<div>可以通过自定义指令的方式来进一步扩展校验规则，表单控件等，不过那是另一个故事了，待续…</div>


