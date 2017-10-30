# WebProject
Learn How to Build Website 


## HTML5 布局标签
- 通用的布局标签：<div>
    - 语义：无明确含义，通常代表“盒子”
    - 应用：根据布局的需要，可以使用到人和地方
    - 应用：可以通过id和class进行区分
- HTML5新增的常用布局标签：
    |标签|说明|
    |:-:|:-:|
    |header|页面或区域的头部|
    |footer|页面或区域的底部|
    |nav    |导航|
    |section|文档中的章节、区段、板块等（类似div，但主要针对文档类区域）|
    |aside  |侧边栏|
    |article|文章/文档|

- CSS：float浮动
    - 作用：将页面元素浮动起来，使其能够向左或者向右排列
    - 应用：
        - 实现页面中布局的左右排版。
        - 实现图文环绕的版式效果
    - 值：
        |值|说明|
        |:-:|:-:|
        |left| 元素本身向左浮动|
        |right| 元素本身向右浮动|
        |none| 元素不浮动（默认值）|

    - 原理：
        - 浮动元素将脱离默认的文档流，漂浮在默认文档流之上。
        - 浮动的元素会向左或向右移动，直到它的边缘碰到父级元素或这个元素之前的另一个浮动元素的边框为止。
    - 特点：对齐方式
        
        不管元素如何浮动，始终以父级容器或它前面同层次并列的元素作为参考进行对齐。
- CSS：clear 清除浮动
    - 作用：规定元素的某一侧不允许存在浮动元素。
    - 应用：消除其他浮动元素对其产生的影响。
    - 值：
        |值|说明|
        |:-:|:-:|
        |both| 两侧都不允许浮动元素|
        |left| 清除元素左侧的浮动元素|
        |right| 清除元素右侧的浮动元素|
        |none| 无清除效果（默认效果）|
    - 实际应用：
        - 解决网页中的“塌陷”问题
        - 塌陷：如果父元素质保函浮动元素，那么在未设置高度的同事，父元素的高度塌陷为0.
    - 解决塌陷的方法：
        1. 创建一个用来清除浮动的CSS样式类（clearfix)
        2. 针对包裹的诠释浮动元素的父级容器使用(clearfix)
        ```css
            .clearfix {zoom:1;} /*zoom属性：IE浏览器专用属性，为老版本的IE所写，为兼容考虑*/
            .clearfix:after {   /*after 伪对向选择符--在这个对象被浏览器渲染后添加一定的内容*/
                content:".";    /*这个属性是专门配合伪对象的，必须写*/
                display:block;  /*将添加进去的内容转换为块状*/
                bisibility:hidden;  /*可视化属性，但无论是否可见，都保留其物理空间，与(display:none)不同*/
                height:0;       /*将添加进去的内容高度设置为0，消除其占位*/
                clear:both;
            }
        ```
## 主流布局的类型（入门级）
- 静态布局（Static）
    - 静态布局是针对PC端的传统Web设计。
    - 设计一个剧种布局，一般具有固定的宽度。当浏览器窗口缩小时，页面内容会被遮挡，呈现横竖向滚动条
    > PS: 入门级布局
- 响应式布局（Responsive）
    - 针对越来越多的移动端设备，一个web设计能够兼容多个终端。
    - 通过CSS3中的Media Query（媒介查询），采用栅格化方式，分别为不同的屏幕终端定义布局。
- 弹性布局（Flexbox CSS3新布局模式）
    - 为了实现响应式布局，CSS3提供的一种最新布局模式。
    - 提供更加高效的方式来对布局容器的子元素进行排列、对齐和分配空白空间。
- PC站常见的布局
    - 一列布局（静态布局）：一列自适应居中
        - 两个要点：
            1. 页面内容区域有一个固定宽度。
            2. 页面内容区域在浏览器窗口中自适应剧种。
        - 实现方法：

            页面内容区域box{width:自定义宽度;margin:0 auto;}
        - 固定宽度的设置：
            - 以主流分辨率来判断
            - 建议（目前）以1200为判断基准
    - 两列布局：一列固定宽 + 一列自适应
        - 固定宽度列：
            
            通常称为边栏，主要放置一些固定性内容，如导航、菜单。
        - 自适应列：
            根据浏览器窗口大小自动判断宽度，主要放置主题内容。
        - 应用场景：
            
            后台管理、用户中心、博客等。
        - 实现方法：
            - 固定列容器：{width:固定数值;float:left/right;}
            - 自适应列容器：{margin-方向:数值=固定列宽;}
    - 三列布局（双飞翼布局）：中间列自适应宽度 + 左右列固定宽度
        - 中间放置主体内容，在浏览器中优先渲染
        - 原理：当子元素处于浮动状态时，设置负margin >= 子元素宽度时，子元素会叠加到兄弟元素身上
