# Fittime Note

## Getting started

1. 安装node 0.12
2. 安装fis3，sudo nom i -g fis3
3. fis3 -v 
4. git clone 代码地址
5. sudo fis3 server info 查看当前服务是什么服务
     sudo fis3 server start 启动服务 —type 启动何种服务 -p 改端口
     sudo fis3 server -h 帮助文档
6. sudo fis3 server start —type jello -p 9090，可能会提示插件找不到，根据提示安装对应插件，优先fis3-开头的安装
7. 插件安装方式 sudo npm i -g 对应插件名称
8. sudo fis3 release 编译 -w监听 -d 输出到某个指定路径

## Fis3

前端js三方插件管理方式

1. sudo fis3 install zepto —save
2. 初始化三方插件安装
3. sudo fis3 install

## Git操作指南：

1. 从master分支新建一个分支：git checkout -b 763 origin/master --no-track
2. 第一次提交分支：git push --set-upstream origin 763
3. git checkout -b 759 origin/759   // 第一次切换分支这样搞
4. git checkout 759  // 第二次切换分支这样搞
5. merge代码：在当前分支下执行 git merge origin/hzm768;  把hzm768分支代码合到当前分支
6. git reset HEAD~1  回退到前一次提交，然后checkout 就能还原了
7. $ git push --delete origin titlebar   //删除远程分支
8. git branch -D titlebar //删除本地分支

## js

1. `new Number\(1\)`=>`Number {\[\[PrimitiveValue\]\]: 1}`,`Number\(1\)`=>`1`,new返回的是个对象

2. `new Date\('1991\/01\/01'\)`=> `Tue Jan 01 1991 00:00:00 GMT+0800 \(CST\)` 

   `new Date\('1991-01-01'\)`=> `Tue Jan 01 1991 08:00:00 GMT+0800 \(CST\)`使用-格式时间会自动到8点

3. 阻止文字选中

  `$('body').bind('selectstart',function(){return false})`

  `window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();`

