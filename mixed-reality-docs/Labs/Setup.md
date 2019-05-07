# <a name="setting-up"></a>设置

开始使用 Azure Kinect DK API？ 不要再找了 ！ 本文档将帮助你启动并运行具有访问权限在设备 ！

首先，下载并安装[Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK)从 Github。

**内容**  
[标头](#Headers)  
[查找 Kinect 设备](#Finding-a-Kinect-Device)  
[启动相机](#Starting-the-Cameras)  
[错误处理](#Error-Handling)  
[完整源](#Full-Source)  

**下面是我们将使用的函数：**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>标头
你将需要的只有一个标头，并位于 k4a.h ！ 请确保你的编译器选择的设置与 SDK 的库并包括文件夹。 您还需要链接的 k4a.lib 和 k4a.dll 文件。
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>查找 Kinect 设备

![](img/Serial.png)

多个 Azure Kinect DK 设备可以连接到您的计算机 ！ 我们首先将首先查找出多少，或任何连接的所有使用[ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)函数。 此函数应立即，无需任何其他设置 ！

```C
uint32_t count = k4a_device_get_installed_count();
```

一旦您确定了那里实际设备连接到计算机，您可以打开使用其[ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)。 你可以提供索引所需的设备若要打开，或您可以只使用[ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT)的第一个。

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
作为 k4a API 中的大多数内容时打开某些内容，应还将其关闭时它已完成 ！ 正在关闭，请记住以调用[ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)。

```C
k4a_device_close(device);
```

打开设备后，我们可以使一个非常简单的测试以确保一切顺利。 因此，让我们读取设备的序列号 ！

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

## <a name="starting-the-cameras"></a>启动相机

一旦您打开了设备，将需要配置与相机[ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t)对象 ！ 照相机配置具有多个不同的选项，并将需要选择最适合自己方案的设置。

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

有关配置详细信息__颜色__照相机[签出此文档]()！  
有关配置详细信息__深度__照相机[签出此文档]()！

## <a name="error-handling"></a>错误处理

为了简洁起见并简单明了，我们不再显示一些内联示例中的错误处理。 但是，错误处理始终是重要的 ！ 许多函数将返回一个常规的成功/失败类型[ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t)，或者的更具体的变体的详细信息，如[ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t)。 请务必检查以查看哪些错误消息，你可能希望从其看到的文档或特定函数的 intellisense ！

错误类型，以及另外，还有[ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED)并[ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED)宏，您可以使用它们。 因此而不是只需打开 k4a 设备，我们可能会防止它像这样：

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>完整源

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>下一步实验室-[读取深度数据](ReadDepth.md)
