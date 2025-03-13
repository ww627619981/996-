
# 界面(win)


#打开界面
## Win_Open(filename)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|filename   |是|string|界面文件名, 目录默认GUILayout下|

#创建界面
## Win_Create(ID, x, y, width, height, hideMain, hideLast, needVoice, escClose, isRevmsg, npcID, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
|hideMain   |否|bool|是否隐藏主界面|
|hideLast   |否|bool|是否隐藏上一个界面|
|needVoice  |否|bool|是否有音效|
|escClose   |否|bool|是否按键盘ESC关闭界面|
|isRevmsg   |否|bool|是否pc鼠标经过吞噬/触摸吞噬，默认true|
|npcID      |否|int|绑定的NPCID|
|param		|否|int|窗口创建层 0主界面层 1普通面板层 2通知层 默认1<br>[仅普通面板时 hideMain、hideLast、escClose参数生效]|
- 注意此方法创建界面只做父节点

#关闭界面
## Win_Close(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|

## Win_CloseByID(ID)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|ID         |是|string|界面ID|
- 通过界面ID关闭界面

## Win_CloseByNPCID(NPCID)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|NPCID      |是|int|NPCID|
- 通过NPCID关闭界面

## Win_SetESCClose(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|value      |是|bool|是否关闭|
- 通过键盘的Esc键关闭界面

## Win_CloseAll()
- 关闭所有界面

#获取界面控件
## GetWindow(parent, ID)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|控件ID|
- 示例代码
```
    local _parent = GUI:Win_Create("QSQ_challengeboss", 0, 0, 0, 0, false, false, true, false)
    local LV_type = GUI:ListView_Create(_parent, "LV_type", 905, 65, 40, 450, 1)
    if LV_type then
            local template = GUI:Layout_Create(LV_type, "template", 0, 0, 40, 100)
            if template then
                GUI:Button_Create(template, "btn_switch", 0,0, "res/01/010022.png")
            end
        end
    end
    方法:一 根据父窗口对象与下级子控件ID获取对象
    local LV_type = GUI:GetWindow(_parent,"LV_type")

    方法:二 根据父窗口对象与多层子控件ID获取对象
    local btn_switch = GUI:GetWindow(_parent,"LV_type/template/btn_switch")

    方法:三 根据当前“桌面”打开的窗口控件ID获取对象
    local _parent = GUI:GetWindow(nil,"QSQ_challengeboss")
    local LV_type = GUI:GetWindow(nil,"QSQ_challengeboss/LV_type")
```

#设置控件自定义参数
## Win_SetParam(widget, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|param      |是|int/string/bool|参数内容|

## Win_GetParam(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
- 获取控件自定义参数

#设置界面拖拽
## Win_SetDrag(widget, dragLayer)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|dragLayer  |是|obj|拖拽区域控件|

#设置主界面隐藏
## Win_SetMainHide(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|value      |是|bool|是否隐藏, 普通面板生效|

#设置是否按ESC键关闭窗口
## Win_SetESCClose(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|value      |是|bool|能否关闭, 普通面板生效|

#设置界面绑定NPC
## Win_BindNPC(widget, npcID)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|npcID      |是|int|NPCID|

#设置界面浮起
## Win_SetZPanel(widget, zPanel)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|zPanel     |是|obj|控件对象|

#设置界面绑定事件
## Win_BindLuaEvent(widget, eventID, eventTag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|eventID    |否|obj|事件ID|
|eventTag   |否|obj|事件描述|

#设置界面内鼠标右键吞噬
## Win_SetSwallowRightMouseTouch(widget, state)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|界面对象|
|state      |是|bool|是否吞噬|

#判断对象是否为空
## Win_IsNull(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

#判断对象是否不为空
## Win_IsNotNull(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|


# 常用方法


#加载UI文件
## LoadExport(parent, filename)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent   |是|obj|父节点对象|
|filename |是|string|文件路径|
- Ctrl+f9 界面编辑器导出的lua文件

*简单示例*
```
    local win = GUI:Win_Create("Win_1", 0, 0, 1136, 640)
    GUI:LoadExport(win, "game_world_confirm")
    -- ...
```

#获取父节点的快捷子控件组
## ui_delegate(parent)
-  返回值 : table  [key 为控件名]

*示例* 
```
    local ui = GUI:ui_delegate(parent)
    if ui.Text_attName then
        GUI:Text_setString(ui.Text_attName, "------")
    end
```

#屏蔽自动修复坐标为整数
```
GUI:DisableFixPosition()
```

#获取当前打开界面挂接点
## Attach_Parent()
- 变化的

#获取主界面左上挂接点
## Attach_LeftTop()

#获取主界面右上挂接点
## Attach_RightTop()

#获取主界面左下挂接点
## Attach_LeftBottom()

#获取主界面右下挂接点
## Attach_RightBottom()

#获取最上层UI挂接点
## Attach_UITop()

#获取上层场景挂接点
## Attach_SceneF()

#获取下层场景挂接点
## Attach_SceneB()

#获取主界面最底层左上挂接点
## Attach_LeftTop_B()

#获取主界面最底层右上挂接点
## Attach_RightTop_B()

#获取主界面最底层左下挂接点
## Attach_LeftBottom_B()

#获取主界面最底层右下挂接点
## Attach_RightBottom_B()

#获取主界面最顶层左上挂接点
## Attach_LeftTop_T()

#获取主界面最顶层右上挂接点
## Attach_RightTop_T()

#获取主界面最顶层左下挂接点
## Attach_LeftBottom_T()

#获取主界面最顶层右下挂接点
## Attach_RightBottom_T()

# 获取自带父节点 [挂接点ID: 101-111]
## Win_FindParent(ID)

#设置坐标
## setPosition(widget, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget   |是|obj|控件对象|
|x        |是|int|横坐标|
|y        |是|int|纵坐标|

## getPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取坐标
```lua
    local pos = GUI:getPosition(widget)
    SL:Print("x",pos.x)
    SL:Print("y",pos.y)
```

## setPositionX(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|横坐标|
- 设置横坐标（纵坐标不变）

## getPositionX(widget)
|参数        |必选|类型|注释|
|:----       |:-|:--|:---|
|widget      |是|obj|控件对象|
- 获取横坐标

## setPositionY(widget, value)
|参数        |必选|类型|注释|
|:----       |:-|:--|:---|
|widget      |是|obj|控件对象|
|value       |是|int|纵坐标|
- 设置纵坐标（横坐标不变）

## getPositionY(widget)
|参数        |必选|类型|注释|
|:----       |:-|:--|:---|
|widget      |是|obj|控件对象|
- 获取纵坐标

#设置控件锚点
## setAnchorPoint(widget, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|x          |是|int|横坐标|
|y          |是|int|纵坐标|
- 示例代码
```
    GUI:setAnchorPoint(parent, 0, 0)        -- 左 下
    GUI:setAnchorPoint(parent, 0, 0.5)      -- 左 中
    GUI:setAnchorPoint(parent, 0, 1)        -- 左 上
    GUI:setAnchorPoint(parent, 0.5, 0)      -- 中 下
    GUI:setAnchorPoint(parent, 0.5, 0.5)    -- 中 中
    GUI:setAnchorPoint(parent, 0.5, 1)      -- 中 上
    GUI:setAnchorPoint(parent, 1, 0)        -- 右 下 
    GUI:setAnchorPoint(parent, 1, 0.5)      -- 右 中
    GUI:setAnchorPoint(parent, 1, 1)        -- 右 上 
```

## getAnchorPoint(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget   |是|obj|控件对象|
- 获取控件锚点

#设置控件尺寸大小
## setContentSize(widget, sizeW, sizeH)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|sizeW      |是|int|宽度|
|sizeH      |是|int|长度|

## getContentSize(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件尺寸大小(纹理大小 不考虑缩放)

## getBoundingBox(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件尺寸大小(考虑缩放的真实大小)

#设置忽略设置的自定义尺寸大小
## setIgnoreContentAdaptWithSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|boolean|是否忽略用户定义尺寸大小|

#设置控件标签
## setTag(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|标签值|

## getTag(widget)
|参数        |必选|类型|注释|
|:----       |:-|:--|:---|
|widget      |是|obj|控件对象|
- 获取控件标签

#设置控件名字
## setName(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|string|名字|

#设置控件置灰
## setGrey(widget, isGrey)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|isGrey     |是|bool|是否置灰|

#设置控件旋转角度
## setRotation(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|旋转角度（0 - 360）|

## getRotation(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

#设置控件X轴倾斜角度
## setRotationSkewX(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|倾斜角度（0 - 360）|

#设置控件Y轴倾斜角度
## setRotationSkewY(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|倾斜角度（0 - 360）|

#设置控件可见性
## setVisible(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否显示|

## getVisible(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件是否显示状态

#设置控件不透明度
## setOpacity(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|不透明度(0-255), 默认255|

## getOpacity(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件不透明度

#设置控件缩放
## setScale(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|float|缩放比例, 默认1.0|

## getScale(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件缩放比例

## setScaleX(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|float|缩放比例, 默认1.0|
- 设置控件X轴方向缩放

## getScaleX(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件X轴方向缩放比例

## setScaleY(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|float|缩放比例, 默认1.0|
- 设置控件Y轴方向缩放

## getScaleY(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件Y轴方向缩放比例

#设置控件翻转
## setFlippedX(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|X轴方向是否翻转|
- 设置水平X轴方向翻转

## getFlippedX(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取是否水平翻转

## setFlippedY(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|value      |是|bool|Y轴方向是否翻转|
- 垂直Y轴方向翻转

## getFlippedY(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取是否垂直翻转

#设置控件渲染层级
## setLocalZOrder(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|渲染层级, 值越大显示越靠前|
- 设置控件在父节点的渲染层级

# 设置控件是否跟随父控件变化透明度
## setCascadeOpacityEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否跟随|

# 设置控件的所有子控件是否跟随变化透明度
## setChildrenCascadeOpacityEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否跟随|

# 获得控件世界坐标
## getWorldPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

## convertToWorldSpace(widget, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|x          |是|int|节点坐标X|
|y          |是|int|节点坐标Y|
- 对应控件的节点坐标转换为世界坐标

## convertToNodeSpace(widget, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|x          |是|int|世界坐标X|
|y          |是|int|世界坐标Y|
- 世界坐标转换为对应控件的节点坐标

#加载子控件
## addChild(widget, child)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|父控件对象|
|child      |是|obj|子控件对象)|

#~~克隆控件~~
## ~~Clone(widget)~~
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

## getTouchEnabled(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件是否可以触摸

#设置控件是否可以触摸
## setTouchEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否触摸|

## getTouchEnabled(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件是否可以触摸

## delayTouchEnabled(widget, delay)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|delay      |否|float|延迟触摸间隔|
- 设置延迟可触摸

## setMouseEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否鼠标触摸|
- 设置控件是否可以鼠标触摸

#设置控件是否触摸吞噬
## setSwallowTouches(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否触摸吞噬|

## getSwallowTouches(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件是否触摸吞噬

## setMouseRSwallowTouches(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 设置控件吞噬鼠标按键事件 [检查自身触摸吞噬时]

#获取控件节点
## getParent(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|子控件对象|
- 获取父节点

## getChildren(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|父控件对象|
- 获取控件所有子节点

## getName(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件名字

## getChildByName(widget, name)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|父控件对象|
|name       |是|string|控件名字|
- 通过控件名字获取子节点

## getChildByTag(widget, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|父控件对象|
|tag        |是|int|控件标记|
- 通过控件标记获取子节点

#删除控件
## removeAllChildren(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 移除传入控件的所有子节点

## removeFromParent(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 将传入控件从父节点上移除 

## removeChildByName(widget, name)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|name       |是|string|控件名字|
- 通过名字删除传入控件的对应子节点

#设置控件点击事件
## addOnClickEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|func      |是|function|回调函数|

#设置控件触摸事件
## addOnTouchEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|func      |是|function|回调函数|

*示例 1 *
```
    -- 添加长按事件, 长按0.5秒触发
    GUI:addOnTouchEvent(btn, function(sender, type)
        -- sender: 传入控件自身
        -- type: 触摸类型 int 0 - 3
        if type == SLDefine.TouchEventType.began then           -- 0 触摸开始
            if not sender._clicking then
                sender._clicking = true
                SL:scheduleOnce(sender, function()
                    sender._clicking = false
                    SL:Print("长按触发---")
                end, 0.5)
            end
        elseif type == SLDefine.TouchEventType.moved then       -- 1 触摸移动

        elseif type == SLDefine.TouchEventType.ended or type == SLDefine.TouchEventType.canceled then       -- 2 触摸结束 3 触摸取消
            if sender._clicking then
                GUI:stopAllActions(sender)
                sender._clicking = false
                SL:Print("单击触发---")
            end
        end
    end)
    
```

*示例 2 *
```
    -- 添加双击事件 0.3秒间隔
    local function doubleCallBack()
        SL:Print("双击触发---")
    end
    GUI:addOnTouchEvent(btn, function(sender, type)
        -- sender: 传入控件自身
        -- type: 触摸类型 int 0 - 3
        if type == SLDefine.TouchEventType.ended then       -- 2 触摸结束
            if doubleCallBack then -- 双击事件
                if not sender._lastClick then
                    sender._lastClick = true
                    sender._clickDelayHandler = SL:ScheduleOnce(function()
                        SL:Print("单击触发---")
                        sender._lastClick = nil
                    end, 0.3)
                else
                    if sender._clickDelayHandler then
                        SL:UnSchedule(sender._clickDelayHandler)
                        sender._clickDelayHandler = nil
                    end
                    -- 双击回调方法
                    if doubleCallBack then
                        doubleCallBack()
                    end
                    sender._lastClick = nil
                end 
            end
        end
    end)
```

## getTouchBeganPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件触摸开始时位置

## getTouchMovePosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件触摸移动时位置

## getTouchEndPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件触摸结束时位置

#设置控件长按触发事件
## addOnLongTouchEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|func      |是|function|回调函数|

#设置控件鼠标进入/移出事件
## addMouseMoveEvent(widget, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|param      |是|table|onEnterFunc: function 鼠标进入回调函数<br>onLeaveFunc: function 鼠标移出回调函数<br>onInsideFunc: function 鼠标一直在内部回调函数|
例 :
```
    GUI:addMouseMoveEvent(button,
    {
        onEnterFunc = function()
            SL:Print("enter!")
        end,
        onLeaveFunc = function()
            SL:Print("leave!")
        end
    }
    )
```

#设置鼠标按钮事件
## addMouseButtonEvent(widget, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|param      |是|table|onRightDownFunc: function 鼠标右键点击事件 <br> OnRightUpFunc: function 鼠标右键松开事件<br> needTouchPos: boolean 需要传入鼠标触摸位置<br>OnScrollFunc: function 鼠标滚轮滚动事件[3.40.8版本新增] |
例 :
```
    GUI:addMouseButtonEvent(btn, {onRightDownFunc = function()
        SL:Print("right!!!!") 
    end})
```

#设置鼠标经过控件显示文本
## addMouseOverTips(widget, str, pos, anr, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|str        |是|string|文本|
|pos        |是|table|位置|
|anr        |是|table|锚点|
|param      |否|table|checkCallback: function 检查接触点是否能展示[函数传入参数: pos <br>返回: true / false ]|
例 :
```
    local param = {
        checkCallback = function(touchPos)
            if touchPos and GUI:isClippingParentContainsPoint(Image_icon, touchPos) then
                return true
            end
            return false
        end
    }
    GUI:addMouseOverTips(Image_icon, "DESC_____", nil, nil, param)
```

#设置控件是否触摸吞噬
## setSwallowTouches(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|是否吞噬|
例 :
```
    local layout1 = GUI:Layout_Create(parent, "layout1", 0, 0, 100, 100, true)
    local layout2 = GUI:Layout_Create(layout1, "layout2", 0, 0, 100, 100, true)
    GUI:setSwallowTouches(layout2,true) -- 触摸layer2层 不会触发 layer1层 触摸回调函数
    GUI:setSwallowTouches(layout2,false) -- 触摸layer2层 同时触发 layer1层 触摸回调函数
```

#获取控件是否触摸吞噬
## getSwallowTouches(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 获取控件是否吞噬

#检查触摸位置是否被父节点裁剪
## isClippingParentContainsPoint(widget, position)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|position   |是|table|世界坐标|

#开启定时器
## schedule(widget, callback, delay)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|callback   |是|function|回调函数|
|delay      |是|int|时间间隔|
例 :
```
    local function showTime()
        print("倒计时ing")
    end
    GUI:schedule(node, showTime, 1)
```

## unSchedule(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
- 停止定时器

#键盘监听事件
## addKeyboardEvent(codeKeys, pressedCB, releaseCB, checkFullSort)
* 注册键盘监听(快捷键)

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|codeKeys   |是|string / table|要监听的键盘键key|
|pressedCB  |是|function|按下回调|
|releaseCB  |否|function|松开回调|
|checkFullSort|否|boolean|兼容全顺序键盘key排列, 针对监听多键 [3.40.7版本]|

* 键盘键key 如下 :
```
    "KEY_NONE",
    "KEY_PAUSE",
    "KEY_SCROLL_LOCK",
    "KEY_PRINT",
    "KEY_SYSREQ",
    "KEY_BREAK",
    "KEY_ESCAPE",
    "KEY_BACKSPACE",
    "KEY_TAB",
    "KEY_BACK_TAB",
    "KEY_RETURN",
    "KEY_CAPS_LOCK",
    "KEY_SHIFT",
    "KEY_RIGHT_SHIFT",
    "KEY_CTRL",
    "KEY_RIGHT_CTRL",
    "KEY_ALT",
    "KEY_RIGHT_ALT",
    "KEY_MENU",
    "KEY_HYPER",
    "KEY_INSERT",
    "KEY_HOME",
    "KEY_PG_UP",
    "KEY_DELETE",
    "KEY_END",
    "KEY_PG_DOWN",
    "KEY_LEFT_ARROW",
    "KEY_RIGHT_ARROW",
    "KEY_UP_ARROW",
    "KEY_DOWN_ARROW",
    "KEY_NUM_LOCK",
    "KEY_KP_PLUS",
    "KEY_KP_MINUS",
    "KEY_KP_MULTIPLY",
    "KEY_KP_DIVIDE",
    "KEY_KP_ENTER",
    "KEY_KP_HOME",
    "KEY_KP_UP",
    "KEY_KP_PG_UP",
    "KEY_KP_LEFT",
    "KEY_KP_FIVE",
    "KEY_KP_RIGHT",
    "KEY_KP_END",
    "KEY_KP_DOWN",
    "KEY_KP_PG_DOWN",
    "KEY_KP_INSERT",
    "KEY_KP_DELETE",
    "KEY_F1",
    "KEY_F2",
    "KEY_F3",
    "KEY_F4",
    "KEY_F5",
    "KEY_F6",
    "KEY_F7",
    "KEY_F8",
    "KEY_F9",
    "KEY_F10",
    "KEY_F11",
    "KEY_F12",
    "KEY_SPACE",
    "KEY_EXCLAM",
    "KEY_QUOTE",
    "KEY_NUMBER",
    "KEY_DOLLAR",
    "KEY_PERCENT",
    "KEY_CIRCUMFLEX",
    "KEY_AMPERSAND",
    "KEY_APOSTROPHE",
    "KEY_LEFT_PARENTHESIS",
    "KEY_RIGHT_PARENTHESIS",
    "KEY_ASTERISK",
    "KEY_PLUS",
    "KEY_COMMA",
    "KEY_MINUS",
    "KEY_PERIOD",
    "KEY_SLASH",
    "KEY_0",
    "KEY_1",
    "KEY_2",
    "KEY_3",
    "KEY_4",
    "KEY_5",
    "KEY_6",
    "KEY_7",
    "KEY_8",
    "KEY_9",
    "KEY_COLON",
    "KEY_SEMICOLON",
    "KEY_LESS_THAN",
    "KEY_EQUAL",
    "KEY_GREATER_THAN",
    "KEY_QUESTION",
    "KEY_AT",
    "KEY_CAPITAL_A",
    "KEY_CAPITAL_B",
    "KEY_CAPITAL_C",
    "KEY_CAPITAL_D",
    "KEY_CAPITAL_E",
    "KEY_CAPITAL_F",
    "KEY_CAPITAL_G",
    "KEY_CAPITAL_H",
    "KEY_CAPITAL_I",
    "KEY_CAPITAL_J",
    "KEY_CAPITAL_K",
    "KEY_CAPITAL_L",
    "KEY_CAPITAL_M",
    "KEY_CAPITAL_N",
    "KEY_CAPITAL_O",
    "KEY_CAPITAL_P",
    "KEY_CAPITAL_Q",
    "KEY_CAPITAL_R",
    "KEY_CAPITAL_S",
    "KEY_CAPITAL_T",
    "KEY_CAPITAL_U",
    "KEY_CAPITAL_V",
    "KEY_CAPITAL_W",
    "KEY_CAPITAL_X",
    "KEY_CAPITAL_Y",
    "KEY_CAPITAL_Z",
    "KEY_LEFT_BRACKET",
    "KEY_BACK_SLASH",
    "KEY_RIGHT_BRACKET",
    "KEY_UNDERSCORE",
    "KEY_GRAVE",
    "KEY_A",
    "KEY_B",
    "KEY_C",
    "KEY_D",
    "KEY_E",
    "KEY_F",
    "KEY_G",
    "KEY_H",
    "KEY_I",
    "KEY_J",
    "KEY_K",
    "KEY_L",
    "KEY_M",
    "KEY_N",
    "KEY_O",
    "KEY_P",
    "KEY_Q",
    "KEY_R",
    "KEY_S",
    "KEY_T",
    "KEY_U",
    "KEY_V",
    "KEY_W",
    "KEY_X",
    "KEY_Y",
    "KEY_Z",
    "KEY_LEFT_BRACE",
    "KEY_BAR",
    "KEY_RIGHT_BRACE",
    "KEY_TILDE",
    "KEY_EURO",
    "KEY_POUND",
    "KEY_YEN",
    "KEY_MIDDLE_DOT",
    "KEY_SEARCH",
    "KEY_DPAD_LEFT",
    "KEY_DPAD_RIGHT",
    "KEY_DPAD_UP",
    "KEY_DPAD_DOWN",
    "KEY_DPAD_CENTER",
    "KEY_ENTER",
    "KEY_PLAY",
```

例 :
```
    local function pressedCB()
        SL:Print("Presss!!!!!!!!!!!!!!")
    end
    local function releaseCB()
        SL:Print("release!!!!!!!!!!!!!!")
    end

    GUI:addKeyboardEvent("KEY_F7", pressedCB, releaseCB)
```

## removeKeyboardEvent(codeKeys)
* 移除键盘监听(快捷键)

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|codeKeys   |是|string / table|要移除监听的键盘键key|
例 :
```
    GUI:removeKeyboardEvent("KEY_F7")
```

## ShowWorldTips(tips, worldPos, anchorPoint)
* 显示文本Tips

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|tips       |是|string|显示文本|
|worldPos   |是|table|世界坐标|
|anchorPoint|是|table|锚点|
例 ：
```
    GUI:ShowWorldTips("测试", GUI:p(400, 400), GUI:p(0, 0))
```
## HideWorldTips()
* 关闭文本Tips

## UserUILayout(pNode, param)
* 自适应布局

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|pNode       |是|obj|控件对象|
|param   |是|table|布局参数|
-  返回值 : table {width = width, height = height}

```
布局参数说明
param = {
        dir： 1：垂直; 2: 水平; 3： 两者
        gap:  x: 左右间距; y: 上下间距; l: 左边距; t: 上边距
        addDir: 动画增长方式 1: 从上到下（从左到右）（多行从左上角）, 2：中间到两边（多行从右上角）, 3：从下到上（从右到左）
        colnum: 多行列数（dir必须是3）
        autosize: 根据内容自适应容器
        sortfunc: 排序函数
        interval：增长方式动画播放时间间隔, 不传值则不播放动画
        rownums ： 每一行的数量table ; 例如：rownums = {3, 2} （第一行3个元素，第二行2个元素）
}
```

```lua
    [[示例代码]]
    local Layout = GUI:Layout_Create(parent, "Layout", 50,50, 500.00, 200.00, false)
    GUI:Layout_setBackGroundColorType(Layout, 1)
    GUI:Layout_setBackGroundColor(Layout, "#96c8ff")
    GUI:Layout_setBackGroundColorOpacity(Layout, 140)

    local Button_1 = GUI:Button_Create(Layout, "button_1", 100.00, 0.00, "res/public/1900000660.png")
    GUI:Win_SetParam(Button_1, 1)
    GUI:Button_setTitleText(Button_1, "button_1")
    local Button_2 = GUI:Button_Create(Layout, "button_2", 200.00, 0.00, "res/public/1900000660.png")
    GUI:Win_SetParam(Button_2, 2)
    GUI:Button_setTitleText(Button_2, "button_2")
    local Button_3 = GUI:Button_Create(Layout, "button_3", 300.00, 100.00, "res/public/1900000660.png")
    GUI:Win_SetParam(Button_3, 2)
    GUI:Button_setTitleText(Button_3, "button_3")

    GUI:UserUILayout(Layout, {
        dir=2,
        addDir=2,
        interval=1,
        gap = {x=1},
        sortfunc = function (lists)
            table.sort(lists, function (a, b)
                return GUI:Win_GetParam(a) > GUI:Win_GetParam(b)
            end)
        end
    })
```
![自适应布局](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2856781569f6d0101fd92c2b00999a43 "自适应布局")


# 图片(Image)


#创建图片
## Image_Create(parent, ID, x, y, nimg)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|nimg       |是|string|图片路径|
- 示例代码
```
local imgPath = "res/public/1900000600.png"
local Image_bg = GUI:Image_Create(parent, "Image_bg", 0, 0, imgPath)
```

# 加载纹理图片
## Image_loadTexture(widget, filepath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|图片对象|
|filepath   |是|string|图片路径|

# 设置图片九宫格
## Image_setScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|图片对象|
|scale9l    |是|int|左边比例|
|scale9r    |是|int|右边比例|
|scale9t    |是|int|上边比例|
|scale9b    |是|int|下边比例|

# 设置图片是否变灰
## Image_setGrey(widget, isGrey)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|图片对象|
|isGrey     |是|bool|是否置灰|


# 按钮(Button)


# 创建按钮
## Button_Create(parent, ID, x, y, nimg)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|nimg       |是|string|图片路径|
- 示例代码
```
local BtnOk = GUI:Button_Create(FrameLayout, "BtnOk", 0, 0, "res/public/1900000611.png")
GUI:setAnchorPoint(BtnOk, { x = 0.5, y = 0.5 })
GUI:Button_setTitleText(BtnOk, "确定")
GUI:Button_setTitleFontSize(BtnOk, 16)
GUI:addOnClickEvent(BtnOk, function()
	-- do something
end)
```

# 设置按钮状态图片
## Button_loadTextures(widget, Normalfilepath, Pressedfilepath, Disabledfilepath, TextureType)
|参数        |必选|类型|注释|
|:----       |:-|:--|:---|
|widget                    |是|obj|按钮对象|
|Normalfilepath            |是|string|正常状态图片路径|
|Pressedfilepath           |否|string|按压状态图片路径|
|Disabledfilepath          |否|string|禁用状态图片路径|
|TextureType               |否|int|加载类型：<br>0 图片<br>1 图片集 plist文件|

## Button_loadTextureNormal(widget, filepath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|filepath   |是|string|图片路径|
- 设置正常状态图片

## Button_loadTexturePressed(widget, filepath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|filepath   |是|string|图片路径|
- 设置按下状态图片

## Button_loadTextureDisabled(widget, filepath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|filepath   |是|string|图片路径|
- 设置禁用状态图片

# 设置按钮文字
## Button_setTitleText(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|string|按钮显示文本|

# 获取按钮文字 [3.40.6版本]
## Button_getTitleText(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|

# 设置按钮文字颜色
## Button_setTitleColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|string|色值（#000000）|

# 设置按钮文字大小
## Button_setTitleFontSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|int|字体大小（字号16）|

# 设置按钮文字样式
## Button_setTitleFontName(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|string|字体样式（font.ttf）|

# 设置按钮文本最大宽度
## Button_setMaxLineWidth(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|int|文本最大宽度|

# 设置按钮文本加描边
## Button_titleEnableOutline(widget, color, outline)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|color      |是|string|描边色值（#000000）|
|outline    |是|int|描边大小|

## Button_titleDisableOutLine(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
- 取消按钮文本描边

# 设置按钮是否禁用
## Button_setBright(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|bool|是否禁用（可触摸）|

## Button_setBrightEx(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|bool|是否禁用（不可触摸）|

## Button_setBrightStyle(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|int|状态（0正常 1按下）|

#设置按钮是否灰态
## Button_setGrey(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|value      |是|bool|是否灰态|

#设置按钮九宫格
## Button_setScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|按钮对象|
|scale9l    |是|int|左边比例|
|scale9r    |是|int|右边比例|
|scale9t    |是|int|上边比例|
|scale9b    |是|int|下边比例|


# 文本(Text)


# 创建文本
## Text_Create(parent, ID, x, y, fontSize, fontColor, str)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|fontSize   |是|int|字体大小|
|fontColor  |是|stirng|字体颜色|
|str        |是|string|文本|
- 示例代码
```
local str = "我的名字" or ""
local Text_name = GUI:Text_Create(parent, "Text_name", 0, 0, 16, "#ffffff", str)
```

# 设置文本
## Text_setString(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|string|文本|

# 获取文本
## GUI:Text_getString(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

# 设置文本颜色
## Text_setTextColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|string|色值("#000000")|

# 设置字体大小
## Text_setFontSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|int|字体大小|

# 设置字体路径
## Text_setFontName(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|string|字体文件路径<br>例: "fonts/font.ttf"|

# 设置字体描边
## Text_enableOutline(widget, color, size)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|color      |是|string|色值("#000000")|
|size       |是|int|描边宽度|

# 设置是否启用下划线
## GUI:Text_enableUnderline(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|文本对象|

# 设置文本最大行宽
## Text_setMaxLineWidth(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|int|宽度|

# 禁用文本特效
## Text_disableEffect(widget, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|int|特效类型：<br>0：正常<br> 1：描边<br>2：阴影<br>3：发光|

## Text_disableNormal(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

## Text_disableOutLine(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

## Text_disableShadow(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

## Text_disableGlow(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|

# 设置文本垂直对齐
## Text_setTextVerticalAlignment(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|int|0：顶对齐<br> 1：垂直居中<br>2：底对齐|

# 设置文本水平对齐
## Text_setTextHorizontalAlignment(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|int|0：顶对齐<br> 1：水平居中<br>2：底对齐|

# 设置文本尺寸
## Text_setTextAreaSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|table|{width = 0, height = 0}|

# 设置倒计时文本
## Text_COUNTDOWN(widget, time, callback)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|time       |是|int|倒计时时间, 单位:秒|
|callback	|否|function|每秒触发回调, 传入参数: 剩余时间<br>**版本号[3.40.4]及以后改为倒计时结束触发**|
|showType   |否|int|倒计时时间显示方式 <br>0: xx时xx分xx秒 <br>1: 小于1天显示xx:xx:xx 大于显示xx天xx时xx分 [3.40.8版本新增]|


# Bmp文本(BmpText)


# 创建Bmp文本
## BmpText_Create(parent, ID, x, y, fontColor, str, fontPath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|fontColor  |否|stirng|字体颜色, [3.40.7版本支持传空]|
|str        |是|string|文本|
|fontPath   |是|string|字体文件路径, 例：`"fonts/stfont.fnt"`|
- PC端 12号宋体
- 示例代码
```
local str = "我的名字" or ""
local Text_name = GUI:BmpText_Create(parent, "Text_name", 0, 0, "#ffffff", str)
```

# 艺术文本(TextAtlas)


# 创建艺术字文本
## TextAtlas_Create(parent, ID, x, y, stringValue, charMapFile, itemWidth, itemHeight, startCharMap, sheet)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|stringValue   |是|string|文本内容|
|charMapFile   |是|string|艺术字路径|
|itemWidth     |是|int|单个字体宽度|
|itemHeight    |是|int|单个字体高度|
|startCharMap  |是|string|起始字符设置("/")|
|sheet		   |是|string|字体内容(H5专属)<br>比如图片文字是“+-0123456789”,那这个sheet的值就是"+-0123456789"|
- 示例代码
```
local artPath = "res/public/word_tywz_01.png"
local artNum = GUI:TextAtlas_Create(parent, "artNum", 0, 0, "123456", artPath, 18, 27, "0")
```

# 设置艺术字配置
## TextAtlas_setProperty(widget, stringValue, charMapFile, itemWidth, itemHeight, startCharMap, sheet)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|艺术字对象|
|stringValue   |是|string|文本内容|
|charMapFile   |是|string|艺术字路径|
|itemWidth     |是|int|字体宽度|
|itemHeight    |是|int|字体高度|
|startCharMap  |是|string|起始字符设置("/")|
|sheet		   |是|string|字体内容(H5专属)<br>比如图片文字是“+-0123456789”,那这个sheet的值就是"+-0123456789"|

# 设置艺术字文本
## TextAtlas_setString(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|艺术字对象|
|value      |是|string|文本内容|

# 获取艺术字文本
## TextAtlas_getString(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|艺术字对象|


# 富文本(RichText)


# 创建富文本
## RichText_Create(parent, ID, x, y, str, width, fontSize, fontColor, vspace, hyperlinkCB, defaultFontFace)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|str        |是|string|文本内容|
|width      |是|int|富文本控件宽度|
|fontSize   |否|int|字体大小|
|fontColor  |否|string|字体颜色|
|vspace     |否|int|富文本行间距|
|hyperlinkCB|否|function|超链回调函数|
- 示例代码

```
local richText = GUI:RichText_Create(parent, "richText", 0, 0, "克里斯蒂亚罗", 100, 16, "#f8e6c6", 0, function()
    -- do something
end)
```

# 创建原始富文本
## RichTextFCOLOR_Create(parent, ID, x, y, str, width, fontSize, color, vspace, hyperlinkCB, fontPath, outlineParam)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|str        |是|string|文本内容|
|width      |是|int|富文本控件宽度|
|fontSize   |否|int|字体大小|
|color      |否|string|字体颜色, 例: "#FFFFFF"|
|vspace     |否|int|富文本行间距|
|hyperlinkCB|否|function|超链回调函数|
|fontPath   |否|string|字体文件路径|
|outlineParam|否|table|描边参数 <br>outlineSize: 描边大小 <br>outlineColor: 描边颜色 C3B <br> (描边颜色 例 : `SL:ConvertColorFromHexString("#FFFFFF")`)|
- 示例代码

```
	local rich = GUI:RichTextFCOLOR_Create(node, "rich", 100, 0, "<灼伤：%s几率灼烧目标/FCOLOR=254>\\<每秒燃烧目标5%生命值/FCOLOR=249>", 600, 16, "#28EF01", 5)
```

# 创建自定义组合富文本 [3.40.3版本]
## RichTextCombine_Create(parent, ID, x, y, width, vspace)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|富文本控件最大宽度|
|vspace     |否|int|富文本行间距|

## 添加自定义富文本cell
## RichTextCombine_pushBackElements(widget, elements)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|elements   |是|obj|[RichTextCombineCell] 单个元素控件对象 或 控件对象table |

## 添加cell完毕格式化富文本
## RichTextCombine_format(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

# 创建自定义组合富文本cell [3.40.3版本]
## RichTextCombineCell_Create(parent, ID, x, y, type, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象 [RichTextCombine]|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|type       |是|int/string|cell类型 <br> 文本类型：1或TEXT<br>节点类型：2或NODE<br>换行类型：3 或 NEWLINE[3.40.4新增]|
|param      |是|table|额外参数, 参考如下:|
```
	{
		node 			= 节点类型必需参数 object 控件对象,
		color			= 颜色值 默认: "#FFFFFF",
		opacity  		= 不透明度 默认: 255,
		str  			= 文本内容 string,
		fontSize 		= 文本字号 默认: SL:GetMetaValue("GAME_DATA", "DEFAULT_FONT_SIZE"),
		fontPath 		= 文本字体路径 默认: "fonts/font2.ttf"
		outlineColor 	= 文本描边颜色 默认: "#000000",
		outlineSize  	= 文本描边大小 默认: 0,
		link 			= 文本点击触发传递内容 string
	}
```

- 示例代码 :

```
		local richText  = GUI:RichTextCombine_Create(GUI:Attach_LeftBottom(), "tt", 500, 320, 1000, 10)
        local element   = GUI:RichTextCombineCell_Create(richText, "txt_1", 0, 0, "TEXT", {
            str         = "1111111",
            color       = "#FF0000",
            fontSize    = 18
        })

        local element   = GUI:RichTextCombineCell_Create(richText, "txt_2", 0, 0, "TEXT", {
            str         = "22222",
            color       = "#0000FF",
            fontSize    = 12
        })
    
        local layout = GUI:Layout_Create(-1, "panel", 0, 0, 50, 50)
        GUI:addStateEvent(layout, function(state)
            if state == "enter" then
                GUI:removeAllChildren(layout)
                local size = GUI:getContentSize(layout)
            local emojiSfx = GUI:Effect_Create(layout, "sfx", size.width / 2, size.height / 2, 0, 1)
            end
        end)
        local element = GUI:RichTextCombineCell_Create(richText, "node_1", 0, 0, "NODE", {node = layout})
```

- 示例 2 : [3.40.4版本]

```
		local elements  = {}
        local element   = GUI:RichTextCombineCell_Create(-1, "show", 0, 0, "TEXT", {
            str         = "第一行文本11111",
            color       = "#FF0000",
            fontSize    = 16
        })
        table.insert(elements, element)

        local element   = GUI:RichTextCombineCell_Create(-1, "111", 0, 0, "NEWLINE", {})
        table.insert(elements, element)

        local element   = GUI:RichTextCombineCell_Create(-1, "222", 0, 0, "TEXT", {
            str         = "第二行文本222222",
            color       = "#00FF00",
            fontSize    = 16
        })
        table.insert(elements, element)

        local richText = GUI:RichTextCombine_Create(GUI:Attach_LeftBottom(), "RichText", 200, 300, 200, 0)
        GUI:RichTextCombine_pushBackElements(richText, elements)
        GUI:RichTextCombine_format(richText)
        GUI:RichText_setBackgroundColor(richText, "#FFFFFF")
```

# 设置富文本背景颜色 [3.40.3版本]
## RichText_setBackgroundColor(widget, color)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|color      |是|string|颜色值, 例: "#000000"|

# 添加富文本url点击触发事件 [3.40.3版本]
## RichText_setOpenUrlEvent(widget, handle)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|handle     |是|function|触发函数 (param1: 富文本控件, param2: string 文本传递内容)|

- 示例:

```
		local str = string.format("<a href='position#%s#200#200'>TTTT</a>", SL:GetMetaValue("MAP_ID"))
		local richText = GUI:RichText_Create(GUI:Attach_LeftBottom(), "rr", 500, 320, str, 1000)
        GUI:RichText_setOpenUrlEvent(richText, function(sender, str)
            SL:Print(str)
            local slices  = string.split(str, "#")
            local command = slices[1]
            if command == "position" then
                local originScale = GUI:getScale(sender)
                GUI:setScale(sender, originScale + 0.2)
                local function reback()
                    GUI:setScale(sender, originScale)
                end
                SL:scheduleOnce(sender, reback, 0.03)
                
                -- find position
                local mapID   = slices[2]
                local x       = tonumber(slices[3])
                local y       = tonumber(slices[4])
                SL:SetMetaValue("BATTLE_MOVE_BEGIN", mapID, x, y)
            end
        end)
```


# 滚动文本(ScrollText)


# 创建滚动文本
## ScrollText_Create(parent, ID, x, y, width, fontSize, fontColor, str, scrollTime, fontPath)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|文本宽度|
|fontSize   |是|int|字体大小|
|fontColor  |是|int|字体颜色|
|str        |是|string|文本内容|
|scrollTime |否 [3.40.4版本生效]|int|滚动时长 (秒)|
|fontPath	|否 [3.40.6版本生效]|string|字体文件路径|
- 示例代码
```
local scrollText = GUI:ScrollText_Create(parent, "scrollText", 0, 0, 100, 16, "#000000", "文本内容")
```

# 设置滚动文本内容
## ScrollText_setString(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动文本对象|
|value      |是|string|文本内容|

# 获取滚动文本内容
## ScrollText_getString(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动文本对象|

# 设置滚动文本描边
## ScrollText_enableOutline(widget, color, size)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动文本对象|
|color      |是|string|描边色值("#000000")|
|size       |是|int|描边大小|

# 设置滚动文本水平对齐
## ScrollText_setHorizontalAlignment(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动文本对象|
|value      |是|int|对齐方式：<br>1 左对齐<br>2 水平居中<br>3 右对齐|

# 设置滚动文本颜色
## ScrollText_setTextColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动文本对象|
|value      |是|string|色值("#000000")|


# 节点(Node)


# 创建节点
## Node_Create(parent, ID, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
- 示例代码

```
 local node = GUI:Node_Create(parent, "node", 0, 0)
```

# Widget


# 创建Widget
## Widget_Create(parent, ID, x, y, width, height)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽|
|height     |是|int|高|
- 示例代码

```
 local widget =  GUI:Widget_Create(parent, "widget_1", 0, 0, 300, 200)
```

# 物品框(ItemShow)


# 创建物品框
## ItemShow_Create(parent, ID, x, y, setData)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|setData    |是|table|配置数据|
- 配置数据详细参数 示例

```
	local setData  = {}
	setData.index = 4                     -- 物品Index
	setData.look  = true                  -- 是否显示tips
	setData.bgVisible = true              -- 是否显示背景框
	setData.count = 1                     -- 物品数量
	setData.color = 225                   -- 颜色ID （0~255）
	--setData.starLv = false              -- 是否显示星级
	--setData.checkPower = true           -- 是否检查战力从而显示提升小箭头
	--setData.showModelEffect = true      -- 只显示内观特效不显示背包特效
	--setData.onlyShowSFX = true          -- 只显示道具特效其它都不显示
	--setData.noSwallow = true            -- 是否触摸吞噬
	--setData.noMouseTips = true          -- 鼠标移入不显示tips
	--setData.mouseCheckTimes = 6         -- 鼠标移入检测物品框是否可见时查找父节点层数, 默认6
	--setData.itemData = table            -- 物品数据 ( ！有真实物品数据可直接传, 避免Tips缺漏 )

	local item = GUI:ItemShow_Create(ui_icon, "item", 0, 0, setData)
```
- 示例代码2 (等同于EquipShow创建)

```
	-- 获取装备位1的装备数据
	local equipData    = SL:GetMetaValue("EQUIP_DATA", 1)
    if equipData then
        local info = {}
        info.index = equipData.Index
        info.itemData = equipData		-- 传入装备数据
        info.look = true
        info.bgVisible = true
        info.starLv = true
		local item = GUI:ItemShow_Create(parent, "item", 0, 0, info)
	end
```

# 设置物品框单击事件
## ItemShow_addReplaceClickEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|eventCB     |是|function|单击事件函数|

# 设置物品框双击事件
## ItemShow_addDoubleEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|eventCB    |是|function|双击事件函数|

# 设置物品框长按事件
## ItemShow_addPressEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|eventCB    |是|function|长按事件函数|

# 设置物品框是否置灰
## ItemShow_setIconGrey(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|value      |是|bool|是否置灰|

# 设置物品框是否选中
## ItemShow_setItemShowChooseState(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|value      |是|bool|是否选中|

# 设置物品框是否拖动
## ItemShow_setMoveEable(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|value      |是|bool|是否拖动|

# 更新物品框内容
## ItemShow_updateItem(widget, itemData)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|setData   |是|table|配置数据|

# 调用GUILayout/Item.lua中的函数
## ItemShow_OnRunFunc(widget, funcname, ...)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|funcname   |是|string|GUILayout/Item.lua中的函数名字|
|...        |否|any|可变参数

*例如*
```
	-- 设置ItemShow的显示道具数量为20
	local ItemShow = GUI:ItemShow_Create(parent, "Item", 0, 0, itemData)
	ItemShow_OnRunFunc(ItemShow, "SetCount", 20)
```

# 设置物品框是否触摸吞噬
## ItemShow_setItemTouchSwallow(widget, bool)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品框对象|
|value      |是|bool|是否触摸吞噬|
# 物品放入框(ItemBox)


# 创建物品放入框
## ItemBox_Create(parent, ID, x, y, img, boxindex, stdmode)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|img        |是|string|放置框底图资源路径|
|boxindex   |是|int|放置框 唯一ID|
|stdmode    |是|string/number/table|允许传入的StdMode ("*": 所有 、单个用number 、多个用table)|

# 获取对应ID放置框的物品数据
## ItemBox_GetItemData(widget, boxindex)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品放入框控件对象|
|boxindex   |是|int|放置框 唯一ID|

# 清空对应ID放置框的传入数据
## ItemBox_RemoveBoxData(widget, boxindex)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品放入框控件对象|
|boxindex   |是|int|放置框 唯一ID|

# 更新对应ID放置框的物品数据 [3.40.4]
## ItemBox_UpdateBoxData(widget, boxindex)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|物品放入框控件对象|
|boxindex   |是|int|放置框 唯一ID|
|itemData   |否|tbl|填充指定的ItemData数据<br>[支持版本号3.40.7以上]|
# 复选框(CheckBox)


# 创建复选框
## CheckBox_Create(parent, ID, x, y, nimg, pimg)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|nimg       |是|string|正常图片路径|
|pimg       |是|string|选中图片路径|
- 示例代码
```
local nimg = "res/private/gui_edit/CheckBox_Normal.png"
local pimg = "res/private/gui_edit/CheckBox_Press.png"
local checkBox = GUI:CheckBox_Create(parent, "checkBox", 0, 0, nimg, pimg)
```

# 设置复选框背景图片
## CheckBox_loadTextureBackGround(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|
|value      |是|string|默认状态图片路径|

## CheckBox_loadTextureFrontCross(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|
|value      |是|string|选中状态图片路径|

## CheckBox_loadTextureFrontCrossDisabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|
|value      |是|string|禁用状态图片路径|

# 设置复选框选中或取消
## CheckBox_setSelected(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|
|value      |是|bool|选中或取消|

# 获取复选框是否选中
## CheckBox_isSelected(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|

# 设置复选框监听事件
## CheckBox_addOnEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|复选框对象|
|eventCB    |是|function|事件函数|


# 输入框(TextInput)


# 创建输入框
## TextInput_Create(parent, ID, x, y, width, height, fontSize)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
|fontSize   |是|int|字体大小|
- 示例代码
```
local TextField_input = GUI:TextInput_Create(parent, "TextField_input", 0, 0, 30, 33, 16)
```

# 设置输入框字体颜色
## TextInput_setFontColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|色值("#000000")|

# 设置输入框字体 [仅支持移动端设置]
## TextInput_setFont(widget, value, value2)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|字体路径|
|value2     |是|int|字号|

# 设置输入框字体大小
## TextInput_setFontSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|字号|

# 设置输入框占位文本字体
## TextInput_setPlaceholderFont(widget, value, value2)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|字体路径|
|value2     |是|string|字体("font.ttf")|

# 设置输入框占位文本字体颜色
## TextInput_setPlaceholderFontColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|色值("#000000")|

# 设置输入框占位文本字体大小
## TextInput_setPlaceholderFontSize(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|字号|

# 设置输入框占位文本
## TextInput_setPlaceHolder(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|输入内容|

# 设置输入框文本
## TextInput_setString(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|string|输入内容|

# 获取输入框文本
## TextInput_getString(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|

# 设置输入框行宽
## TextInput_setMaxLength(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|输入框控件宽度|

# 设置输入框水平对齐
## TextInput_setTextHorizontalAlignment(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|对齐方式：<br>0 顶对齐<br> 1 底对齐<br>2 水平居中|

# 设置输入框文本类型
## TextInput_setInputFlag(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|类型|
-  类型如下
```
0   -- 密码形式
1   -- 敏感数据输入
2   -- 每个单词首字符大写，并有提示
3   -- 第一句首字符大写，并有提示
4   -- 自动大写
```

# 设置输入框键盘编辑类型
## TextInput_setInputMode(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|类型|
-  类型如下
```
0   -- 开启任何文本的输入键盘(含换行)
1   -- 开启邮箱地址输入类型键盘
2   -- 开启数字符号输入类型键盘
3   -- 开启电话号码输入类型键盘
4   -- 开启URL输入类型键盘
5   -- 开启数字输入类型键盘(含小数点)
6   -- 开启任何文本的输入键盘(不含换行)
```

# 设置输入框弹出式键盘返回类型
## TextInput_setReturnType(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|value      |是|int|类型|

# 设置输入框监听事件
## TextInput_addOnEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|
|eventCB    |是|function|事件处理函数|

# 关闭输入框输入 [3.40.5版本]
## TextInput_closeInput(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|输入框对象|


# 滚动条(Slider)


# 创建滚动条
## Slider_Create(parent, ID, x, y, barimg, pbarimg, nimg)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|barimg     |是|string|滚动条背景图片|
|pbarimg    |是|string|滚动条图片|
|nimg       |是|string|滚动条拖动块图片|
- 示例代码
```
local barimg = "res/private/new_setting/bg_progress.png"
local pbarimg = "res/private/new_setting/bg_progress2.png"
local nimg = "res/private/new_setting/icon_xdtzy_17.png"
local Slider_progress = GUI:Slider_Create(parent, "Slider_progress", 0, 0, barimg, pbarimg, nimg)
```

# 设置滚动条背景图
## Slider_loadBarTexture(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|string|背景图路径|

# 设置滚动条图片
## Slider_loadProgressBarTexture(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|string|滚动条图片路径|

# 设置滚动条拖动块普通图片
## Slider_loadSlidBallTextureNormal(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|string|拖动块图片路径|

# 设置滚动条进度
## Slider_setPercent(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|int|滚动条进度(0-100)|

# 获得滚动条进度
## Slider_getPercent(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
- 返回值：滚动条进度

# 设置滚动条最大进度值 [3.40.3版本]
## Slider_setMaxPercent(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|int|滚动条最大进度值|

# 设置滚动条触摸事件
## Slider_addOnEvent(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|滚动条对象|
|value      |是|function|事件函数|


# 圆形进度条(ProgressTimer)


# 创建圆形进度条
## ProgressTimer_Create(parent, ID, x, y, img)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|img        |是|string|图片路径|
- 示例代码
```
local ui_img = "res/private/main/Skill/hero2/0_0001.png"
local heroProgress = GUI:ProgressTimer_Create(parent, "heroProgress", 0, 0, ui_img)
```

# 设置圆形进度条百分比
## ProgressTimer_setPercentage(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|进度(0-100)|

# 获取圆形进度条百分比
## ProgressTimer_getPercentage(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

# 设置圆形进度条方向
## ProgressTimer_setReverseDirection(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|bool|true 顺时针<br>false 逆时针|

# 设置圆形进度条动作和回调函数
## ProgressTimer_progressFromTo(widget, time, from, to, completeCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|from       |是|int|开始进度(0-100)|
|to         |是|int|结束进度(0-100)|
|completeCB |是|function|回调函数|

## ProgressTimer_progressTo(widget, time, to, completeCB, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|to         |是|int|结束进度(0-100)|
|completeCB |是|function|回调函数|
|tag        |是|int|标记|

# 设置圆形进度条背景图
## ProgressTimer_ChangeImg(widget, img)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|img        |是|string|图片路径|


# 条形进度条(LoadingBar)


# 创建进度条
## LoadingBar_Create(parent, ID, x, y, nimg, direction)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|nimg       |是|string|图片路径|
|direction  |是|int|方向：<br>0 从左到右<br>1 从右到左|
- 示例代码
```
local imgBar = "res/private/gui_edit/LoadingBar.png"
local loadingBar = GUI:LoadingBar_Create(parent, "loadingBar", 0, 0, imgBar, 0)
```

# 设置进度条图片
## LoadingBar_loadTexture(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
|value      |是|string|图片路径|

# 设置进度条方向
## LoadingBar_setDirection(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
|value      |是|int|方向：<br>0 从左到右<br>1 从右到左|

# 设置进度条进度
## LoadingBar_setPercent(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
|value      |是|int|进度(0-100)|

# 获取进度条进度
## LoadingBar_getPercent(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
- 返回值：进度条进度

# 设置进度条颜色
## LoadingBar_setColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
|value      |是|string|色值("#000000")|

# 获取进度条颜色
## LoadingBar_getColor(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|进度条对象|
- 返回值：string 进度条颜色值


# 特效(Effect)


# 创建特效
## Effect_Create(parent, ID, x, y, effecttype, effectid, sex, act, dir, speed)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|effecttype |是|int|0 特效<br>1 NPC<br>2 怪物<br>3 技能<br>4 人物<br>5 武器<br>6 翅膀<br>7 发型<br>8 盾牌[3.40.3版本]|
|effectid  |是|int|特效id|
|sex       |否|int|性别(0 男 1 女)|
|act       |否|int|0 待机<br>1 走<br>2 攻击<br>3 施法 <br>4 死亡<br>5 跑步|
|dir       |否|int|方向|
|speed     |否|int|播放速度|
- 代码示例

```
-- 特效展示 Ctrl + F4 查看
local sfx = GUI:Effect_Create(parent, "sfx", 0, 0, 0, 4004, 0, 0, 3, 1)
```

# 特效播放
## Effect_play(widget, act, dir, isLoop, speed, isSequence)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|特效对象|
|act        |是|int|0 待机<br>1 走<br>2 攻击<br>3 施法 <br>4 死亡<br>5 跑步|
|dir        |是|int|方向|
|isLoop     |是|bool|是否循环播放|
|speed      |否|int|播放速度|
|isSequence |否|boolean|倒放参数 [仅false为倒放特效 ]|

# 特效停止
## Effect_stop(widget, frameIndex, act, dir)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|特效对象|
|frameIndex |否|int|第几帧|
|act        |否|int|0 待机<br>1 走<br>2 攻击<br>3 施法 <br>4 死亡<br>5 跑步|
|dir        |否|int|方向|

# 特效播放完成事件
## Effect_addOnCompleteEvent(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|特效对象|
|value      |是|function|播放完成回调函数|

# 设置特效播放完自动移除 [3.40.3版本]
## Effect_setAutoRemoveOnFinish(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|特效对象|


# 动画(Timeline)


#界面弹窗特效
## Timeline_Window1(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=03f85a6ed2e55e4683fcfa2b2065ef89)

## Timeline_Window2(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=680189876aeeed47b9a4146b5b5fe836)

## Timeline_Window3(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=295f3c9fdd8a23f472baadd4e3da2b91)

## Timeline_Window4(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=576798efe374c994ec5420673ce7c2bf)

## Timeline_Window5(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=300d9ba741e3140577e17e3b878a261e)

## Timeline_Window6(widget, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|timelineCB |是|function|回调函数|
- 弹窗效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=dc71a59d3d406543465c92db7c69bf2b)

# 设置动画标记
## Timeline_SetTag(action, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|tag        |是|int|标记值|

# 停止所有动画
## Timeline_StopAll(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|

## Timeline_StopByTag(widget, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|tag        |是|int|标记值|
- 通过标记停止动画

# 动画淡出效果
## Timeline_FadeOut(widget, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 淡出效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=3900ccbab7b16c56dbcfb2fc62cd18b2)

## Timeline_FadeIn(widget, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|

> **淡入需要先设置控件透明度**

- 淡入效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=51a54ae9f13a972b70e71e2cba2d025d)

## Timeline_FadeTo(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|透明度(0-255)|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 修改透明度到某个值
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=81918cf5e2aaf95e6eded401758fa4db)

# 放大缩小动画
## Timeline_ScaleTo(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|缩放比例(0-100)|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 放大缩小到某个比例（放大缩小到原始的倍数）
```lua
-- 实际上图片只放大了2倍
local img = GUI:Image_Create(parent, "img", 0, 0, "res/bg.png")
GUI:Timeline_ScaleTo(img, 2, 1, nil)
GUI:Timeline_ScaleTo(img, 2, 1, nil)
```
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=fc336fbabc3a576209d113141791986e)

## Timeline_ScaleBy(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|缩放比例(0-100)|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 放大缩小到某个比例（放大缩小多少倍数）
```lua
-- 实际上图片放大了4倍
local img = GUI:Image_Create(parent, "img", 0, 0, "res/bg.png")
GUI:Timeline_ScaleBy(img, 2, 1, nil)
GUI:Timeline_ScaleBy(img, 2, 1, nil)
```
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9e8394c7a44e7232fae9d2500167771f)

# 旋转动画
## Timeline_RotateTo(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|旋转角度(0-360)|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 旋转到某个角度（旋转到指定角度）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=42b1c0005259534480b7cd6f059dc3aa)

## Timeline_RotateBy(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|旋转角度(0-360)|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 旋转到某个角度（从原来角度 旋转到 某个角度）

# 移动动画
## Timeline_MoveTo(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|table|{x = 0, y = 0}|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 移动到某坐标（移动绝对位置）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0f04a0785fb11a638b54455340566c9d)

## Timeline_MoveBy(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|table|{x = 0, y = 0}|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 移动到某坐标（移动相对位置）

# 闪烁动画
## Timeline_Blink(widget, value, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|int|闪烁次数|
|time       |是|int|时间|
|timelineCB |是|function|回调函数|
- 闪烁效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7a39a973ecae51a8f66748c0da9e5faa)

# 震动动画
## Timeline_Shake(widget, time, x, y, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|x          |是|int|X轴震动像素|
|y          |是|int|Y轴震动像素|
|timelineCB |是|function|回调函数|
- 震动效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=782737b2cce9e0cbe34f030b1e870faf)

# 疯狂抖动动画
## Timeline_Waggle(widget, time, angle)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|时间|
|angle      |是|int|抖动幅度（0-360）|
- 震动效果

# 动画延迟播放
## Timeline_DelayTime(widget, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|延迟时间|
|timelineCB |是|function|回调函数|

# 动画回调方法
## Timeline_CallFunc(widget, time, timelineCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|延迟时间|
|timelineCB |是|function|回调函数|

# 动画延迟显示
## Timeline_Show(widget, time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|延迟时间|

# 动画延迟隐藏
## Timeline_Hide(widget, time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|time       |是|int|延迟时间|

# 缓动动画
## Timeline_EaseSineIn_MoveTo(widget, value, time, callback)

` widget 对象由慢到快，移动到目标位置 `

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|table|目标坐标位置|
|time       |是|int|动作时间|
|callback   |否|function|动作执行完的回调|

## Timeline_EaseSineOut_MoveTo(widget, value, time, callback)

` widget 对象由快到慢，移动到目标位置 `

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象|
|value      |是|table|目标坐标位置|
|time       |是|int|动作时间|
|callback   |否|function|动作执行完的回调|

## Timeline_DigitChange(widget, cur, target, interval)

` widget 数字滚动动画 `

|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|对象 [ 仅限Button、Text控件] （3.40.8支持TextAtlas控件）|
|cur        |是|int|当前数值|
|target     |是|int|目标数值|
|interval   |否|int|变动间隔（秒）|


# 人物模型(UIModel)


# 创建人物模型
## UIModel_Create(parent, ID, x, y, sex, feature, scale, useStaticScale, job, ext_param)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|sex        |是|int|0 男性 1 女性|
|feature    |是|table|模型属性|
|scale      |否|int|缩放比例(0-1)|
|useStaticScale|否|boolean|是否使用game_data配置staticSacle数据, 默认忽略|
|job        |否|int|职业id 012 战法道等新增职业 [3.40.5版本新增字段]|
|ext_param  |否|table|额外参数列表 [3.40.8版本新增字段]|
- 示例代码

```
-- feature 使用方法
！！除特效ID外 其余装备ID传入对应装备数据的Looks参数.
local feature= {}
feature.clothID                  -- 衣服
feature.weaponID                 -- 武器id
feature.headID                   -- 头盔id
feature.headEffectID             -- 头盔特效id
feature.weaponEffectID           -- 武器特效id
feature.clothEffectID            -- 衣服特效id
feature.capID                    -- 斗笠id
feature.shieldID                 -- 盾牌id
feature.shieldEffectID           -- 盾牌特效id
feature.tDressID                 -- 时装id
feature.tDressEffectID           -- 时装特效id
feature.tWeaponID
feature.tWeaponEffectID
feature.capEffectID              -- 斗笠特效id
feature.veilID                   -- 面巾id
feature.veilEffectID             -- 面巾特效id
feature.notShowMold              -- 是否为裸模
feature.notShowHair              -- 是否显示头发
local UIModel = GUI:UIModel_Create(parent, "UIMODEL", 0, 0, 0, feature, nil)
```


# 层容器(Layout)


# 创建层容器
## Layout_Create(parent, ID, x, y, width, height, isClip)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|长度|
|isClip     |是|bool|是否裁切|
- 示例代码
```
local layout = GUI:Layout_Create(parent, "layout", 0, 0, 100, 100, false)
```

# 设置层背景颜色
## Layout_setBackGroundColor(widget, value)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|value      |是|string|色值("#000000")<br> ! 渐变色需传参table `{"#FF0000", "#FFFFFF"}`|

# 设置层背景颜色类型
## Layout_setBackGroundColorType(widget, value)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|value      |是|int|类型(1单色，2渐变色)|

# 设置层背景颜色不透明度
## Layout_setBackGroundColorOpacity(widget, value)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|value      |是|int|不透明度(0-255)|

# 设置层背景是否裁切
## Layout_setClippingEnabled(widget, value)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|value      |是|bool|是否裁切|

# 设置层背景图片
## Layout_setBackGroundImage(widget, value)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|value      |是|string|图片路径|

# 设置层背景图片九宫格
## Layout_setBackGroundImageScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|
|scale9l    |是|int|左边比例|
|scale9r    |是|int|右边比例|
|scale9t    |是|int|上边比例|
|scale9b    |是|int|下边比例|

# 移除层背景图片设置 [3.40.5版本]
## Layout_removeBackGroundImage(widget)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|

# 获取层背景图片文件路径 [3.40.8版本]
## Layout_getBackGroundImageFile(widget)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|层对象|


# 列表容器(ListView)


# 创建列表容器
## ListView_Create(parent, ID, x, y, width, height, direction)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
|direction  |是|int|1：垂直; 2：水平|
- 示例代码

```
local listView = GUI:ListView_Create(parent,"listView", 0, 0, 300, 400, 1)
```

# 设置列表容器对齐方式
## ListView_setGravity(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|0：左对齐<br>1：右对齐<br>2：水平居中<br>3：顶对齐<br>4：底对齐<br>5：垂直居中|

# 设置列表容器滑动方向
## ListView_setDirection(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|1：垂直; 2：水平|

# 设置列表容器间隔
## ListView_setItemsMargin(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|间隔大小(50像素)|

# 获取列表容器间隔
## ListView_getItemsMargin(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
-  返回值：间隔距离(像素)

# 设置列表容器是否有回弹
## ListView_setBounceEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|bool|是否有回弹|

# 设置列表容器是否有裁切
## ListView_setClippingEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|bool|是否有裁切|

# 设置列表容器背景颜色
## ListView_setBackGroundColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|string|色值("#000000")<br> ! 渐变色需传参table `{"#FF0000", "#FFFFFF"}`|

# 设置列表容器背景颜色类型
## ListView_setBackGroundColorType(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|1：单色，2：渐变色|

# 设置列表容器背景透明度
## ListView_setBackGroundColorOpacity(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|透明度(0-255)|

# 设置列表容器背景图片
## ListView_setBackGroundImage(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|string|图片路径|

# 设置列表容器背景图片九宫格
## ListView_setBackGroundImageScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|scale9l    |是|int|左边比例|
|scale9r    |是|int|右边比例|
|scale9t    |是|int|上边比例|
|scale9b    |是|int|下边比例|

# 移除列表容器背景图片设置 [3.40.5版本]
## ListView_removeBackGroundImage(widget)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 列表容器加载子节点
## ListView_pushBackCustomItem(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|obj|子节点对象（末尾加载）|

## ListView_insertCustomItem(widget, value, value2)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|obj|子节点对象|
|value      |是|int|序列号（index = 1）|

# 列表容器删除所有子节点
## ListView_removeAllItems(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 通过序列号删除列表容器子节点
## ListView_removeItemByIndex(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|index      |是|int|序列号位置|

# 列表容器删除子节点
## ListView_removeChild(widget, item)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|item       |是|obj|子节点对象|

# 跳转到列表容器序列号节点位置
## ListView_jumpToItem(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|序列号位置|

# 某一时间内滑动到列表容器顶部
## ListView_scrollToTop(widget,time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|滑动速度是否减弱|

# 某一时间内滑动到列表容器底部
## ListView_scrollToBottom(widget,time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|滑动速度是否减弱|

# 获取列表容器最顶部可见范围子节点
## ListView_getTopmostItemInCurrentView(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
-- 返回值：顶部范围子节点对象

# 获取列表容器最底部部可见范围子节点
## ListView_getBottommostItemInCurrentView(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：底部范围子节点对象

# 获取子节点序列号
## ListView_getItemIndex(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|obj|子节点对象|
- 返回值：子节点序列号

# 通过子节点序列号获取子节点对象
## ListView_getItemByIndex(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|子节点序列号|
-  返回值：子控件对象

# 获取列表容器所有子节点对象
## ListView_getItems(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：所有子节点对象

# 获取列表容器所有子节点数量
## ListView_getItemCount(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：子节点总数量

# 设置列表容器滚动事件
## ListView_addOnScrollEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|eventCB    |是|function|事件函数|

# 列表容器刷新
## ListView_doLayout(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 列表容器可见区域绘制
## ListView_paintItems(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 列表容器可见区域自动绘制
## ListView_autoPaintItems(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 获取列表容器滚动范围大小
## ListView_getInnerContainerSize(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值 列表容器滚动范围大小

# 获取列表容器内部滚动区域坐标
## ListView_getInnerContainerPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值 列表容器内部滚动区域坐标

# 设置列表容器滚动到某百分比位置(垂直方向)
## ListView_scrollToPercentVertical(widget, percent, time, bool)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|percent    |是|int|百分比(0-100)|
|time       |是|int|时间(秒)|
|bool       |是|boolean|是否衰减滚动速度|

# 设置列表容器滚动到某百分比位置(水平方向)
## ListView_scrollToPercentHorizontal(widget, percent, time, bool)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|percent    |是|int|百分比(0-100)|
|time       |是|int|时间(秒)|
|bool       |是|boolean|是否衰减滚动速度|

# 添加鼠标滚轮滑动列表容器事件
## ListView_addMouseScrollPercent(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|


# 滚动容器(ScrollView)


# 创建滚动容器
## ScrollView_Create(parent, ID, x, y, width, height, direction)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
|direction  |是|int|1：垂直; 2：水平|
- 示例代码

```
local scrollView = GUI:ScrollView_Create(parent, "scrollView", 0, 0, 300, 500, 1)
```

# 设置滚动容器滚动范围大小
## ScrollView_setInnerContainerSize(widget, value1, value2)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value1     |是|int 或 table|宽度 或 尺寸|
|value2     |否|int|高度|
- 代码示例

```
local width = 300
local height = 400
local size = {width = 300, height = 400}
GUI:ScrollView_setInnerContainerSize(ScrollView, width, height)
GUI:ScrollView_setInnerContainerSize(ScrollView, size)
```

# 获取滚动容器滚动范围大小
## ScrollView_getInnerContainerSize(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：滚动容器滚动范围大小

# 获取容器内部滚动区域坐标 [3.40.3版本]
## ScrollView_getInnerContainerPosition(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值 容器内部滚动区域坐标

# 设置滚动容器滚动方向
## ScrollView_setDirection(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|1：垂直; 2：水平|

# 设置滚动容器是否有回弹
## ScrollView_setBounceEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|bool|是否有回弹|

# 设置滚动容器是否有裁切
## ScrollView_setClippingEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|bool|是否有裁切|

# 设置滚动容器背景颜色
## ScrollView_setBackGroundColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|string|色值("#000000")<br> ! 渐变色需传参table `{"#FF0000", "#FFFFFF"}`|

# 设置滚动容器背景颜色类型
## ScrollView_setBackGroundColorType(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|1：单色，2：渐变色|

# 设置滚动容器背景透明度
## ScrollView_setBackGroundOpacity(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|透明度(0-255)|

# 设置滚动容器背景图片
## ScrollView_setBackGroundImage(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|string|图片路径|

# 设置滚动器背景图片九宫格
## ScrollView_setBackGroundImageScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|scale9l    |是|int|左边比例|
|scale9r    |是|int|右边比例|
|scale9t    |是|int|上边比例|
|scale9b    |是|int|下边比例|

# 移除滚动容器背景图片设置 [3.40.5版本]
## ScrollView_removeBackGroundImage(widget)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 设置滚动容器滚动事件
## ScrollView_addOnScrollEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|eventCB    |是|function|事件函数|

# 滚动容器加载子节点
## ScrollView_addChild(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|obj|子节点对象|

# 滚动容器删除所有子节点
## ScrollView_removeAllChildren(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|

# 滚动容器衰减滚动
## ScrollView_scrollToTop(widget, time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减（顶部）|

## ScrollView_scrollToBottom(widget, time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减（底部）|

## ScrollView_scrollToTopLeft(widget, time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减（顶左）|

## ScrollView_scrollToRight(widget, time, boolvalue)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减（右边）|

## ScrollView_scrollToLeft(widget, time, boolvalue) [3.40.5版本]
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减（左边）|

## ScrollView_scrollToPercentVertical(widget, percent, time, bool) [3.40.5版本]
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|percent    |是|int|百分比|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减滚动速度|
- 垂直方向滚动

## ScrollView_scrollToPercentHorizontal(widget, percent, time, bool) [3.40.5版本]
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|percent    |是|int|百分比|
|time       |是|int|时间|
|boolvalue  |是|bool|是否衰减滚动速度|
- 水平方向滚动

# 滚动容器添加滚动条
## SetScrollViewVerticalBar(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|param      |是|table|布局参数|
```lua
        GUI:SetScrollViewVerticalBar(parent, {
            bgPic       = "res/private/gui_edit/scroll/line.png",   -- 背景图
            barPic      = "res/private/gui_edit/scroll/p.png",      -- 滑动按钮图片
            Arr1PicN    = "res/private/gui_edit/scroll/t.png",      -- 上（正常图）
            Arr1PicP    = "res/private/gui_edit/scroll/t_1.png",    -- 上（按下图）可不传
            Arr2PicN    = "res/private/gui_edit/scroll/b.png",      -- 下（正常图）
            Arr2PicP    = "res/private/gui_edit/scroll/b_1.png",    -- 下（按下图）可不传
            default     = 0,                    -- 进度条值（默认是0）
            x           = 0,                    -- 进度条坐标 x
            y           = 0,                    -- 进度条坐标 y
            list        = listHandle,           -- 滚动的容器 list
            callFunc    = function (send)       -- 容器滚动的回调函数
                SL:Print("回调函数")
            end,
        })
```


# 翻页容器(PageView)


# 创建翻页容器
## PageView_Create(parent, ID, x, y, width, height, direction)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
- 示例代码

```
local pageView = GUI:PageView_Create(parent, "pageView", 0, 0, 300, 500, 1)
```

# 设置翻页容器是否有裁切
## PageView_setClippingEnabled(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|bool|是否有裁切|

# 设置翻页容器背景颜色
## PageView_setBackGroundColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|string|色值("#000000")<br> ! 渐变色需传参table `{"#FF0000", "#FFFFFF"}`|

# 设置翻页容器背景颜色类型
## PageView_setBackGroundColorType(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|1：单色，2：渐变色|

# 设置翻页容器背景透明度
## PageView_setBackGroundColorOpacity(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|int|透明度(0-255)|

# 设置翻页容器滚动到子页面
## PageView_scrollToItem(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|index      |是|int|子页面序列号|

# 获取当前子页面序列号
## PageView_getCurrentPageIndex(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：子页面序列号

# 设置翻页容器当前子页序列号 [3.40.3版本]
## PageView_setCurrentPageIndex(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|index      |是|int|子页面序列号|

# 获取翻页容器子页面
## PageView_getItems(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：子页面对象

# 获取翻页容器子页面数量
## PageView_getItemCount(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
- 返回值：子页面数量

# 翻页容器加载子页面
## PageView_addPage(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|value      |是|obj|子页面对象|

# 翻页容器加监听事件
## PageView_addOnEvent(widget, eventCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|容器对象|
|eventCB    |是|function|监听事件函数|


# QuickCell


# 创建滚动容器子节点
## QuickCell_Create(parent, ID, x, y, w, h, createCB)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|w          |是|int|宽度|
|h          |是|int|高度|
|createCB   |是|function|创建子节点内容回调 [函数返回 widget]|
|activeCB	|否|function|判断是否需要激活/创建 [函数返回 boolean值]
- 示例代码

```
    local listviewCells = GUI:ListView_Create(_parent, "listviewCells", 200, 80, 587, 200, 1)
        for i = 1, 10 do
            GUI:QuickCell_Create(listviewCells, "QuickCell_Create"..i, 0, 0, 587, 200,  function(quickParent)
                local item = GUI:Layout_Create(quickParent, "cell_", 0, 0, 571, 70)
                -- 图标
                local itemIcon = GUI:Image_Create(item, "item_icon", 80, 35, "res/01/010001.png")
                GUI:setAnchorPoint(itemIcon, 0.5, 0.5)
                -- name
                local itemDesc = GUI:Text_Create(item, "item_name", 120, 40, 20, "#D6C6AD", "name.."..i)

                -- tips
                local itemDesc = GUI:Text_Create(item, "item_desc", 120, 15, 16, "#D6C6AD", "tips")

                -- 分割线
                local Image_line = GUI:Image_Create(item, "item_line", 0, 0, "res/buff/bg_buffzy_02.png")
                GUI:setAnchorPoint(Image_line, 0.5, 0)
                GUI:setPosition(Image_line, 571/2, 0)

                return item
            end)
        end
```

# 刷新展示
## QuickCell_Refresh(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|QuickCell对象|

# 强制退出/ 清理内容
## QuickCell_Exit(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|QuickCell对象|

```
	-- 顺序使用 通常用于刷新单个cell内容 [可参照 GUILayout/AuctionPutList 等..]
	GUI:QuickCell_Exit(quickCell)
	GUI:QuickCell_Refresh(quickCell)
```


# 动作(Action)


#播放动作
## runAction(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|value      |是|obj|动作内容|

## getActionByTag(widget, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|tag        |是|int|动作标记|
-- 通过标记获取动作内容

#停止所有动作
## stopAllActions(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget       |是|obj|控件对象|

## stopActionByTag(widget, tag)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|控件对象|
|tag        |是|int|动作标记|
-- 通过标记停止动作

# 移动
## ActionMoveTo(time, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
- 移动到B点：以世界坐标系为原点(0,0)

## ActionMoveBy(time, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
- A点移动到B点 移动相对位置：以A点为原点(0,0)

# 缩放
## ActionScaleTo(time, ratio, ...)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|ratio      |是|int|缩放比例（百分比）|
- 放大或缩小到某一比例
- 有第三个参数时, 后两位参数分别表示X轴缩放比、Y轴缩放比 **3.40.8版本新增**

## ActionScaleBy(time, ratio, ...)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|ratio      |是|int|缩放比例（百分比）|
- 放大或缩小到原来的某一比例
- 有第三个参数时, 后两位参数分别表示X轴缩放比、Y轴缩放比 **3.40.8版本新增**

# 旋转
## ActionRotateTo(time, angle)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|angle      |是|int|旋转角度|
- 旋转到多少角度

## ActionRotateBy(time, angle)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|angle      |是|int|旋转角度|
- 旋转到原来的多少角度

# 淡入淡出
## ActionFadeIn(time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
- 淡入

## ActionFadeOut(time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
- 淡出

# 闪烁
## ActionBlink(time, num)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|time       |是|int|时间|
|num        |是|int|闪烁次数|

# 动画回调函数
## CallFunc(callback)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|callback       |是|function|回调函数|

# 延迟
## DelayTime(time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|callback   |是|int|延迟时间|

# 显示与隐藏
## ActionShow() 显示
## ActionHide() 隐藏

# 移除自身
## ActionRemoveSelf()

# 播放顺序
## ActionSequence(action, ...) 多个动作顺序播放
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|

*示例 : * 
```
	local function callback()
		SL:Print("_____")
	end
	GUI:runAction(item., GUI:ActionSequence(GUI:ActionScaleTo(0.1, 1.4), GUI:ActionScaleTo(0.1, 1), GUI:CallFunc(callback)))
```

## ActionSpawn(action, ...) 多个动作同时播放
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|

# 循环播放
## ActionRepeat(action, time)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|
|time       |是|int|时间|

## ActionRepeatForever(action)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象（一直循环）|

# 复合动作
## ActionEaseBackIn(action) 加速度向右，反方向缓慢移动
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|
## ActionEaseBackOut(action) 快速移动到结束，然后缓慢返回到结束
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|

# 贝塞尔曲线运动
## ActionBezierTo(time, controlPoint_1, controlPoint_2, endPosition)
|参数        	|必选|类型|注释|
|:----      	|:-|:--|:---|
|time       	|是|int|时间|
|controlPoint_1 |是|table|控制点1 坐标|
|controlPoint_2 |是|table|控制点2 坐标|
|endPosition    |是|table|结束坐标|

*示例 : * 
```
	local btn = GUI:Button_Create(GUI:Attach_LeftBottom(), "btn1", 200, 200, "res/public/1900000510.png")
	local startPos = GUI:p(200, 200)
	local endPos = GUI:p(600, 200)
	local controlPoint_1 = GUI:p(200, 800)
	local controlPoint_2 = GUI:p(600, 500)
	local endPosition = endPos
	local bezier = GUI:ActionBezierTo(2, controlPoint_1, controlPoint_2, endPosition)
	GUI:runAction(btn, bezier)
```

# 指数缓冲动作
## ActionEaseExponentialIn(action) 缓慢开始, 加速结束
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|

## ActionEaseExponentialOut(action) 加速开始, 缓慢结束
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|

## ActionEaseExponentialInOut(action) 动作缓慢开始和终止
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|action     |是|obj|动作对象|


# 序列帧动画(Frames)


# 创建序列帧动画
## Frames_Create(parent, ID, x, y, prefix, suffix, beginframe, finishframe, ext)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|prefix     |是|string|前缀|
|suffix     |是|string|后缀|
|beginframe |否|int|起始帧, 默认1|
|finishframe|否|int|结束帧|
|ext        |否|table|附加参数, {speed = 播放速度(毫秒), count = 图片数量, loop = 播放次数(-1: 循环), finishhide = 播放结束是否隐藏(1: 隐藏)}|
- 示例代码

```
 	local ext = {
        count = 10,
        speed = 100,
        loop  =  1,
        finishhide = 1
    }
	local frames = GUI:Frames_Create(wnd, "Frames_1", 200, 200, "res/public/word_fubentg_", ".png", 1, 10, ext)
```

# 粒子特效(ParticleEffect)


# 创建粒子特效
## ParticleEffect_Create(parent, ID, x, y, res)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|res        |是|string|粒子特效资源路径 plist文件|

# 设置持续时间
## ParticleEffect_setDuration(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|粒子特效|
|value      |是|int|持续时间, 单位: 秒 <br> -1 表示永久|

# 设置总粒子数量
## ParticleEffect_setTotalParticles(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|粒子特效|
|value      |是|int|数量|

示例代码
```
	local widget = GUI:ParticleEffect_Create(GUI:Attach_LeftBottom(), "TT", 568, 320, "res/private/particles/petal_1.plist")
    GUI:ParticleEffect_setDuration(widget, -1)
    GUI:ParticleEffect_setTotalParticles(widget, 999)
```
# Spine动画(SpineAnim)


# 创建Spine动画
## SpineAnim_Create(parent, ID, x, y, jsonPath, atlasPath, trackIndex, name, loop)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|jsonPath   |是|string|json文件路径|
|atlasPath  |是|string|atlas文件路径|
|trackIndex |是|int|索引值|
|name       |是|string|动画名|
|loop       |是|boolean|动画是否循环|
- 示例代码
示例资源： [nandaoshi.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=09c2fd9bddb3643207257448ff81e6d7 "[nandaoshi.zip")

```
GUI:SpineAnim_Create(GUI:Attach_LeftBottom(), "Spine_1", 200, 100, "res/custom/nandaoshi/nandaoshi.json", "res/custom/nandaoshi/nandaoshi.atlas", 1, "animation", true)
```

# 拖拽控件(MoveWidget)


# 创建拖拽容器
## MoveWidget_Create(parent, ID, x, y, width, height, from, ext)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽|
|height     |是|int|高|
|from     	|是|int|控件来自(界面位置)  官方默认的可参照元变量 ITEMFROMUI_ENUM, <br>自定义类型的示例 : `SL:GetMetaValue("ITEMFROMUI_ENUM").xxx` <br>[xxx: 自定义类型名]|
|ext		|否|table|额外参数<br>beginMoveCB : 开始移动回调 <br>endMoveCB : 结束移动回调<br>cancelMoveCB : 取消移动回调 <br>equipPos: 放置装备的装备位置【来源 `SL:GetMetaValue("ITEMFROMUI_ENUM").PALYER_EQUIP` 时生效】<br>pcDoubleCB : pc双击回调 [3.40.8版本]<br> mouseScrollCB: 鼠标滚轮回调 [3.40.8版本]|

- 装备位30的装备拖动穿脱 的示例代码
```
		local bg = GUI:Image_Create(GUI:Attach_LeftBottom(), "bg_TT", 400, 300, "res/public/btn_npcsm_01.png")
		local function beginMoveCallBack(node)
			GUI:setVisible(node, false)
		end
		local function endMoveCallBack(node)
			GUI:setVisible(node, true)
		end
		local function cancelMoveCallBack(node)
			GUI:setVisible(node, true)
		end
		local moveWidget = GUI:MoveWidget_Create(bg, "moveWidget", 35, 35, 70, 70, SL:GetMetaValue("ITEMFROMUI_ENUM").PALYER_EQUIP, {equipPos = 30, beginMoveCB = beginMoveCallBack, cancelMoveCB = cancelMoveCallBack, endMoveCB = endMoveCallBack})
		local itemData = SL:GetMetaValue("EQUIP_DATA", 30)
		if itemData then
			local item = GUI:ItemShow_Create(moveWidget, "equipItem", 35, 35, {index = itemData.Index, itemData = itemData, look = true})
			GUI:ItemShow_setItemTouchSwallow(item, false)
			GUI:setAnchorPoint(item, 0.5, 0.5)
		end
		-- 穿戴触发
		local function takeOnEquip(data)
			if data.isSuccess and data.pos == 30 then
				GUI:removeAllChildren(moveWidget)
				GUI:setVisible(moveWidget, true)
				local itemData = SL:GetMetaValue("EQUIP_DATA", 30)
				if itemData then
					local item = GUI:ItemShow_Create(moveWidget, "equipItem", 35, 35, {index = itemData.Index, itemData=itemData, look = true})
					GUI:ItemShow_setItemTouchSwallow(item, false)
					GUI:setAnchorPoint(item, 0.5, 0.5)
				end
			end
		end
		-- 脱下触发
		local function takeOffEquip(data)
			if data.isSuccess and data.pos == 30 then
				GUI:removeAllChildren(moveWidget)
				GUI:setVisible(moveWidget, true)
			end
		end
		
		SL:RegisterLUAEvent(LUA_EVENT_TAKE_ON_EQUIP, "TESTMove", takeOnEquip)
		SL:RegisterLUAEvent(LUA_EVENT_TAKE_OFF_EQUIP, "TESTMove", takeOffEquip)
```

# 新增拖拽类型和拖拽事件
## AddMoveWidgetTypeEvent(fromType, toType, fromToEvent, toFromEvent)
|参数       |必选|类型|注释|
|:----      |:-|:--|:---|
|fromType   |是|string|控件来自位置类型名|
|toType     |是|string|控件到达位置类型名|
|fromToEvent|否|function|从fromType类型控件 拖拽到 toType类型控件 触发的函数|
|toFromEvent|否|function|从toType类型控件 拖拽到 fromType类型控件 触发的函数|
* fromToEvent/toFromEvent 起码实现一个.

- 示例代码
```
	--- 自新增移动类型 来自/去达
    local function fromToEvent(_, data)
        SL:PrintTable(data)
        SL:print("++++++FromToEvent  111 -> 222")
    end
    local function toFromEvent(_, data)
        SL:PrintTable(data)
        SL:print("++++++ToFromEvent  222 -> 111")
    end
    GUI:AddMoveWidgetTypeEvent("from", "to", fromToEvent, toFromEvent)
    local moveWidget11 = GUI:MoveWidget_Create(GUI:Attach_LeftBottom(), "moveWidget11", 500, 300, 70, 70, SL:GetMetaValue("ITEMFROMUI_ENUM").from, {cancelMoveCB = cancelMoveCallBack, endMoveCB = endMoveCallBack})
    local img = GUI:Image_Create(moveWidget11, "img", 0, 0, "res/public/word_fubentg_1.png")
    local tt11 = GUI:Text_Create(moveWidget11, "tt", 0, 35, 18, "#000000", "111")
    
    local moveWidget22 = GUI:MoveWidget_Create(GUI:Attach_LeftBottom(), "moveWidget22", 300, 300, 70, 70, SL:GetMetaValue("ITEMFROMUI_ENUM").to, {cancelMoveCB = cancelMoveCallBack, endMoveCB = endMoveCallBack})
    local img = GUI:Image_Create(moveWidget22, "img", 0, 0, "res/public/word_fubentg_2.png")
    local tt11 = GUI:Text_Create(moveWidget22, "tt", 0, 35, 18, "#000000", "222")
```


# 刮图 /  刮刮乐 (ScrapePic)


# 创建刮图
## ScrapePic_Create(parent, ID, x, y, showImg, maskImg, clearHei, moveTime, beginTime, callback)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|showImg    |是|string|展示图片资源|
|maskImg    |是|string|遮罩图片资源|
|clearHei 	|否|int|刮除高度, 默认16|
|moveTime	|是|int|刮除时间, 单位: 秒|
|beginTime  |否|int|开始点击到结束触发间隔, 单位: 秒|
- 示例代码

```
	-- 刮图两秒 自动展示
 	local TT = GUI:ScrapePic_Create(GUI:Attach_LeftBottom(), "ScrapePic", 250, 200, "res/public/word_fubentg_11.png", "res/public/mask_1.png", 18, 2, 5, function()
        SL:Print("刮图完毕|||")
  	end)
```


# TableView [3.40.2版本]


# 创建列表容器[优化加载]
## TableView_Create(parent, ID, x, y, width, height, direction, cellWid, cellHei, num)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|容器宽度|
|height     |是|int|容器高度|
|direction  |是|int|1：垂直; 2：水平|
|cellWid	|是|int|单个cell 宽|
|cellHei	|是|int|单个cell 高|
|num		|是|int|需创建cell个数|

# 设置子cell创建方法
## TableView_setCellCreateEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|func		|是|function|创建函数 传入参数(cell父节点, cell下标)|

# 设置滚动方向
## TableView_setDirection(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|value		|是|int|滚动方向 1：垂直; 2：水平|

# 设置背景颜色
## TableView_setBackGroundColor(widget, value)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|value		|是|string|十六进制颜色值 例: "#FFFFFF"|

# 设置内部区域偏移位置 [3.40.3版本]
## TableView_setContentOffset(widget, x, y)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|x			|是|int|偏移坐标X|
|y			|是|int|偏移坐标Y|

# 获取内部区域偏移位置 [3.40.3版本]
## TableView_getContentOffset(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|

# 添加点击cell事件
## TableView_addOnTouchedCellEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|func		|是|function|点击cell触发回调|

# 滚动到某cell位置
## TableView_scrollToCell(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|index		|是|int|对应cell下标|

# 添加容器滚动回调 [3.40.3版本]
## GUI:TableView_addOnScrollEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|func		|是|function|容器滚动回调函数 param1: TableView控件|

# 设置容器cell个数 [3.40.5版本]
## GUI:TableView_setTableViewCellsNumHandler(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|func		|是|int/function|cell总个数(int)/返回cell总个数的函数(func)|

# 加载容器所有列表数据 [3.40.5版本]
## GUI:TableView_reloadData(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
* 结合GUI:TableView_setTableViewCellsNumHandler方法 改变数据使用

# 添加容器鼠标滚动事件 [3.40.5版本]
## GUI:TableView_addMouseScrollEvent(widget, func)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableView对象|
|func		|否|function|鼠标滚动回调函数传参{widget = widget, x = 滚动坐标X, y = 滚动坐标Y} [不填采用官方默认添加滚动] |

# TableViewCell
# 获取容器cell的下标/序列号
## GUI:TableViewCell_getIdx(cell)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|tableViewCell对象|

* 示例代码
```
		local winWidth = 900
		local winHeight = 600
		local wnd = GUI:Win_Create("Win_1", 0, 0, winWidth, winHeight)
		
		local tableView = GUI:TableView_Create(wnd, "TABLEVIEW", 200, 100, 600, 400, 1, 600, 40, 200)
		GUI:TableView_setBackGroundColor(tableView, "#FFFFFF")
		GUI:TableView_setDirection(tableView, 2)
		-- 设置cell创建方法
		GUI:TableView_setCellCreateEvent(tableView, function(parent, idx, ID)
			if ID == "TABLEVIEW" then
				local panel = GUI:Layout_Create(parent, string.format("layout_%s", idx), 0, 0, 600, 40)
				local text = GUI:Text_Create(panel, "TEXT", 0, 20, 18, "#00FF00", "IDX----------------"..idx)
				GUI:setAnchorPoint(text, 0, 0.5)
			end
		end)
   		
		local function touchCellFunc(tv, cell)
			local idx = GUI:TableViewCell_getIdx(cell)
			local panel = GUI:getChildByID(cell, string.format("layout_%s", idx))
			GUI:Layout_setBackGroundColorType(panel, 1)
			GUI:Layout_setBackGroundColor(panel, "#00EEAA")
			if idx == 15 then
				GUI:TableView_scrollToCell(tv, 18)
			end
		end
		-- 添加cell点击事件
		GUI:TableView_addOnTouchedCellEvent( tableView, touchCellFunc )
		SL:ScheduleOnce(function ()
			GUI:TableView_scrollToCell(tableView, 6)
		end, 1/60)

	```


# 旋转容器(RotateView) [3.40.3版本]


# 创建旋转容器
## RotateView_Create(parent, ID, x, y, width, scrollGap, param)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|width      |是|int|宽度|
|height     |是|int|高度|
|scrollGap  |是|int|滑动间隙, 默认100|
|param      |是|table|子节点参数, 参考如下|

```
	列表各子节点参数 scale: 缩放大小 img: 图片路径 string node:自定义控件 (img和node不同时存在)
	{
		[1] = {scale = 0.4},
		[2] = {scale = 0.6},
		[3] = {scale = 0.8},
	}
```

# 添加子节点到旋转容器对应下标item
## RotateView_addChild(widget, value, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|旋转容器对象|
|value      |是|obj|控件对象|
|index      |是|int|对应下标|

# 获取对应下标item添加的子节点
## RotateView_getChildByIndex(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|旋转容器对象|
|index      |是|int|对应下标|

- 仅能获取RotateView_addChild方法添加的控件.

# 获取对应下标item
## RotateView_getItemByIndex(widget, index)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|旋转容器对象|
|index      |是|int|对应下标|

- 示例代码

```
	local param = {
		[1] = {scale = 0.4, img = "res/public/word_fubentg_1.png"},
		[2] = {scale = 0.6, img = "res/public/word_fubentg_2.png"},
		[3] = {scale = 0.8, img = "res/public/word_fubentg_3.png"},
		[4] = {scale = 1.0, img = "res/public/word_fubentg_4.png"},
		[5] = {scale = 0.8, img = "res/public/word_fubentg_5.png"},
		[6] = {scale = 0.6, img = "res/public/word_fubentg_6.png"},
		[7] = {scale = 0.4, img = "res/public/word_fubentg_7.png"},
	}
	local view = GUI:RotateView_Create(GUI:Attach_LeftBottom(), "rotateView_1", 500, 320, 1000, 500, 100, param)
	local item = GUI:RotateView_getItemByIndex(view, 3)
	local itemSize = GUI:getContentSize(item)
	local layout = GUI:Layout_Create(item, "clickLayout", 0, 0, itemSize.width, itemSize.height)
	GUI:setTouchEnabled(layout, true)
	GUI:setSwallowTouches(layout, false)
	GUI:addOnClickEvent(layout, function()
		SL:Print("Click item index 3 !")
		GUI:removeFromParent(view)
	end)
```

# 装备框(EquipShow)[3.40.6版本]


# 创建装备框
## GUI:EquipShow_Create(parent, ID, x, y, pos, isHero, data)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|parent     |是|obj|父节点对象|
|ID         |是|string|唯一ID|
|x          |是|int|位置 横坐标|
|y          |是|int|位置 纵坐标|
|pos    	|是|int|装备装戴位置|
|isHero		|否|boolean|是否英雄装备|
|data		|否|table|额外参数|
```
	额外参数 参考如下:
	{
		look  = true                  -- boolean 是否显示tips
		noMouseTips = true			-- boolean PC端鼠标移入不显示tips
		bgVisible = true              -- boolean 是否显示背景框
		movable = true				-- boolean 是否可拖动
		doubleTakeOff = true,		 -- boolean 能否双击穿戴
		lookPlayer = true,			-- boolean 查看他人数据
	}
```
示例 :
```
	local equipShow = GUI:EquipShow_Create(GUI:Attach_LeftBottom(), "equipShow1", 400, 300, 1, false, {bgVisible = true, look = true, doubleTakeOff = true})
	-- 装戴后自动刷新
    GUI:EquipShow_setAutoUpdate(equipShow)
```

# 设置装备框显示自动刷新
## GUI:EquipShow_setAutoUpdate(widget)
|参数        |必选|类型|注释|
|:----      |:-|:--|:---|
|widget     |是|obj|装备框对象|
# 介绍


- **功能：TXT部分功能界面使用编辑器创建，实现界面在前端管理**
- 优点：实现界面可视化管理；界面操作可能更流畅；主要针对不会Lua用户
- 所有的界面编辑都是可视化操作
- 新增编辑器快捷键F12
- 用法思路：
	1. 服务器变量通过M2 [其他设置] 推送到客户端
	2. 客户端通过可视化去填写服务器变量，达到自动生成代码的目的

- 变量类型
		  客户端格式     服务器变量类型			名字
		$(<H>, 变量名)   	HUMAN			HUMAN(私有变量)
		$(<G>, 变量名)   	GOLBAL			GOLBAL(全局变量)
		$(<U>, 变量名)   	GUILD			GUILD(行会变量)
		$(<N>, 变量名)   	NATION			NATION(国家变量)
		$(<O>, 变量名)   	其他类型		N1, T1, U3, S6, S$XXX, N$XXX
		$<T_变量名>   		 表   		^ index1, index2, ... ^
		$<V_变量名>   		 表   		{ conten1, conten2, ... }
		

------------
#### NPC面板

#### 普通面板
# TXT如何打开前端界面

- TXT打开前端界面

- 语法：`SENDCUSTMSG 9999 界面参数`

- 界面参数

|字段名字|必选|类型|描述|
|:----|-----|-----|
|GUI_ID     |否|string|界面唯一ID<br>`只有关闭所有界面时可以不传值`|
|exportID   |否|string|编辑器导出的文件名路径<br>`只有关闭所有界面时可以不传值`<br>`GUIExport文件里面路径`|
|page       |否|int   |多面板打开的页签ID<br>`默认打开第一个`|
|close      |否|bool  |是否关闭界面<br>`GUI_ID传值时只关闭当前`<br>`否则关闭所有`|
|showType   |否|int   |界面打开方式（1~6）|
|hideMain   |否|bool  |是否隐藏主界面|
|hideLast   |否|bool  |是否隐藏上一个界面|
|needVoice  |否|bool  |是否有音效|
|escClose   |否|bool  |是否按键盘ESC关闭界面|
|isRevmsg   |否|bool  |是否pc鼠标经过吞噬/触摸吞噬，默认true|
|npcID      |否|int   |绑定的NPCID|
|param		|否|int   |窗口创建层 0主界面层 1普通面板层 2通知层 默认1<br>[仅普通面板时 hideMain、hideLast、escClose参数生效]|

- 例子
		关闭所有界面
		SENDCUSTMSG 9999 {"close":"true"}
		
		只关闭当前界面
		SENDCUSTMSG 9999 {"close":"true","GUI_ID":"Npc界面"}
		
		打开界面
		-- "GUIExport/npcs/npc_1.lua"
		SENDCUSTMSG 9999 {"GUI_ID":"Npc界面","exportID":"npcs/npc_1"}
		
		界面更新
		SENDCUSTMSG 9999 {"GUI_ID":"Npc界面","exportID":"npcs/npc_1"}
		
		
`* 重复打开同一个界面被视为更新界面`


# 如何创建列表界面

*`注意：所有的列表和子控件的关联都是通过列表的子控件ID和子控件的组件ID属性来绑定的`

- 创建TableView（设置子控件ID是2）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=475bd57eaad0f0d7451dca48021bf1be)

	`属性说明`
		子控件ID: 加载到tableView的组件ID(子控件Layout组件ID)
		指定位置：打开时跳转到的子控件索引位置
		
- 创建子控件Layout（组件ID是2）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1932d5b2aed95e1d0c09d4a1a371eacb)

	*`注意：此处的子控件组ID是2， 作为TableView的子控件ID；此时就完成了列表和子空间的绑定`
	
- 同理创建子控件里面的列表容器（设置子控件ID是3）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4341f5cf2b8a0a422706920a2c9b6027)

- 同理创建子控件Item（设置子控件ID是3）
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=f22f96c50bac0271f42cd327e23d60e4)

- 保存

- 预览效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=bf4aaabfd0a5ccecb944b411eb3eaf46)
# 如何创建多行多列容器

#### 1.先创建一个【滚动容器】
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=3d9baba7e32adb93e539dfa158530654)

#### 2.设置【滚动容器】属性
	* 子控件数量：即创建多少个item对象
	* 子控件ID：对象item的组件ID（必填）
	* 增长方向：加载对象的方式（1, 2, 3）;可以自己尝试效果

#### 3.在创建一个【item对象】
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=68579c66ce6917d16928896285ced773)

	* 组件ID：对象item的ID， 唯一
	* 物品ID：此处要填table变量值

#### 4.保存

#### 5.预览效果
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4bf13c5bae57c24da5564f534e0d301f)


# 如何创建多面板界面



# 创建进度条

### 1. 编辑器添加【进度条】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=18327ae6a241520513b4fdd87e7184af)

##### 属性说明

- 当前值：当前进度的值
- 最大值：当前进度的最大值
- 动画帧率：大于0播放进度条动画，否则不播放
- 动画步长：每次增加的进度值
- 文本可见性：进度条上面的"30%"字样是否隐藏

### 3. 保存
# 创建复选框

### 1. 编辑器添加【复选框】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1c1dc768ad815b5f2d4c31e0f07c497e)

##### 属性说明

选中状态会通过用户填入的消息号的第三个参数通知M2，值0（非选中）；1（选中）

### 3. 保存
# 创建输入框


### 1. 编辑器添加【输入框】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9f7a03852c46ed32c1f1298f246ffe15)

##### 属性说明

- 加密：输入完是*号状态
- 关联ID：关联按钮时填值

### 3. 保存
# 创建按钮

### 1. 编辑器添加【按钮】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4358e3ae7cbf925c0560f17ee6605c97)
##### 属性说明

- 输入框组：需要关联的输入框的关联ID, 多个#分割；不关联输入框时无需填值

### 3. 保存
# 创建人物模型

### 1. 编辑器添加【人物模型】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=bcfa58d46c04f10462b2daa0effb9149)
##### 属性说明

- 属性输入支持服务器变量、客户端变量

### 3. 保存
# 创建物品框

### 1. 编辑器添加【物品框】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0df0cad0ec5d0f0dfe3960d0bc2848e2)
##### 属性说明

- 属性输入支持服务器变量、客户端变量
		例如数量：$(Z)，此时是客户端变量

### 3. 保存
# 创建滑动条

### 1. 编辑器添加【滑动条】组件
### 2. 设置属性
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=e2e8364c91efbc6fa4f861a933a1c16a)
##### 属性说明

- 属性输入支持服务器变量、客户端变量
- 文本组：关联的文本组件的关联ID， 滑动条需要配合文本时填值

### 3. 保存
# 滑动条+文本组合


### 1. 编辑器添加【滑动条】组件，添加【文本】组件
### 2. 设置属性
- 滑动条属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=229ffee9e58ff21025322b4b0e9021bd)
	
- 文本1属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2754025368fbb71ae831d7d0e75708f9)
- 文本2属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=33f16b4471b58cc7d58740bde963fa73)

		注意：此时文本的内容格式为中一定要有数字
		例如：xx123xx, 123xx, xx123, 123

### 3. 保存
# 输入框+按钮组合

### 1. 编辑器添加【滑动条】组件，添加【文本】组件
### 2. 设置属性
- 滑动条属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=8afbbaaab9148e1e88472279f2673448)
	
- 输入框1属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c3fbfc7ee09729e7a83bcf6fac5fb3e0)
- 输入框2属性设置
	![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=97c6eb60f7d4a2d729fcdcfe76d4d774)

### 3. 保存
# 更新日志

# 开发快捷键
CTRL+F3   游戏节点快速预览
CTRL+F4   预览模型特效
CTRL+F6   修改预览客户端表格
CTRL+F9   GUI编辑器 [ 可编辑GUIExport目录下UI文件 ]
CTRL+F10  自定义调整界面/内存监控/富文本调试
CTRL+F11  TXT编辑器
0         显示/隐藏地图阻挡格子
SHIFT+ESC 重启游戏

```
GUI编辑器内置快捷键 ：
	选中需要批量操作的控件 : 
	Ctrl + 1  上对齐
	Ctrl + 2  下对齐
	Ctrl + 3  左对齐
	Ctrl + 4  右对齐
	Ctrl + H  水平分布
	Ctrl + E  垂直分布
	打开文件夹资源选择 ：
	BACKSPACE  返回上一级文件夹
```
# 代码提示
VScode代码提示下载[24.03.01更新 ] [客户端3.40代码提示.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c7dd2f1e7fbc460450691b4190fbbeda "[客户端代码提示[24.0301].zip")

# 3.40.8 更新日志
 [-- 2024.5.24 更新]
 * F6新增txt界面字体文件配置、邮件内容富文本类型配置开关
 * 元变量新增玩家外观数据获取、英雄背包数据、背包位置获取物品唯一ID
 * 新增开关型技能开关触发事件
 * GUILayout/ItemTips 新套装无描述才不显示
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=8720ca0e78e531f4e2b2f87be301a34c) 英雄新增BUFF界面、Tips支持属性显示
 * GUILayout/Stall 修复摆摊切换他人摊位名字不刷新
 * 数字滚动动画 支持艺术字 TextAtlas
 * GUI新增获取容器背景图片方法、缩放动作支持单独缩放xy
 * GUILayout/Chat 聊天页掉落频道优化显示方式
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=af0c1168d7f52b49d1e9fe85772ecaac) 修复方法使用
 * GUILayout/AuctionPutList 拍卖行上下架道具刷新右侧显示
 * GUILayout/GUIFunction 额外自动拾取判断方法补充字段
 * 角色时装页分离装备则模型上不显示
 * GUILayout/ItemTips 处理装备数据获取问题
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=bc249403017bd72d0cf444efccbc95c6)  角色装备页开源(自己、他人、交易行)
 * 新增上下马事件、骑马状态元变量
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c7f797abed98977afb363645cd43ee0d) 英雄装备页开源(自己、他人、交易行)
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2d4fc351ca9f375183bd1ca2533fd8dc) 原控制显示自定义属性名称改成全使用自定义属性配置
 * GUILayout/MainAssist、MainAssist_win32 处理任务栏置顶特效问题
 * 英雄查看他人装备面板挂接点id改 53003
 * GUILayout/NPCSellRepaire 区分手机端PC端界面UI
 * GUILayout/Rank、Rank_win32 处理排行榜请求数据问题
 * GUILayout/BagItemText 背包item数量显示规则同步常规item
 * GUILayout/MainMiniMap 处理主界面地图攻击模式按钮切换1像素误差

 [-- 2024.5.27 更新]
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6ab6735bc40462c279c988a2f99040b2) 装备界面处理

 [-- 2024.5.31 更新]
 * GUILayout/GUIFunction 自动穿戴装备位检测判断禁止左手镯穿戴物品规则
 
 [-- 2024.6.4 更新]
 * ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a8ae7454a95093d54dd7e50724667634) 装备界面内容加载改在F10自定义内容之后 、修复查看他人套装数据显示问题
 * GUILayout/GUIDefine.lua 新增两个属性
 * GUILayout/Notice.lua 物品提示适配刘海屏
 
 
 
# 3.40.7 更新日志
 [-- 2024.3.14 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=fd57f1866c382b622f404c1f580b69af)
 ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1c72b4771ad81b65b34edc18d4fa521f)
 ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=758d1865a2488751b9925769362bec5f) 新增跨服频道、假掉落显示
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=91a6338dde9a1bf399d093b4539bef35) 加黑名单、好友输入框限制长度改为1000
* GUILayout/GoldBox 修复错误
* GUILayout/GUIDefine、GUIFunction 开放自动使用比对方法、PC英雄切换锁定目标触发方法
* GUILayout/ItemTips、GUIFunction 新套装单件不显示改作无描述不显示、 映射属性新增参数使用自定义属性名称
* GUILayout/MainBuffList BUFF图标收缩按钮问题修复
* GUILayout/MainSkill 开放英雄锁定相关
* GUILayout/SettingLaunch、SettingLaunch_win32 新增自动狮子吼
* F6 新增开宝箱特效配置
* F6 新增cfg_buff的offsetx和offsety参数支持骑马位置和显示的编辑
* F6 飘血支持类型4的编辑
* 新增元变量 单个actor挂接点 `"ACTOR_MOUNT_NODE"`
[-- 2024.3.18 更新]
* GUILayout/ItemTips 装备Tips新增附加属性显示方式
* GUILayout/PlayerBuff、PlayerBuff_Look 修复Buff页报错
* GUILayout/CompoundItem 处理合成道具装备特效显示问题
[-- 2024.3.20 更新]
* GUILayout/ItemTips 映射属性的自定义描述显示
* GUILayout/GUIFunction 新增额外判断物品自动拾取方法
* F6 支持cfg_magicinfo 内功相关配置
* GUILayout/MainSkill_win32 开放PC技能图标主界面显示
[-- 2024.4.10 更新]
* GUILayout/GUIFunction 人形怪补上挖肉不可挖判断
[-- 2024.4.15 更新]
* GUILayout/GUIFunction 中毒恢复属性十分比
* GUILayout/PurchasePutIn 修复求购放入再次打开列表无显示

# 3.40.6 更新日志
 [-- 2024.1.19 更新]
* GUILayout/MainBuffList 主界面buff图标刷新调整
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=29b4eb75174e0e74445a0b2ed0156b8f) 调整一个方法名

* GUILayout/GuildList 修复已加入行会才显示宣战/结盟描述
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6cea4456a1af80da281cd1e5287505f7) 人物界面添加buff栏

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=376cfdf525285d8ce826e3e6cda44ebb) 修复时装界面按钮条件无效

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=78176e80870b9012d0df6b7aff97a402) 通用弹窗新增复选框
* GUILayout/MainProperty 修复优化
* GUILayout/AuctionBid 竞拍界面限制最大/最小竞拍价输入
* GUILayout/GoldBox、TreasureBox 宝箱新增音效
* 修复提升列表打开状态的刷新问题
* 处理PC设置页签跳转错误
* 处理通用描述Tips打开后右键无效
* 技能声音配置支持按规则区分男女
* 修复SL注册鼠标事件报错
* F6 界面设置保存修复、支持配置PC端地图中心点偏移
* F9 新增自定义装备框、修复道具框tips勾选无效问题
* 行会战颜色 按新规则调整
[-- 2024.1.29 更新]
* GUILayout/CompoundItem 优化合成关闭、红点刷新事件
* 新增按红点表配置增删红点事件
* 新增道具飞入指定按钮完触发事件
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=e1a4296cf3cc0bdc1dd072744ff477a0) 改 默认不显示人物面板buff/天赋按钮

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c362b270c48e8a1cfa4e2258e83321c0)  去掉GUI:Clone方法的使用 、主界面小地图模式切换新增师徒模式
[-- 2024.1.31 更新]
* GUILayout/AuctionPutList 拍卖行寄售道具列表不再实时刷新、点击判断道具是否存在背包
[-- 2024.2.19 更新]
* GUILayout/AuctionPutList、AuctionBidding、AuctionWorld 拍卖行小时数显示、放入也判断是否快捷栏存在
* GUILayout/GUIFunction 方法新增参数
[-- 2024.2.20 更新]
* GUILayout/MainMiniMap 修复切换地图同下标备注不刷新问题
* GUILayout/ItemTips 修复装备对比时装备名可能被按钮遮挡问题
[-- 2024.2.26 更新]
* GUILayout/NearPlayer 修复附近界面不显示玩家
[-- 2024.3.27 更新]
* GUILayout/ItemTips 新套装单件不显示改成无描述不显示
[-- 2024.4.15 更新]
* GUILayout/GUIFunction 中毒恢复属性十分比
* GUILayout/PurchasePutIn 修复求购放入再次打开列表无显示

# 3.40.5 更新日志
* GUILayout/MainProperty_win32 开放调整PC属性栏切频道名显示
* GUILayout/MainMiniMap、MiniMap F6 map配置可清空NPC名字
* GUI新增移除容器背景图片方法
* GUILayout/MainBuffList 开放配置buff显示内容, F6 新增配置buff收缩按钮、自动行排列 
* 新增元变量PC持续攻击目标 ：SELECT_SHIFT_ATTACK_ID 
* SL新增Actor添加删除特效接口
* GUILayout/PlayerSkillSetting_win32 修复PC技能设置页名字显示
* GUILayout/GUIFunction、ItemTips  新增TIPS 自定义属性映射显示
* GUIExport/set/setting_frame_win32 修复PC设置窗口名错误
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2644546b25ce9d47da09258bc8e8f816) 修复英雄技能、连击技能强化技能图标设置无效
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4a95995832a439233111aae365b7ceb0) 新增多职业 相关调整内容
* GUILayout/PlayerEquip_Look_win32、HeroEquip_Look_win32 PC查看他人首饰盒tips显示改
* GUILayout/GUIDefine、GUIFunction 多职业新增属性及显示

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2ea204c8b014b084cc69ec85450abcbc) 属性栏支持根据对应职业显示属性
* GUILayout/AuctionWorld 拍卖行筛选弹出列表最多显示条数调整

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=40e792db002a5fa3e9dc27b712a66250) 聊天新增掉落频道、可分组屏蔽
* GUILayout/SettingLaunch、SettingLaunch_win32 设置 自定义技能的内挂配置支持显示
[-- 2023.12.13 更新]
* GUILayout/LoginRolePanel 修复创角多职业切换性别模型不切换
* GUILayout/ItemTips 支持Tips附加属性按复古极品显示
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=54bbc3ccbc69fee344b0741eddabaad2) 配置人物内观剑甲分离字段
* GUI TableView新增鼠标滚轮事件、设置数量方法
* GUILayout/MainBuffList 新增buff图标排序
[-- 2023.12.18 更新]
* GUILayout/Notice 滚动通知初始位置调整, 避免闪
[-- 2023.12.20 更新]
* GUILayout/PurchasePutIn、PurchaseWorld 处理求购未配置二级菜单显示
[-- 2023.12.22 更新]
* GUILayout/AuctionBidding、AuctionPutList、AuctionWorld 拍卖物品名颜色优先使用真实颜色
[-- 2024.1.2 更新]
* GUILayout/MainMiniMap 修复主界面小地图传送点图片显示偏移
[-- 2024.1.4 更新]
* GUILayout/GuildAllyApply 修复行会结盟申请关闭未注销事件导致崩溃问题
[-- 2024.1.16 更新]
* GUILayout/StoreRecharge 处理充值换行显示问题
[-- 2024.1.26 更新]
* GUILayout/MainBuffList buff图标刷新优化
[-- 2024.2.20 更新]
* GUILayout/MainMiniMap 修复切换地图同下标备注不刷新问题
[-- 2024.2.26 更新]
* GUILayout/NearPlayer 修复附近界面不显示玩家
[-- 2024.3.27 更新]
* GUILayout/ItemTips 新套装单件不显示改成无描述不显示
[-- 2024.4.15 更新]
* GUILayout/GUIFunction 中毒恢复属性十分比
* GUILayout/PurchasePutIn 修复求购放入再次打开列表无显示

# 3.40.4 更新日志
* GUILayout最新版本下载 --> [客户端资源](http://engine-doc.996m2.com/web/#/22/159 "客户端资源")
* Tips相关界面统一输入监听关闭
* GUI:ScrollText控件 支持滚动时间参数设置
* 新增可配置物品拾取条件 - 不被小精灵自动拾取开关
* 优化GUI自动刷新元变量处理
* 新增GUI:Attach_ActorNode() ACTOR挂接节点
* 摆摊摊位名字字号使用场景字号
* GUILayout/PlayDice 摇骰子界面开放
* 修复拒收私聊和黑名单内的弹气泡提示
* 新增地图添加特效方法
* 引导界面打开时不再响应键盘、吞噬鼠标事件
* GUILayout/SettingLaunch、SettingLaunch_win32 新的智能召唤
* GUI:ItemBox组件 新增刷新内容接口
* GUILayout/SettingHelp_win32 帮助文本可自行配置
* GUILayout/SettingSkillPanel 挂机设置技能时判断是否主动技能
* GUILayout/ReinAttr 新版属性加点 更新F9 -> ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a925eac9d75dc486474e344c30c70650)目录
* GUILayout/CompoundItem 合成 优化处理
* GUILayout/BeStrongUp 修复提升按钮单个移除报错
[-- 2023.11.7 更新]
* **！更新版UI资源, GUIExport里主界面属性栏、外框相关ui文件有所调整。** 如需换为上一版, 下载[老资源](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9b40c63e9c9445e1e56b9f19375f5f01 "老资源")处理还原
* GUILayout/ReinAttr 修复新版属性加点 属性值显示错误
* GUILayout/AuctionWorld、StorePage 微调整代码
[-- 2023.11.9 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b990ef91bd69933c01cbd5de1a190a23)查看他人时装 支持分离头盔斗笠、剑甲装备
同时, GUIExport内ui文件有新增调整, 改动文件下载 ->[GUIExport.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d85e77df125bffcf439a68f07d4cf3dd "[GUIExport.zip")
* GUIExport/GUIFunction 加容错属性名缺失
[-- 2023.11.10 更新]
* GUILayout/ReinAttr 新版属性加点显示再修复
* GUILayout/MainMiniMap 主界面小地图传送点展示部分开放
[-- 2024.1.2 更新]
* GUILayout/MainMiniMap 修复主界面小地图传送点图片显示偏移
[-- 2024.1.4 更新]
* GUILayout/GuildAllyApply 修复行会结盟申请关闭未注销事件导致崩溃问题
[-- 2024.1.16 更新]
* GUILayout/StoreRecharge 处理充值换行显示问题
[-- 2024.2.20 更新]
* GUILayout/MainMiniMap 修复切换地图同下标备注不刷新问题
[-- 2024.3.27 更新]
* GUILayout/ItemTips 新套装单件不显示改成无描述不显示
[-- 2024.4.15 更新]
* GUILayout/GUIFunction 中毒恢复属性十分比

# 3.40.3 更新日志
* GUILayout最新版本下载 --> [客户端资源](http://engine-doc.996m2.com/web/#/22/159 "客户端资源")
* GUILayout/ ProgressBar(NPC进度条)、 CommonTipsPop(通用提示) 开放, 可自行调整文本大小
* GUI控件支持不传入父节点, 参数传入-1即可
* 新增开放旋转容器 UIRotateView
* CTRL + F7 新增颜色编辑器, 可新增超出0-255的颜色值供使用
* 原始富文本支持十六进制颜色值, 例: <RText/FCOLOR=255><RText/FCOLOR=#ff0000>
* 合成界面逻辑开放 GUILayout/CompoundItem
* 聊天解析逻辑更多开放、聊天前缀显示修复, 参照GUIFunction内方法 
* 新增主玩家/网络玩家/NPC进/出视野、死亡、复活等事件
* 新增GM自定义数据相关元变量和事件
* 优化玩家变性、转职的刷新
* 交易行相关UI[ 除去交易行角色外框界面 ]不再开放编辑
* 内挂新增屏蔽摆摊
* GUILayout/StoreRecharge 充值代码开源
* GUILayout/StorePage、StoreDetail 商城、商场购买弹框开源代码
* GUILayout/Bag、Storage 大背包大仓库调整
* GUILayout/ItemTips 调整可显示多件对比装备、新老套装件数为1时不显示
* GUILayout/BagItemText 背包数字显示拆分出PC的UI文件 bag_item_num_win32
* GUILayout/NearPlayer 附近界面开放代码 
* GUILayout/MainAssist 导航栏cell展示开放
* GUILayout/StallPut 摆摊放入页加传参
* GUILayout/AutoUsePop 自动使用框UI结构调整
* GUILayout/Item 修复物品调用更新接口偶发空icon问题
* GUILayout/MainProperty、MainProperty_win32 新增获取聊天栏宽方法
* GUILayout相关装备文件 创建装备回调方法[CreateEquipItemCallBack]、 创建人物模型回调方法[CreateModelCallBack]新增传参第二个参数为创建时使用数据, 可自行取用
* GUILayout/MainSkill 优化适应技能栏坐标调整
* GUILayout/BagItem、BagItemEffect、BagItemText、Item 调整透明度跟随设置
[-- 2023.9.4 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d68fbb47fb3c564022193aafa7a40ea6) 装备默认剑甲分离装备位换为 1000、1001
* GUILayout/StoreDetail 商城显示简化数字、修复叠加物品bug
[-- 2023.9.5 更新]
* GUILayout/Chat、ChatExtend 聊天、聊天拓展开放更多内容
[-- 2023 9.8 更新]
* F10 恢复TXT按钮位置工具
* 修复主界面小地图点的显示
* GUILayout/GoldBox 、TreasureBox 开宝箱相关内容开放
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=e10f6d3883a8d6104f1b187521bc7579) 优化内功系统技能列表加载
[-- 2023 9.11 更新]
* GUILayout/AuctionBidding 我的竞拍代码开源
[-- 2023 9.12 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1a6ea2e686203bbbceb4f04175d2dd2f) 修复内功相关技能刷新问题
* GUILayout/Chat 修复关闭按钮失效
[-- 2023 9.13 更新]
* GUILayout/ItemTips 调整显示
* GUILayout/AuctionBidding 修改请求方法名
* GUILayout/StorePage 商城数字简化
[-- 2023 9.14 更新]
* GUILayout/AuctionPutList、AuctionWorld、AuctionBidding 拍卖行更多开放源码
* GUIFunction 新增通用拍卖行相关方法
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=89b3625fa14f3034102736ab4af51545) 调整道具名称字体大小、不再逻辑代码设置 
[--2023 9.15 更新]
* GUILayout/MainNear 新增开放内容
[--2023 9.18 更新]
* GUILayout/StorePage ! 还原SL:OpenStoreDetailUI方法使用
* GUILayout/GUIFunction ! 新增主玩家手动移动触发方法
[--2023 9.19 更新]
* GUILayout/MainProperty 微调整底部条位置适配
[--2023 9.19 更新]
* GUILayout/StoreDetail 商城简化数字bug修复
* GUILayout/ItemTips 处理Tips部分文本未同步字体
[--2023. 9.22 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a186d1e2e88d2897b1639ec1946cafed) 人物属性栏自定义标题变量调整
[--2023. 9.26更新]
* GUILayout/StoreRecharge 充值配置[客户端可输入]最大最小金额
[--2023. 10.07更新]
* GUILayout/Notice 处理屏幕滚动文字提示显示问题
[--2023. 10.18更新]
* GUILayout/MainTop 修复顶部栏电量刷新问题
[-- 2024.1.4 更新]
* GUILayout/GuildAllyApply 修复行会结盟申请关闭未注销事件导致崩溃问题

# 3.40.2 更新日志
* [2023.9.18 更新] [GUILayout_3.40.2.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9e7910770a08044098dfb300c35a4d59 "[GUILayout_3.40.2.zip")
* 元变量增加，增加ACTOR大量元变量
* SL增加方法，地图坐标和世界坐标转换
* GUI增加 GUI:Attach_SceneF() 获取上层场景挂接点，GUI:Attach_SceneB() 获取下层挂接点
* 增加获取视野内NPC元变量 FIND_IN_VIEW_NPC_LIST
* 增加获取视野内玩家元变量 FIND_IN_VIEW_PLAYER_LIST
* 增加获取是业内怪物元变量 FIND_IN_VIEW_MONSTER_LIST
* 增加获取当前对话NPC id和index， CURRENT_TALK_NPC_ID、CURRENT_TALK_NPC_TYPEINDEX
* 增加NPC对话事件 LUA_EVENT_NPC_TALK
* 增加主玩家动作事件，动作开始 LUA_EVENT_PLAYER_ACTION_BEGIN，动作结束 LUA_EVENT_PLAYER_ACTION_COMPLETE
* 增加网络玩家动作事件，动作开始LUA_EVENT_NET_PLAYER_ACTION_BEGIN，动作结束LUA_EVENT_NET_PLAYER_ACTION_COMPLETE
* 增加怪物动作事件，动作开始LUA_EVENT_MONSTER_ACTION_BEGIN，动作结束LUA_EVENT_MONSTER_ACTION_COMPLETE
* 开放登录账号和开门动画GUI编辑
* GUI支持TableView
* GUILayout/MiniMap小地图界面逻辑开放，新增小地图相关元变量、方法和事件 [删除GUILayout/MiniMap_win32]
* GUILayout/SettingProtect、SettingProtect_win32 内挂保护新增复活保护开关
* 新增交易行开启状态元变量 TRADINGBANK_OPENSTATUS
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=35f3765a6e2cc824faddb754e53c9538) 设置相关的UI适配
* GUILayout/BeStrongUp 宠物存活元变量key换PET_ALIVE
* GUILayout/MainAssist 修复未展开任务栏时引导的位置偏移、补全收缩任务栏的引导事件触发
* 修复行会战 PC鼠标点击颜色显示问题
* F9编辑器节点树增加鼠标滚轮
* GUILayout/LoginRolePanel 删除角色部分处理、创角新增配置默认职业
* GUILayout/StorePage 设置商城标题字体大小
* GUILayout/MainMonster 大血条的怪物等级刷新
* GUILayout/MainProperty、MainProperty_win32 快捷栏个数采用元变量
* GUILayout/Bag 背包优化 分层处理
* GUILayout/GUIEquipComparison 开放装备比较方法
* GUILayout/Storage 仓库可配置使用大仓库
* 登录页GUI开放 GUILayout/LoginAccount、GUILayout/LoginServer
* GUILayout/GUIShare 新增装备位置类型
* GUILayout/ItemTips 新增内功技能书等级条件
* 新增内功系统
[-- 6.29 更新]
* GUILayout/GuildList 行会列表加载处理
* SL新增物品使用、装备穿戴/脱下等方法
* GUILayout/GUIFunction 挖肉逻辑开放
* 删除GUILayout/GUIShare、增加GUIDefine, 常用方法放置GUIFunction, 如装备对比、目标是否可挖肉、掉落物能否捡取. 基于此以下文件有改动 :
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=6f73c667b3d07305f22e8a97ced5d3cc)
* GUILayout/MiniMap 修复小地图倒计时显示
[-- 6.30 更新]
* GUILayout/HeroSuperEquip 、HeroSuperEquip_win32 修复英雄时装外显无效
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=41b2819f3614ae51a9bb3c2d27165a7d) 修复英雄和人物自定义属性刷新
* GUILayout/Notice 消息模块开放 新增相关事件
* GUILayout/BagItem 修复背包item锁未设置偏移缩放
* GUILayout/Bag PC背包加金币数量刷新且默认不显示
* GUILayout/MiniMap 小地图NPC图标位置调整
* GUILayout/Bag 修复背包锁显示问题
[-- 7.3 更新]
* GUILayout/HeroState 、GUIExport/hero/hero_state_node 修主界面部分区域不可右键跑
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=05ec6cc92c9a06283b320d75cf84f387) 人物英雄的头盔斗笠分离增加选项 内观模型是否显示头盔斗笠
* GUILayout/Notice 修复bug
* GUILayout/BagItemEffect 修复背包聚灵珠显示
[-- 7.4 更新]
* GUILayout/Notice 新增内功经验飘字、代码优化、普通提示位置调整
* GUILayout/BagItem、Item 代码优化
* GUILayout/MiniMap 修复问题、代码优化
* GUILayout/AuctionPutin PC字体大小调整
* SL新增与移动端交互相关操作，例如: 加Q群等
[-- 7.5 更新]
* GUILayout/SettingLaunch、SettingLaunch_win32 微调
* GUILayout/BagItem 背包item没找到图用透明图
* GUILayout/GuildEditTitle 行会编辑敏感字处理
* GUILayout/GUIFunction 开源聊天解析部分接口
* 新增元变量合服天数、时间戳
[-- 7.6 更新]
* GUILayout/MiniMap PC小地图支持拖拽
* GUILayout/AuctionTimeout 修复拍卖行重新上架无效、上架输入数量字体缺失
* GUILayout/SettingLaunch、SettingLaunch_win32 内挂新增新技能开关
* GUILayout/LoginRolePanel 单职业/随机职业、单性别/随机性别等配置支持0/1
[-- 7.7 更新]
* GUILayout/MiniMap 小地图部分节点改在此创建
* GUILayout/Bag 背包页签处理
* GUILayout/HeroState 容错处理
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=96c4d4397d7479b41e3a10f238bbbe54) 调整一些Color设置
[-- 7.10 更新]
* GUILayout/MainSkill 109按钮模块引导优化
* GUILayout/UIModel 修复装备内功特效添加多个
* GUILayout/BagItemText 背包item字体改黑体
* GUILayout/Notice 修复可配置XY倒计时提示[脚本命令: SENDDELAYMSG]
* GUILayout/ItemTips 修复Tips自定义固定路径图片生效
[-- 7.11 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7ccdeefe164b4d6d92c53c900289a8cc) 去除不再自动调整装备位位置
* GUILayout/BagItemText 背包字体调整
* GUILayout/ItemTips 顶部框体特效位置设置改
* GUILayout/AuctionMain 修复隐藏行会拍卖崩溃
* GUILayout/MergePlayerFrame 修复二合一面板角色名刷新
[-- 7.12 更新]
* GUILayout/UIModel 法阵特效修复 [UpdateEquipEffect命令]
* GUILayout/StorePage 修复商店多个同ID物品不显示、货币刷新问题
* 新增BUFF相关元变量、跨服和快捷栏数据改变事件
* 修复小地图残留的怪物红点
* 修复背包不可穿戴红色遮罩显示问题
* 修复BUFF变色问题
* 修复F10编辑过程中触发快捷栏导致的崩溃
* 修复PC端怪物死亡时可能存在血量依旧显示问题
* 删除TEST敏感字
[-- 7.13 更新]
* 小精灵不拾取金币修复
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7702dd9feb04ab1494e3fef285009f01) 内功各面板支持挂接和跳转
* F6新增一些gane_data表配置
* 新增离开游戏世界事件
* GUILayout/Storage 修复大仓库页签问题
[-- 7.14 更新]
* GUILayout/Storage 修复大仓库显示问题
* 新增进入游戏世界事件、修改PC分辨率元变量
* 背包移入边缘不显示Tips问题修复
* GUILayout/BagItem 修复背包物品移动中取消bug
* GUILayout/ItemTips 处理按钮显示适配
[-- 7.17 更新]
* GUILayout/MainTarget PC默认不显示目标栏
* GUILayout/PlayerSkillSetting 修复技能设置页再次打开无选择特效显示
* GUILayout/PlayerFrame、PlayerFrame_win32、HeroFrame、HeroFrame_win32 修复内功/基础切换问题
* GUILayout/MiniMap 修复PC小地图右击穿透问题
* GUILayout/BagItem 修复背包物品图标显示
* GUILayout/SettingLaunch、SettingLaunch_win32 拾取设置改为配置ID 121
[-- 7.18 更新]
* GUILayout/MiniMap 小地图修复
* 新增发送普通聊天、打开/关闭快捷使用框方法
* GUILayout/BagItem、BagItemEffect、BagItemText 背包物品相关处理
[-- 7.19 更新]
* 主界面小地图支持点击打开/关闭
* GUILayout/MiniMap 小地图长按传送
* GUILayout/Item、BagItemText 星级显示相关修复
* GUILayout/BeStrongUp 提升按钮监听
* GUILayout/MainTarget 调整目标栏PC端位置和显示
* GUILayout/PlayerInternalMeridian 修复内功经脉界面穴位点击不显示Tips
* GUILayout/MainProperty_win32 处理PC属性栏不对等的自适应偏移
[-- 7.20 更新]
* GUILayout/MainProperty_win32 修复PC属性栏等级Tips显示错误
* GUILayout/Item、BagItemText 修复不显示星级参数
* 新增game_data内字段disable_footprint_effect 可屏蔽官方自带足迹, 配置1为屏蔽
[-- 7.24 更新]
* GUILayout/MainTarget 选中目标血条显示节点修改
* GUILayout/Mail 邮件问题处理优化
[-- 7.25 更新]
* GUILayout/FriendApply 好友申请优化
* GUILayout/TeamApply 队伍申请修复
[-- 7.26 更新]
* GUILayout/Item 加单独缩放参数
[-- 7.27 更新]
* GUILayout/GUIFunction 修复聊天解析私聊名字显示问题
[-- 7.28 更新]
* GUILayout/MiniMap 支持cfg_mapdesc的nColor为十六进制颜色值
* GUILayout/MainAssist_win32 修复PC任务栏收缩时引导显示
[-- 7.31 更新]
* GUILayout/MainAssist_win32 修复PC任务栏切换 英雄状态面板跟随变化参数无效
[-- 8.1 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d30783c2bdedc4278f2f1dde906c2f2d) 新增英雄/人物内功/连击技能刷新
[-- 9.12 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=842d36941a19b21f885b1135f60314d5) 修复称号切换无效
[-- 9.18 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=851d86711bff033ab0761bba47b1629d) 修复属性配置不显示
[-- 10.18 更新]
* GUILayout/MainTop 修复顶部栏电量刷新问题
[-- 2024.1.4 更新]
* GUILayout/GuildAllyApply 修复行会结盟申请关闭未注销事件导致崩溃问题

# 3.40.1 更新日志 (需下载最新工具服)
* GUILayout下载[ 7.24更新 ] [GUILayout_3.40.1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1d7e4d0395b74c703bb65d8372f82227 "[GUILayout_3.40.1.zip")
* 3.40.1的全局GUI 不等同 老版本GUI  !! 老版本直接转新框架 建议直接替换代码 GUI: --> ssr.GUI: 使用
* 删除配置表 cfg_chat_face, cfg_tipicon, cfg_colour_style, cfg_colour_style_win32, cfg_newsetup, 大部分配置表都将可视化配置
* 条件系统调整，1000010格式改为 $(LEVEL) >= 10 等
* 自定义UI编辑模式调整, CTRL + F9 直接编辑对应界面文件
* 删除老内挂, 新内挂直接使用 cfg_newsetup表改名为cfg_setup表配置! 
* 开放绝大多数界面和逻辑可供自由改动, 在元变量中几乎能找到所有所需变量
* 手机端界面改用加黑幕点空白区域关闭方式, PC端维持原状
* cfg_menulayer表配置改动, 不再控制页签名称和排序, 使用condition字段作为界面页签点击能否打开条件
* 字体采用思源黑体, PC端默认宋体
* 颜色只保留0-255
* 统一多面板去除, 每个面板有单独外框分别进行调整
* GUILayout增加MiniMap逻辑开源，小地图默认增加外框
* GUILayout增加内观模型UIModel代码开源
* 新增元变量SERVER_VALUE 可获取服务端下发的变量
[-- 5.18 更新]
* GUILayout/LoginRolePanel 角色页崩溃修复
* GUILayout/ItemTips 解决套装表读颜色问题
* GUILayout/StoreRecharge 充值名字展示使用登录角色名
* GUILayout/Mail 邮件 处理一些界面BUG
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=975d1549d872b3e0baad1ffea789c53f) 设置-BOSS提醒 按钮按下效果和编辑重名时优化
* GUILayout/Bag 修复PC大背包显示问题
* GUILayout/UIModel 修复feature为空table时无法创建空裸模的问题
[-- 5.22 更新]
* GUILayout/MainMiniMap_win32 修复PC小地图点击切换透明度
* GUILayout/PlayerFrame_win32 修复PC角色外框点击玩家名字
* GUIExport/hero_look_tradingbank文件夹 交易行英雄UI独立出来一份
[-- 5.24 更新]
* GUILayout/FuncDock 内容开放 新增行会/组队/好友/交易相关方法和元变量
* GUILayout/ItemTips 解决部分报错问题
* GUILayout/GuildCreate 行会创建界面适配
[-- 5.25 更新]
* 新增当前地图相关元变量
* GUILayout/MainMiniMap_win32 PC主界面小地图开放鼠标/键盘事件 新增相关元变量
* GUILayout/MainNearPanel 附近列表页开放Y坐标可调
* GUILayout/ItemTips 镶嵌宝石显示调
* GUILayout/BeStrongUp 提升按钮/气泡开放
* ！重要更新，PC默认还原为黑体，需要使用宋体请自行下载[font4.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=59ba9874828085fb6069304e4ffa2b9d "[font4.zip")放入dev/fonts/font4.ttf
* GUILayout/Rank_win32 数据为空时报错修复
[-- 5.31 更新]
* GUI刮图组件  txt: <ScrapePic> 刮图标签
* GUILayout/HeroEquip_win32 , PlayerEquip_win32 首饰盒提示调整
* M2 cfg_magic表delay字段生效，不使用该字段需要配置为0。刺杀无法打出是该问题导致
[-- 2023.06.07]
* 聊天手机端可使用其他字体，配置gamedata字段 CHAT_FONT_PATH_MOBILE. 例fonts/font.ttf
* 修复提升按钮F10自定义编辑
[-- 6.12 更新]
* GUILayout/MainSkill 修复拾取按钮功能
* GUILayout/Item 修复ItemShow显示问题
[-- 6.16 更新]
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ae2ef30ba3ccb5b2f99c97dd59da64f5) 修复PC装备页-首饰盒隐藏仍显示鼠标Tips问题
[-- 6.25 更新]
* GUILayout/HeroBaseAtt、HeroBaseAtt_Look_TradingBank、HeroBaseAtt_win32、PlayerBaseAtt_Look_TradingBank 修复等级属性不显示转生等级
* GUILayout/SettingBasic 、GUILayout/SettingBasic_win32 修复高帧率模式
* GUIExport/minimap/mini_map 导出文件改
[-- 6.27 更新]

* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ccffbcf2c4a3da3623cd7b57e588cff2)
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9dab78734c88ee3dc30eb45ebaaec65b)
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=96a6cbb773d1a43bdfcdf789d629c0ac)  时装修复服务端开关 正式服无效（仅第一次成功隐藏）的问题
[-- 6.28 更新]
* GUILayout/ItemTips 修复限时倒计时读取数据错误问题
* GUILayout/Item、GUIShare 修复检测能否穿戴方法的使用
* GUILayout/MainProperty_win32 修复魔血球动画资源使用路径错误
[-- 6.30 更新]
* GUILayout/HeroSuperEquip 、HeroSuperEquip_win32 修复英雄时装外显无效
* ![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=41b2819f3614ae51a9bb3c2d27165a7d) 修复英雄和人物自定义属性刷新
[-- 7.3 更新]
* F6 内挂-平滑模式可视
[-- 7.12 更新]
* GUILayout/MainAssist、GUILayout/MainSkill 110任务栏、109按钮模块的引导修复/优化
* 修复任务栏和小地图收缩的跳转
[-- 7.13 更新]
* GUILayout/GuildList 行会列表滑动处理
[-- 7.17 更新]
* GUILayout/PlayerSkillSetting 修复技能设置页再次打开无选择特效显示
* GUILayout/PlayerExtraAtt 背包负重刷新
[-- 7.20 更新]
* GUILayout/Item 星级显示相关修复
[-- 7.24 更新]
* GUILayout/Mail 邮件处理优化
[-- 10.18 更新]
* GUILayout/MainTop 修复顶部栏电量刷新问题


# 元变量


# 游戏内所有变量几乎都藏在元变量中

- ` SL:GetMetaValue(key, param1, param2, ...)` 获取

- ` SL:SetMetaValue(key, param1, param2, ...)` 设置

- ` SL:PrintMetaKey()` 打印所有元变量Key

- ` SL:PrintAllMetaValue()` 打印所有能**获取**的元变量

- ` SL:CheckCondition(conditionStr)` 元变量条件判断， 格式: $(原变量ID) ,需要参数的$(原变量ID,参数...)

- 示例代码
```
    SL:CheckCondition("$(LEVEL) >= 1 and $(PLATFORM_WINDOWS) == false")
    SL:CheckCondition("$(ITEM_COUNT,2) >= 1000 and $(PLATFORM_WINDOWS) == false")
```

# --Set--
|参数名|说明|例子
|:----|:-----|-----|
|"MAIL_CURRENT_ID"|设置当前邮件ID<br>param1: 邮件ID|```SL:SetMetaValue("MAIL_CURRENT_ID", param1)```|
|"BAG_PAGE_CUR"|设置当前选中的背包页<br>param1: 页签|&emsp;|
|"CHAT_CHANNEL_RECEIVIND"|切换聊天频道接收状态<br>param1: 聊天频道<br>param2: boolean 接收状态 [不填默认切换相反状态]|&emsp;|
|"CUR_CHAT_CHANNEL"|当前聊天频道<br>param1: 聊天频道|`SL:SetMetaValue("CUR_CHAT_CHANNEL", channel)`|支持版本号3.40.3以上|
|"SETTING_VALUE"|设置的数据<br>param1：设置ID<br>param2: 设置值 table|&emsp;|
|"SETTING_PICK_VALUE"|设置捡物品数据<br>param1：设置ID<br>param2：设置值 table|&emsp;|
|"SETTING_PICK_GROUP_VALUE"|设置捡物品组数据<br>param1：设置ID<br>param2：设置值 table|&emsp;|
|"SETTING_RANK_DATA"|设置排序相关数据<br>param1：设置ID<br>param2：设置值 table|&emsp;|
|"BOSS_REMIND_TYPE"|设置boss提示类型<br>param1：设置值|&emsp;|
|"BOS_REMIND_VALUE"|设置boss提示值<br>param1：设置值|&emsp;|
|"SUPEREQUIP_SHOW"|角色面板时装显示开关<br>param1：boolean|&emsp;|
|"HERO_SUPEREQUIP_SHOW"|英雄面板时装显示开关<br>param1：boolean|&emsp;|
|"SKILL_KEY"|设置技能快捷键<br>param1：技能ID<br>param2：0~16|&emsp;|
|"H.SKILL_KEY"|英雄设置技能快捷键<br>param1：技能ID<br>param2：0~16|&emsp;|
|"HERO_GUARD_ISCLICK"|是否点击英雄守护按钮 <br>param1: boolean值|&emsp;|
|"HERO_ACTIVES_STATES"|英雄激活的状态列表 <br>param1: table||
|"HERO_SUPEREQUIP_SHOW"|英雄面板 时装显示开关 <br>param1: boolean值||
|"COMPOUND_OPEN_ID"|合成打开的ID <br>param1: 合成表id|&emsp;|
|"SELECT_TARGET_ID"|选择目标ID|```SL:SetMetaValue("SELECT_TARGET_ID", targetID)```|
|"FUNCDOCK_PARAM"|功能菜单参数设置 <br>param1: table 参数数据|```SL:SetMetaValue("FUNCDOCK_PARAM", data)```|
|"CLIPBOARD_TEXT"|设置剪贴板文本<br>param1: string 文本内容|```SL:SetMetaValue("CLIPBOARD_TEXT", "11")```|
|"DROPITEM_FLY_WORLD_POSITION"|设置 自动拾取-掉落物-飞向的世界坐标, 优先级比txt设置的高 <br>需要后端先设置`setpickitemtobag`后才能修改坐标<br>param1: x坐标<br>param2: y坐标|```SL:SetMetaValue("DROPITEM_FLY_WORLD_POSITION", 200, 200)```|
|"QUICK_USE_NUM"|设置快捷栏个数<br>param1: int|```SL:SetMetaValue("QUICK_USE_NUM", 6)```|支持版本号3.40.2以上|
|"GUIDE_EVENT_BEGAN"|特定状况引导事件开始通知<br>param1: 脚本引导父节点ID <br> param2: 是否需要刷新位置|```SL:SetMetaValue("GUIDE_EVENT_BEGAN", 110, true)```|支持版本号3.40.2以上|
|"GUIDE_EVENT_END"|特定状况引导事件结束通知<br>param1: 脚本引导父节点ID|```SL:SetMetaValue("GUIDE_EVENT_END", 110)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_ONOFF"|设置人物内功技能开关<br>param1: 技能ID <br>param2: 技能类型<br>[2 = 人物怒内功技能<br> 4 = 人物静内功技能]<br>param3: 开关状态 0 开启 1关闭 |```SL:SetMetaValue("INTERNAL_SKILL_ONOFF", 101, 2, 1)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_ONOFF"|设置英雄内功技能开关<br>param1: 技能ID <br>param2: 技能类型<br>[3 = 英雄怒内功技能<br> 5 = 英雄静内功技能]<br>param3: 开关状态 0 开启 1关闭 |```SL:SetMetaValue("H.INTERNAL_SKILL_ONOFF", 105, 5, 1)```|支持版本号3.40.2以上|
|"WIN_DEVICE_SIZE"|修改PC端屏幕分辨率<br>param1: 宽 <br>param2: 高|```SL:SetMetaValue("WIN_DEVICE_SIZE", 1024, 768)```|支持版本号3.40.2以上|
|"STALL_SELECT_ID"|摆摊设置选中的物品唯一ID<br>param1: 物品唯一ID|```SL:SetMetaValue("STALL_SELECT_ID", makeIndex)```|支持版本号3.40.3以上|
|"PC_CHAT_INPUT_FILL"|填充PC聊天输入框内容<br>param1: 文本内容|```SL:SetMetaValue("PC_CHAT_INPUT_FILL", msg)```|支持版本号3.40.3以上|
|"TEAM_STATUS_PERMIT"|设置允许组队状态<br>param1: boolean|```SL:SetMetaValue("TEAM_STATUS_PERMIT", true)```|支持版本号3.40.3以上|
|"ADD_STATUS_PERMIT"|设置允许添加状态<br>param1: boolean|```SL:SetMetaValue("ADD_STATUS_PERMIT", true)```|支持版本号3.40.3以上|
|"DEAL_STATUS_PERMIT"|设置允许交易状态<br>param1: boolean|```SL:SetMetaValue("DEAL_STATUS_PERMIT", true)```|支持版本号3.40.3以上|
|"SHOW_STATUS_PERMIT"|设置允许显示状态<br>param1: boolean|```SL:SetMetaValue("SHOW_STATUS_PERMIT", true)```|支持版本号3.40.3以上|
|"TURN_DIR"|设置转向方向<br>param1: int 方向 0 ~ 8|`SL:SetMetaValue("TURN_DIR", 4)`|支持版本号3.40.3以上|
|"USER_TO_MOVE"|手动发起移动 <br> param1: 目标地图坐标 table <br>param2: 移动方向 0 ~ 8 <br> param3: 移动步长<br> param4: 移动类型 int <br>1: 点击地板 2: 摇杆|`SL:SetMetaValue("USER_TO_MOVE", originPos, moveDir, moveStep, 2)`|支持版本号3.40.3以上|
|"SELECT_SHIFT_ATTACK_ID"|设置PC持续攻击目标ID <br> param1: actorID|`SL:SetMetaValue("SELECT_SHIFT_ATTACK_ID", 100181)`|支持版本号3.40.5以上|
|"DROP_TYPE_ISRECEIVE"|设置是否接收该分类掉落信息<br>param1: int 掉落分组id <br>param2: boolean 是否接收|`SL:SetMetaValue("DROP_TYPE_ISRECEIVE", 1, false)`|支持版本号3.40.5以上|
|"AUTOUSE_MAKEINDEX_BY_POS"|添加自动使用弹窗 物品唯一ID <br> param1: 类型 （1: 人物 2: 英雄） param2: 装备位 param3: makeIndex|`SL:SetMetaValue("AUTOUSE_MAKEINDEX_BY_POS", playerType, equipPos, MakeIndex)`|支持版本号3.40.7以上|
# --Get--
### 游戏基础相关
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"SCREEN_WIDTH"|int|屏幕宽|```SL:GetMetaValue("SCREEN_WIDTH")```|
|"SCREEN_HEIGHT"|int|屏幕高|```SL:GetMetaValue("SCREEN_HEIGHT")```|
|"NOTCH_PHONE_INFO"|boolean, table|是否刘海屏<br>返回参数:<br>param1: boolean<br>param2: table {x = 刘海屏偏移坐标x, y = y, width = 减去刘海屏幕宽, height = 屏幕高}|`SL:GetMetaValue("NOTCH_PHONE_INFO")`|
|"PLATFORM_ANDROID"|boolean|安卓平台|```SL:GetMetaValue("PLATFORM_ANDROID")```|
|"PLATFORM_IOS"|boolean|iOS平台|```SL:GetMetaValue("PLATFORM_IOS")```|
|"PLATFORM_WINDOWS"|boolean|Windows平台|```SL:GetMetaValue("PLATFORM_WINDOWS")```|
|"PLATFORM_MOBILE"|boolean|手机平台(包含安卓和iOS)|```SL:GetMetaValue("PLATFORM_MOBILE")```|
|"WINPLAYMODE"|boolean|PC操作模式|```SL:GetMetaValue("WINPLAYMODE")```|
|"IS_PC_PLAY_MODE"|boolean|是否PC操作模式, 等同WINPLAYMODE|```SL:GetMetaValue("IS_PC_PLAY_MODE")```|支持版本号3.40.3以上|
|"CURRENT_OPERMODE"|int|操作模式(PC=1, 手机=2)|```SL:GetMetaValue("CURRENT_OPERMODE")```|
|"GAME_ID"|string|游戏ID|```SL:GetMetaValue("GAME_ID")```|
|"CHANNEL_ID"|string|渠道ID|```SL:GetMetaValue("CHANNEL_ID")```|
|"PACKAGE_NAME"|string|APK包名|```SL:GetMetaValue("PACKAGE_NAME")```|
|"VERSION_NAME"|string|APK版本名|```SL:GetMetaValue("VERSION_NAME")```|
|"VERSION_CODE"|string|APK版本号|```SL:GetMetaValue("VERSION_CODE")```|
|"LOCAL_RES_VERSION"|string|原始/本地客户端版本号|```SL:GetMetaValue("LOCAL_RES_VERSION")```|
|"REMOTE_RES_VERSION"|string|热更客户端版本号|```SL:GetMetaValue("REMOTE_RES_VERSION")```|
|"REMOTE_GM_RES_VERSION"|string|GM资源版本号|```SL:GetMetaValue("REMOTE_GM_RES_VERSION")```|支持版本号3.40.4以上|
|"DEVICE_UNIQUE_ID"|string|PC唯一设备ID|`SL:GetMetaValue("DEVICE_UNIQUE_ID")`|支持版本号3.40.7以上|
|"PROMOTE_ID"|string|推广员ID|```SL:GetMetaValue("PROMOTE_ID")```|
|"FPS"|int|游戏帧率|```SL:GetMetaValue("FPS")```|
|"NET_TYPE"|int|网络类型<br>0 : wifi <br>1 : 蜂窝<br>-1: 未识别 |```SL:GetMetaValue("NET_TYPE")```|
|"BATTERY"|int|手机电量（0~100）|```SL:GetMetaValue("BATTERY")```|
|"GAME_DATA"|table|获取cfg_game_data配置<br>param: 表中的key值|```SL:GetMetaValue("GAME_DATA", param)```|
|"IS_SDK_LOGIN"|boolean|是否是SDK登录|```SL:GetMetaValue("IS_SDK_LOGIN")```|
|"996BOX_LOGIN"|boolean|是否是996盒子登录|```SL:GetMetaValue("996BOX_LOGIN")```|
|"996_CLOUD_DEVICE"|boolean|是否是996云真机|```SL:GetMetaValue("996_CLOUD_DEVICE")```|支持版本号3.40.2以上|
|"YIDUN_DATA" |int|获取易盾的反外挂数据|```SL:GetMetaValue("YIDUN_DATA")```|支持版本号3.40.2以上|
|"SERVER_OPTION"|boolean|服务器开关（param）|```SL:GetMetaValue("SERVER_OPTION", SW_KEY_AUCTION)```|

```lua
param = {
    SW_KEY_AUCTION                        -- 服务器开关 拍卖
    SW_KEY_ALL_FIGHTPAGES                 -- 服务器开关 显示所有战斗页
    SW_KEY_MISSTION                       -- 服务器开关 任务
    SW_KEY_SNDAITEMBOX                    -- 服务器开关 是否显示首饰盒
    SW_KEY_TRADE_DEAL                     -- 服务器开关 面对面交易 true/需要面对面
    SW_KEY_AUTO_DRESS                     -- 服务器开关 自动穿戴
    SW_KEY_OPEN_F_EQUIP                   -- 服务器开关 时装是否开启首饰
    SW_KEY_BIND_GOLD                      -- 服务器开关 开启元宝替换绑元
    SW_KEY_NPC_BUTTON                     -- 服务器开关 显示npc按钮
    SW_KEY_NPC_NAME                       -- 服务器开关 显示npc名字 1:不显示
    SW_KEY_DROP_TIPS                      -- 服务器开关 显示绑定丢弃提示 0:显示
    SW_KEY_EXP_IN_CHAT                    -- 服务器开关 经验信息是否显示在聊天框 0：显示在聊天框
    SW_KEY_SHOW_STALL_NAME                -- 服务器开关 是否显示默认摊位名字  0：显示
    SW_KEY_PLAYER_BLUE_BLOOD              -- 服务器开关  是否显示蓝条HUD_SPRITE_MP   0: 显示
    SW_KEY_ITEMTIPS_TOUBAO_SHOW           -- 服务器开关  是否显示itemtips的投保描述   1= 开启 0 = 关闭
    SW_KEY_BAN_DOUBLE_FIREHIT             -- 服务器开关  是否禁止双烈火    1：禁止
    SW_KEY_ALL_TEAM_EXP                   -- 服务器开关 是否开启全队经验 true/false
    SW_KEY_EQUIP_EXTRA_POS                -- 服务器开关，是否有额外的装备位置  1= 开启 0 = 关闭
}
```

### 服务器相关
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"SERVER_ID"|string|服务器ID|```SL:GetMetaValue("SERVER_ID")```|
|"SERVER_NAME"|string|服务器名字|```SL:GetMetaValue("SERVER_NAME")```|
|"MAIN_SERVER_ID"|string|主服务器ID|```SL:GetMetaValue("MAIN_SERVER_ID")```|
|"RES_VERSION"|string|资源版本|```SL:GetMetaValue("RES_VERSION")```|
|"UID"|string|账号ID|```SL:GetMetaValue("UID")```|
|"LOGIN_DATA"|table|登录角色信息|```SL:GetMetaValue("LOGIN_DATA")```|
|"RESTORE_ROLES"|table|可恢复角色信息|```SL:GetMetaValue("RESTORE_ROLES")```|
|"SERVER_VALUE"|string|服务端下发的变量值 <br> param1: 服务端变量名<br>(可在M2红点中控制下发给客户端的变量)|```SL:GetMetaValue("SERVER_VALUE", param1)```|
|"CURRENT_TALK_NPC_ID"|int|获取当前对话NPC的ID|```SL:GetMetaValue("CURRENT_TALK_NPC_ID")```|支持版本号3.40.2以上|
|"CURRENT_TALK_NPC_TYPEINDEX"|int|获取当前对话NPC的Index|```SL:GetMetaValue("CURRENT_TALK_NPC_TYPEINDEX")```|支持版本号3.40.2以上|
|"CURRENT_TALK_NPC_LAYER"|widget|获取当前打开的NPC面板(txt面板)|```SL:GetMetaValue("CURRENT_TALK_NPC_LAYER")```|支持版本号3.40.6以上|
|"M2_FORBID_SAY"|boolean|M2是否禁止说话<br> param1: boolean 禁止时是否需要提示|```SL:GetMetaValue("M2_FORBID_SAY", true)```|支持版本号3.40.3以上|

### 当前地图
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"MAP_ID"|string|地图ID|```SL:GetMetaValue("MAP_ID")```|
|"MAP_NAME"|string|地图名字|```SL:GetMetaValue("MAP_NAME")```|
|"MAP_DATA_ID"|string|地图数据ID|```SL:GetMetaValue("MAP_DATA_ID")```|
|"MINIMAP_ID"|string|小地图ID|```SL:GetMetaValue("MINIMAP_ID")```|
|"IN_SAFE_AREA"|boolean|是否是安全区域|```SL:GetMetaValue("IN_SAFE_AREA")```|
|"MAP_FORBID_LEVEL_AND_JOB"|boolean|是否禁止职业和等级|```SL:GetMetaValue("MAP_FORBID_LEVEL_AND_JOB")```|
|"MAP_FORBID_SAY"|boolean|是否禁止说话|```SL:GetMetaValue("MAP_FORBID_SAY")```|
|"MAP_SHOW_HPPER"|boolean|是否血量显示百分比|```SL:GetMetaValue("MAP_SHOW_HPPER")```|
|"MAP_FORBID_LOOK"|boolean|是否禁止查看|```SL:GetMetaValue("MAP_FORBID_LOOK")```|
|"MAP_FORBID_LAUNCH_SKILL"|boolean|是否禁止释放某技能|```SL:GetMetaValue("MAP_FORBID_LAUNCH_SKILL")```|
|"MINIMAP_ABLE"|boolean|小地图资源是否有效|```SL:GetMetaValue("MINIMAP_ABLE")```|
|"MAP_DATA_LOADED"|boolean|地图map文件是否加载(false表示正在下载中)```|```SL:GetMetaValue("MAP_DATA_LOADED")```|支持版本号3.40.2以上|
|"MAP_ROWS"|int|地图横向格子数|```SL:GetMetaValue("MAP_ROWS")```|
|"MAP_COLS"|int|地图纵向格子数|```SL:GetMetaValue("MAP_COLS")```|
|"MINIMAP_FILE"|string|获取小地图文件路径|```SL:GetMetaValue("MINIMAP_FILE")```|支持版本号3.40.2以上|
|"MAP_SIZE_WIDTH_PIXEL"|int|地图获取宽度像素|```SL:GetMetaValue("MAP_SIZE_WIDTH_PIXEL")```|支持版本号3.40.2以上|
|"MAP_SIZE_HEIGHT_PIXEL"|string|地图获取高度像素|```SL:GetMetaValue("MAP_SIZE_HEIGHT_PIXEL")```|支持版本号3.40.2以上|
|"MAP_IS_OBSTACLE" |boolean|获取地图格子是否是阻挡<br>param1: 地图坐标X<br>param2: 地图坐标Y|```SL:GetMetaValue("MAP_IS_OBSTACLE", mapX, mapY)```|支持版本号3.40.2以上|
|"MAP_PATH_SIZE"|int|地图计算起点到终点X或者Y 变化最大的差值|```SL:GetMetaValue("MAP_PATH_SIZE")```|支持版本号3.40.2以上|
|"MAP_PATH_POINTS"|table|地图计算路径坐标|```SL:GetMetaValue("MAP_PATH_POINTS")```|支持版本号3.40.2以上|
|"MAP_CURRENT_PATH_INDEX"|int|地图获取当前路径坐标index|```SL:GetMetaValue("MAP_CURRENT_PATH_INDEX")```|支持版本号3.40.2以上|
|"MAP_PLAYER_POS"|table|地图获取人物坐标|```SL:GetMetaValue("MAP_PLAYER_POS")```|支持版本号3.40.2以上|
|"MAP_GET_MONSTERS"|table|地图获取怪物列表位置等信息|```SL:GetMetaValue("MAP_GET_MONSTERS")```|支持版本号3.40.2以上|
|"MAP_GET_PORTALS" |table|地图获取传送点列表位置等信息|```SL:GetMetaValue("MAP_GET_PORTALS")```|支持版本号3.40.2以上|
|"FIND_IN_VIEW_PLAYER_LIST"|table|获取视野内玩家列表|```SL:GetMetaValue("FIND_IN_VIEW_PLAYER_LIST")```|支持版本号3.40.2以上|
|"FIND_IN_VIEW_MONSTER_LIST"|table|获取视野内怪物列表<br>param1: boolean 是否屏蔽主玩家宠物<br>param2: boolean 是否屏蔽网络玩家宠物|```SL:GetMetaValue("FIND_IN_VIEW_MONSTER_LIST")```|支持版本号3.40.2以上|
|"FIND_IN_VIEW_NPC_LIST"|table|获取视野内NPC列表|```SL:GetMetaValue("FIND_IN_VIEW_NPC_LIST")```|支持版本号3.40.2以上|
|"IN_SIEGE_AREA"|boolean|是否在攻城区域|```SL:GetMetaValue("IN_SIEGE_AREA")```|支持版本号3.40.5以上|

### 宠物
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"PET_ALIVE"|boolean|是否有存活的宝宝|```SL:GetMetaValue("PET_ALIVE")```|
|"PET_LOCK_ID"|string|宠物锁定的目标ID|```SL:GetMetaValue("PET_LOCK_ID")```|

### 英雄
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"USEHERO"|boolean|是否开启英雄|```SL:GetMetaValue("USEHERO")```|
|"HERO_IS_ALIVE"|boolean|是否召唤英雄|```SL:GetMetaValue("HERO_IS_ALIVE")```|
|"HERO_IS_ACTIVE"|boolean|是否激活英雄|```SL:GetMetaValue("HERO_IS_ACTIVE")```|
|"HERO_ID"|int|英雄ID|```SL:GetMetaValue("HERO_ID")```|
|"HERO_STATES_SYS_VALUES"|table|英雄状态系统能设置的列表|```SL:GetMetaValue("HERO_STATES_SYS_VALUES")```|
|"HERO_ACTIVES_STATES"|table|英雄激活的状态列表|```SL:GetMetaValue("HERO_ACTIVES_STATES")```|
|"HERO_STATE"|int|获取英雄状态 0 攻击 1 跟随 2 休息|```SL:GetMetaValue("HERO_STATE")```|
|"HERO_GUARDSTATE"|boolean|获取英雄守护状态|```SL:GetMetaValue("HERO_GUARDSTATE")```|
|"HERO_GUARD_ISCLICK"|boolean|是否点击守护按钮|```SL:GetMetaValue("HERO_GUARD_ISCLICK")```|

### 道具
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"MONEY"|string|获取货币数量|```SL:GetMetaValue("MONEY", ID)```|
|"MONEY_ASSOCIATED"|string|获取货币数量 (包括道具表配置的Reserved 等价替换道具的数量)|`SL:GetMetaValue("MONEY_ASSOCIATED", id)`|支持版本号3.40.3以上|
|"STD_ITEMS"|table|获取所有道具信息|```SL:GetMetaValue("STD_ITEMS")```|
|"ITEM_DATA"|table|根据道具index获取道具信息|```SL:GetMetaValue("ITEM_DATA", itemIndex)```|
|"ITEM_COUNT"|int|根据道具index或者名字获取道具数量|```SL:GetMetaValue("ITEM_COUNT", itemIndex)或者SL:GetMetaValue("ITEM_COUNT", itemName)```|
|"ITEM_NAME"|string|根据道具index获取道具名字|```SL:GetMetaValue("ITEM_NAME", itemIndex)```|
|"ITEM_INDEX_BY_NAME"|int|根据道具名字获取道具index|```SL:GetMetaValue("ITEM_INDEX_BY_NAME", itemName)```|
|"ITEM_NAME_COLOR"|string|获取道具名字颜色|```SL:GetMetaValue("ITEM_NAME_COLOR", itemIndex)```|
|"ITEM_NAME_COLOR_VALUE"|string|道具名字颜色,"#FFFFFF"格式|```SL:GetMetaValue("ITEM_NAME_COLOR_VALUE", itemIndex)```|
|"ITEM_NAME_COLORID"|string|道具名字颜色ID, 颜色表ID|```SL:GetMetaValue("ITEM_NAME_COLORID", itemIndex)```|
|"ITEM_PROMPT_DATA"|table|道具表prompt解析后数据|```SL:GetMetaValue("ITEM_PROMPT_DATA")```|
|"ITEM_CUSTOM_ATTR"|table|获取物品自定义属性数据 param1: 物品MakeIndex|```SL:GetMetaValue("ITEM_CUSTOM_ATTR", param1)```|支持版本号3.40.8以上|
|"ITEM_IS_BIND"|boolean|物品是否绑定|```SL:GetMetaValue("ITEM_IS_BIND")```|
|"ITEM_DATA_BY_MAKEINDEX"|table|根据MakeIndex获取背包数据<br>param1: MakeIndex<br>param2: 是否是英雄|```SL:GetMetaValue("ITEM_DATA_BY_MAKEINDEX", param1, param2)```|
|"EQUIP_DATA_BY_MAKEINDEX"|table|根据MakeIndex获取装备数据<br>param1: MakeIndex<br>param2: 是否是英雄|```SL:GetMetaValue("EQUIP_DATA_BY_MAKEINDEX", param1, param2)```|
|"STORAGE_DATA_BY_MAKEINDEX"|table|根据MakeIndex获取仓库数据<br>param1: MakeIndex|```SL:GetMetaValue("STORAGE_DATA_BY_MAKEINDEX", param1)```|
|"QUICKUSE_DATA_BY_MAKEINDEX"|table|根据MakeIndex获取快捷栏数据<br>param1: MakeIndex|```SL:GetMetaValue("QUICKUSE_DATA_BY_MAKEINDEX", param1)```|支持版本号3.40.3以上|
|"LOOKPLAYER_DATA_BY_MAKEINDEX"|table|根据MakeIndex获取查看他人装备数据<br>param1: MakeIndex|```SL:GetMetaValue("LOOKPLAYER_DATA_BY_MAKEINDEX", param1)```|支持版本号3.40.3以上|
|"BAG_DATA"|table|获取背包所有物品数据|```SL:GetMetaValue("BAG_DATA")```|
|"H.BAG_DATA"|table|获取背包所有物品数据|```SL:GetMetaValue("H.BAG_DATA")```|支持版本号3.40.8以上|
|"QUICKUSE_DATA"|table|获取快捷使用数据|```SL:GetMetaValue("QUICKUSE_DATA")```|
|"CHECK_USE_ITEM_BUFF"|boolean, int|检查禁止使用物品buff <br>param1: itemIndex<br> 返回参数：能否使用, buffID|```SL:GetMetaValue("CHECK_USE_ITEM_BUFF", itemIndex)```|支持版本号3.40.7以上|
|"ITEM_CAN_AUTOUSE"|boolean|物品能否自动使用 <br>param1: itemData table -- 物品数据|```SL:GetMetaValue("ITEM_CAN_AUTOUSE", itemData)```|支持版本号3.40.7以上|
|"SKILLBOOK_CAN_USE"|boolean|技能书能否使用 <br>param1: itemName 技能书名字 <br> param2：boolean 是否英雄|```SL:GetMetaValue("SKILLBOOK_CAN_USE", itemName, false)```|支持版本号3.40.7以上|
|"ITEM_BELONG_BY_MAKEINDEX"|int| 根据MakeIndex获取物品归属[可参考GUIDefine.ITEM_BELONG]|```SL:GetMetaValue("ITEM_BELONG_BY_MAKEINDEX", makeIndex)```|支持版本号3.40.7以上|
|"BAG_MAKEINDEX_BY_POS"|int|获取背包物品唯一ID <br>param1: 背包位置 <br> param2: boolean -- 是否英雄|```SL:GetMetaValue("BAG_MAKEINDEX_BY_POS", pos)```|支持版本号3.40.8以上|
|"ITEM_ARTICLE_ENUM"|table|物品规则类型枚举|```SL:GetMetaValue("ITEM_ARTICLE_ENUM")```|支持版本号3.40.8以上|

### 道具框
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"ITEM_SCALE"|int|道具框默认缩放|```SL:GetMetaValue("ITEM_SCALE")```|

### 战斗
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"BATTLE_IS_AFK"|boolean|是否自动挂机中|```SL:GetMetaValue("BATTLE_IS_AFK")```|
|"BATTLE_AFK_BEGIN"|void|开始自动挂机|```SL:SetMetaValue("BATTLE_AFK_BEGIN")```|
|"BATTLE_AFK_END"|void|结束自动挂机|```SL:SetMetaValue("BATTLE_AFK_END")```|
|"BATTLE_IS_AUTO_MOVE"|boolean|是否自动寻路中|```SL:GetMetaValue("BATTLE_IS_AUTO_MOVE")```|
|"BATTLE_MOVE_BEGIN"|void|开始自动寻路<br>mapID: 地图ID<br>mapX: 坐标x<br>mapY: 坐标y<br>target:<br> {<br> &emsp;type: 0：怪物 &emsp;&emsp;&emsp;1：NPC<br>&emsp;index: 目标类型index<br>}<br>type: 寻路类型<br>可参考GUIDefine.AUTO_MOVE_TYPE|```SL:SetMetaValue("BATTLE_MOVE_BEGIN", mapID, mapX, mapY, target, type)```|
|"BATTLE_MOVE_END"|void|结束自动寻路|```SL:SetMetaValue("BATTLE_MOVE_END")```|
|"BATTLE_IS_AUTO_PICK"|boolean|是否自动捡物中|```SL:GetMetaValue("BATTLE_IS_AUTO_PICK")```|
|"BATTLE_PICK_BEGIN"|void|开始自动捡物|```SL:SetMetaValue("BATTLE_PICK_BEGIN")```|
|"BATTLE_PICK_END"|void|结束自动捡物|```SL:SetMetaValue("BATTLE_PICK_END")```|

### Actor

-   `actorID: 玩家、怪物、NPC、人形怪等对象ID(对应服务端唯一ID/UserID)`

|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"MAIN_ACTOR_ID"|string|主玩家actorID|```SL:GetMetaValue("MAIN_ACTOR_ID")```|支持版本号3.40.3以上|
|"ACTOR_IS_PLAYER"|boolean|是否是玩家|```SL:GetMetaValue("ACTOR_IS_PLAYER", actorID)```|
|"ACTOR_IS_NETPLAYER"|boolean|是否是网络玩家|```SL:GetMetaValue("ACTOR_IS_NETPLAYER", actorID)```|
|"ACTOR_IS_MONSTER"|boolean|是否是怪物|```SL:GetMetaValue("ACTOR_IS_MONSTER", actorID)```|
|"ACTOR_IS_NPC"|boolean|是否是NPC|```SL:GetMetaValue("ACTOR_IS_NPC", actorID)```|
|"ACTOR_IS_HERO"|boolean|是否是英雄|```SL:GetMetaValue("ACTOR_IS_HERO", actorID)```|
|"ACTOR_IS_HUMAN"|boolean|是否是人形怪|```SL:GetMetaValue("ACTOR_IS_HUMAN", actorID)```|
|"ACTOR_NAME"|string|获取actor 名字|```SL:GetMetaValue("ACTOR_NAME", actorID)```|
|"ACTOR_HP"|int|获取 actor Hp|```SL:GetMetaValue("ACTOR_HP", actorID)```|
|"ACTOR_MAXHP"|int|获取actor Max Hp|```SL:GetMetaValue("ACTOR_MAXHP", actorID)```|
|"ACTOR_MP"|int|获取actor Mp|```SL:GetMetaValue("ACTOR_MP", actorID)```|
|"ACTOR_MAXMP"|int|获取actor Max Mp|```SL:GetMetaValue("ACTOR_MAXMP", actorID)```|
|"ACTOR_LEVEL"|int|获取actor等级|```SL:GetMetaValue("ACTOR_LEVEL", actorID)```|
|"ACTOR_JOB_ID"|int|获取actor职业|```SL:GetMetaValue("ACTOR_JOB_ID", actorID)```|
|"ACTOR_SEX"|int|获取actor性别|```SL:GetMetaValue("ACTOR_SEX", actorID)```|
|"ACTOR_IS_DIE"|boolean|actor是否死亡|```SL:GetMetaValue("ACTOR_IS_DIE", actorID)```|
|"ACTOR_OWNER_ID"|string|获取actor归属ID|```SL:GetMetaValue("ACTOR_OWNER_ID", actorID)```|
|"ACTOR_OWNER_NAME"|string|获取actor归属名字|```SL:GetMetaValue("ACTOR_OWNER_NAME", actorID)```|
|"ACTOR_BIGICON_ID"|int|获取怪物大图标ID|```SL:GetMetaValue("ACTOR_BIGICON_ID", actorID)```|
|"SELECT_TARGET_ID"|int|选中的目标actorID或者怪物归属者|```SL:GetMetaValue("SELECT_TARGET_ID")```|
|"TARGET_ATTACK_ENABLE"|boolean|检查该目标是否可以攻击<br>param1: 目标actorID|```SL:GetMetaValue("TARGET_ATTACK_ENABLE", actorID)```|支持版本号3.40.3以上|
|"ACTOR_TEAM_STATE"|int|获取actor组队状态<br>0：未组队<br>1：组队中<br> <br>param1: actorID|```SL:GetMetaValue("ACTOR_TEAM_STATE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_GUILD_ID"|string|获取actor行会ID|```SL:GetMetaValue("ACTOR_GUILD_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_GUILD_NAME"|string|获取actor行会名字|```SL:GetMetaValue("ACTOR_GUILD_NAME", actorID)```|支持版本号3.40.2以上|
|"ACTOR_TYPE_INDEX"|int|获取actor的typeIndex, 对应怪物表/NPC表 ID|```SL:GetMetaValue("ACTOR_TYPE_INDEX", actorID)```|支持版本号3.40.2以上|
|"ACTOR_DIR"|int|获取actor方向|```SL:GetMetaValue("ACTOR_DIR", actorID)```|支持版本号3.40.2以上|
|"ACTOR_MAP_X"|int|获取actor地图坐标X|```SL:GetMetaValue("ACTOR_MAP_X", actorID)```|支持版本号3.40.2以上|
|"ACTOR_MAP_Y"|int|获取actor地图坐标Y|```SL:GetMetaValue("ACTOR_MAP_Y", actorID)```|支持版本号3.40.2以上|
|"ACTOR_POSITION_X"|int|获取actor世界坐标X|```SL:GetMetaValue("ACTOR_POSITION_X", actorID)```|支持版本号3.40.2以上|
|"ACTOR_POSITION_Y"|int|获取actor世界坐标Y|```SL:GetMetaValue("ACTOR_POSITION_Y", actorID)```|支持版本号3.40.2以上|
|"ACTOR_MASTER_ID"|int|获取actor主人ID|```SL:GetMetaValue("ACTOR_MASTER_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_HAVE_MASTER"|boolean|获取actor是否有主人|```SL:GetMetaValue("ACTOR_HAVE_MASTER", actorID)```|支持版本号3.40.2以上|
|"ACTOR_FACTION"|int|获取actor阵营ID, 大于0且相等是同阵营|```SL:GetMetaValue("ACTOR_FACTION", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IN_SAFE_ZONE"|boolean|获取actor是否在安全区|```SL:GetMetaValue("ACTOR_IN_SAFE_ZONE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_APPR_ID"|boolean|获取actor的外观ID|```SL:GetMetaValue("ACTOR_APPR_ID", actorID)```|支持版本号3.40.3以上|
|"ACTOR_MOUNT_NODE"|widget|获取actor挂接点 **( ！即取即用 避免存储使用**|`SL:GetMetaValue("ACTOR_MOUNT_NODE", actorID)`|支持版本号3.40.7以上|
|"ACTOR_CAN_LOCK_BY_HERO"|boolean|检查英雄选中的目标是否能锁定|`SL:GetMetaValue("ACTOR_CAN_LOCK_BY_HERO", actorID)`|支持版本号3.40.7以上|
|"ACTOR_PKLV"|int|获取actor红名灰名 <br> 白=0  咖啡=1  红=2  灰=3|```SL:GetMetaValue("ACTOR_PKLV", actorID)```|支持版本号3.40.2以上|
|"ACTOR_SERVER_ID"|int|获取actor区服ID, 跨服时使用|```SL:GetMetaValue("ACTOR_SERVER_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_IN_STALL"|boolean|actor是否在摆摊|```SL:GetMetaValue("ACTOR_IS_IN_STALL", actorID)```|支持版本号3.40.2以上|
|"ACTOR_STALL_NAME"|string|获取actor摆摊名|```SL:GetMetaValue("ACTOR_STALL_NAME", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_OFFLINE"|string|获取actor是否是离线状态玩家|```SL:GetMetaValue("ACTOR_IS_OFFLINE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_MYSTERY_MAN"|boolean|actor是否是神秘人|```SL:GetMetaValue("ACTOR_IS_MYSTERY_MAN", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_HUSHEN"|boolean|获取actor是否拥有护身|```SL:GetMetaValue("ACTOR_IS_HUSHEN", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_MAINPLAYER"|boolean|actor是否是主玩家|```SL:GetMetaValue("ACTOR_IS_MAINPLAYER", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_HORSEBACK_RADING"|boolean|actor是否是骑马状态|```SL:GetMetaValue("ACTOR_IS_HORSEBACK_RADING", actorID)```|支持版本号3.40.8以上|
|"ACTOR_NATION_ID"|int|获取actor国家ID|```SL:GetMetaValue("ACTOR_NATION_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_HORSE_MASTER_ID"|int|获取actor坐骑的主驾ID|```SL:GetMetaValue("ACTOR_HORSE_MASTER_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_HORSE_COPILOT_ID"|int|获取actor坐骑的副驾ID|```SL:GetMetaValue("ACTOR_HORSE_COPILOT_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_HORSE_COPILOT"|boolean|actor是否是坐骑的副驾|```SL:GetMetaValue("ACTOR_IS_HORSE_COPILOT", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_DOUBLE_HORSE"|boolean|actor是否是双人坐骑|```SL:GetMetaValue("ACTOR_IS_DOUBLE_HORSE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_BODY_HORSE"|boolean|actor是否是连体坐骑|```SL:GetMetaValue("ACTOR_IS_BODY_HORSE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_MOVE_EFFECT"|int|获取actor的足迹特效ID|```SL:GetMetaValue("ACTOR_MOVE_EFFECT", actorID)```|支持版本号3.40.2以上|
|"ACTOR_DEAR_ID"|int|获取actor的夫妻ID|```SL:GetMetaValue("ACTOR_DEAR_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_MENTOR_ID"|int|获取actor的师徒ID|```SL:GetMetaValue("ACTOR_MENTOR_ID", actorID)```|支持版本号3.40.2以上|
|"ACTOR_NEAR_SHOW"|boolean|获取actor是否在附近显示|```SL:GetMetaValue("ACTOR_NEAR_SHOW", actorID)```|支持版本号3.40.3以上|
|"ACTOR_IS_MOVE"|boolean|获取actor是否在移动状态|`SL:GetMetaValue("ACTOR_IS_MOVE", SL:GetMetaValue("USER_ID"))`|支持版本号3.40.3以上|
|"ACTOR_STOME_MODE"|boolean|获取actor(怪物)是否石化状态|```SL:GetMetaValue("ACTOR_STOME_MODE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_RACE_SERVER"|int|获取actor(怪物) race server|```SL:GetMetaValue("ACTOR_RACE_SERVER", actorID)```|支持版本号3.40.2以上|
|"ACTOR_RACE_IMG"|int|获取actor(怪物) race img|```SL:GetMetaValue("ACTOR_RACE_IMG", actorID)```|支持版本号3.40.2以上|
|"ACTOR_HIDE_NAME"|boolean|获取actor(怪物)是否不显示名字|```SL:GetMetaValue("ACTOR_HIDE_NAME", actorID)```|支持版本号3.40.2以上|
|"ACTOR_HIDE_HP_BAR"|boolean|获取actor(怪物)是否不显示血条|```SL:GetMetaValue("ACTOR_HIDE_HP_BAR", actorID)```|支持版本号3.40.2以上|
|"ACTOR_NATION_ENEMY_PK"|boolean|获取actor(怪物)国家模式是否可被攻击|```SL:GetMetaValue("ACTOR_NATION_ENEMY_PK", actorID)```|支持版本号3.40.2以上|
|"ACTOR_GM_DATA"|table|获取actor的GM自定义数据|```SL:GetMetaValue("ACTOR_GM_DATA", actorID)```|支持版本号3.40.3以上|
|"ACTOR_IS_DEATH"|boolean|actor是否死亡|```SL:GetMetaValue("ACTOR_IS_DEATH", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_BORN"|boolean|actor是否出生|```SL:GetMetaValue("ACTOR_IS_BORN", actorID)```|支持版本号3.40.2以上|
|"ACTOR_IS_CAVE"|boolean|actor是否钻回洞穴|```SL:GetMetaValue("ACTOR_IS_CAVE", actorID)```|支持版本号3.40.2以上|
|"ACTOR_BUFF_DATA"|table|actor身上所有buff数据|```SL:GetMetaValue("ACTOR_BUFF_DATA", actorID)```|
|"ACTOR_HAS_ONE_BUFF"|boolean|actor是否有某个buff|```SL:GetMetaValue("ACTOR_HAS_ONE_BUFF", actorID, buffID)```|
|"ACTOR_BUFF_DATA_BY_ID"|table|获取actor身上某个buff数据|```SL:GetMetaValue("ACTOR_BUFF_DATA_BY_ID", actorID, buffID)```|支持版本号3.40.2以上|

```
返回值描述(int)：
    类型：table
    {
        {
            id          -- buffID
            endTime     -- buff 结束时间
            ol          -- buff 叠加层级
            config      -- buff cfg_buff配置表中数据
            name        -- buff 名字
            tips        -- buff 描述
            icon        -- buff icon
            sort        -- buff 图标排序字段
        }
    }
```

### 其他
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"PKMODE"|int|获取当前PK模式<br>0：全体<br>1：和平<br>2：夫妻<br>3：师徒<br>4：组队<br>5：公会<br>6：善恶<br>7：国家|```SL:GetMetaValue("PKMODE")```|
|"PKMODE_CAN_USE"|boolean|该PK模式是否可以切换<br>param: PK模式|```SL:GetMetaValue("PKMODE_CAN_USE", 5)```|
|"PET_PKMODE"|int|获取宠物PK模式<br>1：跟随<br>2：战斗<br>3：锁定<br>4：休息|```SL:GetMetaValue("PET_PKMODE")```|
|"PET_ALIVE"|boolean|是否有存活的宝宝|```SL:GetMetaValue("PET_ALIVE")```|
|"PET_LOCK_ID"|string|宠物锁定的目标ID|```SL:GetMetaValue("PET_LOCK_ID")```|
|"KFSTATE"|boolean|是否处于跨服|```SL:GetMetaValue("KFSTATE")```|
|"SERVER_TIME"|int|当前服务器时间|```SL:GetMetaValue("SERVER_TIME")```|
|"X"|int|人物当前坐标X|```SL:GetMetaValue("X")```|
|"Y"|int|人物当前坐标Y|```SL:GetMetaValue("Y")```|
|"BUBBLETIPS_INFO"|table|根据气泡index获取气泡数据<br>气泡类型：<br>1: 可提升提示<br>2: 邮件<br>3: 组队邀请<br>4: 交易邀请<br>5: 好友邀请<br>6: 行会邀请<br>7: 拍卖行提醒<br>8: 经验存储提醒<br>9: 装备首曝提示<br>10: 行会申请提示<br>11: 药品不足提示<br>12: 装备推送<br>13: 结盟申请<br>14: 私聊提示|```SL:GetMetaValue("BUBBLETIPS_INFO", index)```|
|"BONUSPOINT"|int|转生属性点|```SL:GetMetaValue("BONUSPOINT")```|
|"IS_PICK_STATE"|boolean|是否是自动拾取状态|```SL:GetMetaValue("IS_PICK_STATE")```|
|"PC_POS_Y"|int|PC端Y轴适配|```SL:GetMetaValue("PC_POS_Y")```|
|"MENU_LAYERS_BY_GROUNP"|int|*通过 cfg_menulayer 表中的组ID(group_id)获取该组界面配置信息*|```SL:GetMetaValue("MENU_LAYERS_BY_GROUNP", groupID)```|
|"DARK_STATE"|int|黑夜当前状态|```SL:GetMetaValue("DARK_STATE")```|
|"UIMODEL_HAIR_OFFSET"|table|内观头发偏移配置|```SL:GetMetaValue("UIMODEL_HAIR_OFFSET")```|
|"UIMODEL_EQUIP_OFFSET"|table|内观装备偏移配置|```SL:GetMetaValue("UIMODEL_EQUIP_OFFSET")```|
|"TOUCH_STATE"|boolean|屏幕点击状态|```SL:GetMetaValue("TOUCH_STATE")```|
|"BEST_RING_WIN_ISOPEN"|boolean|首饰盒界面是否打开<br>param1: 1: 自己人物、2：自己英雄、11：其他玩家人物、12：其他玩家英雄、21：交易行人物、22：交易行英雄|```SL:GetMetaValue("BEST_RING_WIN_ISOPEN", 1)```|
|"BEST_RING_OPENSTATE"|boolean|首饰盒开启状态<br>param1: 1: 自己人物、2：自己英雄、11：其他玩家人物、12：其他玩家英雄、21：交易行人物、22：交易行英雄|```SL:GetMetaValue("BEST_RING_OPENSTATE", 1)```|
|"CHECK_FUNCBTN_SHOW"|boolean|检查当前类别功能菜单的某种按钮是否显示<br>param1:功能类别 FuncDock.FuncDockType可查 <br>param2: 按钮类型 FuncDock.BtnOperatorType可查 |```SL:GetMetaValue("CHECK_FUNCBTN_SHOW", dockType, btnType)```|
|"MOUSE_MOVE_POS"|table|鼠标移动位置|```SL:GetMetaValue("MOUSE_MOVE_POS")```|
|"CHECK_MINIMAP_OPEN"|boolean|小地图界面是否打开|```SL:GetMetaValue("CHECK_MINIMAP_OPEN")```|
|"TRADINGBANK_OPENSTATUS"|boolean|交易行开启状态<br>进入游戏和打开交易行会请求后台更新状态|```SL:GetMetaValue("TRADINGBANK_OPENSTATUS")```|支持版本号3.40.2以上|
|"OPEN_SERVER_TIME"|int|开服时间戳|```SL:GetMetaValue("OPEN_SERVER_TIME")```|支持版本号3.40.2以上|
|"OPEN_SERVER_DAY"|int|开服天数|```SL:GetMetaValue("OPEN_SERVER_DAY")```|支持版本号3.40.2以上|
|"MERGE_SERVER_COUNT"|int|合服次数|```SL:GetMetaValue("MERGE_SERVER_COUNT")```|支持版本号3.40.2以上|
|"MERGE_SERVER_TIME"|int|合服时间戳|```SL:GetMetaValue("MERGE_SERVER_TIME")```|支持版本号3.40.2以上|
|"MERGE_SERVER_DAY"|int|合服天数|```SL:GetMetaValue("MERGE_SERVER_DAY")```|支持版本号3.40.2以上|
|"BUFF_CONFIG"|table|获取buffID的配置表数据 <br> param1: buffID<br> 无参, 则整个buff表数据|```SL:GetMetaValue("BUFF_CONFIG")```|支持版本号3.40.2以上|
|"SHOW_STATUS_PERMIT"|boolean|允许在附近显示状态|```SL:GetMetaValue("SHOW_STATUS_PERMIT")```|支持版本号3.40.3以上|
|"GAMEPAD_MOVE_PARAM"|int, int|获取游戏摇杆移动参数, 返回第一个参数: 移动方向 int 0 ~ 8<br> 返回第二个参数: 移动步长 int |`SL:GetMetaValue("GAMEPAD_MOVE_PARAM")`|支持版本号3.40.3以上|
|"TARGET_MAPPOS_DIR"|int|获取目标地图坐标到初始地图坐标的方向/朝向 0 ~ 8 <br>param1: 初始地图坐标 table<br>param2: 目标地图坐标 table|`SL:GetMetaValue("TARGET_MAPPOS_DIR", srcPos, destPos)`|支持版本号3.40.3以上|
|"CHECK_REDPOINT_ID"|boolean|检测红点表对应id是否满足条件|`SL:GetMetaValue("CHECK_REDPOINT_ID", id)`|支持版本号3.40.4以上|
|"CTRL_PRESSED"|boolean|PC端 CTRL键是否按下|`SL:GetMetaValue("CTRL_PRESSED")`|支持版本号3.40.4以上|
|"PC_NP_STATUS"|boolean|PC端 是否开启NP反外挂|`SL:GetMetaValue("PC_NP_STATUS")`||
|"SELECT_SHIFT_ATTACK_ID"|int|获取PC持续攻击目标|```SL:GetMetaValue("SELECT_SHIFT_ATTACK_ID")```|支持版本号3.40.5以上|
|"IS_PICKABLE_DROPITEM"|boolean|掉落物是否可拾取<br> param1: 掉落物 actorID<br> param2: 归属ID|`SL:GetMetaValue("IS_PICKABLE_DROPITEM", actorID, mainPlayerID)`|支持版本号3.40.5以上|
|"AUTOUSE_MAKEINDEX_BY_POS"|int|获取已添加的自动使用弹窗物品唯一ID <br> param1: 类型 （1: 人物 2: 英雄） param2: 装备位|`SL:GetMetaValue("AUTOUSE_MAKEINDEX_BY_POS", playerType, equipPos)`|支持版本号3.40.7以上|
|"CHECK_IN_GUIDE"|boolean|是否在引导中 [Lua添加的引导]|`SL:GetMetaValue("CHECK_IN_GUIDE")`|支持版本号3.40.7以上|
|"PICK_ACTORID_BY_POS"|actorID|PC 按坐标选中actor|`SL:GetMetaValue("PICK_ACTORID_BY_POS", pos)`|支持版本号3.40.7以上|

### 聊天
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"CHAT_EMOJI"|table|获取聊天表情包|SL:GetMetaValue("CHAT_EMOJI")|
|"CHAT_INPUT_CACHE"|table|获取聊天输入历史记录缓存|SL:GetMetaValue("CHAT_INPUT_CACHE")|
|"CHAT_SHOW_ITEMS"|table|获取聊天显示的道具|SL:GetMetaValue("CHAT_SHOW_ITEMS")|
|"CHAT_CHANNEL_ISRECEIVE"|boolean|当前频道是否接受聊天信息|SL:GetMetaValue("CHAT_CHANNEL_ISRECEIVE", 3)|
|"DROP_TYPE_ISRECEIVE"|boolean|是否接收该分类掉落信息<br> param1: 掉落分类id 1-10|SL:GetMetaValue("DROP_TYPE_ISRECEIVE", 1)|支持版本号3.40.5以上|
|"CHATANDTIPS_USE_FONT"|string|聊天 Tips使用的字体路径|SL:GetMetaValue("CHATANDTIPS_USE_FONT")|
|"CUR_CHAT_CHANNEL"|int|获取当前聊天频道|SL:GetMetaValue("CUR_CHAT_CHANNEL")|支持版本号3.40.3以上|
|"CHAT_TARGETS"|table|获取聊天目标 {{name = 玩家名, uid = 玩家ID}, ..}|SL:GetMetaValue("CHAT_TARGETS")|支持版本号3.40.3以上|
|"CHAT_CUR_CDTIME"|int|获取当前聊天CD时间|SL:GetMetaValue("CHAT_CUR_CDTIME")|支持版本号3.40.3以上|
|"IS_CLOSE_FAKEDROP"|boolean|是否关闭假掉落|SL:GetMetaValue("IS_CLOSE_FAKEDROP")|支持版本号3.40.7以上|
|"CHAT_MSGTYPE_ENUM"|table|聊天消息类型列表, 详情如下|SL:GetMetaValue("CHAT_MSGTYPE_ENUM")|支持版本号3.40.3以上|
|"CHAT_CHANNEL_ENUM"|table|聊天频道列表, 详情如下|SL:GetMetaValue("CHAT_MSGTYPE_ENUM")|支持版本号3.40.3以上|
```
聊天消息类型：
{
    Normal     = 1,     -- 普通消息
    Position   = 2,     -- 坐标
    Equip      = 3,     -- 装备
    SystemTips = 5,     -- 系统通知消息，需使用特定的富文本解析
    FColorText = 6,     -- 系统通知消息，需使用FColor富文本解析
    SRText     = 7,     -- 系统通知消息，需使用SRText富文本解析
}

聊天频道:
{
    Common    = 0,  -- 综合
    System    = 1,  -- 系统
    Shout     = 2,  -- 喊话
    Private   = 3,  -- 私聊
    Guild     = 4,  -- 行会
    Team      = 5,  -- 组队
    Near      = 6,  -- 附近
    World     = 7,  -- 世界
    Nation    = 8,  -- 国家
    Union     = 9,  -- 联盟
    GuildTips = 40, -- 行会通知
}
```

### 组队
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"TEAM_NEAR"|table|附近队伍列表|```SL:GetMetaValue("TEAM_NEAR")```|
|"TEAM_MEMBER_LIST"|table|队伍成员列表|```SL:GetMetaValue("TEAM_MEMBER_LIST")```|
|"TEAM_COUNT"|int|当前队伍人数|```SL:GetMetaValue("TEAM_COUNT")```|
|"TEAM_MAC_COUNT"|int|队伍最大人数|```SL:GetMetaValue("TEAM_MAC_COUNT")```|
|"TEAM_IS_MEMBER"|boolean|是否是队伍成员|```SL:GetMetaValue("TEAM_IS_MEMBER")```|
|"TEAM_STATUS_PERMIT"|boolean|允许组队状态|```SL:GetMetaValue("TEAM_STATUS_PERMIT")```|
|"TEAM_APPLY"|table|入队申请列表|```SL:GetMetaValue("TEAM_APPLY")```|
|"DOCKTYPE_NENUM"|table|func dock enum,返回值如下：data |```SL:GetMetaValue("DOCKTYPE_NENUM")```|
```
data = {
     Func_Player_Head        = 1,  -- 点击玩家头像
     Func_Friend             = 2,  -- 好友界面
     Func_Team               = 3,  -- 左侧组队导航栏
     Func_Guild              = 4,  -- 行会界面
     Func_Friend_Recent      = 5,  -- 好友最近联系界面
     Func_Friend_Enemy       = 6,  -- 好友仇敌界面
     Func_Friend_BlackList   = 7,  -- 好友黑名单界面
     Func_TeamLayer          = 8,  -- 组队界面
     Func_Monster_Head       = 9,  -- 点击人形怪头像
     Func_Near_Player        = 10  -- 附近玩家
}
```

### 邮件
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"MAIL_LIST"|table|邮件列表|```SL:GetMetaValue("MAIL_LIST")```|
|"MAIL_BY_ID"|string|根据邮件ID获取邮件|```SL:GetMetaValue("MAIL_BY_ID", mailID)```|
|"MAIL_HAVE_DEL_ITEM"|boolean|是否有邮件可以删除|```SL:GetMetaValue("MAIL_HAVE_DEL_ITEM")```|
|"MAIL_CURRENT_ID"|int|当前邮件ID|```SL:GetMetaValue("MAIL_CURRENT_ID")```|

### 拍卖行
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"AUCTION_BIDPRICE_MIN"|int|默认最低竞拍价|```SL:GetMetaValue("AUCTION_BIDPRICE_MIN")```|
|"AUCTION_BIDPRICE_MAX"|int|默认最高竞拍价|```SL:GetMetaValue("AUCTION_BIDPRICE_MAX")```|
|"AUCTION_BUYPRICE_MIN"|int|默认最低一口价|```SL:GetMetaValue("AUCTION_BUYPRICE_MIN")```|
|"AUCTION_BUYPRICE_MAX"|int|默认最高一口价|```SL:GetMetaValue("AUCTION_BUYPRICE_MAX")```|
|"AUCTION_DEFAULT_SHELF"|int|默认货架数量|```SL:GetMetaValue("AUCTION_DEFAULT_SHELF")```|
|"AUCTION_PUT_LIST_CNT"|int|上架列表数量|```SL:GetMetaValue("AUCTION_PUT_LIST_CNT")```|
|"AUCTION_MONEY"|int|拍卖行货币|```SL:GetMetaValue("AUCTION_MONEY")```|
|"AUCTION_CAN_BID"|boolean|是否可竞价 <br>param1: 拍卖物品数据|```SL:GetMetaValue("AUCTION_CAN_BID", item)```|
|"AUCTION_CAN_BUY"|boolean|是否可一口价 <br>param1: 拍卖物品数据|```SL:GetMetaValue("AUCTION_CAN_BUY", item)```|
|"AUCTION_HAVE_MY_BIDDING"|boolean|是否有我的竞拍物品|```SL:GetMetaValue("AUCTION_HAVE_MY_BIDDING")```|
|"AUCTION_ITEM_STATE"|int, string|拍卖行物品状态<br>传入参数：拍卖物品数据<br>返回值两个：<br>value1：<br>&emsp; 0：未知<br>&emsp; 2：竞拍中<br>&emsp; 3：已超时，<br>value2：剩余时间|```SL:GetMetaValue("AUCTION_ITEM_STATE", itemData)```|
|"AUCTION_MY_SHOW_LIST"|table|获取拍卖行我的展示可寄售道具|`SL:GetMetaValue("AUCTION_MY_SHOW_LIST")`|支持版本号3.40.3以上|

### 好友
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"FRIEND_MAX_COUNT"|int|最大好友人数|```SL:GetMetaValue("FRIEND_MAX_COUNT")```|
|"FRIEND_INFO_BY_UID"|table|根据userID获取好友信息|```SL:GetMetaValue("FRIEND_INFO_BY_UID", userID)```|
|"FRIEND_INFO_BY_NAME"|table|根据userName获取好友信息|```SL:GetMetaValue("FRIEND_INFO_BY_NAME, userName")```|
|"SOCIAL_IS_FRIEND"|boolean|是否是好友|```SL:GetMetaValue("SOCIAL_IS_FRIEND")```|
|"SOCIAL_IS_BLICKLIST"|boolean|是否在黑名单|```SL:GetMetaValue("SOCIAL_IS_BLICKLIST")```|
|"FRIEND_LIST"|table|获取好友列表|```SL:GetMetaValue("FRIEND_LIST")```|
|"FRIEND_BLACKLIST"|table|获取黑名单数据|```SL:GetMetaValue("FRIEND_BLACKLIST")```|
|"FRIEND_APPLYLIST"|table|好友申请列表|```SL:GetMetaValue("FRIEND_APPLYLIST")```|
|"ADD_STATUS_PERMIT"|boolean|允许添加状态|```SL:GetMetaValue("ADD_STATUS_PERMIT")```|

### 行会
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"GUILD_MEMBER_LIST"|table|行会成员列表|```SL:GetMetaValue("GUILD_MEMBER_LIST")```|
|"GUILD_APPLY_LIST"|table|行会申请列表|```SL:GetMetaValue("GUILD_APPLY_LIST")```|
|"GUILD_ALLY_APPLY_LIST"|table|行会结盟申请列表|```SL:GetMetaValue("GUILD_ALLY_APPLY_LIST")```|
|"GUILD_WORLD_LIST"|table|获取世界行会列表 param1: 分页id|```SL:GetMetaValue("GUILD_WORLD_LIST", 1)```|
|"GUILD_WORLD_TOTAL_PAGES"|int|获取世界行会列表总页数|```SL:GetMetaValue("GUILD_WORLD_TOTAL_PAGES")```|
|"GUILD_CREATE"|table|获取创建公会消耗信息|```SL:GetMetaValue("GUILD_CREATE")```|
|"GUILD_INFO"|table|我的行会信息<br>rank: int -- 职位id<br>contribute: int --贡献<br>todayDonateGold: int --当天捐钱<br>isJoinGuild: boolean -- 是否加入行会<br>guildName: string --行会名称<br>guildId: int --行会id<br>isChairMan: boolean --是否是会长或者副会长|```SL:GetMetaValue("GUILD_INFO")```|
|"GUILD_OFFICIAL"|string|获取行会职位名称 param1: 职位id|```SL:GetMetaValue("GUILD_OFFICIAL", 1)```|
|"GUILD_MEMBER_INFO"|table|通过uid获取行会成员信息|```SL:GetMetaValue("GUILD_MEMBER_INFO", targetId)```|

### 面对面交易
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"TARGET_ID"|string|交易的目标ID|```SL:GetMetaValue("TARGET_ID")```|
|"TARGET_NAME"|string|交易的目标名字|```SL:GetMetaValue("TARGET_NAME")```|
|"TRADE_DATA"|table|要交易的玩家信息|```SL:GetMetaValue("TRADE_DATA")```|
|"TRADE_MY_LOCK_STATUS"|boolean|交易自己锁定状态|```SL:GetMetaValue("TRADE_MY_LOCK_STATUS")```|
|"TRADE_OTHER_LOCK_STATUS"|boolean|交易对方锁定状态|```SL:GetMetaValue("TRADE_OTHER_LOCK_STATUS")```|
|"DEAL_STATUS_PERMIT"|boolean|允许交易状态|```SL:GetMetaValue("DEAL_STATUS_PERMIT")```|支持版本号3.40.3以上|

### 排行榜
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"RANK_DATA_BY_TYPE"|table|根据页签index获取排行榜数据|```SL:GetMetaValue("RANK_DATA_BY_TYPE", index)```|

### 任务
|参数名|类型|说明|例子
|:----|:-----|-----|-----|
|"MISSION_ITEM_ORDER"|int|根据任务类型/ID获取任务排序值|```SL:GetMetaValue("MISSION_ITEM_ORDER", type)```|

### 技能
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"SKILL_INFO_FILTER"|table|筛选技能数据<br>param1：技能类型<br>param2：职业<br>param3：是否学习<br>param4：是否不是基础技能|```SL:GetMetaValue("SKILL_INFO_FILTER", param1, param2, param3, param4)```|
|"SKILL_NAME"|string|获取技能名字|```SL:GetMetaValue("SKILL_NAME", skillID)```|
|"SKILL_ICON_PATH"|string|获取技能图标|```SL:GetMetaValue("SKILL_ICON_PATH", skillID)```|
|"SKILL_RECT_ICON_PATH"|string|获取矩形技能图标|```SL:GetMetaValue("SKILL_RECT_ICON_PATH", skillID)```|
|"SKILL_IS_ONOFF_SKILL"|boolean|是否是开关型技能|```SL:GetMetaValue("SKILL_IS_ONOFF_SKILL", skillID)```|
|"SKILL_IS_ON_SKILL"|boolean|技能是否开启|```SL:GetMetaValue("SKILL_IS_ON_SKILL", skillID)```|
|"LEARNED_SKILLS"|table|获取已学技能<br>param1:是否排除普攻  <br>param2:是否只获取主动技能|```SL:GetMetaValue("LEARNED_SKILLS", true)```|
|"SKILL_IS_ACTIVE"|boolean|是否是主动技能|```SL:GetMetaValue("SKILL_IS_ACTIVE", skillID)```|
|"SKILL_DATA"|table|获取技能数据 <br>param1: 技能ID|```SL:GetMetaValue("SKILL_DATA", skillID) ```|
|"SKILL_TRAIN_DATA"|table|获取技能的等级熟练度数据 <br>param1: 技能ID |```SL:GetMetaValue("SKILL_TRAIN_DATA", skillID) ```|
|"SKILL_CONFIG"|table|获取技能配置 <br>param1: 技能ID|```SL:GetMetaValue("SKILL_CONFIG", skillID)```|
|"SKILL_KEY"|int|获取技能快捷键 <br>param1: 技能ID|```SL:GetMetaValue("SKILL_KEY", skillID) ```|
|"SKILL_LEVEL"|int|获取技能等级 <br>param1: 技能ID|```SL:GetMetaValue("SKILL_LEVEL", skillID)```|

### 背包
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"MAX_BAG"|int|背包最大格子数量|```SL:GetMetaValue("MAX_BAG")```|
|"H_MAX_BAG"|int|英雄背包最大格子数量|```SL:GetMetaValue("H_MAX_BAG")```|
|"N_MAX_BAG"|int|仓库最大格子数量|```SL:GetMetaValue("N_MAX_BAG")```|
|"BAG_PAGE_CUR"|int|当前选中的背包页签|```SL:GetMetaValue("BAG_PAGE_CUR")```|
|"BAG_IS_FULL"|boolean|背包是否满<br>param1: boolean 是否弹出提示|```SL:GetMetaValue("BAG_IS_FULL", param1)```|
|"BAG_REMAIN_COUNT"|int|背包剩余格子数|```SL:GetMetaValue("BAG_REMAIN_COUNT")```|
|"BAG_USED_COUNT"|int|背包已使用格子数|```SL:GetMetaValue("BAG_USED_COUNT")```|
|"BAG_CHECK_NEED_SPACE"|boolean|检测物品背包是否有富余格子数存放<br>param1: 物品ID <br>param2: 物品数量<br>param3: 不足时是否需要提示 boolean|`SL:GetMetaValue("BAG_CHECK_NEED_SPACE", 4, 11, true)`|支持版本号3.40.3以上|

### 内挂设置
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"SETTING_ENABLED"|int|设置是否生效<br>param1: 内挂设置index<br>返回值：0 或者 1|```SL:GetMetaValue("SETTING_ENABLED", param1)```|
|"SETTING_VALUE"|table|获取设置的数据<br>param1: 内挂设置index|```SL:GetMetaValue("SETTING_VALUE", param1)```|
|"SETTING_CONFIG"|table|获取设置的配置<br>param1: 内挂设置ID|```SL:GetMetaValue("SETTING_CONFIG", param1)```|
|"SETTING_PICK_VALUE"|table|获取物品拾取设置<br>param1: 内挂设置index|```SL:GetMetaValue("SETTING_PICK_VALUE", param1)```|
|"SETTING_PICK_CONFIG"|table|可以拣的物品配置<br>param1: 内挂设置index|```SL:GetMetaValue("SETTING_PICK_CONFIG", param1)```|
|"SETTING_IS_ITEM_PICK_CAN_SET"|table|物品是否可以设置|```SL:GetMetaValue("SETTING_IS_ITEM_PICK_CAN_SET")```|
|"SETTING_PICK_GROUP_VALUE"|table|拾取组的数据<br>param1: 内挂设置组ID|```SL:GetMetaValue("SETTING_PICK_GROUP_VALUE", param1)```|
|"MAPSCALE_PER"|int|通过值获取地图缩放对应百分比<br> param1: 地图缩放值|```SL:GetMetaValue("MAPSCALE_PER", param1)```|
|"MAPSCALE_VALUE"|int|通过百分比获取地图缩放值<br> param1:百分比|```SL:GetMetaValue("MAPSCALE_VALUE", param1)```|

### ItemTips
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"EQUIPMAP_BY_STDMODE"|table|装备Map|```SL:GetMetaValue("EQUIPMAP_BY_STDMODE")```|
|"EX_SHOWLAST_MAP"|table|除装备Map 显示持久的stdmode|```SL:GetMetaValue("EX_SHOWLAST_MAP")```|
|"EQUIP_POS_BY_STDMODE"|int|通过stdmode获取装备位<br>param1：装备的stdmode|```SL:GetMetaValue("EQUIP_POS_BY_STDMODE", param1)```|
|"EQUIP_POSLIST_BY_STDMODE"|table|通过stdmode获取装备位列表<br>param1：装备的stdmode<br>param2: 是否英雄|```SL:GetMetaValue("EQUIP_POSLIST_BY_STDMODE", param1)```|
|"TIP_POSLIST_BY_STDMODE"|table|通过stdmode获取TIPS装备位列表<br>param1：装备的stdmode<br>param2: 是否英雄|```SL:GetMetaValue("TIP_POSLIST_BY_STDMODE", param1)```|支持版本号3.40.3以上|
|"IS_SAMESEX_EQUIP"|boolen|是否是该玩家性别装备<br>param1：装备数据<br>param2: 是否英雄|```SL:GetMetaValue("IS_SAMESEX_EQUIP", param1)```|
|"CUSTOM_DESC"|string|对cfg_custpro_caption操作<br>根据key获取描述<br>param1：表中的key|```SL:GetMetaValue("CUSTOM_DESC", param1)```|
|"CUSTOM_ICON"|string|对cfg_custpro_caption操作<br>根据key获取图片id<br>param1：表中的key|```SL:GetMetaValue("CUSTOM_ICON", param1)```|
|"ATTR_CONFIG"|string|对cfg_att_score表操作<br>获取属性配置<br>param1：表中的key|```SL:GetMetaValue("ATTR_CONFIG", param1)```|
|"SUIT_CONFIG"|string|对cfg_suit表操作<br> 获取对应套装id配置<br>param1：表中的suitid|```SL:GetMetaValue("SUIT_CONFIG", param1)```|
|"SUITEX_CONFIG"|string|对cfg_suitex表操作<br> 获取对应套装id配置<br>param1：表中的suitid|```SL:GetMetaValue("SUITEX_CONFIG", param1)```|
|"ITEMFROMUI_ENUM"|table|物品来自UI,返回值如下：data |```SL:GetMetaValue("ITEMFROMUI_ENUM")```|
```
data = {
    BAG                  = 1,          -- 背包
    PALYER_EQUIP         = 2,          -- 玩家身上
    QUICK_USE            = 3,          -- 快捷栏
    STORAGE              = 4,          -- 仓库
    BAG_GOLD             = 5,          -- 背包金币
    SELL                 = 6,          -- 摆摊
    REQUIRE              = 7,          -- npc商店
    TRADE                = 8,          -- 面对面交易
    STALL                = 9,
    TRADE_GOLD           = 10,         -- 交易
    BEST_RINGS           = 11,         -- 极品首饰
    AUTO_TRADE           = 12,         -- 摆摊
    ITEMBOX              = 13,         -- 自定义UI ITEMBOX
    NPC_DO_SOMETHING     = 14,         -- NPC自定义放入框
    NEWTYPE              = 15,
    HERO_BAG             = 66,         -- 英雄背包
    HERO_EQUIP           = 67,         -- 英雄装备
    HERO_BEST_RINGS      = 68,         -- 英雄极品首饰
    SSR_ITEM_BOX         = 77,         -- ssr 自定义ItemBox
    PETS_EQUIP           = 78,         -- 宠物装备
    SKILL_WIN            = 79,         -- PC 技能
    OTHER                = 99          -- 其他
}
```
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"ITEMTYPE_ENUM"|table|物品类型，返回值如下：data |```SL:GetMetaValue("ITEMTYPE_ENUM")```|

`此分类依据【道具表】和【装备表】中的 StdMode`
```
data = {
    DruaAndSomething = 1,       -- 道具表 StdMode 0~3 的道具
    SkillBook        = 2,       -- 技能书 道具表 StdMode 4  的道具
    Equip            = 3,       -- 装备
    Bundle           = 4,       -- 困束  道具表 StdMode 31  的道具
    Box              = 5,       -- 盒子  道具表 StdMode 200 的道具
    TreasureMap      = 6,       -- StdMode 为 101 的道具
    FashionItem      = 7,       -- 时装道具  道具表 StdMode 102 的道具
    MonsterCard      = 8,       -- 怪物卡片  道具表 StdMode 103 的道具
    SomethingCanUse  = 9,       -- 道具表 StdMode 为 49 的道具
    BoxKey           = 10,      -- 箱子钥匙  道具表 StdMode 40 的道具
    Collimator       = 11,      -- 准星道具  道具表 StdMode 47 的道具
    WishBox          = 12,      -- StdMode 为 96 的道具
    NewPet           = 13,      -- 宠物道具 道具表 StdMode 201 的道具
    Other            = 99       -- 其他
}
```
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"ITEMTYPE"|int|根据道具数据获取物品类型 |```SL:GetMetaValue("ITEMTYPE", itemData)```|
|"CUST_ABIL_MAP"|table|自定义属性ID映射Map|`SL:GetMetaValue("CUST_ABIL_MAP")`|支持版本号3.40.5以上|

### 充值
|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|-----|
|"RECHARGE_PRODUCTS"|table|充值商品信息列表|```SL:GetMetaValue("RECHARGE_PRODUCTS")```|支持版本号3.40.3以上|
|"RECHARGE_PRODUCT_BY_ID"|table|通过商品Id获取商品信息|```SL:GetMetaValue("RECHARGE_PRODUCT_BY_ID", id)```|支持版本号3.40.3以上|
|"IS_SDK_PAY"|boolean|是否接入第三方SDK|```SL:GetMetaValue("IS_SDK_PAY")```|支持版本号3.40.3以上|

### 摆摊
|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|
|"ONSELL_DATA_BY_MAKEINDEX"|table|获取购买摊位的对应物品信息<br>param1: 物品唯一ID |```SL:GetMetaValue("ONSELL_DATA_BY_MAKEINDEX", makeIndex)```|支持版本号3.40.3以上|
|"MYSELL_DATA_BY_MAKEINDEX"|table|获取我的摊位的对应物品信息<br>param1: 物品唯一ID |```SL:GetMetaValue("MYSELL_DATA_BY_MAKEINDEX", makeIndex)```|支持版本号3.40.3以上|
|"SELL_SHOW_NAME"|string|获取购买摊位名字|```SL:GetMetaValue("SELL_SHOW_NAME", makeIndex)```|支持版本号3.40.3以上|
|"ONSELL_DATA"|table|获取购买摊位物品信息 |```SL:GetMetaValue("ONSELL_DATA")```|支持版本号3.40.3以上|
|"MYSELL_DATA"|table|获取我的摊位物品信息 |```SL:GetMetaValue("MYSELL_DATA")```|支持版本号3.40.3以上|

### 宝箱
|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|
|"HAVE_GOLDBOX_OPENTIME"|boolean|是否还有重摇/开启次数|`SL:GetMetaValue("HAVE_GOLDBOX_OPENTIME")`|支持版本号3.40.3以上|

### 合成
|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|
|"COMPOUND_OPEN_ID"|int|获取合成打开的ID （合成表id） |`SL:GetMetaValue("COMPOUND_OPEN_ID")`|支持版本号3.40.3以上|
|"COMPOUND_CONFIG_BY_INDEX"|table|通过id获取合成对应配置 <br>param1: 合成表id|`SL:GetMetaValue("COMPOUND_CONFIG_BY_INDEX", id)`|支持版本号3.40.3以上|
|"COMPOUND_PAGE_BY_ID"|int|通过id获取合成页签组合id [合成表page1 * 1000 + 合成表page2] <br> param1: 合成表id|`SL:GetMetaValue("COMPOUND_PAGE_BY_ID", id)`|支持版本号3.40.3以上|
|"COMPOUND_LIST_DATA"|table|获取合成数据|`SL:GetMetaValue("COMPOUND_LIST_DATA")`|支持版本号3.40.3以上|
|"COMPOUND_LIST_DATA_BY_INDEX"|table|通过id获取合成数据<br> param1: 合成表page1 * 1000 + 合成表page2 |`SL:GetMetaValue("COMPOUND_LIST_DATA_BY_INDEX", id)`|支持版本号3.40.3以上|
|"COMPOUND_CHECK_LIST_IS_SHOW"|boolean|检测该合成页签是否显示<br> param1: 合成表page1 <br>param2: 合成表page1 * 1000 + 合成表page2|`SL:GetMetaValue("COMPOUND_CHECK_LIST_IS_SHOW", page1)`|支持版本号3.40.3以上|
|"COMPOUND_CHECK_LIST_RED_POINT"|boolean|检测合成红点<br> param1: 合成表page1 <br> param2: 合成表page1 * 1000 + 合成表page2 |`SL:GetMetaValue("COMPOUND_CHECK_LIST_RED_POINT", page1)`|支持版本号3.40.3以上|
|"COMPOUND_PAGE_NAME"|string|获取合成页签名字<br> param1: 合成表page1 * 1000 + 合成表page2 |`SL:GetMetaValue("COMPOUND_PAGE_NAME", page1)`|支持版本号3.40.3以上|
|"COMPOUND_SHOW_CONDITION"|boolean|判断合成条件是否显示红点<br> param1: 条件配置 string|`SL:GetMetaValue("COMPOUND_SHOW_CONDITION", conditionStr)`|支持版本号3.40.3以上|
|"COMPOUND_RED_POINT_BY_ID"|boolean|获取合成红点状态<br> param1: 合成表id|`SL:GetMetaValue("COMPOUND_RED_POINT_BY_ID", id)`|支持版本号3.40.3以上|
|"COMPOUND_CHECK_OK"|boolean|检查是否可以合成<br> param1: 合成配置 table<br>param2: 是否提示 boolean|`SL:GetMetaValue("COMPOUND_PAGE_NAME", page2)`|支持版本号3.40.3以上|

### 新版属性加点 [3.40.4]
|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|
|"IS_NEW_BOUNS"|boolean|是否启用新版属性加点|`SL:GetMetaValue("IS_NEW_BOUNS")`|支持版本号3.40.4以上|
|"NEW_BOUNS_CONFIG"|table|获取新版属性加点配置数据|`SL:GetMetaValue("NEW_BOUNS_CONFIG")`|支持版本号3.40.4以上|
|"NEW_BOUNS_ADD_DATA"|table|获取新版属性已加点数据|`SL:GetMetaValue("NEW_BOUNS_ADD_DATA")`|支持版本号3.40.4以上|

### 求购系统 [3.40.5]
* 求购菜单配置 等同 拍卖行配置 (cfg_auction_type)

|参数名|返回值类型|说明|例子|版本|
|:----|:-----|-----|-----|
|"PURCHASE_FILTER_LIST"|table|世界求购菜单列表|`SL:GetMetaValue("PURCHASE_FILTER_LIST")`|支持版本号3.40.5以上|
|"PURCHASE_MENU_CONFIG_BY_ID"|table|对应ID 菜单栏配置|`SL:GetMetaValue("PURCHASE_MENU_CONFIG_BY_ID", id)`|支持版本号3.40.5以上|
|"PURCHASE_ITEM_LIST_BY_TYPE"|table|分类物品列表 param1: 一级菜单id param2: 二级菜单id|`SL:GetMetaValue("PURCHASE_ITEM_LIST_BY_TYPE", 2, 1)`|支持版本号3.40.5以上|
|"PURCHASE_CURRENCIES"|table|求购货币列表|`SL:GetMetaValue("PURCHASE_CURRENCIES")`|支持版本号3.40.5以上|

### 角色相关
|参数名|返回值类型|说明|例子
|:----|:-----|-----|-----|
|"USER_ID"|string|玩家ID|```SL:GetMetaValue("USER_ID")```|
|"USER_NAME"|string|玩家名字|```SL:GetMetaValue("USER_NAME")```|
|"JOB"|int|玩家职业<br>0：战士<br>1：法师<br>2：道士|```SL:GetMetaValue("JOB")```|
|"LEVEL"|int|玩家等级|```SL:GetMetaValue("LEVEL")```|
|"RELEVEL"|int|玩家转生等级|```SL:GetMetaValue("RELEVEL")```|
|"JOB_NAME"|string|职业名字|```SL:GetMetaValue("JOB_NAME")```|
|"SEX"|int|玩家性别<br>0：男<br>1：女|```SL:GetMetaValue("SEX")```|
|"REAL_USER_NAME"|string|玩家真实姓名|```SL:GetMetaValue("REAL_USER_NAME")```|
|"USER_NAME_COLOR"|int|玩家名字颜色值|```SL:GetMetaValue("USER_NAME_COLOR")```|
|"DIR"|int|人物方向<br>0：上<br>1：右上<br>2：右<br>3：右下<br>4：下<br>5：左下<br>6：左<br>7：左上<br>0xff：无效位置|```SL:GetMetaValue("DIR")```|
|"USER_IS_DIE"|boolean|角色是否死亡|```SL:GetMetaValue("USER_IS_DIE")```|
|"USER_IS_CANREVIVE"|boolean|角色是否能复活|```SL:GetMetaValue("USER_IS_DIE")```|支持版本号3.40.3以上|
|"HP"|int|当前血量|```SL:GetMetaValue("HP")```|
|"MAXHP"|string|最大血量|```SL:GetMetaValue("MAXHP")```|
|"MP"|int|当前蓝量|```SL:GetMetaValue("MP")```|
|"MAXMP"|string|最大蓝量|```SL:GetMetaValue("MAXMP")```|
|"BURST"|int|暴击几率|```SL:GetMetaValue("BURST")```|
|"BURST_DAM"|int|暴击伤害|```SL:GetMetaValue("BURST_DAM")```|
|"IMM_ATT"|int|物伤减免|```SL:GetMetaValue("IMM_ATT")```|
|"IMM_MAG"|int|魔伤减免|```SL:GetMetaValue("IMM_MAG")```|
|"DROP"|int|怪物爆率|```SL:GetMetaValue("DROP")```|
|"LUCK"|int|幸运|```SL:GetMetaValue("LUCK")```|
|"AC"|int|最小物防|```SL:GetMetaValue("AC")```|
|"MAXAC"|int|最大物防|```SL:GetMetaValue("MAXAC")```|
|"MAC"|int|最小魔防|```SL:GetMetaValue("MAC")```|
|"MAXMAC"|int|最大魔防|```SL:GetMetaValue("MAXMAC")```|
|"DC"|int|最小物理|```SL:GetMetaValue("DC")```|
|"MAXDC"|int|最大物理|```SL:GetMetaValue("MAXDC")```|
|"MC"|int|最小魔法|```SL:GetMetaValue("MC")```|
|"MAXMC"|int|最大魔法|```SL:GetMetaValue("MAXMC")```|
|"SC"|int|最小道术|```SL:GetMetaValue("SC")```|
|"MAXSC"|int|最大道术|```SL:GetMetaValue("MAXSC")```|
|"HIT"|int|准确|```SL:GetMetaValue("HIT")```|
|"SPD"|int|敏捷|```SL:GetMetaValue("SPD")```|
|"EXP"|int|当前经验|```SL:GetMetaValue("EXP")```|
|"MAXEXP"|int|最大经验|```SL:GetMetaValue("MAXEXP")```|
|"HITSPD"|int|攻速|```SL:GetMetaValue("HITSPD")```|
|"HW"|int|腕力|```SL:GetMetaValue("HW")```|
|"MAXHW"|int|最大可穿戴腕力|```SL:GetMetaValue("MAXHW")```|
|"BW"|int|重量|```SL:GetMetaValue("BW")```|
|"MAXBW"|int|玩家最大负重|```SL:GetMetaValue("MAXBW")```|
|"WW"|int|穿戴负重|```SL:GetMetaValue("WW")```|
|"MAXWW"|int|最大穿戴负重|```SL:GetMetaValue("MAXWW")```|
|"HUNGER"|int|体力恢复|```SL:GetMetaValue("HUNGER")```|
|"LUCK"|int|幸运值|```SL:GetMetaValue("LUCK")```|支持版本号3.40.3以上|
|"DRESS"|string|获取玩家身上衣服的名字|```SL:GetMetaValue("DRESS")```|
|"WEAPON"|string|获取玩家身上武器的名字|```SL:GetMetaValue("WEAPON")```|
|"RIGHTHAND"|string|获取玩家身上勋章的名字|```SL:GetMetaValue("RIGHTHAND")```|
|"HELMET"|string|获取玩家身上头盔的名字|```SL:GetMetaValue("HELMET")```|
|"NECKLACE"|string|获取玩家身上项链的名字|```SL:GetMetaValue("NECKLACE")```|
|"RINGR"|string|获取玩家身上右戒指的名字|```SL:GetMetaValue("RINGR")```|
|"RINGL"|string|获取玩家身上左戒指的名字|```SL:GetMetaValue("RINGL")```|
|"ARMRINGR|string|获取玩家身上右手镯的名字|```SL:GetMetaValue("ARMRINGR"")```|
|"ARMRINGL"|string|获取玩家身上左手镯的名字|```SL:GetMetaValue("ARMRINGL")```|
|"BUJUK"|string|获取玩家身上护符、玉佩、宝珠的名字|```SL:GetMetaValue("BUJUK")```|
|"BELT"|string|获取玩家身上腰带的名字|```SL:GetMetaValue("BELT")```|
|"BOOTS"|string|获取玩家身上鞋子的名字|```SL:GetMetaValue("BOOTS")```|
|"CHARM"|string|获取玩家身上宝石的名字|```SL:GetMetaValue("CHARM")```|
|"EQUIPBYPOS"|string|获取玩家某一装备位的装备名|```SL:GetMetaValue("EQUIPBYPOS", 1)```|
|"EX_ATTR"|string|脚本变量额外属性|```SL:GetMetaValue("EX_ATTR")```|
|"ATT_BY_TYPE"|int|根据类型id获取属性值|```SL:GetMetaValue("ATT_BY_TYPE", 94)```|
|"EQUIP_DATA"|table|获取玩家某一装备数据 <br>param1: 装备位id 或者 装备名称  param2: 是否多个装备位共享|```SL:GetMetaValue("EQUIP_DATA", 30)```|
|"EQUIP_DATA_LIST"|table|获取玩家对应装备位数据列表 <br>param1: 装备位id|```SL:GetMetaValue("EQUIP_DATA_LIST", 30)```|支持版本号3.40.8以上|
|"EMBATTLE"|table|获取玩家法阵数据 |```SL:GetMetaValue("EMBATTLE")```|支持版本号3.40.8以上|
|"FEATURE"|table|玩家外观数据|```SL:GetMetaValue("FEATURE")```|
|"HAIR"|int|发型ID|```SL:GetMetaValue("HAIR")```|
|"EQUIP_POS_DATAS"|table|获取装备位对应MakeIndex数据|```SL:GetMetaValue("EQUIP_POS_DATAS")```|
|"TITLES"|table|玩家的称号数据|```SL:GetMetaValue("TITLES")```|
|"TITLE_DATA_BY_ID"|table|获取玩家对应ID的称号数据|```SL:GetMetaValue("TITLE_DATA_BY_ID", id)```|支持版本号3.40.3以上|
|"ACTIVATE_TITLE"|int|玩家激活的称号id|```SL:GetMetaValue("ACTIVATE_TITLE")```|
|"INTERNAL_FORCE"|int|人物内功当前内力值|```SL:GetMetaValue("INTERNAL_FORCE")```|支持版本号3.40.2以上|
|"INTERNAL_MAXFORCE"|int|人物内功最大内力值|```SL:GetMetaValue("INTERNAL_MAXFORCE")```|支持版本号3.40.2以上|
|"INTERNAL_EXP"|int|人物内功当前经验值|```SL:GetMetaValue("INTERNAL_EXP")```|支持版本号3.40.2以上|
|"INTERNAL_MAXEXP"|int|人物内功最大经验值|```SL:GetMetaValue("INTERNAL_MAXEXP")```|支持版本号3.40.2以上|
|"INTERNAL_LEVEL"|int|人物内功等级|```SL:GetMetaValue("INTERNAL_LEVEL")```|支持版本号3.40.2以上|
|"INTERNAL_DZ_CURVALUE"|int|人物内功当前斗转星移值|```SL:GetMetaValue("INTERNAL_DZ_CURVALUE")```|支持版本号3.40.2以上|
|"INTERNAL_DZ_MAXVALUE"|int|人物内功最大斗转星移值|```SL:GetMetaValue("INTERNAL_DZ_MAXVALUE")```|支持版本号3.40.2以上|
|"INTERNAL_SKILLS"|table|获取人物拥有内功技能列表|```SL:GetMetaValue("INTERNAL_SKILLS")```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_DATA"|table|获取人物内功技能数据<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_DATA", skillID, skillType)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_TRAIN_DATA"|table|获取人物内功技能等级熟练度数据<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_TRAIN_DATA", skillID, skillType)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_ONOFF"|int|获取人物内功技能开关<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_ONOFF", skillID, skillType)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_RECT_ICON_PATH"|string|获取人物内功技能矩形图标路径<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_RECT_ICON_PATH", skillID, skillType)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_NAME"|table|获取人物内功技能名字<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_NAME", skillID, skillType)```|支持版本号3.40.2以上|
|"INTERNAL_SKILL_DESC"|table|获取人物内功技能描述<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_DESC", skillID, skillType)```|支持版本号3.40.2以上|
|"MERIDIAN_DESC"|table|获取人物内功经络的穴位描述|```SL:GetMetaValue("MERIDIAN_DESC")```|支持版本号3.40.2以上|
|"MERIDIAN_AUCPOINT_STATE"|table|获取人物内功对应经络的穴位是否激活列表<br>param1: 经络ID|```SL:GetMetaValue("MERIDIAN_AUCPOINT_STATE", 2)```|支持版本号3.40.2以上|
|"MERIDIAN_OPEN_LIST"|table|获取人物内功经络的开关列表|```SL:GetMetaValue("MERIDIAN_OPEN_LIST")```|支持版本号3.40.2以上|
|"MERIDIAN_LV"|int|获取人物内功对应经络等级|```SL:GetMetaValue("MERIDIAN_LV", 2)```|支持版本号3.40.2以上|
|"HAVE_COMBO_SKILLS"|table|获取人物所有拥有的连击技能|```SL:GetMetaValue("HAVE_COMBO_SKILLS")```|支持版本号3.40.2以上|
|"COMBO_SKILL_DATA"|table|获取人物对应连击技能<br> param1: 技能ID|```SL:GetMetaValue("COMBO_SKILL_DATA", 104)```|支持版本号3.40.2以上|
|"COMBO_SKILL_TRAIN_DATA"|table|获取人物连击技能等级熟练度数据<br>param1: 技能ID |```SL:GetMetaValue("COMBO_SKILL_TRAIN_DATA", skillID)```|支持版本号3.40.2以上|
|"SET_COMBO_SKILLS"|table|获取人物设置为连击的数据|```SL:GetMetaValue("SET_COMBO_SKILLS")```|支持版本号3.40.2以上|
|"OPEN_COMBO_NUM"|int|人物开启的连击个数|```SL:GetMetaValue("OPEN_COMBO_NUM")```|支持版本号3.40.2以上|
|"IS_LEARNED_INTERNAL"|boolean|人物是否学习内功|```SL:GetMetaValue("IS_LEARNED_INTERNAL")```|支持版本号3.40.2以上|
|"EXTRA_COMBO_BJRATE"|int|获取对应连击格子额外加暴击几率<br>param1: 连击格子index(1-4)|`SL:GetMetaValue("EXTRA_COMBO_BJRATE", 1)`|支持版本号3.40.3以上|
|"RUN_STEP"|int|跑步移动格子数|`SL:GetMetaValue("RUN_STEP")`|支持版本号3.40.3以上|
|"CAN_RUN_ABLE"|boolean|能否跑|`SL:GetMetaValue("CAN_RUN_ABLE")`|支持版本号3.40.3以上|
|"LOOK_USER_ID"|string|当前查看他人角色ID|```SL:GetMetaValue("LOOK_USER_ID")```|
|"LOOK_USER_NAME"|string|当前查看他人角色名字|```SL:GetMetaValue("LOOK_USER_NAME")```|
|"LOOK_USER_NAME_COLOR"|int|当前查看他人角色名字颜色ID|```SL:GetMetaValue("LOOK_USER_NAME_COLOR")```|
|"PLAYER_INITED"|boolean|玩家属性初始化完成|`SL:GetMetaValue("PLAYER_INITED")`|支持版本号3.40.7以上|

### 其他角色相关
|参数名|返回值类型|说明|
|:----|:-----|-----|
|L.M.JOB|int|当前查看玩家职业|
|L.M.HAIR|int|当前查看玩家发型|
|L.M.LEVEL|int|当前查看玩家等级|
|L.M.SEX|int|当前查看玩家性别|
|L.M.PLAYER_DATA|table|当前查看玩家数据|
|L.M.EQUIP_DATA|table|当前查看玩家某个装备位数据 param1: 装备位id 或者 装备名称|
|L.M.EQUIP_DATA_LIST|table|当前查看玩家某个装备位数据列表 param1: 装备位id|支持版本号3.40.8以上|
|L.M.EQUIP_POS_DATAS|table|当前查看玩家的所有装备位数据|
|L.M.GUILD_INFO|table|当前查看玩家的行会信息|
|L.M.TITLES|table|当前查看玩家的称号数据|
|L.M.ACTIVATE_TITLE|int|当前查看玩家激活的称号id|
|L.M.EMBATTLE|table|当前查看玩家法阵数据|支持版本号3.40.8以上|

### 英雄相关
|参数名|返回值类型|说明|
|:----|:----- |-----|
|H.USERNAME|string|英雄名字|
|H.LEVEL|int|英雄等级|
|H.RELEVEL|int|转生等级|
|H.EXP|int|当前经验|
|H.MAXEXP|int|最大经验|
|H.JOBNAME|string|职业名称|
|H.JOB|int|职业|
|H.SEX|int|性别|
|H.HAIR|int|发型ID|
|H.MAXHP|int|最大生命值|
|H.MAXMP|int|最大魔法值|
|H.HP|int|当前生命值|
|H.MP|int|当前魔法值|
|H.HPPercent|int|当前血量百分比|
|H.MPPercent|int|当前蓝量百分比|
|H.EXPPercent|int|当前经验百分比|
|H.MIN_ATK|int|攻击下限|
|H.MAX_ATK|int|攻击上限|
|H.MIN_MAT|int|魔攻下限|
|H.MAX_MAT|int|魔攻上限|
|H.MIN_DAO|int|道术下限|
|H.MAX_DAO|int|道术上限|
|H.MIN_DEF|int|物防下限|
|H.MAX_DEF|int|物防上限|
|H.MIN_MDF|int|魔防下限|
|H.MAX_MDF|int|魔防上限|
|H.HIT|int|命中|
|H.HITSPD|int|攻击速度|
|H.BURST|int|暴击几率|
|H.BURST_DAM|int|暴击伤害|
|H.IMM_ATT|int|物伤减免|
|H.IMM_MAG|int|魔伤减免|
|H.IGN_DEF|int|物理穿透|
|H.SUCK_HP|int|吸血|
|H.LUCK|int|幸运|
|H.DROP|int|怪物爆率|
|H.BW|int| 当前重量|
|H.MAXBW|int|英雄最大负重|
|H.WW|int| 穿戴负重|
|H.MAXWW|int| 最大穿戴负重|
|H.HW|int|腕力|
|H.MAXHW|int|当前最大可穿戴腕力|
|H.ANGER|int|当前愤怒|
|H.MAXANGER|int|最大愤怒|
|H.SHAN|boolen|英雄怒气值是否满|
|H.SPEED|int|单次怒气增加值|
|H.DELAYT|int|怒气增加间隔时间|
|H.EQUIP_DATA|table|获取英雄某一装备数据 <br>param1: 装备位id 或者 装备名称  param2: 是否多个装备位共享|
|H.EQUIP_DATA_LIST|table|获取英雄对应装备位数据列表 <br>param1: 装备位id|```SL:GetMetaValue("H.EQUIP_DATA_LIST", 12)```|支持版本号3.40.8以上|
|H.EMBATTLE|table|获取英雄法阵数据 |```SL:GetMetaValue("H.EMBATTLE")```|支持版本号3.40.8以上|
|H.EQUIP_POS_DATAS|table|获取装备位对应MakeIndex数据|
|H.TITLES|table|英雄的称号数据|
|H.ACTIVATE_TITLE|int|英雄激活的称号id|
|H.SKILL_TRAIN_DATA|table|获取技能的等级熟练度数据 <br>param1: 技能ID |
|H.SKILL_DATA|table|获取技能数据 param1: 技能ID|
|H.SKILL_NAME|string|获取技能名 param1: 技能ID|
|H.SKILL_KEY|int|获取技能快捷键 param1: 技能ID|
|H.LEARNED_SKILLS|table|获取已有技能数据 <br>param1:是否排除普攻  <br>param2:是否只获取主动技能|
|"H.INTERNAL_FORCE"|int|英雄内功当前内力值|```SL:GetMetaValue("INTERNAL_FORCE")```|支持版本号3.40.2以上|
|"H.INTERNAL_MAXFORCE"|int|英雄内功最大内力值|```SL:GetMetaValue("INTERNAL_MAXFORCE")```|支持版本号3.40.2以上|
|"H.INTERNAL_EXP"|int|英雄内功当前经验值|```SL:GetMetaValue("INTERNAL_EXP")```|支持版本号3.40.2以上|
|"H.INTERNAL_MAXEXP"|int|英雄内功最大经验值|```SL:GetMetaValue("INTERNAL_MAXEXP")```|支持版本号3.40.2以上|
|"H.INTERNAL_LEVEL"|int|英雄内功等级|```SL:GetMetaValue("INTERNAL_LEVEL")```|支持版本号3.40.2以上|
|"H.INTERNAL_DZ_CURVALUE"|int|英雄内功当前斗转星移值|```SL:GetMetaValue("INTERNAL_DZ_CURVALUE")```|支持版本号3.40.2以上|
|"H.INTERNAL_DZ_MAXVALUE"|int|英雄内功最大斗转星移值|```SL:GetMetaValue("INTERNAL_DZ_MAXVALUE")```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILLS"|table|获取英雄拥有内功技能列表|```SL:GetMetaValue("INTERNAL_SKILLS")```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_DATA"|table|获取英雄内功技能数据<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_DATA", skillID, skillType)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_TRAIN_DATA"|table|获取英雄内功技能等级熟练度数据<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_TRAIN_DATA", skillID, skillType)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_ONOFF"|int|获取英雄内功技能开关<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_ONOFF", skillID, skillType)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_RECT_ICON_PATH"|string|获取英雄内功技能矩形图标路径<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_RECT_ICON_PATH", skillID, skillType)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_NAME"|table|获取英雄内功技能名字<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_NAME", skillID, skillType)```|支持版本号3.40.2以上|
|"H.INTERNAL_SKILL_DESC"|table|获取英雄内功技能描述<br>param1: 技能ID <br>param2: 技能类型|```SL:GetMetaValue("INTERNAL_SKILL_DESC", skillID, skillType)```|支持版本号3.40.2以上|
|"H.MERIDIAN_AUCPOINT_STATE"|table|获取英雄内功对应经络的穴位是否激活列表<br>param1: 经络ID|```SL:GetMetaValue("MERIDIAN_AUCPOINT_STATE", 2)```|支持版本号3.40.2以上|
|"H.MERIDIAN_OPEN_LIST"|table|获取英雄内功经络的开关列表|```SL:GetMetaValue("MERIDIAN_OPEN_LIST")```|支持版本号3.40.2以上|
|"H.MERIDIAN_LV"|int|获取英雄内功对应经络等级|```SL:GetMetaValue("MERIDIAN_LV", 2)```|支持版本号3.40.2以上|
|"H.HAVE_COMBO_SKILLS"|table|获取英雄所有拥有的连击技能|```SL:GetMetaValue("H.HAVE_COMBO_SKILLS")```|支持版本号3.40.2以上|
|"H.COMBO_SKILL_DATA"|table|获取英雄对应连击技能<br> param1: 技能ID|```SL:GetMetaValue("H.COMBO_SKILL_DATA", 104)```|支持版本号3.40.2以上|
|"H.COMBO_SKILL_TRAIN_DATA"|table|获取英雄连击技能等级熟练度数据<br>param1: 技能ID |```SL:GetMetaValue("H.COMBO_SKILL_TRAIN_DATA", skillID)```|支持版本号3.40.2以上|
|"H.SET_COMBO_SKILLS"|table|获取英雄设置为连击的数据|```SL:GetMetaValue("H.SET_COMBO_SKILLS")```|支持版本号3.40.2以上|
|"H.OPEN_COMBO_NUM"|int|英雄开启的连击个数|```SL:GetMetaValue("H.OPEN_COMBO_NUM")```|支持版本号3.40.2以上|
|"H.IS_LEARNED_INTERNAL"|boolean|英雄是否学习内功|```SL:GetMetaValue("H.IS_LEARNED_INTERNAL")```|支持版本号3.40.2以上|
|"H.SKILL_ICON_PATH"|string|获取英雄技能图标|```SL:GetMetaValue("H.SKILL_ICON_PATH", skillID)```|支持版本号3.40.5以上|
|"H.SKILL_RECT_ICON_PATH"|string|获取英雄矩形技能图标|```SL:GetMetaValue("H.SKILL_RECT_ICON_PATH", skillID)```|支持版本号3.40.5以上|
|"HERO_INITED"|boolean|英雄属性初始化完成|`SL:GetMetaValue("HERO_INITED")`|支持版本号3.40.7以上|
|"H.LOCK_TARGET_ID"|int|英雄锁定ActorID|`SL:GetMetaValue("H.LOCK_TARGET_ID")`|支持版本号3.40.7以上|

### 交易行角色
|参数名|返回值类型|说明||
|:----|:----- |-----||
|T.M.USERNAME|string|玩家名字|
|T.M.LEVEL|int|玩家等级|
|T.M.RELEVEL|int|转生等级|
|T.M.EXP|int|当前经验|
|T.M.MAXEXP|int|最大经验|
|T.M.JOB|int|职业|
|T.M.SEX|int|性别|
|T.M.HAIR|int|发型ID|
|T.M.MAXHP|int|最大生命值|
|T.M.MAXMP|int|最大魔法值|
|T.M.HP|int|当前生命值|
|T.M.MP|int|当前魔法值|
|T.M.MIN_ATK|int|攻击下限|
|T.M.MAX_ATK|int|攻击上限|
|T.M.MIN_MAT|int|魔攻下限|
|T.M.MAX_MAT|int|魔攻上限|
|T.M.MIN_DAO|int|道术下限|
|T.M.MAX_DAO|int|道术上限|
|T.M.MIN_DEF|int|物防下限|
|T.M.MAX_DEF|int|物防上限|
|T.M.MIN_MDF|int|魔防下限|
|T.M.MAX_MDF|int|魔防上限|
|T.M.HIT|int|命中|
|T.M.HITSPD|int|攻击速度|
|T.M.BURST|int|暴击几率|
|T.M.BURST_DAM|int|暴击伤害|
|T.M.IMM_ATT|int|物伤减免|
|T.M.IMM_MAG|int|魔伤减免|
|T.M.SUCK_HP|int|吸血|
|T.M.LUCK|int|幸运|
|T.M.DROP|int|怪物爆率|
|T.M.BW|int| 当前重量|
|T.M.MAXBW|int|玩家最大负重|
|T.M.WW|int| 穿戴负重|
|T.M.MAXWW|int| 最大穿戴负重|
|T.M.HW|int|腕力|
|T.M.MAXHW|int|当前最大可穿戴腕力|
|T.M.USERNAME_COLOR|int|玩家名字颜色值|
|T.M.TITLES|table|玩家的称号数据|
|T.M.ACTIVATE_TITLE|int|当前查看玩家激活的称号id|
|T.M.SKILL_TRAIN_DATA|table|获取技能的等级熟练度数据 <br>param1: 技能ID |
|T.M.SKILL_DATA|table|获取技能数据 param1: 技能ID|
|T.M.LEARNED_SKILLS|table|获取已有技能数据 <br>param1:是否排除普攻  <br>param2:是否只获取主动技能|
|T.M.ATT_BY_TYPE|int|根据类型ID获取属性值 <br>param1: 类型ID|
|T.M.EQUIP_POS_DATAS|table|当前查看玩家的所有装备位数据|
|T.M.GUILD_INFO|table|当前查看玩家的行会信息|
|T.M.EQUIP_DATA|table|获取当前查看玩家对应装备位的装备数据|
|T.M.EQUIP_DATA_LIST|table|获取当前查看玩家对应装备位的装备数据列表|支持版本号3.40.8以上|
|T.M.EQUIP_DATA_BY_MAKEINDEX|table|通过MakeIndex获取查看交易行他人装备数据|支持版本号3.40.8以上|

### 交易行英雄
|参数名|返回值类型|说明|
|:----|:----- |-----|
|T.H.USERNAME|string|英雄名字|
|T.H.LEVEL|int|英雄等级|
|T.H.RELEVEL|int|转生等级|
|T.H.EXP|int|当前经验|
|T.H.MAXEXP|int|最大经验|
|T.H.JOB|int|职业|
|T.H.SEX|int|性别|
|T.H.HAIR|int|发型ID|
|T.H.MAXHP|int|最大生命值|
|T.H.MAXMP|int|最大魔法值|
|T.H.HP|int|当前生命值|
|T.H.MP|int|当前魔法值|
|T.H.MIN_ATK|int|攻击下限|
|T.H.MAX_ATK|int|攻击上限|
|T.H.MIN_MAT|int|魔攻下限|
|T.H.MAX_MAT|int|魔攻上限|
|T.H.MIN_DAO|int|道术下限|
|T.H.MAX_DAO|int|道术上限|
|T.H.MIN_DEF|int|物防下限|
|T.H.MAX_DEF|int|物防上限|
|T.H.MIN_MDF|int|魔防下限|
|T.H.MAX_MDF|int|魔防上限|
|T.H.HIT|int|命中|
|T.H.HITSPD|int|攻击速度|
|T.H.BURST|int|暴击几率|
|T.H.BURST_DAM|int|暴击伤害|
|T.H.IMM_ATT|int|物伤减免|
|T.H.IMM_MAG|int|魔伤减免|
|T.H.SUCK_HP|int|吸血|
|T.H.LUCK|int|幸运|
|T.H.DROP|int|怪物爆率|
|T.H.BW|int| 当前重量|
|T.H.MAXBW|int|英雄最大负重|
|T.H.WW|int| 穿戴负重|
|T.H.MAXWW|int| 最大穿戴负重|
|T.H.HW|int|腕力|
|T.H.MAXHW|int|当前最大可穿戴腕力|
|T.H.TITLES|table|英雄的称号数据|
|T.H.ACTIVATE_TITLE|int|当前查看英雄激活的称号id|
|T.H.SKILL_TRAIN_DATA|table|获取技能的等级熟练度数据 <br>param1: 技能ID |
|T.H.SKILL_DATA|table|获取技能数据 param1: 技能ID|
|T.H.LEARNED_SKILLS|table|获取已有技能数据 <br>param1:是否排除普攻  <br>param2:是否只获取主动技能|
|T.H.ATT_BY_TYPE|int|根据类型ID获取属性值 <br>param1: 类型ID|
|T.H.EQUIP_POS_DATAS|table|当前查看英雄的所有装备位数据|
|T.H.EQUIP_DATA|table|获取当前查看英雄对应装备位的装备数据|
|T.H.EQUIP_DATA_LIST|table|获取当前查看英雄对应装备位的装备数据列表|支持版本号3.40.8以上|
|T.H.EQUIP_DATA_BY_MAKEINDEX|table|通过MakeIndex获取查看交易行他人英雄装备数据|支持版本号3.40.8以上|


# SL


#打印函数
#### 日志打印
- `SL:release_print(...)`

#### DEBUG下日志打印
- `SL:Print(...)`
- `SL:PrintEx(...)`
- `SL:PrintTraceback()`
- `SL:dump(data, desciption, nesting)`

|字段|类型|注释|
|:----    |:-------    |:---|
|data    |table   |需要打印的表|
|desciption |string|打印表描述|
|nesting |int|需要打印的深度|

**------------**
#JSON

<font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;">特殊：json过程中已下违禁词不可用</font>
<font color="#ff00ff" style="font-family: Fixedsys;font-size: 15px;">违禁词：`lib` `function` `then` `end` `_G` `return` `index` `set` `%(` `%)` `_`</font>

#### json字符串解密
- `SL:JsonDecode(jsonStr, isfilter)`

|字段|类型|注释|
|:----    |:---   |:---                   |
|jsonStr  |string |json字符串             |
|isfilter |boolean|是否过滤违禁词 默认为true|

-  返回值： json table
-  代码示例

```
	-- [[{"index":1, "value":2}]]   -->  {index = 1, value = 2}

	local jsonStr = [[{"index":1, "value":2}]]
	local jsonData = SL:JsonDecode(jsonStr)
```

------------
#### json字符串加密
- `SL:JsonEncode(jsonData, isfilter)`

|字段|类型|注释|
|:----    |:------|:---                   |
|jsonData |table  |json表                 |
|isfilter |boolean|是否过滤违禁词 默认为true|

- 返回值： json string
- 代码示例

```
	-- {index = 1, value = 2}   -->   [[{"index":1, "value":2}]

	local tab = {"1","2"}
	local jsonStr = SL:JsonEncode(tab)
	SL:Print(jsonStr)
```

**------------**
#常用函数
#### 颜色转换函数
- `SL:ConvertColorFromHexString(hexStr)`

- 从16进制字符转为{r, g, b}
- 返回值： table

*示例*
```
	local color = SL:ConvertColorFromHexString("#FFFFFF")
	SL:dump(color)
```

------------
#### 文件路径是否存在
- `SL:IsFileExist(path)`

- path ：文件路径
- 返回值 ：true / false

*示例*
```
	if SL:IsFileExist("E:/1.png") then
		SL:Print("文件存在")
	else
		SL:Print("文件不存在")
	end
```

------------
#### 深拷贝
- `SL:CopyData(data)`

------------
#### 字符串分割
- `SL:Split(str, delimiter)`

- 按分隔符去拆分一串字符
- 返回值 ： table

*示例*
```
	local spt = SL:Split("11#22#33", "|")
	SL:dump(spt)
```

------------
#### 文本提示
- `SL:ShowSystemTips(str)`

- str : string  提示文本

------------
#### 哈希表转成按数组
- `SL:HashToSortArray(hashTab, sortFunc)`

- 将hashTab转换成有序table，并可以按sortFunc排序，sortFunc可选参数

*示例*
```lua
	local cfg = {["测试表1"] = {"表1", 1},["测试表2"] = {"表2", 2},["测试表3"] = {"表3", 3},["测试表4"] = {"表4", 4},["测试表5"] = {"表5", 5}}
	local function sort_cfg(a, b)
		return a[1] < b[1]
	end
	local new_cfg = SL:HashToSortArray(cfg, sort_cfg)
	SL:dump(new_cfg, "new_cfg")
```
------------
#### 显示提示文本框
- `SL:SHOW_DESCTIP(str, width, pos, anchorPoint)`

|字段        |必选|类型|注释|
|:----      |:-|:--|:---|
|str        |是|string|显示文本|
|width      |否|int|显示宽度, 默认: 1136|
|pos        |否|table|坐标, 默认: {x = 0, y = 0}|
|anchorPoint|否|table|锚点, 默认: {x = 0, y = 1}|

------------
#### 加载文件
- `SL:Require(file, reload)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|file        |是|string|文件名|
|reload      |否|boolean|是否重新加载文件，填true时，会先释放文件再加载|

- `SL:RequireFile(file)`

- DEBUG下默认重新加载文件

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|file        |是|string|文件名|

#### 拆解文件 [3.40.4版本]
- `SL:LoadTxtFile(path, delimiter, callBack)`

- 以指定分隔符拆解一个文件

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|path        |是|string|文件路径|
|delimiter   |否|string|指定分隔符|
|callback    |是|function|拆解回调方法 传入拆分后table参数|

*示例 *
```
	local function callback(data)
        SL:PrintTable(data, "LINE======")
    end
    SL:LoadTxtFile("data_config/msg_decoder_config.txt", "#", callback)
```

------------
#### 数字转换成万、亿单位
- `SL:GetSimpleNumber(num, places)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|num         |是|int|数值|
|places      |否|int|显示小数点后几位数 [3.40.3版本]|

- 将数字 num 转换成 xx万、xx亿

------------
#### 血量单位显示 
- ` SL:HPUnit(hp, pointBit)`

- 将血量数值转换有单位显示 过十亿(单位：E)   10w-99999w(单位：W）

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|hp          |是|int|血量数值|
|pointBit    |否|int|显示小数点后几位, 默认保留后两位|

-----------
#### 中文转换成竖着显示
- `SL:ChineseToVertical(str)`

------------
#### 阿拉伯数字转中文大写
- `SL:NumberToChinese(num)`

------------
#### 获取字符串的byte长度
- `SL:GetUTF8ByteLen(str)`

------------
#### 时间格式化成字符串显示
- `SL:TimeFormatToStr(time)`

- 将时间 time 大于 1 天时转换成 xx天xx时xx分， 否则 xx:xx:xx

- `SL:SecondToHMS(sec, isToStr, isSimple)` [3.40.2版本]

- 秒转时分秒

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|sec         |是|int|秒数|
|isToStr     |否|boolean|是否转成字符串输出, 空或false则返回table <br>{d = 天数, h = 小时, m = 分钟, s = 秒}|
|isSimple    |否|boolean|是否简化字符串[基于isToStr 为 true]|

* 返回字符串格式 :  xx天xx时xx分xx秒

------------
#### 阿拉伯数字转中文大写
- `SL:NumberToChinese(num)`

------------
#### 数字转化为千分位字符串
- `SL:GetThousandSepString(num)`

* 返回字符串格式 : 例: 10,000,000

------------
#### lua table转成config配置表
- `SL:SaveTableToConfig(tab, name, destPath, sortFunc)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|tab         |是|table|需要转换的table|
|name        |是|string|转出文件名|
|destPath    |否|string|文件保存的路径, 默认目录：dev/scripts/game_config/|
|sortFunc    |否|function|外层排序函数|

------------
#### 十六进制转十进制
- `SL:HexToInt(hexStr)`

------------
#### MD5加密
- `SL:GetStrMD5(str)`

------------
#### 计算两坐标间的平方距离 [3.40.3版本]
- `SL:GetPointDistanceSQ(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|起始坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|结束坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两坐标间的距离 [3.40.3版本]
- `SL:GetPointDistance(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|起始坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|结束坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算向量长度 [3.40.3版本]
- `SL:GetPointLength(pt)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt  		 |是|table|GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算向量长度平方 [3.40.3版本]
- `SL:GetPointLengthSQ(pt)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt  		 |是|table|GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两点中心点坐标 [3.40.3版本]
- `SL:GetMidPoint(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两点相加坐标 [3.40.3版本]
- `SL:GetAddPoint(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两点相减坐标 [3.40.3版本]
- `SL:GetSubPoint(pt1, pt2)`
- pt1坐标 减 pt2坐标

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 标准向量化坐标 [3.40.3版本]
- `SL:GetNormalizePoint(pt)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两向量夹角弧度值 [3.40.3版本]
- `SL:GetPointAngle(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算两向量夹角角度值 [3.40.3版本]
- `SL:GetPointRotate(pt1, pt2)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt1  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|
|pt2  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算自身弧度值 [3.40.3版本]
- `SL:GetPointAngleSelf(pt)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

------------
#### 计算自身角度值 [3.40.3版本]
- `SL:GetPointRotateSelf(pt)`

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|pt  		 |是|table|坐标 GUI:p(x, y) 或 <br>{x = x, y = y}|

```
	-- 获取坐标 pt1 到 pt2 的角度值
	local pt1 = GUI:p(100, 100)
	local pt2 = GUI:p(100, 200)
	local p = SL:GetSubPoint(pt2, pt1)
	local rotate = SL:GetPointRotateSelf(p)
	SL:Print(rotate)
	
	-- 两向量夹角 角度值
	local tRotate = SL:GetPointRotate(pt1, pt2)
	SL:Print(tRotate)
```
------------
#### 获取高16位值 [3.40.4版本]
- `SL:GetH16Bit(value)`

#### 获取低16位值 [3.40.4版本]
- `SL:GetL16Bit(value)`

------------
#### 跳转到某个超链
- `SL:JumpTo(id)`

- id : 对应界面的跳转id
*跳转id参考如下: *
```
		Equip               = 1,            -- 角色-装备
		State               = 2,            -- 角色-状态
		Attri               = 3,            -- 角色-属性
		Skill               = 4,            -- 角色-技能
		Title               = 5,            -- 角色-装备
		BestRing            = 6,            -- 角色-首饰盒
		Bag                 = 7,            -- 背包
		Stall               = 8,            -- 摆摊
		StoreHot            = 9,            -- 商城-热销
		StoreBeauty         = 10,           -- 商城-装饰
		StoreEngine         = 11,           -- 商城-功能
		StoreFestival       = 12,           -- 商城-节日
		GuildMain           = 13,           -- 行会-主界面
		GuildMember         = 14,           -- 行会成员列表
		GuildList           = 15,           -- 行会列表
		Mail                = 16,           -- 邮件
		Team                = 17,           -- 组队
		NearPlayer          = 18,           -- 附近玩家

		Setting             = 23,           -- 设置
		MiniMap             = 24,           -- 小地图
		SkillSetting        = 25,           -- 技能设置
		StoreRecharge       = 26,           -- 充值
		Auction             = 27,           -- 拍卖行
		Friend              = 28,           -- 好友
		ExitToRole          = 29,           -- 小退
		GuildCreate         = 30,           -- 行会创建
		Guild               = 31,           -- 智能行会界面
		Rank                = 32,           -- 排行榜
		Trade               = 33,           -- 面对面交易 请求
		ForceExitToRole     = 34,           -- 强制小退
		TradingBank         = 35,           -- 交易行
		GuideEnter          = 36,           -- 引导进入
		SuperEquip          = 37,           -- 角色-神装
		HeroEquip           = 41,           -- 英雄-装备
		HeroState           = 42,           -- 英雄-状态
		HeroAttri           = 43,           -- 英雄-属性
		HeroSkill           = 44,           -- 英雄-技能
		HeroTitle           = 45,           -- 英雄-称号
		HeroBestRing        = 46,           -- 英雄-首饰盒
		HeroBag             = 47,           -- 英雄-背包
		HeroSuperEquip      = 48,           -- 英雄-神装
		ReinAttrPoint       = 51,           -- 转生属性点
		Chat                = 52,           -- 聊天
		PCPrivate           = 53,           -- PC 私聊记录页

		MagicJointAttack    = 99,           -- 释放合击

		AssistChange        = 110,          -- 主界面-任务栏
		Box996              = 111,          -- 盒子称号
		MainMiniMapChange   = 112,          -- 小地图伸缩
		PCResolution        = 113,          -- PC 分辨率设置
		ChatExtendEmoj      = 114,          -- 角色-表情
		ChatExtendBag       = 115,          -- 聊天小框-背包
		MainNear            = 116,          -- 主界面-附近列表
		CallPay             = 117,          -- 调用-支付

		SettingBasic        = 300,          -- 基础设置
		SettingWindowRange  = 301,          -- 视距
		SettingFight        = 302,          -- 战斗
		SettingProtect      = 303,          -- 保护
		SettingAuto         = 304,          -- 挂机
		SettingHelp         = 305,          -- 帮助

		KeFu                = 310,          -- 调用客服界面
		Compound            = 2201,         -- 合成
		
		PlayerInternalState     = 401,      -- 人物内功状态
		PlayerInternalSkill     = 402,      -- 人物内功技能
		PlayerInternalMeridian  = 403,      -- 人物内功经络
		PlayerInternalCombo     = 404,      -- 人物内功连击

		HeroInternalState       = 501,      -- 英雄内功状态
		HeroInternalSkill       = 502,      -- 英雄内功技能
		HeroInternalMeridian    = 503,      -- 英雄内功经络
		HeroInternalCombo       = 504,      -- 英雄内功连击
		
		ReviewGift              = 311,      -- 好评有礼
		Community               = 320,      -- 社区帖子
```
------------
#### 退出到选角界面
- `SL:ExitToRoleUI()`

- 小退时, 有弹窗提示

- `SL:ForceExitToRoleUI()`

- 强制小退, 无弹窗提示

------------
#### 退出到登录界面
- `SL:ExitToLoginUI()`

#### 退出游戏 [3.40.8版本]
- `SL:ExitGame()`
------------
#### 发送GM命令到聊天
- `SL:SendGMMsgToChat(msg)`

- msg  : 字符串

------------
#### 创建一个红点到节点
- `SL:CreateRedPoint(targetNode, offset)`

- 返回红点 widget

|字段        |必选|类型|注释|
|:----       |:-|:--|:---|
|targetNode  |是|widget|目标控件|
|offset      |否|table|偏移位置 例: {x = 5, y = 5}|

------------
#### 设置文本样式(按钮、文本)
- `SL:SetColorStyle(widget, colorID)`

- widget ：按钮或者文本对象

- colorID ：0 - 255 色值ID 

------------
#### 获取对应色值ID的配置
- `SL:GetColorCfg(colorID)`

------------
#### 检查是否满足条件
- `SL:CheckCondition(conditionStr)`
- 返回值 : true / false

------------
#### 显示气泡提醒
- `SL:AddBubbleTips(id, path, callback)`

- id  ：气泡ID

- path：气泡图片资源路径

- callback：气泡点击回调

------------
#### 删除气泡提醒
- `SL:DelBubbleTips(ID)`

- id  ：气泡ID

------------
#### 重新加载地图
- `SL:ReloadMap()`

------------
#### 请求HTTP Get方式
- `SL:HTTPRequestGet(url, httpCB)`

|参数名|必选|类型|说明|
|:---- |:---|:-----   |-----   |
|url   |是  |string   | 链接地址|
|httpCB|是  |function | 回调函数 |

*示例*
```
	local function httpCB(success, response)
		-- success: boolean 请求是否成功
		-- response: string 请求返回数据
	end
	SL:HTTPRequestGet("https://www.baidu.com/", httpCB)
```

------------
#### 请求HTTP Post方式
- `SL:HTTPRequestPost(url, httpCB, suffix, head)`

|参数名|必选|类型|说明|
|:----    |:---|:-----   |-----   |
|url      |是  |string   | 链接地址|
|httpCB   |是  |function | 回调函数|
|suffix   |是  |string   | 请求信息|
|head     |否  |table    | 请求头|

*示例*
```
	local function httpCB(success, response)
		-- success: boolean 请求是否成功
		-- response: string 请求返回数据
	end
	local suffix = "appid=1&device_id=PCDV-6ct5fzZ&game_id=1&platform=0&type=1&username=wuuhui&sign=30a51e6"
	SL:HTTPRequestPost("https://www.baidu.com/", httpCB, suffix)
```

-----------
#### 本地公告展示 [3.40.3版本]
- `SL:ShowLocalNoticeByType(data)`

|参数名|必选|类型|说明|
|:----    |:---|:-----   |-----   |
|data     |是  |table    | 具体参数配置|

参数说明： 
```
	Type         	-- 公告类型
	【
    4: 顶部跑马灯公告 (Msg、 FColor、 BColor)  5: 屏幕跑马灯公告 可控制Y轴坐标 (Msg、 FColor、 BColor、 Y、 Count)
    6: 聊天上方公告 (Msg、 FColor、 BColor、 Time、 Label) 9: 普通通用提示 (Msg) 
    10: 可控制X轴Y轴公告  (Msg、 FColor、 BColor、 X、 Y) 11: 屏幕跑马灯公告 (系统公告) (Type、 Msg、 FColor、 BColor) 
    12: 系统频道公告 (Msg、 FColor、 BColor)  13: 带缩放效果的公告 可设置Y轴 (Msg、 FColor、 BColor、Y)
	】
	Msg          	-- 提示内容
	FColor       	-- 文字色值ID
	BColor       	-- 背景色值ID
	X            	-- 坐标X
	Y            	-- 坐标Y
	Time         	-- 倒计时
	Count        	-- 播放次数
	Label        	-- 响应Link

```

#### 震屏 [3.40.3版本]
- `SL:ShakeScene(time, distance)`

|参数名|必选|类型|说明|
|:----    |:---|:-----   |-----   |
|time     |否  |int    | 震动时间 (毫秒)|
|distance |否  |int    | 震动距离|

例 :
```
	-- 无参默认 time为700 、distance为10 
	SL:ShakeScene()
```

**------------**
#游戏事件函数
#### 注册控件事件
- `SL:RegisterWndEvent(widget, desc, msgtype, callback)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|widget |是  |object |控件对象|
|msg |是  |string | 描述|
|msgtype|是  |int | 窗体事件id|
|callback|是  |function | 回调函数|

```
	窗口事件 msgtype
	WND_EVENT_MOUSE_LB_DOWN             = 1                                         -- 鼠标左键按下事件
	WND_EVENT_MOUSE_LB_UP               = 2                                         -- 鼠标左键弹起事件
	WND_EVENT_MOUSE_LB_CLICK            = 3                                         -- 鼠标左键点击事件
	WND_EVENT_MOUSE_LB_DBCLICK          = 4                                         -- 鼠标左键双击事件
	WND_EVENT_MOUSE_RB_DOWN             = 5                                         -- 鼠标右键按下事件
	WND_EVENT_MOUSE_RB_UP               = 6                                         -- 鼠标右键弹起事件         
	WND_EVENT_MOUSE_RB_CLICK            = 7                                         -- 鼠标右键点击事件
	WND_EVENT_MOUSE_RB_DBCLICK          = 8                                         -- 鼠标右键双击事件
	WND_EVENT_MOUSE_MOVE                = 9                                         -- 鼠标移动事件
	WND_EVENT_MOUSE_WHEEL               = 10                                        -- 鼠标滚轮滚动事件
	WND_EVENT_MOUSE_IN                  = 11                                        -- 鼠标进入控件事件
	WND_EVENT_MOUSE_OUT                 = 12                                        -- 鼠标离开控件事件
	
	WND_EVENT_WND_VISIBLE               = 21                                        -- 可见状态发生变化事件
	WND_EVENT_WND_POS_CHANGE            = 22                                        -- 控件位置发生变化事件
	WND_EVENT_WND_SIZECHANGE            = 23                                        -- 窗口大小发生变化事件
	WND_EVENT_WND_DESTROY               = 24                                        -- 窗体被销毁事件

```
*示例*
```
    SL:RegisterWndEvent(btn, "npc", WND_EVENT_MOUSE_LB_UP, function()
		SL:Print("2")
	end)
```

------------
#### 注销控件事件
- `SL:UnRegisterWndEvent(widget, desc, msgtype)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|widget |是  |object |控件对象|
|msg |是  |string | 描述|
|msgtype|是  |int | 窗体事件id|

*示例*
```
    SL:UnRegisterWndEvent(btn, "npc", WND_EVENT_MOUSE_LB_UP)
```

------------
#### 窗体控件自定义属性

* 添加窗体控件自定义属性 *
- `SL:AddWndProperty(widget, desc, key, value)`

* 删除窗体控件自定义属性*
- `SL:DelWndProperty(widget, desc, key)`

* 获取窗体控件自定义属性*
- `SL:GetWndProperty(widget, desc, key)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|widget   |是  |object |控件对象 |
|desc     |是  |string |描述    |
|key      |是  |string |属性名称|
|value    |是  |any    |属性值  |

*示例*

```
	SL:AddWndProperty(btn, "test", "key", 1)
	local a = SL:GetWndProperty(btn, "test", "key")
	SL:Print(a, type(a))
	SL:DelWndProperty(btn, "test", "key")
```

**------------**
#定时器
#### 开启一个定时器
- `SL:Schedule(callback, time)`

------------
#### 停止一个定时器
- `SL:UnSchedule(scheduleID)`

------------
#### 开启一个单次定时器
- `SL:ScheduleOnce(callback, time)`

------------
####  开启一个定时器, 绑定node节点
- `SL:schedule(node, callback, time)`

------------
#### 开启一个单次定时器, 绑定node节点
- `SL:scheduleOnce(node, callback, time)`

------------

*示例*

```
	local time = 0.5
	local function callback()
		SL:Print("callback...")
	end

	-- 每隔0.5s执行一次 callback
	local sch1 = SL:Schedule(callback, time)

	-- 停止上面的定时器 sch1
	SL:UnSchedule(sch1)

	-- 0.5s后执行一次 callback
	SL:ScheduleOnce(callback, time)

	-- 创建一个Node节点
	local node = GUI:Node_create(parent, "Node", 0 , 0)
	-- node 节点每隔0.5s执行一次 callback
	SL:schedule(node, callback, time)

	-- node 节点0.5s后执行一次 callback
	SL:scheduleOnce(node, callback, time)

	-- node 节点取消定时器操作
	GUI:stopAllActions(node)
```

**------------**
#引导相关
#### 打开引导
- `SL:StartGuide(data)`

- 返回值  : 引导对象

|参数名|必选|类型|说明|
|:--  |:---|:--- |-----       |
|data |是  |table| 数据结构如下, 参考示例|

*table特殊参数*
   **mainIdx** — int 如若指引界面加在主界面节点 需要配置对应标识 :
`1 --左上 2 --中上 3 --右上 4 --左下 5 --中下 6 --右下`

*示例 1 ：*
```
	local function callback()
		SL:Print("callback".....)
	end
	local data = {}
	data.dir           = 8                -- 方向（1~8）从左按瞬时针
	data.guideWidget   = btn_close        -- 当前节点
	data.guideParent   = _parent          -- 父窗口
	data.guideDesc     = "测试"           -- 文本描述
	data.clickCB       = callback         -- 回调
	data.autoExcute    = 3                -- 自动执行秒数
	data.isForce       = true             -- 强制引导

	SL:StartGuide(data)
```

* **针对引导一些引擎原生界面 必需参数 :**

	id — int 提供的原生界面指引ID
	param — int 指引参数 提供的一些原生界面对应位置指引所需参数 比如任务ID
	
*示例 2 ：*
```
	SL:StartGuide({
		id = 1,				-- 背包引导窗口ID
		param = 2682001,		-- 背包物品唯一ID
		guideDesc = "测试引导"
    })
```

#### 关闭引导
- `SL:CloseGuide(guide)`

- 参数 : 传入开始引导返回的 引导对象

**------------**
#本地存储

#### 存储字符到本地
- `SL:SetLocalString(key, data)`

* 存储数据到本地，存储的文件名为："GUIStorage" + 角色ID

|参数名|必选|类型|说明|
|:----     |:---    |:---     |-----   |
|key  |是  |任意类型 |字段名   |
|data |是  |table、int、string| 数据|

*示例*
```
	-- 把数据 t 存储到本地配置的 key 字段里
	local t = {
		val1 = "111", val2 = "222"
	}
    local jsonStr = SL:JsonEncode(t)
    SL:SetLocalString("key", jsonStr)
```

------------
#### 从本地读取字符
- `SL:GetLocalString(key)`

* 读取存储到本地的key数据

* 返回值 : string

|参数名|必选|类型|说明|
|:----|:---|:---    |-----   |
|key  |是  |任意类型 |字段名   |

*示例*
```
	-- 把数据从本地存储配置中取出来
	local data = {}
    local jsonStr = SL:GetLocalString("key")
    if jsonStr and string.len(jsonStr) > 0 then
        local jsonData = SL:JsonDecode(jsonStr)
        if jsonData then
            data = jsonData
        end
    end
	SL:dump( data )
```

**------------**
# 背包常用函数  [3.40.2版本]
#### 背包刷新
- `SL:RefreshBagPos()`

#### 使用物品 
- `SL:UseItemByIndex(Index)`

|参数名|必选|类型|说明|
|:----|:---|:---    |-----   |
|Index|是  |int |物品Index   |

#### 批量勾选背包物品 [3.40.3版本]
- `SL:SetBagItemChoose(data)`

|参数名|必选|类型|说明|
|:----|:---|:---    |-----   |
|data|是  |table |物品唯一ID 数组   |

#### 丢弃物品 [3.40.3版本]
- `SL:IntoDropBagItem(itemData)`

|参数名|必选|类型|说明|
|:----|:---|:---    |-----   |
|itemData|是  |table |装备数据   |

**------------**
# 装备常用函数
#### 检测人物是否可穿戴
- `SL:CheckItemUseNeed(itemData)`

*参数： itemData 装备数据*

------------
#### 检测英雄是否可穿戴
- `SL:CheckItemUseNeed_Hero(itemData)`

*参数： itemData 装备数据*

------------
#### 获得需要比较的装备
- `SL:GetDiffEquip(itemData, isHero)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|isHero    |否  |boolean  |是否对比英雄|

*返回值： table, 具体用法参考官方 GUILayout/ItemTips.lua *

------------
#### 对比传入装备和自身穿戴的装备
- `SL:CheckEquipPowerThanSelf(itemData, from)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|from    |否  |int  |物品来自(界面位置), 可参照元变量"ITEMFROMUI_ENUM"|

*返回值： table

------------
#### 人物装备穿戴 [3.40.2版本]
- `SL:TakeOnPlayerEquip(itemData, pos, isFromHero)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|pos       |是  |int      |装备位置|
|isFromHero|否  |boolean  |是否来自英雄背包|

------------
#### 人物装备脱下 [3.40.2版本]
- `SL:TakeOffPlayerEquip(itemData, isToHero)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|isToHero  |否  |boolean    |是否脱到英雄背包|

------------
#### 英雄装备穿戴 [3.40.2版本]
- `SL:TakeOnHeroEquip(itemData, pos, isFromPlayer)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|pos       |是  |int      |装备位置|
|isFromPlayer|否  |boolean  |是否来自人物背包|

------------
#### 英雄装备脱下 [3.40.2版本]
- `SL:TakeOffHeroEquip(itemData, isToPlayer)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |装备数据|
|isToPlayer|否  |boolean  |是否脱到人物背包|

**------------**
# 界面相关 Menulayer
- `SL:CheckMenuLayerConditionByID(layerID)`

*通过 cfg_menulayer 表中的界面ID检测该界面的条件配置，是否满足显示*

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|layerID  |是  |int    |cfg_menulayer 表中的界面ID|

*返回值： boolean*

------------
- `SL:OpenMenuLayerByID(layerID，parent， extent)`

*通过 cfg_menulayer 表中的界面ID打开该界面*

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|layerID  |是  |int    |cfg_menulayer 表中的界面ID|
|parent   |是  |object |挂接点                    |
|extent   |否  |int    |可选参数                  |

------------
- `SL:CloseMenuLayerByID(layerID)`

*通过 cfg_menulayer 表中的界面ID关闭该界面*

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|layerID  |是  |int    |cfg_menulayer 表中的界面ID|

*返回值： boolean*

------------
### 打开、关闭相关功能界面
####设置界面
- `SL:OpenSettingUI(pageID)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|pageID  |否  |int    |页签ID 不填默认基础设置<br>1 : 基础设置<br>2 : 视距<br>3 : 战斗<br>4 : 保护<br>5 : 挂机<br>6 : 帮助|

- `SL:CloseSettingUI()`

####行会界面
- `SL:OpenGuildMainUI(pageID)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|pageID  |否  |int    |页签ID 不填默认行会主页<br>1 : 主页<br>2 : 成员<br>3 : 列表|

- `SL:CloseGuildMainUI()`
####行会申请界面
- `SL:OpenGuildApplyListUI()`

- `SL:CloseGuildApplyListUI()`

####行会创建界面
- `SL:OpenGuildCreateUI()`

- `SL:CloseGuildCreateUI()`

####行会结盟申请界面
- `SL:OpenGuildAllyApplyUI()`

- `SL:CloseGuildAllyApplyUI()`

####行会宣战/结盟界面 [关闭]
- `SL:CloseGuildWarSponsorUI()`

####人物背包
- `SL:OpenBagUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |pos  : 背包打开位置 <br>bag_page : 背包打开页签ID|
例:
```
	local data = {pos = {x = 200, y = 0}, bag_page = 2}
    SL:OpenBagUI(data) 
```

- `SL:CloseBagUI()`

####英雄背包
- `SL:OpenHeroBagUI()`

- `SL:CloseHeroBagUI()`

####拍卖行
- `SL:OpenAuctionUI()`

- `SL:CloseAuctionUI()`

####摆摊界面
- `SL:OpenStallLayerUI()`

- `SL:CloseStallLayerUI()`

####玩家交易界面
- `SL:OpenTradeUI()`

- `SL:CloseTradeUI()`

####排行榜
- `SL:OpenRankUI(type)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|type  |否  |int    |打开 指定页签ID|

- `SL:CloseRankUI()`

####聊天界面(手机端)
- `SL:OpenChatUI()`

- `SL:CloseChatUI()`

####聊天扩展框
- `SL:OpenChatExtendUI(index)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|index  |否  |int    |打开 指定分组 <br> 1 : 快捷命令<br>2 : 表情<br> 3 : 背包|

- `SL:CloseChatExtendUI()`

####社区帖子 [3.40.3版本]
* 需要后台配置社区地址
- `SL:OpenCommunityUI()`

- `SL:CloseCommunityUI()`

####交易行
- `SL:OpenTradingBankUI()`

- `SL:CloseTradingBankUI()`

####商城
- `SL:OpenStoreUI(page)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|page  |否  |int    |打开 商城对应分页|

- `SL:CloseStoreUI()`

####商城商品购买框
- `SL:OpenStoreDetailUI(storeIndex, limitStr)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|storeIndex  |是  |int    |商品index  cfg_store商城表配置的id|
|limitStr|否|string|超出限制购买的提示|

- `SL:CloseStoreDetailUI()`

####技能配置界面
- `SL:OpenSkillSettingUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |！PC端必填  |table    |对应技能数据 打开技能快捷键配置页|

- `SL:CloseSkillSettingUI()`

####社交
- `SL:OpenSocialUI(page)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|page  |否  |int    |页签ID ( 不填默认1附近 )<br> 1附近玩家、2组队、3好友、4邮件|

- `SL:CloseSocialUI()`

####分辨率修改界面(PC端)
- `SL:OpenResolutionSetUI()`

- `SL:CloseResolutionSetUI()`

####玩家角色界面
- `SL:OpenMyPlayerUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |extent: 子页id<br> 1装备、2状态、3属性、4技能、6称号、11时装<br>isFast:  boolen 是否快捷键打开|
*例 :*
```
	SL:OpenMyPlayerHeroUI({extent = 1})
```

- `SL:CloseMyPlayerUI()`

- `SL:CloseMyPlayerPageUI(data)`  

  *移除对应子页id内容*

####查看他人角色界面
- `SL:OpenOtherPlayerUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |extent: 子页id<br> 1装备、2状态、3属性、4技能、6称号、11时装|

- `SL:CloseOtherPlayerUI()`

- `SL:CloseOtherPlayerPageUI(data)`  

  *移除对应子页id内容*

####英雄角色界面
- `SL:OpenMyPlayerHeroUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |extent: 子页id<br> 1装备、2状态、3属性、4技能、6称号、11时装|

- `SL:CloseMyPlayerHeroUI()`

- `SL:CloseMyPlayerHeroPageUI(data)`  

  *移除对应子页id内容*

####查看他人英雄界面
- `SL:OpenOtherPlayerHeroUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |extent: 子页id<br> 1装备、2状态、3属性、4技能、6称号、11时装|

- `SL:CloseOtherPlayerHeroUI()`

- `SL:CloseOtherPlayerHeroPageUI(data)`  

  *移除对应子页id内容*

####交易行查看他人界面
- `SL:CloseTradingBankPlayerPageUI(data)`

  *移除他人角色对应子页id内容*

- `SL:CloseTradingBankHeroPageUI(data)`

  *移除他人英雄对应子页id内容*

####首饰盒界面
- `SL:OpenBestRingBoxUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

- `SL:CloseBestRingBoxUI(param)`

  *param参数同上*

####打开装备面板
- `SL:OpenPlayerEquipUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开状态面板
- `SL:OpenPlayerBaseAttrUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开属性面板
- `SL:OpenPlayerExtraAttrUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开技能面板
- `SL:OpenPlayerSkillUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开称号面板
- `SL:OpenPlayerTitleUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开时装面板
- `SL:OpenPlayerSuperEquipUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄<br>21：交易行人物<br>22：交易行英雄|

####打开人物BUFF面板 [3.40.6版本]
- `SL:OpenPlayerBuffUI(param)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|param  |是  |int    |param: <br>1: 自己人物<br>2：自己英雄<br>11：其他玩家人物<br>12：其他玩家英雄 [英雄BUFF页3.40.8版本新增]|

####称号提示界面
- `SL:OpenTitleTipsUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |id: 称号id <br> pos: Tips放置位置<br>type: 1未激活 2已激活<br>time: 时间|

- `SL:CloseTitleTipsUI()`

####他人称号提示界面
- `SL:OpenOtherTitleTipsUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |id: 称号id <br> pos: Tips放置位置<br>type: 1未激活 2已激活<br>time: 时间|

- `SL:CloseOtherTitleTipsUI()`

####关闭交易行查看他人容器
- `SL:CloseTradingBankLookPanelUI()`

####关闭交易行查看他人界面
- `SL:CloseTradingBankLookInfoUI()`

####邀请组队界面
- `SL:OpenTeamInvite()`

- `SL:CloseTeamInvite()`

####入队申请列表页
- `SL:OpenTeamApply()`

- `SL:CloseTeamApply()`

####小地图界面
- `SL:OpenMiniMap()`

- `SL:CloseMiniMap()`

####主界面技能按钮区域切换显示
- `SL:OpenGuideEnter(param)`

- `SL:CloseGuideEnter()`

####转生点分配界面
- `SL:OpenReinAttrUI()`

- `SL:CloseReinAttrUI()`

####任务栏收缩切换
- `SL:OpenAssistUI()`

- `SL:CloseAssistUI()`

####主界面小地图收缩切换[手机端]
- ` SL:OpenMiniMapChangeUI()`

- `SL:CloseMiniMapChangeUI()`

####附近展示页
- `SL:OpenMainNearUI()`

- `SL:CloseMainNearUI()`

####直接调用支付
- `SL:OpenCallPayUI()`

####打开客服UI
- `SL:OpenKefuUI()`

####PC端私聊界面
- `SL:OpenPCPrivateUI()`

- `SL:ClosePCPrivateUI()`

####PC端小地图变换
- `SL:OpenPCMiniMapUI()`

####添加好友界面
- `SL:OpenAddFriendUI()`

- `SL:CloseAddFriendUI()`

####添加黑名单界面
- `SL:OpenAddBlackListUI()`

- `SL:CloseAddBlackListUI()`

####好友添加申请页
- `SL:OpenFriendApplyUI()`

- `SL:CloseFriendApplyUI()`

####拍卖行-世界拍卖/行会拍卖
- `SL:OpenAuctionWorldUI(parent, source)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|parent  |是  |widget    |挂接父节点|
|source|是|int|类别 <br>0: 世界拍卖 <br>1: 行会拍卖|

- `SL:CloseAuctionWorldUI()`

####拍卖行-我的竞拍
- `SL:OpenAuctionBiddingUI(parent)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|parent  |是  |widget    |挂接父节点|

- `SL:CloseAuctionBiddingUI()`

####拍卖行-我的上架
- `SL:OpenAuctionPutListUI(parent)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|parent  |是  |widget    |挂接父节点|

- `SL:CloseAuctionPutListUI()`

####拍卖行上架界面
- `SL:OpenAuctionPutinUI(itemData)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |背包物品数据|

- `SL:CloseAuctionPutinUI()`

####拍卖行下架界面
- `SL:OpenAuctionPutoutUI(item)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|item  |是  |table    |拍卖行上架的物品数据|

- `SL:CloseAuctionPutoutUI()`

####拍卖行竞拍界面
- `SL:OpenAuctionBidUI(item)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|item  |是  |table    |拍卖行上架的物品数据|

- `SL:CloseAuctionBidUI()`

####拍卖行一口价界面
- `SL:OpenAuctionBuyUI(item)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|item  |是  |table    |拍卖行上架的物品数据|

- `SL:CloseAuctionBuyUI()`

####拍卖行超时界面
- `SL:OpenAuctionTimeoutUI(item)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|item  |是  |table    |拍卖行上架的物品数据|

- `SL:CloseAuctionTimeoutUI()`

####合成界面
- `SL:OpenCompoundItemsUI()`

- `SL:CloseCompoundItemsUI()`

####怪物提示列表-设置界面
- `SL:OpenBossTipsUI()`

- `SL:CloseBossTipsUI()`

####拾取列表-设置界面
- `SL:OpenPickSettingUI()`

- `SL:ClosePickSettingUI()`

####保护配置-设置界面
- `SL:OpenProtectSettingUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |cfg_setup对应保护配置|

- `SL:CloseProtectSettingUI()`

####增加怪物名字-设置界面
- `SL:OpenAddNameUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |否  |table    |ignoreName:  boolean 是否是挂机忽略名字|

- `SL:CloseAddNameUI()`

####增加BOSS类型-设置界面
- `SL:OpenAddBossTypeUI()`

- `SL:CloseAddBossTypeUI()`

####技能排行-设置界面
- `SL:OpenSkillRankPanelUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |cfg_setup对应保护配置|

- `SL:CloseSkillRankPanelUI(data)`

####新增技能-设置界面
- `SL:OpenSkillPanelUI()`

- `SL:CloseSkillPanelUI()`

####选择下拉框
- `SL:OpenSelectListUI(list, position, cellwidth, cellheight, func)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|list  |是  |table    |下拉要显示的内容|
|position|是  |table   |初始位置 |
|cellwidth|否  |int    |单条cell的宽|
|cellheight|否  |int   |单条cell的高|
|func  |否   |function |回调 选中的编号1~n 0是关闭|

- `SL:CloseSelectListUI()`

####996盒子界面
- `SL:OpenBox996UI(index)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|index|否 [ 3.40.4版本新增参数 ]  |int |盒子打开默认分页id<br>1: 特权称号 2: 每日礼包 3: 超级礼包 4: 会员礼包 5: SVIP|

- `SL:CloseBox996UI()`

####英雄状态选择界面
- `SL:OpenHeroStateSelectUI(data)`

- `SL:CloseHeroStateSelectUI(data)`

####打开快捷使用框
- `SL:OpenAutoUseTip(itemData, equipPos, isBook, isHero)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData |是  |table  |真实物品数据|
|equipPos |否  |int    |物品为装备时装戴的装备位置|
|isBook   |否  |boolean|是否是技能书|
|isHero   |否  |boolean|是否为英雄|

####关闭快捷使用框
- ` SL:CloseAutoUseTip(makeIndex, isHero)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|makeIndex|是  |int    |物品唯一ID|
|isHero   |否  |boolean|是否为英雄|

####开宝箱动画页 [3.40.3版本]
- `SL:OpenTreasureBoxShow(itemData)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData |是  |table  |宝箱物品数据|

- `SL:CloseTreasureBoxShow()`

####宝箱奖励界面 [3.40.3版本]
- `SL:OpenGoldBoxUI(itemData)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData |是  |table  |宝箱物品数据|

- `SL:CloseGoldBoxUI()`

####摇骰子界面 [3.40.4版本]
- `SL:OpenPlayDice(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data     |是  |table  |字段说明如下|
```
	{
        arr = table 投掷值 {xx, xx}
        count = 数量
        callback = @xxx 脚本触发
    }
```

- `SL:ClosePlayDice()`

#### 求购界面 [3.40.5版本]
- `SL:OpenPurchaseUI()`

- `SL:ClosePurchaseUI()`

#### 求购 - 世界求购 [3.40.5版本]
- `SL:OpenPurchaseWorldUI(parent)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|parent  |是  |widget    |挂接父节点|

- `SL:ClosePurchaseWorldUI()`

#### 求购 - 我的求购 [3.40.5版本]
- `SL:OpenPurchaseMyUI(parent)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|parent  |是  |widget    |挂接父节点|

- `SL:ClosePurchaseMyUI()`

#### 求购出售页 [3.40.5版本]
- `SL:OpenPurchaseSellUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |单条世界求购数据|

- `SL:ClosePurchaseSellUI()`

#### 求购上架页 [3.40.5版本]
- `SL:OpenPurchasePutInUI()`

- `SL:ClosePurchasePutInUI()`

#### 仓库 - 关闭
- `SL:CloseStorageUI()`

####通用描述Tips
- `SL:OpenCommonDescTipsPop(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |str: 描述内容 <br> worldPos: 提示位置<br> width: 描述内容宽度<br> anchorPoint: 锚点<br>formatWay: 设置为1 解析富文本格式: `<font></font>`[！否则默认解析老脚本富文本`<RText/FCOLOR=254>`] |

```lua
    local data = {width = 1136, str = "测试文本", worldPos = {x = 568, y = 320}, anchorPoint = {x = 0, y = 1}}
    SL:OpenCommonDescTipsPop(data)
```

- `SL:CloseCommonDescTipsPop()`

####通用弹窗
- `SL:OpenCommonTipsPop(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |str: 文本<br>btnType: 按钮类型 int 1:"确定" 2:{"确定","取消"} <br> btnDesc: 按钮描述 table<br> showEdit: 是否显示输入框<br>editParams: 输入框参数table <br>```{ inputMode: 键盘编辑类型, maxLength: 可输入最大长度, str: 默认文本内容}```<br> callback: 按钮回调 [参数1: 点击的按钮id 参数2: 额外参数 table: {editStr=输入框字符串}]|

*例 :*
```
	local data = {}
	data.str = "请输入邀请玩家的名字"
	data.btnType = 2
	data.showEdit = true
	data.callback = function(atype, param)
		if atype == 1 then
			if param and param.editStr and string.len(param.editStr) > 0 then
				SL:RequestInviteJoinTeam(nil, param.editStr)
			end
		end
	end
	SL:OpenCommonTipsPop(data)
```

- `SL:CloseCommonTipsPop()`

####道具装备Tips
- `SL:OpenItemTips(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |itemData: 物品数据 <br> pos: 提示位置<br> from:非必要 物品来自(界面位置), 可参照元变量ITEMFROMUI_ENUM|

- `SL:CloseItemTips()`

####道具拆分弹窗
- `SL:OpenItemSplitPop(itemData)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|itemData  |是  |table    |物品数据|

- `SL:CloseItemSplitPop()`

####通用功能选择提示
- `SL:OpenFuncDockTips(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |参数说明: <br> type : 类型 可参照元变量DOCKTYPE_NENUM<br> targetId : 选中目标id<br> targetName :目标名称 <br> pos : 展示位置|

示例可参照 MainTarget文件内 点击查看菜单功能。
- `SL:CloseFuncDockTips()`

####NPC进度条提示  [3.40.3版本]
- `SL:OpenProgressBarUI(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |参数说明: <br> time : 时间 <br> msg : 显示内容|

- `SL:CloseProgressBarUI()`

####多条选项弹窗提示  [3.40.3版本]
- `SL:OpenCommonBubbleInfo(data)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|data  |是  |table    |参数说明: <br> pos : 坐标 <br> list : 多条选项列表<br>[单条数据参考: <br>{str = 文本, agreeCall = 同意按钮回调(function), disAgreeCall = 拒绝回调(function)}<br>]|

- `SL:CloseCommonBubbleInfo()`

*例 :*
```
	local tt = {
		[1] = "11111",
		[2] = "22222",
		[3] = "33333",
	}

	local data = {}
	data.pos = {x = 200, y = 400}
	data.list = {}
	for _, v in pairs(tt) do
		local info = {}
		info.str = v
		info.agreeCall = function()
			SL:Print("AgreeCall____" .. v)
		end
		info.disAgreeCall = function()
			SL:Print("disAgreeCall___" .. v)
		end
		table.insert(data.list, info)
	end
	SL:OpenCommonBubbleInfo(data)
```

#### 打开好评有礼  [3.40.3版本]
- `SL:ReviewGift()`

------------
### 打开网址/链接  [3.40.3版本]
- `SL:OpenURL(url)`

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                    |
|url  |是  |string    |网址/链接|

*示例*
```
	SL:OpenURL("https://www.baidu.com/")
```

**------------**
#颜色
- `SL:GetColorByStyleId(id)`

*把 cfg_colour_style 表中的对应 id 的颜色转换成 RGB 格式*

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                   |
|id  |是  |int    |cfg_colour_style 表中的对应 id|

*返回值类型： table {r = 255, g = 255, b = 255} *

------------
- `SL:GetHexColorByStyleId(id)`

*把 cfg_colour_style 表中的对应 id 的颜色转换成 16进制 格式 *

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                   |
|id  |是  |int    |cfg_colour_style 表中的对应 id|

* 返回值类型： string  "#FFFFFF"

------------
- `SL:GetSizeByStyleId(id)`

*把 cfg_colour_style 表中的对应 id 的颜色大小 *

* 返回值类型：  int   size

------------
- `SL:GetColorHexFromRGB(color3B)`

* Color3B颜色转化为hex 16进制

|参数名|必选|类型|说明|
|:----    |:---|:---   |-----                   |
|color3B  |是  |table  |例: {r = 255, g = 255, b = 255}|

* 返回值类型： string  "#FFFFFF"

##颜色Id(0-255) 对应 16进制Hex(#000000-#ffffff)
```
  Id：(0)           Hex：(#000000)
  Id：(1)           Hex：(#800000)
  Id：(2)           Hex：(#008000)
  Id：(3)           Hex：(#808000)
  Id：(4)           Hex：(#000080)
  Id：(5)           Hex：(#800080)
  Id：(6)           Hex：(#008080)
  Id：(7)           Hex：(#c0c0c0)
  Id：(8)           Hex：(#558097)
  Id：(9)           Hex：(#9db9c8)
  Id：(10)          Hex：(#7b7373)
  Id：(11)          Hex：(#2d2929)
  Id：(12)          Hex：(#5a5252)
  Id：(13)          Hex：(#635a5a)
  Id：(14)          Hex：(#423939)
  Id：(15)          Hex：(#1d1818)
  Id：(16)          Hex：(#181010)
  Id：(17)          Hex：(#291818)
  Id：(18)          Hex：(#100808)
  Id：(19)          Hex：(#f27971)
  Id：(20)          Hex：(#e1675f)
  Id：(21)          Hex：(#ff5a5a)
  Id：(22)          Hex：(#ff3131)
  Id：(23)          Hex：(#d65a52)
  Id：(24)          Hex：(#941000)
  Id：(25)          Hex：(#942918)
  Id：(26)          Hex：(#390800)
  Id：(27)          Hex：(#731000)
  Id：(28)          Hex：(#b51800)
  Id：(29)          Hex：(#bd6352)
  Id：(30)          Hex：(#421810)
  Id：(31)          Hex：(#ffaa99)
  Id：(32)          Hex：(#5a1000)
  Id：(33)          Hex：(#733929)
  Id：(34)          Hex：(#a54a31)
  Id：(35)          Hex：(#947b73)
  Id：(36)          Hex：(#bd5231)
  Id：(37)          Hex：(#522110)
  Id：(38)          Hex：(#7b3118)
  Id：(39)          Hex：(#2d1810)
  Id：(40)          Hex：(#8c4a31)
  Id：(41)          Hex：(#942900)
  Id：(42)          Hex：(#bd3100)
  Id：(43)          Hex：(#c67352)
  Id：(44)          Hex：(#6b3118)
  Id：(45)          Hex：(#c66b42)
  Id：(46)          Hex：(#ce4a00)
  Id：(47)          Hex：(#a56339)
  Id：(48)          Hex：(#5a3118)
  Id：(49)          Hex：(#2a1000)
  Id：(50)          Hex：(#150800)
  Id：(51)          Hex：(#3a1800)
  Id：(52)          Hex：(#080000)
  Id：(53)          Hex：(#290000)
  Id：(54)          Hex：(#4a0000)
  Id：(55)          Hex：(#9d0000)
  Id：(56)          Hex：(#dc0000)
  Id：(57)          Hex：(#de0000)
  Id：(58)          Hex：(#fb0000)
  Id：(59)          Hex：(#9c7352)
  Id：(60)          Hex：(#946b4a)
  Id：(61)          Hex：(#734a29)
  Id：(62)          Hex：(#523118)
  Id：(63)          Hex：(#8c4a18)
  Id：(64)          Hex：(#884411)
  Id：(65)          Hex：(#4a2100)
  Id：(66)          Hex：(#211810)
  Id：(67)          Hex：(#d6945a)
  Id：(68)          Hex：(#c66b21)
  Id：(69)          Hex：(#ef6b00)
  Id：(70)          Hex：(#ff7700)
  Id：(71)          Hex：(#a59484)
  Id：(72)          Hex：(#423121)
  Id：(73)          Hex：(#181008)
  Id：(74)          Hex：(#291808)
  Id：(75)          Hex：(#211000)
  Id：(76)          Hex：(#392918)
  Id：(77)          Hex：(#8c6339)
  Id：(78)          Hex：(#422910)
  Id：(79)          Hex：(#6b4218)
  Id：(80)          Hex：(#7b4a18)
  Id：(81)          Hex：(#944a00)
  Id：(82)          Hex：(#8c847b)
  Id：(83)          Hex：(#6b635a)
  Id：(84)          Hex：(#4a4239)
  Id：(85)          Hex：(#292118)
  Id：(86)          Hex：(#463929)
  Id：(87)          Hex：(#b5a594)
  Id：(88)          Hex：(#7b6b5a)
  Id：(89)          Hex：(#ceb194)
  Id：(90)          Hex：(#a58c73)
  Id：(91)          Hex：(#8c735a)
  Id：(92)          Hex：(#b59473)
  Id：(93)          Hex：(#d6a573)
  Id：(94)          Hex：(#efa54a)
  Id：(95)          Hex：(#efc68c)
  Id：(96)          Hex：(#7b6342)
  Id：(97)          Hex：(#6b5639)
  Id：(98)          Hex：(#bd945a)
  Id：(99)          Hex：(#633900)
  Id：(100)          Hex：(#d6c6ad)
  Id：(101)          Hex：(#524229)
  Id：(102)          Hex：(#946318)
  Id：(103)          Hex：(#efd6ad)
  Id：(104)          Hex：(#a58c63)
  Id：(105)          Hex：(#635a4a)
  Id：(106)          Hex：(#bda57b)
  Id：(107)          Hex：(#5a4218)
  Id：(108)          Hex：(#bd8c31)
  Id：(109)          Hex：(#353129)
  Id：(110)          Hex：(#948463)
  Id：(111)          Hex：(#7b6b4a)
  Id：(112)          Hex：(#a58c5a)
  Id：(113)          Hex：(#5a4a29)
  Id：(114)          Hex：(#9c7b39)
  Id：(115)          Hex：(#423110)
  Id：(116)          Hex：(#efad21)
  Id：(117)          Hex：(#181000)
  Id：(118)          Hex：(#292100)
  Id：(119)          Hex：(#9c6b00)
  Id：(120)          Hex：(#94845a)
  Id：(121)          Hex：(#524218)
  Id：(122)          Hex：(#6b5a29)
  Id：(123)          Hex：(#7b6321)
  Id：(124)          Hex：(#9c7b21)
  Id：(125)          Hex：(#dea500)
  Id：(126)          Hex：(#5a5239)
  Id：(127)          Hex：(#312910)
  Id：(128)          Hex：(#cebd7b)
  Id：(129)          Hex：(#635a39)
  Id：(130)          Hex：(#94844a)
  Id：(131)          Hex：(#c6a529)
  Id：(132)          Hex：(#109c18)
  Id：(133)          Hex：(#428c4a)
  Id：(134)          Hex：(#318c42)
  Id：(135)          Hex：(#109429)
  Id：(136)          Hex：(#081810)
  Id：(137)          Hex：(#081818)
  Id：(138)          Hex：(#082910)
  Id：(139)          Hex：(#184229)
  Id：(140)          Hex：(#a5b5ad)
  Id：(141)          Hex：(#6b7373)
  Id：(142)          Hex：(#182929)
  Id：(143)          Hex：(#18424a)
  Id：(144)          Hex：(#31424a)
  Id：(145)          Hex：(#63c6de)
  Id：(146)          Hex：(#44ddff)
  Id：(147)          Hex：(#8cd6ef)
  Id：(148)          Hex：(#736b39)
  Id：(149)          Hex：(#f7de39)
  Id：(150)          Hex：(#f7ef8c)
  Id：(151)          Hex：(#f7e700)
  Id：(152)          Hex：(#6b6b5a)
  Id：(153)          Hex：(#5a8ca5)
  Id：(154)          Hex：(#39b5ef)
  Id：(155)          Hex：(#4a9cce)
  Id：(156)          Hex：(#3184b5)
  Id：(157)          Hex：(#31526b)
  Id：(158)          Hex：(#deded6)
  Id：(159)          Hex：(#bdbdb5)
  Id：(160)          Hex：(#8c8c84)
  Id：(161)          Hex：(#f7f7de)
  Id：(162)          Hex：(#000818)
  Id：(163)          Hex：(#081839)
  Id：(164)          Hex：(#081029)
  Id：(165)          Hex：(#081800)
  Id：(166)          Hex：(#082900)
  Id：(167)          Hex：(#0052a5)
  Id：(168)          Hex：(#007bde)
  Id：(169)          Hex：(#10294a)
  Id：(170)          Hex：(#10396b)
  Id：(171)          Hex：(#10528c)
  Id：(172)          Hex：(#215aa5)
  Id：(173)          Hex：(#10315a)
  Id：(174)          Hex：(#104284)
  Id：(175)          Hex：(#315284)
  Id：(176)          Hex：(#182131)
  Id：(177)          Hex：(#4a5a7b)
  Id：(178)          Hex：(#526ba5)
  Id：(179)          Hex：(#293963)
  Id：(180)          Hex：(#4169E1)
  Id：(181)          Hex：(#292921)
  Id：(182)          Hex：(#4a4a39)
  Id：(183)          Hex：(#292918)
  Id：(184)          Hex：(#4a4a29)
  Id：(185)          Hex：(#7b7b42)
  Id：(186)          Hex：(#9c9c4a)
  Id：(187)          Hex：(#5a5a29)
  Id：(188)          Hex：(#424214)
  Id：(189)          Hex：(#393900)
  Id：(190)          Hex：(#595900)
  Id：(191)          Hex：(#ca352c)
  Id：(192)          Hex：(#6b7321)
  Id：(193)          Hex：(#293100)
  Id：(194)          Hex：(#313910)
  Id：(195)          Hex：(#313918)
  Id：(196)          Hex：(#424a00)
  Id：(197)          Hex：(#526318)
  Id：(198)          Hex：(#5a7329)
  Id：(199)          Hex：(#314a18)
  Id：(200)          Hex：(#182100)
  Id：(201)          Hex：(#183100)
  Id：(202)          Hex：(#183910)
  Id：(203)          Hex：(#63844a)
  Id：(204)          Hex：(#6bbd4a)
  Id：(205)          Hex：(#63b54a)
  Id：(206)          Hex：(#63bd4a)
  Id：(207)          Hex：(#5a9c4a)
  Id：(208)          Hex：(#4a8c39)
  Id：(209)          Hex：(#63c64a)
  Id：(210)          Hex：(#63d64a)
  Id：(211)          Hex：(#52844a)
  Id：(212)          Hex：(#317329)
  Id：(213)          Hex：(#63c65a)
  Id：(214)          Hex：(#52bd4a)
  Id：(215)          Hex：(#10ff00)
  Id：(216)          Hex：(#182918)
  Id：(217)          Hex：(#4a884a)
  Id：(218)          Hex：(#4ae74a)
  Id：(219)          Hex：(#005a00)
  Id：(220)          Hex：(#008800)
  Id：(221)          Hex：(#009400)
  Id：(222)          Hex：(#00de00)
  Id：(223)          Hex：(#00ee00)
  Id：(224)          Hex：(#00fb00)
  Id：(225)          Hex：(#4a5a94)
  Id：(226)          Hex：(#6373b5)
  Id：(227)          Hex：(#7b8cd6)
  Id：(228)          Hex：(#6b7bd6)
  Id：(229)          Hex：(#7788ff)
  Id：(230)          Hex：(#c6c6ce)
  Id：(231)          Hex：(#94949c)
  Id：(232)          Hex：(#9c94c6)
  Id：(233)          Hex：(#313139)
  Id：(234)          Hex：(#291884)
  Id：(235)          Hex：(#180084)
  Id：(236)          Hex：(#4a4252)
  Id：(237)          Hex：(#52427b)
  Id：(238)          Hex：(#635a73)
  Id：(239)          Hex：(#ceb5f7)
  Id：(240)          Hex：(#8c7b9c)
  Id：(241)          Hex：(#7722cc)
  Id：(242)          Hex：(#ddaaff)
  Id：(243)          Hex：(#f0b42a)
  Id：(244)          Hex：(#df009f)
  Id：(245)          Hex：(#e317b3)
  Id：(246)          Hex：(#fffbf0)
  Id：(247)          Hex：(#a0a0a4)
  Id：(248)          Hex：(#808080)
  Id：(249)          Hex：(#ff0000)
  Id：(250)          Hex：(#00ff00)
  Id：(251)          Hex：(#ffff00)
  Id：(252)          Hex：(#4169E1)
  Id：(253)          Hex：(#ff00ff)
  Id：(254)          Hex：(#00ffff)
  Id：(255)          Hex：(#ffffff)
```

**------------**
# 音效
#### 播放按钮点击音效
- `SL:PlayBtnClickAudio()`

#### 播放音效
- `SL:PlaySound(id, isLoop)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|id  |是 |int|cfg_sound表对应id|
|isLoop|否 |boolean|是否循环|

#### 播放登陆-选角音效
- `SL:PlaySelectRoleAudio()`

#### 播放开宝箱音效 [3.40.6版本]
- `SL:PlayOpenBoxAudio()`

#### 播放宝箱内选中音效 [3.40.6版本]
- `SL:PlayFlashBoxAudio()`

#### 停止音效
- `SL:StopSound(id)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|id  |是 |int|cfg_sound表对应id|

#### 停止所有音效
- `SL:StopAllAudio()`

**------------**
# 聊天
#### 发送文本显示到聊天页输入框
- `SL:SendInputMsgToChat(str)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|str  |是 |string|文本内容|

------------
#### 发送[普通消息]到聊天 [3.40.2版本]
- `SL:SendNormalMsgToChat(msg, channel)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|msg  	   |是 |string|消息内容|
|channel   |否 |int|设置频道, 不设置默认当前聊天频道|

------------
#### 发送[系统提示]到聊天框 [3.40.2版本]
- `SL:SendSystemMsgToChat(data)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|data  	   |是 |table|Msg: 提示内容<br> FColor: 字体颜色ID <br> BColor: 背景颜色ID|

```
	local mdata = {
		Msg        = string.format("自动移动坐标点(%s:%s)不可到达", mapX, mapY),
		FColor     = 154,
		BColor     = 255,
	}
	SL:SendSystemMsgToChat(mdata)
```

------------
#### 发送[装备]到聊天
- `SL:SendEquipMsgToChat(itemData, channel)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|itemData  |是 |table|装备数据|
|channel   |否 |int|设置频道, 不设置默认当前聊天频道|

------------
#### 发送[位置]到聊天
- `SL:SendPosMsgToChat(channel)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|channel   |否 |int|设置频道, 不设置默认当前聊天频道|

------------
#### 发送[表情]到聊天
- `SL:SendEmojiMsgToChat(data, channel)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|data |是 |table |表情配置      |
|channel   |否 |int|设置频道, 不设置默认当前聊天频道|

------------
#### 私聊目标
- `SL:PrivateChatWithTarget(targetID, targetName)`

|参数名|必选|类型|说明|
|:--        |:- |:--    |-----        |
|targetID   |是 |string |目标玩家ID    |
|targetName |是 |string |目标玩家名字  |

------------
#### 新增本地掉落消息到聊天 [3.40.7版本] 
- `SL:AddDropChatMsgShow(data)`

|参数名|必选|类型|说明|
|:--  |:- |:---  |-----        |
|data  	   |是 |table|Msg: 掉落内容富文本<br> FColor: 字体颜色ID <br> BColor: 背景颜色ID <br> dropType: 掉落分类ID (1-10)|

例: 
```
	SL:AddDropChatMsgShow({
        FColor = 253,
        BColor = 255,
        Msg = "测试掉落<outline size='1' color='#000'><font color='#ffffff'>物品 </font><font color='#ffffff'> 从 </font><font color='#28ef01'>一只牛</font><font color='#ffffff'> 身上掉落在 </font><font color='#FFA500'>盟重省(222,333)</font><font color='#ffffff'> 附近</font></outline>",
        dropType = 1,
    })
```

**------------**
# 资源下载
- `SL:DownLoadRes(path, url, downloadCB)`

|参数名|必选|类型|说明|
|:--        |:- |:--      |-----         |
|path       |是 |string   |保存的文件路径 |
|url        |是 |string   |下载资源地址  |
|downloadCB |否 |function |回调函数      |

#### 小地图资源下载
- `SL:DownloadMiniMapRes(mapId, callback)`

|参数名|必选|类型|说明|
|:--        |:- |:--      |-----   |
|mapId      |是 |int      |小地图Id |
|callback   |是 |function |回调函数 |

```
    local function callBack(isOk, path) -- isOk 下载是否成功, path 返回小地图路径 
        if isOk then 
            print("下载成功")
        else 
            print("下载失败")
        end 
        print("小地图路径",path)
    end 
    SL:DownloadMiniMapRes(100, callBack)
```

### 删除GM缓存资源 [3.40.6版本]
- `SL:RemoveGMResFile(filePath)`

|参数名|必选|类型|说明|
|:--        |:- |:--      |-----         |
|filePath       |是 |string   |文件路径 |

**---------------**
# Actor
------------
#### 清空选中目标actor
- `SL:ClearTarget()`

------------
#### 快速选择目标
- `SL:QuickSelectTarget(data)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|data |是  |table|type:<br>&emsp;0: 玩家<br>&emsp;50: 怪物<br>&emsp;400: 英雄<br>imgNotice: 没有目标时是否创建范围圈<br>systemTips: 没有目标时是否弹提示|

------------
#### 获取视野内的玩家
- `SL:FindPlayerInCurrViewField(noMainPlayer)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|noMainPlayer |否|boolean  |false: 包含自己， 反之不包含|

- 返回值：table

------------
#### 获取视野内的怪物
- `SL:FindMonsterInCurrViewField(noPetOfMainPlayer, noPetOfNetPlayer)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|noPetOfMainPlayer |否|boolean  |true: 不包含自己的宠物， 反之包含|
|noPetOfNetPlayer  |否|boolean  |false: 包含别人的宠物， 反之不包含|

- 返回值：table

------------
#### 控件加入到元变量自动刷新的组件
- `SL:CustomAttrWidgetAdd(metaValue, widget)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|metaValue |是 |string|传入已配置元变量的字符串 <br>&<元变量KEY/参数>& <br>例 : <br> 红点变量U91: &<REDKEY/U91>& <br>角色名: &<USER_NAME>& |
|widget|是|object|文本控件 Text|

- 示例
```
	local Text_count = GUI:Text_Create(GUI:Attach_LeftBottom(), "MONEY_COUNT", 200, 100, 16, "#00FF00", "")
    SL:CustomAttrWidgetAdd("元宝数量: &<TMONEY/元宝>&", Text_count)
	-- 多货币
	-- SL:CustomAttrWidgetAdd("货币1,2总数量: &<TMONEY/1,2>&", Text_count)
```

------------
#### 检测控件是否可视 (用于检测在列表/滚动容器内控件)
- `SL:CheckNodeCanCallBack(node, touchPos)`
- 默认检测层数 : 6

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|node|是|object|控件 |
|touchPos|是|table|当前接触坐标|

- 示例

```
	GUI:addMouseMoveEvent(node, {
		onEnterFunc = function(touchPos)
			if SL:CheckNodeCanCallBack(node, touchPos) then
				local info = {
					str = "tttt",
					worldPos = touchPos,
				}
				SL:OpenCommonDescTipsPop(info)
			end
		end,
		onLeaveFunc = function()
			SL:CloseCommonDescTipsPop()
		end
	})
```

**------------**
# 提升按钮
#### 添加提升按钮
- `SL:AddUpgradeBtn(id, name, func)`

- 等同TXT脚本命令addbutshow

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|id |是 |int|按钮id 必须唯一!!!! (同脚本命令加的id也不能重复)|
|name|是|string|按钮展示文本|
|func|是|function|点击按钮跳转函数|

#### 删除提升按钮
- `SL:RemoveUpgradeBtn(id)`

- 等同TXT脚本命令delbutshow

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|id |是 |int|按钮id 必须唯一!!!! (同脚本命令加的id也不能重复)|

**------------**
# 鼠标模拟事件
#### 模拟左键点击事件
- `SL:WinClick(widget)`

|参数名|必选|说明|
|:----    |:---|-----|
|widget   |是  |控件对象|

**------------**
#坐标转换 [3.40.2版本]
#### 世界坐标转化为地图坐标
- `SL:ConvertWorldPos2MapPos(worldX, worldY)`

|参数名|必选|说明|
|:----    |:---|-----|
|worldX |是 |世界坐标X|
|worldY |是 |世界坐标Y|

#### 地图坐标转化为世界坐标
- `SL:ConvertMapPos2WorldPos(mapX, mapY, centerOfGrid)`

|参数名|必选|说明|
|:----    |:---|-----|
|mapX |是 |地图坐标X|
|mapY |是 |地图坐标Y|
|centerOfGrid|否| 是否在地图格中心|

#### 世界坐标转化为屏幕坐标
- `SL:ConvertWorldPos2Screen(worldX, worldY)`

|参数名|必选|说明|
|:----    |:---|-----|
|worldX |是 |世界坐标X|
|worldY |是 |世界坐标Y|

#### 屏幕坐标转化为世界坐标
- `SL:ConvertScreen2WorldPos(screenX, screenY)`

|参数名|必选|说明|
|:----    |:---|-----|
|screenX |是 |屏幕坐标X|
|screenY |是 |屏幕坐标Y|

**------------**
# 移动端交互 [3.40.2版本]
#### 打开QQ
- `SL:OpenQQ()`

#### 加QQ
- `SL:JoinQQ(id)`

|参数名|必选|说明|
|:----    |:---|-----|
|id |是 |QQ号|

#### 加QQ群
- `SL:JoinQQGroup(key)`

|参数名|必选|说明|
|:----    |:---|-----|
|key |是 |QQ群key|

#### 打开微信
- `SL:OpenWX()`

#### 添加地图特效 [3.40.4版本]
- `SL:AddMapSpecialEffect(ID, mapID, sfxId, x, y, loop)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|ID       |是 |int|该地图特效标识 必须唯一!!!! |
|mapID    |是 |string|添加到的地图ID|
|sfxId    |是 |int|特效ID|
|x        |是 |int|地图坐标X|
|y        |是 |int|地图坐标Y|
|loop     |否 |boolean|是否循环播放特效, 不填默认循环播放|
|showType |否 |int|显示位置 0:在后面 1: 在前面 [3.40.8版本新增]|

#### 删除地图特效 [3.40.4版本]
- `SL:RmvMapSpecialEffect(ID, mapID)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|ID       |是 |int|该地图特效标识 必须唯一!!!! |
|mapID    |是 |string|添加到的地图ID|

- 示例

```
	local mapID = SL:GetMetaValue("MAP_ID")
    SL:AddMapSpecialEffect(1111, mapID, 10, 295, 305)
```

#### 添加Actor特效 [3.40.5版本]
- `SL:AddActorEffect(actorID, sfxID, isFront, offX, offY)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|actorID  |是 |int|玩家id|
|sfxID    |是 |int|特效ID|
|isFront  |否 |boolen|是否在模型前  默认在前面|
|offX     |否 |int|x偏移|
|offY     |否 |int|y偏移|

#### 删除Actor特效  [3.40.5版本]
- `SL:RmvActorEffect(actorID, sfxID)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|actorID  |是 |int|玩家id|
|sfxID    |是 |int|特效ID|

#### 强攻 [3.40.7版本]
- `SL:ForceAttack()`

**------------**
# 请求类
#### 拉起充值
- `SL:RequestPay(payWay, currencyID, price, productIndex)`

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----|
|payWay |是 |int|1 支付宝 2 花呗 3 微信 -1不选择(手机端接入SDK不选择支付渠道)|
|currencyID|是|int|货币ID|
|price|是|int|支付金额|
|productIndex|是|int| 商品索引/商品ID|

#### 兑换激活码
- `SL:RequestCDK(cdk)`

|参数名|必选|说明|
|:----    |:---|-----|
|cdk |是 |激活码|

#### 请求改变PK模式
- `SL:RequestChangePKMode(pkmode)`

|参数名|必选|说明|
|:----    |:---|-----|
|pkmode |是 |pk模式|

#### 请求改变宠物战斗模式
- `SL:RequestChangePetPKMode(pkmode)`

|参数名|必选|说明|
|:----    |:---|-----|
|pkmode |是 |宝宝模式|

#### 请求从仓库取出道具
- `SL:RequestPutOutStorageData(data)`

|参数名|必选|说明|
|:----    |:---|-----|
|data |是 |table -- 道具数据|

#### 请求道具放入仓库
- `SL:RequestSaveItemToNpcStorage(data)`

|参数名|必选|说明|
|:----    |:---|-----|
|data |是 |table -- 道具数据|

#### 请求使用道具
- `SL:RequestUseItem(itemData)`

|参数名|必选|说明|
|:----    |:---|-----|
|itemData |是 |table -- 道具数据|

#### 请求使用英雄道具
- `SL:RequestUseHeroItem(itemData)`

|参数名|必选|说明|
|:----    |:---|-----|
|itemData |是 |table -- 道具数据|

#### 拆分道具
- `SL:RequestSplitItem(data, num)`

|参数名|必选|说明|
|:----    |:---|-----|
|data |是 |table -- 道具数据|
|num  |是 |int -- 数量|

#### 拆分道具(英雄)
- `SL:RequestSplitHeroItem(data, num)`

|参数名|必选|说明|
|:----    |:---|-----|
|data |是 |table -- 道具数据|
|num  |是 |int -- 数量|

#### 请求购买商品 [3.40.3版本]
- `SL:RequestStoreBuy(index, count)`

|参数名|必选|说明|
|:----    |:---|-----|
|index |是 |int -- 商品Index|
|count  |是 |int -- 购买数量|

#### 召唤英雄或收回
- `SL:RequestCallOrOutHero()`

#### 请求玩家首饰盒状态
- `SL:RequestOpenPlayerBestRings()`

#### 请求英雄首饰盒状态
- `SL:RequestOpenHeroBestRings()`

#### 请求宠物锁定
- `SL:RequestLockPetID(targetID)`

|参数名|必选|说明|
|:----    |:---|-----|
|targetID |是 |目标宠物ID|

#### 请求取消宠物锁定
- `SL:RequestUnLockPetID(targetID)`

|参数名|必选|说明|
|:----    |:---|-----|
|targetID |是 |目标宠物ID|

#### 释放技能
- `SL:RequestLaunchSkill(skillID)`

|参数名|必选|说明|
|:----    |:---|-----|
|skillID |是 |技能ID|

#### 请求施法合击
- `SL:RequestMagicJointAttack()`

#### 查看目标玩家信息
- `SL:RequestLookPlayer(targetId, notForbid)`

|参数名|必选|说明|
|:----    |:---|-----|
|targetID |是 |目标ID|
|notForbid|否 |boolean --是否不判断地图禁止查看|

#### 请求开关开关型技能 [3.40.7版本]
- `SL:RequestOnOffSkill(skillID)`

|参数名|必选|说明|
|:----    |:---|-----|
|skillID |是 |技能ID|

###行会
#### 请求行会申请列表
- `SL:RequestGuildAllyApplyList()`

#### 行会同盟申请操作
- `SL:RequestAllyOperate(guildID, param)`

|参数名|必选|说明|
|:----    |:---|-----|
|guildID |是 |行会ID|
|param|是 |操作编号 1同意 2拒绝|

#### 请求行会成员列表
- `SL:RequestGuildMemberList()`

#### 请求世界行会列表 
- `SL:RequestWorldGuildList(page)`

|参数名|必选|说明|
|:----    |:---|-----|
|page |是 |分页id|

#### 邀请玩家入会
- `SL:RequestGuildInviteOther(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 踢出行会
- `SL:RequestSubGuildMember(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 任命行会职位
- `SL:RequestAppointGuildRank(uid, rank)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|
|rank|是 |职位id 1-5|

### 组队
#### 请求创建队伍
- `SL:RequestCreateTeam()`

#### 邀请玩家入队
- `SL:RequestInviteJoinTeam(uid, name)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |否 |玩家id|
|name|否 [ 两参数必须填一个 ] |玩家昵称|

#### 拒绝组队邀请
- `SL:RequestRefuseTeamInvite(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 同意组队邀请
- `SL:RequestAgreeTeamInvite(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 同意申请入队
- `SL:RequestApplyAgree(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 请求入队申请列表
- `SL:RequestApplyData()`

#### 请求附近队伍
- `SL:RequestNearTeam()`

#### 请求加入队伍
- `SL:RequestApplyJoinTeam(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |队长id|

#### 召集队友
- `SL:RequestCallTeamMember()`

#### 离开队伍
- `SL:RequestLeaveTeam()`

#### 保存允许组队状态
- `SL:RequestSetTeamPermitStatus(status)`

|参数名|必选|说明|
|:----    |:---|-----|
|status |是 |int -- 1允许 0不允许|

#### 踢出队伍
- `SL:RequestSubTeamMember(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 移交队长
- `SL:RequestTransferTeamLeader(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

### 交易
#### 请求进行交易
- `SL:RequestTrade(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

### 好友
#### 请求好友列表
- `SL:RequestFriendList()`

#### 请求添加好友
- `SL:RequestAddFriend(uname)`

|参数名|必选|说明|
|:----    |:---|-----|
|uname|是 |玩家昵称|

#### 删除好友
- `SL:RequestDelFriend(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 好友加到黑名单
- `SL:RequestAddBlacklistByName(uname)`

|参数名|必选|说明|
|:----    |:---|-----|
|uname|是 |玩家昵称|

#### 移出黑名单
- `SL:RequestOutBlacklist(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

#### 同意好友申请
- `SL:RequestAgreeFriendApply(uname)`

|参数名|必选|说明|
|:----    |:---|-----|
|uname|是 |玩家昵称|

#### 删除好友申请数据
- `SL:RequestDelFriendApplyData(uname)`

|参数名|必选|说明|
|:----    |:---|-----|
|uname|是 |玩家昵称|

#### 清空好友申请列表
- `SL:RequestClearFriendApplyList()`

### 邮件
#### 请求获取邮件列表 一次十条
- `SL:RequestMailList()`

#### 删除已读邮件
- `SL:RequestDelReadMail()`

#### 读邮件
- `SL:RequestReadMail(mailId)`

|参数名|必选|说明|
|:----    |:---|-----|
|mailId|是 |邮件ID|

#### 删除邮件
- `SL:RequestDelMail(mailId)`

|参数名|必选|说明|
|:----    |:---|-----|
|mailId|是 |邮件ID|

#### 邮件全部提取
- `SL:RequestGetAllMailItems()`

#### 邮件提取
- `SL:RequestGetMailItems(mailId)`

|参数名|必选|说明|
|:----    |:---|-----|
|mailId|是 |邮件ID|

### 拍卖行
#### 请求拍卖行上架列表
- `SL:RequestAuctionPutList(listType)`

|参数名|必选|说明|
|:----    |:---|-----|
|listType|是 |int -- 1: 表示查询自己上架的物品，2: 表示查询参与过的|

#### 拍卖行请求上架
- `SL:RequestAuctionPutin(makeindex, count, bidPrice, buyPrice, currencyID, rebate)`

|参数名|必选|说明|
|:----    |:---|-----|
|makeindex|是 |物品唯一ID|
|count    |是 |数量|
|bidPrice |是 |竞拍价格|
|buyPrice |是 |一口价|
|currencyID|是 |货币ID|
|rebate   |否 |折扣|

#### 拍卖行请求下架
- `SL:RequestAuctionPutout(makeindex)`

|参数名|必选|说明|
|:----    |:---|-----|
|makeindex|是 |物品唯一ID|

#### 拍卖行请求重新上架
- `SL:RequestAuctionRePutin(makeindex, count, bidPrice, buyPrice, currencyID, rebate)`

|参数名|必选|说明|
|:----    |:---|-----|
|makeindex|是 |物品唯一ID|
|count    |是 |数量|
|bidPrice |是 |竞拍价格|
|buyPrice |是 |一口价|
|currencyID|是 |货币ID|
|rebate   |否 |折扣|

#### 拍卖行请求竞价
- `SL:RequestAuctionBid(makeindex, price)`

|参数名|必选|说明|
|:----    |:---|-----|
|makeindex|是 |物品唯一ID|
|price    |是 |竞拍价|

#### 拍卖行请求领取竞拍成功物品 [3.40.3版本]
- `SL:RequestAcquireBidItem(makeindex)`

|参数名|必选|说明|
|:----    |:---|-----|
|makeindex|是 |物品唯一ID|

### 排行榜
#### 请求排行榜数据
- `SL:RequestRankData(type)`

|参数名|必选|说明|
|:----    |:---|-----|
|type|是 |类别ID|

#### 请求玩家排行榜数据
- `SL:RequestPlayerRankData(userID, type)`

|参数名|必选|说明|
|:----    |:---|-----|
|userID   |是|玩家ID|
|type|是 |int -- 玩家/英雄 1玩家 2英雄|

### 任务
#### 提交任务
- `SL:RequestSubmitMission(missionID)`

|参数名|必选|说明|
|:----    |:---|-----|
|missionID |是|任务ID|

### 玩家
#### 请求玩家称号数据
- `SL:ResquestTitleList()`

#### 请求取下称号
- `SL:ResquestDisboardTitle()`

#### 请求激活称号
- `SL:ResquestActivateTitle(titleId)`

|参数名|必选|说明|
|:----    |:---|-----|
|titleId |是|称号id|

#### 通知服务端 时装显示开关
- `SL:SendSuperEquipSetting(type)`

|参数名|必选|说明|
|:----    |:---|-----|
|type |是|int -- 2 : 设置显示神魔<br> 1 : 设置时装显示|

### 英雄
#### 切换英雄状态
- `SL:RequestChangeHeroMode(type)`

|参数名|必选|说明|
|:----    |:---|-----|
|type |是|状态值|

#### 请求英雄称号数据
- `SL:ResquestTitleList_Hero()`

#### 英雄请求取下称号
- `SL:ResquestDisboardTitle_Hero()`

#### 英雄请求激活称号
- `SL:ResquestActivateTitle_Hero(titleId)`

|参数名|必选|说明|
|:----    |:---|-----|
|titleId |是|称号id|

#### 通知服务端 英雄时装显示开关
- `SL:SendSuperEquipSetting_Hero(type)`

|参数名|必选|说明|
|:----    |:---|-----|
|type |是|int -- 2 : 设置显示神魔<br> 1 : 设置时装显示|

#### 英雄请求锁定目标 [3.40.7版本]
- `SL:RequestLockTargetByHero(actorID, isPlayer)`

|参数名|必选|说明|
|:----    |:---|-----|
|actorID |是|actorID|
|isPlayer|是|boolean -- 是否人物|

#### 英雄取消锁定 [3.40.7版本]
- `SL:RequestCancelLockByHero()`

### 合成
#### 请求合成
- `SL:ResquestCompoundItem()`

#### 请求敏感词检测
- `SL:RequestCheckSensitiveWord(str, type, callback)`

|参数名|必选|说明|
|:----    |:---|-----|
|str |是|string -- 需要检测的文本|
|type|是|文本类型 int <br> 1 : 昵称类<br> 2 : 聊天类<br> 3 : 行会公告|
|callback|是|function -- 检测完毕的回调事件<br> 事件传入参数: param1: boolean 能否通过 param2: 文本 |

#### 邀请上马
- `SL:RequestInviteInHorse(uid)`

|参数名|必选|说明|
|:----    |:---|-----|
|uid |是 |玩家id|

### 小地图 [3.40.2版本]
#### 请求地图组队成员数据 
- `SL:RequestMiniMapTeam()`

#### 请求地图怪物数据 
- `SL:RequestMiniMapMonsters()`

### 内功 [3.40.2版本]
#### 请求内功技能数据
- `SL:RequestInternalSkillData(isHero)`

|参数名|必选|说明|
|:----    |:---|-----|
|isHero |否 |boolean -- 是否请求英雄|

#### 请求经络穴位激活
- `SL:RequestAucPointOpen(typeID, aucPointID, isHero)`

|参数名|必选|说明|
|:----    |:---|-----|
|typeID |是 |经络ID|
|aucPointID|是|穴位ID|
|isHero |否 |boolean -- 是否请求英雄|

#### 修炼经络
- `SL:RequestMeridianLevelUp(typeID, isHero)`

|参数名|必选|说明|
|:----    |:---|-----|
|typeID |是 |经络ID|
|isHero |否 |boolean -- 是否请求英雄|

#### 设置连击技能
- `SL:RequestSetComboSkill(key, skillID, isHero)`

|参数名|必选|说明|
|:----    |:---|-----|
|key    |是 |int -- 键位 (1, 2, 3, 4)|
|skillID|是 |技能ID|
|isHero |否 |boolean -- 是否请求英雄|

#### 请求设置内功条前置开关 并刷新显示 [3.40.8版本]
- `SL:RequestNGHudShow(show)`

|参数名|必选|说明|
|:----    |:---|-----|
|show    |是 |boolean -- 是否开启 默认true|

### 宝箱 [3.40.3版本]
#### 请求获取宝箱物品奖励
- `SL:RequestGetGoldBoxReward()`

#### 请求再开启宝箱
- `SL:RequestOpenGoldBox()`

### 属性加点 [3.40.4版本]
#### 请求确认加属性点 [新版属性加点]
- `SL:RequestAddReinAttr_N(data, m_nBonusPoint)`

|参数名|必选|说明|
|:----    |:---|-----|
|data    |是 |table -- 加点数据table `{"Bonus":[{"id":1,"value":1}, ...]}`|
|m_nBonusPoint|是 |int -- 剩余加点数|

### 求购 [3.40.5版本]
#### 请求求购数据 
- `SL:RequestPurchaseItemList(data)`

|参数名|必选|说明|
|:----    |:---|-----|
|data    |是 |table -- 请求参数|
```
	参数如下:
	{
		type 	   = 类型(int),					-- 0: 世界求购, 1: 我的求购, 2: 我的已收
		pageIndex   = 请求页码(int),
		stdmode 	= 筛选的stdmode(string),		-- #分隔需要筛选的stdmode  例: "1#2#3#4"
		currency	= 筛选货币(string), 			-- ,分隔需要筛选的货币ID 例: "1,2,3"
		sort		= 排序规则(int),				-- 0: 不排序 1: 单价正序 2: 单价倒序 3: 总价正序 4: 总价倒序
		itemids 	= 筛选道具idx(string),  		-- ,分隔筛选的道具Index 例: "1001,1002,1003"
	}
```

#### 请求求购出售物品
- `SL:RequestPurchaseSell(data)`

|参数名|必选|说明|
|:----    |:---|-----|
|data    |是 |table -- 请求参数 {guid = 求购列表标识id, qty = 出售数量}|

#### 请求上架求购物品
- `SL:RequestPurchasePutIn(data)`

|参数名|必选|说明|
|:----    |:---|-----|
|data    |是 |table -- 请求参数|

```
	参数如下: 
	{
		qty   	= 求购数量(int),
		minqty	= 求购最小数量(int),
		price 	= 物品单价(int),
		itemid	= 道具Index,
		currency  = 货币ID
	}
```

#### 请求下架求购物品
- `SL:RequestPurchasePutOut(guid)`

|参数名|必选|说明|
|:----    |:---|-----|
|guid |否|求购列表标识id, 不填则全部下架|

#### 请求取出求购已收物品
- `SL:RequestPurchaseTakeOut(guid)`

|参数名|必选|说明|
|:----    |:---|-----|
|guid |否|求购列表标识id, 不填则全部取出|

#### 请求点击NPC [3.40.5版本]
- `SL:RequestNPCTalk(npcID)`

|参数名|必选|说明|
|:----    |:---|-----|
|npcID |是|NPCID|


# GUILayout



#### &bull; 界面文件:

|UI ID|说明|
|:----|-----|
|MainLeftTop                            |主界面 左上|
|MainRightTop                           |主界面 右上|
|MainLeftBottom                         |主界面 左下|
|MainRightBottom                        |主界面 右下|
|MainMiniMap                            |主界面 小地图|
|MainAssist                             |主界面 导航栏|
|MainProperty                           |主界面 属性栏|
|MainSkill                              |主界面 技能/按钮|
|MainTarget                             |主界面 目标栏|
|MainTop                                |主界面 最上方|
|MainDig                                |主界面 尸体挖掘|
|MainSummons                            |主界面 召唤物|
|MainCollect							|主界面 采集怪|
|MainProperty_win32                     |PC 属性栏|
|MainAssist_win32                       |PC 导航栏|
|MainNear                         		|附近列表展示|
|MainBuffList							|主界面 buff图标配置展示|
|LoginRolePanel                         |人物登录界面|
|SettingFrame                           |设置 外框|
|SettingBasic                           |设置:基础|
|SettingWinRange                        |设置:视距|
|SettingLaunch                          |设置:战斗|
|SettingProtect                         |设置:保护|
|SettingProtectSetting                  |设置:保护相关设置|
|SettingAuto                            |设置:自动|
|SettingSkillRank                       |设置:技能优先级|
|SettingSkillPanel                      |设置:技能|
|SettingPickSetting                     |设置:拾取|
|SettingAddMonsterName                  |设置:增加怪物name|
|SettingAddMonsterType                  |设置:增加怪物type|
|SettingBossTips                        |设置:增加boss提醒|
|SettingHelp                            |设置:帮助|
|SettingFrame_win32                     |PC 设置:外框|
|SettingBasic_win32                     |PC 设置:基础|
|SettingLaunch_win32                    |PC 设置:战斗|
|SettingProtect_win32                   |PC 设置:保护|
|SettingAuto_win32                      |PC 设置:自动|
|SettingHelp_win32                      |PC 设置:帮助|
|GameWorldConfirm                       |游戏世界确认公告|
|GuildFrame                             |行会 外框|
|GuildList                              |行会列表|
|GuildMain                              |行会主界面|
|GuildCreate                            |行会创建|
|GuildMember                            |行会成员|
|GuildEditTitle                         |行会编辑|
|GuildApplyList                         |行会申请列表|
|GuildAllyApply                         |行会结盟申请列表|
|GuildWarSponsor                        |宣战、结盟结盟|
|GUIShare                        		|客户端默认配置|
|FuncDock                               |功能菜单|
|SocialFrame                            |社交 外框|
|Mail                                   |邮件|
|NearPlayer                             |附近|
|Team                                   |组队|
|Friend                                 |好友|
|TeamApply                              |组队申请|
|TeamInvite                             |组队邀请|
|FriendApply                            |好友申请|
|FriendAdd                              |添加好友|
|FriendAddBlacklist                     |添加黑名单|
|TeamBeInvitedPop                       |被邀请组队弹窗|
|PlayerFrame                            |玩家:人物面板外框|
|PlayerEquip                            |玩家:装备|
|PlayerBaseAtt                          |玩家:基础属性|
|PlayerExtraAtt                         |玩家:额外属性|
|PlayerSkill                            |玩家:技能|
|PlayerSkillSetting                     |技能设置|
|PlayerTitle                            |玩家:称号|
|TitleTips                              |称号提示|
|PlayerSuperEquip                       |玩家:神装|
|PlayerBestRing                         |玩家:生肖|
|PlayerInternalState                    |玩家:内功状态|
|PlayerInternalSkill                    |玩家:内功技能|
|PlayerInternalMeridian                 |玩家:内功经络|
|PlayerInternalCombo                    |玩家:内功连击|
|HeroFrame                              |英雄:主界面|
|HeroEquip                              |英雄:装备|
|HeroBaseAtt                            |英雄:基础属性|
|HeroExtraAtt                           |英雄:额外属性|
|HeroSkill                              |英雄:技能|
|HeroTitle                              |英雄:称号|
|HeroSuperEquip                         |英雄:神装|
|HeroBestRing                           |英雄:生肖|
|HeroInternalState                      |英雄:内功状态|
|HeroInternalSkill                      |英雄:内功技能|
|HeroInternalMeridian                   |英雄:内功经络|
|HeroInternalCombo                      |英雄:内功连击|
|PlayerFrame_Look                       |他人:玩家:主界面|
|PlayerEquip_Look                       |他人:玩家:装备|
|PlayerTitle_Look                       |他人:玩家:称号|
|TitleTips_Look                         |他人:称号提示|
|PlayerSuperEquip_Look                  |他人:玩家:神装|
|PlayerBestRing_Look                    |他人:玩家:生肖|
|HeroFrame_Look                         |他人:英雄:主界面|
|HeroEquip_Look                         |他人:英雄:装备|
|HeroTitle_Look                         |他人:英雄:称号|
|HeroSuperEquip_Look                    |他人:英雄:神装|
|HeroBestRing_Look                      |他人:英雄:生肖|
|MergePlayerFrame                       |人物和英雄二合一外框|
|LookMergePlayerMain                    |他人:人物和英雄二合一外框|
|HeroState                              |英雄状态|
|HeroStateSelect                        |英雄状态设置|
|HeroStateThreeSelect                   |英雄状态设置|
|PlayerHeroFrame_Look_TradingBank       |交易行:玩家:主界面|
|PlayerEquip_Look_TradingBank           |交易行:玩家:装备|
|PlayerBaseAtt_Look_TradingBank         |交易行:玩家:基础属性|
|PlayerExtraAtt_Look_TradingBank        |交易行:玩家:额外属性|
|PlayerSkill_Look_TradingBank           |交易行:玩家:技能|
|PlayerSuperEquip_Look_TradingBank      |交易行:玩家:神装|
|PlayerTitle_Look_TradingBank           |交易行:玩家:称号|
|PlayerBestRing_Look_TradingBank        |交易行:玩家:生肖|
|HeroEquip_Look_TradingBank             |交易行:英雄:装备|
|HeroBaseAtt_Look_TradingBank           |交易行:英雄:基础属性|
|HeroExtraAtt_Look_TradingBank          |交易行:英雄:额外属性|
|HeroSkill_Look_TradingBank             |交易行:英雄:技能|
|HeroSuperEquip_Look_TradingBank        |交易行:英雄:神装|
|HeroTitle_Look_TradingBank             |交易行:英雄:称号|
|HeroBestRing_Look_TradingBank          |交易行:英雄:生肖|
|TradingBankFrame                       |交易行主界面|
|Bag                                    |玩家:背包|
|BagItem                                |玩家:背包道具|
|BagItemText                            |玩家:背包文字|
|BagItemEffect                          |玩家:背包特效|
|HeroBag                                |英雄:背包|
|MergeBag                               |玩家、英雄:背包合并|
|Storage                                |仓库|
|NPCStore                               |NPC商店|
|NPCMakeDrug                            |炼药|
|NPCSellRepaire                         |出售或修理|
|ProgressBar                            |NPC 进度条|
|AuctionMain                            |拍卖行主界面|
|AuctionWorld                           |世界拍卖、行会拍卖|
|AuctionBidding                         |我的竞拍|
|AuctionPutList                         |我的上架|
|AuctionPutin                           |上架道具|
|AuctionTimeout                         |超时|
|AuctionPutout                          |下架道具|
|AuctionBid                             |竞拍|
|AuctionBuy                             |购买|
|Stall                                  |摆摊|
|StallSet                               |摆摊:请输入商户信息|
|StallPut                               |摆摊:确认界面|
|Trade                                  |交易|
|TradeTips                              |交易弹窗|
|Rank                                   |排行榜|
|StoreFrame                             |商城外框|
|StorePage                              |商城内容|
|StoreDetail                            |商城快捷购买|
|StoreRecharge                          |商城充值|
|RechargeQRCode                         |充值二维码|
|AutoUsePop                             |自动使用|
|CommonBubbleInfo                       |被多人邀请组队、交易|
|CommonTipsPop                          |通用弹窗|
|CommonDescTips                         |通用描述tips|
|ItemSplitPop                           |道具拆分弹窗|
|TreasureBox                            |宝箱道具|
|GoldBox                                |宝箱|
|ItemTips                               |道具tips|
|Chat                                   |聊天|
|ChatExtend                             |聊天拓展框|
|PrivateChat_win32                      |PC私聊记录|
|Notice                                 |系统类通知|
|MainMonster                            |怪物大血条|
|MonsterBelongNetPlayer                 |快捷选中归属|
|CompoundItem                           |合成|
|Item                                   |物品框|
|ReinAttr                               |转生加点|
|SetWinSizePop                          |设置分辨率|
|CommonQuestion                         |答题|
|CommonVerification                     |验证|
|CommonSelectList                       |选择下拉栏|
|MiniMap                                |小地图|
|UIModel                                |内观模型|
|BeStrongUp                             |提升按钮|
|LoginServer                            |登录账号 开门动画|
|LoginAccount                           |登录账号|
|GUIFunction                            |常用方法模块|
|Notice                                 |系统类通知|
|PurchaseMain                           |求购主面板|
|PurchaseWorld                          |世界求购|
|PurchaseMy                             |我的求购|
|PurchaseSell                           |求购出售|
|PurchasePutIn                          |求购上架|
|GUIUtil                                |进入游戏最开始加载该文件,  在主界面加载之前<br>优先于原先的ssr/ssrgame/ssrmain.lua<br>！优先于LUA_EVENT_ENTER_WORLD 进游戏事件|


# 游戏事件


##派发事件
`SL:onLUAEvent(eventID, data)`

- 说明

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|eventID |是  |string | 事件ID|
|data |否  |any | 数据|

- 返回值: 无

- 示例代码
<pre><code class="lua hljs">
	SL:onLUAEvent(LUA_EVENT_EXPCHANGE, {value = 100})
</code>
</pre>

**------------**
##注册游戏事件回调
`SL:RegisterLUAEvent(eventID, eventTag, eventCB, widget)`

- 说明

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|eventID |是  |string | 事件ID|
|eventTag |是  |string | 事件描述|
|eventCB|是  |function | 回调函数|
|widget      |否|obj|界面对象|

- 返回值: 无

- 示例代码
<pre><code class="lua hljs">
	local function onRefAttr()
		SL:Print("属性刷新...")
	end
    SL:RegisterLUAEvent(LUA_EVENT_EXPCHANGE, "属性刷新", onRefAttr)
</code>
</pre>

**------------**

##注销游戏事件回调
`SL:UnRegisterLUAEvent(eventID, eventTag)`

- 说明

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|eventID |是  |string | 事件ID|
|eventTag |是  |string | 事件描述|

- 返回值: 无

- 示例代码
<pre><code class="lua hljs">
    SL:UnRegisterLUAEvent(LUA_EVENT_EXPCHANGE, "属性刷新")
</code>
</pre>

**------------**

## 事件ID
|事件ID|说明|参数|
|:----|-----|-----|
|LUA_EVENT_ROLE_PROPERTY_INITED  |   玩家角色属性初始化完毕| 无|
|LUA_EVENT_ROLE_PROPERTY_CHANGE  |   玩家属性变化时| 无|
|LUA_EVENT_LEVELCHANGE           |   等级改变|table -- {currlevel = 当前等级, lastlevel = 上次等级} |
|LUA_EVENT_REINLEVELCHANGE		 |   转生等级改变|table -- {currReinLevel = 当前转生等级, lastReinLevel = 上次转生等级} |
|LUA_EVENT_HPMPCHANGE            |   HP/MP改变|table -- {curHP = curHP, maxHP = maxHP, curMP = curMP, maxMP = maxMP}|
|LUA_EVENT_EXPCHANGE             |   EXP改变|table -- {currexp = 当前经验值, changed = 改变值}|
|LUA_EVENT_BATTERYCHANGE         |   电池电量改变|int -- 电池容量百分比值
|LUA_EVENT_NETCHANGE             |   网络状态改变|int -- 网络类型 <br>-1: 未知 0: wifi 1: 蜂窝
|LUA_EVENT_WEIGHTCHANGE			 |   负重改变|table -- {weight = 当前负重, wearWeight = 穿戴负重, handWeight = 腕力}
|LUA_EVENT_PKMODECHANGE          |   pk模式改变|int -- 当前PK模式|
|LUA_EVENT_AFKBEGIN              |   自动挂机开始||
|LUA_EVENT_AFKEND                |   自动挂机结束||
|LUA_EVENT_AUTOMOVEBEGIN         |   自动寻路开始|table -- {mapID = 目标地图ID, x = 目标坐标X, y = 目标坐标Y}|
|LUA_EVENT_AUTOMOVEEND           |   自动寻路结束||
|LUA_EVENT_AUTOPICKBEGIN         |   自动捡物开始||
|LUA_EVENT_AUTOPICKEND           |   自动捡物结束||
|LUA_EVENT_MAINBUFFUPDATE        |   主玩家buff刷新|table -- {actorID = 玩家id, buffID = buffID, type = 类型(0: 删除 1: 新增 2: 刷新)}|
|LUA_EVENT_BUFFUPDATE            |   通用buff刷新|table -- {actorID = 玩家id, buffID = buffID, type = 类型(0: 删除 1: 新增 2: 刷新)}|
|LUA_EVENT_TALKTONPC             |   与NPC对话|table -- {UserID = npcID, index = NPC配置ID, name = NPC名称}|
|LUA_EVENT_CHANGESCENE           |   切换地图(包含同地图)|table -- {mapID = mapID}|
|LUA_EVENT_MAPINFOCHANGE         |   切换地图(不同地图)|table -- {mapID = mapID, lastMapID = lastMapID}|
|LUA_EVENT_MAPINFOINIT			 |   地图初始化|table -- {mapID = mapID}|
|LUA_EVENT_MAP_STATE_CHANGE      |   地图状态改变|boolen -- 是否在安全区域|
|LUA_EVENT_MAP_SIEGEAREA_CHANGE  |   地图攻城区域状态改变|boolean -- 是否进入攻城区域|支持版本号3.40.5以上|
|LUA_EVENT_CLOSEWIN              |   关闭界面|string -- GUI界面ID|
|LUA_EVENT_WINDOW_CHANGE         |   窗体尺寸改变||
|LUA_EVENT_DEVICE_ROTATION_CHANGED|  设备方向改变||
|LUA_EVENT_MONEYCHANGE           |   货币变化| table -- {id = 货币ID, count = 货币值}|
|LUA_EVENT_GUILD_MAIN_INFO       |   行会信息刷新||
|LUA_EVENT_GUILD_CREATE          |   行会创建消耗||
|LUA_EVENT_GUILD_WORLDLIST       |   世界行会列表刷新||
|LUA_EVENT_GUILD_APPLYLIST       |   入会申请列表刷新||
|LUA_EVENT_GUILDE_ALLY_APPLY_UPDATE| 结盟申请列表刷新||
|LUA_EVENT_TRADE_MONEY_CHANGE    |   对方交易货币改变|table -- {count = 货币数量}|
|LUA_EVENT_TRADE_MY_MONEY_CHANGE |   自己交易货币改变|table -- {count = 货币数量}|
|LUA_EVENT_TRADE_STATUS_CHANGE   |   对方交易状态改变||
|LUA_EVENT_TRADE_MY_STATUS_CHANGE|   自己交易状态改变||
|LUA_EVENT_ADDFIREND             |   添加好友|string -- 好友名|
|LUA_EVENT_REMFIREND             |   删除好友|string -- 好友名|
|LUA_EVENT_JOINTEAM              |   加入队伍|string -- 成员名|
|LUA_EVENT_LEAVETEAM             |   离开队伍|string -- 成员名|
|LUA_EVENT_REF_ITEM_LIST         |   刷新背包道具列表||
|LUA_EVENT_PLAYER_EQUIP_CHANGE   |   角色装备数据操作|table -- {MakeIndex = 唯一ID, Where = 装备位置, opera = 操作类型 ( 0:初始化 1:增加 2:删除 3:改变), ItemData = 装备数据}|
|LUA_EVENT_BAG_ITEM_CHANGE       |   背包数据变化| {opera = 操作类型 ( 0:初始化 1:增加 2:删除 3:改变), operID = 物品数据(table)}|
|LUA_EVENT_REF_HERO_ITEM_LIST    |   刷新英雄背包道具列表||
|LUA_EVENT_HERO_EQUIP_CHANGE     |   英雄装备变化|table -- {MakeIndex = 唯一ID, Where = 装备位置, opera = 操作类型 ( 0:初始化 1:增加 2:删除 3:改变), ItemData = 装备数据}|
|LUA_EVENT_HERO_BAG_ITEM_CAHNGE  |   英雄背包数据变化| {opera = 操作类型 ( 0:初始化 1:增加 2:删除 3:改变), operID = 物品数据(table)}|
|LUA_EVENT_DISCONNECT            |   断线||
|LUA_EVENT_RECONNECT             |   重连||
|LUA_EVENT_TAKE_ON_EQUIP         |   玩家穿戴装备|table -- {isSuccess = 是否成功, pos = 成功穿戴装备位}|
|LUA_EVENT_TAKE_OFF_EQUIP        |   玩家脱掉装备|table -- {isSuccess = 是否成功, pos = 成功脱下装备位}|
|LUA_EVENT_HERO_TAKE_ON_EQUIP    |   英雄穿戴装备|table -- {isSuccess = 是否成功}|
|LUA_EVENT_HERO_TAKE_OFF_EQUIP   |   英雄脱掉装备|table -- {isSuccess = 是否成功}|
|LUA_EVENT_SETTING_CAHNGE        |   设置项改变||
|LUA_EVENT_BESTRINGBOX_STATE     |   首饰盒状态改变||
|LUA_EVENT_ACTOR_IN_OF_VIEW      |   玩家/怪物/NPC进视野|table -- {id = ActorID}|支持版本号3.40.3以上|
|LUA_EVENT_ACTOR_OUT_OF_VIEW     |   玩家/怪物/NPC出视野|table -- {id = ActorID}|支持版本号3.40.3以上|
|LUA_EVENT_DROPITEM_IN_OF_VIEW      |   掉落物进视野|table -- {actorID = ActorID, item = 掉落物相关数据(table)}|支持版本号3.40.5以上|
|LUA_EVENT_DROPITEM_OUT_OF_VIEW     |   掉落物出视野|table -- {actorID = ActorID}|支持版本号3.40.5以上|
|LUA_EVENT_TARGET_HP_CHANGE      |   目标血量变化|table -- {actorID = 目标ID}|
|LUA_EVENT_TARGET_CAHNGE         |   目标改变|int -- 目标ID|
|LUA_EVENT_ACTOR_OWNER_CHANGE    |   目标归属改变|table -- {actorID = 目标ID}
|LUA_EVENT_HERO_ANGER_CAHNGE     |   英雄怒气改变|table -- {forceRefresh = boolean(true时禁止刷新)}
|LUA_EVENT_PLAYER_BEHAVIOR_STATE_CAHNGE|玩家行为状态改变（站立、走、跑等）|int -- 主玩家动作
|LUA_EVENT_PLAYER_ACTION_BEGIN   |主玩家行为动作开始（站立、走、跑等）|table -- {id = 玩家ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_ACTION_COMPLETE|主玩家行为动作结束（站立、走、跑等）|table -- {id = 玩家ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_NET_PLAYER_ACTION_BEGIN|网络玩家行为动作开始（站立、走、跑等）|table -- {id = 玩家ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_NET_PLAYER_ACTION_COMPLETE|网络玩家行为动作结束（站立、走、跑等）|table -- {id = 玩家ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_MONSTER_ACTION_BEGIN|怪物行为动作开始（站立、走、跑等）|table -- {id = 怪物ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_MONSTER_ACTION_COMPLETE|怪物行为动作结束（站立、走、跑等）|table -- {id = 怪物ID, act = 动作ID}|支持版本号3.40.2以上|
|LUA_EVENT_ACTOR_GMDATA_UPDATE   |   玩家/怪物 GM自定义数据改变|table -- {id = ActorID, data = GM自定义数据}|支持版本号3.40.3以上|
|LUA_EVENT_SKILL_INIT            |   初始化技能|table -- 技能数据
|LUA_EVENT_SKILL_ADD             |   新增技能|table -- 技能数据
|LUA_EVENT_SKILL_DEL             |   删除技能|table -- 技能数据
|LUA_EVENT_SKILL_UPDATE          |   技能更新|table -- 技能数据
|LUA_EVENT_SKILL_ONOFF           |   开关型技能开关触发|table -- {skillID = 技能ID, isOn = boolen 是否开启}| 支持版本号3.40.8以上|
|LUA_EVENT_SUMMON_MODE_CHANGE    |   召唤物-状态改变|table -- {mode = int( 2:战斗 4:休息)}
|LUA_EVENT_SUMMON_ALIVE_CHANGE   |   召唤物-存活状态改变|table -- {status = boolean(是否存活)}
|LUA_EVENT_BUBBLETIPS_STATUS_CHANGE|   气泡状态改变|table -- {id = 气泡id, status = 气泡状态 (boolean true: 加, false: 删), callback = function 气泡点击回调函数}
|LUA_EVENT_PLAY_MAGICBALL_EFFECT |   脚本魔血球动画|table -- 各项参数
|LUA_EVENT_AUTOFIGHT_TIPS_SHOW   |   自动战斗提示显示与否|boolean
|LUA_EVENT_AUTOMOVE_TIPS_SHOW    |   自动寻路提示显示与否|boolean
|LUA_EVENT_AUTOPICK_TIPS_SHOW    |   自动捡物提示显示与否|boolean
|LUA_EVENT_HERO_LOGIN_OROUT      |   英雄登录/登出|boolean true:登录, false:登出
|LUA_EVENT_REIN_ATTR_CHANGE      |   转生点数据变化||
|LUA_EVENT_ASSIST_MISSION_TOP    |   主界面-辅助-任务置顶|int -- 置顶id|
|LUA_EVENT_ASSIST_MISSION_ADD    |   主界面-辅助-任务增加|table -- 任务数据|
|LUA_EVENT_ASSIST_MISSION_CHANGE |   主界面-辅助-任务改变|table -- 任务数据|
|LUA_EVENT_ASSIST_MISSION_REMOVE |   主界面-辅助-任务移除|table -- 任务数据|
|LUA_EVENT_ASSIST_MISSION_SHOW   |   主界面-辅助-任务显示和隐藏|boolean 是否显示任务栏|
|LUA_EVENT_TEAM_MEMBER_UPDATE    |   主界面-辅助-队伍刷新||
|LUA_EVENT_TEAM_NEAR_UPDATE      |   附近队伍刷新||
|LUA_EVENT_TEAM_APPLY_UPDATE     |   申请入队列表刷新||
|LUA_EVENT_RANK_PLAYER_UPDATE    |   排行榜个人数据刷新|table -- 选中排行榜个人数据|
|LUA_EVENT_RANK_DATA_UPDATE      |   排行榜分类数据刷新|int -- 分类ID|
|LUA_EVENT_BIND_MAINPLAYER       |   绑定主玩家||
|LUA_EVENT_PLAYER_MAPPOS_CHANGE  |   主玩家位置改变||
|LUA_EVENT_FRIEND_LIST_UPDATE    |   好友列表刷新||
|LUA_EVENT_FRIEND_APPLY          |   收到好友申请||支持版本号3.40.2以上|
|LUA_EVENT_MAIL_UPDATE           |   邮件列表刷新||
|LUA_EVENT_ITEMTIPS_MOUSE_SCROLL |   ITEMTIPS鼠标滚轮滚动|滚动位置 table -- {x = x, y = y}
|LUA_EVENT_PCMINIMAP_STATUS_CHANGE|  PC 主界面小地图展示状态改变|int -- 展示状态 <br>0: 不显示<br>1: 小地图尺寸1<br>2: 小地图尺寸2<br> 3: 打开小地图界面|
|LUA_EVENT_DARK_STATE_CHANGE     |   黑夜状态改变||
|LUA_EVENT_MONSTER_IGNORELIST_ADD|   设置-怪物忽略列表增加|string -- 怪物名字
|LUA_EVENT_BOSSTIPSLIST_ADD      |   设置-boss提示-增加|table -- { 怪物名字, 1, "BOSS" }
|LUA_EVENT_MONSTER_NAME_RM       |   设置-怪物类型删除|int -- 怪物类型
|LUA_EVENT_SKILL_RANKDATA_ADD    |   设置-技能数据添加|table -- 技能数据
|LUA_EVENT_SKILLBUTTON_DISTANCE_CHANGE|   技能边距调整||
|LUA_EVENT_PLAYER_FRAME_PAGE_ADD |   角色框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_PLAYER_FRAME_NAME_RRFRESH|   角色外框角色名刷新||
|LUA_EVENT_PLAYER_LOOK_FRAME_PAGE_ADD|   查看他人角色框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_PLAYER_GUILD_INFO_CHANGE|    玩家行会信息改变||
|LUA_EVENT_HERO_FRAME_PAGE_ADD   |   英雄框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_HERO_FRAME_NAME_RRFRESH|   英雄框名字刷新||
|LUA_EVENT_HERO_LOOK_FRAME_PAGE_ADD|   查看他人英雄框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_TRAD_PLAYER_LOOK_FRAME_PAGE_ADD|   交易行查看他人玩家框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_TRAD_HERO_LOOK_FRAME_PAGE_ADD|   交易行查看他人英雄框增加子页| table -- {child = 子页控件, index = 对应pageId, init = 是否初始化}|
|LUA_EVENT_SERVER_VALUE_CHANGE   |   服务器下发的变量改变|table -- {key = key, value = value}|
|LUA_EVENT_MAIN_PLAYER_REVIVE   |     主玩家复活    ||
|LUA_EVENT_NET_PLAYER_REVIVE    |     网络玩家复活  |table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_MONSTER_REVIVE       |     怪物复活      |table -- {id = 怪物ID}|支持版本号3.40.3以上|
|LUA_EVENT_MAIN_PLAYER_DIE      |     主玩家死亡    ||
|LUA_EVENT_NET_PLAYER_DIE       |     网络玩家死亡  |table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_MONSTER_DIE          |     怪物死亡      |table -- {id = 怪物ID}|支持版本号3.40.3以上|
|LUA_EVENT_NPCLAYER_OPENSTATUS | NPC界面打开/关闭状态刷新|boolean -- true: 打开 false: 关闭|
|LUA_EVENT_NPC_TALK            |     NPC对话 [打开TXT-NPC界面] |table -- {id = NPCID, index = NPC配置ID, name = NPC名称}|支持版本号3.40.2以上|
|LUA_EVENT_MINIMAP_FIND_PATH  |    寻路路径      ||支持版本号3.40.2以上|
|LUA_EVENT_MINIMAP_MONSTER    |    小地图怪物数据刷新||支持版本号3.40.2以上|
|LUA_EVENT_MINIMAP_PLAYER     |    小地图人物坐标刷新||支持版本号3.40.2以上|
|LUA_EVENT_MINIMAP_TEAM       |    小地图组队成员数据刷新||支持版本号3.40.2以上|
|LUA_EVENT_MINIMAP_RELEASE    |    小地图释放内存||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_INTERNAL_FORCE_CHANGE |人物内力值改变||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_INTERNAL_EXP_CHANGE |人物内功经验值改变||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_INTERNAL_LEVEL_CHANGE|人物内功等级改变|table -- {lastLevel = 上次等级, curLevel = 当前等级}|支持版本号3.40.3以上|
|LUA_EVENT_INTERNAL_SKILL_ADD |人物内功技能增加|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_INTERNAL_SKILL_DEL |人物内功技能删除|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_INTERNAL_SKILL_UPDATE|人物内功技能刷新|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_LEARNED_INTERNAL |人物学习内功||支持版本号3.40.2以上|
|LUA_EVENT_MERIDIAN_DATA_REFRESH |人物内功经络数据刷新||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_INTERNAL_DZVALUE_CHANGE |人物内功斗转值改变/恢复||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_COMBO_SKILL_ADD |人物连击技能增加||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_COMBO_SKILL_DEL |人物连击技能删除||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_COMBO_SKILL_UPDATE |人物连击技能刷新|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_SET_COMBO_REFRESH |人物设置的连击技能刷新||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_COMBO_SKILLCD_STATE|人物连击技能CD状态|boolean -- true: 可释放<br> false: CD未到|支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_OPEN_COMBO_NUM|人物开启连击格子数|int -- 格子数|支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_FORCE_CHANGE |英雄内力值改变||支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_EXP_CHANGE |英雄内功经验值改变||支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_LEVEL_CHANGE|英雄内功等级改变|table -- {lastLevel = 上次等级, curLevel = 当前等级}|支持版本号3.40.3以上|
|LUA_EVENT_HERO_INTERNAL_SKILL_ADD |英雄内功技能增加|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_SKILL_DEL |英雄内功技能删除|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_SKILL_UPDATE |英雄内功技能刷新|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_HERO_LEARNED_INTERNAL |英雄学习内功||支持版本号3.40.2以上|
|LUA_EVENT_HERO_MERIDIAN_DATA_REFRESH |英雄内功经络数据刷新||支持版本号3.40.2以上|
|LUA_EVENT_HERO_INTERNAL_DZVALUE_CHANGE |英雄内功斗转值改变/恢复||支持版本号3.40.2以上|
|LUA_EVENT_HERO_COMBO_SKILL_ADD |英雄连击技能增加||支持版本号3.40.2以上|
|LUA_EVENT_HERO_COMBO_SKILL_DEL |英雄连击技能删除||支持版本号3.40.2以上|
|LUA_EVENT_HERO_COMBO_SKILL_UPDATE |英雄连击技能刷新|table -- 技能数据|支持版本号3.40.2以上|
|LUA_EVENT_HERO_SET_COMBO_REFRESH |英雄设置连击技能刷新||支持版本号3.40.2以上|
|LUA_EVENT_HERO_OPEN_COMBO_NUM|英雄开启连击格子数||支持版本号3.40.2以上|
|LUA_EVENT_HERO_PROPERTY_CHANGE |英雄属性变化||支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SERVER|顶部跑马灯 全服公告|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SERVER_EVENT|屏幕跑马灯 系统公告|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SYSYTEM|屏幕跑马灯公告 可控制Y轴|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SYSYTEM_SCALE|系统公告缩放 |table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SYSYTEM_XY|跑马灯公告 可控制XY轴|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_SYSYTEM_TIPS|系统 提示弹窗|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_TIMER|聊天上方倒计时公告|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_DELETE_TIMER|移除倒计时公告||支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_ITEM_TIPS|飘字 物品获取/消耗提示|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_ATTRIBUTE|飘字 属性变化|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_EXP|飘字 经验变化|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_NOTICE_DROP|公告 掉落物品提示|table -- 消息参数内容|支持版本号3.40.2以上|
|LUA_EVENT_RICHTEXT_OPEN_URL|富文本超链(href)点击触发|string -- href内容|支持版本号3.40.2以上|
|LUA_EVENT_KF_STATUS_CHANGE|跨服状态改变|boolean -- true:进入跨服 <br> false: 退出跨服|支持版本号3.40.2以上|
|LUA_EVENT_QUICKUSE_DATA_OPER|快捷栏道具数据变动触发|table -- {opera = 操作类型 ( 0:初始化 1:增加 2:删除 3:改变), param = 具体数据(table)}|支持版本号3.40.2以上|
|LUA_EVENT_ENTER_WORLD|进入游戏世界 主界面已经初始化||支持版本号3.40.2以上|
|LUA_EVENT_LEAVE_WORLD|离开游戏世界 小退触发||支持版本号3.40.2以上|
|LUA_EVENT_PLAYER_IN_SAFEZONE_CHANGE|主玩家安全区状态改变||支持版本号3.40.3以上|
|LUA_EVENT_NET_PLAYER_IN_SAFEZONE_CHANGE|网络玩家安全区状态改变|table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_PLAYER_STALL_STATUS_CHANGE|主玩家摆摊状态改变||支持版本号3.40.3以上|
|LUA_EVENT_NET_PLAYER_STALL_STATUS_CHANGE|网络玩家摆摊状态改变|table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_PLAYER_HUSHEN_STATUS_CHANGE|主玩家护身状态改变||支持版本号3.40.3以上|
|LUA_EVENT_NET_PLAYER_HUSHEN_STATUS_CHANGE|网络玩家护身状态改变|table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_PLAYER_TEAM_STATUS_CHANGE|主玩家组队状态改变||支持版本号3.40.3以上|
|LUA_EVENT_NET_PLAYER_TEAM_STATUS_CHANGE|网络玩家组队状态改变|table -- {id = 玩家ID}|支持版本号3.40.3以上|
|LUA_EVENT_PURCHASE_ITEM_LIST_PULL|求购列表数据返回|table|支持版本号3.40.5以上|
|LUA_EVENT_PURCHASE_ITEM_LIST_COMPLETE|求购列表加载完成|table -- {type = 类型 0: 世界求购, 1: 我的求购, 2: 我的已收}|支持版本号3.40.5以上|
|LUA_EVENT_PURCHASE_SEARCH_ITEM_UPDATE|求购搜索参数刷新|string -- 筛选的道具Index字符串|支持版本号3.40.5以上|
|LUA_EVENT_PURCHASE_MYITEM_UPDATE|我的求购数据刷新|table -- {type = 类型(1: 新增, 2: 删除, 3: 更新), isReceive = bool 是否为已收列表, item = 求购数据}|支持版本号3.40.5以上|
|LUA_EVENT_PURCHASE_WORLDITEM_UPDATE|世界求购数据刷新|table -- {type = 类型(1: 新增, 2: 删除, 3: 更新), item = 求购数据}|支持版本号3.40.5以上|
|LUA_EVENT_RED_POINT_ADD|红点增 (按红点表cfg_redpoint配置)|table -- {id = 表配置id}|支持版本号3.40.6以上|
|LUA_EVENT_RED_POINT_DEL|红点删 (按红点表cfg_redpoint配置)|table -- {id = 表配置id}|支持版本号3.40.6以上|
|LUA_EVENT_FLYIN_BTN_ITEM_COMPLETE|道具飞入指定按钮完成|table -- {itemIndex = 道具Index}|支持版本号3.40.6以上|
|LUA_EVENT_STORAGE_DATA_CHANGE|仓库数据变动|table -- {opera = 操作类型 (1:增加 2:删除 3:改变 4:整理/刷新页), item = 物品数据, page = 仓库页签 }|支持版本号3.40.7以上|
|LUA_EVENT_HERO_LOCK_CHANGE|英雄锁定刷新||支持版本号3.40.7以上|
|LUA_EVENT_PLAYER_TITLE_CHANGE|人物称号数据变动|table -- {opera = 类型 (1:初始化 2:增加 3:删除 4:激活 5:卸下 6: 清理全部称号)}|支持版本号3.40.7以上|
|LUA_EVENT_SKILL_ADD_TO_UI_WIN32|PC端-添加技能到主界面触发|table -- {skill = 技能ID, pos = table 坐标位置}|支持版本号3.40.7以上|
|LUA_EVENT_SKILL_REMOVE_TO_UI_WIN32|PC端-移除主界面技能触发|table -- {skill = 技能ID}|支持版本号3.40.7以上|
|LUA_EVENT_SKILL_CD_TIME_CHANGE|技能CD时间变动|table -- {id = 技能ID, percent = 倒计时百分比(不为0时), time = 剩余CD时间}|支持版本号3.40.7以上|
|LUA_EVENT_PLAYER_EMBATTLE_CHANGE|人物法阵刷新||支持版本号3.40.8以上|
|LUA_EVENT_PLAYER_SEX_CHANGE|人物性别刷新||支持版本号3.40.8以上|
|LUA_EVENT_HERO_EMBATTLE_CHANGE|英雄法阵刷新||支持版本号3.40.8以上|
|LUA_EVENT_HERO_SEX_CHANGE|英雄性别刷新||支持版本号3.40.8以上|
|LUA_EVENT_HORSE_UP|骑马上马事件|table -- {actorID = actorID}|支持版本号3.40.8以上|
|LUA_EVENT_HORSE_DOWN|骑马下马事件|table -- {actorID = actorID}|支持版本号3.40.8以上|

------------

**------------**

### 简单示例
* 主玩家添加足迹特效 : 
```
	SL:RegisterLUAEvent(LUA_EVENT_PLAYER_ACTION_BEGIN, "TTT", function(data)
    local id = data and data.id 
    if id then
        local posX = SL:GetMetaValue("ACTOR_POSITION_X", id)
        local posY = SL:GetMetaValue("ACTOR_POSITION_Y", id)
        if posX and posY then
            local actBegin = data.act
            if actBegin == 1 or actBegin == 6 or actBegin == 17 then
                local eff = GUI:Effect_Create(GUI:Attach_SceneB(), string.format("foot_effect%s_%s%s", id, posX, posY), posX, posY, 0, 2133)
                if eff then
                    GUI:Effect_addOnCompleteEvent(eff, function()
                        GUI:removeFromParent(eff)
                    end)
                end
            end
        end
    end
end)
```


# 游戏触发

触发函数返回true则阻断官方自带逻辑，返回false继续执行官方逻辑
触发函数会带参数
- 注册触发 SL:RegisterTrigger(eventName, eventCB)
- 注销触发 SL:UnRegisterTrigger(eventName)
- 例子 SL:RegisterTrigger(LUA_TRIGGER_CHAT_CLICK_PLAYER_NAME, function(userData) end)

|触发名|触发参数|说明
|:----|:-----|-----|
|LUA_TRIGGER_CHAT_CLICK_PLAYER_NAME|table -- {SendId = 角色ID, SendName = 角色名}|聊天框点击玩家名
|LUA_TRIGGER_NOTICE_SHOW_ATTRIBUTES|table -- 属性展示列表|属性提示通知
|LUA_TRIGGER_NOTICE_SHOW_GET_ITEM|table -- {name = 物品名称, count = 数量, str = 文本, ishero = boolen(true为英雄)}|获得物品提示
|LUA_TRIGGER_NOTICE_SHOW_COST_ITEM|table -- {name = 物品名称, count = 数量, str = 文本, ishero = boolen(true为英雄)}|消耗物品提示
|LUA_TRIGGER_NOTICE_SHOW_EXP_CHANGE|table -- 显示参数|经验提示通知


# 教程示例

视频教程
http://engine-doc.996m2.com/web/#/9/5026

* 20230422直播 透视戒指和目标下方显示拥有BUFF
[20230422直播_buff和透视戒指功能.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=086ec824cc35b6aea49c1761414ab085 "[20230422直播_buff和透视戒指功能.zip")

* buff示例
[buff源码.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=f12a4c8dade8b5f7a125648c330ceddc "[buff源码.zip")

*  转盘示例
[转盘.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b8ecbce94a951ca5b8cc851abf349d6c "[转盘.zip")

* PK模式源码
[PK模式.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=118b5732885ac73ed7fa0b27fb21cfad "[PK模式.zip")

* 自动挂机按钮示例
[自动挂机按钮.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=54c9631842733e4af4d2e31211c0003d "[自动挂机按钮.zip")

* 充值面板
[充值面板.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c42526243dd7b82c63d367be29f5b623 "[充值面板.zip")

* 角色面板修改官方源码，增加页签
[角色面板增加页签.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=926c8bcf2798e9ebee7f27bec10e7d47 "[角色面板增加页签.zip")

* 角色野蛮时增加特效，沿野蛮方向释放
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=5c6f7c69f86ccfb446455419201365f4)

* [登陆界面示例1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=5928ac8f50fe143e9225fefb7fa2ca85 "[登陆界面示例1.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=39c3c05903255150b18b01197e8e33b3)

* [登陆界面示例2.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=1005f9967da49b0ab5b4d563f8825bfa "[登陆界面示例2.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a98db9849b8037129a0efcc8d1a80011)

* [登陆界面示例3.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=bc6b27c235af0b888e5618fc8a4a79f1 "[登陆界面示例3.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c75cbb4ea88363659f14b10a8051df5a)
------------

* [裂神符.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=c585d7898bf357d9c08495dd25d0ca0a "[GUILayout.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=79a40be00c94328f021614441a1f2664)

------------

* [超链广播.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=38f756655215a3a3c37e65dde1460109 "[GUILayout_超链广播[0103].zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b1151a34e9217cdd343c5d3d244b7894)

------------

* [轮盘-新框架.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=683a299836515a1871148fb1a2330d91 "[dev.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d9687c2ba7581ba3cd055b7763072cc9)

------------

* [BOSS墓碑.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4bd31ca744162b73f4ef53db865656e6 "[GUILayout_BOSS墓碑.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=b5da0f4b35d891bd0d01e24a6eb1bc63)

------------

* [场景特效示例.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=fc69706b18058c1ddb652c536a71fa15 "[GUILayout_场景特效示例.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ebdaa295905c509813603bdf8d31aa34)

------------

* [背包示例.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=60485e626441c85628c42498dda94de0 "[GUILayout_背包示例.zip")
![](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=71cd2b0759302071daeb5367da05febf)

------------

* 前端获取装备的标记

```lua
function ssrGetItemFalg(addValues,pos)
    local n = nil
    if addValues then
        for _, v in pairs(addValues) do
            if v.Id == 19 then
                n = v.Value
                break
            end
        end
    end
    if not n then return 0 end
    local mask = bit.lshift(1, pos)
    local masked_n = bit.band(n, mask)
    return bit.rshift(masked_n, pos)
end

local itemData = SL:GetMetaValue("EQUIP_DATA", 1)
if itemData and itemData.AddValues then
    -- 对应TXT接口设置的1~32物品标记
    for i = 0, 31 do
        SL:Print("装备标记1111",i,ssrGetItemFalg(itemData.AddValues,i))
    end
end

```

------------
* [GmBox示例.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=8c17f64c712bb8364463592217febc19 "[gmbox_0226(2).zip")

![gmbox示例](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=be7e5ae1fd3c4b0a46b1e6acff6d78cc)

------------

* NPC界面(后端Say)添加动画
```lua
SL:RegisterLUAEvent("LUA_EVENT_NPC_TALK", "GUIUtile", function(data)
    local npcID = SL:GetMetaValue("CURRENT_TALK_NPC_ID")
    local npcIndex = SL:GetMetaValue("CURRENT_TALK_NPC_TYPEINDEX")
    local layer = SL:GetMetaValue("CURRENT_TALK_NPC_LAYER")
    if layer then
        GUI:Timeline_Window1(layer)
    end
end)
```


# 网络

#### `消息分为两种：一种是对 Lua 操作的； 另一种是对 TXT 进行操作`

----
# `服务器使用Lua的技术` ：
  * 接收网络消息 `SL:RegisterLuaNetMsg(msgID, networkCB, widget)`,  networkCB(msgID, n1, n2, n3, recvStr)

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|msgID |是  |int | 消息ID|
|networkCB|是  |function | 接收消息的函数回调|
|widget   |否|obj|绑定的界面(win)对象， 界面关闭则注销接收回调|
	
  * 注销网络消息接收 `SL:UnRegisterLuaNetMsg(msgID)`
 
  * 发送网络消息 `SL:SendLuaNetMsg(msgID, p1, p2, p3, sendStr)`

	Lua脚本接收客户端消息，代码写在 `QFunction-0.lua`
	Lua自定义消息统一执行：`handlerequest(actor, msgID, param1, param2, param3, str)`
	比如客户端发送消息号100

    ```
	-- Lua脚本 接收消息
	function handlerequest(actor, msgID, param1, param2, param3, str)
		release_print("-----------------------------")
		release_print(msgID)
		release_print(param1)
		release_print(param2)
		release_print(param3)
		release_print(str)
	end

	-- 客户端执行 发送消息
	SL:SendLuaNetMsg(100, 1, 2, 3, "Hello World, This engine, for Lua!")
    ```

	Lua脚本发送消息给客户端，支持 3个int和1个字符串，使用 `sendluamsg`
	客户端注册对应消息号
	比如脚本发送消息号1000
	```
	-- 客户端注册 接收消息
	local function networkCB(msgID, p1, p2, p3, msgData)
		SL:Print(msgID, p1, p2, p3, msgData)
	end
	SL:RegisterLuaNetMsg(1000, networkCB)

	-- Lua脚本执行
	sendluamsg(actor, 1000, 1, 2, 3, "我是来自服务器的消息 By Lua")
	```

# `服务器使用TXT的技术` ：

* 接收网络消息 `SL:RegisterNetMsg(msgID, networkCB, widget)`,  networkCB(msgID, msgData)

|参数名|必选|类型|说明|
|:----    |:---|:----- |-----   |
|msgID |是  |int | 消息ID|
|networkCB|是  |function | 接收消息的函数回调|
|widget   |否|obj|绑定的界面(win)对象， 界面关闭则注销接收回调|
* 注销网络消息接收 `SL:UnRegisterNetMsg(msgID)`

* 发送网络消息 `SL:SendNetMsg(msgID, PARAM1, PARAM2, PARAM3, CUSTMSGPARAM)`
* 注意！！！ 一个 msgID 只能注册一个回调

	TXT脚本接收客户端消息，代码写在 `QFunction-0.txt`
	TXT自定义消息监听触发：`Message_xxx`, xxx 为消息号ID
	比如客户端发送消息号100
	```
	;接收来自客户端的消息号 100
	[@Message_100]
	#ACT
	SENDMSG 0 收到消息，<$PARAM1>, <$PARAM2>, <$PARAM3>, <$CUSTMSGPARAM>

	-- 客户端执行 发送消息
	SL:SendNetMsg(100, 1, 2, 3, "Hello World, This engine, for TXT!")
	```

	TXT脚本发送消息给客户端，支持发字符串，使用 `SENDCUSTMSG`
	客户端注册对应消息号
	比如脚本发送消息号1000
	```
	-- 客户端注册 接收消息
	local function networkCB(msgID, msgData)
		SL:Print(msgID)
		SL:Print(msgData)
	end
	SL:RegisterNetMsg(1000, networkCB)

	TXT脚本执行
	SENDCUSTMSG 1000 我是来自服务器的消息, By TXT
	```
# 常量说明

##角色动作

```
	0,  -- 站立
	1,  -- 走
	2,  -- 平砍
	3,  -- 施法    
	4,  -- 死亡    
	5,  -- 受击
	6,  -- 跑
	7,  -- 出生
	8,  -- 准备
	9,  -- 挖矿
	10, -- 坐下
	11, -- 死亡
	14, -- 变身
	15, -- 转身
	16, -- 钻回洞穴
	17, -- 骑马跑
	18, -- 服务器触发怪物动作1
	19, -- 服务器触发怪物动作2
	20, -- 服务器触发怪物动作3
	21, -- 野蛮冲撞
	22, -- 被野蛮
	23, -- 野蛮等待
	24, -- 瞬移
	25, -- 站着等待
	26, -- 倚天辟地
	27, -- 追心刺
	28, -- 三绝杀
	29, -- 断岳斩
	30, -- 横扫千军
	31, -- 凤舞祭
	32, -- 惊雷爆
	33, -- 冰天雪地
	34, -- 双龙破
	35, -- 虎啸诀
	36, -- 八卦掌
	37, -- 三焰咒
	38, -- 万剑归宗
	39, -- 野蛮失败的撞墙动作
```
# 游戏入口


---------------------------------------------------------------------------------
# 入口
**进入游戏世界会自动调用 `dev/scripts/ssr/ssrgame/ssrmain.lua`**
# 功能系统

# 配置表
  * 客户端使用lua表
  * 纯客户端使用表不再放到引擎上，本地目录为 dev/scripts/game_config/...
  * 提供导表工具，xls转lua
  * 导表工具使用，需使用///指定导出key和导出字段，参考cfg_buff表
  * 导表工具 [996M2资源集成工具.exe](http://192.168.4.240:4999/server/index.php?s=/api/attachment/visitFile/sign/5b0df789b7e0434a1f2abd757a485655 "[996M2资源集成工具.exe")
  * 客户端表 [game_config.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/f3d6d0711ec3d5f329ccd3101084623e "[game_config.zip")

# 游戏常用常量
  * 配置表 cfg_game_data
  * isShowAttributeTips             有值=显示属性变化飘字  不配置=不显示
  * isSingleJob                     是否是单职业 1=单职业
  * isRandomJob                     是否随机职业 1=随机
  * isSingleSex                     是否单性别 boy=男 girl=女
  * isRandomSex                     是否随机性别 1=随机
  * buttonSmall                     小退CD时间 单位:毫秒
  * JPshuxingEquipEffect            道具光柱持续时间，有且>0 才会生效光柱
  * playerInfoMode                  人物/英雄面板合并显示 1=合并
  * syshero                         英雄系统是否开启 1=开启
  * attackglobalCD                  公共CD 攻击类技能公共CD
  * magicglobalCD                   公共CD 魔法类技能公共CD
  * MonsterPaperback                怪物简装形象外观ID
  * HumanPaperback                  人物简装 战士衣服#武器|法师衣服#武器|道士衣服#武器 (例 17#22#2#1001|18#21#2#1001|19#20#2#1001)
  * prompt                          聚灵珠/祝福罐满提醒 PC资源路径#x#y#缩放|手机资源路径#x#y#缩放
  * SHOUTCHANEL_TIME                聊天世界频道CD
  * PRIVATECHANEL_TIME              聊天私聊频道CD
  * GUILDCHANEL_TIME                聊天行会频道CD
  * TEAMCHANEL_TIME                 聊天组队频道CD
  * WORLDCHANEL_TIME                聊天附近频道CD
  * WORLDCHANEL_TIME                聊天传音频道CD
  * SHOUTCHANEL_LEVEL               聊天世界频道等级限制
  * PRIVATECHANEL_LEVEL             聊天私聊频道等级限制
  * GUILDCHANEL_LEVEL               聊天行会频道等级限制
  * TEAMCHANEL_LEVEL                聊天组队频道等级限制
  * WORLDCHANEL_LEVEL               聊天附近频道等级限制
  * WORLDCHANEL_LEVEL               聊天传音频道等级限制
  * Team_assembled                  队伍召集令道具ID
  * BuiltinCD                       吃药CD  红药#蓝药#瞬回药#随机回城等
  * Heroqiehuan                     英雄 战斗#跟随#休息#守护
  * Heroqiehuanmoshi                英雄 切换模式 双击/长按
  * BackpackGuide                   道具tips 拆分/佩戴开关
  * EXPcoordinate                   经验提醒 PCX#Y|手机X#Y
  * warehouse_max_num               NPC商店数量
  * RankingList                     排行榜类型名字 类型#名字|类型#名字...
  * guild_updata                    行会升级经验 最低1000金币#可兑换1荣誉|最低1000金币#可兑换10行会建设度|每日捐献上限
  * isHideAuctionGuild              是否隐藏行会拍卖 1=隐藏
  * StallName                       默认摆摊摊位名
  * auto_equip_quality              自动穿戴 最底品质限制
  * Redtips                         红点系统图片 PC图片|手机图片
  * boxtexiao                       宝箱特效配置 宝箱Shape#普通特效#打开特效#开启特效
  * alliance                        行会结盟花费 itemid#num (例 1#1#20000&2#1#30000&6#1#50000&12#1#80000&24#1#100000)
  * alliance_time                   行会结盟时长 (例 1#2#6#12#24)
  * Hangxuan                        行会宣战按钮开关 0: 关  1: 开
  * declareWar                      行会宣战花费 itemid#num  (例 2#1#100000&4#1#200000&8#1#300000&12#1#500000)
  * declareWar_time                 宣战时长 (例 2#4#8#12)
  * MiniMap                         小地图大小和坐标配置 x#y#width#height
  * Fashionfx                       是否显示裸模 0开启  1关闭
  * rechargeMin                     最底充值金额 单位:元
  * drug_tips                       内挂-保护-药品提醒自定义富文本
  * Progressbarmode                 英雄进度条模式 1 / 0
  * outlineSize                     默认所有字体描边大小
  * defaultOutlineSize              自定义ui默认字体秒变大小
  * defaultOutlineColor             自定义ui默认字体颜色
  * itemSacle                       道具图标缩放 手机缩放|PC缩放
  * gameOption_WalkOnly             开启只有走模式 1开启

# 装备位
	0,            --// 衣服
	1,            --// 武器
	2,            --// 勋章
	3,            --// 项链
	4,            --// 头盔
	5,            --// 右手镯      左右以人物内观内的左右为标准
	6,            --// 左手镯
	7,            --// 左戒指
	8,            --// 右戒指
	9,            --// 护身符位置 玉佩 宝珠
	10,           --// 腰带
	11,           --// 鞋子
	12,           --// 宝石
	13,           --// 斗笠
	14,           --// 左下 军鼓
	15,           --// 右下 马牌
	16,           --// 盾牌
	17,           --// 神装衣服 --冰雪是神魔套装
	18,           --// 神装武器
	19,           --// 时装斗笠
	20,        --// 时装项链
	21,          --// 时装头盔
	22,        --// 时装左手镯
	23,        --// 时装右手镯
	24,           --// 时装左戒指
	25,           --// 时装右戒指
	26,       --// 时装勋章
	27,            --// 时装腰带
	28,           --// 时装靴子
	29,           --// 时装宝石
	42,     --// 时装马牌
	43,           --// 时装符印
	44,      --// 时装军鼓
	45,          --// 时装盾牌
	46,            --// 时装面巾
	30,           --// 极品首饰1
	31,           --// 极品首饰2
	32,           --// 极品首饰3
	33,           --// 极品首饰4
	34,           --// 极品首饰5
	35,           --// 极品首饰6
	36,           --// 极品首饰7
	37,           --// 极品首饰8
	38,           --// 极品首饰9
	39,           --// 极品首饰10
	40,           --// 极品首饰11
	41,           --// 极品首饰12
	55,           --// 面纱
	30,
	47,            -- 特戒左
	48,            -- 特戒右
	49,            -- 时装衣服 --冰雪
	50,            -- 时装武器
	
	-- 71-100 后端发送，脚本自定义

# buff系统
  * 配置表 cfg_buff
  * 给场景内 掉落物 增加特效，可控制获得该特效时是否可以 走/跑、使用技能、使用道具等

# 技能系统
  * 配置表 cfg_magicinfo、 cfg_skill_present
  * cfg_magicinfo  控制所有技能的释放策略
  * cfg_skill_present控制所有技能的场景表现，怪物的场景表现ID为 100000 + race .. raceImg (例 race=121，raceImg=50，技能表现ID=112150)

# 游戏内使用特效ID
  * 5012				 	-- 点地板特效
  * 5011					-- 点击屏幕
  * 4008				 	-- 选中目标特效
  * 4012					-- 升级特效 前面
  * 4013					-- 升级特效 后面
  * 7   					-- 飞入特效
  * 58   					-- 飞入特效 另外一个
  * 6 						-- 飞出特效
  * 59						-- 飞出特效 另外一个
  * 4016					-- NPC头顶任务状态特效 可以接
  * 4015					-- NPC头顶任务状态特效 已接
  * 4011					-- NPC头顶任务状态特效 已完成
# 游戏内触发

# 响应事件名，会响应继承自ssrBaseObj的类，在  onEvent(eventName, eventData) 监听
  * `onDisconnect`                    -- 断线
  * `onReconnect`                     -- 重连
  * `onMapInfoChange`                 -- 地图改变 不同地图 {mapID = mapID, lastMapID = lastMapID}
  * `onChangeScene`                   -- 切换场景 同地图或不同地图 {mapID = mapID, lastMapID = lastMapID}
  * `onPlayerPropertyInited`          -- 角色属性初始化完毕，通常在这里认为已正常进入游戏，可以执行其他逻辑
  * `onPlayerLevelChange`             -- 角色等级发生改变  {currlevel = currlevel, lastlevel = lastlevel}
  * `onPlayerPropertyChange`          -- 角色属性发生改变
  * `onPlayerManaChange`			  -- 角色hp/mp发生改变 {curHP = curHP, maxHP = maxHP, curMP = curMP, maxMP = maxMP, roleName = roleName}
  * `OnPlayerNameInited`			  -- 角色名初始化/改变 {roleName = roleName}
  * `OnPlayerMoneyChange`			  -- 角色货币数据改变 {id = id, count = count} -- 发生改变的货币id和数量
  * `OnTargetChange`				  -- 选中目标改变  {actorID = actorID, actorName = actorName, curHP = curHP, maxHP = maxHP, level = level, type = type, masterID = masterID, typeID = typeID }  
  type: 类型 1玩家 2怪    masterID: 主人ID     typeID: 怪物表配置IDX
  * `OnRefreshTargetHP`				  -- 已选中的目标血量变化 {userID = userID, curHP = curHP, maxHP = maxHP}
  * `OnTakeOnEquip`					  -- 穿戴装备 {isSuccess = isSuccess} isSuccess: boolean 成功/失败  pos:  成功时返回装备位id
  * `OnTakeOffEquip`				  -- 脱掉装备 {isSuccess = isSuccess} isSuccess: boolean 成功/失败  pos:  成功时返回装备位id
  * `OnChangePKStateSuccess`		  -- 成功改变玩家攻击模式 {pkMode = pkMode}
  * `OnBatteryValueChange`			  -- 电量改变  value -- 电量百分比值
  * `OnPlayerExpChange`				  -- 玩家经验值改变	{changed = changed} -- 变动的数值
  * `OnNetStateChange`				  -- 网络状态改变	  {type = type} type: -1:未知 0:wifi 1:2G 2:3G 3:4G
  * `OnPreBagOperData`				  -- 背包数据操作 前 触发  -- 参数等同下方
  * `OnBagOperData`					  -- 背包数据操作  {opera = opera, operID = operID} -- opera类型: 0:初始化 1:增加 2:删除 3:改变  operID 物品数据: table
  * `OnActionBegin`					  -- 走路/跑步动作触发 type -- 1走路 2跑步 [主玩家]
  * `OnPetActionBegin`				  -- 主玩家的宠物/宝宝动作触发  -- 1走路 2跑步
  * `OnSkillAdd`					  -- 新增技能 技能数据: table
  * `OnSkillDel`					  -- 删除技能 技能数据: table
  * `OnSkillUpdate`					  -- 技能更新 技能数据: table
  * `OnAddChatItem`					  -- 聊天消息增加 table
  		{
            Msg         = 信息内容,
            FColor      = 文字色值ID,
            BColor      = 背景色值ID,
            ChannelId   = 聊天频道,
            SendName    = 发送者角色名,
            SendId      = 发送者角色ID,
            mt          = 消息类型, -- 1.普通消息 2.坐标 3.装备 5. 系统通知消息/特定富文本解析 6.系统通知消息/FColor富文本解析 7. 系统通知消息/SRText富文本解析 8.骰子
          }	
  * `OnLookPlayerDataUpdate`		  -- 查看他人数据更新  table --此时table内Items为服务端未解析过的装备信息数据 
  * `OnAutoFightBegin`				  -- 自动战斗开始
  * `OnAutoFightEnd`				  -- 自动战斗结束
  * `OnPlayerEquipInit`				  -- 角色装备数据初始化
  * `OnCloseBag`					  -- 关闭背包触发
  * `OnJoinOrExitGuild`				  -- 加入/退出行会触发 {type = type, guildName = guildName} 
   type 类型: 1加入 2退出 [主玩家]   -- guildName: 加入时行会名称
  * `OnAcrossDay`					  -- 跨天触发
  * `OnRichTextOpenUrl`				  -- 富文本超链(href)点击触发
  * `OnMainPlayerDie`				  -- 主玩家死亡
  * `OnMainPlayerRevive`			  -- 主玩家复活
  * `OnMainPlayerBuffChange`		  -- 主玩家buff变动
  * `OnQuickUseOperData`			  -- 快捷栏物品数据操作 {opera = opera} -- opera类型: 0:初始化 1:增加 2:删除 3:改变  
  * `OnGUINewWinClose`				  -- 新窗口关闭触发 value -- 新窗口ID
  * `onLeaveWorld`                    -- 离开游戏世界  小退触发
  * `onRestartGame`                   -- 重启游戏触发
  * `onGameSuspend`                   -- 游戏暂停
  * `onGameResumed`                   -- 游戏恢复

# 常用方法

# 方法
  * `ssr.print`                       -- 打印日志到控制台
    例
    ```
    ssr.print("Hello World, This is ssrengine, for Lua!")
    ```

  * `ssr.PrintTable`                  -- 打印一个Table
    例
    ```
    local t = {1, 2, 3}
    ssr.PrintTable(t)
    ```

  * 获取屏幕宽高
    ```
    local visibleSize = ssr.getVisibleSize()
    ssr.PrintTable(visibleSize)
    ```

  * 获取当前平台 安卓 iOS PC  [!不是方法 作常量使用]
    `ssr.isWindows`   Windows平台 (注意开发时这个值一直是true)
    `ssr.isMobile`    手机 (包含安卓和iOS)
    `ssr.isAndroid`   安卓平台
    `ssr.isIOS`       iOS平台

  * 获取当前游戏运行版本  手机端/PC端 (开发时可用)
  	`ssr.IsWinMode()`	
	*返回值: *  boolean  -- true则为PC端 false: 手机端

  * `ssr.PrintTraceback`              -- 打印堆栈
    例
      ```
      ssr.PrintTraceback()
      ```

  * `ssr.LoadTxt`                     -- 以指定分隔符拆解一个文件，如拆解csv表。注意！！会自动抛弃带//行
    *参数*
      path            路径
      delimiter       分隔符
      callback        回调
    例
      ```
      local function loadCB(dataTable)
        ssr.PrintTable(dataTable)
      end
      ssr.LoadTxt("data_config/msg_decoder_config.txt", "#", loadCB)
      ```

  * `ssr.Schedule`                    -- 开启一个定时器
    *返回值*
      定时器ID
    *参数*
      callback        回调
      interval        间隔时间 （单位: 秒）
    例
    ```
    local function scheduleCB(dt)
      ssr.print(dt)
    end
    local scheduleID = ssr.Schedule(scheduleCB, 1)
    ```

  * `ssr.UnSchedule`                  -- 停止一个定时器
    *参数*
      scheduleID     上一个方法返回值
    例
    ```
    ssr.UnSchedule(scheduleID)
    ```

  * `ssr.PerformWithDelayGlobal`      -- 开启一个单次定时器
    *返回值*
      定时器ID
    *参数*
      callback        回调
      time            等待时间 （单位: 秒）
    例
    ```
    local function performCB()
      ssr.print("This is ssr.PerformWithDelayGlobal.")
    end
    local scheduleID = ssr.PerformWithDelayGlobal(performCB, 1)
    ```

  * `ssr.UIQuickChild`                -- ui快速化
    *返回值*
      ui
    *参数*
      root            节点
    例
    ```
    local ui = ssr.UIQuickChild(root)
    ssr.print(ui.img1)
    ssr.print(ui.img2)
    ```
  * `ssr.encodeJson(table)`			-- 编码table对象为json字符串
  	*返回值 :*
	编码成功, 返回字符串
  
  * `ssr.decodeJson`				-- 解析json: 将json字符串解码为table对象
  	*返回值 :*
	解码成功, 返回table

  * `ssr.tonumber(s, base)`			-- 转换为数字
    *参数 :*
    s    		-- 传入的需要转换的字符串或数字
	base		-- 可不填, 若传入表示进制, 且s是以该进制表示的整数字符串.(进制可以是2到36之间的任何整数)
	例 :
	```
		ssr.print(ssr.tonumber("6F  ",16))
	```

  * `ssr.SecondToHMS(sec, isToStr, isSimple)` -- 秒转时分秒 
  	*参数 :*
	sec			-- int 秒数
	isToStr 	-- boolean 是否转成字符串输出
	isSimple	-- boolean 是否简洁化字符串  (基于isToStr 为true时)
	*返回值 :*
	isToStr 为false时, 返回 table {d = 天数, h = 小时, m = 分钟, s = 秒}
	否则返回对应字符串 
	例 :
	```
		local timeData = ssr.SecondToHMS(70000)
		ssr.PrintTable(timeData)
		local timeStr = ssr.SecondToHMS(70000, true)
		ssr.print("剩余时间为:  "..timeStr)
	```

  * `ssr.GetColorFromHexString( hexString )` -- 将HTML颜色码转为Color3B颜色
  	*参数 :*
	hexString   -- HTML颜色码 十六进制字符串
	*返回值 :*
	cc.c3b(R, G, B)
	例 :
	```
		local colorc3b = ssr.GetColorFromHexString("#928978")
    	self._quickUI.Text_name:setTextColor(colorc3b)
	```

  * `ssr.GetColorHexFromRGB(rgb)`   -- 将Color3B颜色转为HTML颜色码
  
  * `ssr.GetColorByStyleId(colorId)`  -- 将cfg_colour_style里的色值id转换为Color3B颜色
  	例 :
	```
		local colorc3b = ssr.GetColorByStyleId(1006)
    	self._quickUI.Text_name:setTextColor(colorc3b)
	```
  
  * `ssr.GetSimpleNumber(n)`		-- 简化数字 (过万以万为单位, 过亿以亿为单位)
    *返回值 :*  string

  * `ssr.GetThousandSepString( num )`		-- 获得千分位格式化字符串
  	*返回值 :*  string
	例 :
	```
		ssr.print(ssr.GetThousandSepString( 1234567890 ))
		-- 输出 1,234,567,890
	```
  
  * `ssr.SplitStr(inputStr,  delimiter)`  -- 字符串分割
    *参数 :* 
	inputStr   -- 输入字符串
	delimiter  -- 分隔符
	*返回值 :*
	table  --分割后的数组
	例 :
	```
		ssr.PrintTable(ssr.SplitStr("123,456,7,89,",","))
	```

  * `ssr.SplitStrFirst( inputStr, delimiter )`  -- 将字符串切割成两部分 
  	*参数 :* 
	inputStr   -- 输入字符串
	delimiter  -- 分隔符
	*返回值 :*
	table  --分割后的数组
	例 :
	```
		ssr.PrintTable(ssr.SplitStrFirst("123,456,7,89,",","))
	```
  * `ssr.max(value1, value2)`		-- 取最大值
  * `ssr.min(value1, value2)`		-- 取最小值
  * `ssr.ceil(value)`				-- 向上取整
  * `ssr.floor(value)`				-- 向下取整
  * `ssr.abs(value)`				-- 取绝对值
  
  * `ssr.encodeBase64(source_str)`  -- Base64编码
  	*参数 :*  
	source_str  -- 指定编码字符串

  * `ssr.decodeBase64(source_str)`  -- Base64解码
  	*参数 :*  
	source_str  -- 指定Base64编码后的字符串

  * `ssr.urlencode(input)`			-- URL编码
  	*参数 :*  
	input  -- 指定编码字符串

  * `ssr.urldecode(input)`			-- URL解码
  	*参数 :*  
	input  -- 指定URL编码后的字符串

  * `ssr.getFileMD5(filePath)`		-- 获取文件MD5
    *参数 :*
	filePath -- 指定文件路径
	*返回值 :*
	MD5值

  * `ssr.getStrMD5( str )`			-- 对指定字符串进行MD5加密
  	*返回值 :*
	加密后的字符串

  * `ssr.HTTPRequestPost(url, callback, suffix, header)`		-- HTTP请求 POST方式 
	*参数: *
	url			-- 请求的接口/API地址
	callback	-- 请求返回的回调函数		第一个参数 boolean 是否成功 第二个参数 返回数据 
	suffix		-- 接口所需参数
	header		-- HTTP header配置 		
	```
	例: 
		local header = {}
		header["Content-Type"] = "application/json"
		local url = "https://xxx.com/v1.0/tt/ttapi"
		local data = {
			role_id = "11111",
			type = 1,
		}
		local suffix = ssr.encodeJson(data)
		local function httpCB(success, response)
			ssr.print(success)
			ssr.print(response)
		end
		ssr.HTTPRequestPost(url, httpCB, suffix, header)
	
	```

  * `ssr.HTTPRequest(url, callback)`	-- HTTP请求 GET方式  
	*参数: *
	url			-- 拼接好的请求地址
	callback	-- 请求返回的回调函数		第一个参数 boolean 是否成功 第二个参数 返回数据 
--------------------
#### 游戏相关

  * `ssr.GetOpenServerDay`          -- 获取开服天数
    ```
    local openDay = ssr.GetOpenServerDay()
    ssr.print("开服天数："..openDay)
    ```
	
  * `ssr.GetOpenServerTime()`	-- 获取开服时间戳

  * `ssr.GetServerTime`       -- 获取服务器时间
    ```
    local curServerTime = ssr.GetServerTime()
    ssr.print("服务器时间戳："..curServerTime)
    ```

  * `ssr.createSFXAnim`               -- 创建一个普通特效
    *返回值*
      anim            特效对象
    *参数*
      sfxID           特效ID
    例
    ```
    local sfx = ssr.createSFXAnim(1)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
	-- 播放 (动作, 方向, 是否循环)
    sfx:Play(0,0,true)
    ```

  * `ssr.createSkillAnim`             -- 创建一个技能特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      dir             初始方向
    例
    ```
    local sfx = ssr.createSkillAnim(1, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createNpcAnim`               -- 创建一个NPC特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
    例
    ```
    local sfx = ssr.createNpcAnim(1)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createMonsterAnim`           -- 创建一个怪物特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      act             动作
    例
    ```
    local sfx = ssr.createMonsterAnim(1, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createPlayerAnim`            -- 创建一个玩家特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      sex             性别
      act             动作
    例
    ```
    local sfx = ssr.createPlayerAnim(1, 0, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createWeaponAnim`            -- 创建一个武器特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      sex             性别
      act             动作
    例
    ```
    local sfx = ssr.createWeaponAnim(1, 0, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createWingsAnim`             -- 创建一个翅膀特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      sex             性别
      act             动作
    例
    ```
    local sfx = ssr.createWingsAnim(1, 0, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```

  * `ssr.createHairAnim`              -- 创建一个发型特效
    *返回值*
      anim
    *参数*
      sfxID           特效ID
      sex             性别
      act             动作
    例
    ```
    local sfx = ssr.createHairAnim(1, 0, 0)
    parent:addChild(sfx)
    sfx:setPosition(cc.p(400,400))
    sfx:Play(0,0,true)
    ```
  
  * ` ssr.CreateStaticUIModel`    -- 创建一个角色静态模型
  >*返回值:*    Node
    *参数:(sex, feature, scale)*
    sex     -- 性别
    feature   -- 特征 table值  为{}时为裸模
    scale   -- 模型缩放比例
    >*feature 具体:*
      ```
	  ！！除特效ID外 其余装备ID传入对应装备数据的Looks参数.
      clothID     --时装ID
      clothEffectID   --时装特效ID
      weaponID      --武器ID
      weaponEffectID  --武器特效ID
      headID      --头盔ID
      headEffectID  --头盔特效ID
      capID         --斗笠
      capEffectID   --斗笠特效ID
      shieldID      --盾牌
      shieldEffectID  --盾牌特效ID
      tDressID
      tDressEffectID
      tWeaponID
      tWeaponEffectID
      veilID      --时装面巾
      veilEffectID  --时装面巾特效
      hairID      --发型
      notShowMold   --boolean: true则不显示裸模  
      notShowHair   --boolean: true则不显示头发
      ```

  例 :
  ```
  local UIModel = ssr.CreateStaticUIModel(1, {}, 1)
    UIModel:setPosition(200, -200)
    parent:addChild(UIModel)
  ```

  * `ssr.getSelectedRoleID`           -- 取得当前选择角色唯一ID
    *返回值*
      roleID
    例
    ```
    local userID = ssr.getSelectedRoleID()
    ssr.print(userID)
    ```

  * `ssr.getMainPlayerID`             -- 取得主玩家ID， 通常和ssr.getSelectedRoleID相同，但是ssr.getMainPlayerID可能为空
    *返回值*
      playerID
    例
    ```
    local mainPlayerID = ssr.getMainPlayerID()
    ssr.print(mainPlayerID)
    ```

  * `ssr.getBuffByActorID`            -- 取得某个actor所有可显示buff数据
    *返回值：*
      table
	 ```
	单条buff数据内参数说明 ：
	  id 		-- buffID
	  endTime	-- buff结束时间 [ 减去服务器时间/ssr.GetServerTime() 可得剩余时间戳 ] 
	  			  !PS: buffID在10000以内时间不准确,建议不展示倒计时
	  ol		-- 叠加层数
	```
    例 :
    ```
    local mainPlayerID = ssr.getMainPlayerID()
    local buffData = ssr.getBuffByActorID(mainPlayerID)
    ssr.PrintTable(buffData)
    ```

  * `ssr.checkHaveOnBuff`             -- 检测 人/怪/npc 是否拥有某个buff
    *返回值*
      true/false
    *参数*
      actorID
      buffID
    例
    ```
    local mainPlayerID = ssr.getMainPlayerID()
    local isHave = ssr.checkHaveOnBuff(mainPlayerID, 11)
    ssr.print("主玩家当前是否拥有魔法盾", isHave)
    ```

  * `ssr.getPlayerSkills`       --获取当前玩家已有技能
    *返回值 :*  table
    *参数 :* (noBasicSkill, activeOnly)
    noBasicSkill    -- boolean值 : 是否排除普攻
    activeOnly      -- boolean值 : 是否只获取主动技能
    ```
    local skills = ssr.getPlayerSkills(true)
    ssr.PrintTable(skills)
    ```

  * `ssr.IsInMapSafeArea`     -- 是否在安全区域
  *返回值*
  boolean
  例 :
    ```
    local isSafe = ssr.IsInMapSafeArea()
    ssr.print(isSafe)
    ```

  * `ssr.getBagData`                  -- 获取背包数据 ( 深拷贝一份数据到新表并返回 )
    *返回值*
      table
    例 :
    ```
    local items = ssr.getBagData()
    ssr.PrintTable(items)
    ```

  * `ssr.getCurBagData()`			  -- 获取背包数据 ( **！获取的为引用, 改变值会直接改变背包数据! 小心操作** )
	*返回值*
      table
  * `ssr.GetMaxBag()`				-- 获取背包开启的最大格子数
  	*返回值*
	  int
  
  * `ssr.getQuickUseData`             -- 获取快捷使用数据
    *返回值*
      table
    例 :
    ```
    local items = ssr.getQuickUseData()
    ssr.PrintTable(items)
    ```

  * `ssr.getEquipData`                -- 获取所有装备数据
    *返回值*
      table
    例 :
    ```
    local items = ssr.getEquipData()
    ssr.PrintTable(items)
    ```

  * `ssr.getEquipDataByPos(pos)`  -- 获取该装备位置的装备数据
    *参数: pos -- 装备位置ID*
    例 :
    ```
    local equipData = ssr.getEquipDataByPos(3)
    ssr.PrintTable(equipData)
    ```

  * 
  `ssr.IsRoleAlive()`     -- 获取角色是否活着  *返回值: * boolean
  `ssr.GetRoleLevel()`    -- 获取角色等级   *返回值: * int
  `ssr.GetRoleReinLv()`   -- 获取角色转生等级   *返回值: * int
  >*后两者需要在监听到 角色属性初始化或改变 事件后刷新。* 
    例 :
    ```
    local roleLevel = ssr.GetRoleLevel()
    ssr.print(roleLevel)
    ```
    
  * `ssr.ShowSystemTips(str)`     -- 弹出系统提示
    *参数 ：*      string  -- 文本内容
    例 :
    ```
    ssr.ShowSystemTips("信息不同步")
    ```

  * `ssr.UseItemByIndex(index)`   -- 快捷使用道具物品
    *参数 :*    index     -- 物品Idx
	*返回值 :*  boolean   -- 是否有该物品可用
    例 :
    ```
    ssr.UseItemByIndex(10001)
    ```
  * `ssr.RequestChangePKState(pkMode)`	-- 请求改变玩家攻击模式
  	*参数 :*  pkMode  -- 模式ID
	```
	0,          -- 全体攻击模式
	1,          -- 和平
	2,          -- 夫妻
	3,          -- 师徒
	4,          -- 组队
	5,          -- 公会
	6,          -- 善恶
	7,          -- 阵营
	```
  * `ssr.JumpToLayer(hyperlinkID)` -- 跳转打开对应界面
  	*参数 :* hyperlinkID -- 跳转ID / 超链ID 
	例：
	`ssr.JumpToLayer(32)  -- 跳转排行榜`
	>具体对应超链ID 如下 :
	
	```
		1 角色-装备		2 角色-状态		3 角色-属性		4 角色-技能
		5 角色-称号		6 角色-首饰盒		7 背包			8 摆摊			
		9 商城-热销		10 商城-装饰		11 商城-功能		12 商城-节日
		13 行会-主界面	14 行会-成员列表	15 行会-行会列表
		16 邮件			17 组队			18 附近玩家		19 装扮
		20 设置-保护		21 设置-拾取		22 设置-战斗		23 设置-基础
		24 小地图		25 技能设置		26 充值			27 拍卖行
		28 好友			29 小退(返回角色)			30 打开创建行会界面
		31 打开行会(智能打开)				32 排行榜面板 
		33 面对面交易面板	34 强制小退   	35 交易行
		36 切换按钮		37 时装界面		51 转生属性点面板
		52 聊天面板
		-----------------------英雄面板
		41 英雄-装备		42 英雄-状态		43 英雄-属性		44 英雄-技能
		45 英雄-称号		46 英雄-首饰盒	47 英雄-背包		48 英雄-时装界面
	```
	```
		-- 36 自动切换 需传第二个参数
		ssr.JumpToLayer(36, true)
	```
  * `ssr.CloseLayer( hyperlinkID )` 	-- 关闭对应超链界面
  	例 :
	```
		ssr.CloseLayer(24)
	```
  * `ssr.OpenTargetFuncDockLayer(targetID, pos)`  -- 打开对应目标ID的操作选项框 
	*参数 :* 
	targetID -- 目标ID
	pos		-- {x = x, y = y} 设置位置坐标, 以选项框左上角为锚点
	例 :
	```
	ssr.OpenTargetFuncDockLayer("1628663006000677284", {x= 100, y =200})
	```
  * `ssr.TakeOnEquipRequest(itemData, pos)`  -- 穿戴装备请求
  	*参数 :* 
	itemData	-- 装备数据
	pos			-- 装备位置
  * `ssr.TakeOffEquipRequest(itemData)` -- 脱下装备请求
  	*参数 :*  itemData -- 装备数据
	
  * `ssr.ShowLoadingBar` -- 显示转圈圈效果
    *参数 :*  time	 -- 设置自动关闭时间 可无
	例 :
	```
	ssr.ShowLoadingBar()		-- 一直播放
	```
  * `ssr.HideLoadingBar`    -- 关闭转圈效果
  * `ssr.AddToSkillActivePanel(widget)`  -- 添加控件到主界面技能-按钮块
  	例 :
	```
	local Button = ssr.Button:create()
    Button:loadTextureNormal("res/private/main/bottom/1900013017.png")
    Button:setAnchorPoint(cc.p(0, 0))
    Button:setPosition(cc.p(10, 0))
    ssr.AddToSkillActivePanel(Button)
	```
  * `ssr.AddToSkillPanel(widget)`	-- 添加控件到主界面技能-技能块

  * `ssr.ShowLocalNoticeByType(jsonData)`  -- 本地显示公告
  	*参数 :*  jsonData -- table值
	>*具体参数如下:*
      ```
	  Type		-- 公告类型
	  【
	    4: 顶部跑马灯公告 (Msg、 FColor、 BColor)  5: 屏幕跑马灯公告 可控制Y轴坐标 (Msg、 FColor、 BColor、 Y、 Count)
		6: 聊天上方公告 (Msg、 FColor、 BColor、 Time、 Label) 9: 普通通用提示 (Msg) 
		10: 可控制X轴Y轴公告  (Msg、 FColor、 BColor、 X、 Y) 11: 屏幕跑马灯公告 (系统公告) (Type、 Msg、 FColor、 BColor) 
		12: 系统频道公告 (Msg、 FColor、 BColor)  13: 带缩放效果的公告 可设置Y轴 (Msg、 FColor、 BColor、Y) 
	  】
      Msg     	-- 提示内容
      FColor   	-- 文字色值ID
      BColor	-- 背景色值ID
      Y			-- 坐标Y
	  Time		-- 倒计时
	  Count		-- 播放次数
	  Label		-- 响应Link
      ```
   
   例 :
	```
	local data = {}
    data.Msg    = "测试内容看一看"
    data.BColor = 0
    data.Y      = 130
	data.Type   = 5
    ssr.ShowLocalNoticeByType(data)
	```
  * `ssr.OpenCommonTipLayer( str, btnDesc, callback )`  -- 打开通用提示页面
  	*参数 :* 
	str  -- 文本内容 必填
	btnDesc		-- 按钮描述  顺序table数据 {按钮1文本, 按钮2文本} 可只有一个.
	callback	-- 自定义按钮回调事件 可无.
	extend		-- 额外参数 table  需要输入框时配置
	>具体如下:
	```
		showEdit = true,  -- 显示输入框
        editParams = {
			inputMode = 输入类型,  -- 0任意  2数字
            str = 默认显示内容,
            maxLength = 最大输入长度
        }
	```
	
	例 :
	```
	local function callback(bType, custom)
        if bType == 1 then
            ssr.print("按钮1触发~~")
        elseif bType == 2 then
            ssr.print("按钮2触发--")
        end
    end
    local str = "是否显示某某界面"
    local btnDesc = { "确认", "取消"}
    local extend = {
        showEdit = true,
        editParams = {
            inputMode = 0,
            str = "哈哈哈哈哈哈哈哈哈",
            maxLength = 10
        }
    }
    ssr.OpenCommonTipLayer( str, btnDesc, callback, extend)
	```
  * `ssr.StoreBuyTipsOpen(idx)`    -- 打开商城某物品购买框
  	*参数 :*  idx  -- 该物品在cfg_store商城表配置的id 
	```
	ssr.StoreBuyTipsOpen( idx )
	```
	
  * `ssr.BuyStoreItemsById(idx, count)`		-- 直接购买商场某物品
  	*参数 :*  
	idx  -- 该物品在cfg_store商城表配置的id 
	count -- 购买数量
  * `ssr.OnQuickSelectTarget(type)`		-- 快速选择目标 
  	*参数 :*  type -- 类型 1玩家 2怪物
	```
	ssr.OnQuickSelectTarget( 1 )
	```
  * `ssr.SetMainPropertyPanelVisible( state )` --设置主界面属性栏块是否显示
 	*参数 :* state -- 状态 bool值 : true显示  false隐藏
	 ```
	 ssr.SetMainPropertyPanelVisible(false)
	 ```
  * `ssr.GetBatteryPercent()`		-- 获取电量百分比值
  
  * `ssr.GetCurExpAndMaxValue()`	-- 获取当前经验值和最大经验值
  	*返回值 ：*  table值
	 {curExp = xx, maxExp = xx}	
  
  * `ssr.GetItemDataByMakeIndex(MakeIndex)`		--通过物品唯一ID 获取物品数据
  	*参数 :* makeIndex  -- 物品唯一ID
	*返回值 :*	table值

  * `ssrGlobal_ItemTipsEx( itemData )`    -- 需自定义同名全局方法 给Tips内容加显示 (固定位置: 物品来源之前)
  	*参数 :*  itemData -- 客户端传入的物品数据
	*返回值 :* widget  -- 处理后返回的控件
	例 :
	```
	function ssrGlobal_ItemTipsEx(itemData)
        if itemData and itemData.Index == 100712 then
            -- body
            local Button = ssr.Button:create()
            Button:ignoreContentAdaptWithSize(false)
            Button:loadTextureNormal("res/private/main/bottom/1900013017.png")
            return Button
        end
    end
	```
  * `ssrGlobal_ItemTipsBasePanelEx( itemData, tipsPanel )` -- 自定义同名全局方法 
  *参数：* 默认传入 itemData -- 物品数据   tipsPanel -- tips底板
  可返回控件 或者 自行添加控件到tips底板.
  例 :
  ```
  	function ssrGlobal_ItemTipsBasePanelEx( itemData, tips )
        local tipsWidth  = tips:getContentSize().width
        local tipsHeight  = tips:getContentSize().height
        ssr.print(tipsWidth)
        ssr.print(tipsHeight)
        -- 1.返回按钮
        -- local button = ssr.Button:create()
        -- button:setAnchorPoint(cc.p(0, 0.5))
        -- button:setPosition(cc.p(tipsWidth, 100))
        -- button:loadTextureNormal("res/public/1900000652.png")
        -- return button
        -- 2.自添加按钮
        local button = ssr.GUI:Button_Create(tips, "BUTTON_EX", tipsWidth, 100, "res/public/1900000652.png")
        ssr.GUI:setAnchorPoint(button, 0, 0.5)
        local function func(widget)
            for i, v in ipairs(ssr.GUI:getChildren(widget)) do
                if tolua.type(v) == "ccui.Text" then
                    ssr.print(ssr.GUI:Text_getString(v))
                end
                func(v)
            end
        end
        func(tips)
    end
  ```
  
  * `ssrGlobal_ItemTipsSuitPanelEx( itemData, tipsPanel )`	-- 套装Tips自定义方法改动
  	*参数：* 默认传入 itemData -- 物品数据   tipsPanel -- 套装tips底板
	
  * `ssrGlobal_BagItemChooseEx(MakeIndex)`  -- 提供自定义方法供手机端背包物品单击处理
    *参数：* 默认传入 物品唯一ID 
	* 返回值boolean, 是否继续原有单击事件 [false: 不再执行原有单击事件]

  * `ssr.GetMoneyCountById(id)`   -- 通过货币id 获取货币数量
  	*参数 :* id -- 货币id
	例 :
	```
		ssr.print("该货币数量为: ".. ssr.GetMoneyCountById(7))
	```

  * `ssr.GetItemConfigData()`	-- 获取物品装备表数据
	例 :
	```
		local data = ssr.GetItemConfigData()
		ssr.PrintTable(data)
	```
  * `ssr.RefreshBagPos()`	-- 整理背包
  * `ssr.SendGMMsgToChat( msg )`  -- 直接发GM命令
  	例 :
	```
		ssr.SendGMMsgToChat("Superman")   -- 发送 @Superman 命令
	```
  * `ssr.CreateExport( filename )`  -- 自适应导出CocosStudio生成的场景文件
  	*返回值 :*
	场景组件, uiTable
	例 :
	```
		local panel, ui = ssr.CreateExport("main/skill/skill_empty_cell.lua")
	    if  panel then
	        panel:setPosition(cc.p(300,-300))
	        ui.Panel_bg:setVisible(false)
	        self:addChild(panel)
	    end
	```
  * `ssr.ReturnLogin(isForce)`   -- 返回登录界面 ( 大退 )
  	*参数 :*	 isForce : boolean值 是否强制返回登录 (不填：默认不强制, 有提示框弹出)
	```
		ssr.ReturnLogin(true)
	```
  * `ssr.DoLayout(widget)`		-- 主动调用 使控件自适应父节点大小
  	*参数 :* widget: UI组件

  * `ssr.GetPlayerSkillDataById(skillID)`  -- 通过技能ID获得玩家已修炼技能数据 (未修炼则返回nil)
  	*返回值 :* table 
	 读table数据 对应参数取值：
	 Level  	-- 技能等级
	 CurTrain  	-- 技能修炼度
	 LevelUp 	-- 技能强化等级
 	例 :
	```
		local data = ssr.GetPlayerSkillDataById(56)
		if data and next(data) then
			ssr.print("此技能等级为".. data.Level or "ERROR NIL")
		end
	```  
  * `ssr.PrivateChatWithTarget( targetId, targetName )`  -- 与目标玩家私聊
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名

  * `ssr.InviteAddTeam( targetId )`			-- 邀请组队
  	*参数 :*
	 targetId  	-- 目标玩家Id

  * `ssr.ApplyInTeam( targetId )`			-- 申请入队
  	*参数 :*
	 targetId  	-- 目标玩家Id

  * `ssr.InviteAddGuild( targetId )`		-- 邀请加入行会
	*参数 :*
	 targetId  	-- 目标玩家Id

  * `ssr.AddFriend( targetId, targetName )`	-- 加为好友
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名

  * `ssr.DeleteFriend( targetId, targetName, tips)` -- 删除好友
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名
	 tips		-- 是否有提示框弹出确认

  * `ssr.AddToBlackList( targetId, targetName )`  -- 加入黑名单
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名

  * `ssr.OutFromBlackList( targetId, targetName )` -- 从黑名单中移除
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名

  * `ssr.SendTradeRequest( targetId, targetName )` -- 发送交易请求
  	*参数 :*
	 targetId  	-- 目标玩家Id
	 targetName	-- 目标玩家姓名

  * `ssr.LookPlayerInfo( targetId )`	-- 查看目标玩家信息
  	*参数 :*
	 targetId  	-- 目标玩家Id

  * `ssr.GetTeamMembers()`				-- 获取所有组队成员数据
	*返回值 :* table
	  
  * `ssr.RequestGuildMembersList()`		-- 请求所有行会成员数据
  * `ssr.GetGuildMembers()`				-- 获取所有行会成员数据
	*返回值 :* table
  
  * `ssr.IsInBlackList( uid )` 			-- 判断是否在我的黑名单内
  	*参数 :* uid -- 玩家Id
	*返回值 :* boolean
	
  * `ssr.IsMyFriend( uid )`				-- 判断是否为我的好友
  	*参数 :* uid -- 玩家Id
	*返回值 :* boolean
	
  * `ssr.IsMyTeamMember( uid )`			-- 判断是否跟我在同一队伍
  	*参数 :* uid -- 玩家Id
	*返回值 :* boolean
	
  * `ssr.IsFileExist( filePath )`		-- 判断该文件是否存在
  	*参数 :*
	filePath -- 对应文件路径
	*返回值 :*
	boolean 
  * `ssr.AFKBegin()`					-- 开始挂机
  * `ssr.AFKEnd()`						-- 结束挂机
  
  * `ssr.AttachOrUnAttachSUI(data)`		-- 自添加UI到原有界面
   *参数 :* data -- table值
    >*具体参数如下:*
      ```
		index -- 原有界面UI编号  （ 等同之前脚本挂接点id ）
		subid -- 自添加ui编号
		content -- 自添加ui内容/控件
		type	-- 类型 不填或为0表示添加 、 为1表示移除
      ```  
   >*原有界面挂接点id  :*
			101 主界面左上 
			102 主界面右上 
			103 主界面左下 
			104 主界面右下 
			105 主界面左中 
			106 主界面上中 
			107 主界面右中 
			108 主界面下中 
			109 主界面切换按钮 （仅移动端
			110 主界面任务界面
			111 主界面导航栏
			112 PC主界面聊天上方功能栏
			-- 新增主界面最底层挂接点 (官方主界面下层) [3.3.3及其以上版本新增]
			1001 主界面最底左上
			1002 主界面最底右上
			1003 主界面最底左下
			1004 主界面最底右下
			-- 新增主界面最顶层挂接点 (高于主界面小地图) [3.3.3及其以上版本新增]
			1101 主界面最顶左上
			1102 主界面最顶右上
			1103 主界面最顶左下
			1104 主界面最顶右下
			--
			2	 角色-外框主面板-(切换页签按钮也会在)
			3	角色-装备-上层
			3001 角色-装备-下层
			301  查看别人角色-装备界面-上层
			3002 查看别人角色-装备界面-下层
			4 	角色-状态
			5 	角色-属性
			6 	角色-技能
			601	查看他人角色-技能界面
			7 	角色-背包
			8 	小地图
			9  	行会 行会列表
			10 	行会 行会创建
			11 	行会 主面板
			14 	邮件 
			15 	好友
			19 	设置 保护 [19 - 22 老版本设置面板]
			20 	设置 拾取
			21 	设置 战斗
			22 	设置 操作
			23 	角色-称号
			2301   查看他人角色-称号界面
			29 	拍卖行 主面板
			30 	拍卖行 世界拍卖
			31 	拍卖行 行会拍卖
			32 	拍卖行 我的竞拍
			33 	拍卖行 我的上架
			34 	拍卖行 竞价
			35 	拍卖行 一口价
			36 	拍卖行 上架
			37 	拍卖行 下架
			38 	拍卖行 超时
			39 	角色-时装
			3901   查看他人角色-时装界面
			3902   角色-时装 下层
			3903   查看他人角色-时装界面-下层
			40 	充值界面
			41	 首饰盒界面
			4101   查看他人首饰盒
			300	新设置- 基础 [新框架- 设置]
			302	新设置- 战斗
			303	新设置- 保护
			304	新设置-挂机
			305	新设置-视距
			---
			50002 英雄-角色外框主面板(切换页签按钮也会在)
			50003 英雄-装备 上层
			53001 英雄-装备 下层
			50301 英雄-查看别人装备-上层
			53002 英雄-查看别人装备-下层
			50004 英雄-状态
			50005 英雄-属性
			50006 英雄-技能
			50007 英雄-背包
			50023 英雄-称号
			52301 英雄-查看别人称号
			50039 英雄-时装
			53901 英雄-查看别人时装
			50041 英雄-首饰盒
			54101 英雄-查看他人首饰盒
		
  	例 : 
	```
		local showText = ssr.Text:create()
    	showText:setString("测试文本")
    	showText:setFontSize(18)
    	showText:setTextColor(cc.c3b(0,255,0))
    	showText:setAnchorPoint(cc.p(0, 1))
    	showText:setFontName(ssr.define.PATH_FONT)
    	showText:setPosition(cc.p(50, 50))
    	showText:getVirtualRenderer():enableUnderline()
    	local richText = ssr.RichText:CreateRichTextWithXML(string.format( "等级-%s",100 ), 200)
    	richText:setPosition(50, 50)
    	showText:addChild(richText)
    	ssr.AttachOrUnAttachSUI({index = 110, subid = 222, content = showText})  -- 添加到任务面板
		-----
		ssr.AttachOrUnAttachSUI({index = 110, subid = 222, type = 1})		-- 从任务面板移除
	```
	
* `ssr.CheckSettingValue( id, allValue )`    -- 获取游戏设置的值
    *参数 :*
	id -- 游戏设置选项的索引  ( 具体参考cfg_setup表 )
	allValue	-- boolean 是否显示当前设置所有参数值 false则只显示第一个参数
    例 :
	```
	  ssr.PrintTable(ssr.CheckSettingValue(7, true))
	```
* `ssr.ChangeSettingValue( id, value )`	  -- 改变游戏设置
    *参数 :*
	id -- 游戏设置选项的索引 
	value	-- 可table可单个 根据当前设置参数个数调整传参 (参数1一般为是否选择 0取消1选中)
    例 :
	```
	  ssr.ChangeSettingValue(2004 , 1)
	  ssr.print("是否设置屏蔽怪物: ".. ssr.CheckSettingValue( 2004 ))
	```
* `ssr.SetSkillKey(skillID, key)`   -- 设置已有技能键位
  *参数 :*
	skillID	-- 技能ID
	key		-- 键位 (手机端配置仅显示 1-9 、 PC端1-8键位-> 快捷键Fkey 、 9-16键位-> 快捷键CTRL+Fkey)

* `ssr.DeleteSkillKey(skillID)`	-- 删除技能键位
  *参数 :*
	skillID	-- 对应技能ID

* `ssr.GetSkillKey(skillID)`		-- 获取技能键位 
  *参数 :*
	skillID	-- 对应技能ID
   例 :
	```
	ssr.print("技能58对应键位为  ".. ssr.GetSkillKey(58))
	ssr.DeleteSkillKey(58)
	ssr.print("技能58对应键位为  ".. ssr.GetSkillKey(58))
	ssr.SetSkillKey(58, 5)
	ssr.print("技能58对应键位为  ".. ssr.GetSkillKey(58))
	```
* `ssr.GetActorStallStatus( actorID )`	-- 获取玩家是否在摆摊状态
 	*参数 :*
	actorID		-- 玩家ID
	*返回值 :*
	boolean  -- 获取不到对应ID玩家 则返回nil

* `ssr.GetSkillConfig()`		-- 获取技能表数据
 	*返回值 :*  table

* `ssr.OnLaunchSkill(skillID)`		-- 释放技能
	*参数 :*  
	skillID  -- 技能ID/MagicID
	
* `ssr.GetTitleList()`		--	获取称号数据
 	*返回值 :*  table
* `ssr.GetMetaValueByKey(key, param)`  -- 获得对应元变量值
 	*参数 :*
	key  -- 元变量标识
	param  -- 取值时需要的传参 
   例 :
	```
	ssr.print(ssr.GetMetaValueByKey("MONEY", 2))
	ssr.print(ssr.GetMetaValueByKey("USERNAME"))
	```
* `ssr.PrintMetaKey()` -- 打印所有元变量标识
* `ssr.GetNetType()`	-- 获取网络状态
 	*返回值 :* int
	-1:未知  0:wifi  1:2G  2:3G  3:4G
* `ssr.GetBatteryLevel()`  -- 获取剩余电池百分比
* `ssr.Screen2World( srcPos )`	-- 屏幕坐标转世界坐标
 	*参数 :* 
	屏幕坐标	--cc.p(float, float)
* `ssr.World2Screen( srcPos )`	-- 世界坐标转屏幕坐标
 	*参数 :* 
	世界坐标	--cc.p(float, float)
* `ssr.WorldPos2MapPos( worldPos )`  -- 世界坐标转地图坐标
 	*参数 :* 
	世界坐标	--cc.p(float, float)
* `ssr.MapPos2WorldPos(  mapPos, centerOfGrid  )` -- 地图坐标转世界坐标
 	*参数 :*
	mapPos -- 地图坐标 cc.p(int, int)
	centerOfGrid -- boolean 是否在网格中心
	例 :
	```
	local mapPos = ssr.WorldPos2MapPos(ssr.Screen2World(cc.p(568, 320)))
	ssr.PrintTable(mapPos)
	local screenPos =  ssr.World2Screen(ssr.MapPos2WorldPos(mapPos, true))
	ssr.PrintTable(screenPos)		
	```
* `ssr.OpenItemTips(data)`		-- 打开道具tips面板
 	*参数 :* table
	typeId 		-- 物品id
	itemData	-- table 物品数据 ( 与typeId同时存在时，优先取itemData数据！ )
	pos 		-- tips面板打开时显示的位置 ( 不填，则默认在屏幕中央 )
	例 :
	```
	local tipsData = {}
    -- tipsData.itemData = ssr.GetItemConfigData() and ssr.GetItemConfigData()[10001]
    tipsData.typeId = 10001
	ssr.OpenItemTips(tipsData)
	```
* `ssr.GetCurLookPlayerEquipData(pos)`  -- 获取当前查看玩家的装备数据 ( 查看他人 )
 	*参数 :* 
	pos -- 为空时返回所有装备位数据 、 有值时返回对应装备位数据
 	*返回值 :*
	table -- 装备数据
	例 :
	```
	ssr.PrintTable(ssr.GetCurLookPlayerEquipData()) 
	-- [推荐配合 查看他人数据事件"OnLookPlayerDataUpdate" 触发使用]
	```
* `ssr.GetMainPlayerBaseData()` 	-- 获取主玩家基础信息
 	*返回值 :* table
	roleJob  -- 职业 int :  0 战士 1 法师 2 道士
	sex		-- 性别	int :  0 男 1 女
	level 	-- 等级	int
	reinLv	-- 转生等级 int
	name 	-- 角色名
	pkMode	-- PK模式/攻击模式 : 0全体 1和平 2夫妻 4组队 5工会 6善恶 
	例 :
	```
	ssr.PrintTable(ssr.GetMainPlayerBaseData())
	```

* `ssr.GetRoleAttrByType(type)`	-- 获取玩家属性值
 	*参数 :*
	type -- int 给定对应属性id获取对应值  ( 为空, 则返回所有属性值 )
	>*具体属性id 参考如下：*
	```
	1  --生命		2  --魔法		3  --物攻下限		4  --物攻上限		5  --魔攻下限
	6  --魔攻上限	7  --道术下限	8  --道术上限		9  --物防下限		10 --物防上限
	11 --魔防下限	12 --魔防上限	15 --魔法躲避		13 --准确			14 --敏捷
	16 --毒物躲避	17 --中毒恢复	19 --体力恢复		18 --魔法恢复		20 --攻速
	21 --暴击		22 --爆伤		23 --韧性			24 --暴击抵抗		25 --增加伤害
	26 --物伤减免	27 --魔伤减免	28 --忽视防御		29  --反弹伤害		30 --体力增加
	31 --魔力增加	32 --爆率增加	33 --爆率降低		34 --吸血			35 --攻魔道加成
	36 --防御加成	37 --魔防加成	38 --神圣伤害		39 --幸运			40 --对怪增伤 固定值
	41 --对怪增伤	42 --怒气恢复	43 --合击伤害		44 --怪物爆率		45 --防止麻痹
	46 --防止护身	47 --防止复活	48 --防止全度		49 --防止诱惑		50 --防止火墙
	51 --防止冰冻	52 --防止蛛网	54 --对战士伤害增加	55 --受到战士伤害减免
	56 --对法师伤害增加	57 --受到法师伤害减免	58 --对伤道士害增加	59 --受到道士伤害减免	60 --生命加成
	61 --生命恢复	62 --魔法恢复	63 --格挡概率		64 --格挡概率		65 --掉落概率
	66 --经验倍率	67 --基础倍攻	68 --对人伤害		69 --冰冻概率		70 --防止冰冻
	71 --每秒回血	72 --对怪爆率	73 --击力倍数		74 --对怪伤害		75 --对怪增伤
	76 --PK增伤	  77 --PK减伤	 78 --穿透			79 --致命一击		80 --致命伤害
	81 --吸血比例	82 --对怪物吸血  83 --减少来自怪物的伤害 84 --药品恢复	  85 --忽视防御抵抗
	86 --烈火减免	87 --刺杀减免	88 --攻杀减免		90 --致命一击几率减
	91 --每秒回蓝	92 --强度		93 --诅咒			94 --当前重量		95 --玩家最大负重
	96 --穿戴负重	97 --最大穿戴负重 98 --腕力			99 --当前最大可穿戴腕力
	``` 
	
	例 :
	```
	ssr.print(ssr.GetRoleAttrByType(1))
	```
* `ssr.SetBagItemChoose(data)`  -- 批量勾选背包物品
 	*参数 :* table -- 物品唯一ID( MakeIndex )数组 
	例 :
	```
	ssr.SetBagItemChoose({139608, 139610,139612,139614 ,139600,139596})
	```
* `ssr.ClearTarget()`  	-- 取消当前选中目标
* `ssr.AddBubbleTips( data )`   -- 新增/取消气泡提示在气泡栏
 	*参数 :* table -- 气泡提示参数
	id 			-- int 气泡id 	[ cfg_tipicon表 配置id及相关排序、资源参数 ] !3.3.1及后续版本删除 cfg_tipicon 表
	status		-- boolean 气泡状态  true: 加, false: 删
	callback 	-- function 气泡点击回调函数
	path		-- string 气泡图片资源路径 默认拼res/ 例："res/custom/xx.png" 只需填 "custom/xx.png"
	例 :
	```
	local data = {}
	data.id = 5
	data.status = true
	data.callback = function()
	    ssr.print("OnClick!!!!!")
	end
	ssr.AddBubbleTips( data )
	```
* `ssr.IsMainSkillPanelShow()` -- 获取主界面技能栏是否显示状态
	*返回值 :* boolean
	例 :
	```
	ssr.JumpToLayer(36, true)
	ssr.print(ssr.IsMainSkillPanelShow())
	```
	
* `ssr.GetMainPlayerMapPos()`  -- 获取主玩家所在地图坐标 
 *返回值 :* table
 例 :
 ```
 	ssr.PrintTable(ssr.GetMainPlayerMapPos())
 ```
 
* `ssr.SendCodeToExchange(convertID)`  -- 请求兑换激活码
*参数 :*  激活码
* `ssr.SendMsgToChat( mt, msg, channel, isEquip)`	-- 发送内容到聊天
 	*参数 :*  
	mt		-- 消息类型 int 1: 普通 2: 坐标 3: 装备/物品
	msg		-- 消息内容 
	> *普通消息 mt为1 时:*  string文本
	> *坐标消息 mt为2 时:*  table
	> msg = 
		{
			mapID   = 地图ID,
			mapName = 地图名字,
			mapX    = 地图坐标X轴,
			mapY    = 地图坐标Y轴,
        }
	> *装备/物品信息 mt为3 时* 传物品数据
	
	channel  -- 频道 int
	`0 -- 综合	1 -- 系统	2 -- 喊话	3 -- 私聊	4 -- 行会	5 -- 组队	6 -- 附近	7 -- 世界`
	isEquip	 -- boolean 发送已穿戴装备时为true 其余情况可缺省
	
    例 :
	```
		--发送一个背包物品到聊天
		local items = {} 
	    for _, v in pairs(ssr.getBagData()) do
	        table.insert(items, v)
	    end
	    if items[1] then
	        ssr.SendMsgToChat( 3, items[1], 6 )
	    end

		--发送一个穿戴装备到聊天
	    local equipItems = {} 
	    for _, v in pairs(ssr.getEquipData()) do
	        table.insert(equipItems, v)
	    end
	    if equipItems[1] then
	        ssr.SendMsgToChat( 3, equipItems[1], 4, true )
	    end
				
	```
* `ssr.CheckEquipPowerThanSelf(itemData)`	-- 对比传入装备和自身穿戴装备
	*参数 :* itemData	-- 物品数据
	*返回值 :* boolean  比自身强返回true 否则false
* `ssr.CreateTextInputByTextField(textField)`  -- 转cocos的textField输入框组件 为 GUI的TextInput !!
 
* `ssr.IsBagToFull(isTips)`  -- 获取背包是否已满
 	*参数 :* isTips  -- boolean 是否弹出官方默认提示
	例 :
	```
	ssr.print(ssr.IsBagToFull())
	```
* `ssr.OpenSplit(itemData)`		-- 打开拆分
 	*参数 :* itemData	-- 物品数据

* `ssr.IntoDropItem(itemData)`		-- 丢弃物品
	*参数 :* itemData	-- 物品数据

* `ssr.putInStorageItem(itemData)`		-- 物品从背包存入仓库
	*参数 :* itemData	-- 物品数据

* `ssr.putOutStorageItem(itemData)`		-- 物品从仓库取出到背包
	*参数 :* itemData	-- 物品数据
* `ssr.CloseLookPlayerLayer()`			-- 关闭查看他人界面

* `ssr.CloseItemTips()`			-- 关闭物品Tips

* `ssr.OpenAutoUseTip( itemData, equipPos, isBook, isBestRing , isHero)`  -- 打开快捷使用框
	*参数 :*
	itemData	-- 真实物品数据
	equipPos	-- int 穿戴位置  
	isBook		-- boolean 	是否是技能书
	isBestRing	-- boolean 	是否是首饰盒装备
	isHero		-- boolean	是否为英雄
	例 :
	```
	-- 普通物品
	ssr.OpenAutoUseTip( itemData )
	```

* `ssr.ShakeScene(time, distance)`
	*参数 :*
	time 		-- 震动时间 (毫秒)
	distance  	-- 震动距离
	例 :
	```
	-- 无参默认 time为700 、distance为10 
	ssr.ShakeScene()
	```

* `ssr.GetCurMapData()`		-- 获取当前地图信息
	*返回值 :* table  
	mapID 		-- 地图ID
	mapName 	-- 地图名称

* `ssr.AutoMoveBegin(x, y, mapID)`  -- 自动寻路到坐标位置
	*参数 :*
	x  			-- 地图x坐标
	y			-- 地图y坐标
	mapID		-- 地图ID

* `ssr.GetAutoMoveState()`	-- 获取 是否自动寻路
	*返回值 :*  boolean

* `ssr.PayProductRequest(currencyID, price, productIndex, payWay)` -- 调起充值
	*参数 :*
	currencyID		-- 货币ID
	price 			-- 支付金额
	productIndex	-- 产品ID
	payWay			-- 支付方式 1支付宝 2花呗 3微信
	
* `ssr.GetItemCount(index)`		-- 通过物品index获取该物品数量

* `ssr.PlaySound(id, isLoop)`		-- 播放音效
	*参数 :*
	id		-- cfg_sound表对应id
	isLoop	-- boolean 是否循环

* `ssr.GetRolesData()`		-- 获取所有角色信息

* `ssr.AddRedDot(data)`	-- 添加红点 PS:等同脚本命令 Reddot 参数1 参数2 参数3 参数4 参数5 参数6
	*参数 :*
	data 	-- table 数据
	>具体如下
	```
	{   add 	= 状态, 	-- 1添加 0删除
		mainId	= 主窗口ID,
		uiId 	= 按钮ID, 
		x 		= X坐标, 
		y 		= Y坐标, 
		mode 	= 模式, 		-- 0图片 1特效
		res 	= 图片路径或特效编号,
	}
	```

	例 :
	```
	-- 给背包物品加红点 uiId 物品唯一ID
	local data = {add = 1, mainId = 1, uiId = 2677945, x = 50, y = 50, mode = 0, res = "res/public/btn_npcfh_04.png"}
    ssr.AddRedDot( data )
	```
	
* `ssr.IsCanRevive()`		-- 获取可复活状态
	*返回值 :* boolean

* `ssr.RequestCreateGuild( guildName )`		-- 请求创建行会
	*参数 :* 
	guildName  -- 请求行会名 **!不填会默认判断创建行会页是否打开 若为打开状态则使用输入框内文本进行请求**

* `ssr.RegisterLUAEvent(eventName, eventTag, eventCB)` 		-- 注册游戏事件回调
	*参数 :*
	eventName		--	string	游戏内触发的响应事件名 
	eventTag		--  string	事件描述/标识
	eventCB			--	function 回调函数
	
	例 :
	```
	-- 注册玩家等级改变的事件回调
	local function onRefreshLevel(data)
		ssr.print("等级改变!!!!")
		ssr.PrintTable(data)
	end
	ssr.RegisterLUAEvent("onPlayerLevelChange", "LevelEvent", onRefreshLevel)
	```

* `ssr.UnRegisterLUAEvent(eventID, eventTag)`		-- 注销游戏事件回调
	*参数 :*
	eventName		--	string	游戏内触发的响应事件名 
	eventTag		--  string	事件描述/标识

* `ssr.IsShowCurPkMode(mode)`				-- 判断是否显示当前PK模式 
	*参数 :* PK模式id 	-- 0全体 1和平 2夫妻 4组队 5公会 6善恶 7国家 10区服
	*返回值 :* boolean

* `ssr.IsKfState()`					-- 是否正在跨服状态
	*返回值 :* boolen

* `ssr.RequestStoreDataByPage(page)`		-- 请求商城数据通过分页id 
	*返回值 :* table
	
* `ssr.SetClipboardText( str )`		-- 将文本复制到剪贴板
	
* `ssr.OpenBagByPos( pos )`			-- 打开背包设置坐标
	*参数 :*	 table 坐标 (初始坐标设置cc.p(0,0))

* `ssr.CheckSensitiveWordsCB( str, type, callback, ex_param )`		-- 敏感词检测
	*参数 :* 
	str			-- string 需要检测的文本
	type		-- number 文本类型 1昵称类 2聊天类 3行会公告
	callback	-- function 检测完毕的回调事件 
	ex_param	-- table 额外参数!聊天文本需要 
	`{   channelId = 聊天频道ID,  uid		  = 私聊对象id, name	  = 私聊对象昵称 }`
	例 :
	```
	local str = "猪猪猪猪"
	local function handle_Func(state, content)
		-- state 是否通过检测
		-- content 通过检测后的文本
		ssr.print(state, content)
	end
	ssr.CheckSensitiveWordsCB( str, 2, handle_Func )
	```

##### 3.3.2版本新增：
* `ssr.GetGameDataCfg()`    -- 获取游戏cfg_game_data表配置 
    *返回值 :* table

* `ssr.GetEquipDataByMakeIndex(MakeIndex, isHero)`    -- 通过唯一ID获取装备数据 isHero:是否英雄
    *返回值 :* table

* `ssr.GetBagDataByMakeIndex(MakeIndex, isHero)`    -- 通过唯一ID获取背包数据 isHero:是否英雄
    *返回值 :* table

* `ssr.GetStorageDataByMakeIndex(MakeIndex)`    -- 通过唯一ID获取仓库数据
    *返回值 :* table

* `ssr.GetLookPlayerItemDataByPos(pos, param)`    -- 获取正在查看玩家的某一装备位数据
    *返回值 :* table

* `ssr.GetLookPlayerData()`                -- 获取查看玩家数据
    *返回值 :* table

* `ssr.GetLookPlayerEquipDataByName(name)`     -- 通过名字获取查看玩家装备数据
    *返回值 :* table

* `ssr.GetEquipDataByName(name, isHero)`    -- 通过名字获取装备数据 isHero:是否英雄
    *返回值 :* table

* `ssr.CheckSetById(id)`                -- 通过id获取游戏设置值

* `ssr.SetSettingValue(id, values)`        -- 设置对应id游戏设置的值

* `ssr.TransToMiniMapPos( value1, value2 )`        -- 将地图坐标转化为小地图坐标 (仅小地图界面打开状态可用!)

##### tips相关 :
* `ssr.GetItemFromList()`        -- 获取游戏内所有来源列表 例如: 1背包 2人物装备

* `ssr.GetItemType()`            -- 获取所有物品类型 例如: 2技能书 3装备

* `ssr.GetItemTypeByData(itemData)`    -- 通过物品数据获取它的物品类型

* `ssr.GetItemDataByIndex(index)`    -- 通过物品Idx获取物品数据

* `ssr.GetDiffEquip(itemData, isHero)`    -- 获取对比装备数据

* `ssr.CheckSeverOptions(id)`            -- 检查服务器对应配置

* `ssr.GetItemNameByIndex(index)`        -- 根据道具 index 获取道具名字

* `ssr.CheckItemisBind(itemData, articleType)`    -- 检查物品是否绑定

* `ssr.GetEquipMapByStdModeList()`        -- 获取有对应装备位的stdMode列表

* `ssr.GetExtraShowLastingByStdMode()`    -- 获取额外显示持久的stdMode列表

* `ssr.GetEquipPosByStdMode( stdMode )`    -- 通过stdMode获取对应装备位

* `ssr.GetExAttType()`                -- 获取额外属性对应id列表

* `ssr.GetExAttMap()`                -- 获取 服务段下发的额外id对应的属性id列表

* `ssr.GetAttConfigByAttId( id )`    -- 获取cfg_att_score表对应id的数据

* `ssr.CheckItemUseNeed(itemData, isHero)`    -- 检查道具是否满足条件可使用 isHero：boolean 是否英雄

* `ssr.GetAttrTypeList()`                -- 获取所有属性类型

* `ssr.GetCustomDescById( id )`            -- 获取cfg_custpro_caption 对应id的描述

* `ssr.GetCustomIconShowById( id )`        -- 获取cfg_custpro_caption 对应id的图标显示

* `ssr.GetAttrConfigById( id )`            -- 获取id在cfg_att_score表内的配置

* `ssr.GetSuitConfigByName(name)`        -- 通过名字获取cfg_suit配置

* `ssr.GetSuitConfigById(id)`            -- 通过id获取cfg_suit配置

* `ssr.GetNewSuitConfigById(id)`        -- 通过id获取cfg_suitex配置
# 常用功能

# 常用功能
  * ssr.UserData 存储数据到本地
    存储
    ```
    local userData = ssr.UserData:new("test")
    userData:setStringForKey("test1", "hello")
    userData:setStringForKey("test2", "world")
    userData:writeMapDataToFile()
    ```
    读取
    ```
    local userData = ssr.UserData:new("test")
    local t1 = userData:getStringForKey("test1", "")
    local t2 = userData:getStringForKey("test2", "")
    ssr.print(t1, t2)
    ```

  * ssr.ItemShow 创建道具图标
  	* 方式一：
    *参数：itemIndex  -- 物品id*
    ```
    local itemShow = ssr.ItemShow:create(itemIndex)		-- 简单创建
    root:addChild(itemShow)
    ```

	* 方式二 :
   	*参数: table*
	index 		-- int 物品id
	itemData	-- table 物品数据		( ！有真实物品数据可直接传, 避免Tips缺漏 )
	look		-- boolean 是否显示tips
	count		-- int 物品数量
	bgVisible	-- boolean 是否显示背景图
	starLv		-- boolean 是否显示星级
	color		-- int 数量文本颜色显示  cfg_colour_style表中已有颜色id
	checkPower	-- boolean 是否检查战力从而显示提升小箭头
	showModelEffect -- boolean true: 只显示内观特效不显示背包特效
	onlyShowSFX     -- boolean true: 只显示道具特效其它都不显示
	noMouseTips		-- boolean true: 鼠标移入不显示tips

	*函数 :*
	`addReplaceClickEventListener(function)`  -- 添加替代原有点击事件
	`addPressCallBack(function)`			-- 添加长按事件
	`addDoubleEventListener(function)`		-- 添加双击事件
	`UpdateGoodsItem(itemData)`				-- 更新同一物品数据
	`setItemTouchSwallow(boolean)`			-- 设置是否触摸吞噬 (原默认true
	`setItemExtraLockStatus(boolean)`		-- 设置绑定锁是否显示 (未传入真实数据时可用

	示例 :
	```
	local data = {}
	data.index = 10001
	data.look  = true
	data.bgVisible = true
	data.count = 10
	data.color = 225
	local item = ssr.ItemShow:create(data)
	item:setPosition(300, -50)
	parent:addChild(item)
	item:setItemExtraLockStatus(true)			--显示绑定锁

	local function pressCallBack( ... )		-- 设置长按打开tips
        local tipsData = {}
        -- tipsData.itemData = ssr.GetItemConfigData() and ssr.GetItemConfigData()[tonumber(data.index)]
        tipsData.typeId = tonumber(data.index)
        tipsData.pos = item:getWorldPosition()
        ssr.OpenItemTips(tipsData)
    end

    item:addPressCallBack(pressCallBack)	
    item:addReplaceClickEventListener(function ( ... )
        ssr.print("替代原有点击触发!!!")
    end)
    item:addDoubleEventListener(function ( ... )
        ssr.print("增加双击事件~~~")
    end)
	-------------- 创建某一装备位穿戴的装备图标
	local equipData = ssr.getEquipDataByPos(1)
	if equipData and next(equipData) then
		local equipItem = ssr.ItemShow:create({itemData = equipData, look = true})
		equipItem:setPosition(30,30)
		parent:addChild(equipItem)
	end
	```

* ssr.RichText	创建富文本

	`CreateRichTextWithXML(str, width, defaultSize, defaultColor, fontFace, callback, vspace)`
	>*参数：(文本内容, 宽度, 字体大小, 文字颜色, 字体样式, 超链回调, 行距)*
	文字颜色: 采用十六进制颜色码 例"#FFFFFF"格式,  默认白色
	
	```
	local str = "<outline size='1'><font color = '#008000'>富文本呢</font></outline>"
    local richText = ssr.RichText:CreateRichTextWithXML(str , 200)
    richText:setPosition(300, -100)
    parent:addChild(richText)
	```
	
* ssr.ItemBox 创建OK框
 	*参数 : table*
	boxindex -- int OK框ID
	stdmode -- 允许传入的StdMode  "*": 所有 、单个用number 、多个用table
	img		-- string 背景图片资源路径

	*相关函数 :*
	`ssr.GetItemBoxDataByIndex(boxindex) ` -- 获取对应OK框ID的传入物品数据
	`ssr.RemoveItemBoxDataByIndex(boxindex)`	-- 清空对应OK框ID的传入物品

	`ssrGlobal_PutInItemBox(boxindex, itemData)`  -- 需自定义同名全局方法 物品放入OK框触发
	 *参数 :*
	 boxindex	-- 客户端传入的OK框ID
	 itemData	-- 客户端传入的 对应OK框物品数据

	`ssrGlobal_PutItemBoxItemToBag(boxindex, itemData)`  -- 需自定义同名全局方法 物品从OK框取出到背包触发
	 *参数 :*
	 boxindex	-- 客户端传入的OK框ID
	 itemData	-- 客户端传入的 取出OK框物品数据

	例 :
	```
	local itemBox = ssr.ItemBox:create({boxindex = 100, stdmode = {31,0} ,img  = "res/public/btn_npcsm_01.png"})
	itemBox:setPosition(100, 200)
	ssr.AttachOrUnAttachSUI({index = 3, subid = 222, content = itemBox})
	function ssrGlobal_PutInItemBox(boxindex , itemData)
		ssr.print("ItemBox框 index 为 ".. boxindex or 1)
		ssr.PrintTable(itemData)
		ssr.RemoveItemBoxDataByIndex(boxindex)
	end
	```

* ssr.GuideTask 	创建单步引导
	* 针对引导一些引擎原生界面 必需参数 :
	>*id -- int 提供的原生界面指引ID *
	*param -- int 指引参数 提供的一些原生界面对应位置指引所需参数  比如任务ID *

	* 针对引导自身创建界面/UI 必需参数 :
	>*guideWidget -- 需要指引的组件*
	*guideParent -- 指引组件的窗口父节点*
	* 通用参数 :
	>isForce	-- bool 是否强制指引 (默认不强制指引 ,即点击除指引外区域可关闭引导)
	guideDesc	-- string 指引说明/描述
	clickCB	-- function 指引位置的点击回调事件 (不填默认原有触发事件)
	autoExcute	-- int	自动执行秒数 (为空则不自动执行)
	dir		-- int 	引导框所在方位 (1-8) [为空时系统自行调整左右方位]	
	mainIdx	-- int  如若指引界面加在主界面节点 需要对应标识 ：
	`1 --左上  2 --中上  3 --右上 4 --左下  5 --中下	6 --右下`
	* 可调方法 ：
	`Start()`				-- 开始执行引导
	`Destory()`				-- 销毁该引导任务
	`SetAutoExcute(time)`	-- 设定自动执行指引秒数 

	示例 ：
	```
	local testData = {guideWidget = self._layer._ui.Button_by , guideParent = self._layer, guideDesc = "测试哦~~", isForce = true ,dir = 4, autoExcute = 2}
	local testGuide = ssr.GuideTask.new(testData)
	testGuide:Start()
		```

---------------------------------------------------------------------------------
# 网络
  * 接收网络消息 `ssr.NetworkUtil:RegisterNetworkHandler( msgID, networkCB )`,  networkCB( msgID, msgData )
  * 注销网络消息接收 `ssr.NetworkUtil:UnRegisterNetworkHandler(msgID)`
  
  * 发送接收消息 `ssr.NetworkUtil:SendMsg( msgID, sendData, p1, p2, p3 )`
  * 注意！！！ 一个msgID只能注册一个回调
  客户端自定义消息监听触发：Message_xxx,xxx 为消息号ID
  比如客户端发送消息号100，则会触发，传过来的字符串参数，会放在<$CUSTMSGPARAM> 常量里
  p1会放在<$PARAM1>，p2会放在<$PARAM2>，p3会放在<$PARAM3>
  [@Message_100]
  \#IF
  \#ACT
  SENDMSG 0 收到消息，内容是<$CUSTMSGPARAM>,p1内容是<$PARAM1>,p2内容是<$PARAM2>,p3内容是<$PARAM3>
  给客户端发消息：SendCustMsg 消息号Id  内容(格式为json)
  例
    ```
      -- 接收
      local function netCB(msgID, msgData)
        ssr.print(msgID)
        ssr.print(msgData)
      end
      ssr.NetworkUtil:RegisterNetworkHandler( 100, netCB )

      -- 发送
      ssr.NetworkUtil:SendMsg( 100, "Hello World, This ssrengine, for Lua!" )
    ```

##### 针对服务器和客户端都使用Lua的技术 ：
  * 接收网络消息 `ssr.NetworkUtil:RegisterLuaNetworkHandler( msgID, networkCB )`,  networkCB( msgID, n1, n2, n3, recvStr )
  * 注销网络消息接收 `ssr.NetworkUtil:UnRegisterLuaNetworkHandler(msgID)`
  
  * 发送网络消息 `ssr.NetworkUtil:SendLuaMsg( msgID, n1, n2, n3, sendStr )`
  例
    ```
      -- 接收
      local function netCB(msgID, n1, n2, n3, recvStr)
        ssr.print(msgID)
        ssr.print(n1, n2, n3, recvStr)
      end
      ssr.NetworkUtil:RegisterLuaNetworkHandler( 100, netCB )

      -- 发送
      ssr.NetworkUtil:SendLuaMsg( 100, 1, 2, 3, "Hello World, This ssrengine, for Lua!" )
    ```

---------------------------------------------------------------------------------
# 引擎基类
* ssrBaseObj，可被继承
  + `onEvent(eventName, eventData)`  响应事件
* ssrBaseObjUI，继承自ssrBaseObj，可被继承，用以打开界面
  + `self._ltype`   界面类型
    - `ssr.define.UI_MAIN`   主界面，必须配合mainIdx使用
    - `ssr.define.UI_NORMAL` 普通弹出面板
    - `ssr.define.UI_TIPS`   tips层
    - `ssr.define.UI_NOTICE` 通知层 最高层
  + `self._layer`   界面node
  + `self._mainIdx` 主界面索引 字符串
    - `"MAIN_NODE_LT"`  左上
    - `"MAIN_NODE_MT"`  中上
    - `"MAIN_NODE_RT"`  右上
    - `"MAIN_NODE_LB"`  左下
    - `"MAIN_NODE_MB"`  中下
    - `"MAIN_NODE_RB"`  右下
  + `self._hideMain` 是否隐藏主界面  默认false , 限UI_NORMAL类型面板可用
  + 打开界面 `OpenLayer()`
  + 关闭界面 `CloseLayer()`

---------------------------------------------------------------------------------
ssrBaseObj
  `onEvent(eventName, eventData)`

ssrBaseObjUI
  `OpenLayer()`
  `CloseLayer()`
  `onEvent(eventName, eventData)`

ssrNetworkUtil
  `RegisterNetworkHandler(msgID, handler)`
  `SendMsg(msgID, sendData)`


# ssr.GUI_教程

* 获取自带父节点
```lua
	local parent = ssr.GUI:Win_FindParent(101)

	-- 0         -- 普通面板
	-- 1,        -- 通知层
	-- 100,      -- 主界面左下(不适配刘海屏)
	-- 101,      -- 主界面左上
	-- 102,      -- 主界面右上
	-- 103,      -- 主界面左下
	-- 104,      -- 主界面右下
	-- 105,      -- 主界面左中
	-- 106,      -- 主界面上中
	-- 107,      -- 主界面右中
	-- 108,      -- 主界面下中
	-- 109,      -- 主界面 -按钮模块 
	-- 110,      -- 主界面 -任务模块
	-- 111,      -- 主界面 -状态栏
	-- 1001,     -- 主界面最底左上
	-- 1002,     -- 主界面最底右上
	-- 1003,     -- 主界面最底左下
	-- 1004,     -- 主界面最底右下
	-- 1101,     -- 主界面最顶左上
	-- 1102,     -- 主界面最顶右上
	-- 1103,     -- 主界面最顶左下
	-- 1104,     -- 主界面最顶右下
```

* 增加组件到主界面
```lua
	-- 加到主界面 左上
    local parent = ssr.GUI:Win_FindParent(101)
    local Button_101 = ssr.GUI:Image_Create(parent, "Button_101", 100, -50, "res/public/btn_bbgm_02.png")
    ssr.GUI:setTouchEnabled(Button_101, true)
    ssr.GUI:addOnClick(Button_101, function()
        ssr.ShowSystemTips("Button_101")
    end)

    -- 加到主界面 右上
    local parent = ssr.GUI:Win_FindParent(102)
    local Button_102 = ssr.GUI:Image_Create(parent, "Button_102", -200, -50, "res/public/btn_bbgm_02.png")
    ssr.GUI:setTouchEnabled(Button_102, true)
    ssr.GUI:addOnClick(Button_102, function()
        ssr.ShowSystemTips("Button_102")
    end)
```

* 加载CocosStudio导出
```lua
    -- 加载 cocostudio导出
    local ccsWin, quickUI = ssr.GUI:LoadExport(0, 1, "game/view/export/mini_map/mini_map.lua")
    ssr.GUI:setPosition(quickUI.Button_close, 50, 50)
    ssr.GUI:addOnClick(quickUI.Button_close, function()
        ssr.GUI:Win_Close(ccsWin)
    end)
```

* 加载老脚本字符串
```lua
    -- 加载老脚本
    local str = 
    [[
        <Img|move=0|img=public/bg_npc_01.png|loadDelay=1|bg=1|reset=1|show=0>
        <Layout|x=545|y=0|width=80|height=80|link=@exit>
        <Button|x=546|y=0|nimg=public/1900000510.png|pimg=public/1900000511.png|link=@exit>
        <RText|x=25|y=20|text=对对对>
        <Button|x=172.0|y=53.0|nimg=public/00000361.png|mimg=public/00000363.png|pimg=public/00000362.png|size=18|color=255|text=Button|link=@123>             
    ]]
    local sayWin = nil
    local function linkCB(cdata)
        if cdata.Act == "@exit" then
            ssr.GUI:Win_Close(sayWin)
        end
    end
    sayWin = ssr.GUI:LoadSay(0, 0, str, linkCB)
```

# ssr.GUI_API

```
-------------------------------------------------------------
-- 通过ID获取对应父节点
ssr.GUI:Win_FindParent(ID)

-- 关闭窗口
ssr.GUI:Win_Close(widget)

-- 创建新窗口  canMove:boolean 是否可拖动
ssr.GUI:Win_Create(parent, ID, x, y, width, height, canMove)

-- 添加窗口按ESC关闭
ssr.GUI:Win_SetInESCClose(widget)

-- 添加窗口绑定NPCID
ssr.GUI:Win_SetBindNPCIndex(widget, npcID)

-- 窗口设置禁止右键穿透  value: boolean true则禁止穿透
ssr.GUI:Win_SetSwallowRightMouseTouch(widget, value)

-- 加载原脚本txt内容
ssr.GUI:LoadSay(parent, ID, str, linkCB)

-- 加载cocos studio导出文件
ssr.GUI:LoadExport(parent, ID, filename)

-------------------------------------------------------------
-- 常用方法

-- 设置/获取控件位置
ssr.GUI:setPosition(widget, x, y)

ssr.GUI:getPosition(widget)

-- 设置/获取控件X轴坐标
ssr.GUI:setPositionX(widget, value)

ssr.GUI:getPositionX(widget)

-- 设置/获取控件Y轴坐标
ssr.GUI:setPositionY(widget, value)

ssr.GUI:getPositionY(widget)

-- 设置/获取控件锚点
ssr.GUI:setAnchorPoint(widget, x, y)

ssr.GUI:getAnchorPoint(widget)

-- 设置/获取控件尺寸大小
ssr.GUI:setContentSize(widget, size)

ssr.GUI:getContentSize(widget)

-- 设置/获取控件旋转角度
ssr.GUI:setRotation(widget, value)

ssr.GUI:getRotation(widget)

-- 设置/获取控件可见性 boolean
ssr.GUI:setVisible(widget, value)

ssr.GUI:getVisible(widget)

-- 设置/获取控件的不透明度 0-255
ssr.GUI:setOpacity(widget, value)

ssr.GUI:getOpacity(widget)

-- 设置/获取控件的缩放比例
ssr.GUI:setScale(widget, value)

ssr.GUI:getScale(widget)

-- 设置/获取控件X轴的缩放比例
ssr.GUI:setScaleX(widget, value)

ssr.GUI:getScaleX(widget)

-- 设置/获取控件Y轴的缩放比例
ssr.GUI:setScaleY(widget, value)

ssr.GUI:getScaleY(widget)

-- 设置/获取控件X轴方向是否翻转 boolean 
ssr.GUI:setFlippedX(widget, value)

ssr.GUI:getFlippedX(widget)

-- 设置/获取控件Y轴方向是否翻转 boolean 
ssr.GUI:setFlippedY(widget, value)

ssr.GUI:getFlippedY(widget)

-- 设置/获取控件可点性
ssr.GUI:setTouchEnabled(widget, value)

ssr.GUI:getTouchEnabled(widget)

-- 获取控件父节点
ssr.GUI:getParent(widget)

-- 获取控件所有的子节点
ssr.GUI:getChildren(widget)

-- 通过名字获取控件对应子节点
ssr.GUI:getChildByName(widget, name)

-- 将控件从父节点移除
ssr.GUI:removeFromParent(widget)

-- 通过名字移除对应子节点
ssr.GUI:removeChildByName(widget, name)

-- 移除所有子节点
ssr.GUI:removeAllChildren(widget)

-- 使控件执行某个动作 action
ssr.GUI:runAction(widget, value)
-- 控件停止所有动作
ssr.GUI:stopAllActions(widget)

-- 加点击事件 function
ssr.GUI:addOnClick(widget, value)

-- 加触摸事件 function
ssr.GUI:addOnTouch(widget, value)

-- 加鼠标移动事件 param: table 
   具体参数 ->
   onEnterFunc : 进入控件回调
   onLeaveFunc : 移出控件回调
ssr.GUI:addMouseMoveEvent(widget, param)

-- 加鼠标进入显示tips str: 文本 pos: 位置  anr: 锚点
ssr.GUI:addMouseOverTips(widget, str, pos, anr, param)

-- 设置控件是否跟随父控件变化透明度 param: boolean
ssr.GUI:setCascadeOpacityEnabled(widget, value)

-- 设置控件是否跟随父控件变化颜色 param: boolean
ssr.GUI:setCascadeColorEnabled(widget, value)

-------------------------------------------------------------
-- **NewWin 新新窗口类型** ！有别于Win, 加入界面管理 可控、监听游戏事件更简易
-- 创建新窗口 
	hideMain: 	是否隐藏主界面 	boolean		默认false
	hideLast: 	是否隐藏上一界面 	boolean		默认false
	needVoice: 	是否点击时有音效 	boolean		默认false
	escClose: 	是否能ESC键关闭 	boolean  	默认true
	isRevmsg: 	是否屏蔽触摸  	boolean		默认false
ssr.GUI:NewWin_Create(ID, x, y, width, height, hideMain, hideLast, needVoice, escClose, isRevmsg)

-- 关闭窗口 传入窗口控件 
ssr.GUI:NewWin_Close(widget)

-- 关闭所有新窗口
ssr.GUI:NewWin_CloseAll()

-- 关闭窗口 传入窗口ID
ssr.GUI:NewWin_CloseByID(ID)

-- 关闭窗口 传入绑定的NPCID
ssr.GUI:NewWin_CloseByNPCID(NPCID)

-- 设置窗口参数
ssr.GUI:NewWin_SetParam(widget, param)

-- 获取窗口参数
ssr.GUI:NewWin_GetParam(widget)

-- 设置窗口ESC关闭  boolean
ssr.GUI:NewWin_SetESCClose(widget, value)

-- 设置窗口可拖拽区域	传入控件
ssr.GUI:NewWin_SetDrag(widget, dragLayer)

-- 设置窗口绑定NPCID
ssr.GUI:NewWin_BindNPC(widget, npcID)

-- 设置窗口点击上浮区域 传入控件
ssr.GUI:NewWin_SetTouchZPanel(widget, touchPanel)

-- 设置窗口监听游戏事件 eventName : 事件名  func : 回调方法
ssr.GUI:NewWin_RegisterGameEvent(widget, eventName, func)

-------------------------------------------------------------
-- Win
-- 设置窗口位置 show : 0 左上角 1 右上角 2 左下角 3 右下角 4 屏幕中心
ssr.GUI:Win_setShow(widget, show)

-- 设置窗口背景色 color3B
ssr.GUI:Win_setBackGroundColor(widget, value)

-- 设置窗口背景不透明度 0-255
ssr.GUI:Win_setBackGroundOpacity(widget, value)

-------------------------------------------------------------
-- Image
-- 创建图片 (父节点, 标识, x坐标, y坐标, 图片路径)
ssr.GUI:Image_Create(parent, ID, x, y, nimg)

-- 设置图片路径
ssr.GUI:Image_loadTexture(widget, filepath)

-- 设置九宫格参数
ssr.GUI:Image_setScale9Slice(widget, scale9l, scale9r, scale9t, scale9b)

-------------------------------------------------------------
-- Button
-- 创建按钮
ssr.GUI:Button_Create(parent, ID, x, y, nimg)

-- 设置按钮正常图片
ssr.GUI:Button_loadTextureNormal(widget, filepath)

-- 设置按钮按下图片
ssr.GUI:Button_loadTexturePressed(widget, filepath)

-- 设置按钮禁用图片
ssr.GUI:Button_loadTextureDisabled(widget, filepath)

-- 设置按钮文本
ssr.GUI:Button_setTitleText(widget, value)

-- 设置按钮文本颜色 color3B
ssr.GUI:Button_setTitleColor(widget, value)

-- 设置按钮字体大小
ssr.GUI:Button_setTitleFontSize(widget, value)

-- 设置显示状态 boolean 正常/禁用
ssr.GUI:Button_setBright(widget, value)

-- 设置按钮文本最大宽度
ssr.GUI:Button_setMaxLineWidth(widget, value)

-- 设置按钮文本加描边显示 color: 描边颜色rgb size: 描边大小
ssr.GUI:Button_titleEnableOutline(widget, color, size)

-------------------------------------------------------------
-- Text
-- 创建文本 (父节点, 标识, x坐标, y坐标, 字号, 文本颜色, 文本内容)
ssr.GUI:Text_Create(parent, ID, x, y, fontSize, fontColor, str)

-- 设置文本内容
ssr.GUI:Text_setString(widget, value)

-- 设置文本颜色 color3B
ssr.GUI:Text_setTextColor(widget, value)

-- 设置字体大小
ssr.GUI:Text_setFontSize(widget, value)

-- 设置文本字体 value:字体路径
ssr.GUI:Text_setFontName(widget, value)

-- 设置描边 (控件, 描边颜色, 描边大小)
ssr.GUI:Text_enableOutline(widget, color, size)

-- 加下划线
ssr.GUI:Text_enableUnderline(widget)

-------------------------------------------------------------
-- Layout
-- 创建基础容器 (父节点, 标识, x坐标, y坐标, 宽, 高, 是否超出裁剪)
ssr.GUI:Layout_Create(parent, ID, x, y, width, height, isClip)

-- 设置背景颜色
ssr.GUI:Layout_setBackGroundColor(widget, value)

-- 设置背景颜色类型 0:无 1：纯色
ssr.GUI:Layout_setBackGroundColorType(widget, value)

-- 设置背景色不透明度 0-255
ssr.GUI:Layout_setBackGroundColorOpacity(widget, value)

-- 设置是否裁剪内容 boolean
ssr.GUI:Layout_setClippingEnabled(widget, value)

-------------------------------------------------------------
-- LoadingBar
-- 创建进度条
ssr.GUI:LoadingBar_Create(parent, ID, x, y, nimg, direction)

-- 设置进度条样式图片 
ssr.GUI:LoadingBar_loadTexture(widget, value)

-- 设置进度条加载方向 0: 从左到右 1: 从右到左
ssr.GUI:LoadingBar_setDirection(widget, value)

-- 设置进度条加载的进度值 0-100
ssr.GUI:LoadingBar_setPercent(widget, value)

-- 获取进度条的进度值
ssr.GUI:LoadingBar_getPercent(widget)

-------------------------------------------------------------
-- TextInput
-- 创建输入框
ssr.GUI:TextInput_Create(parent, ID, x, y, width, height, fontSize)

-- 设置输入文本颜色
ssr.GUI:TextInput_setFontColor(widget, value)

-- 设置输入文本字体格式 value: 通用TTF文件路径 value2: 字体大小
ssr.GUI:TextInput_setFont(widget, value, value2)

-- 设置输入文本字体大小
ssr.GUI:TextInput_setFontSize(widget, value)

-- 设置占位文本字体格式 value: 通用TTF文件路径 value2: 字体大小
ssr.GUI:TextInput_setPlaceholderFont(widget, value, value2)

-- 设置占位文本颜色
ssr.GUI:TextInput_setPlaceholderFontColor(widget, value)

-- 设置占位文本字体大小
ssr.GUI:TextInput_setPlaceholderFontSize(widget, value)

-- 设置占位文本内容
ssr.GUI:TextInput_setPlaceHolder(widget, value)

-- 设置输入文本最大长度
ssr.GUI:TextInput_setMaxLength(widget, value)

-- 设置/获取输入文本内容
ssr.GUI:TextInput_setString(widget, value)

ssr.GUI:TextInput_getString(widget)

-- 设置输入文本水平对齐方式 0: 左对齐 1: 居中 2: 右对齐
ssr.GUI:TextInput_setTextHorizontalAlignment(widget, value)

-- 设置格式化显示输入文本 0: 加密输入内容
ssr.GUI:TextInput_setInputFlag(widget, value)

-- 设置允许输入的文本类型模式 0: 可输入任何文本 1: 允许输入电子邮件地址  2: 允许输入数字
ssr.GUI:TextInput_setInputMode(widget, value)

-- 输入框添加监听事件
ssr.GUI:TextInput_addOnEvent(widget, eventCB)

-------------------------------------------------------------
-- TextAtlas
-- 创建艺术数字 (父节点, 标识, x坐标, y坐标, 文本内容, 图片路径, 字符宽, 字符高, 初始字符)
ssr.GUI:TextAtlas_Create(parent, ID, x, y, stringValue, charMapFile, itemWidth, itemHeight, startCharMap)

-- 设置艺术字体属性
ssr.GUI:TextAtlas_setProperty(widget, stringValue, charMapFile, itemWidth, itemHeight, startCharMap)

-- 设置/获取文本内容
ssr.GUI:TextAtlas_setString(widget, value)

ssr.GUI:TextAtlas_getString(widget)

-------------------------------------------------------------
-- Slider
-- 创建滑动条 (父节点, 标识, x坐标, y坐标, 滑动条背景底图, 滑动条内部图, 滑动标识图)
ssr.GUI:Slider_Create(parent, ID, x, y, barimg, pbarimg, nimg)

-- 设置滑动条背景底图 文件路径
ssr.GUI:Slider_loadBarTexture(widget, value)

-- 设置滑动条内部样式图片
ssr.GUI:Slider_loadProgressBarTexture(widget, value)

-- 设置滑动条滑动标识图片
ssr.GUI:Slider_loadSlidBallTextureNormal(widget, value)

-- 设置/获取滑动到的百分比值 0-100
ssr.GUI:Slider_setPercent(widget, value)

ssr.GUI:Slider_getPercent(widget)

-- 加监听事件 
ssr.GUI:Slider_addOnEvent(widget, eventCB)

-------------------------------------------------------------
-- ListView
-- 创建列表容器
ssr.GUI:ListView_Create(parent, ID, x, y, width, height, direction)

-- 设置滚动方向 1: 垂直方向 2: 水平方向
ssr.GUI:ListView_setDirection(widget, value)

-- 设置子控件间隔
ssr.GUI:ListView_setItemsMargin(widget, value)

-- 设置是否有回弹效果 boolean
ssr.GUI:ListView_setBounceEnabled(widget, value)

-- 设置是否裁剪内容 boolean
ssr.GUI:ListView_setClippingEnabled(widget, value)

-- 添加子控件到列表容器中 value: 子控件
ssr.GUI:ListView_pushBackCustomItem(widget, value)

-- 插入子控件到列表容器中指定位置 value2: 指定位置
ssr.GUI:ListView_insertCustomItem(widget, value, value2)

-- 移除列表容器所有的子控件
ssr.GUI:ListView_removeAllItems(widget)

-- 跳转到指定下标的子控件 value: 指定下标
ssr.GUI:ListView_JumpToItem(widget, value)

-- 获取指定子控件的下标  value: 子控件
ssr.GUI:ListView_GetItemIndex(widget, value)

-- 设置列表容器背景颜色
ssr.GUI:ListView_setBackGroundColor(widget, value)

-- 设置背景颜色不透明度 0-255
ssr.GUI:ListView_setBackGroundOpacity(widget, value)

-- 获取列表容器子控件数量
ssr.GUI:ListView_getItemCount(widget)

-- 获取列表容器滚动区域大小
ssr.GUI:ListView_getInnerContainerSize(widget)

-- 获取列表容器滚动区域位置
ssr.GUI:ListView_getInnerContainerPosition(widget)

-- 使列表容器滚动到某百分比位置(垂直方向) percent:百分比 0~100  time: 滚动时间 bool: 是否衰减滚动速度
ssr.GUI:ListView_scrollToPercentVertical(widget, percent, time, bool)

-- 使列表容器跳转到某百分比位置(垂直方向) percent:百分比 0~100
ssr.GUI:ListView_jumpToPercentVertical(widget, percent)

-- 添加列表容器滚动事件
ssr.GUI:ListView_addOnScrollEvent(widget, eventCB)

-------------------------------------------------------------
-- CheckBox
-- 创建复选框
ssr.GUI:CheckBox_Create(parent, ID, x, y, nimg, pimg)

-- 设置复选框正常状态下的背景图片
ssr.GUI:CheckBox_loadTextureBackGround(widget, value)

-- 设置复选框正常状态下的标识图片
ssr.GUI:CheckBox_loadTextureFrontCross(widget, value)

--  设置复选框禁用状态下的标识图片
ssr.GUI:CheckBox_loadTextureFrontCrossDisabled(widget, value)

-- 设置/获取复选框是否选中 boolean
ssr.GUI:CheckBox_setSelected(widget, value)

ssr.GUI:CheckBox_isSelected(widget)

-- 加监听事件
ssr.GUI:CheckBox_addOnEvent(widget, eventCB)

-------------------------------------------------------------
-- Effect
-- 创建一个特效 effecttype: 特效类型 (0:普通、1:NPC、2:怪物、3:技能、4:人物、5:武器、6:翅膀、7:发型)
ssr.GUI:Effect_Create(parent, ID, x, y, effecttype, effectid, sex, act, dir, speed)

-- 播放特效 isLoop: 是否循环 boolean
ssr.GUI:Effect_Play(widget, act, dir, isLoop, speed, isSequence)

-- 停止播放特效 
ssr.GUI:Effect_Stop(widget, frameIndex, act, dir)

-- 添加动画完成回调事件
ssr.GUI:Effect_addOnCompleteEvent(widget, eventCB)

-------------------------------------------------------------
-- RichText
-- 创建富文本
ssr.GUI:RichText_Create(parent, ID, x, y, str, width, fontSize, fontColor, vspace, hyperlinkCB)

-------------------------------------------------------------
-- PageView
-- 创建翻页容器
ssr.GUI:PageView_Create(parent, ID, x, y, width, height)

-- 设置是否裁剪
ssr.GUI:PageView_setClippingEnabled(widget, value)

-- 设置背景颜色
ssr.GUI:PageView_setBackGroundColor(widget, value)

-- 设置背景颜色类型 0:无 1:纯色
ssr.GUI:PageView_setBackGroundColorType(widget, value)

-- 设置背景颜色不透明度 0-255
ssr.GUI:PageView_setBackGroundColorOpacity(widget, value)

-- 滚动到某一下标页面
ssr.GUI:PageView_scrollToItem(widget, index)

-- 获取当前页下标
ssr.GUI:PageView_getCurrentPageIndex(widget)

-- 获取所有项
ssr.GUI:PageView_getItems(widget)

-- 获取所有项数量
ssr.GUI:PageView_getItemCount(widget)

-- 添加页
ssr.GUI:PageView_addPage(widget, value)

-- 加监听事件
ssr.GUI:PageView_addOnEvent(widget, eventCB)

-------------------------------------------------------------
-- ProgressTimer
-- 创建圆形进度条
ssr.GUI:ProgressTimer_Create(parent, ID, x, y, img)

-- 设置/获取百分比进度
ssr.GUI:ProgressTimer_setPercentage(widget, value)

ssr.GUI:ProgressTimer_getPercentage(widget)

-- 执行进度条转动动作 time:时长 from:起始进度 to:结束进度 completeCB:动作完成回调函数
ssr.GUI:ProgressTimer_ProgressFromTo(widget, time, from, to, completeCB)

-------------------------------------------------------------
-- QuickCell
-- 创建QuickCell优化加载  w:宽 h:高 createCB:创建方法 默认传入父节点、需返回添加组件
ssr.GUI:QuickCell_Create(parent, ID, x, y, w, h, createCB)

-------------------------------------------------------------
-- ScrollView
-- 创建滚动容器	width: 显示宽度 height: 显示高度  direction: 滚动方向
ssr.GUI:ScrollView_Create(parent, ID, x, y, width, height, direction)

-- 设置滚动容器内部滚动区域大小 (大于显示大小 则可滚动) value1: 宽 value2: 高
ssr.GUI:ScrollView_setInnerContainerSize(widget, value1, value2)

-- 设置滚动方向 1: 垂直方向 2: 水平方向
ssr.GUI:ScrollView_setDirection(widget, value)

-- 设置是否回弹  boolean
ssr.GUI:ScrollView_setBounceEnabled(widget, value)

-- 使滚动容器滚动到顶部 time: 时间 boolvalue: 速度是否衰减 true:衰减 false:匀速
ssr.GUI:ScrollView_scrollToTop(widget, time, boolvalue)

-- 使滚动容器滚动到底部  参数同上
ssr.GUI:ScrollView_scrollToBottom(widget, time, boolvalue)

-- 使滚动容器滚动到左部  参数同上
ssr.GUI:ScrollView_scrollToLeft(widget, time, boolvalue)

-- 使滚动容器滚动到右部  参数同上
ssr.GUI:ScrollView_scrollToRight(widget, time, boolvalue)

-- 设置背景颜色 value: {r=xx, g=xx, b=xx}
ssr.GUI:ScrollView_setBackGroundColor(widget, value)

-- 设置背景颜色不透明度 0-255
ssr.GUI:ScrollView_setBackGroundOpacity(widget, value)

-- 设置滚动事件 eventCB: function
ssr.GUI:ScrollView_addOnScrollEvent(widget, eventCB)

-------------------------------------------------------------
-- TableView
-- 创建列表容器 (优化加载版! 初次加载只加载可视区域组件) 
-- cellWid: 单个cell的宽 cellHei: 单个cell的高  num: 需创建cell个数
ssr.GUI:TableView_Create(parent, ID, x, y, width, height, direction, cellWid, cellHei, num)

-- 设置滚动方向 1: 垂直方向 2: 水平方向
ssr.GUI:TableView_setDirection( widget, value )

-- 设置背景颜色
ssr.GUI:TableView_setBackGroundColor(widget, value)

-- 添加点击cell事件 function
ssr.GUI:TableView_addOnTouchedCellEvent( widget, func )

-- 全局方法实现 创建该列表容器的cell 传入参数: (cell父节点, cell下标, 列表容器ID)  [参考示例]
ssrGlobal_GUITableViewCell_Create( parent, idx, ID )

-------------------------------------------------------------
-- ItemShow
-- 创建道具图标 setData : 可参考【常用功能】-> ssr.ItemShow
ssr.GUI:ItemShow_Create(parent, ID, x, y, setData)

-- 加点击事件
ssr.GUI:ItemShow_AddReplaceClickEvent(widget, eventCB)

-- 加长按事件
ssr.GUI:ItemShow_AddPressEvent(widget, eventCB)

-- 加双击事件
ssr.GUI:ItemShow_AddDoubleEvent(widget, eventCB)

-- 置灰道具图标 value: boolean
ssr.GUI:ItemShow_setIconGrey( widget, value)

-------------------------------------------------------------
-- ItemBox
-- 创建物品放入框 boxindex: int OK框ID stdmode: 允许传入的StdMode ("*": 所有 、单个用number 、多个用table)
ssr.GUI:ItemBox_Create(parent, ID, x, y, img, boxindex, stdmode)

-- 获取对应OK框ID的物品数据
ssr.GUI:ItemBox_GetItemData(widget, boxindex)

-- 清空对应OK框ID的传入物品
ssr.GUI:ItemBox_RemoveBoxData(widget, boxindex)

-------------------------------------------------------------
-- Frames
-- 创建序列帧 prefix: 前缀 suffix: 后缀 finishframe: 结束帧  
-- ext : 附加参数 {speed = 播放速度(毫秒), count = 图片数量, loop = 播放次数(-1: 循环), finishhide = 播放结束是否隐藏(1: 隐藏)}
ssr.GUI:Frames_Create(parent, ID, x, y, prefix, suffix, finishframe, ext)

-------------------------------------------------------------
-- TIMETIPS
-- 创建倒计时提示 linkCB: function 倒计时结束后跳转函数
ssr.GUI:TIMETIPS_Create(parent, ID, x, y, size, color, time, linkCB)

-------------------------------------------------------------
-- CircleBar
-- 创建圆形进度条 (父节点, 标识, x坐标, y坐标, 背景图资源, 进度条资源, 开始进度, 结束进度, 加载时长)
ssr.GUI:CircleBar_Create(parent, ID, x, y, bgImg, barImg, startper, endper, time)

-- 设置进度条基于背景图中心点 的偏移
ssr.GUI:CircleBar_setBarOffSet(widget, offsetX, offsetY)

-- 添加加载完毕后的回调事件  linkCB: function
ssr.GUI:CircleBar_AddEndLinkCB(widget, linkCB)

-------------------------------------------------------------
-- PercentImg
-- 创建百分比图片 img:图片资源 direction: 方向 minValue: 显示值 maxValue: 最大值
ssr.GUI:PercentImg_Create(parent, ID, x, y, img, direction, minValue, maxValue)

-------------------------------------------------------------
-- UIModel
-- 创建人物模型
ssr.GUI:UIModel_Create(parent, ID, x, y, sex, feature, scale)

-------------------------------------------------------------
-- EquipShow
-- 创建装备图标 pos: 装备位id bgVisible: 是否显示背景  showtips：是否显示tips showstar: 是否显示星级 isHero: 是否是英雄
ssr.GUI:EquipShow_Create(parent, ID, x, y, pos, bgVisible, showtips, showstar, isHero)

-- 设置装备图标缩放 value: 缩放比例
ssr.GUI:EquipShow_setScale( widget, value )

-- 设置装备图标置灰显示 value: boolean
ssr.GUI:EquipShow_setIconGrey( widget, value )

-------------------------------------------------------------
-- DBItemShow
-- 创建数据库道具图标  makeindex: 唯一ID isHero: 是否为英雄的
ssr.GUI:DBItemShow_Create(parent, ID, x, y, makeindex, bgVisible, showtips, showstar, isHero)

-- 设置缩放比例
ssr.GUI:DBItemShow_setScale( widget, value )

-- 设置是否灰化显示
ssr.GUI:DBItemShow_setIconGrey( widget, value )

-- 设置数量显示
ssr.GUI:DBItemShow_setCount( widget, value )

----------------------------------------------------------
--- Timeline 
-- 动作/效果相关
可参照纯lua版本说明书 : http://engine-doc.996m2.com/web/#/29/337

```
# ssr.GUI_测试代码

```lua
-- wnd
local winWidth = 900
local winHeight = 600
local wnd = ssr.GUI:Win_Create(0, "Win_1", 0, 0, winWidth, winHeight, true)
ssr.GUI:Win_setShow(wnd, 4)
ssr.GUI:Win_setBackGroundColor(wnd, ssr.Color3B.BLACK)
ssr.GUI:Win_setBackGroundOpacity(wnd, 150)
ssr.GUI:Win_SetInESCClose(wnd)
-- ssr.GUI:Win_SetBindNPCIndex( wnd,  "10253")
ssr.GUI:Win_SetSwallowRightMouseTouch(wnd, true)

-- 取出窗口大小
local wndSize = ssr.GUI:getContentSize(wnd)

-- 背景图
local image = ssr.GUI:Image_Create(wnd, "Image_bg", wndSize.width/2, wndSize.height/2, "res/public/1900000672.png")
ssr.GUI:addMouseMoveEvent(image, {
    onEnterFunc = function()
        ssr.print(" !!!!!! OnEnter image")
    end,
    onLeaveFunc = function()
        ssr.print(" !!!!!! OnLeave image")
    end,
})

-- 关闭按钮
local button = ssr.GUI:Button_Create(wnd, "Button_1", wndSize.width, wndSize.height, "res/public/1900000510.png")
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:setAnchorPoint(button, 1, 1)
ssr.GUI:addOnClick(button, function()
    ssr.GUI:Win_Close(wnd)
end)

-- listview
local listview = ssr.GUI:ListView_Create(wnd, "ListView_1", 0, 0, 106, wndSize.height, 1)
ssr.GUI:ListView_setBounceEnabled(listview, true)
ssr.GUI:ListView_setItemsMargin(listview, 20)

-- Image 展示
local button = ssr.GUI:Button_Create(listview, "Button_1", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "普通图片")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
-- ssr.GUI:Button_SetGrey(button, true)     
ssr.GUI:addOnClick(button, function()
    local image = ssr.GUI:Image_Create(wnd, "Image_", wndSize.width/2, wndSize.height/2, "res/public/icon_fubentg_03_1.png")
    -- ssr.GUI:Image_SetGrey(image, true)
    -- image
    ssr.performWithDelay(image, function()
        image:removeFromParent()
    end, 5)
end)

-- Image 九宫格
local button = ssr.GUI:Button_Create(listview, "Button_2", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "九宫图片")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local image = ssr.GUI:Image_Create(wnd, "Image_2", wndSize.width/2, wndSize.height/2, "res/public/1900000677.png")
    ssr.GUI:Image_setScale9Slice(image, 10, 10, 10, 10)
    local index = 1
    ssr.schedule(image, function()
        index = index + 1
        ssr.GUI:setContentSize(image, cc.size(index * 50, index * 50))
    end, 1)
    ssr.performWithDelay(image, function()
        image:removeFromParent()
    end, 5)
end)

-- Text
local button = ssr.GUI:Button_Create(listview, "Button_Text", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "文本")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:Text_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 20, ssr.Color3B.RED, "我是测试内容")

    ssr.schedule(widget, function()
        ssr.GUI:Text_setFontSize(widget, ssr.random(10, 50))
        ssr.GUI:Text_setTextColor(widget, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))
    end, 0.5)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- layout
local button = ssr.GUI:Button_Create(listview, "Button_layout", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "容器")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:Layout_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 100, 100, true)
    ssr.GUI:Layout_setBackGroundColorType(widget, 1)

    ssr.schedule(widget, function()
        ssr.GUI:Layout_setBackGroundColorOpacity(widget, ssr.random(50, 255))
        ssr.GUI:Layout_setBackGroundColor(widget, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))
    end, 0.5)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- loadingbar
local button = ssr.GUI:Button_Create(listview, "Button_LoadingBar_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "进度条")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:LoadingBar_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/bg_szjm_03_2.png", 0)

    ssr.schedule(widget, function()
        ssr.GUI:LoadingBar_setPercent(widget, ssr.random(0, 100))
        ssr.print(ssr.GUI:LoadingBar_getPercent(widget))
    end, 0.5)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- TextInput_Create
local button = ssr.GUI:Button_Create(listview, "Button_TextInput_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "输入框")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:TextInput_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 300, 50, 18)
    ssr.GUI:TextInput_setString(widget, "我是测试输入内容")

    ssr.schedule(widget, function()
        ssr.GUI:TextInput_setString(widget, "我是测试输入内容" .. ssr.random(0, 100))
        ssr.print(ssr.GUI:TextInput_getString(widget))
    end, 0.5)

    -- ssr.GUI:TextInput_addOnEvent(widget, function(sender, eventType)
    --     if eventType == 0 then 
    --         ssr.print("输入开始========")
    --     elseif eventType == 1 then 
    --         ssr.print("输入结束========")
    --     elseif eventType == 2 then
    --         ssr.print("输入改变========")
    --     end
    -- end)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- TextAtlas_Create
local button = ssr.GUI:Button_Create(listview, "Button_TextAtlas_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "艺术字")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:TextAtlas_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "", "res/public/word_tywz_01.png", 18, 28, "0")
    ssr.GUI:TextAtlas_setString(widget, "321")

    ssr.schedule(widget, function()
        ssr.GUI:TextAtlas_setString(widget, ssr.random(0, 999999))
        ssr.print(ssr.GUI:TextAtlas_getString(widget))
    end, 0.5)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- Slider_Create
local button = ssr.GUI:Button_Create(listview, "Button_Slider_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "滑动条")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:Slider_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/bg_szjm_01.png", "res/public/bg_szjm_02.png", "res/private/setting_basic/icon_xdtzy_17.png")
    ssr.GUI:Slider_setPercent(widget, 20)

    ssr.GUI:Slider_addOnEvent(widget, function(sender, eventType)
        ssr.print("响应类型", eventType)   
        ssr.print(ssr.GUI:Slider_getPercent(widget))   
    end)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- CheckBox_Create
local button = ssr.GUI:Button_Create(listview, "Button_CheckBox_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "复选框")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:CheckBox_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/1900000654.png", "res/public/1900000655.png")

    ssr.GUI:CheckBox_addOnEvent(widget, function(sender, eventType)
        ssr.print("响应类型", eventType)   
        ssr.print(ssr.GUI:CheckBox_isSelected(widget))   
    end)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- ProgressTimer_Create
local button = ssr.GUI:Button_Create(listview, "Button_ProgressTimer_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "圆形进度条")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:ProgressTimer_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/lock_2.png")
    ssr.GUI:ProgressTimer_ProgressFromTo(widget, 2, 0, 100, function()
        ssr.print("完成了")
    end)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- Effect_Create
local button = ssr.GUI:Button_Create(listview, "Button_Effect_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "特效")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local widget = ssr.GUI:Effect_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 0, 1, 0, 0, 0, 1)

    ssr.GUI:Effect_addOnCompleteEvent(widget, function()
        ssr.print("播完了")   
    end)

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 5)
end)

-- RichText_Create
local button = ssr.GUI:Button_Create(listview, "Button_RichText_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "富文本")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local text = 
    {
        "您背包中的<font color='#00cb52'>随机卷/随机石</font>已耗尽",
        "您背包中的<font color='#ff0000'>随机卷/随机石</font>已耗尽",
        "您背包中的<font color='#00cb52' size='30'>随机卷/随机石</font>已耗尽",
        "您背包中的<u><font color='#00cb52'>随机卷/随机石</font></u>已耗尽",
    }
    local str = text[ssr.random(1, #text)]
    local widget = ssr.GUI:RichText_Create(wnd, "widget"..ssr.random(0, 9999)..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, str, 500)
    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
    end, 2)
end)

-- PageView_Create
local button = ssr.GUI:Button_Create(listview, "Button_PageView_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "翻页容器")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local textPage = ssr.GUI:Text_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, 100, 30, ssr.Color3B.ORANGE, "")
    ssr.GUI:Text_setString(textPage, "1/3")

    local widget = ssr.GUI:PageView_Create(wnd, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 300, 200, 1)
    ssr.GUI:setAnchorPoint(widget, cc.p(0.5, 0.5))
    ssr.GUI:PageView_setBackGroundColorType(widget, 1)
    ssr.GUI:PageView_setBackGroundColorOpacity(widget, ssr.random(50, 255))
    ssr.GUI:PageView_setBackGroundColor(widget, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))
    ssr.GUI:PageView_addOnEvent(widget, function(sender, eventType)
        local itemCount = ssr.GUI:PageView_getItemCount(widget)
        local currentIndex = ssr.GUI:PageView_getCurrentPageIndex(widget)
        print("eventType", eventType)
        ssr.GUI:Text_setString(textPage, (currentIndex+1).. "/" .. itemCount)
    end)

    local page1 = ssr.GUI:Layout_Create(widget, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 300, 200)
    ssr.GUI:Layout_setBackGroundColorType(page1, 1)
    ssr.GUI:Layout_setBackGroundColorOpacity(page1, ssr.random(50, 255))
    ssr.GUI:Layout_setBackGroundColor(page1, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))

    local page2 = ssr.GUI:Layout_Create(widget, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 300, 200)
    ssr.GUI:Layout_setBackGroundColorType(page2, 1)
    ssr.GUI:Layout_setBackGroundColorOpacity(page2, ssr.random(50, 255))
    ssr.GUI:Layout_setBackGroundColor(page2, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))

    local page3 = ssr.GUI:Layout_Create(widget, "widget"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 300, 200)
    ssr.GUI:Layout_setBackGroundColorType(page3, 1)
    ssr.GUI:Layout_setBackGroundColorOpacity(page3, ssr.random(50, 255))
    ssr.GUI:Layout_setBackGroundColor(page3, ssr.c3b(ssr.random(0, 255), ssr.random(0, 255), ssr.random(0, 255)))

    ssr.performWithDelay(widget, function()
        widget:removeFromParent()
        textPage:removeFromParent()
    end, 10)
end)

-- ItemShow_Create
local button = ssr.GUI:Button_Create(listview, "Button_ItemShow_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "道具图标")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local data = {}
    data.index = 10001
    data.look  = true
    data.bgVisible = true
    data.count = 10
    data.color = 225
    data.noMouseTips = true
    local item = ssr.GUI:ItemShow_Create(wnd, "ItemShow_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, data)
    ssr.GUI:ItemShow_AddReplaceClickEvent(item, function()
        ssr.print("替代原有点击触发!")
    end)
    ssr.GUI:ItemShow_AddPressEvent(item, function()
        ssr.print("长按触发!")
    end)
    ssr.GUI:ItemShow_AddDoubleEvent(item, function()
       ssr.print("双击触发!") 
    end)
    ssr.performWithDelay(item, function()
        item:removeFromParent()
    end, 5)
    ssr.GUI:ItemShow_setIconGrey(item, true)
end)

-- ItemBox_Create
local button = ssr.GUI:Button_Create(listview, "Button_ItemBox_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "物品放入框")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local itemBox = ssr.GUI:ItemBox_Create(wnd, "ItemBox_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/btn_npcsm_01.png", 100, {31, 0})
    ssr.performWithDelay(itemBox, function()
        itemBox:removeFromParent()
    end, 5)
end)

-- 跳转
-- local index = ssr.GUI:ListView_GetItemIndex(listview, button)
-- ssr.GUI:ListView_JumpToItem(listview, index)

-- Frames_Create
local button = ssr.GUI:Button_Create(listview, "Button_Frames_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "序列帧")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local ext = {
        count = 10,
        speed = 100,
        loop  =  1,
        finishhide = 1
    }
    local frames = ssr.GUI:Frames_Create(wnd, "Frames_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "public/word_fubentg_", ".png", nil, ext )
end)

-- TIMETIPS
local button = ssr.GUI:Button_Create(listview, "Button_TIMETIPS_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "倒计时提示")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local function endLinkCB()
        ssr.print("-------- time end")
    end
    local timeTip = ssr.GUI:TIMETIPS_Create(wnd, "TIMETIPS_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 18, {r=255,g=0,b=0}, 5, endLinkCB )
    ssr.PerformWithDelayGlobal(function()
        timeTip:removeFromParent()
    end, 5)
end)

-- CircleBar
local button = ssr.GUI:Button_Create(listview, "Button_CircleBar_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "圆形进度条（原标签）")
ssr.GUI:Button_setTitleFontSize(button, 18)
ssr.GUI:Button_setMaxLineWidth(button, 100)
ssr.GUI:Button_titleEnableOutline(button, {r=255,g=0,b=0}, 1)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local circleBar = ssr.GUI:CircleBar_Create(wnd, "CircleBar_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/private/sui/bg_xbzy_02.png", "res/private/sui/bg_xbzy_03.png", 0, 100, 3)
    ssr.GUI:CircleBar_AddEndLinkCB(circleBar, function()
        if circleBar then
            circleBar:removeFromParent()
        end
    end)
end)

-- PercentImg
local button = ssr.GUI:Button_Create(listview, "Button_PercentImg_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "百分比图片")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local percentImg = ssr.GUI:PercentImg_Create(wnd, "PercentImg_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, "res/public/bg_szjm_03_2.png", 0, 50, 100)
    ssr.performWithDelay(percentImg, function()
        percentImg:removeFromParent()
    end, 5)
end)

-- UIModel
local button = ssr.GUI:Button_Create(listview, "Button_UIModel_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "人物模型")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local uiModel  = ssr.GUI:UIModel_Create(wnd, "PercentImg_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 0, {}, 1)
    ssr.performWithDelay(uiModel, function()
        uiModel:removeFromParent()
    end, 3)
end)

-- EquipShow
local button = ssr.GUI:Button_Create(listview, "Button_EquipShow_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "装备图标")
ssr.GUI:Button_setTitleFontSize(button, 20)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local equipShow  = ssr.GUI:EquipShow_Create(wnd, "EquipShow_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 1, true, true, true)
    ssr.performWithDelay(equipShow, function()
        equipShow:removeFromParent()
    end, 3)
end)

-- DBItemShow
local button = ssr.GUI:Button_Create(listview, "Button_DBItemShow_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "数据库道具图标")
ssr.GUI:Button_setTitleFontSize(button, 18)
ssr.GUI:Button_setMaxLineWidth(button, 100)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local dbItemShow  = ssr.GUI:DBItemShow_Create(wnd, "DBItemShow_"..ssr.random(0, 9999), wndSize.width/2, wndSize.height/2, 140873, true, true, true)
    ssr.GUI:DBItemShow_setCount( dbItemShow, 18 )
    ssr.performWithDelay(dbItemShow, function()
        dbItemShow:removeFromParent()
    end, 3)
end)

-- QuickCell
local button = ssr.GUI:Button_Create(listview, "Button_QuickCell_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "快捷控件")
ssr.GUI:Button_setTitleFontSize(button, 18)
ssr.GUI:Button_setMaxLineWidth(button, 100)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    local listView = ssr.GUI:ListView_Create(wnd, "LISTVIEW", 200, 80, 500, 400, 1)
    ssr.GUI:ListView_setBackGroundColor(listView, {r=255,g=255,b=255})
    for i = 1, 20 do
        ssr.GUI:QuickCell_Create(listView, "QuickCell_Create"..i, 0, 0, 500, 40,  function(quickParent)
            local item = ssr.GUI:Layout_Create(quickParent, "item", 0, 0, 500, 40)
            local itemDesc = ssr.GUI:Text_Create(item, "item_name", 120, 10, 20, {r=200, g=0, b=0}, "name.."..i)
            return item
        end)
    end
end)

-- ScrollView 
local button = ssr.GUI:Button_Create(listview, "Button_ScrollView_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "滚动容器")
ssr.GUI:Button_setTitleFontSize(button, 18)
ssr.GUI:Button_setMaxLineWidth(button, 100)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    if ssr.GUI:getChildByID(wnd, "SCROLLVIEW") then
        ssr.GUI:removeChildByID(wnd, "SCROLLVIEW")
    end

    local scrollView = ssr.GUI:ScrollView_Create(wnd, "SCROLLVIEW", wndSize.width/2, wndSize.height/2, 400, 400, 1)
    ssr.GUI:setAnchorPoint(scrollView, 0.5, 0.5)
    ssr.GUI:ScrollView_setInnerContainerSize(scrollView, 400, 1000)
    ssr.GUI:ScrollView_setBounceEnabled(scrollView, true)
    ssr.GUI:ScrollView_setClippingEnabled(scrollView, true)
    ssr.GUI:ScrollView_setBackGroundColor(scrollView, {r=200, g=200, b=200})

    local text1 = ssr.GUI:Text_Create(scrollView, "Text_1", 200, 200, 18, {r=255, g=255, b=255}, "111111111111111111111111111")
    ssr.GUI:setAnchorPoint(text1, 0.5, 0.5)

    local text2 = ssr.GUI:Text_Create(scrollView, "Text_2", 200, 700, 18, {r=255, g=0, b=0}, "2222222222222222222222222222")
    ssr.GUI:setAnchorPoint(text2, 0.5, 0.5)

end)

-- TableView （复用cell 初始化时只创建可视区域的子cell)
function ssrGlobal_GUITableViewCell_Create( parent, idx, ID )
    if ID == "TABLEVIEW" then
        local panel = ssr.GUI:Layout_Create(parent, string.format("layout_%s", idx), 0, 0, 600, 40)
        local text = ssr.GUI:Text_Create(panel, "TEXT", 0, 20, 18, {r=0,g=255,b=0}, "IDX----------------"..idx)
        ssr.GUI:setAnchorPoint(text, 0, 0.5)
    end
end

local button = ssr.GUI:Button_Create(listview, "Button_TableView_Create", 0, 0, "res/public/1900000660.png")
ssr.GUI:Button_setTitleText(button, "列表视图(优)")
ssr.GUI:Button_setTitleFontSize(button, 18)
ssr.GUI:Button_setMaxLineWidth(button, 100)
ssr.GUI:setTouchEnabled(button, true)
ssr.GUI:addOnClick(button, function()
    if ssr.GUI:getChildByID(wnd, "TABLEVIEW") then
        ssr.GUI:removeChildByID(wnd, "TABLEVIEW")
    end
    local tableView = ssr.GUI:TableView_Create(wnd, "TABLEVIEW", 200, 100, 600, 400, 1, 600, 40, 200)
    ssr.GUI:TableView_setBackGroundColor(tableView, {r=255,g=255,b=255})
    ssr.GUI:TableView_setDirection(tableView, 2)

    local function touchCellFunc(tv, cell)
        print(cell)
        print(tv)
        local idx = ssr.GUI:TableViewCell_getIdx(cell)
        local panel = ssr.GUI:getChildByID(cell, string.format("layout_%s", idx))
        ssr.GUI:Layout_setBackGroundColor(panel, {r=0, g=200, b=100})
    end
    -- 添加cell点击事件
    ssr.GUI:TableView_addOnTouchedCellEvent( tableView, touchCellFunc )
end)

--[[
	-- 新窗口示例！！
	local testWin = ssr.GUI:NewWin_Create("TT", 200, 200, 400, 400, false, true, true, false)

	local bg = ssr.GUI:Image_Create(testWin, "BG", 200, 200, "res/public/bg_npc_11.jpg")
	ssr.GUI:setAnchorPoint(bg, 0.5, 0.5)
	ssr.GUI:setContentSize(bg, 400, 400)
	ssr.GUI:NewWin_SetDrag(testWin, bg)
	ssr.GUI:NewWin_SetTouchZPanel(testWin, bg)
	ssr.GUI:NewWin_SetESCClose(testWin, true)
	
	local closeBtn = ssr.GUI:Button_Create(testWin, "CLOSEBTN", 400, 400, "res/public/1900000510.png")
	ssr.GUI:setAnchorPoint(closeBtn, 1, 1)
	ssr.GUI:addOnClick(closeBtn, function()
	    -- 关闭窗口方式1
	    ssr.GUI:NewWin_Close(testWin)
	    -- 关闭窗口方式2
	    -- ssr.GUI:NewWin_CloseByID("TT")
	end)
	
	local titleText = ssr.GUI:Text_Create(bg, "TITLE", 200, 350, 18, "#00FFFF", "测试界面标题")
	ssr.GUI:setAnchorPoint(titleText, 0.5, 0.5)
	ssr.GUI:setVisible(titleText, true)
	
	local btn = ssr.GUI:GetWindow(testWin, "CLOSEBTN")
	local posX = ssr.GUI:getPositionX(btn)
	ssr.GUI:setPositionX(btn, posX + 50)
	 
	local title = ssr.GUI:GetWindow(testWin,"BG/TITLE")
	if title then
	    ssr.GUI:runAction(title, cc.FadeOut:create(0.5))
	end
	
	ssr.GUI:NewWin_RegisterGameEvent(testWin, "OnGUINewWinClose", function()
	   ssr.print("测试界面关闭监听触发!!!!!!!!") 
	end)
	
	ssr.GUI:NewWin_RegisterGameEvent(testWin, "onPlayerLevelChange", function(data)
	    ssr.print("角色等级改变!!!!!!!!") 
	    ssr.PrintTable(data)
	    ssr.print("____________________________________________")
	end)
]]
```
# UI组件 ( 已废弃 )



 # 组件常用方法
 * 常用方法 基础
    + `setPosition(cc.p(float, float))`                             -- 设置 坐标
    + `setAnchorPoint(cc.p(float, float))`                          -- 设置 锚点
    + `setRotation(float)`                                          -- 设置旋转角度
    + `setVisible(boolean)`                                         -- 设置可见性
    + `setOpacity(float)`                                           -- 透明度 0-255
    + `setTouchEnabled(boolean)`                                    -- 设置可点性
    + `setScale(float)`												-- 设置缩放大小
    + `runAction(action)`											-- run一个action
    + `stopAllActions()`                                            -- 停止所有action
    + `stopActionByTag(tag)`                                        -- 停止单个action
    + `setLocalZOrder(int)`											-- 设置其在父节点的渲染层级 值越大显示越靠前
    + `getPosition()`												-- 获取坐标 {x = x, y = y}
    + `getPositionX()` 												-- 获取X轴坐标
    + `getPositionY()` 												-- 获取Y轴坐标
    + `getContentSize()`											-- 获取尺寸大小 {width = width, height = height}
    + `getChildByName(string)`										-- 通过子节点的名称获取该组件的某个子节点
    + `getChildren()`												-- 获取所有子节点	
    + `removeFromParent()`											-- 将其本身从父节点上移除	
    + `removeAllChildren()`											-- 移除其所有的子节点

 * 常用方法 功能性
    + `addClickEventListener(function(sender) end)`                 -- 设置点击事件
    ```
      local button = ssr.Button:create()
      button:setAnchorPoint(cc.p(0.5, 0.5))
      button:setPosition(cc.p(300, 300))
      button:loadTextureNormal("res/public/1900000652.png")
      button:addClickEventListener(function()
        ssr.print("点击了按钮")
      end)
    ```

    + `addTouchEventListener(function(sender, eventType) end)`      -- 设置 按下 移动 抬起事件
    ```
      local button = ssr.Button:create()
      button:setAnchorPoint(cc.p(0.5, 0.5))
      button:setPosition(cc.p(300, 300))
      button:loadTextureNormal("res/public/1900000652.png")
      button:addTouchEventListener(function(sender, eventType)
        if eventType == 0 then
          ssr.print("按下了按钮")
        elseif eventType == 1 then
          ssr.print("发生改变")
        elseif eventType == 2 or eventType == 3 then
          ssr.print("离开了按钮")
        elnd
      end)
    ```
    + `getTouchBeganPosition()`				-- 获取到控件的触摸起始点
	+ `getTouchMovePosition()`				-- 获取到控件的触摸移动点
	+ `getTouchEndPosition()`				-- 获取到控件的触摸终点/停止触摸位置
	结合触摸事件 示例如下:
	```
		local layoutBlack = ssr.Layout:create()
		local visibleSize = ssr.getVisibleSize()
		layoutBlack:setContentSize(cc.size(visibleSize.width/2, visibleSize.height/2))
		layoutBlack:setTouchEnabled(true)
		layoutBlack:setBackGroundColor(cc.c3b(0, 0, 0))
		layoutBlack:setBackGroundColorType(1)
		layoutBlack:setBackGroundColorOpacity(100)
		layoutBlack:setAnchorPoint(cc.p(0.5, 0.5))
		layoutBlack:setPosition(cc.p(visibleSize.width/2, - visibleSize.height/2))
		self:addChild(layoutBlack)
		layoutBlack:addTouchEventListener(function (sender,eventType)
		    if eventType == 0 then
		         local touchBeganPos = sender:getTouchBeganPosition()
		         ssr.PrintTable(touchBeganPos)
		
		    elseif eventType == 1 then
		         local touchMovePos = sender:getTouchMovePosition()
		         ssr.PrintTable(touchMovePos)
		            
		    elseif eventType == 2 or eventType == 3 then 
		         local touchBeganPos = sender:getTouchBeganPosition()
		         local touchEndPos = sender:getTouchEndPosition()
		         ssr.PrintTable(touchEndPos)
		
		         local layoutWorldPos = sender:getWorldPosition()
		         local layoutSize   = sender:getContentSize()
		         local anchorPoint  = sender:getAnchorPoint()
		         local posXInLayout = touchEndPos.x - layoutWorldPos.x + (layoutSize.width)*(anchorPoint.x) 
		         local posYInLayout = touchEndPos.y - layoutWorldPos.y + (layoutSize.height)*(anchorPoint.y)
		         ssr.print("触摸结束点在该容器位置 X坐标:".. posXInLayout.."  Y坐标：".. posYInLayout)
		     end
		end)
	```

  #### Action 动作
    + action用处非常广泛，可以用来做动画，做托管类定时器等
    ```
      local moveAction    = cc.MoveBy:create(1, cc.p(50, 50))
      local fadeOutAction = cc.FadeOut:create(1)
      local fadeInAction  = cc.FadeIn:create(1)
      local imageView = ssr.ImageView:create()
      imageView:loadTexture("res/public/1900000657.png")
      imageView:setAnchorPoint(cc.p(0.5, 0.5))
      imageView:setPosition(cc.p(300, 300))
      imageView:runAction(cc.Sequence:create(moveAction, fadeOutAction, fadeInAction))
    ```

  #### ImageView 图片
    + `loadTexture(filepath, [resType])`                            -- 设置图片  filepath: 图片路径 注意大小写和反斜杠 正确格式例子 res/public/test.png,  resType:资源类型，可不传， 0.本地散图 1.整图
    + `setScale9Enabled(boolean)`									-- 设置是否九宫格

  #### Button  按钮
    + `loadTextureNormal(filepath, [resType])`                      -- 设置正常图片 filepath: 图片路径 注意大小写和反斜杠 正确格式例子 res/public/test.png,  resType:资源类型，可不传， 0.本地散图 1.整图
    + `loadTexturePressed(filepath, [resType])`                     -- 设置按下图片 filepath: 图片路径 注意大小写和反斜杠 正确格式例子 res/public/test.png,  resType:资源类型，可不传， 0.本地散图 1.整图
    + `loadTextureDisabled(filepath, [resType])`                    -- 设置禁用图片 filepath: 图片路径 注意大小写和反斜杠 正确格式例子 res/public/test.png,  resType:资源类型，可不传， 0.本地散图 1.整图 
    + `setTitleText(string)`                                        -- 设置按钮文本
    + `setTitleColor(Color3B)`                                      -- 设置按钮文本颜色 颜色方式 cc.c3b(255,255,255)
    + `setTitleFontSize(int)`                                       -- 设置按钮字体大小
    + `setBright(boolean)`											-- 设置显示状态 默认值为true 正常状态 false 显示禁用状态
    ```
      local button = ssr.Button:create()
      button:setAnchorPoint(cc.p(0.5, 0.5))
      button:setPosition(cc.p(300, 300))
      button:loadTextureNormal("res/public/1900000652.png")
      button:loadTexturePressed("res/public/1900000652_1.png")
      button:loadTextureDisabled("res/public/1900000652_1.png")
      button:setTitleText("我是按钮")
      button:setTitleColor(cc.c3b(255,0,0))
      button:setTitleFontSize(25)
    ```

  ####Text 文本
 	+ `setString(string)` 					-- 设置文本内容
 	+ `setTextColor(Color3B)` 				-- 设置文本颜色 颜色格式 cc.c3b(255,0,0)
 	+ `setFontSize(int)`					-- 设置文本字体大小
 	+ `setFontName(string)`					-- 设置文本字体 string: 若使用系统字体采用字体名称 采用自定TTF字体则设置TTF文件路径
 	+ `enableOutline(Color3B, int size)`	-- 设置文字描边 参数 Color3B: 描边颜色 size: 描边大小
	```
		local text = ssr.Text:create()
		text:setAnchorPoint(cc.p(0, 0.5))
		text:setString("文本内容")
		text:setTextColor(cc.c3b(255, 0, 0))
		text:setFontSize(16)
		text:setFontName(ssr.define.PATH_FONT)		-- ssr.define.PATH_FONT 通用字体
		text:enableOutline(cc.c3b(0, 0, 0), 1)
		text:setPosition(cc.p(200, 200))
		text:getVirtualRenderer():enableUnderline()  -- 加下划线!
	```

  #### Layout 基础容器
	+ `setContentSize(cc.size(width, height))`				-- 设置容器大小 cc.size(宽, 高)
	+ `setBackGroundColor(Color3B)`							-- 设置背景颜色 cc.c3b(0, 0, 0)
	+ `setBackGroundColorType(type)`						-- 设置背景填充色类型 type: 0无 1纯色 2渐变
	+ `setBackGroundColorOpacity(opacity)`					-- 设置背景色不透明度 opacity: 0 ~ 255
	```
		local layout = ssr.Layout:create()
    	layout:setBackGroundColorType(1)
    	layout:setBackGroundColorOpacity(255)
    	layout:setBackGroundColor(cc.c3b(0, 255, 0))
    	layout:setAnchorPoint(cc.p(0, 1))
    	layout:setContentSize(cc.size(200, 200))
    	layout:setPosition(cc.p(200, 0))
	```
	
  #### LoadingBar 进度条
	+ `loadTexture(filepath, [resType])`				-- 设置进度条样式图片 具体格式参照上文ImageView图片设置
	+ `setDirection(direction)`							-- 设置进度条方向 direction: 0从左到右 1从右到左
	+ `setPercent(float)`								-- 设置进度条加载的进度值 百分比(%): 0 ~ 100 
	```
	local loading = ssr.LoadingBar:create()
    loading:loadTexture("res/public/bg_szjm_03_2.png")
    loading:setDirection(1)
    loading:setPercent(100)
    loading:setAnchorPoint(cc.p(0.5, 1))
    loading:setPosition(cc.p(400, -40))
	```
	
  #### TextInput 输入框
	+ `setFontColor(Color3B)`						-- 设置输入文本颜色 cc.c3b(255, 0, 0)
	+ `setFont(string, int)`						-- 设置输入文本字体格式 参数1: 通用TTF文件路径 参数2: 字体大小
	+ `setFontSize(int)`							-- 设置输入文本字体大小
	+ `setPlaceholderFont(string, int)`				-- 设置占位文本字体格式 参数1: 通用TTF文件路径 参数2: 字体大小
	+ `setPlaceholderFontColor(Color3B)`			-- 设置占位文本颜色 cc.c3b(0, 0, 255)
	+ `setPlaceholderFontSize(int)`					-- 设置占位文本字体大小
	+ `setPlaceHolder(string)`						-- 设置占位文本内容
	+ `setMaxLength(int)`							-- 设置输入文本最大长度
	+ `setText(string)`								-- 设置输入文本内容
	+ `setTextHorizontalAlignment(type)`			-- 设置输入文本水平对齐方式 type: 0左对齐 1居中 2右对齐
	+ `setInputFlag(inputFlag)`						-- 设置格式化显示输入文本 可不设置! inputFlag: 加密输入内容可设置为 0
	+ `setInputMode(inputMode)`						-- 设置允许输入的文本类型模式 inputMode: 默认为0 可输入任何文本, 1.允许输入电子邮件地址 , 2.允许输入数字 
	```
	local TextInput = ssr.TextInput:create(cc.size(200, 40), ssr.define.PATH_RES_ALPHA) -- cc.size() 设置输入框宽高
    TextInput:setFontColor(cc.c3b(255, 0, 0))
    TextInput:setFont(ssr.define.PATH_FONT, 14)
    TextInput:setPlaceHolder("请输入....")
    TextInput:setPlaceholderFontColor(cc.c3b(0, 0, 255))
    TextInput:setPlaceholderFontSize(16)
    TextInput:setTextHorizontalAlignment(0)
    TextInput:setMaxLength(10)
	TextInput:setInputFlag(0)
    TextInput:setInputMode(2)
    TextInput:setPosition(cc.p(600, -20))
	```

  #### TextAtlas 艺术数字
	+ `setProperty(stringValue, charMapFile, itemWidth, itemHeight, string startCharMap)` 
	-- 设置艺术字体属性
	-- stringValue: 文本内容, charMapFile: 图片路径, itemWidth: 字符宽, itemHeight: 字符高, startCharMap: 初始字符
	+ `setString(string)`					-- 设置文本内容
	```
	local TextAtlas = ssr.TextAtlas:create()
    TextAtlas:setProperty( "", "res/public/word_tywz_01.png", 18, 28, "0" )
    TextAtlas:setString(200)
	TextAtlas:setPosition(cc.p(400, -20))
	```

  #### Slider 滑动条
	+ `loadBarTexture(filepath, [resType])`			-- 设置滑动条底图样式 filepath: 图片路径 resType: 资源类型，可不传， 0.本地散图 1.整图
	+ `loadProgressBarTexture(filepath, [resType])`	-- 设置滑动条内部样式 参数同上
	+ `loadSlidBallTextureNormal(filepath, [resType])`	-- 设置滑动条滑动标识样式 参数同上
	+ `setPercent(int)`									-- 设置滑动到的百分比值 0 ~ 100
	```
	local Slider = ssr.Slider:create()
	Slider:loadBarTexture("res/public/bg_szjm_01.png",0)
	Slider:loadProgressBarTexture("res/public/bg_szjm_02.png",0)
	Slider:loadSlidBallTextureNormal("res/private/setting_basic/icon_xdtzy_17.png",0)
	Slider:setPercent(50)
	Slider:setAnchorPoint(0, 0.5)
	Slider:setPosition(30, 15)
	```
	
  #### ListView 列表容器
	+ `setDirection(direction)`				-- 设置列表容器滚动方向 direction: 1.垂直方向 2.水平方向 
	+ `setGravity(gravity)`					-- 设置子控件对齐方式 gravity: 0.左对齐 1.右对齐 2.水平居中 3.顶对齐 4.底对齐 5.垂直居中
	+ `setItemsMargin(float)`				-- 设置子控件间隔
	+ `setBounceEnabled(boolean)`			-- 设置是否有回弹效果
	+ `setClippingEnabled(boolean)`			-- 设置是否裁剪内容
	+ `pushBackCustomItem(widget)`			-- 添加子控件到列表容器中  widget: 子控件
	+ `insertCustomItem(widget, index)`		-- 插入子控件到列表容器中指定index位置 
	+ `removeAllItems()`					-- 移除该列表容器中所有子控件
	```
	local ListView = ssr.ListView:create()
    ListView:setContentSize(cc.size(200, 600))
    ListView:setClippingEnabled(true)
    ListView:setClippingType(0)
    ListView:setDirection(1)
    ListView:setGravity(0)
    ListView:setItemsMargin(10)
    ListView:setBounceEnabled(true)
    ListView:setBackGroundColorType(1)
    ListView:setBackGroundColorOpacity(155)
    ListView:setBackGroundColor(cc.Color3B.RED)
    ListView:setAnchorPoint(cc.p(0, 1))
    ListView:setPosition(cc.p(400, 0))
    local showText = ssr.Text:create()
    showText:setString("子控件是我")
    showText:setFontSize(18)
    showText:setTextColor(cc.c3b(0,255,0))
    ListView:pushBackCustomItem(showText)
	```

  #### CheckBox 复选框
	+ `loadTextureBackGround(filepath, [resType])` -- 设置复选框正常状态下的背景样式 filepath: 图片路径 resType: 资源类型，可不传， 0.本地散图 1.整图
	+ `loadTextureFrontCross(filepath, [resType])`	-- 设置复选框正常状态下的标识样式 参数同上
	+ `loadTextureFrontCrossDisabled(filepath, [resType])`	-- 设置复选框禁用状态下的标识样式 参数同上
	+ `setSelected(boolean)`			-- 设置复选框是否选中 boolean 
	+ `isSelected()`					-- 获取复选框是否选中
	```
	local checkBox_show = ssr.CheckBox:create()
    checkBox_show:loadTextureBackGround("res/public/1900000550.png",0)
    checkBox_show:loadTextureFrontCross("res/public/1900000551.png",0)
    checkBox_show:loadTextureFrontCrossDisabled("res/public/1900000550.png",0)
    checkBox_show:setSelected(true)
    checkBox_show:setPosition(300, 200)
    checkBox_show:addEventListener(function (sender)
        local isSelected = sender:isSelected()
        local status = isSelected and 1 or 0
        print("选中状态： --> "..status)
    end)
    ssr.AttachOrUnAttachSUI({index = 103, subid = 2, content = checkBox_show})
	```
# 资源工具

* Cocostudio
[CocosForWin-v3.10.exe.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=87d757922dbd3e23a5bbe15b2ff9f072 "[CocosForWin-v3.10.exe.zip")

* 996工具集
[996M2资源集成工具.exe](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/55be968afd12d9e8941415108c1398ba "[996M2资源集成工具.exe")

* 客户端表
[game_config.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/5d7eac2cd82754a4ef48ed9b11ed6c94 "[game_config.zip")
# 源码示例

* buff界面
[buff界面.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/c3dd49c5bf615bd0cb0dbeedda34d02c "[buff界面.zip")

* 转盘示例
[转盘示例.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/41af78ee3ab3445bc9aa570ced363256 "[转盘示例.zip")
# 视频教程

* Cocostudio使用教程
[64位CocosStudio相关教程.7z](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/6d41c9b9eea86695f93c756d919ae9ed "[64位CocosStudio相关教程.7z")

* ssrGUI使用教程
[ssrGUI使用教程.7z](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/2245768a38d49fdb4b85cdb0c264f887 "[ssrGUI使用教程.7z")
# 客户端资源

|资源|说明|更新时间|
|:----|-----|-----|
|[996M2_release.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=38f3dfda9c2b56a3faa9c1b389a8e650 "[996M2_release.zip")|release客户端|2023-11-06
|[996M2_debug.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9e0304d81fa76259734dc57a21e03777 "[996M2_debug.zip")|debug客户端(开发建议使用)|2023-11-06|
|[GUILayout.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=4f2a9bfb0cb32fa8df9e06302173d507 "[GUILayout.zip")|官方界面(v3.3.3版本)|2023-04-19|
|[GUILayout_3.40.1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=252028e6fe9f3adcafad9f8232e623e4 "[GUILayout_3.40.1.zip")|官方界面(v3.40.1版本)|2023-10-18|
|[GUILayout_3.40.2.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=615111eedbe7ea5a70cfd44c187d5c8c "[GUILayout_3.40.2.zip")|官方界面(v3.40.2版本)|2024-01-04|
|[GUILayout_3.40.3.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=162ea72eac99b1065e934bd92fdbe374 "[GUILayout_3.40.3.zip")|官方界面(v3.40.3版本)|2024-01-04|
|[GUILayout_3.40.4.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=a560762a6062e7afdc78e3d221b6d3e5 "[GUILayout_3.40.4.zip")|官方界面(v3.40.4版本)|2024-04-18|
|[GUILayout_3.40.5.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=88c024af149338f9e411660792957c18 "[GUILayout_3.40.5.zip")|官方界面(v3.40.5版本)|2024-04-18|
|[GUIExport_3.40.5改动.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=efb4a326459cd0c377b701189858434d "[GUIExport_3.40.5改动.zip")|v3.40.5版本官方界面UI文件(有改动文件)|2023-12-13|
|[GUILayout_3.40.6.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7ce38d4a7f678fdcc591e08a1b52575f "[GUILayout_3.40.6.zip")|官方界面(v3.40.6版本)|2024-04-18|
|[GUIExport_3.40.6改动.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=09ba1f66fee195fec32158dd98b4611b "[GUIExport_3.40.6改动.zip")|v3.40.6版本官方界面UI文件(有改动文件)|2024-01-29|
|[GUILayout_3.40.7.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=7d9f75f5dd682b00536747efd83be0cc "[GUILayout_3.40.7.zip")|官方界面(v3.40.7版本)|2024-04-18|
|[GUILayout_3.40.8.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=595236f789b3e90c933bc3adbda75797 "[GUILayout_3.40.8.zip")|官方界面(v3.40.8版本)|2024-06-04|
|[dev-第一版UI.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/199c6b898dd2038f40bc2cf749f38152 "[dev-第一版UI.zip")|996第一版UI资源|2023-08-23|
|[uiminimap.7z](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=aecd6b2ef2dae651a98a81dd16865210 "[uiminimap.7z")|996小地图文件|2023-08-23|
|[Map.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=5b560d8f1dfd57e69386fe474e4183e2 "[Map.zip")|996地图MAP文件|2023-08-23|
|[font4.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0b819d64aeaf301f5b5d741e21c92571 "[font4.zip")|PC宋体文件(dev/fonts/font4.ttf)|2023-08-23|
|[dev-第二版UI.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=9b40c63e9c9445e1e56b9f19375f5f01 "[dev-第二版UI.zip")|996第二版UI资源 及 GUIExport  [- 3.40.4版本更换新版UI前 ]|2023-11-03|
|[GUIExport_3.40.1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=357f0a1438fa85229925217fbc0f537e "[GUIExport_3.40.1.zip")|官方界面UI文件(v3.40.1版本)|2024-02-01|
|[GUIExport_3.40.2.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=5d27ab3b67ec9ef9cd220f520b0b5618 "[GUIExport_3.40.2.zip")|官方界面UI文件(v3.40.2版本)|2024-02-01|
|[GUIExport_3.40.3.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=d5547b2e1ff15e889ff91d577b8c4aab "[GUIExport_3.40.3.zip")|官方界面UI文件(v3.40.3版本)|2024-02-01|
|[GUIExport_3.40.4.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=922514a50e7692adc77905d8231cc69c "[GUIExport_3.40.4.zip")|官方界面UI文件(v3.40.4版本)|2024-02-01|
|[GUIExport_3.40.5.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=2059899623709953f5a4e931069ffb53 "[GUIExport_3.40.5.zip")|官方界面UI文件(v3.40.5版本)|2024-02-01|
|[GUIExport_3.40.6.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=3065b40fb3bf24b38e670572eb9f0250 "[GUIExport_3.40.6.zip")|官方界面UI文件(v3.40.6版本)|2024-02-01|
|[GUIExport_3.40.7.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=464933686cbac912ea3376c410a21f4d "[GUIExport_3.40.7.zip")|官方界面UI文件(v3.40.7版本)|2024-03-18|
|[GUIExport_3.40.8.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=fd1eb5824e6fa81cd92411dc49e7d40d "[GUIExport_3.40.8.zip")|官方界面UI文件(v3.40.8版本)|2024-05-24|
|[GUILayout_3.50.1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=ab67dae05a139eb12b6784c059e80029 "[GUILayout_3.50.1.zip")|官方界面UI(大服 v3.50.1版本)|2024-03-01|
|[GUIExport_3.50.1.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0213e5f0aac7692a9e64e7f1de73bf7b "[GUIExport_3.50.1.zip")|官方界面UI文件(大服v3.50.1版本)|2024-03-01|

|链接|说明|
|:----|-----|
|[Open996_Client_GUI](https://gitee.com/jiujiuyinqing/Open996_Client_GUI/tree/master/ "Open996_Client_GUI")|各版本客户端开源文件-仓库地址|
# 工具下载

|资源|说明|更新时间|
|:----|-----|-----|
|[996M2资源集成工具.exe](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile/sign/55be968afd12d9e8941415108c1398ba "[996M2资源集成工具.exe")|996集成工具|2023-08-23|
|[android-log-view-0.20-SNAPSHOT.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=78a8b7f9387adf2670f8608b9d59dd0d "[android-log-view-0.20-SNAPSHOT.zip")|安卓日志工具(需要先安装adb，可自行搜索电脑如何安装)|2023-08-23|
|[debug.zip](http://engine-doc.996m2.com/server/index.php?s=/api/attachment/visitFile&sign=0c252739c148b1900e0cf718d10c15ea "[debug.zip")|Windows日志工具(dbg)|2023-08-23|