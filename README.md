# SVG 可缩放矢量图形
#### 属性

1. ##### Stroke 

   - stroke 定义一条线，文本或元素轮廓颜色

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
       <g fill="none">
         <path stroke="red" d="M5 20 l215 0" />
         <path stroke="blue" d="M5 40 l215 0" />
         <path stroke="black" d="M5 60 l215 0" />
       </g>
     </svg>
     ```

     

   - stroke-width 定义了一条线，文本或元素轮廓厚度 即粗细

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
       <g fill="none" stroke="black">
         <path stroke-width="2" d="M5 20 l215 0" />
         <path stroke-width="4" d="M5 40 l215 0" />
         <path stroke-width="6" d="M5 60 l215 0" />
       </g>
     </svg>
     ```

     

   - stroke-linecap 定义不同类型的开放路径的终结 即线两端的样式 

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
       <g fill="none" stroke="black" stroke-width="6">
         <!-- butt 直角边缘 无内边距 -->
         <path stroke-linecap="butt" d="M5 20 l215 0" /> 
         <!-- round 圆角边缘 有内边距 -->
         <path stroke-linecap="round" d="M5 40 l215 0" />
         <!-- square 直角边缘 有内边距 -->
         <path stroke-linecap="square" d="M5 60 l215 0" />
       </g>
     </svg>
     ```

   - stroke-dasharray 创建虚线

     一个参数时 表示每段虚线长度之间的间距

      多个参数时：一个表示长度一个表示间距 10, 10,  5, 5

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
       <g fill="none" stroke="black" stroke-width="4">
         <path stroke-dasharray="5,5" d="M5 20 l215 0" />
         <path stroke-dasharray="10,10" d="M5 40 l215 0" />
         <path stroke-dasharray="20,10,5,5,5,10" d="M5 60 l215 0" />
       </g>
     </svg>
     ```

     

   - stroke-dashoffset 偏移 (示例可见loading.html)

     这个属性是相对于起始点的偏移，正数偏移x值的时候，相当于往左移动了x个长度单位，负数偏移x的时候，相当于往右移动了x个长度单位。

      需要注意的是，不管偏移的方向是哪边，要记得dasharray 是循环的，也就是 虚线-间隔-虚线-间隔。

      这个属性要搭配stroke-dashoffset才能看得出来效果，非虚线的话，是无法看出偏移的。

   - stroke-linejoin 描边转角的表现方式

     1. miter 尖叫
     2. round 圆角
     3. bevel 斜角

     ```html
     <svg xmlns="http://www.w3.org/2000/svg">
             <g fill="none" stroke="black" stroke-width="10">
                 <path stroke-linejoin="miter" d="M5 20 L50 20 L50 50"/>
                 <path stroke-linejoin="round" d="M5 60 L50 60 L50 100"/>
                 <path stroke-linejoin="bevel" d="M5 120 L50 120 L50 150"/>
             </g>
         </svg>
     ```

     

   - stroke-opacity 描边透明度

     ```html
     <svg xmlns="http://www.w3.org/2000/svg">
             <g fill="none" stroke="black" stroke-width="10">
                 <path stroke-dasharray="5,5" d="M5 20 l215 0" stroke-opacity="0.5"/>
             </g>
         </svg>
     ```

