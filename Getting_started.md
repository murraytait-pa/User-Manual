# Quick start with Iota

This section provides an introduction on how to start using the Iota software. Particularly, it will focus on how to use and Iota and its Python Library using [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html).

## <a id='starting-jupyter'></a>[Starting Iota Jupyter](#starting-jupyter)

The [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) is installed during the installation process of Iota. Users can start Jupyter by clicking on the shortcut "Iota Jupyter" that can be found the "Iota" folder at the Start menu of their operative system.


![](/images/License_registration_Iota_Jupyter.PNG)
  

After clicking on the "Iota Jupyter" shortcut, a command window will be open and after a few seconds, the home page of Jupyter will be automatically open in a tab of the user's default web browser (see picture below). "Iota Jupyter" is started, by default, at the "ParticleAnalytics" folder located in the user's home directory of the operative system (e.g. `C:/Users/Stephen/ParticleAnalytics`). Therefore, the home page of Jupyter shows the content of "ParticleAnalytics" folder.

![](/images/Getting_started_Jupyter_Notebooks_tree.PNG)

## <a id='creating-a-new-notebook'></a>[Creating a new notebook](#creating-a-new-notebook)

Before starting to analyze your simulation data, users will need to create an Iota notebook where the analysis of the simulation data can be conducted. To do so, click on "**New**" and then select the option "Notebook:" > "**iota**"

![](/images/Getting_started_Jupyter_Notebooks_New_Notebook.PNG)

The new empty notebook will be created and opened in new tab in your web browser. 

![](/images/Getting_started_iota_notebook.PNG)

As a good practice, it is recommended to create first a folder for your analysis and then create the notebook inside that folder. This way the notebook of the analysis and any images, videos or other files generated during the analysis will be stored together inside the same folder. A new folder can be created from the Jupyter home page by clicking on the "New" button located at the right side of the window and then select the option "Other:" > "Folder". Alternatively, the folder can also be created using the standard procedure of your operative system.


## <a id='what-is-notebook'></a>[Creating a new notebook](#creating-a-new-notebook)

A notebook consists on a sequence of cells. Each cell can multiple commands or text to be executed. The execution of the cell can be triggered b user can execute those lines 

https://jupyter-notebook.readthedocs.io/en/stable/notebook.html

The notebook consists of a sequence of cells. A cell is a multiline text input field, and its contents can be executed by using Shift-Enter, or by clicking either the “Play” button the toolbar, or Cell, Run in the menu bar. The execution behavior of a cell is determined by the cell’s type. There are three types of cells: code cells, markdown cells, and raw cells. Every cell starts off being a code cell, but its type can be changed by using a drop-down on the toolbar (which will be “Code”, initially), or via keyboard shortcuts.


## <a id='importing-iota-library'></a>[Importing iota library](#importing-iota-library)
The first step to start working with the Iota Python Library is to import the library into the notebook. To this end, you will need to type the following in the first code cell of your notebook:

``` python
import iota
```

## <a id='loading-a-dataset'></a>[Loading a simulation dataset](#loading-a-dataset)
 




## <a id='getting-started-notebook'></a>[Getting started notebook](#getting-started-notebook)

A getting started package that includes a example ANSYS Fluent simulation data files and a notebook with instructions to perfrom the post-analysis of the simulation data can be downloaded here: Download 