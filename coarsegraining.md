# iota.coarsegraining
**Description**

This module provides functionalities to transform the discrete data from particle based simulations (e.g DPM, DEM) into continuum data.



* [Coarsegraining](#class_Coarsegraining)
  * [settings](#Coarsegraining_settings)
  * [settings_default](#Coarsegraining_settings_default)
  * [settings_merged](#Coarsegraining_settings_merged)
  * [run](#Coarsegraining_run)
  * [output_dataset](#Coarsegraining_output_dataset)
  * [output_graphs](#Coarsegraining_output_graphs)
  * [output_padem](#Coarsegraining_output_padem)
  * [export_settings](#Coarsegraining_export_settings)





## <a id='class_Coarsegrainig'></a> [class Coarsegraining](#class_coarsegraining)

#### <a id='Coarsegraining_ctor'></a> [iota.coarsegrainig.Coarsegraining(file, settings, dataset)](#Coarsegraining_ctor)

*Coarsegraining class object. This object contains the settings, the output and the run methods for a coarsegraining analysis.*

**Parameters**

- `file`: (str) path and name to a coarsegraining settings file (Default: **None**)
- `settings`: (dict) coarsegraining settings given as a dictionary (Default: **None**)
- `dataset` : ([iota.dataset.Dataset](dataset.md#class_dataset)) a dataset object to be used as input dataset for the coarsegraining analysis. If provided, it overwrites the input dataset of the coarsegraining settings (Default: **None**)

**Examples**

*Creating a Coarsegraining object with default settings*

```python
my_cg = iota.coarsegraining.Coarsegraining()
```

*Creating a Coarsegraining object based on the settings in an existing coarsegraining settings file*

```python
my_cg = iota.coarsegraining.Coarsegraining(file='C:/Users/Stephe/CGSettings/my_cg_settings.json')
```

*Creating a Coarsegraining object given on an existing settings dictionary*

```python
my_new_cg = iota.coarsegraining.Coarsegraining(settings=my_cg.settings)
```

*Creating a Coarsegraining object with default settings and an existing dataset object as the input dataset*

```python
my_cg = iota.coarsegraining.Coarsegraining(dataset=my_dataset)
```

*Creating a Coarsegraining object based on the settings in an existing coarsegraining settings file and using an existing dataset object as the input dataset*

```python
my_cg = iota.coarsegraining.Coarsegraining(file='C:/Users/Stephe/CGSettings/my_cg_settings.json', dataset=my_dataset)
```

*Creating a Coarsegraining object given on an existing settings dictionary and using an existing dataset object as the input dataset*

```python
my_new_cg = iota.coarsegraining.Coarsegraining(settings=my_cg.settings, dataset=my_dataset)
```



### Attributes

#### <a id='Coarsegraining_settings'></a>[Coarsegraining.settings](#Coarsegraining_settings)

*Get the coarsegraining settings that the user explicitly has set*

**Returns**

- A **dictionary** with the settings explicitly set by the user

**Example**

*Getting the settings of a coarsegraining object*

```python
my_cg_settings = my_cg.settings
print(my_cg_settings)
```





### Methods

#### <a id='Coarsegraining_settings_default'></a>[Coarsegraining.settings_default()](#Coarsegraining_settings_default)

*Get the default coarsegraining settings*

**Returns**

- A **dictionary** with the default coarsegraining settings

**Example**

*Getting the default settings of a coarsegraining object*

```python
default_cg_settings = my_cg.settings_default()
print(default_cg_settings)
```



#### <a id='Coarsegraining_settings_merged'></a>[Coarsegraining.settings_merged()](#Coarsegraining_settings_merged)

*Get the complete coarsegraining settings that result from merging the settings explicitly set by the user and the default settings*

**Returns**

- A **dictionary** with the complete coarsegraining settings of the coarsegraining object

**Example**

*Getting the complete settings of a coarsegraining object*

```python
cg_settings = my_cg.settings_merged()
print(cg_settings)
```



#### <a id='Coarsegraining_run'></a>[Coarsegraining.run()](#Coarsegraining_run)

*Run the coarsegraining transformation based on the settings of the coarsegraining object*

**Example**

*Running the coarsegraining transformation for the coarsegraining object*

```python
cg_settings.run()
```



#### <a id='Coarsegraining_output_dataset'></a>[Coarsegraining.output_dataset()](#Coarsegraining_output_dataset)

*Get the dataset object that corresponds to the coarsegraining dataset generated after running the coarsegraining transformation*

**Return**

* A [**iota.dataset.Dataset**](dataset.md#class_dataset) object that corresponds to the coarsegraining dataset

**Example**

*Getting the coarsegraining dataset generated after running coarsegraining transformation*

```python
my_cg.run()
my_cg_dataset = my_cg.output_dataset()
```



#### <a id='Coarsegraining_output_graphs'></a>[Coarsegraining.output_graphs()](#Coarsegraining_output_graphs)

*Get a list that contains the graphs object that may have been generated as result of the coarsegraining transformation*

**Return**

- A **list of [iota.graph.Graph ](graph.md#class_Graph)**objects that correspond to the graphs generated by the coarsegraining transformation

**Example**

*Getting the list of graph objects generated after running coarsegraining transformation*

```python
my_cg.run()
my_cg_graphs = my_cg.output_graphs()
my_cg_graphs[0].display()
```



#### <a id='Coarsegraining_output_padem'></a>[Coarsegraining.output_padem()](#Coarsegraining_output_padem)

*Get the dataset object that corresponds to the padem dataset that may have been generated after running the coarsegraining transformation. The padem dataset would contain the raw data of the particle based simulation in Particle Analytics format*

**Return**

- A [**iota.dataset.Dataset**](dataset.md#class_dataset) object that corresponds to the padem dataset

**Example**

*Getting the padem dataset generated after running coarsegraining transformation*

```python
my_cg.run()
my_padem_dataset = my_cg.output_padem()
```



#### <a id='Coarsegraining_export_settings'></a>[Coarsegraining.export_settings(file, merged)](#Coarsegraining_export_settings)

*Export the settings of a given coarsegraining object to file in [json](https://www.json.org/) format*

**Parameters**

* `file`: (str) path and name for the file where the settings will be exported to.
* `merged`: (bool) if True, the complete coarsegraining settings are exported, i.e., the settings resulting of merging the user settings and the default ones. If False, only the user settings are exported  (Default: **False**)

**Example**

*Exporting the coarsegraining settings set by the user to a file*

```python
my_cg.export(file='C:/Users/Stephen/CGsettings/my_cg_settings.json')
```

*Exporting the complete coarsegraining settings to a file*

```python
my_cg.export(file='C:/Users/Stephen/CGsettings/my_cg_settings.json', merged=True)
```