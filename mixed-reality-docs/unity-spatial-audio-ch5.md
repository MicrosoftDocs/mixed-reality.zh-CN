---
title: 空间音频教程-5。 使用回音向空间音频添加距离
description: 添加回音效果，提高对空间音频的距离变体的意义。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182734"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>使用回音向空间音频添加距离

## <a name="objectives"></a>目标
在前面的章节中，我们将 spatialization 添加到声音，使其成为一种方向。 在本5章节中，我们将添加一个回音效果，为声音指定距离。 我们的目标是：
* 通过添加回音来改善声音源的感知距离
* 使用侦听器与全息图的距离控制声音的已知距离

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>添加混音器组和回音效果
在[第2章](unity-spatial-audio-ch2.md)，我们添加了一个混音器。 混音器默认包含一个名为**Master**的**组**。 因为我们只是想要将回音效果应用到一些声音，接下来要为这些声音添加另一个**组**。 若要添加**组**，请在**音频混合器**中右键单击**主控**组，然后选择 "**添加子组**"：

![添加子组](images/spatial-audio/add-child-group.png)

在此示例中，我们已将新组命名为 "房间效果"。

每个**组**都有自己的效果集。 通过在新组中单击 "**添加 ...** " 并选择 " **SFX 回音**"，向新组添加回音效果：

![添加 SFX 回音](images/spatial-audio/add-sfx-reverb.png)

在音频术语中，原始、unreverberated 的音频称为_晾干路径_，筛选后的音频被称为_湿路径_。 这两个路径都发送到音频输出，在此组合中，其相对强度称为_湿/干燥混合_。 湿/干燥混合会对距离的理解产生很大影响。

**SFX 回音**包含用于在效果内调整湿/干燥混合的控件。 由于**Microsoft Spatializer**插件处理晾干路径，因此，我们只为湿路径使用**SFX 回音**。 在**SFX 回音**的 "**检查器**" 窗格上：
* 将 "晾干级别" 属性设置为最低设置（-10000 mB）
* 将 "房间" 属性设置为 "最高" 设置（0 mB）

进行这些更改后， **SFX 回音**的 "**检查器**" 窗格将如下所示：

![SFX 回音属性](images/spatial-audio/sfx-reverb-properties.png)

其他设置控制模拟房间的感觉。 具体而言，**衰减时间**与感知到的空间大小相关。 

## <a name="enable-reverb-on-the-video-playback"></a>启用视频播放时播放回音
在音频源上启用回音的步骤有两个：
* 将**音频源**路由到相应的**组**
* 设置**Microsoft Spatializer**插件以将音频传递到**组**进行处理

在以下步骤中，我们将调整脚本以控制音频路由，并附加**Microsoft Spatializer**插件提供的控制脚本，将数据送入回音。

在 "**四核** **检查器**" 窗格中，单击 "**添加组件**" 并添加 "**房间效果发送级别**脚本"：

![添加发送级别脚本](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> 除非你启用**Microsoft Spatializer**插件的**会议室效果发送级别**功能，否则它不会将任何音频发送回 Unity 音频引擎以进行有效处理。

"**房间效果发送级别**" 组件包括一个图形控件，该控件设置发送到 Unity 音频引擎以进行回音处理的音频级别。 单击并向下拖动曲线，将级别设置为30dB：

![调整回音曲线](images/spatial-audio/adjust-reverb-curve.png)

接下来，取消注释**SpatializeOnOff**脚本中的4个注释行。 该脚本现在将如下所示：
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

取消注释这些行将两个属性添加到脚本的 "**检查器**" 窗格中。 若要设置这些设置，请在 Spatialize 的 "**关闭**组件" 组件的 "**检查器**" 窗格**中：**
* 将 "**房间效果组**" 属性设置为新的 "房间效果" 混音器组
* 将 "**主组**" 属性设置为 "主混音器" 组

完成这些更改后， **Spatialize On**属性将如下所示：

![Spatialize 扩展](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>后续步骤

在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。 现在，在接触应用中的按钮以激活 spatialization 时，该脚本会将视频的音频路由到房间效果组以添加回音。 切换到立体声时，它会将音频路由到主组，并避免添加回音。

已完成适用于 Unity 的 HoloLens 2 空间音频教程。 恭喜你！


