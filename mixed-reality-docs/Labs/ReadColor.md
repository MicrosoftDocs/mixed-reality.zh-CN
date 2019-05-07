# <a name="reading-rgb-data"></a><span data-ttu-id="279fd-101">读取 RGB 数据</span><span class="sxs-lookup"><span data-stu-id="279fd-101">Reading RGB Data</span></span>

<span data-ttu-id="279fd-102">**内容**</span><span class="sxs-lookup"><span data-stu-id="279fd-102">**Contents**</span></span>  
[<span data-ttu-id="279fd-103">配置设备</span><span class="sxs-lookup"><span data-stu-id="279fd-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="279fd-104">获取颜色帧</span><span class="sxs-lookup"><span data-stu-id="279fd-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="279fd-105">清理</span><span class="sxs-lookup"><span data-stu-id="279fd-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="279fd-106">完整源</span><span class="sxs-lookup"><span data-stu-id="279fd-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="279fd-107">**下面是我们将使用的函数：**</span><span class="sxs-lookup"><span data-stu-id="279fd-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="279fd-108">配置设备</span><span class="sxs-lookup"><span data-stu-id="279fd-108">Configuring the Device</span></span>

<span data-ttu-id="279fd-109">之后[打开 k4a 设备]()，我们将需要将摄像机设置为获取颜色数据 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="279fd-110">有很多的选项，因此我们将逐一介绍它们。</span><span class="sxs-lookup"><span data-stu-id="279fd-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="279fd-111">下面是一个快速示例的如下所示启动真正基本颜色照相机。</span><span class="sxs-lookup"><span data-stu-id="279fd-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="279fd-112">`color_format`使我们能够说我们希望我们存储的图像缓冲区中的颜色信息 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="279fd-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` 将 32 位 / 像素，存储为 8 位用于蓝色、 绿色、 红色和 Alpha。</span><span class="sxs-lookup"><span data-stu-id="279fd-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="279fd-114">我们在由于其方便起见，示例中使用此格式，但如果你想要的内存使用情况的 concious，其他格式可能是卓越的选择 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="279fd-115">颜色数据将采用[运动 JPEG 格式](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="279fd-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="279fd-116">[YUV](https://en.wikipedia.org/wiki/YUV)颜色空间 4:2:0 格式，NV12，只能以 720p 分辨率。</span><span class="sxs-lookup"><span data-stu-id="279fd-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="279fd-117">[YUV](https://en.wikipedia.org/wiki/YUV)颜色空间 4:2:2 格式，YUY2，只能以 720p 分辨率。</span><span class="sxs-lookup"><span data-stu-id="279fd-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="279fd-118">原始颜色数据，32 位 / 像素，序号为蓝色、 绿色、 红色、 Alpha</span><span class="sxs-lookup"><span data-stu-id="279fd-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="279fd-119">写入时自己 YUV 转换开销可能很简单，快速、 可靠的库的 YUV 转换，请参阅[libyuv](https://chromium.googlesource.com/libyuv/libyuv/)。</span><span class="sxs-lookup"><span data-stu-id="279fd-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="279fd-120">`color_resolution`还具有几个选项 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="279fd-121">解决方法</span><span class="sxs-lookup"><span data-stu-id="279fd-121">resolution</span></span>|<span data-ttu-id="279fd-122">方面</span><span class="sxs-lookup"><span data-stu-id="279fd-122">aspect</span></span>|<span data-ttu-id="279fd-123">视野</span><span class="sxs-lookup"><span data-stu-id="279fd-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="279fd-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="279fd-124">1280 x 720</span></span>  | <span data-ttu-id="279fd-125">16:9</span><span class="sxs-lookup"><span data-stu-id="279fd-125">16:9</span></span> | <span data-ttu-id="279fd-126">90x59</span><span class="sxs-lookup"><span data-stu-id="279fd-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="279fd-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="279fd-127">1920 x 1080</span></span> | <span data-ttu-id="279fd-128">16:9</span><span class="sxs-lookup"><span data-stu-id="279fd-128">16:9</span></span> | <span data-ttu-id="279fd-129">90x59</span><span class="sxs-lookup"><span data-stu-id="279fd-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="279fd-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="279fd-130">2560 x 1440</span></span> | <span data-ttu-id="279fd-131">16:9</span><span class="sxs-lookup"><span data-stu-id="279fd-131">16:9</span></span> | <span data-ttu-id="279fd-132">90x59</span><span class="sxs-lookup"><span data-stu-id="279fd-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="279fd-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="279fd-133">3840 x 2160</span></span> | <span data-ttu-id="279fd-134">16:9</span><span class="sxs-lookup"><span data-stu-id="279fd-134">16:9</span></span> | <span data-ttu-id="279fd-135">90x59</span><span class="sxs-lookup"><span data-stu-id="279fd-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="279fd-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="279fd-136">2048 x 1536</span></span> | <span data-ttu-id="279fd-137">4:3</span><span class="sxs-lookup"><span data-stu-id="279fd-137">4:3</span></span>  | <span data-ttu-id="279fd-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="279fd-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="279fd-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="279fd-139">4096 x 3072</span></span> | <span data-ttu-id="279fd-140">4:3</span><span class="sxs-lookup"><span data-stu-id="279fd-140">4:3</span></span>  | <span data-ttu-id="279fd-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="279fd-141">90x74.3</span></span> | <span data-ttu-id="279fd-142">最大帧速率为 15。</span><span class="sxs-lookup"><span data-stu-id="279fd-142">Max framerate 15.</span></span>

<span data-ttu-id="279fd-143">当然，`camera_fps`也。</span><span class="sxs-lookup"><span data-stu-id="279fd-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="279fd-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="279fd-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="279fd-145">获取颜色帧</span><span class="sxs-lookup"><span data-stu-id="279fd-145">Getting a Color Frame</span></span>

<span data-ttu-id="279fd-146">获取颜色范围和深度帧的数据是一个非常类似的过程 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="279fd-147">我们首先从该设备，获取一个捕获然后我们提取彩色图像，然后我们提取原始数据从该映像。</span><span class="sxs-lookup"><span data-stu-id="279fd-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

<span data-ttu-id="279fd-148">数据现在存储在`colorDataBRGA`取决于我们在配置中指示的格式。</span><span class="sxs-lookup"><span data-stu-id="279fd-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="279fd-149">由于我们的要求`K4A_IMAGE_FORMAT_COLOR_BGRA32`，我们有一个数组，完整的 32 位颜色值存储在 BGRA ！</span><span class="sxs-lookup"><span data-stu-id="279fd-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="279fd-150">在本例中为.tga 文件存储颜色 BGR 顺序已 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="279fd-151">并且，由于我们正在保存函数可以跳过用这些自变量的 alpha 通道，我们只是可以将图像数据按原样传递 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="279fd-152">清理</span><span class="sxs-lookup"><span data-stu-id="279fd-152">Cleaning Up</span></span>

<span data-ttu-id="279fd-153">并始终记得用完时释放资源 ！</span><span class="sxs-lookup"><span data-stu-id="279fd-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="279fd-154">完整源</span><span class="sxs-lookup"><span data-stu-id="279fd-154">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="279fd-155">下一步实验室-[混合使用颜色和深度数据](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="279fd-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>