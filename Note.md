



# 八股文



## 一、HTML篇



### HTM5新标签

**语义化标签**

* header 头部布局标签
* nav 导航标签，h4中主要使用ul搭配li制作导航栏，h5中可以直接使用nav
* main 主要内容
* footer 尾部布局
* article 页面中独立的内容布局
* section 块级标签
* aside 独立内容之外，但是和article有关联的布局（侧边栏）

**音视频标签**

* audio 音频标签
* video 视频标签

**表单标签**

* email 邮箱
* url url地址
* number 数字

**其他标签**

* svg 矢量图
* canvas
* figure figurecaption 包裹多媒体内容和他们的标题



### HTML语义化

HTML语义化是指在用HTML构建页面时，避免大篇幅的使用无语义的标签，尽可能多的使用有语义的标签。

HTML语义化的作用：

* 提高代码的可读性
* 利于页面结构化。在没有css的情况下，也能呈现出良好的结构
* 利于SEO（Serach Engine Optimization），爬虫依赖标签确定关键字的权重，可以和搜索引擎建立良好沟通

常见的语义化标签：header、main、footer、articel、section、aside、nav、h1-h6、p、input、textarea、video、audio





---------



## 二、CSS篇



### CSS盒模型

* 内容区：content 
* 内边距：padding
* 边框：border
* 外边距：margin

根据盒子大小计算方式不同盒模型分为两种：标准盒模型和怪异盒模型。

* 标准盒模型：box-sizing：content-box，给盒子设置width和height，实际上设置的是content部分，盒子的宽度还需要考虑率border和padding
* 怪异盒模型：box-sizing：border-box，给盒子设置width和height，包含了padding和border，设置的宽高就是盒子实际的宽高



### CSS选择器

**基本选择器**

* 通配选择器 `*`
* 标签选择器（元素选择器）`p`
* 类选择器（多类名选择器）`.box`
* ID选择器 `#nav`

**复合选择器**

* 并集选择器 `p, div`
* 交集选择器 `div.box`
* 子元素选择器 `ul > li`
* 后代元素选择器 `ul li`
* 相邻兄弟选择器 `p + span`
* 通用兄弟选择器 `p ~ span`
* 属性选择器 `img[src=xxx]`

**伪类选择器**

* 结构伪类 `:`
  * `:first-child :last-child :nth-child(an+b) `
  * `:first-of-type() :last-of-type() `
  * `:only-child()`
* 链接伪类 `:link :visited :hover :active :focus`
* 否定伪类 `:not()`

**伪元素选择器**



### CSS优先级与权重

* ！import的样式具有最高优先级，优先于所有样式
* 行内样式优先级最高，嵌入和外链样式遵循层叠性规则，即权重一样，后面的会覆盖前面的
* 按照特指度排列
  * 行内样式 1，0，0， 0
  * ID选择器 0，1，0，0
  * 类选择器、伪类选择器、属性选择器 0，0，1，0
  * 标签选择器 0，0，0，1
  * 通配选择器 0，0，0，0
* 继承的样式不具有优先级，最后考虑继承



### CSS单位

* px：像素，绝对长度的单位，取决于电脑的分辨率，开发中常使用的单位。

* em：相对长度单位，font-size中使用是相对父元素的字体大小，其他属性中使用是相对自身的字体大小。如果当前未设置字体大小，则向上搜索其父元素的字体大小，直至浏览器的默认字体大小。

* rem：相对长度单位，相对根元素的字体大小，若根元素字体大小未设置，则默认相对浏览器字体大小。

* vw：相对长度单位，相对当前视窗宽度的1%

* vh：相对长度单位，相对当前视窗高度的1%

  

### 浮动

① 浮动的作用：

* 设置浮动的图片，可以实现文字环绕图片
* 设置了浮动的块级元素可以排列在同一行
* 设置了浮动的行内元素可以设置宽高（获得行内块元素特性），同时可以按照浮动设置的方向对齐排列盒子。

② 设置浮动元素的特点： 

* 设置了浮动，该元素脱标（脱离标准流），元素不占位置。
* 浮动可以进行模式转换（拥有了行内块元素的特性） 

