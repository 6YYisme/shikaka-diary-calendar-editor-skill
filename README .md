# Food Sticker Generator

用于将 App 的 **日记页（Diary）** 和 **月历 / 月报页（Calendar）**
截图批量制作成「真实食物照片 + 手账贴纸」效果。

本项目最重要的原则：

> **不要重新设计截图。**
>
> **保持原截图完全一致，只在允许区域增加食物手账贴纸。**
>
> **食物要像普通人用手机随手拍的真实照片抠出来，而不是 AI
> 生成的摄影棚美食图。**

------------------------------------------------------------------------

## 1. 项目用途

本项目主要处理两类图片：

### Diary 日记页

在日记页面的空白区域加入较大的食物贴纸，可根据版面适量加入：

-   食物名称
-   kcal
-   白色贴纸描边
-   少量手绘箭头
-   爱心
-   小线条
-   简单手账装饰

整体效果参考 `diary_sticker_reference_*`。

### Calendar 月历 / 月报页

在日期格中加入较小的真实食物贴纸。

重点：

-   每个食物对应具体日期
-   贴纸不能破坏原来的日期格
-   不能遮挡日期、运动数据、热量等重要 UI
-   缩小后仍然可以辨认是什么食物
-   整体像用户每天随手记录后逐渐填满月历

整体效果参考 `calendar_sticker_reference_*`。

------------------------------------------------------------------------

## 2. 推荐目录

``` text
project/
├── README.md
├── FOOD_STICKER_STYLE_GUIDE.md
│
├── references/
│   ├── diary_sticker_reference_01.jpg
│   ├── diary_sticker_reference_02.jpg
│   │
│   ├── diary_food_realism_reference_01.jpg
│   ├── diary_food_realism_reference_02.jpg
│   ├── diary_food_realism_reference_03.jpg
│   ├── diary_food_realism_reference_04.jpg
│   │
│   ├── calendar_sticker_reference_01.png
│   ├── calendar_sticker_reference_02.jpg
│   ├── calendar_sticker_reference_03.jpg
│   │
│   ├── calendar_food_realism_reference_01.jpg
│   └── calendar_food_realism_reference_02.jpg
│
├── inputs/
│   ├── diary/
│   ├── calendar/
│   └── food_photos/
│
└── outputs/
    ├── diary/
    └── calendar/
```

`references/` 中放已经确认满意的效果图。

`inputs/` 中放每次需要处理的新截图或真实食物照片。

`outputs/` 用于保存最终生成结果。

------------------------------------------------------------------------

## 3. Reference 的分类

Reference 分成两种，作用完全不同。

### A. Sticker Reference

负责告诉模型：

> **最终版面应该长什么样。**

包括：

-   贴纸大小
-   贴纸位置
-   白边效果
-   页面留白
-   食物之间的错落关系
-   kcal / 食物名称的位置
-   手绘装饰程度
-   整体手账感

### B. Food Realism Reference

负责告诉模型：

> **食物本身应该长什么样。**

包括：

-   手机随手拍质感
-   普通生活光线
-   普通餐具
-   外卖包装
-   塑料杯
-   食堂餐盘
-   手拿食物
-   不完美构图
-   自然阴影
-   不同照片之间的色温差异

**不要把 Sticker Reference 和 Food Realism Reference 当成同一种参考。**

------------------------------------------------------------------------

# 4. Diary Reference

## 4.1 Diary Sticker Reference

使用：

``` text
diary_sticker_reference_01.jpg
diary_sticker_reference_02.jpg
```

这两张图负责规定 Diary 的最终视觉效果。

重点参考：

-   食物贴纸在页面中的大小
-   2～4 个较大食物贴纸的组合方式
-   食物之间自然错落
-   白色描边
-   kcal 标签
-   食物名称
-   少量手绘箭头 / 爱心 / 小线条
-   页面留白
-   贴纸与原 App UI 的融合方式

**不要复制 reference 中具体的食物。**

Reference 主要用于学习：

> 排版 / 比例 / 贴纸语言 / 视觉层级 / 装饰程度

------------------------------------------------------------------------

## 4.2 Diary Food Realism Reference

使用：

``` text
diary_food_realism_reference_01.jpg
diary_food_realism_reference_02.jpg
diary_food_realism_reference_03.jpg
diary_food_realism_reference_04.jpg
```

这些图片是 Diary 食物真实感的重要标准。

生成的食物应该让人感觉：

> 普通人吃饭时用手机随手拍了一张照片，然后把照片里的食物、餐具、包装或手部主体直接抠出来，做成了手账贴纸。

