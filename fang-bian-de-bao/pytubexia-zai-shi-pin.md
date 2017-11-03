> from-http://www.cnblogs.com/yinxiangnan-charles/p/5645561.html

**安装**

pip install pytube

**库的使用**

```py
from pytube import YouTube

# pprint-pretty print 不必要，仅仅为了让输出更好看，每个视频文件占一行
from pprint import pprint

yt = YouTube("http://www.youtube.com/watch?v=Ik-RsDGPI5Y")

# 显示所有可以下载的视频文件
pprint(yt.get_videos())

# 显示视频文件名
print(yt.filename)

# 设置视频文件名
yt.set_filename('myFirstVideo')

# 根据文件类型过滤视频文件
pprint(yt.filter('flv'))

# 由于排序是按清晰度从低到高，所以可以用 -1 索引到最高清版本
print(yt.filter('.mp4')[-1])

# 根据清晰度过滤文件
pprint(yt.filter(resolution='480p'))

# 通过文件类型和清晰度指定下载的视频
video = yt.get('mp4','720p')

# 如果有多个相同类型，或者相同清晰度的文件，则不能仅指定一种格式来下载视频，例如下面一行可能会报错：
video = yt.get('mp4')

# 其实，上面的 video 完全可以用过滤+索引的方式获得，不一定非得用 get 方法
video = yt.filter('.mp4')[-1]

# 下载到指定路径
video.download('/home/Desktop')
```

**命令行工具的使用**

```bash
传入参数 -e （或者 --extension=）来设置下载的文件类型
$ pytube -e mp4 https://www.youtube.com/watch?v=hMPBSwexqG8
传入 -r 设定清晰度
$ pytube -r 720p https://www.youtube.com/watch?v=hMPBSwexqG8
传入 -p 设置保存路径
$ pytube -r 720p -p ~/Downloads/ https://www.youtube.com/watch?v=hMPBSwexqG8
传入 -f 设置保存名称
$ pytube -e mp4 -f liangjian https://www.youtube.com/watch?v=hMPBSwexqG8
 同时设置下载的类型和清晰度
$ pytube -e mp4 -r 720p https://www.youtube.com/watch?v=hMPBSwexqG8
```