③ 浮动造成的影响：使盒子脱离文档流，如果父级盒子没有设置高度，需要被子盒子撑开，那么这时候父级盒子的高度就塌陷了，同时也会造成父级盒子后面的兄弟盒子布局受到影响。如果浮动元素后面还有其他兄弟元素，其他兄弟元素的布局也会受到影响。

④ 清除浮动的方法：

* 伪元素清除浮动：给浮动元素父级增加 .clearfix::after { content: ''; display: table; clear: both; } /*兼容IE低版本 */ .clearfix { *zoom: 1; } 
* overflow：hidden：给浮动元素父级增加overflow：hidden属性 
* 额外标签法：给浮动元素父级增加标签 
* 三种清除浮动的特点和影响 
  - 伪元素清除浮动：不会新增标签，不会有其他影响，是当下清除浮动最流行的方法
  -  overflow：hidden：不会新增标签，但是如果父级元素有定位元素超出父级，超出部分会隐藏，在不涉及父级元素有超出内容的情况，overflow：hidden比较常用，写法方便简洁 
  - 标签插入法：清除浮动的语法加在新增标签上，由于新增标签会造成不必要的渲染，所以这种方法目前不建议使用



### 定位

css有static、inherit、relative、absolute、fixed、sticky等定位方法

#### static

静态定位。css中的默认定位方法，也就是没有定位。静态定位下top、bottom、right、left、z-index等属性都是无效的。

#### inherit

继承定位。继承父元素的定位方式，若父元素没有定位，则子元素也没有定位。

#### relative

相对定位。相对定位是指相对盒子原有位置进行偏移，**相对定位下的盒子没有脱离标准流**，仍占有原来位置。

#### absolute

绝对定位。绝对定位是指相对外层第一个有定位（非static）的祖先元素进行偏移，**绝对定位的盒子会脱离标准流**。

#### fixed

固定定位。固定定位是指相对浏览器窗口进行偏移（不管滚条怎么滑动），**固定定位的盒子会脱离标准流。**

#### sticky

可以看成是relative和fixed的结合，初始状态为relative，随着浏览器视口的移动，会变成fixed。

它的具体规则是，当页面滚动，父元素开始脱离视口时（即部分不可见），只要与`sticky`元素的距离达到生效门槛，`relative`定位自动切换为`fixed`定位；等到父元素完全脱离视口时（即完全不可见），`fixed`定位自动切换回`relative`定位。



### Flex布局

Flex布局，全称Flexible Box（弹性盒布局），为盒子模型提供了最大的灵活性。任何一种元素都可以指定Flex布局。

指定方法：使用display: flex、display: inline-flex（行内元素）、display: -webkit-flex;（safari）

#### 容器和项目

采用flex布局的元素称为容器，采用flex布局的子元素称为项目。若父元素采取flex布局，则全部子元素自动成为项目。



### 水平/垂直居中方法













-------



## 三、Js篇



### Js数据类型

Js数据类型有两类，分别是**基本类型**，也叫简单类型和**引用类型**，也叫复杂类型。

基本类型（简单类型）主要包括**Number、BigInt、Symbol、Null、Undefined、String、Boolean**

引用类型（复杂类型）只有**Object（包括Array、Object、Function、RegExp等）**

基本类型是**存储在栈内存**的简单数据段，每一块栈内存中存储着实际值，占据空间小，使用较频繁。

因此，为基本类型的变量赋值时，会先开辟一块新的栈内存，然后将该值拷贝，形成一个副本。

引用类型**存储在堆内存**中，占据空间大。**每一块栈内存中存储着指针**，该指针指向堆内存中该实体的起始地址，当解释器寻找引用类型值时，会先检索其在栈中的地址，取得地址后从堆中获得实体。

因此，存储引用类型的变量，就是一个指针。给另一个变量赋引用类型的值，实际上只是传递了指针，他们指向的是同个对象。



### Js判断数据类型

js判断数据类型有四种方法：typeof、instanceof运算符、constructor、Object.prototype.toString().call()