而不是：

> 专门为了做海报，在摄影棚里拍摄的精致美食素材。

### Diary 食物允许出现

-   普通手机画质
-   轻微噪点
-   自然环境光
-   室内偏黄灯光
-   窗边自然光
-   轻微曝光差异
-   普通餐桌
-   普通餐具
-   塑料杯
-   外卖包装
-   食堂餐盘
-   便利店食品
-   手拿食物
-   食物自然的不规则形状
-   普通甚至略显随意的摆盘
-   轻微阴影
-   不同照片之间不同的拍摄角度
-   不同照片之间不同的色温

这些"不完美"应该保留。

------------------------------------------------------------------------

# 5. Calendar Reference

## 5.1 Calendar Sticker Reference

使用：

``` text
calendar_sticker_reference_01.png
calendar_sticker_reference_02.jpg
calendar_sticker_reference_03.jpg
```

这些图片负责规定 Calendar / 月报页面的最终贴纸效果。

Calendar 与 Diary 的处理方式不同。

Calendar 中：

-   食物贴纸明显更小
-   贴纸跟随日期格排列
-   通常每个有记录的日期放 1 个主要食物贴纸
-   必要时可以出现 2～3 个小食物组合
-   不需要像 Diary 一样加入大量文字说明
-   不需要大量手绘装饰
-   必须保持月历原本的信息层级

效果应该像：

> 在原来的 Calendar UI 上额外贴了一层真实食物小贴纸。

而不是：

> 重新设计了一张新的 Calendar。

------------------------------------------------------------------------

## 5.2 Calendar Food Realism Reference

使用：

``` text
calendar_food_realism_reference_01.jpg
calendar_food_realism_reference_02.jpg
```

这些图片负责规定 Calendar 中食物本身的质感。

即使 Calendar 的食物尺寸很小，也必须保持：

-   真实照片感
-   自然光影
-   普通生活记录感
-   食物自身真实纹理
-   真实杯子 / 餐具 / 包装
-   白色贴纸描边

不要因为贴纸较小就变成：

-   emoji
-   icon
-   卡通食物
-   插画
-   3D render
-   电商素材
-   统一风格的素材包

------------------------------------------------------------------------

# 6. 最重要规则：LOCKED BASE IMAGE

所有输入截图都视为：

> **LOCKED BASE IMAGE**

除新增贴纸之外，原截图原则上全部锁定。

必须保持：

-   原始 width
-   原始 height
-   原始 aspect ratio
-   UI 布局
-   所有按钮位置
-   字体
-   字号
-   日期
-   数字
-   图标
-   状态栏
-   导航栏
-   卡片
-   背景
-   原有文字
-   原有颜色
-   原有间距
-   原有截图裁切范围

### 禁止

不要为了放入食物而：

-   拉伸截图
-   压缩截图
-   改变宽高比
-   裁掉截图
-   扩展截图
-   重画整个 UI
-   修改原有文字
-   修改日期
-   修改数字
-   移动按钮
-   改变卡片尺寸
-   改变 App 页面比例
-   自动"优化"原 UI

核心原则：

> **EDIT THE SCREENSHOT. DO NOT RECREATE THE SCREENSHOT.**

如果无法保证 UI 重绘后与原图完全一致，就不要重绘 UI。

------------------------------------------------------------------------

# 7. 食物真实感：最高优先级

这是整个项目最重要的视觉规则之一。

## 正确效果

食物应该像：

> iPhone / 普通手机随手拍 → 抠图 → 加白边 → 贴到页面。

关键词：

``` text
casual smartphone snapshot
ordinary phone photo
real-life food
natural ambient light
slightly imperfect exposure
casual composition
everyday meal
non-studio photography
realistic food texture
natural shadow
unpolished
```

真实感的优先级：

> **真实 \> 精致**

> **普通 \> 商业**

> **自然不完美 \> AI 完美**

------------------------------------------------------------------------

## 禁止的食物效果

不要生成：

-   摄影棚美食摄影
-   商业广告图
-   电商产品图
-   专业 food photography
-   过度精致摆盘
-   完美顶光
-   强 HDR
-   过高饱和度
-   过度锐化
-   塑料感
-   蜡质感
-   3D render
-   卡通
-   emoji
-   插画
-   所有食物完全相同光线
-   所有食物完全相同拍摄角度
-   所有食物完全相同餐具
-   所有食物统一成一套素材库风格
-   AI 自动把普通食物"美化"成高级餐厅菜品

如果"更漂亮"和"更真实"冲突：

