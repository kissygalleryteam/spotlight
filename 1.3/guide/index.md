## 综述

spotlight是 KISSY 聚光灯组件（引导动画）。

* 版本：1.3
* 作者：隐若（原作者：xuebi1109@gmail.com，[旧代码](https://github.com/kissygalleryteam/kissy-gallery/tree/gh-pages/gallery/spotlight)：
* 标签：spotlight, 引导动画, guide
* demo：[http://gallery.kissyui.com/spotlight/1.3/demo/index.html](http://gallery.kissyui.com/spotlight/1.3/demo/index.html)

## 初始化组件

    S.use('gallery/spotlight/1.3/index', function (S, Spotlight) {
         var spotlight = new Spotlight();
    })

## API说明

### 配置项

    Spotlight.Config = {
        quene: [ { node: Element } ], // 需要聚焦的队列
        zIndex:9999,
        bgColor: '#000',
        opacity: .5,
        maskCls: 'spotlight-mask',
        // 默认的focus区域是目标元素的outerWidth（以及outerHeight），但是可以通过maskPadding来扩展边缘
        maskPadding: {
            top: 0,
            bottom: 0,
            left: 0,
            right: 0
        },
        anim: {
            duration: .2
        }
        , initIndex: 0//默认的焦点下标值
        , lazyInit: true//实例化组建的时候是否直接渲染所需元素 否则等待手动激活的时候才渲染
        , clickOnHide: true//点击空白处隐藏mask
        , lastOnEnd: true//到达最后一个之后 如果在执行next的话 会清除mask
        , resizeBuffer: 50//窗口resize事件的时候缓冲执行适应函数的时间
        , clickOnHideTip: ''
        , toggleOnAnim: false//上一个下一个切换的时候是否为动画形式
        , focusBorder: null//显示焦点的时候在周围添加边框的配置
        , listeners: null, 四种事件如下
            // 'nextFocus'
            // 'prevFocus'
            // 'hide'
            // 'render'
            // 'focusTo'
    };

### 方法

- `canNext()`: Boolean, 是否还有下一个焦点
- `canPrevious()`: Boolean, 是否还有上一个焦点
- `hide()`: 隐藏
- `end()`: 设置当前焦点为第一个，并隐藏
- `start()`: 开始聚焦
- `nextFocus()`: 聚焦到下一个
- `prevFocus()`: 聚焦到前一个
- `focusTo( index )`: 聚焦到指定索引
- `addFocus( target )`: 添加一个焦点对象到队列
    - target: object --> { node: element }
- `removeFocus(index)`: 从队列中移除某个焦点
- `destroy()`: 摧毁组件
- `getFocusOffset()`: 获取焦点区域的长款和位置：{ left: 100, top: 100, width: 20, height: 50 }
- `getTarget()`: 获取当前焦点对象节点
