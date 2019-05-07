# <a name="accessing-the-imu"></a><span data-ttu-id="76a55-101">访问 IMU</span><span class="sxs-lookup"><span data-stu-id="76a55-101">Accessing the IMU</span></span>

<span data-ttu-id="76a55-102">Azure Kinect DK 包含惯性度量单位 (IMU) ！</span><span class="sxs-lookup"><span data-stu-id="76a55-102">Azure Kinect DK contains an Inertial Measurement Unit (IMU)!</span></span> <span data-ttu-id="76a55-103">这可用于帮助确定动作和方向的设备在捕获过程。</span><span class="sxs-lookup"><span data-stu-id="76a55-103">This can be useful for helping to determine motion and orientation of the device during capture.</span></span> <span data-ttu-id="76a55-104">尤其是如果你的设备不是静态的 ！</span><span class="sxs-lookup"><span data-stu-id="76a55-104">Especially if you device isn't stationary!</span></span>

<span data-ttu-id="76a55-105">**内容：**</span><span class="sxs-lookup"><span data-stu-id="76a55-105">**Contents:**</span></span>  
[<span data-ttu-id="76a55-106">配置和设置</span><span class="sxs-lookup"><span data-stu-id="76a55-106">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="76a55-107">获取数据</span><span class="sxs-lookup"><span data-stu-id="76a55-107">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="76a55-108">清理</span><span class="sxs-lookup"><span data-stu-id="76a55-108">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="76a55-109">完整源</span><span class="sxs-lookup"><span data-stu-id="76a55-109">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="76a55-110">**下面是我们将使用的函数：**</span><span class="sxs-lookup"><span data-stu-id="76a55-110">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-imu)  
[`k4a_device_stop_imu()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-imu)  
[`k4a_device_get_imu_sample()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-imu-sample)  

## <a name="configuration-and-setup"></a><span data-ttu-id="76a55-111">配置和设置</span><span class="sxs-lookup"><span data-stu-id="76a55-111">Configuration and Setup</span></span>

<span data-ttu-id="76a55-112">此处的配置是相当简单 ！</span><span class="sxs-lookup"><span data-stu-id="76a55-112">Configuration here is pretty simple!</span></span> <span data-ttu-id="76a55-113">没有您需要指定的项 IMU 的设备配置中采样的工作，但你将需要调用`k4a_device_start_cameras`它将在之前 ！</span><span class="sxs-lookup"><span data-stu-id="76a55-113">There are no items you need to specify the in the device configuration for IMU sampling to work, but you will need to call `k4a_device_start_cameras` before it'll work!</span></span> <span data-ttu-id="76a55-114">相反，将调用`k4a_device_start_imu`后启动相机。</span><span class="sxs-lookup"><span data-stu-id="76a55-114">Instead, you'll make a call to `k4a_device_start_imu` after starting the cameras.</span></span>

```C
// Cameras need to be 'started' even if all we want is the IMU
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
k4a_device_start_cameras(device, &config);

// Start up the IMU sensors
k4a_device_start_imu(device);
```

## <a name="getting-data"></a><span data-ttu-id="76a55-115">获取数据</span><span class="sxs-lookup"><span data-stu-id="76a55-115">Getting Data</span></span>

<span data-ttu-id="76a55-116">![IMU 示例应用程序图像](img/IMU.png "下面是我们要生成作为示例 ！")</span><span class="sxs-lookup"><span data-stu-id="76a55-116">![IMU sample app image](img/IMU.png "Here's what we'll build as an example!")</span></span>

<span data-ttu-id="76a55-117">IMU 提供数据的增长 1.6 kHz ！</span><span class="sxs-lookup"><span data-stu-id="76a55-117">The IMU provides data at a rate of 1.6kHz!</span></span> <span data-ttu-id="76a55-118">这是很多数据，，这意味着，如果您仅查找在它每次深度/颜色帧是可用，可能会有很多队列等待你 IMU 示例 ！</span><span class="sxs-lookup"><span data-stu-id="76a55-118">That's a lot of data, and this means that if you're only looking at it each time a depth/color frame is available, you'll likely have quite a queue of IMU samples waiting for you!</span></span> <span data-ttu-id="76a55-119">请注意，此数据并不方向或位置，而不是，当前应用于设备的力的度量值。</span><span class="sxs-lookup"><span data-stu-id="76a55-119">Note that this data is not an orientation or position, but rather, a measure of the force currently applied to the device.</span></span>

<span data-ttu-id="76a55-120">我们可以抓住示例并将其从队列删除通过调用`k4a_device_get_imu_sample`具有的 0 毫秒的超时值。</span><span class="sxs-lookup"><span data-stu-id="76a55-120">We can grab a sample and remove it from the queue by calling `k4a_device_get_imu_sample` with a timeout of 0 milliseconds.</span></span> <span data-ttu-id="76a55-121">它将返回`K4A_WAIT_RESULT_SUCCEEDED`，只要它有一个可用的示例 ！</span><span class="sxs-lookup"><span data-stu-id="76a55-121">It'll return `K4A_WAIT_RESULT_SUCCEEDED` as long as it has a sample available!</span></span>