## CSS 样式
- CSS:文本样式
    - text-align 设置文本的水平对齐方式
        - 必须用于块状元素，入`<p>,<div>`.定义内部文本及内联元素如何横向对齐
        - 默认是`start`,取决于html文档的`direction`属性设置（默认都是从左到右，`left`。如果从右到左就相当于`right`）
        - 值：
            |值|说明|
            |:-:|:-:|
            |left| 左对齐|
            |center| 居中|
            |right| 右对齐|
            |justify| 两端对齐（老浏览器支持度不好，新浏览器效果不错）|
    - text-decoration 设置文本的修饰方式
        - 值：
            |值|说明|
            |:-:|:-:|
            |none| 无修饰|
            |underline| 下划线|
            |line-through| 删除线|
            |overline| 上划线|
        - 通常为了美观，会消除超级链接默认的下划线修饰:`a {text-decoration:none;}`
    - text-indent 设置文本的首行缩进
        - 属性说明
            - 作用于块状元素，用来在块级元素的内容第一行添加一定的空格，以达到首行缩进的效果
            - 和`font-size`属性一样，对于首行缩进，你也可以使用`em px`或`%`
        - 使用技巧
            - 一般使用相对单位em,以元素本身字体尺寸作为参考基准。
            - 中文网页中段落的首行缩进通常是2个文字的距离，常用代码`p {text-indent:2em;}`
            - 可以使用负值，产生一些特殊效果，如“悬挂缩进”
    - text-transform 设置文本的转换（针对英文）
        - 属性说明
            
            用于转换文本中的大小写方式（忽略源文档中的大小写），对中文无影响
        - 值：
            |值|说明|
            |:-:|:-:|
            |uppercase| 全部大写|
            |lowercase| 全部小写|
            |capitalize| 单词首字母大写|
    - text-shadow 设置文本的阴影效果
        - 属性说明
            - `text-shadow`用来设置文本的阴影效果，是CSS3新增属性
            - 实现一种阴影效果需要设定一组值而非一个值，并按照顺序书写
            - 可以通过添加多组值来设定多重阴影，达到特殊效果，多组值用','分割
            - 部分老浏览器不支持改属性（IE9及以下），但这影响并不大
        - 值的写法：
            
            按顺序书写4个值：水平阴影距离 > 垂直阴影距离>模糊程度 > 阴影颜色
        - 值：
            |值|必须|说明|
            |:-:|:-:|:-:|
            |水平位置|必须值|长度单位，允许负值，控制阴影水平方向|
            |垂直位置|必须值|长度单位，允许负值，控制阴影垂直方向|
            |模糊程度|可选值|不允许负值，不写时默认为0，物模糊效果，值越大阴影越模糊|
            |阴影颜色|可选值|阴影颜色，默认和文本颜色相同|
    - `line-height` 设置文本行高
        - 常用技巧
            - 通常使用相对单位来设置行高，此时行高是以文本的字号作为参考基准
            - 默认情况下浏览器将行高呈现为字体尺寸的1到1.2倍左右，行间紧凑，视觉感易疲劳，所以通常将行高设置为字号的150%~180%之间，比较舒适
        - 典型应用
            
            单行文本在容器中垂直居中，通过让行高等同于容器高度来实现。
    - `overflow` 设置文本（容器内部内容）溢出的控制方式
        - 属性说明
            - 针对容器内部的内容，不仅仅是文本内容
            - 此属性用于块状元素
            - 内容溢出可能是横向或纵向。因此延展开来，可以细分为X轴Y轴。
        - 属性
            |值|说明|
            |:-:|:-:|
            |overflow |包括横向和纵向的内容溢出控制|
            |overflow-x |仅处理横向的内容溢出|
            |overflow-y |仅处理纵向的内容溢出|
        - 常用值：
            |值|说明|
            |:-:|:-:|
            |visible |内容可见，溢出到容器外（默认值）|
            |hidden |溢出内容被隐藏，无法查看|
            |scroll |无论内容是否溢出，容器都被添加滚动条（溢出才激活）|
            |auto |当内容溢出时，容器边缘（纵向）出现滚动条|
        - 应用技巧：
            - `overflow:hidden;`
                - 使固定了高和宽的容器墙纸隐藏内部超出容器的内容。
                - 应用场景：放置页面布局被撑开、配合实现文字截断等。
            - `overflow:auto;`
                
                在某个页面或栏目板块的固定区域中调用必须呈现的内容。
    - `letter-spacing` 设置字符间距
        - 属性说明：
            - 设置单个字符间的间距。中文：单个文字，英文：单个字幕。
            - 指定的间距将被添加到字符之后。
            - 通常以字号为参考，使用相对单位来控制间距。
            - 可以使用负值。
        - 怎么使大幅度的`letter-spacing`的文字水平居中？
            
            text-align:center;padding-left: letter-spacing宽度px;
    - `word-spacing` 设置词语间距
        - 属性说明：
            - 设置单词或词语之间的间距。判断单词或词语的依据是文本间的空格。
            - 指定的间距将被添加到单词或词语之后，但最后一个词语除外。
            - 通常以字号为参考，使用相对单位来控制间距。
            - 可以使用负值。
    - `word-break` 设置文本自动换行方式
        - 值：
            |值|说明|
            |:-:|:-:|
            |break-all| 允许文本在达到容器边缘时，可以任意位置断开，不受词语限制。|
            |keep-all |不允许词语断开，只能出现在词语分隔的空格或者连字符时才能换行。|
        - 常见应用：`word-break: break-all;`
            
            针对梳子或英文字母排版，防止出现连续无意义的长字符打破布局。