> **选择更真实。**

------------------------------------------------------------------------

# 8. 食物贴纸抠图规则

贴纸应该沿主体真实轮廓进行抠图。

主体可以包含：

-   食物
-   碗
-   盘子
-   杯子
-   包装
-   与食物直接相关的手部
-   必要的小餐具

然后添加自然白色描边。

### 白边

白边应该：

-   清晰
-   柔和
-   有手账贴纸感
-   宽度适中
-   随主体轮廓变化

不要：

-   强行裁成圆形
-   强行裁成方形
-   保留原照片的大块矩形背景
-   使用特别粗的白边
-   做成发光描边

边缘可以稍微不规则。

不要追求机器切割般绝对光滑。

------------------------------------------------------------------------

# 9. Diary 排版规则

Diary 页面以 **2～4 个较大的食物贴纸** 为主。

优先使用页面原有空白区域。

贴纸可以：

-   左右错落
-   轻微旋转
-   大小略有区别
-   局部产生轻微视觉重叠

但不要：

-   挡住原始文字
-   挡住日期
-   挡住心情状态
-   挡住按钮
-   挡住底部照片
-   填满整个页面
-   把所有贴纸排得像商品目录

Diary 的目标是：

> 像用户自己做的一页轻松饮食手账。

------------------------------------------------------------------------

## Diary 文字

如果需要，可为食物加入：

``` text
早餐
≈ 420 kcal
```

或：

``` text
牛腩捞面
≈ 520 kcal
```

文字可以使用轻微手写感，但必须：

-   清晰
-   简洁
-   不抢 UI
-   不过度装饰

允许少量：

-   箭头
-   爱心
-   小线条
-   小星星

但这些只是辅助元素。

**食物始终是视觉主体。**

------------------------------------------------------------------------

# 10. Calendar 排版规则

Calendar 中必须优先尊重日期格。

每个食物应该属于某一个具体日期。

通常：

``` text
日期
↓
食物贴纸
↓
原有数据
```

贴纸必须限制在对应日期列允许的空间内。

不要：

-   跨越多个日期格
-   遮住相邻日期
-   遮住 kcal
-   遮住运动时间
-   遮住运动类型
-   改变原有日期排列

------------------------------------------------------------------------

## Calendar 不需要每天都填满

如果原始截图只有部分日期有记录：

> **只给已有记录日期增加贴纸。**

不要擅自填满整个月。

如果输入页面只有 20 天记录，就保持 20 天记录。

不要为了视觉效果自动补齐剩余日期。

------------------------------------------------------------------------

# 11. Diary 与 Calendar 的区别

  项目       Diary        Calendar
  ---------- ------------ ----------------
  贴纸尺寸   较大         较小
  食物数量   少量         多日期
  食物细节   丰富         缩小后仍可辨认
  kcal       可额外标注   优先保留原 UI
  食物名称   可添加       通常不额外添加
  手绘元素   少量允许     极少
  排版       自由错落     严格跟随日期
  真实感     强           强
  原 UI      完全保留     完全保留

------------------------------------------------------------------------

# 12. 执行流程

每次处理图片时严格按照以下顺序执行。

## STEP 1 --- 判断任务类型

判断输入属于：

``` text
DIARY
```

还是：

``` text
CALENDAR
```

------------------------------------------------------------------------

## STEP 2 --- 自动选择 Reference

### DIARY

读取：

``` text
references/diary_sticker_reference_*
references/diary_food_realism_reference_*
```

### CALENDAR

读取：

``` text
references/calendar_sticker_reference_*
references/calendar_food_realism_reference_*
```

**不要使用错误类别的 reference 控制排版。**

例如：

不要拿 Diary 大贴纸的尺寸去做 Calendar。

------------------------------------------------------------------------

## STEP 3 --- 锁定截图

首先读取原图：

``` text
width
height
aspect_ratio
```

最终输出必须保持一致。

------------------------------------------------------------------------

## STEP 4 --- 分析不可修改区域

识别：

-   状态栏
-   标题
-   日期
-   数字
-   卡片
-   按钮
-   导航栏
-   原有照片
-   月历日期格
-   运动 / 热量信息

这些区域原则上不得修改。

------------------------------------------------------------------------

## STEP 5 --- 确定贴纸区域

寻找：

-   Diary 中的空白区域

或：

-   Calendar 中每个日期允许放置贴纸的位置

------------------------------------------------------------------------

## STEP 6 --- 准备食物

如果用户提供真实食物照片：

> 优先使用用户提供的照片。

对照片进行：

