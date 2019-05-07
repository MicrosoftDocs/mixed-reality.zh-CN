# <a name="mixing-color-and-depth-data"></a><span data-ttu-id="6d16e-101">混合使用颜色和深度数据</span><span class="sxs-lookup"><span data-stu-id="6d16e-101">Mixing Color and Depth Data</span></span>

<span data-ttu-id="6d16e-102">从颜色照相机和深度照相机中获取的资源都具有不同的形状和大小 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-102">The resources you get from the color camera and the depth camera have different shapes and sizes!</span></span> <span data-ttu-id="6d16e-103">如果你想要合并两个，没有执行大量操作可以执行以将它们相互对齐。</span><span class="sxs-lookup"><span data-stu-id="6d16e-103">If you want to combine the two, there's a number of things you can do to align them to each other.</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="6d16e-104">**内容：**</span><span class="sxs-lookup"><span data-stu-id="6d16e-104">**Contents:**</span></span>  
[<span data-ttu-id="6d16e-105">配置和设置</span><span class="sxs-lookup"><span data-stu-id="6d16e-105">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="6d16e-106">获取数据</span><span class="sxs-lookup"><span data-stu-id="6d16e-106">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="6d16e-107">对数据进行转换</span><span class="sxs-lookup"><span data-stu-id="6d16e-107">Transforming Data</span></span>](#Transforming-Data)  
[<span data-ttu-id="6d16e-108">从点云中创建网格</span><span class="sxs-lookup"><span data-stu-id="6d16e-108">Creating a Mesh From the Point Cloud</span></span>](#Creating-a-Mesh-From-the-Point-Cloud)  
[<span data-ttu-id="6d16e-109">从深度和颜色创建映像</span><span class="sxs-lookup"><span data-stu-id="6d16e-109">Creating an Image From Depth and Color</span></span>](#Creating-an-Image-From-Depth-and-Color)  
[<span data-ttu-id="6d16e-110">清理</span><span class="sxs-lookup"><span data-stu-id="6d16e-110">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="6d16e-111">完整源</span><span class="sxs-lookup"><span data-stu-id="6d16e-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="6d16e-112">**下面是我们将使用的函数：**</span><span class="sxs-lookup"><span data-stu-id="6d16e-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a><span data-ttu-id="6d16e-113">配置和设置</span><span class="sxs-lookup"><span data-stu-id="6d16e-113">Configuration and Setup</span></span>

<span data-ttu-id="6d16e-114">虽然我们可以在此处使用几乎任何我们想要的配置，我们要坚持较小的解决方法，因为我们将向文件写入未压缩的数据。</span><span class="sxs-lookup"><span data-stu-id="6d16e-114">While we could use just about any configuration we wanted here, we're sticking to smaller resolutions since we'll be writing uncompressed data to file.</span></span> <span data-ttu-id="6d16e-115">检查上从读取文档[颜色照相机]()并[深度照相机]()有关配置详细信息 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-115">Check the documents on reading from the [color camera]() and [depth camera]() for more information about configurations!</span></span>

<span data-ttu-id="6d16e-116">一个额外的元素是`synchronized_images_only`选项 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-116">One additional element here is the `synchronized_images_only` option!</span></span> <span data-ttu-id="6d16e-117">将其设置为`true`指定我们只需要具有这两种颜色的捕获<i>和</i>填充的深度。</span><span class="sxs-lookup"><span data-stu-id="6d16e-117">Setting it to `true` specifies that we only want captures that have both color <i>and</i> depth populated.</span></span> <span data-ttu-id="6d16e-118">如果我们不使用此，从捕获的第几个`k4a_device_get_capture`可能缺少任一深度或彩色图像。</span><span class="sxs-lookup"><span data-stu-id="6d16e-118">If we don't use this, the first few captures from `k4a_device_get_capture` may lack either depth, or color images.</span></span>

```C
// Configure the Kinect to open a stream of 512x512 wide field of view
// 16 bit depth data + 1280x720 BRGA color at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;
config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
config.synchronized_images_only = true;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="6d16e-119">现在，我们有我们的配置信息，我们需要设置将传递到所有我们转换函数的校准对象 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-119">Now that we have our configuration information, we need to set up a calibration object that will be passed into all of our transformation functions!</span></span> <span data-ttu-id="6d16e-120">此对象包含预先计算用于转换与颜色深度空间和 visa 迁移照相机空间坐标的资源。</span><span class="sxs-lookup"><span data-stu-id="6d16e-120">This object contains precalculated resources used for transforming coordinates to and from color camera space to depth space and visa versa.</span></span> <span data-ttu-id="6d16e-121">使其中一个是非常简单：</span><span class="sxs-lookup"><span data-stu-id="6d16e-121">Making one is pretty simple:</span></span>

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a><span data-ttu-id="6d16e-122">获取数据</span><span class="sxs-lookup"><span data-stu-id="6d16e-122">Getting Data</span></span>

<span data-ttu-id="6d16e-123">现在，我们需要获取彩色图像，并深图像 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-123">Now we need to acquire both a color image, and a depth image!</span></span> <span data-ttu-id="6d16e-124">因此，在这里捕获单个帧和从它的相关数据。</span><span class="sxs-lookup"><span data-stu-id="6d16e-124">So here's grabbing a single frame and the relevant data from it.</span></span> <span data-ttu-id="6d16e-125">如果你的映像之一传入回 null，则确保您使用`synchronized_images_only`在配置中 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-125">If one of your images is coming back null, ensure you used `synchronized_images_only` in your configuration!</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Grab image data from the Kinect
k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
int32_t color_w = k4a_image_get_width_pixels (raw_colors);
int32_t color_h = k4a_image_get_height_pixels(raw_colors);
printf("Captured depth image, %dx%d\n", depth_w, depth_h);
printf("Captured rgb image, %dx%d\n", color_w, color_h);
```

## <a name="transforming-data"></a><span data-ttu-id="6d16e-126">对数据进行转换</span><span class="sxs-lookup"><span data-stu-id="6d16e-126">Transforming Data</span></span>

<span data-ttu-id="6d16e-127">`k4a_transform_`函数将转换到另一个图像数据从一个照相机空间 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-127">The `k4a_transform_` functions will transform your image data from one camera space to another!</span></span> <span data-ttu-id="6d16e-128">生成的映像将匹配的失真和解决方法的目标照相机空间，因此关联颜色和深度信息一起轻松地。</span><span class="sxs-lookup"><span data-stu-id="6d16e-128">Resulting images will match the distortion and resolution of the target camera space, so you can correlate color and depth information together easily.</span></span>

<span data-ttu-id="6d16e-129">例如 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-129">For example!</span></span> <span data-ttu-id="6d16e-130">很多情况下您可能希望从照相机，每个颜色的像素将相应深度的彩色图像 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-130">Quite often, you might want a color image from the camera, with a corresponding depth for each color pixel!</span></span> <span data-ttu-id="6d16e-131">为此，会将深度数据转换为颜色照相机空间。</span><span class="sxs-lookup"><span data-stu-id="6d16e-131">For this, you would transform the depth data into color camera space.</span></span>

<span data-ttu-id="6d16e-132">或者，你可能想要从深度相机，创建三维点数据的云并知道每个点是何种颜色。</span><span class="sxs-lookup"><span data-stu-id="6d16e-132">Alternatively, you might want to create a cloud of 3D point data from the depth camera, and know what color each point is.</span></span> <span data-ttu-id="6d16e-133">为此，我们可以将深度数据转换为一个点云和，并将彩色图像转换为深度照相机空间 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-133">For this, we can transform the depth data into a point cloud, and transform the color image into depth camera space!</span></span> <span data-ttu-id="6d16e-134">然后将具有 XYZ 值的缓冲区和相应的缓冲区的颜色。</span><span class="sxs-lookup"><span data-stu-id="6d16e-134">Then you'll have a buffer of XYZ values, and a corresponding buffer of colors.</span></span>

### <a name="depth-data-in-color-space"></a><span data-ttu-id="6d16e-135">颜色空间中的深度数据</span><span class="sxs-lookup"><span data-stu-id="6d16e-135">Depth Data in Color Space</span></span>

<span data-ttu-id="6d16e-136">这将转换深度数据，以匹配颜色照相机的输出 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-136">This transforms depth data to match the color camera's output!</span></span> <span data-ttu-id="6d16e-137">得到的缓冲区将具有彩色图像中每个像素的 16 位深度值。</span><span class="sxs-lookup"><span data-stu-id="6d16e-137">The resulting buffer will have a 16 bit depth value for each pixel in the color image.</span></span>
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a><span data-ttu-id="6d16e-138">创建一个点云和</span><span class="sxs-lookup"><span data-stu-id="6d16e-138">Creating a Point Cloud</span></span>

<span data-ttu-id="6d16e-139">点云也存储在图像资源 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-139">Point clouds are also stored in image resources!</span></span> <span data-ttu-id="6d16e-140">在这里，我们创建格式的映像`K4A_IMAGE_FORMAT_CUSTOM`，因为一个点云和不完全是一个图像。</span><span class="sxs-lookup"><span data-stu-id="6d16e-140">Here, we create an image of format `K4A_IMAGE_FORMAT_CUSTOM`, since a point cloud is not exactly an image.</span></span> <span data-ttu-id="6d16e-141">在图中每个像素将组成 3`int16_t`表示 x y Z 坐标的值，因此我们还正确的大小为指定的。</span><span class="sxs-lookup"><span data-stu-id="6d16e-141">Each 'pixel' in the image will be composed of 3 `int16_t` values representing XYZ coordinates, so we also specify the correct size for that.</span></span>

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a><span data-ttu-id="6d16e-142">颜色深度空间中的数据</span><span class="sxs-lookup"><span data-stu-id="6d16e-142">Color Data in Depth Space</span></span>

<span data-ttu-id="6d16e-143">这将转换颜色数据，以匹配深度照相机的输出 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-143">This transforms color data to match the output from the depth camera!</span></span> <span data-ttu-id="6d16e-144">得到的缓冲区中每个颜色值将对应的深度图像中的值。</span><span class="sxs-lookup"><span data-stu-id="6d16e-144">Each color value from the resulting buffer will correspond with a value from the depth image.</span></span>

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a><span data-ttu-id="6d16e-145">从点云中创建网格</span><span class="sxs-lookup"><span data-stu-id="6d16e-145">Creating a Mesh From the Point Cloud</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="6d16e-146">我们首先将点云数据转换为更熟悉的格式。</span><span class="sxs-lookup"><span data-stu-id="6d16e-146">We'll start by converting the point cloud data into a format that's a little more familiar.</span></span> <span data-ttu-id="6d16e-147">我们将从毫米为单位转换为指标，并将它移动到浮点数。</span><span class="sxs-lookup"><span data-stu-id="6d16e-147">We'll convert it from millimeters to meters, and move it over to floats.</span></span>

```C
// Convert the point cloud from millimeters to meters
float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
for (int32_t i = 0; i < depth_w*depth_h; i++)
{
    vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
    vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
    vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
}
```

<span data-ttu-id="6d16e-148">现在我们将拼结向上这些顶点的人脸的一些信息 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-148">Now we'll stitch up these vertices with some face information!</span></span> <span data-ttu-id="6d16e-149">由于所有内容的布局方式为网格中，这是一个简单的过程的链接上每个单元格的角。</span><span class="sxs-lookup"><span data-stu-id="6d16e-149">Since everything is laid out as a grid, this is a straightforward process of linking up the corners of each cell.</span></span> <span data-ttu-id="6d16e-150">我们要做的唯一附加件事就跳过任何包含空数据的人脸。</span><span class="sxs-lookup"><span data-stu-id="6d16e-150">The only additional thing we're doing here is skipping any face that contains empty data.</span></span> <span data-ttu-id="6d16e-151">如果 Kinect 找不到深度数据的中点云的点，它将其放在 < 0,0,0 > ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-151">If the Kinect couldn't find depth data for a point in the point cloud, it places it at <0,0,0>!</span></span> <span data-ttu-id="6d16e-152">它将转换非常 hedgehog，如果您将它们添加到索引列表。</span><span class="sxs-lookup"><span data-stu-id="6d16e-152">It turns into quite the hedgehog if you add those to the index list.</span></span>

```C
// Make mesh faces as quads across the image. Skip the 
// face if any part of its data is empty.
vector<uint32_t> indices;
for (int32_t y = 0; y < depth_h; y++)
{
    for (int32_t x = 0; x < depth_w; x++)
    {
        int32_t row1 = x +       y * depth_w;
        int32_t row2 = x + (y + 1) * depth_w;

        // If all corners of this quad have depth data
        if (xyz_data[ row1      * 3 + 1] != 0 && 
            xyz_data[(row1 + 1) * 3 + 1] != 0 && 
            xyz_data[ row2      * 3 + 1] != 0 && 
            xyz_data[(row2 + 1) * 3 + 1] != 0)
        {
            // ..then add indices for this quad
            indices.push_back(row2);
            indices.push_back(row2+1);
            indices.push_back(row1+1);
            indices.push_back(row1);
        }
    }
}
```

<span data-ttu-id="6d16e-153">然后我们可以只是此信息写入文件 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-153">Then we can just write this information to file!</span></span> <span data-ttu-id="6d16e-154">我们不会删除未使用的颜色，或由于位置中创建索引，因此我们可以只需传递到目前为止我们已创建的缓冲区中增加了复杂性。</span><span class="sxs-lookup"><span data-stu-id="6d16e-154">We aren't removing unused colors or positions due to added complexity in creating indices, so we can just pass in the buffers we've created so far.</span></span>

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a><span data-ttu-id="6d16e-155">从深度和颜色创建映像</span><span class="sxs-lookup"><span data-stu-id="6d16e-155">Creating an Image From Depth and Color</span></span>

![](img/ColorandDepthSmall.png)

<span data-ttu-id="6d16e-156">使用颜色，这就很容易做到 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-156">With colors, this is much easier to do!</span></span> <span data-ttu-id="6d16e-157">在这里，我们将执行简单淡化为黑色的距离，但无法执行各种各样的有趣的事情，如剪切掉某些深度范围，或在用作照片操作工具中的掩码的 alpha 通道中存储深度 ！</span><span class="sxs-lookup"><span data-stu-id="6d16e-157">Here, we'll do a simple fade to black in the distance, but you could do all sorts of interesting things, like clipping out certain depth ranges, or storing depth in the alpha channel for use as a mask in a photo manipulation tool!</span></span>

```C
// Create an RGB image where we fade color values to black as they recede into the distance
uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
for (int32_t i = 0; i < color_w*color_h; i++)
{
    // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
    float depth = 1 - depth_data[i]/4000.0f;
    depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

    // Fade this pixel, and assign it to our new buffer
    mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
    mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
    mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
}
// Write the image to file
tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
free(mixed_colors);
```

## <a name="cleaning-up"></a><span data-ttu-id="6d16e-158">清理</span><span class="sxs-lookup"><span data-stu-id="6d16e-158">Cleaning Up</span></span>

<span data-ttu-id="6d16e-159">和往常一样，为发布的所有内容完成后:)</span><span class="sxs-lookup"><span data-stu-id="6d16e-159">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(point_cloud_xyz);
k4a_image_release(depth_color_space);
k4a_image_release(color_depth_space);
k4a_image_release(raw_colors);
k4a_image_release(raw_depth);
k4a_capture_release(capture);
k4a_transformation_destroy(transform);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="6d16e-160">完整源</span><span class="sxs-lookup"><span data-stu-id="6d16e-160">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

#include <vector>
using namespace std;

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices);
void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 512x512 wide field of view
    // 16 bit depth data + 1280x720 BRGA color at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;
    config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
    config.synchronized_images_only = true;
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
        printf("Failed to start cameras!\n");

    // Prep data for transforming depth information to color camera space
    k4a_calibration_t calibration;
    if (K4A_FAILED(k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration)))
        printf("Failed to get calibration!\n");
    k4a_transformation_t transform = k4a_transformation_create(&calibration);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    if (K4A_FAILED(k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE)))
        printf("Failed to capture image!\n");

    // Grab image data from the Kinect
    k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
    k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
    int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
    int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
    int32_t color_w = k4a_image_get_width_pixels (raw_colors);
    int32_t color_h = k4a_image_get_height_pixels(raw_colors);
    printf("Captured depth image, %dx%d\n", depth_w, depth_h);
    printf("Captured rgb image, %dx%d\n", color_w, color_h);

    // Transform the raw depth data into color camera space
    k4a_image_t depth_color_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_DEPTH16, color_w, color_h, color_w * sizeof(uint16_t), &depth_color_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

    // Get the point cloud
    k4a_image_t point_cloud_xyz;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_CUSTOM, depth_w, depth_h, depth_w * 3 * sizeof(int16_t), &point_cloud_xyz)))
        printf("Failed to create a point cloud image resource!\n");
    k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

    // Transform the raw color data into depth camera space
    k4a_image_t color_depth_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_COLOR_BGRA32, depth_w, depth_h, depth_w * sizeof(uint32_t), &color_depth_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

    // Get access to the raw color and point cloud data.
    uint8_t  *raw_color_data = static_cast     <uint8_t  *>(k4a_image_get_buffer(raw_colors));
    uint8_t  *color_data     = static_cast     <uint8_t  *>(k4a_image_get_buffer(color_depth_space));
    uint16_t *depth_data     = reinterpret_cast<uint16_t *>(k4a_image_get_buffer(depth_color_space));
    int16_t  *xyz_data       = reinterpret_cast<int16_t  *>(k4a_image_get_buffer(point_cloud_xyz));

    // Turn the point cloud into a mesh, and write it to file!

    // Convert the point cloud from millimeters to meters
    float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
    for (int32_t i = 0; i < depth_w*depth_h; i++)
    {
        vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
        vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
        vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
    }

    // Make mesh faces as quads across the image. Skip the
    // face if any part of its data is empty.
    vector<uint32_t> indices;
    for (int32_t y = 0; y < depth_h; y++)
    {
        for (int32_t x = 0; x < depth_w; x++)
        {
            int32_t row1 = x +       y * depth_w;
            int32_t row2 = x + (y + 1) * depth_w;

            // If all corners of this quad have depth data
            if (xyz_data[ row1      * 3 + 1] != 0 && 
                xyz_data[(row1 + 1) * 3 + 1] != 0 && 
                xyz_data[ row2      * 3 + 1] != 0 && 
                xyz_data[(row2 + 1) * 3 + 1] != 0)
            {
                // ..then add indices for this quad
                indices.push_back(row2);
                indices.push_back(row2+1);
                indices.push_back(row1+1);
                indices.push_back(row1);
            }
        }
    }

    // Write geometry data to a .PLY, and clean up
    ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, static_cast<uint32_t>(indices.size()) / 4, &indices[0]);
    free(vertex_positions);
    
    // Create an RGB image where we fade color values to black as they recede into the distance
    uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
    for (int32_t i = 0; i < color_w*color_h; i++)
    {
        // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
        float depth = 1 - depth_data[i]/4000.0f;
        depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

        // Fade this pixel, and assign it to our new buffer
        mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
        mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
        mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
    }
    // Write the image to file
    tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
    free(mixed_colors);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(point_cloud_xyz);
    k4a_image_release(depth_color_space);
    k4a_image_release(color_depth_space);
    k4a_image_release(raw_colors);
    k4a_image_release(raw_depth);
    k4a_capture_release(capture);
    k4a_transformation_destroy(transform);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices)
{
    FILE *fp = nullptr;
    fopen_s(&fp, filename, "w");

    // Write the .PLY header information
    fprintf(fp, "ply\nformat ascii 1.0\n");
    fprintf(fp, "element vertex %d\nproperty float x\nproperty float y\nproperty float z\nproperty uchar red\nproperty uchar green\nproperty uchar blue\n", vertex_count);
    fprintf(fp, "element face %d\nproperty list uchar int vertex_index\n", index_quad_count);
    fprintf(fp, "end_header\n");

    // Write each vertex with color information!
    for (uint32_t i = 0; i < vertex_count; i++)
    {
        fprintf(fp, "%g %g %g %d %d %d\n", 
            vertex_positions[i*3    ],
            vertex_positions[i*3 + 1],
            vertex_positions[i*3 + 2], 
            vertex_colors_bgra[i*4 + 2], 
            vertex_colors_bgra[i*4 + 1], 
            vertex_colors_bgra[i*4    ]);
    }

    // Write faces as quads.
    for (size_t i = 0; i < index_quad_count; i++)
    {
        fprintf(fp, "4 %d %d %d %d\n", quad_indices[i*4], quad_indices[i*4 + 1], quad_indices[i*4 + 2], quad_indices[i*4 + 3]);
    }
    fclose(fp);
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width%256, (uint8_t)(width/256), height%256, (uint8_t)(height/256), file_channels*8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---accessing-the-imuusingimumd"></a><span data-ttu-id="6d16e-161">下一步实验室-[访问 IMU](UsingIMU.md)</span><span class="sxs-lookup"><span data-stu-id="6d16e-161">Next Lab - [Accessing the IMU](UsingIMU.md)</span></span>