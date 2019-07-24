# Getting started with Iota

This section provides an introduction on how to start using the Iota software. Particularly, it will focus on how to use and Iota and its Python Library using [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html).


## <a id='starting-jupyter'></a>[Starting Iota Jupyter](#starting-jupyter)

The [Jupyter Notebooks](https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/what_is_jupyter.html) is installed during the installation process of Iota. Users can start Jupyter by clicking on the shortcut "Iota Jupyter" that can be found the "Iota" folder at the Start menu of their operative system.


![](/images/License_registration_Iota_Jupyter.PNG)
  
After clicking on the "Iota Jupyter" shortcut, a command window will be open and after a few seconds, the dashboard of Jupyter will be automatically open in a tab of the user's default web browser (see picture below). This dashboard shows the content of the working directory of Iota. By default, this working directory is the "ParicleAnalytics" folder located in the user's home directory of the operative system (e.g. `C:/Users/Stephen/ParticleAnalytics`).

![](/images/Getting_started_Jupyter_Notebooks_tree.PNG)

## <a id='creating-a-new-notebook'></a>[Creating a new notebook](#creating-a-new-notebook)

Users need an Iota notebook in order analyze their simulation data. A new notebook can be created by clicking on the "**New**" button located at the top right side of the window. Then select the  option "Notebook:" > "**iota**" from the drop-down menu.

![](/images/Getting_started_Jupyter_Notebooks_New_Notebook.PNG)


The new empty notebook will be created and opened in new tab in your web browser. The image below shows an empty notebook.


![](/images/Getting_started_iota_notebook.PNG)

As a good practice, it is recommended to create first a folder for your analysis and then create the notebook inside that folder. In this way, the images, videos or other files generated during the analysis will be stored inside that folder by default. A new folder can be created from the Jupyter home page by clicking on the "New" button located at the right side of the window and then selecting the option "Other:" > "Folder". Alternatively, the folder can also be created using the standard procedure of the operative system.


## <a id='what-is-a-notebook'></a>[What is a notebook?](#what-is-a-notebook)

A notebook can be understood as an interactive journal that records the analysis of one or more simulations. It contains a sequence of cells that capture the different steps of the analysis. Cells can contains multiple lines where users can type python commands or simple text. Two type of cells are mainly used:

* **Code cells**: users can type python functions including those provided by the Iota Python library.
* **Markdown cells**: users can type here text to add comments for their analysis.

By default, all new cells are initially added as a code cell, but users can change its type by using the drop-down on the toolbar of the notebook. Users can execute the content of a cell by using Shift-Enter or by clicking the "Run" button on the toolbar. New cells can be added by using the "+" button also located also on the toolbar.

For more detailed information about Jupyter notebooks and the user interface components, please see the following link: [The Jupyter Notebook](https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#)


## <a id='getting-started-notebook'></a>[Getting started notebook](#getting-started-notebook)

A getting started package to help users to learn how to use Iota is available. The package contains a notebook where the most common steps to use Iota to analyze an CFD simulation with Discrete Phase Modelling data are described:

1. Click on the following link to download the zip file that contains the getting started package: [Download link](https://s3-eu-west-1.amazonaws.com/particle-analytics/Getting_Started_Notebook.zip)
2. Unzip the download file into the "ParticleAnalytics" folder located in the user's home directory (e.g. `C:/Users/Stephen/ParticleAnalytics`)
3. Start "Iota Jupyter" using the shortcut in the Start Menu of the operative system.
4. In the Dashboard of Jupyter, click on the folder "Getting_Started_Notebook"  
5. Click on the "Getting Started Notebook" notebook to open it and follow the instructions in it.  
