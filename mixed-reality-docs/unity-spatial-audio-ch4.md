---
title: 空间音频教程-4。 在运行时启用和禁用空间音频
description: 使用按钮来启用和禁用运行时音频的 spatialization。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 混合现实、unity、教程、hololens2、空间音频
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182864"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>在运行时启用和禁用 spatialization

## <a name="objectives"></a>目标
在此第4章中，你将：
* 添加新脚本以控制游戏对象上的 spatialization
* 从按钮操作驱动 spatialization 控件脚本

## <a name="add-spatialization-control-script"></a>添加 spatialization 控件脚本
右键单击 "**项目**" 窗格并通过选择 " C# **创建-> C#脚本**" 创建新脚本。 将脚本命名为 "SpatializeOnOff"。

![创建脚本](images/spatial-audio/create-script.png)

双击 "**项目**" 窗格中的脚本，在 Visual Studio 中将其打开。 将默认脚本内容替换为以下内容：

> [!NOTE]
> 脚本的几行被注释掉。[第5章](unity-spatial-audio-ch5.md)将取消注释这些行。

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> 若要启用或禁用 spatialization，此脚本只会调整**spatialBlend**属性，使**spatialization**属性保持启用状态。 在此模式下，Unity 仍会应用**卷**曲线。 否则，如果用户在远距离源时禁用了 spatialization，则会听到音量突然增加。 <br> <br>
> 如果希望完全禁用 spatialization，请修改脚本，同时调整**SourceObject**变量的**spatialization**布尔值属性。

## <a name="attach-your-script-and-drive-it-from-the-button"></a>附加脚本，然后从按钮中进行驱动器
在**四**个 "**检查器**" 窗格中，单击 "**添加组件**" 并添加**Spatialize On** script：

![将脚本添加到四个](images/spatial-audio/add-script-to-quad.png)

在四个**Spatialize**的**故障**组件上：
1. 在**层次结构**中查找**PressableButtonHoloLens2-> IconAndText-> TextMeshPro**子对象
2. 将**TextMeshPro** suboject 拖到**Spatialize On Off**组件的**ButtonTextObject**字段上

进行这些更改后，四个**Spatialize**组件的**故障**组件如下所示：

![Spatialize on basic](images/spatial-audio/spatialize-on-off-basic.png)

若要将按钮设置为在释放按钮时调用**Spatialize On On**脚本，请打开**PressableButtonHoloLens2**对象的**检查器**窗格，查找**种不可交互**组件，并执行以下操作：
1. 查找**Events**子节的**OnClick （）** 区域
2. 将**四**个部分从**层次结构**拖至目标对象槽。
3. 从 "操作" 下拉框中选择 " **SpatializeOnOff"。**

进行这些更改之后，**种不可交互**组件将如下所示：

![按钮操作设置](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>后续步骤
在 HoloLens 2 上或在 Unity 编辑器中试用你的应用程序。 在应用程序中，你现在可以触摸按钮以激活和停用视频上的 spatialization。 在 Unity 编辑器中测试时，按空格键并滚动鼠标滚轮以激活手动模拟。 

继续学习[第5章](unity-spatial-audio-ch5.md)，使用回音添加感知到声音源的距离。