2. ##### 滤镜 用来增加对SVG图形的特殊效果

   eg: 每个svg元素可以使用多个滤镜

   - feBlend - 与图像相结合的滤镜

   - feColorMatrix - 用于彩色滤光片转换 用来转换偏移的图像使之更接近黑色的颜色。 每一像素的颜色值(一个表示为[红,绿,蓝,透明度] 的矢量) 都经过矩阵乘法 (matrix multiplated) 计算出的新颜色。 '0.2'矩阵的三个值都获取乘以红色，绿色和蓝色通道。降低其值带来的颜色至黑色（黑色为0）

   - feComponentTransfer

   - feComposite

   - feConvolveMatrix

   - feDiffuseLighting

   - feDisplacementMap

   - feFlood

   - feGaussianBlur 定义模糊效果 对输入图像进行高斯模糊 stdDeviation属性定义了模糊量

     in属性 

     - SourceGraphic 该关键词表示图形元素自身将作为<filter>原语的原始输入.

     - SourceAlpha SourceAlpha与SourceGraphic具有相同的规则除了SourceAlpha只使用元素的透明度.在Alpha通道使用残影，而不是整个RGBA像素

     - BackgroundImage 使用图片

     - BackgroundAlpha 使用图片透明度. 

   - feImage

   - feMerge

   - feMorphology

   - feOffset - 过滤阴影 定义阴影效果 该输入图像作为一个整体，在属性dx和属性dy的值指定了它的偏移量。

   - feSpecularLighting

   - feTile

   - feTurbulence

   - feDistantLight - 用于照明过滤

   - fePointLight - 用于照明过滤

   - feSpotLight - 用于照明过滤

3. ##### 渐变

   - linearGradient 线性渐变 线性渐变可以定义为水平，垂直或角渐变

     - 当y1和y2相等，而x1和x2不同时，可创建水平渐变

     - 当x1和x2相等，而y1和y2不同时，可创建垂直渐变

     - 当x1和x2不同，且y1和y2不同时，可创建角形渐变

     - 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个<stop>标签来规定。offset属性用来定义渐变的开始和结束位置。

       ```html
       <svg xmlns="http://www.w3.org/2000/svg">
               <!-- 定义滤镜 -->
               <defs>
                   <linearGradient id="grad1" x1="0%" x2="100%" y1="0%" y2="100%">
                     <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
                     <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
                   </linearGradient>
               </defs>
               <ellipse cx="200" cy="70" rx="85" ry="55" fill="url(#grad1)"></ellipse>
               <text fill="#ffffff" font-size="45" font-family="Verdana" x="150" y="80">SVG</text>
           </svg>
       ```

       

   - radialGradient 放射性渐变，径向渐变

     - cx 定义一个中心点的 x 轴坐标

     - cy 定义一个中心点的 y 轴坐标

     - r 用来定义圆的半径

     - fx 定义径向渐变的焦点的 x 轴坐标。如果该属性没有被定义，就假定它与中心点是同一位置。

     - fy 定义径向渐变的焦点的 y 轴坐标。如果该属性没有被定义，就假定它与中心点是同一位置。

     - fr 定义径向渐变的焦点的半径。若该属性没有被定义，默认值为 0%。

       ```html
       <svg xmlns="http://www.w3.org/2000/svg">
               <!-- 定义滤镜 -->
               <defs>
                   <radialGradient id="grad2" cx="50%" cy="50%" r="30%" fx="50%" fy="50%" fr="50%">
                     <stop offset="0%" style="stop-color:rgb(255,255,0);stop-opacity:1" />
                     <stop offset="100%" style="stop-color:rgb(255,0,0);stop-opacity:1" />
                   </radialGradient>
               </defs>
               <ellipse cx="200" cy="70" rx="85" ry="55" fill="url(#grad2)"></ellipse>
               <text fill="#ffffff" font-size="45" font-family="Verdana" x="150" y="80">SVG</text>
           </svg>
       ```

       

#### 形状元素

1. ##### 矩形 <rect>

   - x 属性定义矩形的左侧位置（例如，x="0" 定义矩形到浏览器窗口左侧的距离是 0px）

   - y 属性定义矩形的顶端位置（例如，y="0" 定义矩形到浏览器窗口顶端的距离是 0px）

   - rx 和 ry 属性可使矩形产生圆角。

   - rect 元素的 width 和 height 属性可定义矩形的高度和宽度

   - fill 可定义填充色

     ```HTML
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
             <rect x="100" y="100" rx="10" ry="10" width="300" height="300" style="fill: aqua;stroke-width: 10;stroke: beige" />
         </svg>
     ```

     

