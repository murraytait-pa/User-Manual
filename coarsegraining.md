# iota.coarse_graining
**Description**

This module provides functionalities to transform the discrete data from particle based simulations (e.g DPM, DEM) into continuum data.


* [CoarseGraining](#class_Coarsegraining)
  * [settings](#Coarsegraining_settings)
  * [settings_default](#Coarsegraining_settings_default)
  * [settings_merged](#Coarsegraining_settings_merged)
  * [run](#Coarsegraining_run)
  * [output_dataset](#Coarsegraining_output_dataset)
  * [output_graphs](#Coarsegraining_output_graphs)
  * [output_padem](#Coarsegraining_output_padem)
  * [export_settings](#Coarsegraining_export_settings)





## <a id='class_Coarsegraining'></a> [class CoarseGraining](#class_coarsegraining)

#### <a id='Coarsegraining_ctor'></a> [iota.coarse_grainig.CoarseGraining(file, settings, dataset)](#Coarsegraining_ctor)

*CoarseGraining class object. This object contains the settings, the output and the run methods for a coarse-graining analysis.*

**Parameters**

- `file`: (str) path and name to a coarse-graining settings file (Default: **None**)
- `settings`: (dict) coarse-graining settings given as a dictionary (Default: **None**)
- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to be used as input dataset for the coarse-graining analysis. If provided, it overwrites the input dataset of the coarse-graining settings (Default: **None**)

**Examples**

*Creating a CoarseGraining object with default settings*

```python
my_cg = iota.coarse_graining.CoarseGraining()
```

*Creating a CoarseGraining object based on the settings in an existing coarse-graining settings file*

```python
my_cg = iota.coarse_graining.CoarseGraining(file='C:/Users/Stephe/CGSettings/my_cg_settings.json')
```

*Creating a CoarseGraining object given on an existing settings dictionary*

```python
my_new_cg = iota.coarse_graining.CoarseGraining(settings=my_cg.settings)
```

*Creating a CoarseGraining object with default settings and an existing dataset object as the input dataset*

```python
my_cg = iota.coarse_graining.CoarseGraining(dataset=my_dataset)
```

*Creating a CoarseGraining object based on the settings in an existing coarse-graining settings file and using an existing dataset object as the input dataset*

```python
my_cg = iota.coarse_graining.CoarseGraining(file='C:/Users/Stephe/CGSettings/my_cg_settings.json', dataset=my_dataset)
```

*Creating a CoarseGraining object given on an existing settings dictionary and using an existing dataset object as the input dataset*

```python
my_new_cg = iota.coarse_graining.CoarseGraining(settings=my_cg.settings, dataset=my_dataset)
```



### Attributes

#### <a id='Coarsegraining_settings'></a>[CoarseGraining.settings](#Coarsegraining_settings)

*Get the coarse-graining settings that the user explicitly has set*

**Returns**

- A **dictionary** with the settings explicitly set by the user

**Example**

*Getting the settings of a coarse-graining object*

```python
my_cg_settings = my_cg.settings
print(my_cg_settings)
```





### Methods

#### <a id='Coarsegraining_settings_default'></a>[CoarseGraining.settings_default()](#Coarsegraining_settings_default)

*Get the default coarse-graining settings*

**Returns**

- A **dictionary** with the default coarse-graining settings

**Example**

*Getting the default settings of a coarse-graining object*

```python
default_cg_settings = my_cg.settings_default()
print(default_cg_settings)
```



#### <a id='Coarsegraining_settings_merged'></a>[CoarseGraining.settings_merged()](#Coarsegraining_settings_merged)

*Get the complete coarse-graining settings that result from merging the settings explicitly set by the user and the default settings*

**Returns**

- A **dictionary** with the complete coarse-graining settings of the CoarseGraining object

**Example**

*Getting the complete settings of a CoarseGraining object*

```python
cg_settings = my_cg.settings_merged()
print(cg_settings)
```



#### <a id='Coarsegraining_run'></a>[CoarseGraining.run()](#Coarsegraining_run)

*Run coarse-graining transformation based on the settings of the CoarseGraining object*

**Example**

*Running the coarse-graining transformation for the CoarseGraining object*

```python
cg_settings.run()
```



#### <a id='Coarsegraining_output_dataset'></a>[CoarseGraining.output_dataset()](#Coarsegraining_output_dataset)

*Get the dataset object that corresponds to the coarse-graining dataset generated after running the coarse-graining transformation*

**Return**

* A [**iota.dataset.Dataset**](dataset.md#class_dataset) object that corresponds to the coarse-graining dataset

**Example**

*Getting the coarse-graining dataset generated after running coarse-graining transformation*

```python
my_cg.run()
my_cg_dataset = my_cg.output_dataset()
```



#### <a id='Coarsegraining_output_graphs'></a>[CoarseGraining.output_graphs()](#Coarsegraining_output_graphs)

*Get a list that contains the graphs object that may have been generated as result of the coarse-graining transformation*

**Return**

- A **list of [iota.graph.Graph ](graph.md#class_Graph)**objects that correspond to the graphs generated by the coarse-graining transformation

**Example**

*Getting the list of graph objects generated after running coarse-graining transformation*

```python
my_cg.run()
my_cg_graphs = my_cg.output_graphs()
my_cg_graphs[0].display()
```



#### <a id='Coarsegraining_output_padem'></a>[CoarseGraining.output_padem()](#Coarsegraining_output_padem)

*Get the dataset object that corresponds to the padem dataset that may have been generated after running the coarse-graining transformation. The padem dataset would contain the raw data of the particle based simulation in Particle Analytics format*

**Return**

- A [**iota.dataset.Dataset**](dataset.md#class_dataset) object that corresponds to the padem dataset

**Example**

*Getting the padem dataset generated after running coarse-graining transformation*

```python
my_cg.run()
my_padem_dataset = my_cg.output_padem()
```



#### <a id='Coarsegraining_export_settings'></a>[CoarseGraining.export_settings(file, merged)](#Coarsegraining_export_settings)

*Export the settings of a given CoarseGraining object to file in [json](https://www.json.org/) format*

**Parameters**

* `file`: (str) path and name for the file where the settings will be exported to.
* `merged`: (bool) if True, the complete coarse-graining settings are exported, i.e., the settings resulting of merging the user settings and the default ones. If False, only the user settings are exported  (Default: **False**)

**Example**

*Exporting the coarse-graining settings set by the user to a file*

```python
my_cg.export(file='C:/Users/Stephen/CGsettings/my_cg_settings.json')
```

*Exporting the complete coarse-graining settings to a file*

```python
my_cg.export(file='C:/Users/Stephen/CGsettings/my_cg_settings.json', merged=True)
```