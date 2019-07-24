# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>针对 HoloLens 2 的 Galaxy 资源管理器创建

欢迎使用更新 HoloLens 2 的 Galaxy 资源管理器的方法。 [Galaxy 资源管理器](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy 资源管理器")最初是通过共享你的想法计划开发的, 它是一种用于 HoloLens (第一代) 的开源应用程序, 这是许多人的第一种混合现实体验之一。 现在我们正在更新它, 以获得[HoloLens 2 的全新功能](https://www.microsoft.com/hololens/hardware)。

作为 Microsoft 混合现实工作室 (1) 之一, 我们通常会开发商业级解决方案, 并在整个创意和开发过程中在目标平台上开发 & 测试。 现在, 我们有了一种独特的情况, 即目前尚不具有对 HoloLens 2 设备的访问权限, 但很高兴能够开始更新到 Galaxy 资源管理器。 我们将使用框架和工具 (如[MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) 来着手此项目, 因为我们和社区都可以使用这些框架和工具。

正如原始 Galaxy 资源管理器, 我们将在[GitHub 上提供项目](https://github.com/Microsoft/GalaxyExplorer), 以确保社区具有完全访问权限。 我们还将在这里记录我们的旅程, 其中介绍了我们 undertook 从 MRTK v1 迁移到 MRTK v2 的方法, 我们如何根据 HoloLens 2 中提供的新功能增强体验, 以及我们如何确保 Galaxy 资源管理器保持多平台体验。 因此, 无论你是在 HoloLens (第一代)、HoloLens 2、Windows Mixed Reality 耳机还是 Windows 10 桌面上观看 Galaxy 资源管理器, 我们都希望确保你有一个沉浸式体验, 并尽可能地欣赏旅程!

此页面将在我们完成项目的过程中展开, 并链接到更详细的文章、代码、设计项目、附加的 MRTK v2 文档等, 为你提供内幕的项目。



(1) Microsoft 混合现实工作室团队-位于美洲、欧洲和亚太地区, 是用户体验设计、全息计算、AR/VR 技术和三维开发方面的专家;包括3D 资产创建、DirectX、Unity 和 Unreal。 我们帮助构想预期的先期备货、设计、构建和交付解决方案, 同时使客户能够在其组织中创造实实在在的影响。 录音室与超过22000个 Microsoft 服务专业人员密切合作, 以实现企业应用程序集成、采用、操作和支持。