* Typeof: 常用于**判断基本类型**，对于引用类型和Null，除了function显示为‘function’，其余全部为‘object’。
  * 检测原理为：利用底层数据的**二进制结构**判断。
* Instanceof：用于测试检测的类型是否在当前实例的原型链上，不太适合简单类型的检测，无法检测Null、Undefined、Symbol等。
  * 检测原理为：验证当前类的原型，是否出现在实例的**原型链**上，只要出现就返回true。
* Constuctor：用于**检测引用类型**，具体原理是检查实例的构造函数是否和某个类相等，如果相等则说明是该类型的实例，这种方法不会考虑原型链上其他元素，避免了原型链的干扰。
  * 检测原理为：根据**构造器**判断
* Object.prototype.toString.call(data)：适用于**所有类型的检测**，返回该数据类型的字符串。
  * 检测原理为：Object.prototype.toString返回一个类型的字符串，使用call可以改变this指向，从而适用不同的数据。



### 数组去重

* 对象属性：

  遍历数组，将数组的每个值作为key加入到一个对象中去，每遍历一个元素就判断该元素是否已经加入到对象中。优点是效率高，缺点是占用了较多的空间，使用了一个查询对象和新的数组。

  ```js
  function m1(arr) {
      const table = {};
      for (let i = 0; i < arr.length; i++) {
          if (table[arr[i]] === undefined) {
              table[arr[i]] = arr[i];
          }
      }
  
      const ans = [];
      for (prop in table) {
          ans.push(table[prop]);
      }
  
      return ans;
  }
  ```

  

* new Set()：

  将数组传入构造函数，返回一个集合，再将集合转为数组。优点是代码简单易懂，缺点是可能有兼容性问题。

  ```js
  function m2(arr) {
      const set = new Set(arr);
      return Array.from(set);
  }
  ```



* filter+indexOf

  过滤出index === indexOf（item）的元素，即实现去重

  ```js
  function m3(arr) {
      return arr.filter((item, index) => {return arr.indexOf(item) === index} )
  }
  ```

  

* 移动法

  从头遍历元素，如果元素未出现过，就将元素从头部移出，再从尾部插入；若出现过则直接移除。

  ```js
  function m4(arr) {
      let len = arr.length;
      for (let i = 0; i < len; i++) {
          if (arr.indexOf(arr[0]) === arr.lastIndexOf(arr[0])) {
              const head = arr.shift();
              arr.push(head);
          } else {
              arr.shift();
          }
      }
      return arr;
  }
  ```

  

### null和undefined的区别

undefined是全局对象的一个属性，**【当一个变量没被赋值】【一个函数没有返回值】【某个对象不存在某个属性却被访问了该属性】【函数定义形参但未传递实参】**，得到的结果都是undefined。undefined有自己的数据类型Undefined，通过typeof判断undefined返回值为'undefined'，undefined==undefined， undefined == =undefined。

null代表对象的值未设置，一个对象没有设置指针就是null。null通过typeof判断得到的结果是'object'，null==null, null == =null, null == undefined, null  ! == undefined。

undefined是一个变量的初始状态，而null则是人为设置的空状态，如果想要销毁一个对象，直接赋值为null即可。

null属于自己的类型Null，而不属于Object。为什么typeof会判断为object，是因为数据在底层都是以二进制存储的，**前三位为0会被判定为Object，null的二进制位恰好都是0。**



### map和forEach的区别

**相同点**

* 二者都是数组提供的**迭代方法**
* 均接受一个**回调函数**（数组项、该数组项的索引、原数组）
* 均**不能被return/break语句打断**

**不同点**

* **map有返回值**，开辟新空间，返回一个和原数组长度一致的新数组，**一般不修改原数组**
* **forEach默认无返回值**，**一般用于修改原数组**
* map的效率高于forEach



### Js变量提升

Js变量提升是指在**编译时，使用Js声明的变量和函数会被提到代码的最前面。**

变量提升的条件是：**必须使用var声明变量**，而不能使用let、const等关键字声明

