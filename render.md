# iota.render
**Description**

This module provides functionalities to create scenes to render in 3D the data in simulation datasets. It also provides methods to create screenshots and videos from 3D render of the scenes.



* [Scene](#class_Scene)
  * [set_view_x](#Scene_set_view_x)
  * [set_view_z](#Scene_set_view_y)
  * [set_view_z](#Scene_set_view_z)
  * [set_view_iso](#Scene_set_view_iso)
  * [set_result](#Scene_set_result)
  * [set_mesh](#Scene_set_mesh)
  * [display](#Scene_display)
  * [export](#Scene_export)
  * [create_screenshots](#Scene_create_screenshot)
  * [create_video](Scene_create_video)
* [MeshMode](#class_MeshMode)
  * [SOLID](#class_MeshMode)
  * [WIREFRAME](#class_MeshMode)
  * [WIREFRAME2](#class_MeshMode)
* [VideoFormat](#class_videoformat)
  * [MPEG](#class_VideoFormat)
  * [AVI](#class_VideoFormat)
  * [MP4](#class_VideoFormat)
  * [WEBM](#class_VideoFormat)

- [display](#display)
- [create_screenshots](#create_screenshots)
- [create_video](#create_video)



## <a id='class_Scene'></a> [class Scene](#class_Scene)

#### <a id='Scene_ctor'></a> [iota.render.**Scene**(dataset, pac_file)](#Scene_ctor)

*Scene class object. This object contains the settings of a scene to generate a 3D render*

**Parameters**

- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to use as the base to create a scene with default settings (Default: **None**)
- `pac_file`: (str) path and file name to a .pac file that contains the scene settings to be loaded (Default: **None**)

**Example**

*Creating a scene with the default settings based on a fluent dataset*

```python
my_dataset = iota.dataset.load_fluent(case_files=['C:/Users/Stephen/Myimulations/myfluentsimulation.cas.gz'], data_files=['C:/Users/Stephen/Myimulations/myfluentsimulation.dat.gz'])
my_scene = iota.render.Scene(dataset=my_dataset)
print(my_scene)
```

*Creating a scene based on the settings stored in a pac file*

```python
my_scene = iota.render.Scene(pac_file='C:/Users/Stephen/MyScenes/myscene_settings.pac')
print(my_scene)
```



### Methods

#### <a id='Scene_display'></a>[Scene.display(step, width, height)](#Scene_display)

*Display a scene as 3D interactive render on the working notebook*

**Parameters**

- `step`: (int) index of timestep for the scene (Default: **0**)
- `width` : (int) width of the display of the scene in pixels (Default: **800**)
- `height` : (int) height of the video display of the scene in pixels (Default: **600**)

**Example**

*Displaying a scene*

```python
my_scene.display()
```

*Displaying a scene for the 5th step of the scene dataset and with a with equal to 1000 pixels and a height equal to 800 pixels*

```python
my_scene.display(step = 4, width=1000, height=800)
```



#### <a id='Scene_set_view_x'></a>[Scene.set_view_x(positive)](#Scene_set_view_x)

*Set the view of the scene so that x-axis is perpendicular to the screen*

**Parameters**

- `positive`: (bool) If True the positive x-axis point inwards (Default: **True**)

**Example**

*Setting the view of the scene with the positive x-axis being perpendicular to the the screen and pointing inwards*

```python
my_scene.set_view_x()
```

*Setting the view of the scene with the positive x-axis being perpendicular to the the screen and pointing outwards*

```python
my_scene.set_view_x(positive=False)
```



#### <a id='Scene_set_view_y'></a>[Scene.set_view_y(positive)](#Scene_set_view_y)

*Set the view of the scene so that y-axis is perpendicular to the screen*

**Parameters**

- `positive`: (bool) If True the positive y-axis point inwards (Default: **True**)

**Example**

*Setting the view of the scene with the positive y-axis being perpendicular to the the screen and pointing inwards*

```python
my_scene.set_view_y()
```

*Setting the view of the scene with the positive y-axis being perpendicular to the the screen and pointing outwards*

```python
my_scene.set_view_y(positive=False)
```



#### <a id='Scene_set_view_z'></a>[Scene.set_view_z(positive)](#Scene_set_view_y)

*Set the view of the scene so that z-axis is perpendicular to the screen*

**Parameters**

- `positive`: (bool) If True the positive z-axis point inwards (Default: **True**)

**Example**

*Setting the view of the scene with the positive z-axis being perpendicular to the the screen and pointing inwards*

```python
my_scene.set_view_z()
```

*Setting the view of the scene with the positive z-axis being perpendicular to the the screen and pointing outwards*

```python
my_scene.set_view_z(positive=False)
```



#### <a id='Scene_set_view_iso'></a>[Scene.set_view_iso(positive)](#Scene_set_view_y)

*Set the view of the scene to isometric*

**Parameters**

- `positive`: (bool) If True the positive parts of the axis point inwards (Default: **True**)

**Example**

*Setting the view of the scene to isometric view*

```python
my_scene.set_iso()
```

*Setting the view of the scene to isometric with the positive part of the axis pointing outwards*

```python
my_scene.set_iso(positive=False)
```



#### <a id='Scene_set_result'></a>[Scene.set_result(mesh, result, analysis, component, minmax)](#Scene_set_result)

*Set a result-analysis to be rendered  for a mesh (or all meshes) in the scene*

**Parameters**

- `mesh`: (str) name of the mesh to set with a result. If mesh=None, the result is set for all the meshes in the scene
- `result`: (str) name of the result to be rendered
- `analysis`: (str) name of the analysis to be rendered
- `component`: (int) index of the component of the result to be rendered (Default: **0**)
- `minmax`: ([float, float]) min and max value for the colorbar of the scene. If not provided, the min and max values of the colorbar are automatically set to the min and max values of the result to be rendered (Default: **None**)

**Example**

*Setting the mesh called 'my_mesh' to be rendered with the magnitude of the velocity of the analysis 'phase-1' and colorbar with min and max value set to the min and max value of the result*

```python
my_scene.set_result(mesh='my_mesh', result='VELOCITY', analysis='phase-1', component=3)
```

*Setting all meshes to be rendered with the magnitude of the velocity of the analysis 'phase-1' and colorbar with min and max value set to the min and max value of the result*

```python
my_scene.set_result(mesh=None, result='VELOCITY', analysis='phase-1', component=3)
```

*Setting all meshes to be rendered with the magnitude of the velocity of the analysis 'phase-1' and colorbar with min value equal to 0.1 and max value equal to 0.8*

```python
my_scene.set_result(mesh=None, result='VELOCITY', analysis='phase-1', component=3, minmax=[0.1, 0.8])
```



#### <a id='Scene_set_mesh'></a>[Scene.set_mesh(mesh, mode, visibility)](#Scene_set_mesh)

*Set the render mode for a mesh in the scene*

**Parameters**

- `mesh`: (str) name of the mesh

- `mode`: ([iota.render.MeshMode](#class_MeshMode)) render mode for the mesh (Default: **iota.render.MeshMode.SOLID**)

- `visibility`: (float) level of opacity between 0.0 and 1.0 (Defaut: **1.0**)

  

**Example**

*Setting the mesh called 'my_mesh' to be rendered as a solid a level of opacity equal to 0.5*

```python
my_scene.set_mesh(mesh='my_mesh', visibility=0.5)
```

*Setting the mesh called 'my_mesh' to be rendered as a solid with wireframe a level of opacity equal to 1.0*

```python
my_scene.set_mesh(mesh='my_mesh', mode=iota.render.MeshMode.WIREFRAME2)
```

*Setting the mesh called 'my_mesh' to invisible*

```python
my_scene.set_mesh(mesh='my_mesh', visbility=0.0)
```



#### <a id='Scene_export'></a>[Scene.export(filename)](#Scene_export)

*Export the scene setting to pac file on disk and/or a [Scene](#class_Scene) object*

**Parameters**

- `filename`: (str) name for the pac file where the scene settings will be exported to (Default: **None**)

**Returns**

* A [**iota.render.Scene**](#class_Scene) object with the settings of the scene 

**Example**

*Exporting the scene setting to a pac file*

```python
scene_exported = my_scene.export(filename='C:/Users/Stephen/MyScenes/my_scene.pac')
print(scene_exported)
```



#### <a id='Scene_create_screenshots'></a>[Scene.create_screenshots(filename, tstart, tend, timestep_frequency)](#Scene_create_screenshots)

*Generate a screenshot or a set of screenshots based on the scene settings*

**Parameters**

- `filename`: (str) name for the files of the screenshots to be generated
- `tsart`: (int) index of the step that defines the start of the steps interval for the screenshot generation
- `tend`: (int) index of the step that defines the end of the steps interval for the screenshot generation
- `timestep_frequency`: (int) defines the frequency of the steps within the defined interval that will be used for the screenshot generation

**Returns**

- A list of  [**iota.medio.IotaImage**](media.d#class_IotaImage) objects that corresponds to the screenshots generated

**Example**

*Generating a screenshot based on the scene settings and for the 2nd step of the dataset in the scene*

```python
my_screenshot = my_scene.create_screenshots(
    filename='C:/Users/Stephen/MyScreenshots/my_screenshots', 
    tstart=1, tend=1, timestep_frequency=1)
my_screenshot[0].display()
```

*Generating a sequence of screenshot based on the scene settings for every step within the interval defined from the  2nd step to the 5th step of the dataset in the scene*

```python
my_screenshots = my_scene.create_screenshots(
    filename='C:/Users/Stephen/MyScreenshots/my_screenshots', 
    tstart=1, tend=4, timestep_frequency=1)
my_screenshots[0].display()   #screenshot for the 2nd step in the dataset
my_screenshots[1].display()   #screenshot for the 3rd step in the dataset
my_screenshots[2].display()   #screenshot for the 4th step in the dataset
my_screenshots[3].display()   #screenshot for the 5th step in the dataset
```

*Generating a sequence of screenshot based on the scene settings with a step frequency equal to 2 (i.e., a step every 2 steps) within the interval defined from the 2nd step to the 5th step of the dataset in the scene*

```python
my_screenshots = my_scene.create_screenshots(
    filename='C:/Users/Stephen/MyScreenshots/my_screenshots', 
    tstart=1, tend=4, timestep_frequency=2)
my_screenshots[0].display()   #screenshot for the 2nd step in the dataset
my_screenshots[1].display()   #screenshot for the 4th step in the dataset
```



#### <a id='Scene_create_video'></a>[Scene.create_video(filename, frame_rate, format, tstart, tend)](#Scene_create_video)

*Generate a video based on the scene settings*

**Parameters**

- `filename`: (str) name for the files of the screenshots to be generated
- `frame_rate`: (int) frame rate for the video, i.e, frames per second (Default: **5**)
- `format`: ([iota.render.VideoFormat](#class_videoformat)) format for the video file (Default: **iota.render.MP4**)
- `tsart`: (int) index of the step that defines the start of the steps interval for the video generation. If None, the interval starts from the first step in the dataset  (Default: **None**)
- `tend`: (int) index of the step that defines the end of the steps interval for the video generation. If None, the interval goes up to the last step in the dataset  (Default: **None**)

**Returns**

- A [**iota.medio.IotaVideo**](media.d#class_IotaVideo) objects that corresponds to the video generated

**Example**

*Generating a video based on the scene settings and for all the step of the dataset in the scene*

```python
my_video = my_scene.create_video(filename='C:/Users/Stephen/MyVideos/my_video.mp4')
my_video.display()
```

*Generating a video in AVI format and based on the scene settings using the frame rate of 10 frames per second. The video will includes the dataset steps going from the 3rd step to 50th step* 

```python
my_video = my_scene.create_video(filename='C:/Users/Stephen/MyVideos/my_video.avi',
                                 frame_rate= 10,
                                 format = iota.render.VideoFormat.AVI,
                                 tstart=2, 
                                 tend=49)
my_video.display()
```



------



## <a id='class_MeshMode'></a> [class MeshMode](#class_MeshMode)

*Mesh render mode class object. It is usually used to the define the render mode of the meshes in a scene (see [Scene.set_mesh()](render.md#Scene_set_mesh) method)* 

**Attributes**

- `iota.render.MeshMode.SOLID`: the mesh is rendered as a solid
- `iota.render.MeshMode.WIREFRAME`: only the wireframe of the mesh is rendered
- `iota.render.MeshMode.WIREFRAME2`: the mesh is rendered as a solid with its wireframe 



------



## <a id='class_VideoFormat'></a> [class VideoFormat](#class_VideoFormat)

*Class object to define the video format. It is usually used as an input parameter for the video generation methods (see the methods [Scene.create_video()](#Scene_create_video) and [iota.render.create_video()](#create_video))* 

**Attributes**

- `iota.render.VideoFormat.MPEG`: [H.264 format](https://en.wikipedia.org/wiki/H.264/MPEG-4_AVC). File extension: .mpg

- `iota.render.VideoFormat.AVI`: [Audio Video Interleave format](https://en.wikipedia.org/wiki/Audio_Video_Interleave) . File extension: .avi

- `iota.render.MeshMode.MP4`: [MPEG-4 Part 14 format](https://en.wikipedia.org/wiki/MPEG-4_Part_14). File extension: .mp4

- `iota.render.MeshMode.WEBM`: [WebM format](https://en.wikipedia.org/wiki/WebM). File extension: .webm

  

------



#### <a id='display'></a>[iota.render.display(scene, dataset, step, result, analysis, component, minmax, width, height)](#display)

*Display a 3D interactive render on the working notebook given a set of scene settings*

**Parameters**

- `scene`: ([iota.render.Scene](#class_Scene)) a scene object that contains the settings for the render
- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to be rendered. If provided, it overwrites the dataset from the given scene object for the render settings  (Default: **None**)
- `step`: (int) index of the timestep in the dataset to be rendered (Default: **None**) (Default: **0**)
- `result`: (str) name of the result in the dataset to be rendered. If provided, it overwrites the result from the given scene object for the render settings (Default: **None**)
- `analysis`: (str) name of the analysis in the dataset to be rendered. If provided, it overwrites the analysis from the given scene object for the render settings (Default: **None**)
- `component`: (int) index of the component of the result-analysis in the dataset to be rendered. If provided, it overwrites the component from the given scene object for the render settings (Default: **None**)
- `minmax`: ([float, float]) min and max value for the colorbar to be rendered.  If provided, it overwrites the min and max values from the given scene object for the render settings (Default: **None**)
- `width` : (int) width of the display of the scene in pixels (Default: **800**)
- `height` : (int) height of the video display of the scene in pixels (Default: **600**)

**Example**

*Displaying a 3D render using an existing scene settings but using a new dataset and setting the step to the 3rd one in the dataset*

```python
iota.render.display(scene = my_scene, dataset=my_new_dataset, step=2)
```

*Displaying a 3D render using an existing scene settings but rendering the magnitude of the velocity of the analysis 'phase-1' at the 5th step of the dataset and setting the min and max values of the colorbar to 0.2 and 0.8 respectively*

```python
iota.render.display(scene = my_scene, result='VELOCITY', analysis='phase-1', component=3, step=4, mimax=[0.2, 0.8])
```

#### 

#### <a id='create_screenshots'></a>[iota.render.create_screenshots(scene, dataset, filename, tstart, tend, timestep_frequency)](#create_screenshots)

*Generate a screenshot or a set of screenshots based on a given set of scene settings*

**Parameters**

- `scene`: ([iota.render.Scene](#class_Scene)) a scene object that contains the settings for the render
- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to be rendered. If provided, it overwrites the dataset from the given scene object for the render settings  (Default: **None**)
- `filename`: (str) name for the files of the screenshots to be generated
- `tsart`: (int) index of the step that defines the start of the steps interval for the screenshot generation
- `tend`: (int) index of the step that defines the end of the steps interval for the screenshot generation
- `timestep_frequency`: (int) defines the frequency of the steps within the defined interval that will be used for the screenshot generation

**Returns**

- A list of  [**iota.medio.IotaImage**](media.d#class_IotaImage) objects that corresponds to the screenshots generated

**Example**

*Generating a screenshot based on an existing scene settings but using a new dataset and setting the screenshot for the 3rd step in the dataset*

```python
my_screenshot = iota.render.create_screenshots(scene=my_scene, filename= 'C:/Users/Stephen/MyScreenshots/my_screenshot.png', dataset = my_dataset, tstart=2, tend=2, timestep_frequency=1)
```

*Generating a sequence of screenshot based on an existing scene settings but using a new dataset and setting the screenshots for every step within the interval defined from the 2nd step to the 5th step in the dataset*

```python
my_screenshots = my_scene.create_screenshots(scene=my_scene, dataset= my_dataset, filename='C:/Users/Stephen/MyScreenshots/my_screenshots', tstart=1, tend=4, timestep_frequency=1)
my_screenshot[0].display()   #screenshot for the 2nd step in the dataset
my_screenshot[1].display()   #screenshot for the 3rd step in the dataset
my_screenshot[2].display()   #screenshot for the 4th step in the dataset
my_screenshot[3].display()   #screenshot for the 5th step in the dataset
```

*Generating a sequence of screenshot based on an existing scene settings but using a new dataset and setting the screenshots to be generated with a step frequency equal to 2 (i.e., a step every 2 steps) within the interval defined from the 2nd step to the 5th step in the dataset*

```python
my_screenshots = my_scene.create_screenshots(sceme=my_scene, dataset=my_dataset, filename='C:/Users/Stephen/MyScreenshots/my_screenshots', tstart=1, tend=4, timestep_frequency=2)
my_screenshots[0].display()   #screenshot for the 2nd step in the dataset
my_screenshots[1].display()   #screenshot for the 4th step in the dataset
```



#### <a id='create_video'></a>[iota.render.create_video(scene, dataset, filename, frame_rate, format, tstart, tend)](#create_video)

*Generate a video based on a given set of scene settings*

**Parameters**

- `scene`: ([iota.render.Scene](#class_Scene)) a scene object that contains the settings for the render
- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to be rendered. If provided, it overwrites the dataset from the given scene object for the render settings  (Default: **None**)
- `filename`: (str) name for the files of the screenshots to be generated
- `frame_rate`: (int) frame rate for the video, i.e, frames per second (Default: **5**)
- `format`: ([iota.render.VideoFormat](#class_videoformat)) format for the video file (Default: **iota.render.MP4**)
- `tsart`: (int) index of the step that defines the start of the steps interval for the video generation. If None, the interval starts from the first step in the dataset  (Default: **None**)
- `tend`: (int) index of the step that defines the end of the steps interval for the video generation. If None, the interval goes up to the last step in the dataset  (Default: **None**)

**Returns**

- A [**iota.medio.IotaVideo**](media.d#class_IotaVideo) objects that corresponds to the video generated

**Example**

*Generating a video based on an existing scene settings but using a new dataset and including all the steps in the dataset*

```python
my_video = iota.render.create_video(scene= my_scene, dataset=my_dataset, filename='C:/Users/Stephen/MyVideos/my_video.mp4')
my_video.display()
```

*Generating a video in AVI format and based on an existing  scene settings but using a new dataset and setting the frame rate of 10 frames per second. The video will includes the steps within the interval defined from the 3rd to 50th step in the dataset* 

```python
my_video = my_scene.create_video(scene= my_scene,
                                 dataset=my_dataset,
                                 filename='C:/Users/Stephen/MyVideos/my_video.avi',
                                 frame_rate= 10,
                                 format = iota.render.VideoFormat.AVI,
                                 tstart=2, 
                                 tend=49)
my_video.display()
```



------

