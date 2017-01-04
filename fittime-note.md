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

## css

1. 两张图片之间有条白线，可能是图片宽高度与屏幕除不尽，渲染误差造成的
2. scss中+transform，可以自动自动带前缀的属性
3. position:sticky是一个新的css3属性，它的表现类似position:relative和position:fixed的合体，在目标区域在屏幕中可见时，它的行为就像position:relative; 而当页面滚动超出目标区域时，它的表现就像position:fixed，它会固定在目标位置
4. 使用CSS3中translatez会开启GPU硬件加速提升网站动画渲染性能

## other

1. SK3-7402-6134-9955-3470-7947 sketch key
2. webstorm如何实现代码全局搜索，试过设置ctrl+Shift+N和ctrl+Shift+alt+N但是只能查找到文件位置
   control+shift+F

