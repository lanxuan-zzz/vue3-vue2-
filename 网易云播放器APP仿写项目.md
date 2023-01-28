# 网易云播放器APP仿写项目





## 技术点与收获

1. 屏幕大小适配

   ```js
   // 自动执行初始函数
   
   function remSize(){
       // 获取设备的宽度
       var deviceWidth=document.documentElement.clientWidth ||window.innerWidth
       // 设计稿最大像素为750
       if (deviceWidth>=750) {
           deviceWidth=750
       }
       // 最小为320
       if (deviceWidth<=320) {
           deviceWidth=320
       }
       // px=rpx ,rm=rem   //手机像素单位
       // 1rem=100px so 750px>1rem=100px,375px>1rem=50px
       document.documentElement.style.fontSize=(deviceWidth/7.5)+'px'
       // 设置字体大小
       document.querySelector('body').style.fontSize=0.3+'rem'
   }
   remSize()
   
   // 当窗口发生改变的时候
    window.onresize=function(){
       //  当大小发生变化时，再次调用初始函数前来适配屏幕
       remSize()
    }
   ```

   

2. vue3播放量计算转换

   ```js
   function changeCcount (num){
               if(num>=1000000000){
               return (num/1000000000).toFixed(1)+'亿'
               }else if(num>=10000){
               return (num/10000).toFixed(1)+'万'
               }
           }
   ```

   

3. 拿到数据渲染时（例如一些深度数据）页面已渲染，但数据没拿到导致页面不显示控制台报错.

   第一种方法
```js
sessionStorage.setItem('musicDatail',JSON.stringify(state))
//属性使用教学
localStorage 和 sessionStorage 属性允许在浏览器中存储 key/value 对的数据。
sessionStorage 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。
提示: 如果你想在浏览器窗口关闭后还保留数据，可以使用 localStorage 属性， 改数据对象没有过期时间，今天、下周、明年都能用，除非你手动去删除。
sessionStorage也可存储Json对象：存储时，通过JSON.stringify()将对象转换为文本格式；读取时，通过JSON.parse()将文本转换回对象。
var userEntity = {
name: 'tom',
age: 22
};

// 存储值：将对象转换为Json字符串
//第一个值为命名值，第二值为修改值
sessionStorage.setItem('user', JSON.stringify(userEntity));

// 取值时：把获取到的Json字符串转换回对象
var userJsonStr = sessionStorage.getItem('user');
userEntity = JSON.parse(userJsonStr);
console.log(userEntity.name); // => tom
//教学转载自csdn
```

   第二种方法（极为简洁）

```js
 <div v-if="playlist.creator!=null">
  //给外层套个div，你数据不出我就不渲染[dog]
//此方法来源于评论[666]
```