``` text
抠图
→ 保留自然质感
→ 添加白色描边
→ 调整尺寸
→ 放入截图
```

不要重新生成一个"更漂亮"的版本替代用户照片。

如果没有提供食物照片，需要生成食物：

> 严格参考对应 `food_realism_reference_*` 的真实感。

------------------------------------------------------------------------

## STEP 7 --- 合成

将贴纸加入原截图。

原则：

> 尽可能只改变需要增加贴纸的像素区域。

不要重新生成整张截图。

------------------------------------------------------------------------

## STEP 8 --- QA 检查

输出前逐项检查：

``` text
[ ] width 是否与输入一致
[ ] height 是否与输入一致
[ ] aspect ratio 是否与输入一致
[ ] 截图是否被裁切
[ ] UI 是否被重新设计
[ ] 原文字是否变化
[ ] 日期是否变化
[ ] 数字是否变化
[ ] 按钮是否变化
[ ] 原图颜色是否被整体修改
[ ] 食物是否像手机随手拍
[ ] 是否出现摄影棚质感
[ ] 是否出现 AI 塑料感
[ ] 白色描边是否自然
[ ] 贴纸轮廓是否合理
[ ] Diary 贴纸是否过小
[ ] Calendar 贴纸是否过大
[ ] 是否错误覆盖原 UI
[ ] 是否擅自增加原截图不存在的数据
```

任何一项失败：

> **重新处理，不要直接输出。**

------------------------------------------------------------------------

# 13. 批量生产规则

批量处理多个截图时，所有结果需要保持同一个系列的视觉语言，但不能看起来像复制粘贴。

## 可以变化

主动变化：

-   食物种类
-   饮料种类
-   餐具
-   包装
-   拍摄角度
-   光线
-   色温
-   贴纸旋转角度
-   贴纸大小
-   食物组合
-   构图
-   白边的自然轮廓

## 不可以变化

必须保持：

-   输入截图 UI
-   输入截图尺寸
-   输入截图比例
-   App 原有字体
-   App 原有按钮
-   App 原有文字
-   Reference 所规定的整体视觉语言
-   手机随手拍真实感

最终应该让人感觉：

> **同一个人在不同天真实记录自己的饮食。**

而不是：

> **AI 一次性生成了一套统一的食物素材包。**

------------------------------------------------------------------------

# 14. Codex 执行指令

处理新图片时，可直接使用以下要求：

``` text
Read README.md and FOOD_STICKER_STYLE_GUIDE.md before processing.

First classify the input as DIARY or CALENDAR.

If DIARY:
use references/diary_sticker_reference_* for layout and sticker styling,
and references/diary_food_realism_reference_* for food realism.

If CALENDAR:
use references/calendar_sticker_reference_* for layout and sticker styling,
and references/calendar_food_realism_reference_* for food realism.

Treat the input screenshot as a LOCKED BASE IMAGE.

Do not redesign, recreate, resize, stretch, crop, extend, translate,
or modify the original UI.

Preserve the exact original width, height, aspect ratio, layout, text,
numbers, dates, icons, buttons, colors, spacing, status bar and navigation.

Only add food sticker elements in appropriate available areas.

Food must look like casual smartphone snapshots taken by an ordinary user,
not studio food photography.

Preserve natural imperfections:
ordinary lighting, casual composition, slight exposure differences,
real plates, cups, packaging, takeaway containers and natural shadows.

Cut food subjects out along their natural silhouettes and add a soft,
clean white sticker border.

Do not make the food look like:
commercial photography, ecommerce imagery, 3D renders, illustrations,
emoji, plastic food, overly polished restaurant photography or a
consistent AI-generated asset pack.

For Diary:
use a small number of larger stickers with natural scrapbook composition.

For Calendar:
use small stickers aligned to the correct date cells without covering
existing calendar information.

Realism is more important than beauty.

Natural imperfection is more important than AI perfection.

EDIT THE SCREENSHOT.
DO NOT RECREATE THE SCREENSHOT.

Before export, compare the result against the original screenshot and
verify that all non-sticker UI pixels remain visually unchanged.
```

------------------------------------------------------------------------

# 15. 最终原则

如果只记住三句话：

> **1. 原截图锁死，不要重新设计 UI。**

> **2. 食物是普通手机随手拍，不是摄影棚美食图。**

> **3. Diary 看 Diary reference，Calendar 看 Calendar
> reference，不要串风格。**

最终视觉目标：

> **真实用户的饮食记录 + 手账贴纸感。**

而不是：

> **AI 设计的精致美食海报。**
