
# Getting started with Iota

This section provides an introduction on how to start using the Iota Python Library from a Jupyter notebook. The [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) is installed during the installation process of Iota and is available at the Start menu inside the "Iota" folder.

## Starting a new Iota notebook 


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


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>



```python
my_graph.add_trace(x=[0,1,2,3], y=[0,1,2,3], name='Trace1')
```


```python
my_graph.display()
```


<script>requirejs.config({paths: { 'plotly': ['https://cdn.plot.ly/plotly-latest.min']},});if(!window.Plotly) {{require(['plotly'],function(plotly) {window.Plotly=plotly;});}}</script>


<div id="bdedd98b-e986-47f3-a3da-3d05ab51dc62" style="height: 525px; width: 100%;" class="plotly-graph-div"></div><script type="text/javascript">require(["plotly"], function(Plotly) { window.PLOTLYENV=window.PLOTLYENV || {};window.PLOTLYENV.BASE_URL="https://plot.ly";Plotly.newPlot("bdedd98b-e986-47f3-a3da-3d05ab51dc62", [{"type": "scatter", "x": [0, 1, 2, 3], "name": "Trace1", "y": [0, 1, 2, 3]}], {}, {"linkText": "Export to plot.ly", "displaylogo": false, "showLink": false, "modeBarButtonsToRemove": ["pan2d", "lasso2d", "sendDataToCloud"]})});</script>

