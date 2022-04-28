# python 画图代码记录

## pip 下载笔记

### 使用镜像站下载

临时

```CMD

pip install -U plotly -i https://pypi.tuna.tsinghua.edu.cn/simple

```

默认

```CMD

pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

```

### 网站

**清华**
<https://pypi.tuna.tsinghua.edu.cn/simple/>

**中科大**
<https://pypi.mirrors.ustc.edu.cn/simple/>

**阿里云**
<https://mirrors.aliyun.com/pypi/simple/>

**豆瓣**
<https://pypi.douban.com/simple/>

## pyecharts 点线叠图模板

```python

from pyecharts import options as opts
from pyecharts.charts import Line, Scatter
from pyecharts.faker import Faker
from pyecharts.globals import ThemeType

x = Faker.choose()

# 线图
li = (
    # 基础设置
    Line(
        init_opts=opts.InitOpts(
            # width="900px",
            # height="600px",
            chart_id="线图",
            page_title="测试网页",
            renderer= "svg",
            # theme="CHALK",
            bg_color=None,
        ),
    )

    # 添加XY数据
    .add_xaxis(x)
    .add_yaxis("商家A",Faker.values(),yaxis_index=0,)
    .add_yaxis("商家B",Faker.values(),yaxis_index=0,color="#9c9",)

    # 整体画面设置
    .set_global_opts(

        # 标题设置
        title_opts=opts.TitleOpts(
            # title="测试分类",
            title_link="https://hehu.fun",
            title_target='blank',
            # subtitle="208Pb / 207Pb",
            subtitle_link=None,
            subtitle_target="#",
            pos_left="left",
            pos_top="top",
            padding=[5,20,5,20],
            item_gap=10,
            title_textstyle_opts=opts.TextStyleOpts(
                color="#9c9",
            ),
            subtitle_textstyle_opts=opts.TextStyleOpts(
                color="#666",
            ),
        ),

        # 图例设置
        legend_opts=opts.LegendOpts(
            type_='plain',
            is_show=True,
            pos_left="center",
            pos_top="top",
            orient='horizontal',
            padding=20,
        ),

        # 提示框配置项
        tooltip_opts=opts.TooltipOpts(
            is_show=True,
            trigger='item',
            trigger_on="mousemove|click",
            axis_pointer_type="cross",
            is_show_content=True,
            is_always_show_content=False,
        ),

        # 工具栏设置
        toolbox_opts=opts.ToolboxOpts(
            is_show=True,
            orient="vertical",
            item_size=20,
            item_gap=16,
            pos_left="right",
            pos_top="center",
            feature=opts.ToolBoxFeatureOpts(
                # 保存为图片
                save_as_image=opts.ToolBoxFeatureSaveAsImageOpts(
                    type_="jpeg",
                    is_show=True,
                    title="保存💾",
                    pixel_ratio=2
                ),
                # 配置项还原
                restore=opts.ToolBoxFeatureRestoreOpts(
                    is_show=True,
                    title="还原♻️",
                ),
                # 数据视图工具，可以展现当前图表所用的数据，编辑后可以动态更新
                data_view=opts.ToolBoxFeatureDataViewOpts(
                    is_show=True,
                    title="数据🔢",
                    is_read_only=False,
                    background_color="#fff",
                    text_area_color="#fff",
                    text_area_border_color="#9c9",
                    text_color="#000",
                    button_color="#9c9",
                    button_text_color="#000",
                ),
                # 数据区域缩放。
                data_zoom=opts.ToolBoxFeatureDataZoomOpts(
                    is_show=False,
                ),
                # 动态类型切换
                magic_type=opts.ToolBoxFeatureMagicTypeOpts(
                    is_show=True,
                    # type_=['line','bar','stack','tiled'],
                ),
                # 选框组件的控制按钮
                brush=opts.ToolBoxFeatureBrushOpts(
                    type_=[],
                ),
            ),
        ),

        # 区域选择组件配置项
        brush_opts=opts.BrushOpts(
            tool_box=["clear",],
        ),

        # X轴
        xaxis_opts=opts.AxisOpts(
            is_show=True,
            is_scale=True,
            is_inverse=False,
            name_location="middle",
            name_gap=30,
            # type_="value",
            name="206Pb",
            # 坐标轴刻度线配置项
            axisline_opts=opts.AxisLineOpts(
                is_show=True,
                is_on_zero=False,
                symbol=["none","arrow"],
            ),
            # 坐标轴刻度配置项
            axistick_opts=opts.AxisTickOpts(
                is_show=True,
                is_align_with_label=False,
                is_inside=True,
                length=10,
            ),
            # 坐标轴标签配置项
            axislabel_opts=opts.LabelOpts(
                is_show=True,
                margin=8,
            ),
            # 坐标轴次刻度线相关设置
            minor_tick_opts=opts.MinorTickOpts(is_show=True,split_number=5,length=3),
            minor_split_line_opts=opts.MinorSplitLineOpts(is_show=False,width=1,opacity=0.5,type_="dotted",),
            # 分割区域配置项
            splitline_opts=opts.SplitLineOpts(is_show=False),
            splitarea_opts=opts.SplitAreaOpts(is_show=False),
        ),

        # Y轴
        yaxis_opts=opts.AxisOpts(
            is_show=True,
            is_scale=True,
            is_inverse=False,
            name_location="middle",
            name_gap=30,
            type_="value",
            name="207Pb",
            # 坐标轴刻度线配置项
            axisline_opts=opts.AxisLineOpts(
                is_show=True,
                is_on_zero=False,
                symbol=["none","arrow"],
            ),
            # 坐标轴刻度配置项
            axistick_opts=opts.AxisTickOpts(
                is_show=True,
                is_align_with_label=False,
                is_inside=True,
                length=10,
            ),
            # 坐标轴标签配置项
            axislabel_opts=opts.LabelOpts(
                is_show=True,
                margin=8,
            ),
            # 坐标轴次刻度线相关设置
            minor_tick_opts=opts.MinorTickOpts(is_show=True,split_number=5,length=3),
            minor_split_line_opts=opts.MinorSplitLineOpts(is_show=False,width=1,opacity=0.5,type_="dotted",),
            # 分割区域配置项
            splitline_opts=opts.SplitLineOpts(is_show=False),
            splitarea_opts=opts.SplitAreaOpts(is_show=False),
        ),

        # 视觉映射配置项
        visualmap_opts=opts.VisualMapOpts(
            is_show=False,
            type_="color",
            min_=0,
            max_=150,
            range_color=["#9c9","#999","#000","#8g8"],
            range_text=["高","低"],
            range_size=2,
            range_opacity=0.1,
            orient="vertical",
            pos_left="left",
            pos_top="bottom",
            series_index=[],#选取序列
            dimension=None,
            is_calculable=True,
            is_piecewise=False,
            is_inverse=False,
            precision=2,
            pieces=[],
            out_of_range=None,
            item_width=20,
            item_height=200,
        ),

        # 缩放设置
        datazoom_opts=opts.DataZoomOpts(
            is_show=True,
            type_="inside",
            range_start=0,
            range_end=100,
            is_zoom_lock=False,
        ),

    )
)

# 散点图
sca = (
    Scatter()
    .add_xaxis(x)
    .add_yaxis("商家C", Faker.values())
    .add_yaxis("商家B", Faker.values())
)

li.overlap(sca)
li.render("点线图.html")
li.render_notebook()

```
