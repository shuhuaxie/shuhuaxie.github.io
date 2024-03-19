---
layout: post
title:  "2024-03-04-mediaPlayer源码理解.markdown"
date:   2024-03-04 12:11:30 +0800

1) 整体流程
app接受指令,并通过surface进行内容展示
app会将指令通过aidl进程间通讯传递给MediaPlayerService
MediaPlayerService创建AudioTrack进行音频播放

2) 
- App端使用MediaPlayer进行内容播放
- MediaPlayer调用c++代码frameworks\base\media\jni\android_media_MediaPlayer.cpp进行prepare等具体的操作
- 转至frameworks\av\media\libmedia\mediaplayer.cpp
- 调用frameworks\av\media\libmedia\IMediaDeathNotifier.cpp和MediaPlayerService进行通讯
    sp<IServiceManager> sm = defaultServiceManager();
    sp<IBinder> binder;
    do {
        binder = sm->getService(String16("media.player"));
        if (binder != 0) {
            break;
        }
        ALOGW("Media player service not published, waiting...");
        usleep(500000); // 0.5 s
    } while (true);
- 通过frameworks\av\media\libmediaplayerservice\MediaPlayerService.cpp创建AudioTrack
t = new AudioTrack(...);


 








    






