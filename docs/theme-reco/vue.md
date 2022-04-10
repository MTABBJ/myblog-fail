---
title: vue入门笔记
date: 2022-01-18
---

[视频链接](https://www.bilibili.com/video/BV12J411m7MG)

[toc]
<hr>

# 一、Vue基础
## 03.第一个Vue程序
1. 导入开发版本的Vue.js
2. 创建Vue实例对象，设置el属性和data属性
3. 使用简介的模板语法，把数据渲染到页面上

## 04.el挂载点
 el是用来设置Vue实例的挂载（管理）的元素
> #### Vue实例的使用范围是什么？
>    Vue会管理el选项命中的元素及其内部的后代元素
> #### 是否可以使用其他的选择器？
>    可以使用其他的选择器，但是建议使用<hh style="color:red">id选择器</hh>
> #### 是否可以设置其他的dom元素？
>    可以使用其他的双标签，<hh style="color:red">不能使用HTML和BODY</hh>

## 05.data数据对象
* Vue中用到的数据定义在data中
* data中可以写复杂类型的数据
* 渲染复杂类型数据时，遵守js语法即可

# 二、本地应用
## 07. v-text指令
* 设置标签的文本值
* 默认写法会替换全部内容，使用差值表达式{{}}可以替换指定内容
* 内部支持写表达式

## 08. v-html指令
* 设置元素的<hh style="color:red">innerHTML</hh>
* 内容中有html结构会被解析为标签
* 而v-text指令无论内容是什么，只会解析为文本
* 解析文本使用v-text，需要解析html结构使用v-html

## 09. v-on指令
* 为元素绑定事件
* 事件名不需要写on
* 指令可以简写为@
* 绑定的方法定义在methods属性中
* 方法的内部通过this关键字可以访问定义在data中的数据

## 10.计数器
逻辑：
1. data中定义数据：比如num
2. 在methods中添加两个方法：比如add(递增)，sub(递减)
3. 使用v-text将num设置给span标签
4. 使用v-on将add、sub分别绑定给+、-按钮
5. 累加的逻辑：小于10累加，否则提示
6. 递减的逻辑：大于0递减，否则提示

> 总结：
> * 创建Vue示例时:<hh style="color:red">el</hh> (挂载点),<hh style="color:red">data</hh>(数据),<hh style="color:red">methods</hh>(方法)
> * <hh style="color:red">v-on</hh>指令的作用是绑定事件,简写为<hh style="color:red">@</hh>
> * 方法中通过<hh style="color:red">this</hh>,关键字获取<hh style="color:red">data</hh>中的数据
> * <hh style="color:red">v-text</hh>指令的作用是:设置元素的<hh style="color:red">文本值</hh>,简写为<hh style="color:red">{{}}</hh>
> * <hh style="color:red">v-html</hh>指令的作用是:设置元素的<hh style="color:red">innerHTML</hh>

## 11.v-show指令
> 根据表达值的真假，切换元素的显示和隐藏
> 如：广告、遮罩层
* 根据真假，切换元素的显示状态
* 原理是修改元素的display，实现显示隐藏
* 指令后面的内容，最终都会解析为布尔值
* 值为true元素显示，值为false元素隐藏
* 数据改变之后，对应元素的显示状态会同步更新
 
## 12.v-if指令
> 根据表达值的真假，切换元素的显示和隐藏(操纵dom元素)
* 根据真假，切换元素的显示状态
* 本质是通过操纵dom元素来切换显示状态
* 表达式的值为true，元素存在于dom树中；为false，从dom树中移除
* 频繁的切换使用v-show，切换消耗小；反之使用v-if

## 13.v-bind指令
> 设置元素的属性
> 比如：src、title、class
> v-bind:属性名=表达式
* 为元素绑定属性
* 完整写法是<hh style="color:red"> v-bind：属性名</hh>
* 简写的话可以直接省略v-bind，只保留 <hh style="color:red">:属性名</hh>
* 需要动态的增删class时，建议使用对象的方式

## 14.图片切换
1. 定义图片数组
2. 添加图片索引
3. 绑定src属性
4. 图片切换逻辑
5. 显示状态切换
>  a标签 <hh style="color:red">href="javascript:void(0)"</hh> :为了防止a标签跳转
* 列表数据使用<hh style="color:red">数组</hh>保存
* v-bind指令可以设置元素属性,比如src
* v-show和v-if都可以切换元素的显示状态, <hh style="color:red">频繁切换用v-show</hh>

## 15.v-for指令
* 根据数据生成列表结构
* 数组经常和<hh style="color:red">v-for</hh>结合使用
* 语法是<hh style="color:red">(item,index) in 数据 </hh>
* item 和 index 可以结合其他指令一起使用
* 数组长度的更新会同步到页面上，是响应式的

## 16.v-on指令补充
* 事件绑定的方法写成<hh style="color:red">函数调用</hh>的形式，可以传入自定义参数
* 定义方法时需要定义<hh style="color:red">形参</hh>来接收传入的实参
* 事件的后面跟上<hh style="color:red"> .修饰符 </hh> 可以对事件进行限制
* <hh style="color:red">.enter </hh>可以限制触发的按键为回车
* 事件修饰符有多种
https://cn.vuejs.org/v2/api/#v-on

## 17.v-model指令
> 获取和设置表单元素的值（双向数据绑定）
* 便捷的设置和获取表单元素的值
* 绑定的数据会和表单元素值相关联
* 绑定的数据←→表单元素的值


## 19.小黑记事本-新增
1. 生成列表结构(v-for 数组)
2. 获取用户输入(v-model)
3. 回车，新增数据(v-on .enter 添加数组)
4. 通过审查元素快速定位

## 20.小黑记事本-删除
> 点击删除指定内容(v-on splice 索引)
1. 数据改变,和数据绑定的元素同步改变
2. 事件的自定义参数
3. splice方法和作用 (根据索引删除对应元素)

## 21.小黑记事本-统计
> 统计信息个数(v-text length)
1. 基于数据的开发方式
2. v-text指令的作用 


## 22.小黑记事本-清空
> 点击清除所有信息（v-on）
1. 基于数据的开发方式

## 23.小黑记事本-隐藏
> 没有数据时,隐藏元素(v-show v-if 数组非空)

## 小黑记事本总结
>  总结：
> * 列表结构可以通过<hh style="color:red">v-for</hh>指令结合数据生成
> * <hh style="color:red">v-on</hh>结合事件修饰符可以对事件进行限制,比如<hh style="color:red">.enter</hh>
> * <hh style="color:red">v-on</hh>在绑定事件时可以传递自定义参数
> * 通过<hh style="color:red">v-model</hh>可以快速的设置和获取表单元素的值
> * 基于数据的开发方式


# 三、网络应用
## 25.axios基本使用
* <hh style="color:red">axios</hh>必须先导入才可以使用
* 使用<hh style="color:red">get</hh>或<hh style="color:red">post</hh>方法即可发送对应的请求
* <hh style="color:red">then</hh>方法中的回调函数会在请求成功或失败时触发
* 通过回调函数的形参可以获取相应内容,或错误信息

axios文档传送门 https://github.com/axios/axios

## 26.axios+vue
* axios回调函数中this已经改变，无法访问到data中数据
* 把this保存起来，回调函数中直接使用保存的this即可
* 和本地应用的最大区别就是改变了数据来源

## 28.天知道-回车查询
逻辑:
 1. 按下回车 (v-on .enter)
 2. 查询数据 (axios接口 v-model)
 3. 渲染数据 (v-for数组 that)
> * 应用的逻辑代码建议和页面分离，使用单独的js文件编写
> * axios回调函数中this指向改变了，需要额外的保存一份
> * 服务器返回的数据比较复杂时，获取的时候需要注意层级结构

## 29.天知道-点击查询
逻辑:
 1. 点击城市 (v-on 自定义参数)
 2. 查询数据 (this.方法() )
 3. 渲染数据 (v-for数组 that)
 > * 自定义参数可以让代码的复用性更高
 > * methods中定义的方法内部，可以通过this关键字点出其他的方法



# 四、综合应用
## 31.悦听-歌曲搜索
逻辑：
1. 按下回车（v-on .enter）
2. 查询数据（axios接口 v-model）
3. 渲染数据（v-for数组 that）

> * 服务器返回的数据比较复杂时，获取的时候需要注意<hh style="color:red">层级</hh>结构
> * 通过<hh style="color:red">审查元素</hh>快速定位到需要操纵的元素
> 
## 32.悦听-歌曲播放
逻辑：
1. 点击播放（v-on）
2. 歌曲地址获取（接口 歌曲id）
3. 歌曲地址设置（v-bind）
> * 歌曲id依赖歌曲搜索的结果，对于不用的数据也需要关注

## 33.悦听-歌曲封面
逻辑：
1. 点击播放(增加逻辑)
2. 歌曲封面获取（接口 歌曲id）
3. 歌曲封面设置（v-bind）


## 34.悦听-歌曲评论
## 35.悦听-播放动画
## 36.悦听-播放mv