2. ##### 圆形 <circle>

   - cx和cy属性定义圆点的x和y坐标。如果省略cx和cy，圆的中心会被设置为(0, 0)

   - r属性定义圆的半径

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
             <circle cx="100" cy="100" r="50" style="stroke: yellow;stroke-width: 2;fill: red"/>
     </svg>
     ```

     

3. ##### 椭圆 <ellipse>

   - 椭圆与圆很相似。不同之处在于椭圆有不同的x和y半径，而圆的x和y半径是相同的：

   - CX属性定义的椭圆中心的x坐标

   - CY属性定义的椭圆中心的y坐标

   - RX属性定义的水平半径

   - RY属性定义的垂直半径

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
             <ellipse cx="300" cy="300" rx="220" ry="30" style="fill: red" />
         </svg>
     ```

     

4. ##### 线 <line>

   - x1 属性在 x 轴定义线条的开始

   - y1 属性在 y 轴定义线条的开始

   - x2 属性在 x 轴定义线条的结束

   - y2 属性在 y 轴定义线条的结束

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
             <line x1="0" y1="0" x2="200" y2="300" style="stroke: aqua;stroke-width: 2" />
         </svg>
     ```

     

5. ##### 折线 <polyline>

   - points 属性定义多边形每个角的 x 和 y 坐标  每个点坐标为x,y 每个点用空格间隔 例如：x1,y1 x2,y2

6. ##### 多边形 <polygon>

   - points 属性定义多边形每个角的 x 和 y 坐标  每个点坐标为x,y 每个点用空格间隔 例如：x1,y1 x2,y2

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
             <polyline points="0,40 40,40 40,80 80,80 80,120 120,120" style="fill:white;stroke:red;stroke-width:4"/>
     
         </svg>
     ```

     

   - SVG的图形填充规则通过fill-rule属性来指定。
     - 有效值：nonzero | evenodd
       - nonzero 字面意思是“非零”。按该规则，要判断一个点是否在图形内，从该点作任意方向的一条射线，然后检测射线与图形路径的交点情况。从0开始计数，路径从左向右穿过射线则计数加1，从右向左穿过射线则计数减1。得出计数结果后，如果结果是0，则认为点在图形外部，否则认为在内部。
       - evenodd 字面意思是“奇偶”。按该规则，要判断一个点是否在图形内，从该点作任意方向的一条射线，然后检测射线与图形路径的交点的数量。如果结果是奇数则认为点在内部，是偶数则认为点在外部。
     - 注：作的是射线，不是直线

   ```html
   <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
   <!--        五角星-->
           <polygon points="100,10 40,198 190,78 10,78 160,198"
                    style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
   
       </svg>
   ```

   

7. ##### 路径 <path>

   > 注：由于在绘制路径时的复杂性，强烈建议使用SVG编辑器来创建复杂的图形。https://c.runoob.com/more/svgeditor/

   下面的命令可用于路径数据：

   - M = moveto

   - L = lineto

   - H = horizontal lineto

   - V = vertical lineto

   - C = curveto

   - S = smooth curveto

   - Q = quadratic Bézier curve

   - T = smooth quadratic Bézier curveto

   - A = elliptical Arc

   - Z = closepath

     ```html
     <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
     <!--        画三角形-->
             <path d="M0 300 L100 0 L200 300 Z" style="fill: none;stroke-width: 2;stroke: red"/>
     <!--        中间加一横线-->
     <!--        <path d="M50 150 L150 150 Z" style="fill: none;stroke-width: 2;stroke: yellowgreen"/>-->
     <!--        曲线-->
             <path d="M0 300 Q100 0 200 300 " style="fill: none;stroke-width: 2;stroke: greenyellow"/>
         </svg>
     ```

     