- WEB图片的格式及应用
    |格式|有损压缩|支持透明度|支持动画|使用场景|
    |:-:|:-:|:-:|:-:|:-:|
    |JPG| 有损压缩|    不支持透明度|  不支持动画|   适用于 图片、文章配图、广告图|
    |PNG| 无损压缩|    支持透明度|    不支持动画|   透明图、图片、简单背景|
    |GIF| 无损压缩|    支持透明度|    支持动画|     图标、小动图、表情包|
    - 应用途径：
        - 内容图片（作为网页的内容数据，HTML进行结构化）
            
            写在HTML网页结构中，以<img>标签的形式关联图片文件。
        - 背景图片（作为网页的修饰效果，CSS进行表现）
            
            写在CSS样式表中，如使用background属性来定义背景图。
        - 判断使用内容图or背景图
            - 内容图片一般具有内容意义，属于文档内容，应该使用HTML<img>元素
                
                应用场景：公司logo、用户照片、新闻配图、广告宣传、产品图片及缩略图。
            - 背景图片不具备内容含义，作为修饰html元素的存在，即使不可用，也不会影响网页的可用性。
                
                应用场景：背景修饰图案、内容的图标点缀。
            > 例如：
                要做一个漂亮相框的相册。那么装饰相框的图片就是背景图，写在css里面，相册里的内容照片就是内容图片，写在html里面。
- HTML内容图片的应用
    - 图像标签`<img>`
        - 单标签
        - 行间元素，但默认表现为inline-block效果，可以直接适用盒模型属性。
        - `<img>`标签不是直接在网页中插入图像，而是指定一个链接图像文件的地址，因此，`<img>`标签创建的是被引用图像的占位空间。
    - `<img>`属性
        |属性值|说明|
        |:-:|:-:|
        |src| 必须属性，指定图像链接路径|
        |alt| 必须属性，规定图像的替代文本（图片无法正确显示的时候起到文本替换的作用）|
        |title| 鼠标滑过时显示的文字提示（引导用户操作或增强用户体验）|
        |width/height| 宽高设置（建议用css设置）|
        - width/height应用：
            - 不需要带单位，（默认单位都是px）
            - 如果指定了宽高（通常都是图片本身尺寸）页面加载时会保留尺寸。
            - 如果没有指定，图片加载失败时或出现问题时，img标签的占位空间无法确定，可能会破坏HTML的页面布局。
            - 遵循内容和样式分离，CSS中设定的宽高会优先于img标签的宽高。
