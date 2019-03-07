
# Getting started with Iota

This section provides an introduction on how to start using the Iota Python Library from a Jupyter notebook. 

## Starting Iota Jupyter

The [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) is installed during the installation process of Iota. "Iota Jupyter" can be started by clicking on its shortcut available in the "Iota" folder at the Start menu of the your operative system.

![](/images/License_registration_Iota_Jupyter.PNG)
  

After clicking on the "Iota Jupyter" shortcut, a command window will be open and after a few second, the home page of Jupyter will be automatically open in a tab of your default web browser (see picture below).

![](/images/Getting_started_Jupyter_Notebooks_tree.PNG)

## Creating a new notebook
Next step is to create a new notebook where the analysis of the simulation data will be conducted. To do so, click on "**New**" and then select the option "Notebook:" > "**iota**"

![](/images/Getting_started_Jupyter_Notebooks_New_Notebook.PNG)

The new empty notebook will be created and opened in new tab in your web browser. 

![](/images/Getting_started_iota_notebook.PNG)


As a good practice, it is recommended to create first a folder for your analysis and then create the notebook inside that folder. This way the notebook of the analysis and any images, videos or other files generated during the analysis will be stored together inside the same folder. A new folder can be created from the Jupyter home page by clicking on the "New" button located at the right side of the window and then select the option "Other:" > "Folder". Alternatively, the folder can also be created using the standard procedure of your operative system.

## Importing Iota library


```python
import iota
```

## Loading a dataset


```python
my_dataset = iota.dataset.load_fluent(case_files=['C:/Users/AJanda/Desktop/Demo_example/Fluent/Radiation_hdf5/Astec-radiation-240s.cas.h5'],
                             data_files=['C:/Users/AJanda/Desktop/Demo_example/Fluent/Radiation_hdf5/Astec-radiation-240s.dat.h5'])
```

    C:\Users\AJanda\Desktop\Demo_example\Fluent\Radiation_hdf5/Astec-radiation-240s.cas.json has been created
    Dataset successfully loaded


## Visualizing a datataset


```python
my_scene = iota.render.Scene(dataset=my_dataset)
```


```python
my_scene.display(timestep=0, width=900, height=600)
```


    ---------------------------------------------------------------------------
    
    AttributeError                            Traceback (most recent call last)
    
    <ipython-input-9-db2223094d1f> in <module>()
    ----> 1 my_scene.display(timestep=0, width=900, height=600)


    C:\Program Files\iota_suite\iota\render\scene.py in display(self, width, height, timestep)
        933             first_displayable = list(self._graphics_displayables.values())[0].displayable
        934 
    --> 935         scene_bounding_box_low_left = first_displayable.bounding_box_low_left
        936         scene_bounding_box_up_right = first_displayable.bounding_box_up_right
        937 


    AttributeError: 'NoneType' object has no attribute 'bounding_box_low_left'



```python
my_graph = iota.graph.Graph()
```

```python
my_graph.add_trace(x=[0,1,2,3], y=[0,1,2,3], name='Trace1')
```


```python
my_graph.display()
```
