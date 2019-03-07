# iota.graph
**Description**

This module provides functionalities to generate, edit, display and export graphs.



**Generating graphs**

- [plot_xy](#plot_xy)
- [plot_histogram](#plot_histogram)



**Accessing, adding and deleting data from the graph**

* [Graph](#class_Graph)

  * [get_data](#get_data)

  * [set_data](#set_data)

  * [delete_data](#delete_data)

  * [add_data](#add_data)

  * [add_histogram](#add_histogram)

  * [add_trace](#add_trace)

    

**Displaying and exporting graphs** 

- [Graph](#class_Graph)

  - [display](#display)
  - [export_html](#export_html)
  - [export_csv](#export_csv)

  

**Getting and setting graph layout**

- [Graph](#class_Graph)
  - [get_layout](#get_layout)
  - [set_layout](#set_layout)



------

## <a id='class_Graph'></a> [class Graph](#class_Graph)

#### <a id='Graph_ctor'></a> [iota.graph.**Graph**()](#Graph_ctor)

*Graph class object. This object is returned when generating a plot using one of the plot methods in the [iota.graph](graph.md) (see for example [iota.graph.plot_xy](#plot_xy) or [iota.graph.plot_histogram](#plot_histogram))*

### Methods

#### <a id='add_data'></a>[Graph.add_data(data)](#add_data)

*Add a [ploty.go_objs.Data](https://plot.ly/python/user-guide/#data) object to the graph. The Data objects contains a list of data collections objects.*

**Parameters**

- `data` : ([ploty.go_objs.Data](https://plot.ly/python/user-guide/#data)) Data object containing a list of data collections 

**Example**

*Adding a Data object that contains a list of two traces*

```python
import ployly as plt
trace1 =  plt.graph_objs.Scatter(x=[8,9,10], y=[11,12,13], name='trace 1')
trace2 =  plt.graph_objs.Scatter(x=[8,9,10], y=[14,15,16], name='trace 2')
Data = plt.graph_objs.Data([trace1, trace2]) 
my_graph = iota.graph.Graph()
my_graph.add_data(Data)
```



#### <a id='add_histrogram'></a>[Graph.add_histogram(name, values, nbins, sizebins, normalize)](#add_histogram)

*Add a new data collection as a histogram to the graph*

**Parameters**

- `name` : (str) name for the histogram
- `values` : (list of floats or numpy.ndarray of floats) list of values to build the histogram
- `nbins` : (int) maximum number of bins for the histogram (ignored if `sizebins` is provided)
- `sizebins`: (float) size for the bins of the histogram
- `normalize`: (str) method to normalize the values of the height of the bins (Default: **''**)
  -   ``''``:  number of occurrences 
  -  `'percent'`: percentage of occurrences with respect to the total number of values in `value` (sum of the height of all bins is equal to 100%)  
  -  `'probability'`: fraction of occurrences with respect to the total number of values in `value` (sum of the height of all bins is equal to 1)  
  -  `'density'`: number of occurrences in a bin is divided by the of the bin (sum of all bin areas is equal to total number of values in `value`)   
  -  `'probability density'`: the area of each bin corresponds to the probability that an event falls within the corresponding bin (sum of all bin areas is equal to 1) 

**Examples**

*Adding a new histogram called 'histogram 1' with maximum number of bins equal to 4*

```python
my_graph.add_histogram(name='histogram 1', values=[0.5,1.15,1.25,0.8,0.5,0.6], nbins=4)
```

*Adding a new histogram called 'histogram 1' with bin size equal to 0.5 and normalizing the height of the bin based on percentage*

```python
my_graph.add_histogram(name='histogram 1', values=[0.1,1.15,1.25,0.8,0.2,0.6], sizebins=0.5, normalize='percent')
```



#### <a id='add_trace'></a>[Graph.add_trace(name, x, y)](#add_trace)

*Add a new data collection as a  trace (scatter) to the graph*

**Parameters**

- `name` : (str) name of the trace
- `x` : (list of floats or numpy.ndarray of floats) x-values of the trace
- `y` : (list of floats or numpy.ndarray of floats) y-values of the trace

**Examples**

*Adding a new trace to an existing graph given the x and y values as a list of floats*

```python
my_graph.add_trace(name='my new trace', x=[0.5,1.5,2.5,3.5], y=[10.2,11.2,12.2,13.2])
```

*Adding a new trace to an existing graph given the x and y values as numpy array of floats*

```python
x_values = numpy.array([0.5,1.5,2.5,3.5])
y_values = numpy.array([10.2,11.2,12.2,13.2])
my_graph.add_trace(name='my new trace', x=x_values, y=y_values)
```



#### <a id='display'></a>[Graph.display(width, height)](#display)

*Display the graph in the working notebook*

**Parameters**

- `width` : (int) width for the display of the graph in pixels (Default: **800**)
- `height` : (int) height for the display of the graph in pixels (Default: **600**)

**Examples**

*Displaying the graph with the default height and width*

```python
my_graph.display()
```

*Displaying the graph and setting its width to 1000 pixels and height to 800 pixels*

```python
my_graph.display(width=1000, height=800)
```

#### 

#### <a id='delete_data'></a>[Graph.delete_data(name)](#delete_data)

*Delete an existing collection of data (e.g. a trace data or a histogram data) from the graph given the name of the data collection*

**Parameters**

- `name` : (str) name of the collection of data to be deleted from the graph

**Example**

*Deleting the existing trace called 'my new trace' from the graph*

```python
my_graph.delte_data(name='my new trace')
```



#### <a id='export_csv'></a>[Graph.export_csv(file)](#export_csv)

*Export the data values of the traces and histograms in the graph to csv file*

**Parameters**

- `file` : (str) path for the csv file

**Example**

*Exporting the data values of a graph to a csv file called 'my_graph_data.csv'*

```python
my_graph.export_csv(file='C:/Users/Stephen/MyGraphs/my_graph_data.csv')
```



#### <a id='export_html'></a>[Graph.export_html(file, auto_open, width, height)](#export_html)

*Export the graph to html file*

**Parameters**

- s`file` : (str) path for the csv file
- `auto_open` : (bool) If True, the exported html file is automatically opened in your web browser (Default: **False**)
- `width` : (int) width for th graph in pixels (Default: **800**)
- `height` : (int) height for the graph in pixels (Default: **600**)

**Examples**

*Exporting a graph to a html file called 'my_graph.html'*

```python
my_graph.export_html(file='C:/Users/Stephen/MyGraphs/my_graph.html')
```

*Exporting the graph to a html file call 'my_graph.html' and setting its width to 1000 pixels and height to 800 pixels*

```python
my_graph.export_html(file='C:/Users/Stephen/MyGraphs/my_graph.html', width=1000, height=800)
```



#### <a id='get_data'></a>[Graph.get_data(name)](#get_data)

*Get the [ploty graph object](https://plot.ly/python/reference/) that represents a data collection in the graph* 

**Parameters**

- `name` : (str) name of the data collection

**Output**

* A [**ploty graph object**](https://plot.ly/python/reference/) representing the data collection:
  * [plotly.graph_objs.Scatter](https://plot.ly/python/reference/#scatter)
  * [plotly.graph_objs.Histogram](https://plot.ly/python/reference/#histogram)
  * [plotly.graph_objs.Surface](https://plot.ly/python/reference/#surface)

**Example**

*Getting the plolty graph object of the existing trace called 'Trace 1' in  the graph*

```python
my_graph.get_data(naem='Trace 1')
```



#### <a id='set_data'></a>[Graph.set_data(name, data)](#set_data)

*Set the  a new [ploty graph object](https://plot.ly/python/reference/) to an existing data collection in the graph* 

**Parameters**

- `name` : (str) name of the existing data collection
- `data`: ([ploty.graph_objs](https://plot.ly/python/reference/)) a plotly graph object with the new setting for the data collection:
  - [plotly.graph_objs.Scatter](https://plot.ly/python/reference/#scatter)
  - [plotly.graph_objs.Histogram](https://plot.ly/python/reference/#histogram)
  - [plotly.graph_objs.Surface](https://plot.ly/python/reference/#surface)

**Examples**

*Creating a new graph with a trace called 'Trace 1'  ands setting afterwards the x-values of the trace to a new list of values*

```python
my_graph = iota.graph.Graph()
my_graph.add_trace(name='Trace 1', x=[0.5,1.5,2.5,3.5], y=[10.2,11.2,12.2,13.2])
my_trace = my_graph.get_data(name='Trace 1')
my_trace['x'] = [1.5,2.5,3.5,4.5]
my_graph.set(name='Trace 1', data=my_trace)
```



#### <a id='get_layout'></a>[Graph.get_layout()](#get_layout)

*Get a [layout object](https://plot.ly/python/reference/#layout) that contains the settings of the layout of the graph* 

**Output**

- A [plotly layout object](https://plot.ly/python/reference/#layout) that contains the settings of the layout

**Example**

*Getting the layout settings of a graph*

```python
layout_settings = my_graph.get_layout()
print(layout_settings)
```



#### <a id='set_layout'></a>[Graph.set_layout()](#set_layout)

*Set the settings of the layout of graph* 

**Parameters**

- `title` : (str) title for the graph (Default: **None**)
- `x_label`: (str) title for the x-axis (Default: **None**)
- `y_label`: (str) title for the y-axis (Default: **None**)
- `x_range`: (list of two floats): Min and Max values defining the range of the x-axis (Default: **None**)
- `y_range`: (list of two floats): Min and Max values defining the range of the y-axis (Default: **None**)
- `width`: (int) width of the graph in pixels (Default: **None**)
- `height`: (int) width of the graph in pixels (Default: **None**)

**Example**

*Setting the title of the graph, x-axis and y-axis*

```python
my_graph.set_layout(title='My new graph', 
                    x_label='time (s)', 
                    y_label='Pressure (kPa)')
```



#### <a id='plot_xy'></a>[Graph.plot_xy(x, y, name, title, x_label, y_label, layout)](#plot_xy)

*Generate a graph with a scatter plot of trace given its x and y values*

**Parameters**

- `x` : (list of floats or numpy.ndarray of floats) x-values of the trace
- `y` : (list of floats or numpy.ndarray of floats) y-values of the trace
- `name`: (str) name for the trace
- `title` : (str) title of the graph (default: **None**)
- `x_label` : (str) title for the x-axis (Default: **None**)
- `y_label` : (str) title for the y-axis (Default: **None**)
- `layout`: ([plotly.go_objs.Layout](https://plot.ly/python/reference/#layout)) a plotly layout object with the settings for the layout of the graph (Default: **None**) 

**Output**

- A [Graph](#class_Graph) object that contains a collection of data represented as a trace

**Example**

*Generating graph with a scatter 2D plot called 'Maximum Pressure' and given the array of x values and the array of y values*

```python
x_values = numpy.array([0.5,1.5,2.5,3.5])
y_values = numpy.array([10.2,11.2,12.2,13.2])
my_graph = my_graph.plot_xy( name='Maximum Pressure', x=x_values, y=y_values, x_label='time (s)', y_label='Pressure (KPa)')
my_graph.display()
```



#### <a id='plot_histogram'></a>[Graph.plot_histogram(name, values, nbins, sizebins, normalize, title, x_label, y_label, layout)](#plot_histogram)

*Generate a graph with a scatter plot of trace given its x and y values*

**Parameters**

- `name` : (str) name for the histogram
- `values` : (list of floats or numpy.ndarray of floats) list of values to build the histogram
- `nbins` : (int) maximum number of bins for the histogram (ignored if `sizebins` is provided)
- `sizebins`: (float) size for the bins of the histogram
- `normalize`: (str) method to normalize the values of the height of the bins (Default: **''**)
  - ``''``:  number of occurrences 
  - `'percent'`: percentage of occurrences with respect to the total number of values in `value` (sum of the height of all bins is equal to 100%)  
  - `'probability'`: fraction of occurrences with respect to the total number of values in `value` (sum of the height of all bins is equal to 1)  
  - `'density'`: number of occurrences in a bin is divided by the of the bin (sum of all bin areas is equal to total number of values in `value`)   
  - `'probability density'`: the area of each bin corresponds to the probability that an event falls within the corresponding bin (sum of all bin areas is equal to 1) 
- `title` : (str) title for graph (Default: **None**)
- `x_label` : (str) title for the x-axis (Default: **None**)
- `y_label` : (str) title for the y-axis (Default: **None**)
- `layout`: ([plotly.go_objs.Layout](https://plot.ly/python/reference/#layout)) a plotly layout object with the settings for the layout of the graph (Default: **None**) 

**Output**

- A [Graph](#class_Graph) object that contains a collection of data represented as a histogram

**Examples**

*Generating a new graph with a histogram called 'Pressure' given an array with the values and a maximum number of bins equal to 4*

```python
values = numpy.asarray([0.5,1.15,1.25,0.8,0.5,0.6])
my_graph = iota.graph.plot_histogram(name='Pressure', values=values, nbins=4, title='Pressure Histogram', x_label='Pressure (kPa)', y_label='Number of nodes')
my_graph.display()
```

*Generating a new graph with a histogram called 'Pressure' given an array with the values, a bin size equal to 0.5 and normalizing the height of the bin based on percentage*

```python
values = numpy.asarray([0.5,1.15,1.25,0.8,0.5,0.6])
my_graph = iota.graph.plot_histogram(name='Pressure', values=values, sizebins=0.5, normalize='percent', title='Pressure Histogram', x_label='Pressure (kPa)', y_label='Number of nodes')
my_graph.display()
```