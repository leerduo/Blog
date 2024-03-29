title: Magic Progress Widget
date: 2015-12-13 15:45:03
tags:
- draw
- sweep
- gradient
- open source

---

> 渐变的圆形进度条与轻量横向进度条

<!--more-->

## I. 最终效果

![demo gif][demo_gif]

## II. 如何使用

`build.gradle`中配置:

```
compile 'com.liulishuo.magicprogresswidget:library:1.0.7'
```

> 建议参考github中的demo

```
<com.liulishuo.magicprogresswidget.MagicProgressCircle
    android:id="@+id/demo_mpc"
    android:layout_width="@dimen/mpc_size"
    android:layout_height="@dimen/mpc_size"
    app:mpc_percent="0.8"
    app:mpc_start_color="@color/mpc_start_color"
    app:mpc_end_color="@color/mpc_end_color"
    app:mpc_stroke_width="@dimen/mpc_stroke_width"
    app:mpc_default_color="@color/mpc_default_color"/>

<com.liulishuo.magicprogresswidget.MagicProgressBar
    android:id="@+id/demo_2_mpb"
    android:layout_width="match_parent"
    android:layout_height="@dimen/mpb_height"
    app:mpb_fill_color="@color/mpb_color"
    app:mpb_background_color="@color/mpb_default_color"
    app:mpb_flat="true"/>
```

#### 1. Magic Progress Circle

| 参数 | 含义 | 默认值 |
| :--- | :--- | :--- |
| mpc_percent | 填充的百分比[0, 1] | 0 |
| mpc_stroke_width | 描边宽度 | 18dp |
| mpc_start_color | 渐变颜色起点颜色(percent=0) | <font color="#FF00FFED">#FF00FFED</font> |
| mpc_end_color | 渐变颜色终点颜色(percent=1) | <font color="#FFED00FF">#FFED00FF</font> |
| mpc_default_color | 未填充部分的描边的颜色 | <font color="#1AFFFFFF">#1AFFFFFF</font> |

#### 2. Magic Progress Bar

> 相比系统的ProgressBar更加轻量，如果你的ProgressBar要求不是很复杂，推荐使用

| 参数 | 含义 | 默认值 |
| :--- | :--- | :--- |
| mpb_percent | 填充的百分比[0, 1] | 0 |
| mpb_fill_color | 填充进度的颜色 | 0 |
| mpb_background_color | 进度背景的颜色 | 0 |
| mpb_flat | 填充的进度条右侧是否是平面(不是平面就是圆弧) | false |

## III. Github

[lingochamp](https://github.com/lingochamp/MagicProgressWidget)

## IV. bintray

[![Download][bintray_svg]][bintray_link]

[demo_gif]: https://github.com/lingochamp/MagicProgressWidget/raw/master/art/demo.gif
[bintray_svg]: https://api.bintray.com/packages/jacksgong/maven/MagicProgressWidget/images/download.svg
[bintray_link]: https://bintray.com/jacksgong/maven/MagicProgressWidget/_latestVersion
