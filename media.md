# iota.media
**Description**

This module provides functionalities to display videos and images on notebooks.



* [IotaVideo](#class_IotaVideo)
  * [filepath](IotaVideo_filepath)
  * [display](IotaVideo_display)



- [IotaImage](#class_IotaVideo)
  - [filepath](IotaImage_filepath)
  - [display](IotaImage_display)



## <a id='class_IotaVideo'></a> [class IotaVideo](#class_IotaVideo)

#### <a id='IotaVideo_ctor'></a> [iota.media.**IotaVideo**(filepath)](#IotaVideo_ctor)

*Iota Video class object. This object can be created based on an existing video file or returned by the iota methods that allow to generate a videos (see for example [iota.render.create_video](render.md#create_video) and  [iota.render.Scene.create_video](render.md#scene_create_video))*

**Parameters**

- `filepath` : (str) filepath and name of the video file

**Example**

*Creating an IotaVideo object given a the path to a video file*

```python
my_video = iota.media.IotaVideo(filepath= 'C:/Users/Stephen/MyVideo/my_video.mp4')
```



### Attributes

#### <a id='IotaVideo_filepath'></a>[IotaVideo.filepath](#IotaVideo_filepath)

*Get the path and the name of the video file*

**Returns**

- A **string** with path and name of the video file

**Example**

*Getting the path and the name of the IotaVideo object*

```python
video_file = my_video.filepath
print(video_file)
```

### 

### Methods

#### <a id='IotaVideo_display'></a>[IotaVideo.display(width, height)](#IotaVideo_display)

*Display an  IotaVideo on the working notebook*

**Parameters**

- `width` : (int) width of the video display in pixels (Default: **None**)
- `height` : (int) height of the video display in pixels (Default: **None**)

**Example**

*Displaying an IotaVideo on the working notebook with original dimensions of the video*

```python
my_video.display()
```

*Displaying an IotaVideo on the working notebook with width equal to 600 pixels and keeping the original aspect ratio of the video*

```python
my_video.display(width=600)
```

*Displaying an IotaVideo on the working notebook with width equal to 800 pixels and height equal to 600 pixels*

```python
my_video.display(width=800, height=600)
```



## 

## <a id='class_IotaImage'></a> [class IotaImage](#class_IotaImage)

#### <a id='IotaImage_ctor'></a> [iota.media.**IotaImage**(filepath)](#IotaImage_ctor)

*Iota Image class object. This object can be created based on an existing image file or returned by the iota methods that allow to generate a images (see for example [iota.render.create_screenshots](render.md#create_screenshots) and  [iota.render.Scene.create_screenshots](render.md#scene_create_screenshots))*

**Parameters**

- `filepath` : (str) filepath and name of the image file

**Example**

*Creating an IotaImage object given a the path to a image file*

```python
my_image = iota.media.IotaImage(filepath= 'C:/Users/Stephen/MyImages/my_image.png')
```



### Attributes

#### <a id='IotaImage_filepath'></a>[IotaImage.filepath](#IotaImage_filepath)

*Get the path and the name of the image file*

**Returns**

- A **string** with path and name of the video file

**Example**

*Getting the path and the name of the IotaImage object*

```python
image_file = my_image.filepath
print(image_file)
```



### Methods

#### <a id='IotaImage_display'></a>[IotaImage.display(width, height)](#IotaImage_display)

*Display an  IotaImage on the working notebook*

**Parameters**

- `width` : (int) width of the image display in pixels (Default: **None**)
- `height` : (int) height of the image display in pixels (Default: **None**)

**Example**

*Displaying an IotaImage on the working notebook with original dimensions of the image*

```python
my_image.display()
```

*Displaying an IotaImage on the working notebook with width equal to 600 pixels and keeping the original aspect ratio of the image*

```python
my_image.display(width=600)
```

*Displaying an IotaImage on the working notebook with width equal to 800 pixels and height equal to 600 pixels*

```python
my_image.display(width=800, height=600)
```