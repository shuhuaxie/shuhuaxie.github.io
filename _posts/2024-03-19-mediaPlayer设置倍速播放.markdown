---
layout: post
title:  "2024-03-19-mediaPlayer设置倍速播放.markdown"
date:   2024-03-19 12:11:30 +0800

调用过程
- App设置倍速
PlaybackParams params = uiHolder.player.getPlaybackParams();
params.setSpeed(speed);
uiHolder.player.setPlaybackParams(params);
- 进入native层 [android_media_MediaPlayer.cpp]
mp->setPlaybackSettings(rate);
- [mediaplayer.cpp]
status_t err = mPlayer->setPlaybackSettings(rate);
    1. mPlayer的创建
        1) getMediaPlayerService()[MediaPlayerService.cpp]
        2) service->create(this, mAudioSessionId, mAttributionSource)
            sp<Client> c = new Client(
            this, verifiedAttributionSource, connId, client, audioSessionId);
- [MediaPlayerService.cpp] 中转给player
    status_t MediaPlayerService::Client::setPlaybackSettings(const AudioPlaybackRate& rate)
    {
        ALOGV("[%d] setPlaybackSettings(%f, %f, %d, %d)",
        mConnId, rate.mSpeed, rate.mPitch, rate.mFallbackMode, rate.mStretchMode);
        sp<MediaPlayerBase> p = getPlayer();
        if (p == 0) return UNKNOWN_ERROR;
        return p->setPlaybackSettings(rate);
    }
- [MediaPlayerService.h]
sp<MediaPlayerBase>     getPlayer() const { Mutex::Autolock lock(mLock); return mPlayer; }
- [MediaPlayerService.cpp] MediaPlayerFactory提供真正的player
p = MediaPlayerFactory::createPlayer(playerType, mListener,
VALUE_OR_FATAL(aidl2legacy_int32_t_pid_t(mAttributionSource.pid)));
- [MediaPlayerFactory.cpp] 
factory = sFactoryMap.valueFor(playerType);
CHECK(NULL != factory);
p = factory->createPlayer(pid);
- factory注册
    status_t MediaPlayerFactory::registerFactory_l(IFactory* factory,
    player_type type) {
    if (NULL == factory) {
    ALOGE("Failed to register MediaPlayerFactory of type %d, factory is"
    " NULL.", type);
    return BAD_VALUE;
    }
    
    if (sFactoryMap.indexOfKey(type) >= 0) {
    ALOGE("Failed to register MediaPlayerFactory of type %d, type is"
    " already registered.", type);
    return ALREADY_EXISTS;
    }
    
    if (sFactoryMap.add(type, factory) < 0) {
    ALOGE("Failed to register MediaPlayerFactory of type %d, failed to add"
    " to map.", type);
    return UNKNOWN_ERROR;
    }
    
    return OK;
    }


在Android系统中，MediaPlayerFactory.h中的registerFactory方法用于注册自定义的MediaPlayer工厂，
以便在需要创建MediaPlayer实例时，系统可以使用这个工厂来选择合适的MediaPlayer类型。
通常情况下，Android系统中有多种MediaPlayer实现，例如：
NuPlayer：这是Android Framework层中默认的MediaPlayer实现，用于处理大多数音视频播放任务。
AwesomePlayer：这是旧版的MediaPlayer实现，用于向后兼容以及特定的音视频播放场景。
FFmpeg 或其他第三方库的播放器：Android系统允许开发者使用第三方库来扩展MediaPlayer的功能，比如使用FFmpeg库来支持更多的音视频格式。
- [NuPlayer.cpp]
1. setPlaybackSettings
2. onMessageReceived
    case kWhatConfigPlayback:
3. mRenderer->setPlaybackSettings(rate);
new Renderer(mAudioSink, mMediaClock, notify, flags);
4. newRate.mSpeed = mPlaybackSettings.mSpeed;
mVideoDecoder->setParameters(params);



 








    






