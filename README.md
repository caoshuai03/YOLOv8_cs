### 旧版本YOLOv8代码修改
# loss修改
(【最新！YOLOv8修改损失函数】 https://www.bilibili.com/video/BV1QC4y1d7WW/?share_source=copy_web&vd_source=d7850fadfe10285a97043c4d7320aefc)

1、找到loss.py和tal.py文件

2、两个文件各自搜索iou1,找到对应所在行,修改函数名即可

3、点击函数bbox_iou可以查看可使用的loss函数,其中WIOU使用方法见视频

# 注意力机制修改
【最新！YOLOv8添加注意力机制——轻松上手】 https://www.bilibili.com/video/BV1tV4y1v7ND/?share_source=copy_web&vd_source=d7850fadfe10285a97043c4d7320aefc

1、找到需要添加的注意力机制

2、在conv.py文件下 
路径：ultralytics/nn/modules/conv.py
放入注意力机制代码

3、--在conv.py的__all__里添加名字
----在ultralytics/nn/modules/__init__.py 添加名字
----在ultralytics/nn/tasks.py 添加名字

4、在ultralytics/nn/tasks.py添加配置

（1）elif m in {CBAM}:
        c1, c2 = ch[f], args[0]
        if c2 != nc:
            c2 = make_divisible(min(c2, max_channels) * width, 8)
        args = [c1, *args[1:]]

（2）elif m in {GatherExcite}:
    args =[ch[f],*args]

5、test运行一下 报什么错 对应debug