4. `document.domain`可以拿到当前的域
5. `navigator.onLine`判断网络是否在线
6. `$(sel).data('shuxin','aaa')`修改，页面上的标签的data-shuxin不会自动变，使用`attr()`修改会变
7. `xhr.abort()`会触发`abort()`事件
8. 使用iframe实现上传文件[http://www.cnblogs.com/think_fish/archive/2011/03/29/1998455.html](http://www.cnblogs.com/think_fish/archive/2011/03/29/1998455.html)
9. from的action指向一个返回文件流的地址，提交表单会下载文件，如果想在当前页面内下载，可在页面内隐藏一个iframe,将form的target指向iframe的name
10. jquery事件参数中可以判断点击是否是左键

```javascript
$('#ftLayout').on('mousedown',function(e) { //只允许鼠标左键拖动 if (e.which != 1) { return; }})
```

11. 滑动鼠标加载更多数据

    ```javascript
    $(window).scroll(function(){
    if($(document).scrollTop()==0){
        //加载更多数据
    }
    })
    ```

12. jsmartk中定义变量`{%assign "repeat" $action.repeats[0]%}`

13. jQuery禁用浏览器的前进后退按钮

```javascript
$(document).ready(function() {
     window.history.forward(1);
     //OR
     window.history.forward(-1);
});
```

14. 如果这些CDN上的jQuery服务不可用，我们还可以通过以下代码来切换到本地服务器的jQuery版本：

```html
<script type="text/javascript" language="Javascript" src="http://ajax.aspnetcdn.com/ajax/jquery/jquery-1.4.1.min.js "></script>
<script type='text/javascript'>//<![CDATA[
if (typeof jQuery == 'undefined') {
document.write(unescape("%3Cscript src='/Script/jquery-1.4.1.min.js' type='text/javascript' %3E%3C/script%3E"));
}//]]>
</script>
```

15. `preventDefault()` 方法阻止元素发生默认的行为
    `stopPropagation()`该方法将停止事件的传播

    低版本ie下需要用`window.event.returnValue = false;`取消事件的默认行为 

16. 鼠标移动到表单元素松开，有时不会触发mouseup事件，在做拖动改变位置时要注意，只需要将被拖动的元素前加个蒙层即可解决

17. js获取视频时长

```javascript
// create the video element but don't add it to the page
var vid = document.createElement('video');
document.querySelector('#input').addEventListener('change', function() {
  // create url to use as the src of the video
  var fileURL = URL.createObjectURL(this.files[0]);
  vid.src = fileURL;
  // wait for duration to change from NaN to the actual duration
  vid.ondurationchange = function() {
    alert(this.duration);
  };
});
```

18. 关于移动使用fixed定位做蒙层，弹框中有输入框中存在的问题：
    1. android上键盘可能会挡住input，让弹框的子盒子离窗口顶部更近可解决，ios下无此问题
    2. ios上出键盘，下面部分蒙层盖不住，可以点击，原因是ios对`positon:fixed;`处理不好
19. 浏览器判断

```javascript
var ua = navigator.userAgent.toLowerCase();
function isWeixinBrowser() {
    return (/micromessenger/.test(ua)) ? true : false;
}

function isQQBrowser() {
    return (ua.match(/QQ/i) == "qq") ? true : false;
}

function isAndroid() {
    return (ua.match(/Android/i) != null) ? true : false;
}

function isIos() {
    return (ua.match(/iPhone|iPod/i) != null) ? true : false;
}
```

20. js启动app

```javascript
var timer;
var config = {
    /*scheme:必须*/
    scheme: 'xxapp://aa.com',
    download_url: '',
    timeout: 1000
};

function openclient(params) {
    var myConf = $.extend(config, params);
    var startTime = Date.now();
    if (isWeixinBrowser() || isQQBrowser()) {
            window.location = 'https://redirect.bb.net/?source=fittime&redirect=http%3A%2F%2Fa.app.qq.com%2Fo%2Fsimple.jsp%3Fpkgname%3Dcom.aa.app';
    } else {
        if (isAndroid()) {
            var ifr = document.createElement('iframe');
            ifr.src = myConf.scheme;
            ifr.style.display = 'none';
            document.body.appendChild(ifr);
            timer = setTimeout(function() {
                var endTime = Date.now();
                if (!startTime || endTime - startTime < myConf.timeout + 200) {
                    window.location = myConf.download_url;
                }
            }, myConf.timeout);
        } else {
            window.location = myConf.scheme;
        }
    }
}

document.addEventListener('visibilitychange', function() {
    var isHidden = document.hidden;
    if (isHidden) {
        clearTimeout(timer);
        // 动画停止
        // 服务器轮询停止 等等
    } else {
        // $.alert('页面开始');
        // 动画开始
        // 服务器轮询
    }
});

window.onblur = function() {
    clearTimeout(timer);
}
window.onpagehide = function() {
    clearTimeout(timer);
}
```

21. `Node.insertBefore()` 方法，在当前节点的某个子节点之前再插入一个子节点。

```
<div id="parentElement">
  <span id="childElement">foo bar</span>
</div>
<script>
// Create a new, plain <span> element
var sp1 = document.createElement("span");
// Get a reference to the element, before we want to insert the element
var sp2 = document.getElementById("childElement");
// Get a reference to the parent element
var parentDiv = sp2.parentNode;
// Insert the new element into the DOM before sp2
parentDiv.insertBefore(sp1, sp2);
</script>
```

22. `getComputedStyle()`与`currentStyle`
    currentStyle是IE浏览器自娱自乐的一个属性，其与element.style可以说是近亲，至少在使用形式上类似，element.currentStyle，差别在于element.currentStyle返回的是元素当前应用的最终CSS属性值（包括外链CSS文件，页面中嵌入的<style>属性等）。
    因此，从作用上将，getComputedStyle方法与currentStyle属性走的很近，形式上则style与currentStyle走的近。不过，currentStyle属性貌似不支持伪类样式获取，这是与getComputedStyle方法的差异，也是jQuery.css()方法无法体现的一点。
23. 图片基本处理（imageView2）http://blog.csdn.net/quiet_girl/article/details/50721119

## css

1. 两张图片之间有条白线，可能是图片宽高度与屏幕除不尽，渲染误差造成的
2. scss中+transform，可以自动自动带前缀的属性
3. position:sticky是一个新的css3属性，它的表现类似position:relative和position:fixed的合体，在目标区域在屏幕中可见时，它的行为就像position:relative; 而当页面滚动超出目标区域时，它的表现就像position:fixed，它会固定在目标位置
4. 使用CSS3中translatez会开启GPU硬件加速提升网站动画渲染性能

## other

1. SK3-7402-6134-9955-3470-7947 sketch key
2. webstorm如何实现代码全局搜索，试过设置ctrl+Shift+N和ctrl+Shift+alt+N但是只能查找到文件位置
   control+shift+F
3. sass --style expanded --watch css:css --style compressed
4. browser-sync start --server --files "*.html,css/**.scss,js/**.js" --no-notify