- CSS背景设置
    - background基本属性
        - background-color 背景色
            - 大多html元素默认的背景色是透明的{background-color:transparent;}
            - 同时设定背景色和背景图时，背景图会呈现在背景色之上。
        - background-image 背景图
            - 默认背景图从html元素左上角开始显示，并在水平和垂直方向重复
        - background-repeat 背景图的重复方式
            - 设置是否重复背景图及如何重复
                |值|说明|
                |:-:|:-:|
                |repeat |默认值，水平和垂直方向都重复。|
                |repeat-x |背景图像在水平方向重复|
                |repeat-y |背景图像在垂直方向重复|
                |no-repeat |不允许重复，背景图像仅显示一次|
        - `background-attachment` 背景图的附着位置方式
            - 设置背景图的固定方式（针对不同的参照物）
            - 与`background-positioin`易冲突，因此应用中不多见，通常用默认值。
            - `scroll` 默认，背景图会随着页面其余部分的滚动而滚动，相对于HTML元素（容器本身）
            - `fixed` 背景图位置固定，不会随着页面其余对向滚动而滚动，相对浏览器窗口
            - `local` 背景图会随着页面其余部分滚动而滚动，相对于内容（容器里面的内容）
        - `background-positioin` 背景图的位置定位
            - 设置背景图的其实（原点）位置，默认是html元素的左上角。
            - 其值应该有2个，以此为：1、横向坐标值。2、纵向坐标值。
            - 如果只设置了1个，那么该值为横向坐标，第二个默认为50%（`center`）
            - 值写法支持 像素、百分比、范围值(`left/right/bottom`)
            - 允许存在负值
            - 如果`background-attachment`值为`fixed`，那么`background-position`会无法正常工作。
        - `background` 复合属性，一句样式声明所有背景设置。
            - 值顺序为：
                `background-color background-image background-repeat background-attachment background-position`
                
                以上属性无需全部使用，可按照需要使用，没有设定的属性为默认。
                
                建议使用符合属性进行背景定义，代码高效，兼容性好。
            > PS: CSS3版本中，对背景相关属性有更高级的设置。
- 超级链接
    - 链接的常见形式：
        - 锚点（anchor），用来在网页内部跳转
            - 主要用来跳转到页面中特定位置
            - 通过设置属性值#+id名，可以定位到具有特定ID属性的HTML元素所在位置
            > 例如：
                
                `<a href="#footer">`可以链接到当前页面中的`<div id="footer">`元素
        - 相对路径URL，用来在网站内部跳转
        - 绝对路径URL，用来在不同网站页面之间进行跳转
        - 空链接
            - 空链接是用#号来替代未指定的URL
            - 通常在页面制作和调试的阶段，常常会使用到空链接。
                `<a href="#">`
        - 邮箱链接
            
            `<a href="mailto:demo@163.com">demo</a>`
            
            如果电脑上未安装邮件客户端程序，则链接无法正常工作
        - `target`属性
            - 规定在何处打开链接文档
                |值|说明|
                |:-:|:-:|
                |_self |默认值，当前窗口打开链接|
                |_blank |在新窗口（标签页）打开链接|
            - 如果要页面中所有的链接都在新窗口打开，可以直接在页面的<head>区加上一句代码：
            
                `<base target='_blank'>`
- CSS 伪类
    - 超级链接的交互状态
        - 未被点击（默认）
        - 已被点击
        - 鼠标悬停
        - 激活状态（鼠标点击时）
        - 使用CSS的伪类选择符可以设定超级链接的各种交互状态效果
    - 伪类：
        - 当html元素具有不同的状态或特征时，伪类可以设定元素的不同状态或特征下的样式效果。
        - 伪类写法
            - 在常用选择符后加一个':',然后加上伪类名称
            
                `a {color: blue;}`

                `a:hover {color: red;} `鼠标悬停状态时超级链接变为红色
        - 常用的伪类
            |常用伪类|作用对象|说明|
            |:-:|:-:|:-:|
            |:link| 主要作用对象`<a>` |未被访问的链接状态|
            |:visited| 主要作用对象`<a>` |已被访问的链接状态|
            |:hover| 所有html元素 |鼠标悬停时状态|
            |:active| 作用对象`<a>` |被激活时状态（鼠标点击与释放之间）|
            |:focus| 作用对象表单控件 |获得焦点时的状态|
    - 超级链接的伪类应用：
        - 直接设定<a>标签，等同于同时设定了<a>的4中伪类状态
        - 如要分开描述<a>的4种状态，需按顺序来编写，否则容易失效。
            
            :link > :visited > :hover > :active
        - 实际应用中，通常都是直接设定<a>标签对象，再单独设置:hover一种状态即可