<span data-ttu-id="76a55-122">下面是求和当前在队列中的所有示例和打印平均值的示例。</span><span class="sxs-lookup"><span data-stu-id="76a55-122">Here's an example of summing all the samples currently in the queue, and printing the average.</span></span> 

```C
k4a_float3_t gyro_sum  = {0};
k4a_float3_t acc_sum   = {0};
int32_t      sum_count = 0;

// Sum the current queue of IMU samples
k4a_imu_sample_t sample;
while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
{
    gyro_sum.xyz = { 
        gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
        gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
        gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
    acc_sum.xyz = { 
        acc_sum.xyz.x + sample.acc_sample.xyz.x,  
        acc_sum.xyz.y + sample.acc_sample.xyz.y,  
        acc_sum.xyz.z + sample.acc_sample.xyz.z };
    sum_count += 1;
    samples   += 1;
}

// If we got any samples, print out their average!
if (sum_count > 0)
{
    k4a_float3_t gyro_avg = {
        gyro_sum.xyz.x / sum_count,
        gyro_sum.xyz.y / sum_count,
        gyro_sum.xyz.z / sum_count };
    k4a_float3_t acc_avg = {
        acc_sum.xyz.x / sum_count,
        acc_sum.xyz.y / sum_count,
        acc_sum.xyz.z / sum_count };

    printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
    printf("<%6.2f, %6.2f, %6.2f>", acc_avg.xyz.x, acc_avg.xyz.y, acc_avg.xyz.z);

    // Write backspaces so we'll overwrite this line next time
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
    printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
}
```

## <a name="cleaning-up"></a><span data-ttu-id="76a55-123">清理</span><span class="sxs-lookup"><span data-stu-id="76a55-123">Cleaning Up</span></span>

<span data-ttu-id="76a55-124">和往常一样，为发布的所有内容完成后:)</span><span class="sxs-lookup"><span data-stu-id="76a55-124">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_device_stop_imu(device);
k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="76a55-125">完整源</span><span class="sxs-lookup"><span data-stu-id="76a55-125">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Cameras need to be 'started' even if all we want is the IMU
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    k4a_device_start_cameras(device, &config);

    // Start up the IMU sensors
    k4a_device_start_imu(device);

    // Display 10,000 samples as fast as they arrive
    printf("Sampling 10,000 times.\n");
    printf("Gyroscope radians/s:       Accelerometer meters/s^2:\n");
    int32_t samples = 0;
    while (samples < 10000)
    {
        k4a_float3_t gyro_sum  = {0};
        k4a_float3_t accel_sum = {0};
        int32_t      sum_count = 0;

        // Sum the current queue of IMU samples
        k4a_imu_sample_t sample;
        while (k4a_device_get_imu_sample(device, &sample, 0) == K4A_WAIT_RESULT_SUCCEEDED)
        {
            gyro_sum.xyz = { 
                gyro_sum.xyz.x + sample.gyro_sample.xyz.x, 
                gyro_sum.xyz.y + sample.gyro_sample.xyz.y, 
                gyro_sum.xyz.z + sample.gyro_sample.xyz.z };
            accel_sum.xyz = { 
                accel_sum.xyz.x + sample.acc_sample.xyz.x,  
                accel_sum.xyz.y + sample.acc_sample.xyz.y,  
                accel_sum.xyz.z + sample.acc_sample.xyz.z };
            sum_count += 1;
            samples   += 1;
        }

        // If we got any samples this loop, print out their average!
        if (sum_count > 0)
        {
            k4a_float3_t gyro_avg = {
                gyro_sum.xyz.x / sum_count,
                gyro_sum.xyz.y / sum_count,
                gyro_sum.xyz.z / sum_count };
            k4a_float3_t accel_avg = {
                accel_sum.xyz.x / sum_count,
                accel_sum.xyz.y / sum_count,
                accel_sum.xyz.z / sum_count };

            printf("<%6.2f, %6.2f, %6.2f>   ", gyro_avg.xyz.x, gyro_avg.xyz.y, gyro_avg.xyz.z);
            printf("<%6.2f, %6.2f, %6.2f>", accel_avg.xyz.x, accel_avg.xyz.y, accel_avg.xyz.z);

            // Write backspaces so we'll overwrite this line next time
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
            printf("\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b");
        }
    }
    printf("\nShutting down.\n");

    // Release all allocated resources, and shut down the Kinect
    k4a_device_stop_imu(device);
    k4a_device_stop_cameras(device);
    k4a_device_close(device);
}
```