变量提升时，**只有变量声明会被提升**，赋值不会被提升，且函数会先于变量被提升。

变量提升的结果是：可以在变量初始化之前访问该变量，返回的是undefined；在函数声明前可以调用该函数（必须是函数声明）

使用let、const声明变量的语句之前，形成**暂时性死区**，如果在该区域访问变量会报错。





------



## 四、开发工具篇



#### 开发用到的工具有哪些？

vscode、git、chrome、postman



#### git的基本操作有哪些？

**本地操作**

* git init **-- 创建一个本地的git仓库**

* git status **--查看当前文件的状态（untracked、modified、unmodified、staged）**

* git status -s **--查看当前文件状态（简短）**

  * ?? **未追踪文件**
  * A **已经被加入暂存区**
  * 红色M **文件修改后未提交至暂存区**
  * 绿色M **文件修改后已经提交至暂存区**
  * D **表示在工作区已删除**

* git log **--查看提交日志**

* git reset --hard < commitID > **--回退到某一版本**

* git reflog **--查看完整的日志**

* git diff HEAD -- < file > **-- 查看工作区和git仓库代码的区别**

* git add < file > **--将文件添加至暂存区**

* git add . **--将所有Untracked的文件添加至暂存区**

* git commit -m **--将暂存区所有文件提交至git仓库**

* git  checkout -- < file > **--丢弃对工作区文件的修改、将工作区中误删的文件还原**

* git reset HEAD < file > **--将暂存区的文件回退到工作区**

* git rm < file > **--将git仓库里的文件删掉**

  

**远程仓库操作**

* git remote add origin git@github.com:ElioChiu/learngit.git **链接到远程github仓库**

* git push -u origin main **本地git仓库推送至远程仓库（第一次推送）**

* git push origin main  **本地git仓库推送至远程仓库（非第一次推送）**

* git remote rm < repository > **删除远程仓库(只是解除远程仓库和本地之间的关系)**

* git remote -v **查看远程库版本**

* git clone git@github.com:ElioChiu/learngit.git 从远程仓库克隆到本地仓库

  

**分支操作**

* git branch **查看分支**
* git branch < name  >**创建新分支**
* git checkout < name > / git switch < name > **切换到某分支**
* git checkout -b < name >/git switch -c < name >**创建+切换到新分支**
* git merge < name > **合并某分支到当前分支**
* git branch -d < name > **删除某分支**



-----



## 五、计算机网络篇



------



## 六、Vue篇



### v-if和v-show的区别

**相同点**

均能实现特定条件下显示或隐藏元素的需求，接受true则显示，接受false则隐藏

**不同点：**

二者控制元素显示和隐藏的机制不同：

v-if在接受true时动态创建该元素，接受false时动态删除该元素。

v-show在接受true时将元素的display属性设置为block，接受false时将元素的display属性设置为none

v-show适合频繁切换显示/隐藏状态的元素，性能高于v-if，v-if比较消耗性能



### v-for为什么要加key

为了性能优化。

vue是虚拟dom，在更新dom时要使用diff算法进行比对。

如果没有key，在每次更新dom时都要重新渲染一次页面，性能消耗很大。

如果有key，就可以按照key值对比元素，只需创建新的li元素即可，不需要对其它元素重新进行渲染。

key值不能指定为列表元素的index，因为index不能和元素一对一的绑定。

例如数组[1, 2, 3]，此时1和index0绑定，在数组前插入一个0，则0和index0绑定，且整个数组的index都发生了变化。



-----



## 七、Ajax篇



### 如何创建Ajax

1. 创建XHR对象

   ```JS
   const xhr = new XMLHttpRequest();
   ```

2. 请求参数设置

   ```js
   xhr.open(请求方式, URL)
   ```

3. 发送请求

   ```JS
   xhr.send()
   // get请求不需要参数
   // post请求需要data参数
   ```

4. 监听请求成功后的状态变化

   ```JS
   xhr.onreadystagechange() = function() {
       if (xhr.readyState === 4 && xhr.status === 200) {
           console.log(xhr.responseText);
           xhr = null;
       }
   }
   ```

   
