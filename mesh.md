# iota.mesh
**Description**

This module provides functionalities to operate with data from the meshes.



* [CFDMesh](#class_CFDmesh)
  * [add_cell_faces](#add_cell_faces)
  * [add_face](#add_face)
  * [add_vertex](#add_vertex)
  * [add_vertices](#add_vertices)
  * [cell](#cell)
  * [cell_faces](#cell_faces)
  * [cell_ids](#cell_ids)
  * [cell_neighbours](#cell_neighbours)
  * [cell_size](#cell_size)
  * [cell_type](#cell_type)
  * [cell_volume](#cell_volume)
  * [cells_around_vertex](#cells_around_vertex)
  * [check_consistency](#check_consistency)
  * [dimension](#dimension)
  * [edge](#edge)
  * [edge_ids](#edge_ids)
  * [edge_size](#edge_size)
  * [edges](#edges)
  * [face](#face)
  * [face_area](#face_area)
  * [face_ids](#face_ids)
  * [face_neighbours](#face_neighbours)
  * [face_size](#face_size)
  * [is_valid](#is_valid)
  * [isosurface](#isosurface)
  * [reserve_faces](#reserve_faces)
  * [reserve_vertices](#reserve_vertices)
  * [skin](#skin)
  * [slice](#slice)
  * [vertex](#vertex)
  * [vertex_ids](#vertex_ids)
  * [vertex_size](#vertex_size)
  * [vertices](#vertices)
  * [vertices_bytes](#vertices_bytes)
  * [vertices_weight](#vertices_weigth)
  * [volume](#volume)
* Package
    * [mesh_load](#mesh_load)
    * [mesh_export](#mesh_export)
    * [mesh_create_line](#mesh_create_line)
    * [mesh_create_cuboid](#mesh_create_cuboid)
    * [mesh_create_cylinder](#mesh_create_cylinder)
------

## <a id='class_CFDMesh'></a> [class CFDMesh](#class_dataset)

#### <a id='CFDMesh_ctor'></a> [iota.mesh.**CFDMesh**(id, name](#CFDMesh_ctor)

*CFD mesh class object. This object is returned when getting a mesh from a CFD dataset using [Dataset.get_mesh](datasets.md/#dataset_get_mesh) method.*

**Parameters**

- `id`: (int) id for the mesh
- `name`: (str) name for the mesh

**Example**

```python
my_mesh = iota.mesh.CFDMesh(0,'my_mesh')
```



### Methods

#### <a id='add_cell_faces'></a>[CFDMesh.add_cell_faces(type, faces)](#add_cell_faces)

*Add a new cell defined by a list of faces*

**Parameters**

- `type` : (CFDMesh.CellType) the type of the cell
- `faces` : (list of FaceHandle) a list of faces 

**Examples**

*Adding a cell of type hexahedron defined by a list of faces*

```python
my_mesh.add_cell_faces(iota.mesh.CellType.HEXAHEDRON,list_of_faces)
```

*Adding a cell of type polyhedron defined by a list of faces*

```python
my_mesh.add_cell_faces(iota.mesh.CellType.POLYHEDRON,list_of_faces)
```



#### <a id='add_face'></a>[CFDMesh.add_face(vertices,id)](#add_face)

*Add a new face defined by a list of vertices*

**Parameters**

- `vertices` : (list of VertexHandle) a list of vertices 
- `id` : (int) identifier of the face

**Examples**

*Adding a cell of type hexahedron defined by a list of faces*

```python
my_mesh.add_cell_faces(iota.mesh.CellType.HEXAHEDRON,list_of_faces)
```

*Adding a cell of type polyhedron defined by a list of faces*

```python
my_mesh.add_cell_faces(iota.mesh.CellType.POLYHEDRON,list_of_faces)
```



#### <a id='add_vertex'></a>[CFDMesh.add_vertex(vertex,id)](#add_vertex)

*Add a single new vertex to the mesh*

**Parameters**

- `vertex` : (iota.Vector3) vertex position (x,y,z)
- `id` : (int) id for the vertex

**Example**

```python
my_mesh.add_vertex(iota.Vector3(0,0,0), 1)
```



#### <a id='add_vertices'></a>[CFDMesh.add_vertices(vertices)](#add_vertices)

*Add a set of new vertices to the mesh*

**Parameters**

- `vertices` : (numpy.ndarray of floats) An array with the position (x,y,z) of the vertices

**Example**

*Adding two new vertices to the mesh*

```python
ArrayOfVertices = numpy.array([(0.5,0.5,0.5), (1.3,2.8, 2.9)])
my_mesh.add_vertices(ArrayOfVertices)
```



#### <a id='cell'></a>[CFDMesh.cell(id)](#cell)

*Get the id of the vertices of a cell given its id*

**Parameters**

- `id` : (int) index of cell

**Returns**

* A **numpy.ndarray of integers** that contains the id of the vertices of the cell

**Example**

*Getting the ids of the vertices of the cell with id = 5*

```python
vertices = my_mesh.cell(id=5)
print(vertices)
```



#### <a id='cell_faces'></a>[CFDMesh.cell_faces(id)](#cell_faces)

*Get the id of the faces of a cell given its id*

**Parameters**

- `id` : (int) index of cell

**Returns**

- A **numpy.ndarray of integers** that contains the id of the faces of the cell

**Example**

*Getting the id of the faces of the cell with id = 5*

```python
faces = my_mesh.cell_face(id=5)
print(faces)
```



#### <a id='cell_ids'></a>[CFDMesh.cell_ids()](#cell_ids)

*Get the id of the cells in the mesh*

**Returns**

- A **numpy.ndarray of integers** that contains the id of cells

**Example**

```python
id_cells = my_mesh.cell_ids()
print(id_cells)
```



#### <a id='cell_neighbours'></a>[CFDMesh.cell_neighbours(id)](#cell_neighbours)

*Get the id of the cells that are neighbors of a cell given its id*

**Parameters**

- `id` : (int) index of cell

**Returns**

- A **numpy.ndarray of integers** that contains the id of the cells

**Example**

*Getting the id of the cells that are neighbors of the cell with id = 5*

```python
cells_neighbors = my_mesh.cell_neighbours(id=5)
print(cells_neighbors)
```



#### <a id='cell_size'></a>[CFDMesh.cell_size(id)](#cell_size)

*Get the number of cells in the mesh*

**Parameters**

- `id` : (int) index of cell

**Returns**

- A **integer** that represents number of cells in the mesh

**Example**

*Getting the size of the cells with id = 5*

```python
size_of_cell = my_mesh.cell_size(id=5)
print(size_of_cell)
```



#### <a id='cell_type'></a>[CFDMesh.cell_type(id)](#cell_type)

*Get the type of a cell given its id*

**Parameters**

- `id` : (int) index of cell

**Returns**

- A **iota.mesh.CellType** that represents the type of the cell

**Example**

*Getting the type of the cell with id = 5*

```python
type_of_cell = my_mesh.cell_type(id=5)
print(type_of_cell)
```



#### <a id='cell_volume'></a>[CFDMesh.cell_volume(id)](#cell_volume)

*Get the volume of a cell given its id*

**Parameters**

- `id` : (int) index of cell

**Returns**

- A **float** that represents the volume of the cell

**Example**

*Getting the volume of the cell with id = 5*

```python
volume_of_cell = my_mesh.cell_volume(id=5)
print(volume_of_cell)
```



#### <a id='cells_arround_vertex'></a>[CFDMesh.cells_around_vertex(id)](#cells_around_vertex)

*Get the id of the cells around a vertex given its id*

**Parameters**

- `id` : (int) index of the vertex

**Returns**

- A **numpy.ndarray of integers** with the id of the cells

**Example**

*Getting the id of the cells around the vertex with id = 5*

```python
id_cells = my_mesh.cells_around_vertex(id=5)
print(id_cells)
```



#### <a id='check_consistency'></a>[CFDMesh.check_consistency()](#check_consistency)

*Check if the faces of the boundary of the mesh have consistent pointing normal vectors*

**Returns**

- A **tuple** of
  - A **bool** that is True if the faces have consistent pointing normal vectors
  - A **bool**  that is True if the normal vectors point inwards

**Example**

*Getting the id of the cells around the vertex with id = 5*

```python
id_cells = my_mesh.cells_around_vertex(id=5)
print(id_cells)
```



#### <a id='dimension'></a>[CFDMesh.dimension()](#dimension)

*Get the dimension of the mesh*

**Returns**

- A **integer** that represents the dimension of the mesh:
  - **0**: point mesh 
  - **1** : line segments
  - **2** : surface mesh 
  - **3** : volume mesh

**Example**

```python
mesh_dimension = my_mesh.dimension()
print(mesh_dimension)
```



#### <a id='edge'></a>[CFDMesh.edge(id)](#edge)

*Get the id of the vertices of an edge given its id*

**Parameters**

- `id` : (int) index of edge

**Returns**

- A **numpy.ndarray of integers** that contains the id of the vertices of the edge

**Example**

*Getting the ids of the vertices of the edge with id = 5*

```python
vertices_edge = my_mesh.edge(5)
print(vertices_edge)
```



#### <a id='edge_ids'></a>[CFDMesh.edge_ids()](#edge_ids)

*Get the id of the edges in the mesh*

**Returns**

- A **numpy.ndarray of integers** that contains the id of the edges

**Example**

```python
id_edges = my_mesh.edge_ids()
print(id_edges)
```



#### <a id='edge_size'></a>[CFDMesh.edge_size()](#edge_size)

*Get the number of edges in the mesh*

**Returns**

- An **integer** the corresponds to the number of edges

**Example**

```python
number_edges = my_mesh.edge_size()
print(number_edges)
```



#### <a id='edge_size'></a>[CFDMesh.edge_size()](#edge_size)

*Get the number of edges in the mesh*

**Returns**

- An **integer** the corresponds to the number of edges

**Example**

```python
number_edges = my_mesh.edge_size()
print(number_edges)
```



#### <a id='edges'></a>[CFDMesh.edges()](#edges)

*Get the pair of vertices id for all the edges in the mesh*

**Returns**

- A **numpy.ndarray of integers** that contains a pair of vertices id for each edge 

**Example**

```python
id_vertices_edges = my_mesh.edges()
print(id_vertices_edges)
```



#### <a id='face'></a>[CFDMesh.face(id)](#face)

*Get the id of the vertices of a face given its id*

**Parameters**

- `id` : (int) index of the face

**Returns**

- A **numpy.ndarray of integers** that contains the id of the vertices of the face

**Example**

*Getting the ids of the vertices of the face with id = 5*

```python
vertices_face = my_mesh.face(5)
print(vertices_face)
```



#### <a id='face_area'></a>[CFDMesh.face_area(id)](#face_area)

*Get the area of a face given its id*

**Parameters**

- `id` : (int) index of the face

**Returns**

- A **float** that represents the area of the face

**Example**

*Getting the area of the face with id = 5*

```python
area_face = my_mesh.face_area(5)
print(area_face)
```



#### <a id='face_ids'></a>[CFDMesh.face_ids()](#face_ids)

*Get the id of the faces in the mesh*

**Returns**

- A **numpy.ndarray of integers** that contains the id of the faces

**Example**

```python
id_faces = my_mesh.face_ids()
print(id_faces)
```



#### <a id='face_neighbours'></a>[CFDMesh.face_neighbours(id)](#face_neighbours)

*Get the id of the faces that are neighbors of a face given its id*

**Parameters**

- `id` : (int) index of the face

**Returns**

- A **numpy.ndarray of integers** that contains the id of the faces

**Example**

*Getting the id of the faces that are neighbors of the face with id = 5*

```python
neighbours_face = my_mesh.face_neighbours(5)
print(neighbours_face)
```



#### <a id='face_size'></a>[CFDMesh.face_size()](#face_size)

*Get the number the faces in the mesh*

**Returns**

- A **integer** that represents the number of faces

**Example**

```python
number_faces = my_mesh.face_size()
print(number_faces)
```



#### <a id='isosurface'></a>[CFDMesh.isosurface(variable, value)](#isosurface)

*Get the mesh that represents the isosurface for a constant value of a given an array of values of a variable*

**Parameters**

- `variable` : (numpy.ndarray of floats) array of values. Note the that the size of the values of the variable must be equal to the number of vertices of the input CFDMesh.
- `value`: (float) constant value of variable for the calculation of the isosurface

**Returns**

- A **iota.CFDMesh** object that contains the mesh that represents the isosurface

**Example**

*Getting the isosurface mesh from the mesh called 'my_mesh'  and based on the values of the result-analysis 'PRESSURE'-'phase-1' and a constant value of result equal to 0.0*

```python
my_cfd_mesh = my_dataset.get_mesh('my_mesh')
variable_values = my_dataset.get_result(step=0, mesh='my_mesh', result='PRESSURE', analysis='phase-1')
my_cfd_mesh.isosurface(varaibale=variable_values, value=0.0)
```



#### <a id='skin'></a>[CFDMesh.skin()](#skin)

*Get the mesh that represents the skin of a volume mesh*

**Returns**

- A **iota.CFDMesh** object that contains the mesh representing the skin of the volume mesh

**Example**

*Getting the skin of the volume mesh*

```python
skin_mesh = my_mesh.skin()
```



#### <a id='slice'></a>[CFDMesh.slice(normal, origin)](#slice)

*Get a mesh that represents a slice of a volume mesh given the normal vector (n<sub>x</sub>,n<sub>y</sub>,n<sub>z</sub> ) and the position (x,y,z) of the origin that define the slice*

**Parameters**

* `normal`: (list of floats) normal vector (n<sub>x</sub>,n<sub>y</sub>,n<sub>z</sub> ) of the slice
* `origin`: (list of float) position (x,y,z) of the slice

**Returns**

- A **iota.CFDMesh** object that contains the mesh representing the slice

**Example**

*Getting a slice with normal vector pointing the z-axis and centered at position (0,0,0)*

```python
new_slice = my_mesh.slice(normal=[0,0,1], origin=[0,0,0])
print(new_slice)
```



#### <a id='vertex'></a>[CFDMesh.vertex(id)](#vertex)

*Get the position (x,y,z) of a vertex given its id*

**Parameters**

- `id`: (int) index of the vertex

**Returns**

- A **numpy.ndarray of floats** with the position (x,y,z) of the vertex

**Example**

*Getting the position of the vertex with id=5*

```python
vertex_position = my_mesh.vertex(id=5)
print(vertex_position)
```



#### <a id='vertex_ids'></a>[CFDMesh.vertex_ids()](#vertex_ids)

*Get the id of the all the vertices in the mesh*

**Returns**

- A **numpy.ndarray of integers** with the id of the vertices

**Example**

*Getting the id of the vertices of the mesh*

```python
vertices_ids = my_mesh.vertex_ids()
print(vertices_ids)
```



#### <a id='vertex_size'></a>[CFDMesh.vertex_size()](#vertex_size)

*Get the number of vertices in the mesh*

**Returns**

- An **integer** that represents the number of vertices in the mesh

**Example**

*Getting the number of the vertices in the mesh*

```python
number_vertices = my_mesh.vertex_size()
print(number_vertices)
```



#### <a id='vertices'></a>[CFDMesh.vertices()](#vertices)

*Get the positions (x,y,z) of all the vertices in the mesh*

**Returns**

- An **numpy.ndarray of floats** that contains the positions (x,y,z) of the vertices

**Example**

*Getting the positions of the vertices in 'my_mesh'*

```python
vertices_positions = my_mesh.vertices()
print(vertices_positions)
```



#### <a id='volume'></a>[CFDMesh.volume()](#volume)

*Get the volume/area of a volume/surface mesh.*

**Returns**

- A **float** that represents the volume/area of the volume/surface mesh

**Example**

*Getting the volume of a volume mesh*

```python
volume = my_volume_mesh.volume()
print(volume)
```

*Getting the area of a surface mesh*

```python
area = my_surface_mesh.volume()
print(area)
```

### <a id='mesh_load'></a>[load(filename, [split])](#mesh_load)

*Load a mesh list from file*

*Returns a list of meshes

**Arguments**
* `filename`: (str) file containing the meshes to me readed
* `split`: (bool) split meshes by connectivities (default: True)

**Example**
```python
meshes = iota.mesh.load(
    filename = 'my_username',
    split = True
)
print(meshes)
```

### <a id='mesh_export'></a>[export(mesh, filename, [format])](#mesh_export)

*Export a mesh to file*

**Arguments**
* `mesh`: (iota.mesh.Mesh) mesh object to be exported
* `filename`: (str) file to write the mesh
* `format`: (iota.mesh.export_format) mesh format for to written (default: P4S)

**Example**
```python
status = iota.mesh.export(
    mesh = myMesh,
    filename = '/file/to/write/the/mesh/mesh.meta',
    format = iota.mesh.export_format.P4S
)
print('mesh is ok: ',status)
```


### <a id='mesh_create_line'></a>[create_line(start, end, element_size, [name])](#mesh_create_line)

*Create a linear mesh of edges*

**Arguments**
* `start`: (iota.Vector3d) point representing the origin of the line
* `end`: (iota.Vector3d) point representing the end of the line
* `element_size`: (float) size of the triangular elements
* `name`: (str) name of the mesh (default: 'line')

**Example**
```python
line = iota.mesh.create_line(
    start = iota.Vector3d(0,0,0),
    end = iota.Vector3d(1,1,0),
    element_size = 0.1,
    name = 'my_linear_mesh'
)
```


### <a id='mesh_create_circle'></a>[create_circle(centre, radius, normal, element_size, [name])](#mesh_create_circle)

*Create a circular mesh of triangles*

**Arguments**
* `centre`: (iota.Vector3d) point representing the centre of the circle
* `radius`: (float) radius of the circle
* `normal`: (iota.Vector3d) normal vector representing the plane of the circle
* `element_size`: (float) size of the triangular elements
* `name`: (str) name of the mesh (default: 'circle')

**Example**
```python
circle = iota.mesh.create_circle(
    centre = iota.Vector3d(0,0,0),
    radius = 1.0,
    normal = iota.Vector3d(0,0,1),
    element_size = 0.1,
    name = 'my_circle'
)
```


### <a id='mesh_create_rectangle'></a>[create_rectangle(origin, normal, lenght, width, element_size, [name])](#mesh_create_circle)

*Create a rectangular mesh of triangles*

**Arguments**
* `origin`: (iota.Vector3d) point representing the origin of the rectangle
* `normal`: (iota.Vector3d) normal vector representing the plane of the rectangle
* `length`: (float) length of the rectangle
* `width`: (float) width of the rectangle
* `element_size`: (float) size of the triangular elements
* `name`: (str) name of the mesh (default: 'rectangle')

**Example**
```python
rectangle = iota.mesh.create_rectangle(
    origin = iota.Vector3d(0,0,0),
    normal = iota.Vector3d(0,0,1),
    length = 1.0,
    width = 1.0,
    element_size = 0.1,
    name = 'my_rectangle'
)
```


### <a id='mesh_create_cuboid'></a>[create_cuboid(origin, up, lenght, width, height, element_size, [name], [skin])](#mesh_create_cuboid)

*Create a cuboid mesh of tetrahedra*

**Arguments**
* `origin`: (iota.Vector3d) point representing the origin of the cuboid
* `up`: (iota.Vector3d) vector representing the up direction of the cuboid
* `length`: (float) length of the cuboid
* `width`: (float) width of the cuboid
* `height`: (float) height of the cuboid
* `element_size`: (float) size of the elements
* `name`: (str) name of the mesh (default: 'cuboid')
* `skin`: (bool) generate the surface instead of volume (default: False)

**Example**
```python
cuboid = iota.mesh.create_cuboid(
    origin = iota.Vector3d(0,0,0),
    up = iota.Vector3d(0,0,1),
    length = 1.0,
    width = 1.0,
    height = 1.0,
    element_size = 0.1,
    name = 'my_cuboid'
)
```


### <a id='mesh_create_cylinder'></a>[create_cylinder(origin, up, radius, element_size, [name], [skin])](#mesh_create_cylinder)

*Create a cylinder mesh of tetrahedra*

**Arguments**
* `origin`: (iota.Vector3d) point representing the origin of the cylinder
* `up`: (iota.Vector3d) vector representing the up direction of the cylinder
* `radius`: (float) radius of the cylinder
* `height`: (float) height of the cylinder
* `element_size`: (float) size of the elements
* `name`: (str) name of the mesh (default: 'cylinder')
* `skin`: (bool) generate the surface instead of volume (default: False)

**Example**
```python
cylinder = iota.mesh.create_cylinder(
    origin = iota.Vector3d(0,0,0),
    up = iota.Vector3d(0,0,1),
    radius = 1.0,
    height = 1.0,
    element_size = 0.1,
    name = 'my_cylinder'
)
```
