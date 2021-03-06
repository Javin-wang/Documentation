
---
title: 美声与音效
description: How to adjust voice effect for Android
platform: Android
updatedAt: Fri Jun 19 2020 13:41:17 GMT+0800 (CST)
---
# 美声与音效
## 功能描述
在社交娱乐应用中，为增加产品的趣味性和互动性，用户常常需要变声和混响效果。Agora 提供多种预置的变声和混响效果，你也可以灵活定制自己想要的声音，比如设置音调、均衡和混响等。

Agora 提供[在线 Demo](https://www.agora.io/cn/audio-demo)，你可以体验变声与混响效果。

## 实现方法

开始前请确保已在你的项目中实现基本的实时音视频功能。 详见[开始音视频通话](../../cn/Video/start_call_android.md)或[开始互动直播](../../cn/Video/start_live_android.md)。

### 预设声音效果

#### 变声音效

通常在语聊场景中，通过 `setLocalVoiceChanger` 中以下枚举值，你可以实现变声效果：

| 枚举值                 | 变声效果 |
| :--------------------- | :------- |
| VOICE_CHANGER_OLDMAN   | 老年男性   |
| VOICE_CHANGER_BABYBOY  | 小男孩   |
| VOICE_CHANGER_BABYGIRL | 小女孩   |
| VOICE_CHANGER_ZHUBAJIE | 猪八戒   |
| VOICE_CHANGER_ETHEREAL | 空灵     |
| VOICE_CHANGER_HULK     | 绿巨人   |

<div class="alert note">同一时间，只能实现变声音效、美音、语聊美声、混响音效中的一种。</div>

```java
// 预设变声音效为老年男性
mRtcEngine.setLocalVoiceChanger(VOICE_CHANGER_OLDMAN);
// 关闭效果
mRtcEngine.setLocalVoiceChanger(VOICE_CHANGER_OFF);
```

####  美音

通常在语聊或歌唱场景中，通过 `setLocalVoiceChanger` 中以下枚举值，你可以实现美音效果：

| 枚举值                  | 美音效果 |
| :---------------------- | :------- |
| VOICE_BEAUTY_VIGOROUS   | 浑厚     |
| VOICE_BEAUTY_DEEP       | 低沉     |
| VOICE_BEAUTY_MELLOW     | 圆润     |
| VOICE_BEAUTY_FALSETTO   | 假音     |
| VOICE_BEAUTY_FULL       | 饱满     |
| VOICE_BEAUTY_CLEAR      | 清澈     |
| VOICE_BEAUTY_RESOUNDING | 高亢     |
| VOICE_BEAUTY_RINGING    | 嘹亮     |
| VOICE_BEAUTY_SPACIAL    | 空旷     |

<div class="alert note">同一时间，只能实现变声音效、美音、语聊美声、混响音效中的一种。</div>

```java
// 预设美音效果为浑厚
mRtcEngine.setLocalVoiceChanger(VOICE_BEAUTY_VIGOROUS);
// 关闭效果
mRtcEngine.setLocalVoiceChanger(VOICE_CHANGER_OFF);
```

#### 语聊美声

通常在语聊场景中，通过 `setLocalVoiceChanger` 中以下枚举值，你可以实现语聊美声效果：

| 枚举值                               | 语聊美声效果 |
| :----------------------------------- | :----------- |
| GENERAL_BEAUTY_VOICE_MALE_MAGNETIC   | 磁性（男）   |
| GENERAL_BEAUTY_VOICE_FEMALE_FRESH    | 清新（女）   |
| GENERAL_BEAUTY_VOICE_FEMALE_VITALITY | 活力（女）   |

<div class="alert warning">该功能主要细化了男声和女声各自的特点，请确保使用 <tt>GENERAL_BEAUTY_VOICE_MALE_MAGNETIC</tt> 处理男声，使用 <tt>GENERAL_BEAUTY_VOICE_FEMALE_FRESH</tt> 或 <tt>GENERAL_BEAUTY_VOICE_FEMALE_VITALITY</tt> 处理女声，否则音频可能会产生失真。</div>

<div class="alert note">同一时间，只能实现变声音效、美音、语聊美声、混响音效中的一种。</div>

```java
// 预设语聊美声效果为磁性（男）
mRtcEngine.setLocalVoiceChanger(GENERAL_BEAUTY_VOICE_MALE_MAGNETIC);
// 关闭效果
mRtcEngine.setLocalVoiceChanger(VOICE_CHANGER_OFF);
```

#### 混响音效

通过 `setLocalVoiceReverbPreset`，你可以实现以下混响音效：

| 枚举值                        | 描述                                                         |
| :---------------------------- | :----------------------------------------------------------- |
| AUDIO_REVERB_POPULAR          | 流行                                                         |
| AUDIO_REVERB_RNB              | R&B                                                          |
| AUDIO_REVERB_ROCK             | 摇滚                                                         |
| AUDIO_REVERB_HIPHOP           | 嘻哈                                                         |
| AUDIO_REVERB_VOCAL_CONCERT    | 演唱会                                                       |
| AUDIO_REVERB_KTV              | KTV                                                          |
| AUDIO_REVERB_STUDIO           | 录音棚                                                       |
| AUDIO_REVERB_FX_KTV           | KTV（增强版）                                                |
| AUDIO_REVERB_FX_VOCAL_CONCERT | 演唱会（增强版）                                             |
| AUDIO_REVERB_FX_UNCLE         | 大叔                                                         |
| AUDIO_REVERB_FX_SISTER        | 小姐姐                                                       |
| AUDIO_REVERB_FX_STUDIO        | 录音棚（增强版）                                             |
| AUDIO_REVERB_FX_POPULAR       | 流行（增强版）                                               |
| AUDIO_REVERB_FX_RNB           | R&B（增强版）                                                |
| AUDIO_REVERB_FX_PHONOGRAPH    | 留声机                                                       |
| AUDIO_VIRTUAL_STEREO          | 虚拟立体声。虚拟立体声是指将单声道的音轨渲染出立体声的效果，使频道内所有用户听到有空间感的声音效果。 |

<div class="alert warning">当使用以 <tt>AUDIO_REVERB_FX</tt> 为前缀的枚举值时，请确保在调用该方法前将 <tt>setAudioProfile</tt> 的 <tt>profile</tt> 参数设置为 <tt>AUDIO_PROFILE_MUSIC_HIGH_QUALITY(4)</tt> 或 <tt>AUDIO_PROFILE_MUSIC_HIGH_QUALITY_STEREO(5)</tt>，否则该方法设置无效。</div>

<div class="alert note"><li>同一时间，只能实现变声音效、美音、语聊美声、混响音效中的一种。<li>为达到更好的混响音效，Agora 推荐使用以 <tt>AUDIO_REVERB_FX</tt> 为前缀的枚举值。<li>当使用 <tt>AUDIO_VIRTUAL_STEREO</tt> 设置虚拟立体声时，Agora 推荐在调用该方法前将 <tt>setAudioProfile</tt> 的 <tt>profile</tt> 参数设置为 <tt>AUDIO_PROFILE_MUSIC_HIGH_QUALITY_STEREO(5)</tt>。</div>

```java
// 预设混响音效为演唱会（增强版 ）
mRtcEngine.setLocalVoiceReverbPreset(AUDIO_REVERB_FX_VOCAL_CONCERT);
// 关闭混响效果
mRtcEngine.setLocalVoiceReverbPreset(AUDIO_REVERB_OFF);
```

### 定制声音效果

如果预设效果无法满足你的需求，你也可以通过 `setLocalVoicePitch`、`setLocalVoiceEqualization` 和 `setLocalVoiceReverb` 自行调整音调、均衡和混响效果。

你可以根据以下示例代码把原始声音变成绿巨人霍克的声音。

```java
// 设置音调。可以在 [0.5, 2.0] 范围内设置。取值越小，则音调越低。默认值为 1.0，表示原始音调。
double pitch = 0.5;
rtcEngine.setLocalVoicePitch(pitch);
  
// 设置本地语音均衡波段的中心频率
// 第1个参数为频谱子带索引，取值范围 [0, 9]，分别代表 10 个频带，对应的中心频率是 [31, 62, 125, 250, 500, 1k, 2k, 4k, 8k, 16k] Hz
// 第2个参数为每个频率区间的增益值，取值范围 [-15,15]，单位 dB, 默认值为 0
rtcEngine.setLocalVoiceEqualization(0, -15);
rtcEngine.setLocalVoiceEqualization(1, 3);
rtcEngine.setLocalVoiceEqualization(2, -9);
rtcEngine.setLocalVoiceEqualization(3, -8);
rtcEngine.setLocalVoiceEqualization(4, -6);
rtcEngine.setLocalVoiceEqualization(5, -4);
rtcEngine.setLocalVoiceEqualization(6, -3);
rtcEngine.setLocalVoiceEqualization(7, -2);
rtcEngine.setLocalVoiceEqualization(8, -1);
rtcEngine.setLocalVoiceEqualization(9, 1);
  
// 原始声音强度，即所谓的 dry signal，取值范围 [-20, 10]，单位为 dB
rtcEngine.setLocalVoiceReverb(Constants.AUDIO_REVERB_DRY_LEVEL, 10);
  
// 早期反射信号强度，即所谓的 wet signal，取值范围 [-20, 10]，单位为 dB
rtcEngine.setLocalVoiceReverb(Constants.AUDIO_REVERB_WET_LEVEL, 7);
  
// 所需混响效果的房间尺寸，一般房间越大，混响越强，取值范围 [0, 100]
rtcEngine.setLocalVoiceReverb(Constants.AUDIO_REVERB_ROOM_SIZE, 6);
  
// Wet signal 的初始延迟长度，取值范围 [0, 200]，单位为 ms
rtcEngine.setLocalVoiceReverb(Constants.AUDIO_REVERB_WET_DELAY, 124);
  
// 混响持续的强度，取值范围为 [0, 100]，值越大，混响越强
rtcEngine.setLocalVoiceReverb(Constants.AUDIO_REVERB_STRENGTH, 78);
```

### API 参考

**预设声音效果：**
- [`setLocalVoiceChanger`](https://docs.agora.io/cn/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#ade6883c7878b7a596d5b2563462597dd)
- [`setLocalVoiceReverbPreset`](https://docs.agora.io/cn/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a10dd25bc8e129512cd6727133b7fc42f)

**定制声音效果：**
- [`setLocalVoicePitch`](https://docs.agora.io/cn/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a41b525f9cbf2911594bcda9b20a728c9)
- [`setLocalVoiceEqualization`](https://docs.agora.io/cn/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a9e3aa79f0d6d8f2ea81907543506d960)
- [`setLocalVoiceReverb`](https://docs.agora.io/cn/Video/API%20Reference/java/classio_1_1agora_1_1rtc_1_1_rtc_engine.html#a4afc32ba68e997e90ba3f128317827fa)

## 开发注意事项

- 本文所有方法对人声的处理效果最佳，Agora 不推荐调用这类方法处理含人声和音乐的音频数据。
- Agora 建议不要同时使用预设声音效果相关方法和定制声音效果相关方法，否则可能会发生未定义行为。若需同时使用，请在调用预设声音效果相关方法后调用定制声音效果相关方法，否则定制声音效果相关方法会不生效。
- Agora 建议不要同时使用 `setLocalVoiceChanger` 和 `setLocalVoiceReverbPreset` 方法，否则先调用的方法会不生效。
- 为达到更好的声音效果，Agora 推荐在调用 `setLocalVoiceChanger` 或 `setLocalVoiceReverbPreset` 前将 `setAudioProfile` 的 `profile` 参数设置为 `AUDIO_PROFILE_MUSIC_HIGH_QUALITY(4)` 或 `AUDIO_PROFILE_MUSIC_HIGH_QUALITY_STEREO(5)`。
