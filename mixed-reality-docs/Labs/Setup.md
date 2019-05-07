# <a name="setting-up"></a><span data-ttu-id="6f514-101">设置</span><span class="sxs-lookup"><span data-stu-id="6f514-101">Setting Up</span></span>

<span data-ttu-id="6f514-102">开始使用 Azure Kinect DK API？</span><span class="sxs-lookup"><span data-stu-id="6f514-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="6f514-103">不要再找了 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-103">Look no further!</span></span> <span data-ttu-id="6f514-104">本文档将帮助你启动并运行具有访问权限在设备 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="6f514-105">首先，下载并安装[Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK)从 Github。</span><span class="sxs-lookup"><span data-stu-id="6f514-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="6f514-106">**内容**</span><span class="sxs-lookup"><span data-stu-id="6f514-106">**Contents**</span></span>  
[<span data-ttu-id="6f514-107">标头</span><span class="sxs-lookup"><span data-stu-id="6f514-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="6f514-108">查找 Kinect 设备</span><span class="sxs-lookup"><span data-stu-id="6f514-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="6f514-109">启动相机</span><span class="sxs-lookup"><span data-stu-id="6f514-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="6f514-110">错误处理</span><span class="sxs-lookup"><span data-stu-id="6f514-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="6f514-111">完整源</span><span class="sxs-lookup"><span data-stu-id="6f514-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="6f514-112">**下面是我们将使用的函数：**</span><span class="sxs-lookup"><span data-stu-id="6f514-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="6f514-113">标头</span><span class="sxs-lookup"><span data-stu-id="6f514-113">Headers</span></span>
<span data-ttu-id="6f514-114">你将需要的只有一个标头，并位于 k4a.h ！</span><span class="sxs-lookup"><span data-stu-id="6f514-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="6f514-115">请确保你的编译器选择的设置与 SDK 的库并包括文件夹。</span><span class="sxs-lookup"><span data-stu-id="6f514-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="6f514-116">您还需要链接的 k4a.lib 和 k4a.dll 文件。</span><span class="sxs-lookup"><span data-stu-id="6f514-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="6f514-117">查找 Kinect 设备</span><span class="sxs-lookup"><span data-stu-id="6f514-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="6f514-118">多个 Azure Kinect DK 设备可以连接到您的计算机 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="6f514-119">我们首先将首先查找出多少，或任何连接的所有使用[ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)函数。</span><span class="sxs-lookup"><span data-stu-id="6f514-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="6f514-120">此函数应立即，无需任何其他设置 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="6f514-121">一旦您确定了那里实际设备连接到计算机，您可以打开使用其[ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)。</span><span class="sxs-lookup"><span data-stu-id="6f514-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="6f514-122">你可以提供索引所需的设备若要打开，或您可以只使用[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT)的第一个。</span><span class="sxs-lookup"><span data-stu-id="6f514-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="6f514-123">作为 k4a API 中的大多数内容时打开某些内容，应还将其关闭时它已完成 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="6f514-124">正在关闭，请记住以调用[ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)。</span><span class="sxs-lookup"><span data-stu-id="6f514-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="6f514-125">打开设备后，我们可以使一个非常简单的测试以确保一切顺利。</span><span class="sxs-lookup"><span data-stu-id="6f514-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="6f514-126">因此，让我们读取设备的序列号 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="6f514-127">启动相机</span><span class="sxs-lookup"><span data-stu-id="6f514-127">Starting the Cameras</span></span>

<span data-ttu-id="6f514-128">一旦您打开了设备，将需要配置与相机[ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)对象 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="6f514-129">照相机配置具有多个不同的选项，并将需要选择最适合自己方案的设置。</span><span class="sxs-lookup"><span data-stu-id="6f514-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="6f514-130">有关配置详细信息__颜色__照相机[签出此文档]()！</span><span class="sxs-lookup"><span data-stu-id="6f514-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="6f514-131">有关配置详细信息__深度__照相机[签出此文档]()！</span><span class="sxs-lookup"><span data-stu-id="6f514-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="6f514-132">错误处理</span><span class="sxs-lookup"><span data-stu-id="6f514-132">Error Handling</span></span>

<span data-ttu-id="6f514-133">为了简洁起见并简单明了，我们不再显示一些内联示例中的错误处理。</span><span class="sxs-lookup"><span data-stu-id="6f514-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="6f514-134">但是，错误处理始终是重要的 ！</span><span class="sxs-lookup"><span data-stu-id="6f514-134">However, error handling is always important!</span></span> <span data-ttu-id="6f514-135">许多函数将返回一个常规的成功/失败类型[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)，或者的更具体的变体的详细信息，如[ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)。</span><span class="sxs-lookup"><span data-stu-id="6f514-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="6f514-136">请务必检查以查看哪些错误消息，你可能希望从其看到的文档或特定函数的 intellisense ！</span><span class="sxs-lookup"><span data-stu-id="6f514-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="6f514-137">错误类型，以及另外，还有[ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)并[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)宏，您可以使用它们。</span><span class="sxs-lookup"><span data-stu-id="6f514-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="6f514-138">因此而不是只需打开 k4a 设备，我们可能会防止它像这样：</span><span class="sxs-lookup"><span data-stu-id="6f514-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="6f514-139">完整源</span><span class="sxs-lookup"><span data-stu-id="6f514-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="6f514-140">下一步实验室-[读取深度数据](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="6f514-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
