#QueryList交流社区: [http://ql.44i.cc/](http://ql.44i.cc/)#QueryList交流QQ群:123266961 <a target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=a1b248ae30b3f711bdab4f799df839300dc7fed54331177035efa0513da027f6"><img border="0" src="http://pub.idqqimg.com/wpa/images/group.png" alt="╰☆邪恶 魔方☆" title="╰☆邪恶 魔方☆"></a>#QueryList简介***QueryList是一个基于phpQuery的通用列表采集类,是一个简单、 灵活、强大的采集工具，采集任何复杂的页面     基本上就一句话就能搞定了。#QueryList 使用```php//获取采集对象$hj = QueryList::Query('http://www.baidu.com/s?wd=jaekj',array('title'=>array('h3','text')));//输出结果：二维关联数组print_r($hj->jsonArr);//输出结果：JSON数据echo $hj->getJSON();```上面的代码实现的功能是采集百度搜索结果页面的所有搜索结果的标题,然后分别以数组和JSON格式输出。###QueryList  静态方法Query原型：>***Query***($page,$regArr,$regRange='',$getHtmlWay="curl",$output_encoding=false)一共有五个参数，后面三个参数是可选的>$page
>>类型: **string**  
>>说明: **必选参数，要抓取的网页URL地址(支持https)，或者是html源代码；这意味着你可以直接传一个网址给QueryList，也可以将通过自己的方式获取到的并经过你自己处理过的HTML源码传给QueryList**  

>$regArr
>>类型: **array**  
>> 说明: **必选参数，选择器数组，格式array("名称"=>array("选择器","类型"[,"标签过滤列表"][,"回调函数"]),.......[,"callback"=>"全局回调函数"]);**  
>>>+ **选择器**:可以为任意的jQuery选择器语法  
>>>+ **类型**：值 "text" ,"html" ,"HTML标签属性" 
>>>+ **标签过滤列表**:可选，当标签名前面添加减号(-)时（此时标签可以为任意的元素选择器），表示移除该标签以及标签内容;否则当 **类型** 值为text时表示需要保留的HTML标签，为html时表示要过滤掉的HTML标签。有减号与没有减号的区别就在于，有减号时会移除那个标签包括那个标签内的所有内容，没有减号时只会移除那个标签并不会移除标签内的内容
>>>+ **回调函数** / **全局回调函数**:可选，字符串（函数名） 或 数组（array("类名","类的静态方法")），回调函数应有俩个参数，第一个参数是选择到的内容，第二个参数是选择器数组下标，回调函数会覆盖全局回调函数  
>$regRange
>>类型:**array**  
>默认值:**''**  
>说明:**可选参数,块选择器,指 先按照规则 选出 几个大块 ，然后再分别再在块里面 进行相关的选择**  

>$getHtmlWay
>>类型:**string**   
>>默认值:**'curl'**  
>>可选值:**'curl','get'**  
>>说明:**可选参数,源码获取方式，指是通过curl抓取源码，还是通过file\_get\_contents抓取源码**  
>$outputEncoding
>>类型:**string**  
>>默认值:**false**  
>>可选值:**false,'UTF-8','GB2312'等**  
>>说明:**可选参数，输出编码格式，指要以什么编码输出(UTF-8,GB2312,.....)，防止出现乱码,如果设置为 假值 则不改变原字符串编码**###QueryList 属性* **得到多维数组格式的采集结果**	>***jsonArr***###QueryList 方法*  **重新设置选择器**	>void ***setQuery***($regArr,$regRange='')	一共两个参数,第二个参数是可选的，参数意义同构造函数。* **得到JSON格式的采集结果**	> string ***getJSON***()	无参，返回JSON字符串。##QueryList 依赖库```phpQuery```phpQuery项目主页:[https://code.google.com/p/phpquery/](https://code.google.com/p/phpquery/)##其它说明QueryList 内置的只是简单的源码抓取方法，遇到更复杂的抓取情况，如：需要登陆身份验证 时，请配合其它的PHP的HTTP类来使用，通过将辅助的HTTP类抓取到的网页源码传给QueryList即可。##DEMO站微动态:[http://querylist.jaekj.com/](http://querylist.jaekj.com/)* thinkphp版本:V3.1.2* QueryList版本:V1.6* 后台地址: /admin* 后台账号密码: guest guest这个demo站实现的功能相当于一个轻量级的微博站，内容全自动采集更新，可以自定义时间间隔采集任意站点的信息，自动更新到这个站点来，只需要在后台规则库简单的添加一条规则就可以实现全自动采集了，大家可以自行进入后台进行尝试，体验QueryList的魅力！冷云搞笑:[http://x.44i.cc/](http://x.44i.cc/)##作者信息```Author : JaegerEmail : hj.q@qq.com交流QQ群:123266961 ```##支持作者如果您觉得 QueryList 对您非常有用并希望QueryList能越来越好，您可以考虑通过捐赠来支持作者，您的帮助是对作者最大的支持和动力。<center> ![捐赠](http://git.oschina.net/jae/QueryList/raw/master/demo/thanks.png)  用手机扫描二位码支付</center>