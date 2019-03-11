# [iota.dataset](#module_dataset)

**Description**
This module provides the methods to load,  access, interrogate the data from the simulation datasets. It also provides methods to a new data (e.g. custom results) to a dataset.



**Loading datasets**

* [`load_fluent`](#load_fluent)
* [`load_edem`](#load_edem)
* [`load_pa`](#load_pa)



**Accessing data** 

* [`Dataset`](#class_dataset)

  * [`__init__`](#dataset_ctor)

  - [`name`](#dataset_name)
  - [`software`](#dataset_software)
  - [`type`](#dataset_type)
  - [`reader_format`](#dataset_reader_format)

  - [`timesteps`](#dataset_timesteps)
  - [`timestep_exists`](#dataset_timestep_exists)
  - [`timestep_count`](#dataset_timesteps_count)

  - [`result_max`](#dataset_result_max)
  - [`result_min`](#dataset_result_min)
  - [`result_type`](#dataset_result_type)
  - [`results`](#dataset_results)
  - [`results_count`](#dataset_results_count)
  - [`result_exists`](#dataset_result_exists)
  - [`get_result_component`](#dataset_get_result_component)
  - [`get_result_min`](#dataset_get_result_min)
  - [`get_result_max`](#dataset_get_result_max)
  - [`get_result_component_minmax`](#dataset_get_result_component_minmax)
  - [`get_result_info`](#dataset_get_result_info)
  - [`get_result_interpreter`](#dataset_get_result_interpreter)
  - [`get_result_legend`](#dataset_get_result_legend)
  - [`get_result_legends`](#dataset_get_result_legends)
  - [`get_result_type`](#dataset_get_result_type)
  - [`get_result`](#dataset_get_result)

  - [`mesh_type`](#dataset_mesh_type)
  - [`meshes`](#dataset_meshes)
  - [`get_mesh`](#dataset_get_mesh)
  - [`get_mesh_vertices`](#dataset_get_mesh_vertices)
  - [`get_mesh_info`](#dataset_get_mesh_info)
  - [`get_particles_mesh`](#dataset_get_particles_mesh)



**Interrogating the data**

- [`Dataset`](#class_dataset)

  - [`point_evolution`](#dataset_point_evolution)

  - [`statistics_evolution`](#dataset_statistics_evolution)

  - [`line_variation`](#dataset_line_variation)

  - [`mesh_integral`](#dataset_mesh_integral)

    

**Adding and deleting data**

- [`Dataset`](#class_dataset)
  - [`set_name`](#dataset_set_name)

  - [`add_dem_mesh`](#dataset_add_dem_mesh)

  - [`add_mesh`](#dataset_add_mesh)

  - [`add_result`](#dataset_add_result)

  - [`add_slice`](#dataset_add_slice)

  - [`add_timestep`](#dataset_add_timestep)

  - [`delete_mesh`](#dataset_delete_mesh)

  - [`delete_mesh_finished`](#dataset_delete_mesh_finished)

    

------

#### <a id='load_fluent'></a>[iota.dataset.load_fluent(case_files, data_files, metadata, calculate_minmax)](#load_fluent)

*Loads a dataset from an existent ANSYS Fluent simulation. The simulation can contain DPM dataset*

**Parameters**

* `case_files`: ([str]) a list of file path/s to the case file/s of the ANSYS Fluent simulation (Default: **None**)
* `data_files`: ([str]) a list of file path/s to the data file/s of the ANSYS Fluent simulation (Default: **None**)
* `encase_files`: ([str]) a list of file path/s to the encas Ensight file/s exported from the ANSYS Fluent simulation with the DPM data (Default: **None**)
* `metadata`: (str) file path to the metadata for the dataset (Default: **None**)
* `calculate_minmax`: (bool) enables the calculation of the global min and max value for each result when loading the dataset (Default: **False**)

**Returns**

- [``Dataset``](#class_dataset): a dataset object

**Examples**
_Loading a single case file and a single data file_

```python
my_dataset = iota.dataset.load_fluent(
    case_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.cas.gz'],
    data_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.dat.gz']
)
```

_Loading a single case file and multiple data files_
```python
my_dataset = iota.dataset.load_fluent(
    case_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.cas.gz'],
    data_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation-100.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-200.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-300.dat.gz']
)
```

_Loading a single case file, a single data file and a encase file with the DPM data_
```python
my_dataset = iota.dataset.load_fluent(
    case_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.cas.gz'],
    data_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.dat.gz'],
    encase_files = [''C:\Users\Stephen\MySimulation\my_dpm_data.new.encas']
)
```

_Loading a single case file, multiple data files and specifying the path for the metadata file to be generated_
```python
my_dataset = iota.dataset.load_fluent(
    case_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.cas.gz'],
    data_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation-100.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-200.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-300.dat.gz'],
    metadata = 'C:\Users\Stephen\MySimulation\my_fluent_simulation_metadatafile.json'
)
```

_Loading the dataset using an existing metadata file previously generated by Iota_
```python
my_dataset = iota.dataset.load_fluent(
   metadata = 'C:\Users\Stephen\MySimulation\my_fluent_simulation_metadatafile.json'
)
```

_Loading a single case file and multiple data files with goblal min and max calculation for the results enabled_
```python
my_dataset = iota.dataset.load_fluent(
    case_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation.cas.gz'],
    data_files = ['C:\Users\Stephen\MySimulation\my_fluent_simulation-100.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-200.dat.gz',
        'C:\Users\Stephen\MySimulation\my_fluent_simulation-300.dat.gz'],
    calculate_minmax=True
)
```



#### <a id='load_edem'></a>[iota.dataset.load_edem(edem_file,metadata, calculate_minmax)](#load_edem)

*Loads a dataset from an existent EDEM simulation*

**Parameters**

- `edem_file`: (str) file path to the .dem file of the EDEM simulation (Default: **None**)
- `metadata`: (str) file path to the metadata for the dataset (Default: **None**)
- `calculate_minmax`: (bool) enables the calculation of the global min and max value for each result when loading the dataset (Default: **False**)

**Returns**

* [``Dataset``](#class_dataset): a dataset object 

**Examples**
_Loading a EDEM simulation_

```python
my_dataset = iota.dataset.load_edem(
    edem_file = 'C:\Users\Stephen\MyEDEMSimulation\my_edem_simulation.dem',
)
```

_Loading a EDEM simulation and specifying the path for the metadata file to be generated_

```python
my_dataset = iota.dataset.load_edem(
    edem_file = 'C:\Users\Stephen\MyEDEMSimulation\my_edem_simulation.dem',
    metadata = 'C:\Users\Stephen\MyEDEMSimulation\my_edem_simulation_metadatafile.json
)
```

_Loading the dataset using an existing metadata file previously generated by Iota_

```python
my_dataset = iota.dataset.load_edem(
   metadata = 'C:\Users\Stephen\MyEDEMSimulation\my_edem_simulation_metadatafile.json'
)
```

_Loading a EDEM simulation with goblal min and max calculation for the results enabled_

```python
my_dataset = iota.dataset.load_edem(
    edem_file = 'C:\Users\Stephen\MyEDEMSimulation\my_edem_simulation.dem',
    calculate_minmax=True
)
```



#### <a id='load_pa'></a>[iota.dataset.load_pa(metadata)](#load_edem)

*Loads dataset in Particle Analytics format: coarse-graining (pacg) or DEM (padem)*

**Parameters**

- `metadata`: (str) file path to the metadata for the dataset

**Returns**

- [``Dataset``](#class_dataset): a dataset object 

**Examples**
_Loading a coarse-graining dataset_

```python
my_dataset = iota.dataset.load_pa(
    metadata = 'C:\Users\Stephen\MyPACGDataset\my_coarse_graining_dataset.json',
)
```

_Loading a DEM dataset in Particle Analytics formart_

```python
my_dataset = iota.dataset.load_pa(
    metadata = 'C:\Users\Stephen\MyPADEMDataset\my_padem_dataset.json',
)
```



---
## <a id='class_dataset'></a> [class Dataset](#class_dataset)


#### <a id='dataset_ctor'></a> [iota.dataset.**Dataset**(filename, [mode])](#dataset_ctor)

*Dataset class object. This is returned by all the iota.dataset.load_* methods*

**Parameters**

* `filename`: (str) file path of the dataset (extension **.meta** required)
* `mode`: (IO_Type) access mode: *WRITE* or *READ_ONLY*. (Default: **iota.IO_Type.WRITE**)

**Example**

```python
my_dataset = iota.dataset.Dataset(
    filename = 'C:\Users\Stephen\MyDatasets\my_new_dataset.meta',
    mode = iota.IO_Type.WRITE
)
```



### Methods

#### <a id='dataset_name'></a>[Dataset.name()](#dataset_name)

*Get the name of the dataset*

**Returns**

* A **string** with name of the dataset

**Example**

```python
name = my_dataset.name()
print(name)
```



#### <a id='dataset_software'></a>[Dataset.software()](#dataset_software)

*Get the software of the dataset*

**Returns**

- A **string** with name of the software of the dataset

**Example**

```python
dataset_software = my_dataset.software()
print(dataset_software)
```



#### <a id='dataset_type'></a>[Dataset.type()](#dataset_type)

*Get type of the dataset*

**Returns**

* A value of type **iota.DatasetType**

**Example**

```python
dataset_type = my_dataset.type()
print(dataset_type)
```



#### <a id='dataset_reader_format'></a>[Dataset.reader_format()](#dataset_reader_format)

*Get the format of the dataset reader*

**Returns**

* A **string** with the internal reader format

**Example**

```python
dataset_reader_format = my_dataset.reader_format()
print(dataset_reader_format)
```



#### <a id='dataset_timesteps'></a>[Dataset.timesteps()](#dataset_timesteps)

*Get the list of timesteps of the dataset*

**Returns**

* A **list of strings** that contains the timesteps of the dataset

**Example**

```python
dataset_timesteps = my_dataset.timesteps()
print(dataset_timesteps)
```



#### <a id='dataset_timestep_exists'></a>[Dataset.timestep_exists(timestep, mesh)](#dataset_timestep_exists)

*Check the existence of a given step on a given mesh*

**Parameters**

* `timestep` : (int) timestep index to be checked
* `mesh` : (str) name of the mesh to be checked

**Returns**

* A **boolean** value **True** if timestep exists, or **False** otherwise

**Example**

```python
mesh_exists_at_timestep = my_dataset.timestep_exists(timestep=0, mesh='my_mesh')
print(mesh_exists_at_timestep)
```



#### <a id='dataset_timesteps_count'></a>[Dataset.timesteps_count(mesh)](#dataset_timesteps_count)

*Get the number of timesteps for a given mesh*

**Parameters**

* `mesh` : (str) name of the mesh

**Returns**

* The number of timesteps as an **integer**

**Example**

```python
Number_timesteps_for_mesh = my_dataset.timesteps_count(mesh='my_mesh')
print(Number_timesteps_for_mesh)
```



#### <a id='dataset_result_max'></a>[Dataset.result_max(result, analysis)](#dataset_result_max)

*Get the global maximum value for a given result and analysis for the whole simulation dataset*

**Parameters**

* `result` : (str) name of the result
* `analysis` : (str) name of the analysis

**Returns**

* A **float**  if the result type is scalar, or a **numpy.ndarray of floats** if the result have more than one component  

**Example**

```python
result_max = my_dataset.result_max(result='Density', analysis='none')
print(result_max)
```



#### <a id='dataset_result_min'></a>[Dataset.result_min(result, analysis)](#dataset_result_min)

*Get the global minimum value for a given result and analysis for the whole simulation dataset*

**Parameters**

* `result` : (str) name of the result
* `analysis` : (str) name of the analysis

**Returns**

* A **float**  if the result type is scalar, or a **numpy.ndarray of floats** if the result have more than one component  

**Example**

```python
result_min = my_dataset.result_min(result='Density', analysis='none')
print(result_min)
```



#### <a id='dataset_result_type'></a>[Dataset.result_type(result, analysis)](#dataset_result_type)

*Get the type of the result for a given result and analysis*

**Parameters**

* `result` : (str) name of the result
* `analysis` : (str) name of the analysis

**Returns** 

* A value of type **iota.ResultType** representing the type of the result

**Example**

```python
result_type = my_dataset.result_max(result='Density', analysis='none')
print(result_type)
```



#### <a id='dataset_results'></a>[Dataset.results(mesh)](#dataset_results)

*Get the list of all results in the dataset for all the meshes, or for a given mesh*

**Parameters**

* `mesh` : (str) name of the mesh (Default: **None**) 

**Returns** 

* A **list of strings** if none mesh name is provided , or a **list of (string,string)** pairs with result name and analysis if a mesh name is provided*

**Example**

```python
results_list = my_dataset.results()
print(results_list)

result_list_mesh = my_dataset.results(mesh='my_mesh')
print(results_list_mesh)
```



#### <a id='dataset_results_count'></a>[Dataset.results_count(mesh)](#dataset_results_count)

*Get the number of results for for a specific mesh*

**Parameters**

* `mesh` : (str) name of the mesh

**Returns** 

* An **integer** that corresponds to the number of results for the specified mesh

**Example**

```python
Number_results_mesh = my_dataset.results_count(mesh='my_mesh')
print(Number_results_mesh)
```



#### <a id='dataset_result_exists'></a>[Dataset.result_exists(step, mesh, result, analysis)](#dataset_result_exists)

*Check the existence of a given result and analysis at a given timestep and mesh*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns**

* A **bool** indicating if the result exists at the given timestep and mesh

**Example**

```python
result_exists = my_dataset(ste0=0, mesh='my_mesh',result='Density', analysis='none')
print(result_exists)
```



#### <a id='dataset_get_result_component'></a>[Dataset.get_result_component(step, mesh, result, analysis, component)](#dataset_get_result_component)

*Get the list of values per vertex/particle of a given result,analysis and component at a given step and mesh*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name
* ``component`` : (int) component index 

**Returns** 

* A value of type **numpy.ndarray of floats**  that contains the values of the component of the result. If component is **iota.ALL_COMPONENTS**, all components of the result are returned.

**Example**

```python
result_component_values = my_dataset.get_result_component(step=1, mesh='my_mesh', result='Velocity',analysis='none', component=2)
print(result_component_values)
```



#### <a id='dataset_get_result_min'></a>[Dataset.get_result_min(step, mesh, result, analysis)](#dataset_get_result_min)

*Get the minimum value of a result and analysis  at a given step and mesh*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns** 

* A **float**  if the result type is scalar, or a **numpy.ndarray of floats** if the result have more than one component . 

**Example**

```python
result_min_value = my_dataset.get_result_min(step=1, mesh='my_mesh', result='Velocity', analysis='none')
print(result_min_value)
```



#### <a id='dataset_get_result_max'></a>[Dataset.get_result_max(step, mesh, result, analysis)](#dataset_get_result_max)

*Get the maximum value of a result and analysis  at a given step and mesh*

**Parameters**

- `step` : (int) timestep index
- `mesh` : (str) mesh name
- `result` : (str) result name
- `analysis` : (str) analysis name

**Returns** 

- A **float**  if the result type is scalar, or a **numpy.ndarray of floats** if the result have more than one component . 

**Example**

```python
result_max_value = my_dataset.get_result_max(step=1, mesh='my_mesh', result='Velocity', analysis='none')
print(result_max_value)
```



#### <a id='dataset_get_result_component_minmax'></a>[Dataset.get_result_component_minmax(step, mesh, result, analysis, component)](#dataset_get_result_component_minmax)

*Get the values of the component of a result and analysis at given step and mesh ad result/analysis. It also calculates the minimum and maximum values*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int) component index

**Returns** 

* A **tuple**  composed of 
  * A **numpy.ndarray of floats** with the values of the component of the result
  * A **float** that corresponds to the minimum value of the component of the result, float)** 
  * A **float** that corresponds to the maximum value of the component of the result, float)** 

**Example**

```python
result_min_max = my_dataset.get_result_component_minmax(step=1, mesh='my_mesh', result='Velocity', analysis='none', component=2)
print(result_min_max)
```



#### <a id='dataset_get_result_info'></a>[Dataset.get_result_info(result, analysis)](#dataset_get_result_info)

*Get the metadata information of a given result and analysis. The information includes the result type, the result name, the analysis name and the list of meshes that have the given result-analysis.*

**Parameters**

* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns** 

* A **dictionary** containing the metadata information of the result

**Example**

```python
result_info = my_dataset.result_info(result='Velocity', analysis='none')
print(result_info)
```



#### <a id='dataset_get_result_interpreter'></a>[Dataset.get_result_interpreter(result, analysis)](#dataset_get_result_interpreter)

*Get the label for the components of a given result-analysis*

* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns**

* A **list of strings** with the label for each of the components of the result-analysis

**Example**

```python
result_interpreter = my_dataset.result_interpreter(result='Velocity', analysis='none')
print(result_interpreter)
```



#### <a id='dataset_get_result_legend'></a>[Dataset.get_result_legend(result, analysis, component)](#dataset_get_result_legend)

*Get the title of the legend of a given result, analysis and component.*

**Parameters**

* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int or iota.ALL_COMPONENTS) component index or all components type

**Returns**

* A **string** with the title of the legend the label for a given result/analysis, including result name, component and units (if available). If component is **iota.ALL_COMPONENTS,** a **list of strings** with legend for each component is returned.

**Examples**

*Getting the title of the legend for only one component of a result-analysis*

```python
result_legend = my_dataset.result_legend(result='Velocity', analysis='none', component=0)
print(result_legend)
```

*Getting the title of the legends for all the components of a result-analysis*

```python
result_legend = my_dataset.result_legend(result='Velocity', analysis='none', component=iota.ALL_COMPONENTS)
print(result_legend)
```



#### <a id='dataset_get_result_legends'></a>[Dataset.get_result_legends(result, analysis)](#dataset_get_result_legends)

*Get the titles of the legend for all components of a given result, analysis.*

**Parameters**

* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns**

- A **list of strings** with the titles of the legend for each component.

**Example**

```python
result_legends = my_dataset.result_legends(result='Velocity', analysis='none')
print(result_legends)
```



#### <a id='dataset_get_result_type'></a>[Dataset.get_result_type(result,analysis)](#dataset_get_result_type)

*Get result type*
*Returns a variable of type **iota.ResultType** *

* `result` : (str) result name
* `analysis` : (str) analysis name

**Example**

```python
result_type = my_dataset.get_result_type('Velocity','none')
print(result_type)
```



#### <a id='dataset_get_result'></a>[Dataset.get_result(step, mesh, result, analysis)](#dataset_get_result)

*Get the values of a given result and analysis at a given step and mesh*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name

**Returns** 

* A **numpy.ndarray of floats** with the values of the result

**Example**

```python
result_values = my_dataset.get_result(step=5, mesh='my_mesh', result='Velocity', analysis='none')
```



#### <a id='dataset_mesh_type'></a>[Dataset.mesh_type(mesh)](#dataset_mesh_type)

*Get the type of a given mesh contained in the dataset*

**Parameters**

* `mesh` : (str) mesh name

**Returns**

* A variable of type **iota.MeshType**

**Example**

```python
mesh_type = my_dataset.mesh_type(mesh='my_mesh')
print(mesh_type)
```



#### <a id='dataset_meshes'></a>[Dataset.meshes()](#dataset_meshes)

*Get the list of meshes in the dataset*

**Returns** 

* A **list of strings** with the name of the meshes

**Example**

```python
meshes_name = my_dataset.meshes()
print(meshes_name)
```



#### <a id='dataset_get_mesh'></a>[Dataset.get_mesh(mesh,step)](#dataset_get_mesh)

*Get a mesh for a given mesh name and step in the dataset*

**Parameters**

* `mesh` : (str) mesh name
* `step` : (int) timestep index

**Returns** 

* A variable of type **iota.mesh.Mesh**

**Example**

```python
mesh = my_dataset.get_mesh(mesh='my_mesh', step=0)
print(mesh) 
```



#### <a id='dataset_get_mesh_vertices'></a>[Dataset.get_mesh_vertices(mesh, step)](#dataset_get_mesh_vertices)

*Get the position (x,y,z) of the vertices of mesh at a given step*

**Parameters**

* `mesh` : (str) mesh name
* `step` : (int) timestep index

**Returns** 

* An **numpy.ndarray of floats** array containing the position [x,y,z] of each vertex in the mesh

**Example**

```python
mesh_vertices = my_dataset.get_mesh_vertices(mesh='my_mesh', step=0)
print(mesh_vertices)
```



#### <a id='dataset_get_mesh_info'></a>[Dataset.get_mesh_info(mesh)](#dataset_get_mesh_info)

*Get the metadata information on a given mesh. This includes the mesh name, mesh type and if the mesh is dynamic.*

**Parameters**

* `mesh` : (str) mesh name

**Returns** 

* A **dictionary** containing the metadata information

**Example**

```python
mesh_info = my_dataset.get_mesh_info(mesh='my_mesh')
print(mesh_info)
```



#### <a id='dataset_get_particles_mesh'></a>[Dataset.get_particles_mesh(step, mesh, variable)](#dataset_get_particles_mesh)

*Get the value of an attribute/variable  of mesh of particles at a given step*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) particles mesh name
* `variable` : (str) name of one of the following variables of a particles mesh:
  *  ``'id'``: particles identifier
  *  ``'group'``: particles group identifier
  * ``'position'``:  position (x,y,z) of the center of the particles
  * ``'orientation'``: orientation of the particles as a quaternion (q0, q1, q2, q3)
  * ``'diameter'``: diameter of the particles
  * ``'mass'``: mass of the particles
  * ``'volume'``: volume of the particles
  * ``'velocity'``:  velocity (vx,vy, vz) of the particles
  * ``'spheres'``:  position (x,y,z) and radius of the spheres of the particles

**Returns**

* A **numpy.ndarray of floats** with the values of the variable for each particle in the mesh 



**Example**

```python
particle_mesh_variable = my_dataset.get_particles_mesh(step=3, mesh='my_particles_mesh', variable='position')
```

---

#### <a id='dataset_point_evolution'></a>[Dataset.point_evolution(mesh, point, result, analysis, component, [step])](#dataset_point_evolution)

*Get the value of the component of a result and analysis at a given point (x,y,z) in the space and at a given step/s in the dataset*

**Parameters**

* `mesh` : (str) mesh name
* `point` : (list of floats or numpy.ndarray of floats) point (x,y,z) to evaluate the result 
* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int) component index
* `step` : (int or iota.ALL_STEPS) timestep index (Default: **iota.ALL_STEPS**)

**Returns**

* A **tuple** that contains: 
  * A **list of floats** with the values of the timestep/s
  * A **list** that contains a **list of floats** with the values of component of the result-analysis at the given point and at each timestep

**Example**

*Getting the value of the magnitude of the velocity in the mesh named 'my_mesh', at point (0,0.1,0.5) and at the 5th step of the dataset*

```python
ts, y = my_dataset.statistics_evolution(mesh='my_mesh', point=[0,0.1,0.5], result='Velocity', analysis='none', component=3, step=4)
print(x)
print(y)
```

*Getting the values of the magnitude of the velocity in the mesh named 'my_mesh' and over all timesteps of the dataset at point (0,0.1,0.5)*

```python
ts, y = my_dataset.statistics_evolution(mesh='my_mesh', point=[0,0.1,0.5], result='Velocity', analysis='none', component=3, step=iota.ALL_STEPS)
print(x)
print(y)
```



#### <a id='dataset_statistics_evolution'></a>[Dataset.statistics_evolution(mesh, result, analysis, component, [step], [data])](#dataset_statistics_evolution)

*Get the temporal evolution of different statistical variables at the nodes/vertices of a given mesh, result, analysis and component*

**Parameters**

* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int) component index
* `step` : (int) timestep index (Default: **iota.ALL_STEPS**)
* `data` : (list[str]) list of statistical values to be evaluated (Default: **[]**): 
  * ``'min'``: minimum value
  * ``'max'``: maximum value
  * ``'mean'``: arithmetic mean value
  * ``'stdev'``:  standard deviation value
  * ``'median'``:  median value
  * ``'cov'``: coefficient of variance value

**Returns** 

* A **tuple** that contains: 
  - A **list of floats** with the values of the timestep/s
  - A **list** that contains a **list of floats** with the values of statistical variables at each timestep/s. 

**Example**

*Getting the minimum, maximum and mean value of the magnitude of the velocity at the nodes/vertices of the mesh named 'my_mesh' and at the 5th step of the dataset*

```python
ts, y = my_dataset.statistics_evolution(mesh='my_mesh', result='Velocity', analysis='none', component=3, step=4, data=['min','max', 'mean'])
print(x)
print(y)
```

*Getting the minimum, maximum and mean value of the magnitude of the velocity at the nodes/vertices of the mesh named 'my_mesh' over all the timesteps of the dataset*

```python
ts, y = my_dataset.statistics_evolution(mesh='my_mesh', result='Velocity', analysis='none', component=3, step=iota.ALL_STEPS,data=['min','max', 'mean'])
print(x)
print(y)
```



#### <a id='dataset_line_variation'></a>[Dataset.line_variation(mesh, point_start, point_end, num_points, result, analysis, component, step, [x_type])](#dataset_line_variation)

*Extract the values of the component of result-analysis along a line defined by a given start and end point and at given timestep and mesh in the dataset*

**Parameters**

* `mesh` : (str) mesh name
* `point_start` : (list of floats or numpy.ndarray of floats) point (x,y,z) that defined the start of the line
* `point_end` : (list of floats or numpy.ndarray of floats) point (x,y,z) that defined the end of the line
* `num_points` : (int) number of points along the line to extract the values
* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int) component index
* `step` : (int) timestep index
* `x_type` : (str) defines the variable to be used to represent the position of the points in the line (Default: **'dist'**):
  *  ``'x'``:  uses the x-position of the points
  *  ``'y'``:  uses the y-position of the points
  *  ``'z'``:  uses the z-position of the points
  *  ``'dist'``:  uses the distance from the point to the start point

**Returns** 

* A **tuple** that contains: 
  - A **list of floats** with the values that represent the position of the points in the line
  - A **list** that contains a **list of floats** with the values of the component of the result-analysis at the points along the defined line

**Example**

*Getting the values of the magnitude of the velocity for the mesh called 'my_mesh' at the 6th timestep in the dataset and along a line that goes from (0,0,0) to (0,0,2.5)* 

```python
x, y = my_dataset.line_variation(mesh='my_mesh', start_point=[0,0,0], end_point=[0,0,2.5], num_points=50, resusult='Velocity', analysis='none', component=3, step=5, x_type = 'z')
print(x)
print(y)
```



#### <a id='dataset_mesh_integral'></a>[Dataset.mesh_integral(mesh, result, analysis, component, [step])](#dataset_mesh_integral)

*Get the temporal evolution integral of the component of a result-analysis over a given mesh. Volume integral is calculated for the volumetric meshes. In the case of surface meshes, the surface integral is computed.*

**Parameters**

* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name
* `component` : (int) component index
* `step` : (int) timestep index (Default: **iota.ALL_STEPS**)

**Returns**

* A **tuple** that contains: 
  - A **list of floats** with the values of the timestep/s
  - A **list** that contains a **list of floats** with the values of the integral of the component of the result-analysis over the specified mesh at the timestep/s

**Example**

*Getting the value of the integral of the magnitude of the velocity over the mesh called 'my_mesh' and at the 6th timestep in the dataset*

```python
x, y = my_dataset.mesh_integral(mesh='my_mesh', result='Velocity', analysis='none', component=3, step=5)
print(x)
print(y)
```

*Getting the temporal evolution of the integral of the magnitude of the velocity over the mesh called 'my_mesh'*

```python
x, y = my_dataset.mesh_integral(mesh='my_mesh', result='Velocity', analysis='none', component=3)
print(x)
print(y)
```



---



#### <a id='dataset_set_name'></a>[Dataset.set_name(name)](#dataset_set_name)

*Set the name of the dataset*

**Parameters**

* `name` : (str) new name for the dataset

**Example**

```python
my_dataset.set_name('new name')
print(my_dataset.name())
```



#### <a id='dataset_add_dem_mesh'></a>[Dataset.add_dem_mesh(step, mesh,[name])](#dataset_add_dem_mesh)

*Adds a mesh of particles to an existing step in the dataset*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (iota.mesh.DEM_Mesh) a mesh of particles object
* `name` : (str)  name for the mesh of particles (Default: **'particles'**)

**Example**

*Adding a new mesh of particles to the 1st step of the dataset*

```python
my_dataset.add_dem_mesh(step=0, mesh=my_DEM_particles_mesh)
```

*Adding a new mesh of particles to be called 'my_new_particles' to the 1st step of the dataset*

```python
my_dataset.add_dem_mesh(step=0, mesh=my_DEM_particles_mesh, name='my_new_particles')
```



#### <a id='dataset_add_mesh'></a>[Dataset.add_mesh(step, mesh)](#dataset_add_mesh)

*Add a mesh to an existing step in the dataset*

**Parameters**

* `step` : (int) timestep index or **iota.STATIC_MESH** if the mesh to be added is static
* `mesh` : (iota.mesh.Mesh) mesh to be added to the dataset

**Examples**

*Adding a new mesh to the 6th timestep of the dataset*

```python
my_dataset.add_mesh(step=5, mesh=my_mesh)
```
*Adding a static mesh to the dataset*

```python
my_dataset.add_mesh(step=iota.STATIC_MESH, mesh=my_static_mesh)
```



#### <a id='dataset_add_result'></a>[Dataset.add_result(step, mesh, result, analsis, data)](#dataset_add_result)

*Add a result to an existing mesh and step in the dataset*

**Parameters**

* `step` : (int) timestep index
* `mesh` : (str) mesh name
* `result` : (str) result name
* `analysis` : (str) analysis name
* `data` : (numpy.ndarray of floats) array of results to be added.

**Example**

```python
my_dataset.add_result(step=5, mesh='my_mesh', result='my_new_result', analysis='none', data=my_new_result_data)
```



#### <a id='dataset_add_slice'></a>[Dataset.add_slice(mesh, normal, origin, result, analysis, step)](#dataset_add_slice)

*Creates a slice/cut-plane of an existing mesh in the dataset. The slice is defined by the vector (nx, ny, nz) representing the normal direction to the plane of the slice and the position (x,y,z) of the point that defines the origin of the slice. The values of the results-analyses present in the dataset are interpolated at the nodes of the mesh of the slice. The mesh of the slice and its interpolated results are automatically added to the dataset as new mesh*

**Parameters**

* `mesh` : (str) name of the mesh to be cut
* `normal` : (list of floats or a numpy.ndarray of floats) vector (n<sub>x</sub>,n<sub>y</sub>,n<sub>z</sub>) representing the normal direction to define the slice/cut-plane 
* `origin` : (iota.Vector3d) vector contained in the slice/cut-plane plane
* `result` : (str) name of an existing result in the dataset to be interpolated on the slice/cut-plane. If empty, all results in the dataset are included (Default: **''**)
* `analysis` : (str) name of the analysis of an existing result in the dataset. If empty, all analysis are included (Default: **''**)
* `step` : (int) timestep index (Default: **iota.ALL_STEPS**)

**Returns**

* A **string** that corresponds to the name of the new mesh that represents the slice

**Examples**

*Creating a slice of the mesh called 'my_mesh', with normal vector pointing the z-axis and centered at position (0,0,0) for all timesteps and results-analyses*

```python
my_dataset.add_slice(mesh='my_mesh', normal=[0,0,1], origin=[0,0,0])
```

*Creating a slice of the mesh called 'my_mesh', with normal vector pointing the z-axis and centered at position (0,0,0) for all timesteps and only for the result velocity of the analysis 'phase-1'*

```python
my_dataset.add_slice(mesh='my_mesh', normal=[0,0,1], origin=[0,0,0], result='Velocity', analysis='phase-1')
```

*Creating a slice of the mesh called 'my_mesh', with normal vector pointing the z-axis and centered at position (0,0,0) for only the 4th timestep and the result velocity of the analysis 'phase-1'*

```python
my_dataset.add_slice(mesh='my_mesh', normal=[0,0,1], origin=[0,0,0], result='Velocity', analysis='phase-1', step=3)
```



#### <a id='dataset_add_timestep'></a>[Dataset.add_timestep(timestep)](#dataset_add_timestep)

*Add a new timestep to the dataset*

**Parameters**

* `timestep` : (str) timestep to be added

**Returns**

* An **integer** that corresponds to the index of the new timestep in the dataset

**Example**

```python
ts_index = my_dataset.add_timestep(timestep='15.65')
print(ts_index)
print(my_dataset.timesteps())
```



#### <a id='dataset_delete_mesh'></a>[Dataset.delete_mesh(mesh)](#dataset_delete_mesh)

*Delete an existing mesh from the dataset*

**Parameters**

* `mesh` : (str) mesh name

**Example**

```python
my_dataset.delete_mesh(mesh='my_mesh')
```



#### <a id='dataset_delete_mesh_finished'></a>[Dataset.delete_mesh_finished()](#dataset_delete_mesh_finished)

*Check if a mesh deletion process in the dataset has finished*

**Returns**

* A **tuple** that contains:
  * A **bool** with the status of the mesh deletion process. If the process finished correctly, the bool is True.
  * A **string** with a message in case an error occurred during the mesh deletion process.

**Example**

```python
status, msg = my_dataset.delete_mesh_finished()
print(status, msg)
```