8. ##### 文本<text>

   ```html
   <svg xmlns="http://www.w3.org/2000/svg" style="width: 100%;height: 100vh">
           <text x="0" y="15" fill="red">45564654654654</text>
   <!--        旋转 rotate(旋转度数，旋转点坐标)-->
           <text x="0" y="30" fill="red" transform="rotate(30 0,30)">45564654654654</text>
   <!--        路径上的文字 路径加id 文字使用xlink:href="#path1"-->
           <path id="path1" d="M75,20 a1,1 0 0,0 100,0" fill="none"/>
           <text x="0" y="70" fill="red">
               <textPath xlink:href="#path1">12222222222222222222</textPath>
           </text>
   <!--     链接外部地址   -->
           <a xlink:href="http://www.baidu.com">
               <text x="0" y="100" fill="red" >45564654654654</text>
           </a>
   
       </svg>
   ```

#### 参考手册

| 元素                | 说明                                                         | 属性                                                         |
| :------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| <a>                 | 创建一个SVG元素周围链接                                      | xlink:show xlink:actuate xlink:href target                   |
| <altGlyph>          | 允许对象性文字进行控制，来呈现特殊的字符数据                 | x y dx dy rotate glyphRef format xlink:href                  |
| <altGlyphDef>       | 定义一系列象性符号的替换                                     | id                                                           |
| <altGlyphItem>      | 定义一系列候选的象性符号的替换                               | id                                                           |
| <animate>           | 随时间动态改变属性                                           | attributeName="目标属性名称" from="起始值" to="结束值" dur="持续时间" repeatCount="动画时间将发生" |
| <animateColor>      | 定义随着时间的推移颜色转换                                   | by="相对偏移值" from="起始值" to="结束值"                    |
| <animateMotion>     | 使元素沿着动作路径移动                                       | calcMode="动画的插补模式。可以是'discrete', 'linear', 'paced', 'spline'" path="运动路径" keyPoints="沿运动路径的对象目前时间应移动多远" rotate="应用旋转变换" xlink:href="一个URI引用<path>元素，它定义运动路径" |
| <animateTransform>  | 动画上一个目标元素变换属性，从而使动画控制平移，缩放，旋转或倾斜 | by="相对偏移值" from="起始值" to="结束值" type="类型的转换其值是随时间变化。可以是 'translate', 'scale', 'rotate', 'skewX', 'skewY'" |
| <circle>            | 定义一个圆                                                   | cx="圆的x轴坐标" cy="圆的y轴坐标" r="圆的半径". 必需.  + 显现属性：颜色，FillStroke，图形 |
| <clipPath>          | 用于隐藏位于剪切路径以外的对象部分。定义绘制什么和什么不绘制的模具被称为剪切路径 | clip-path="引用剪贴路径和引用剪贴路径交叉" clipPathUnits="userSpaceOnUse'或'objectBoundingBox"。第二个值childern一个对象的边框，会使用掩码的一小部分单位（默认："userSpaceOnUse"）" |
| <color-profile>     | 指定颜色配置文件的说明（使用CSS样式文件时）                  | local="本地存储颜色配置文件唯一ID" name="" rendering-intent="auto\|perceptual\|relative-colorimetric\|saturation\|absolute-colorimetric" xlink:href="ICC配置文件资源URI" |
| <cursor>            | 定义一个独立于平台的自定义光标                               | x="x轴左上角光标（默认为0）" y="y轴的左上角光标（默认为0）" xlink:href="使用光标图像URI |
| <defs>              | 引用的元素容器                                               |                                                              |
| <desc>              | 对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示 |                                                              |
| <ellipse>           | 定义一个椭圆                                                 | cx="椭圆x轴坐标" cy="椭圆y轴坐标" rx="沿x轴椭圆形的半径"。必需。 ry="沿y轴长椭圆形的半径"。必需。  + 显现属性：颜色，FillStroke，图形 |
| <feBlend>           | 使用不同的混合模式把两个对象合成在一起                       | mode="图像混合模式：normal\|multiply\|screen\|darken\|lighten" in="标识为给定的滤镜原始输入：SourceGraphic \| SourceAlpha \| BackgroundImage \| BackgroundAlpha \| FillPaint \| StrokePaint \| <filter-primitive-reference>" in2="第二输入图像的混合操作" |
| feColorMatrix       | SVG滤镜。适用矩阵转换                                        |                                                              |
| feComponentTransfer | SVG 滤镜。执行数据的 component-wise 重映射                   |                                                              |
| feComposite         | SVG 滤镜                                                     |                                                              |
| feConvolveMatrix    | SVG 滤镜                                                     |                                                              |
| feDiffuseLighting   | SVG 滤镜                                                     |                                                              |
| feDisplacementMap   | SVG 滤镜                                                     |                                                              |
| feDistantLight      | SVG滤镜。定义一个光源                                        |                                                              |
| feFlood             | SVG滤镜                                                      |                                                              |
| feFuncA             | SVG 滤镜。feComponentTransfer 的子元素                       |                                                              |
| feFuncB             | SVG 滤镜。feComponentTransfer 的子元素                       |                                                              |
| feFuncG             | SVG 滤镜。feComponentTransfer 的子元素                       |                                                              |
| feFuncR             | SVG 滤镜。feComponentTransfer 的子元素                       |                                                              |
| feGaussianBlur      | SVG滤镜。执行高斯模糊图像                                    |                                                              |
| feImage             | SVG滤镜。                                                    |                                                              |
| feMerge             | SVG滤镜。建立在彼此顶部图像层                                |                                                              |
| feMergeNode         | SVG 滤镜。feMerge的子元素                                    |                                                              |
| feMorphology        | SVG 滤镜。 对源图形执行"fattening" 或者 "thinning"           |                                                              |
| feOffset            | SVG滤镜。相对其当前位置移动图像                              |                                                              |
| fePointLight        | SVG滤镜                                                      |                                                              |
| feSpecularLighting  | SVG滤镜                                                      |                                                              |
| feSpotLight         | SVG滤镜                                                      |                                                              |
| feTile              | SVG滤镜                                                      |                                                              |
| feTurbulence        | SVG滤镜                                                      |                                                              |
| filter              | 滤镜效果的容器                                               |                                                              |
| font                | 定义字体                                                     |                                                              |
| font-face           | 描述一种字体的特点                                           |                                                              |
| font-face-format    |                                                              |                                                              |
| font-face-name      |                                                              |                                                              |
| font-face-src       |                                                              |                                                              |
| font-face-uri       |                                                              |                                                              |
| foreignObject       |                                                              |                                                              |
| <g>                 | 用于把相关元素进行组合的容器元素                             | id="该组的名称" fill="该组填充颜色" opacity="该组不透明度"  + 显现属性: All |
| glyph               | 为给定的象形符号定义图形                                     |                                                              |
| glyphRef            | 定义要使用的可能的象形符号                                   |                                                              |
| hkern               |                                                              |                                                              |
| <image>             | 定义图像                                                     | x="图像的左上角的x轴坐标" y="图像的左上角的y轴坐标" width="图像的宽度". 必须. height="图像的高度". 必须. xlink:href="图像的路径". 必须.  + 显现属性: Color, Graphics, Images, Viewports |
| <line>              | 定义一条线                                                   | x1="直线起始点x坐标" y1="直线起始点y坐标" x2="直线终点x坐标" y2="直线终点y坐标"  + 显现属性: Color, FillStroke, Graphics, Markers |
| <linearGradient>    | 定义线性渐变。通过使用矢量线性渐变填充对象，并可以定义为水平，垂直或角渐变。 | id="id 属性可为渐变定义一个唯一的名称。引用必须" gradientUnits="'userSpaceOnUse' or 'objectBoundingBox'.使用视图框或对象，以确定相对位置矢量点。 （默认为'objectBoundingBox）" gradientTransform="适用于渐变的转变" x1="渐变向量x启动点（默认0％）" y1="渐变向量y启动点（默认0％）" x2="渐变向量x的终点。 （默认100％）" y2="渐变向量y的终点。 （默认0％）" spreadMethod="'pad' or 'reflect' or 'repeat'" xlink:href="reference to another gradient whose attribute values are used as defaults and stops included. Recursive" |
| <marker>            | 标记可以放在直线，折线，多边形和路径的顶点。这些元素可以使用marker属性的"marker-start"，"marker-mid"和"marker-end"，继承默认情况下或可设置为"none"或定义的标记的URI。您必须先定义标记，然后才可以通过其URI引用。任何一种形状，可以把标记放在里面。他们绘制元素时把它们附加到顶部 | markerUnits="strokeWidth'或'userSpaceOnUse"。如果是strokeWidth"那么使用一个单位等于一个笔划宽度。否则，标记尺度不会使用同一视图单位作为引用元素（默认为'strokeWidth'）" refx="标记顶点连接的位置（默认为0）" refy="标记顶点连接的位置（默认为0）" orient="'auto'始终显示标记的角度。 "auto"将计算某个角度使得X轴一个顶点的正切值（默认为0） markerWidth="标记的宽度（默认3）" markerHeight="标记的高度（默认3）" viewBox="各点"看到"这个SVG绘图区域。由空格或逗号分隔的4个值。(min x, min y, width, height)"  + presentation attributes: All |
| <mask>              | 度屏蔽是一种不透明度值的组合和裁剪。像裁剪，您可以使用图形，文字或路径定义掩码的部分。一个掩码的默认状态是完全透明的，也就是裁剪平面的对面的。在掩码的图形设置掩码的不透明部分 | maskUnits="'userSpaceOnUse' or 'objectBoundingBox'.设定裁剪面是否是相对完整的视窗或对象（默认：'objectBoundingBox'）" maskContentUnits="第二个掩码相对对象的图形位置使用百分比'userSpaceOnUse'或'objectBoundingBox'（默认：'userSpaceOnUse'）" x="裁剪面掩码（默认值：-10％）" y="裁剪面掩码（默认值：-10％）" width="裁剪面掩码（默认是：120％）" height="裁剪面掩码（默认是：120％）" |
| metadata            | 指定元数据                                                   |                                                              |
| missing-glyph       |                                                              |                                                              |
| mpath               |                                                              |                                                              |
| <path>              | 定义一个路径                                                 | d="定义路径指令" pathLength="如果存在，路径将进行缩放，以便计算各点相当于此值的路径长度" transform="转换列表"  + 显现属性: Color, FillStroke, Graphics, Markers |
| <pattern>           | 定义坐标，你想要的视图显示和视图的大小。然后添加到您的模式形状。该模式命中时重复视图框的边缘（可视范围） | id="用于引用这个模式的唯一ID。"必需的。 patternUnits="userSpaceOnUse'或'objectBoundingBox"。第二个值X，Y，width，height 一个会使用模式对象的边框的小部分，单位（％）。" patternContentUnits="'userSpaceOnUse'或 'objectBoundingBox'" patternTransform="允许整个表达式进行转换" x="模式的偏移量，来自左上角（默认为0）" y="模式的偏移量，来自左上角（默认为0）" width="模式平铺的宽度（默认为100％）" height="模式平铺的高度（默认为100％）" viewBox="各点"看到"这个SVG绘图区域。由空格或逗号分隔的4个值。(min x, min y, width, height)" xlink:href="另一种模式，其属性值是默认值以及任何子类可以继承。递归" |
| <polygon>           | 定义一个包含至少三边图形                                     | points="多边形的点。点的总数必须是偶数"。必需的。 fill-rule="FillStroke演示属性的部分"  + 显现属性: Color, FillStroke, Graphics, Markers |
| <polyline>          | 定义只有直线组成的任意形状                                   | points=折线上的"点"。必需的。  + 显现属性: Color, FillStroke, Graphics, Markers |
| <radialGradient>    | 定义放射性渐变。放射性渐变创建一个圆圈                       | gradientUnits="'userSpaceOnUse' or 'objectBoundingBox'. 使用视图框或对象以确定相对位置的矢量点。 （默认为'objectBoundingBox）" gradientTransform="适用于渐变的变换" cx="渐变的中心点（数字或％ - 50％是默认）" cy="渐变的中心点。 （默认50％）" r="渐变的半径。 （默认50％）" fx="渐变的焦点。 （默认0％）" fy="渐变的焦点。 （默认0％）" spreadMethod="'pad' or 'reflect' or 'repeat'" xlink:href="引用到另一个渐变，其属性值作为默认值。递归" |
| <rect>              | 定义一个矩形                                                 | x="矩形的左上角的x轴" y="矩形的左上角的y轴" rx="x轴的半径（round元素）" ry="y轴的半径（round元素）" width="矩形的宽度"。必需的。 height="矩形的高度"。必需的。  + 显现属性: Color, FillStroke, Graphics |
| script              | 脚本容器。（例如ECMAScript）                                 |                                                              |
| set                 | 设置一个属性值指定时间                                       |                                                              |
| <stop>              | 渐变停止                                                     | offset="偏移停止（0到1/0％到100％）". 参考 stop-color="这个stop的颜色" stop-opacity="这个Stop的不透明度 (0到1)" |
| style               | 可使样式表直接嵌入SVG内容内部                                |                                                              |
| <svg>               | 创建一个SVG文档片段                                          | x="左上角嵌入（默认为0）" y="左上角嵌入（默认为0）" width="SVG片段的宽度（默认为100％）" height="SVG片段的高度（默认为100％）" viewBox="点"seen"这个SVG绘图区域。由空格或逗号分隔的4个值。 (min x, min y, width, height)" preserveAspectRatio="'none'或任何'xVALYVAL'的9种组合,VAL是"min"，"mid"或"max"。（默认情况下none）" zoomAndPan="'magnify' or 'disable'.Magnify选项允许用户平移和缩放您的文件（默认Magnify ）" xml="最外层<svg>元素都需要安装SVG和它的命名空间： xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xml:space="preserve""  + 显现属性: All |
| switch              |                                                              |                                                              |
| symbol              |                                                              |                                                              |
| <text>              | 定义一个文本                                                 | x="列表的X -轴的位置。在文本中在第n个字符的位置在第n个x轴。如果后面存在额外的字符，耗尽他们最后一个字符之后放置的位置。 0是默认" y="列表的Y轴位置。（参考x）0是默认" dx="在字符的长度列表中移动相对最后绘制标志符号的绝对位置。（参考x）" dy="在字符的长度列表中移动相对最后绘制标志符号的绝对位置。（参考x）" rotate="一个旋转的列表。第n个旋转是第n个字符。附加字符没有给出最后的旋转值" textLength="SVG查看器将尝试显示文本之间的间距/或字形调整的文本目标长度。（默认：正常文本的长度）" lengthAdjust="告诉查看器，如果指定长度就尝试进行调整用以呈现文本。这两个值是'spacing'和'spacingAndGlyphs'"  + 显现属性: Color, FillStroke, Graphics, FontSpecification, TextContentElements |
| textPath            |                                                              |                                                              |
| title               | 对 SVG 中的元素的纯文本描述 - 并不作为图形的一部分来显示。用户代理会将其显示为工具提示 |                                                              |
| <tref>              | 引用任何SVG文档中的<text>元素和重用                          | 相同的<TEXT>元素                                             |
| <tspan>             | 元素等同于<text>，但可以在内部嵌套文本标记以及内部本身       | Identical to the <text> element + in addition: xlink:href="引用一个<TEXT>元素" |
| <use>               | 使用URI引用一个<G>,<svg>或其他具有一个唯一的ID属性和重复的图形元素。复制的是原始的元素，因此文件中的原始存在只是一个参考。原始影响到所有副本的任何改变。 | x="克隆元素的左上角的x轴" y="克隆元素的左上角的y轴" width="克隆元素的宽度" height="克隆元素的高度" xlink:href="URI引用克隆元素"  + 显现属性: All |
| view                |                                                              |                                                              |
| vkern               |                                                              |                                                              |
