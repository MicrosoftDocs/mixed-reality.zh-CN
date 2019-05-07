# <a name="reading-depth-data"></a><span data-ttu-id="881a5-101">读取深度数据</span><span class="sxs-lookup"><span data-stu-id="881a5-101">Reading Depth Data</span></span>

<span data-ttu-id="881a5-102">需要从设备读取深度数据？</span><span class="sxs-lookup"><span data-stu-id="881a5-102">Need to read depth data from the device?</span></span> <span data-ttu-id="881a5-103">它非常容易 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-103">It's easy!</span></span>

<span data-ttu-id="881a5-104">**内容**</span><span class="sxs-lookup"><span data-stu-id="881a5-104">**Contents**</span></span>  
[<span data-ttu-id="881a5-105">配置设备</span><span class="sxs-lookup"><span data-stu-id="881a5-105">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="881a5-106">访问深度数据</span><span class="sxs-lookup"><span data-stu-id="881a5-106">Acessing Depth Data</span></span>](#Acessing-Depth-Data)  
[<span data-ttu-id="881a5-107">清理</span><span class="sxs-lookup"><span data-stu-id="881a5-107">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="881a5-108">完整源</span><span class="sxs-lookup"><span data-stu-id="881a5-108">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="881a5-109">**下面是我们将使用的函数：**</span><span class="sxs-lookup"><span data-stu-id="881a5-109">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a><span data-ttu-id="881a5-110">配置设备</span><span class="sxs-lookup"><span data-stu-id="881a5-110">Configuring the Device</span></span>

<span data-ttu-id="881a5-111">之后[打开接口]()到 Azure Kinect DK 设备，你将需要配置照相机用于捕获深度数据。</span><span class="sxs-lookup"><span data-stu-id="881a5-111">After [opening an interface]() to the Azure Kinect DK device, you'll need to configure the camera for capturing depth data.</span></span> <span data-ttu-id="881a5-112">只有一项真正需要时配置深度，需要知道这`depth_mode`！</span><span class="sxs-lookup"><span data-stu-id="881a5-112">There's only one item you really need to know about when configuring depth, and that's the `depth_mode`!</span></span>

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="881a5-113">此处`depth_mode`有几个选择 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-113">Here the `depth_mode` has a couple choices!</span></span> <span data-ttu-id="881a5-114">根据我们的应用程序的上下文，我们可以请求深度数据以不同的格式。</span><span class="sxs-lookup"><span data-stu-id="881a5-114">Depending on the context of our application, we can request our depth data in different formats.</span></span>

<span data-ttu-id="881a5-115">你运行时间约束算法深度数据？</span><span class="sxs-lookup"><span data-stu-id="881a5-115">Are you running time constrained algorithms on the depth data?</span></span> <span data-ttu-id="881a5-116">也许 pick 2X2BINNED 模式，因此较少的数据进行操作 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-116">Maybe pick a 2X2BINNED mode so there's less data to operate on!</span></span> <span data-ttu-id="881a5-117">您考虑过多有关什么是最直接出预，而不是什么是关闭和外围中？</span><span class="sxs-lookup"><span data-stu-id="881a5-117">Do you care more about what's far out directly ahead, rather than what's close and in the periphery?</span></span> <span data-ttu-id="881a5-118">使用 NFOV 模式使用窄的视野 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-118">Use a narrow field of view with the NFOV modes!</span></span>
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | <span data-ttu-id="881a5-119">description</span><span class="sxs-lookup"><span data-stu-id="881a5-119">description</span></span> |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|<span data-ttu-id="881a5-120">宽角度视图 (120 x 120)，浅表深度 (0.25-2.21 m)，较高的数据解析 (1024 x 1024)。</span><span class="sxs-lookup"><span data-stu-id="881a5-120">Wide angle view (120x120), shallow depth (0.25-2.21m), high data resolution (1024x1024).</span></span> <span data-ttu-id="881a5-121">具有最大帧速率为 15。</span><span class="sxs-lookup"><span data-stu-id="881a5-121">Has a maximum framerate of 15.</span></span>|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|<span data-ttu-id="881a5-122">宽角度视图 (120 x 120)，浅表深度 (0.25-2.88 m)、 低分辨率 (512 x 512)。</span><span class="sxs-lookup"><span data-stu-id="881a5-122">Wide angle view (120x120), shallow depth (0.25-2.88m), low data resolution (512x512).</span></span>|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|<span data-ttu-id="881a5-123">窄角度视图 (75 x 65)，远端的深度 (0.5-3.86 m)，较高的数据解析 (640 x 576)。</span><span class="sxs-lookup"><span data-stu-id="881a5-123">Narrow angle view (75x65), far depth (0.5-3.86m), high data resolution (640x576).</span></span>|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|<span data-ttu-id="881a5-124">窄角度视图 (75 x 65)，远端的深度 (0.5-5.46 m)、 低分辨率 (320 x 288)。</span><span class="sxs-lookup"><span data-stu-id="881a5-124">Narrow angle view (75x65), far depth (0.5-5.46m), low data resolution (320x288).</span></span>|
|`K4A_DEPTH_MODE_PASSIVE_IR`|<span data-ttu-id="881a5-125">原始源通过红外线 （ir） 照相机 (1024 x 1024)</span><span class="sxs-lookup"><span data-stu-id="881a5-125">Raw feed from the IR camera (1024x1024)</span></span>|
||<span data-ttu-id="881a5-126">将外部具体取决于对象反射率指示范围内提供深度。</span><span class="sxs-lookup"><span data-stu-id="881a5-126">Depth will be provided outside of indicated range depending on object reflectivity.</span></span>|

## <a name="acessing-depth-data"></a><span data-ttu-id="881a5-127">访问深度数据</span><span class="sxs-lookup"><span data-stu-id="881a5-127">Acessing Depth Data</span></span>

![](img/Depth.png)

<span data-ttu-id="881a5-128">当我们捕获帧设备中的时，我们可以使用`k4a_capture_get_depth_image`和`k4a_image_get_buffer`获取原始深度数据 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-128">When we capture a frame from the device, we can use `k4a_capture_get_depth_image` and `k4a_image_get_buffer` to get the raw depth data!</span></span>

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

<span data-ttu-id="881a5-129">无符号 16 位整数，表示从照相机毫米为单位的形式提供深度信息。</span><span class="sxs-lookup"><span data-stu-id="881a5-129">Depth information is provided as an array of unsigned 16 bit integers, representing millimeters from the camera.</span></span> <span data-ttu-id="881a5-130">如果不存在的某一特定像素的深度值，该数组将保存一个零。</span><span class="sxs-lookup"><span data-stu-id="881a5-130">The array will hold a zero if the depth value isn't present for a particular pixel.</span></span>

<span data-ttu-id="881a5-131">在此示例中，我们只需将深度数据转换为灰度图像，并将其文件 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-131">In this example, we'll just convert the depth data into a grayscale image, and save it to file!</span></span>

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a><span data-ttu-id="881a5-132">清理</span><span class="sxs-lookup"><span data-stu-id="881a5-132">Cleaning Up</span></span>

<span data-ttu-id="881a5-133">请注意，若要关闭和释放已分配或获取的所有内容 ！</span><span class="sxs-lookup"><span data-stu-id="881a5-133">Remember to shut down and release everything you've allocated or grabbed!</span></span> <span data-ttu-id="881a5-134">请记住在完成与其和之前获取的另一个帧后应释放帧捕获。</span><span class="sxs-lookup"><span data-stu-id="881a5-134">Remember that frame captures should be freed after you're finished with them and before grabbing another frame.</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="881a5-135">完整源</span><span class="sxs-lookup"><span data-stu-id="881a5-135">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
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

## <a name="next-lab---reading-rgb-datareadcolormd"></a><span data-ttu-id="881a5-136">下一步实验室-[读取 RGB 数据](ReadColor.md)</span><span class="sxs-lookup"><span data-stu-id="881a5-136">Next Lab - [Reading RGB Data](ReadColor.md)</span></span>