### 列表
- 什么是列表？
    - 列表式一种具有一定规律顺序，排列而成的数据项的集合。
- 列表常见应用
    - 列表呈现的信息整齐直观，适用于有规律可循的区域或栏目板块。
        - 资讯列表
        - 图片展示（产品/商品）
        - 导航
- 列表的结构
    - 外围的列表区 + 内部的列表项
- 列表的类型
    - 无序列表 `<ul> + <li>`
    - 有序列表 `<ol> + <li>`
        - 特殊属性
            
            可以设定排序顺序和起始序号

            - start 数值，规定起始值
            - reversed reversed，降序（反序） `<ol reversed></ol>`

            reversed是HTML5新属性，部分浏览器不支持
    - 自定列表 `<dl> + <dt> + <dd>`
- 列表标签
    - `<ul>` 无序列表
    - `<ol>` 有序列表
    - `<li>` 无序和有序的列表项
    - `<dl>` 自定义列表
    - `<dt>` 自定义列表标题(级别重一些的列表项)
    - `<dd>` 自定义列表描述(级别轻一些的列表项)
- 列表的特点
    - 列表是具有固定嵌套关系的标签组合，如`<ul>+<li>` 列表区内不能出现其他标签，但是列表项内可以有其他标签，ul下只能有li，但li下可以有其他标签
    - 所有的标签都是双标签，块状元素，是装载内容元素的“盒子”
    - 列表可以多重嵌套，来实现复杂的栏目排版

### 列表的CSS样式
- 列表样式的专有属性： list-style
    
    list-style是针对列表的项目符号进行样式设置的的专有属性

    |属性| 说明 |
    |:--:|:--:|
    |list-style|设置所有列表属性|
    |list-style-type|列表符号的类型|
    |list-style-image|列表符号的图像|
    |list-style-position|列表符号的放置位置|

    - list-style-type

        常见值： <a href='http://www.w3school.com.cn/cssref/pr_list-style-type.asp'>CSS2枚举值</a>

        - disc: 实心小圆点(无序列表默认值)
        - decimal: 数字（有序列表默认值）
        - none: 无（去除默认的项目符号）
        
        > PS: 通过该属性可实现有序无序李彪的视觉转换

    - list-style-image
        - 设定列表的项目符号的自定义图像
        - 作用：当前项目符号类型不能满足设计需求时，可以通过该属性自定义列表项目符号
        - 值 url(图片路径)
        - 弊端：无法精确定位图片的位置
        
        > PS: 该属性的应用并不多见

    - list-style-position
        - 设定列表项目符号的位置
        - 项目符号属于每一个列表项，所以此属性只能定义项目符号的位置是放置在项目里面还是外面，无法精确控制定位距离
        
        |值|说明|
        |:--:|:--:|
        |inside|项目符号位于列表项目内|
        |outside|项目符号位于列表项外部（默认值）|
    
    - list-style
        - 值声明顺序
        
            `list-style-type > list-style-position > list-style-image`
        - 声明的时候可以忽略其中某个值得设定
        - 如果同时定义了类型和图像，则图像优先
- 实际应用原则
    - 使用盒子模型属性来精确控制列表
    - 使用列表项的背景属性来模拟项目符号
    > PS: 由于list-style主要设置项目符号且无法精确控制，所以实际应用中并不提倡使用list-style去控制列表项的样式
- 实际应用技巧
    1. 消除默认的列表区域中的边距 `ul,ol {padding: 0;} dl {margin:0;}`

        `<ul> <ol>`默认存在`padding`，`<dl>`默认存在`margin`
    2. 消除默认的项目符号 `ul,ol {list-style:none;}`

        项目符号设置基于列表区域和列表项，`<ul> <ol>`默认存在项目符号，`<dl>`没有。
    3. 使用背景属性模拟列表项符号效果

        项目符号属于列表项，背景属性需要附加给`<li> <dt> <dd>`
    