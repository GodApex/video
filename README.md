# video

`用来存储视频`

------

# 执行切片

## 第一步：mp4转成ts格式，一对一转换，转换后大小没什么变化。

```
ffmpeg -y -i 你的名字.mp4 -vcodec copy -acodec copy -vbsf h264_mp4toannexb 你的名字.ts
```

## 第二步，按间隔分片，1对N，下面的5即“每个分片5秒”，可以自己切换。

```
ffmpeg -i 你的名字.ts -c copy -map 0 -f segment -segment_list playlist.m3u8 -segment_time 5 你的名字%03d.ts
```

------

# 再使用upload.bat上传

![](https://cdn.jsdelivr.net/gh/Peter-Highness/free@6e0b404d9f97e084d9559feeecf8face53620a6c/2020/10/17/c3ee5ad7fb65be99ad7224d783070ec6.png)

------

# upload.bat内容

```bat
git add -A
git commit -m"%date:~0,4%%date:~5,2%%date:~8,2%%time:~0,2%%time:~3,2%%time:~6,2%"
git branch -M master
git push -u origin master
```

