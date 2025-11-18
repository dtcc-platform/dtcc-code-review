# DTCC Platform - Comprehensive Analysis Report

## Executive Summary

The DTCC (Digital Twin Cities Centre) repository is a meta-package that serves as the primary interface for the DTCC Platform, an open-source platform for digital twinning of cities developed at Chalmers University of Technology. The repository has been actively developed since February 2023 with 964 total commits across 17 unique contributors.

**Repository**: https://github.com/dtcc-platform/dtcc
**License**: MIT License (Copyright 2023 DTCC Platform)
**Current Version**: 0.9.2dev
**Repository Age**: ~2.8 years (February 27, 2023 - November 15, 2025)
**Location**: /Users/vasnas/scratch/dtcc

---

## Repository Metrics

### Size and Structure
- **Total repository size**: 72 MB
- **Git repository size**: 60 MB
- **Total tracked files**: 122 files
- **Total lines of code**: 60,119 lines

### Primary Programming Languages
- **Python**: 53 files (5,739 lines)
- **reStructuredText** (documentation): 19 files
- **YAML** (CI/CD): 7 files
- **Markdown**: 2 files
- **Images**: 13 JPG files, 2 SVG files

### Directory Structure and Sizes
- `/docs`: 12 MB (documentation)
- `/sandbox`: 288 KB (experimental/testing code, 27 Python files)
- `/demos`: 68 KB (17 demo Python files)
- `/src`: 28 KB (core package code)
- `/workflows`: 5 workflow Python files
- `/tests`: 1 test file
- `/utils`: Utility scripts
- `/build`: Build artifacts

---

## Commit Analysis

### Total Commits
**964 commits** spanning from February 2023 to November 2025

**Commits by Year**:
- **2023**: 459 commits (initial development phase)
- **2024**: 211 commits
- **2025**: 294 commits (as of November 18, 2025)

### Commit Activity by Month (Most Active)
- **February 2025**: 193 commits
- **August 2023**: 174 commits (early development surge)
- **September 2023**: 104 commits
- **December 2024**: 48 commits
- **May 2024**: 52 commits

### Recent Activity
**Last 3 months**: 16 commits showing steady maintenance
- Most recent commits focus on submodule imports and IntelliSense improvements
- Latest commit: November 15, 2025

### Commit Type Breakdown
- **"Update" commits**: 200
- **"Add" commits**: 139
- **"Fix" commits**: 107
- **Merge commits**: 79 (88 merge-related commits found)
- **"Remove/Delete" commits**: 27

### Commit Patterns
- Heavy focus on documentation updates
- Regular CI/CD workflow improvements
- Demo additions and updates
- Version bumping and release management
- Dependency management changes

---

## Author Statistics

### Total Unique Authors
**17 contributors** (16 human + 1 bot)

### Top Contributors by Commit Count

1. **Anders Logg** (logg@chalmers.se)
   - 317 commits (32.9%)

2. **Vasilis Naserentin** (combined)
   - 295 commits total (30.6%)
   - 125367195+vbassn@users.noreply.github.com: 268 commits
   - vasilis.naserentin@chalmers.se: 27 commits

3. **Dag Wästberg** (dwastberg@gmail.com)
   - 176 commits (18.3%)

4. **George Spaias** (georspai/spaikgeo@gmail.com)
   - 67 commits (7.0%)

5. **Sanjay Somanath** (snjsomnath)
   - 63 commits (6.5%)

6. **Jens Olsson** (jens.olsson@chalmersindustriteknik.se)
   - 17 commits (1.8%)

7. **Themistoklis Arvanits**
   - 19 commits combined (2.0%)

8. **Others**: <1% each

### Contributor Email Domains
- **chalmers.se**: 344 commits (35.7%) - Academic/institutional
- **users.noreply.github.com**: 335 commits (34.7%) - GitHub users
- **gmail.com**: 263 commits (27.3%) - Personal emails
- **chalmersindustriteknik.se**: 17 commits (1.8%) - Industry partner
- **develop.dtcc**: 4 commits - Development server
- **Other**: 1 commit

### Key Contributors
Based on pyproject.toml authors section:
1. Dag Wästberg (dwastberg@gmail.com)
2. Anders Logg (logg@chalmers.se)
3. Vasilis Naserentin (vasilis.naserentin@chalmers.se)
4. George Spaias (gspaiasa@ece.auth.gr)
5. Jens Olsson (jens.olsson@chalmersindustriteknik.se)
6. Themistoklis Arvanitis (thearva@chalmers.se)

---

## Branching and Release Strategy

### Main Branches
- **main**: Release branch
- **develop**: Development branch (current HEAD)

### Development Branches (remote)
- dev/dtcc-core
- dev/iboflow
- dev/lod2
- dev/new-volume-mesh-builder-testing
- dev/sanjayworkflow
- city_surface_mesh
- dem-demo
- new_data_model_demos

### Tags/Releases
- v0.9.2dev (current development)
- v0.9.2
- v0.9.1dev
- v0.9.1

---

## CI/CD Infrastructure

### GitHub Actions Workflows

1. **ci-build-tests.yml**: Runs on push/PR to develop and main
   - Tests on Ubuntu, Python 3.11
   - Includes Slack notifications on success/failure

2. **ci-demos.yml**: Runs demos as integration tests
   - Multi-OS testing (Ubuntu, macOS, Windows)
   - Python 3.11 and 3.12

3. **ci-docs.yml**: Documentation building and deployment

4. **ci-wheels.yml**: Wheel building for distribution

5. **dtcc-data-hourly.yml**: Hourly automated testing
   - Runs download_data.py demo every hour
   - Multi-OS and multi-Python version testing

---

## Code Organization

### Source Code (`/src/dtcc/`)

**`__init__.py`** (85 lines): Main package initialization
- Imports from dtcc_core submodules (common, model, io, builder)
- Conditional dtcc_viewer import with fallback
- Lazy loading implementation for IntelliSense
- TYPE_CHECKING block for static analysis

**`logging.py`** (6 lines): Logging utilities

### Demos (`/demos/`): 17 demonstration scripts
- build_city.py
- build_city_mesh.py
- build_city_mesh_from_cityjson.py
- build_city_surface_mesh.py
- build_city_volume_mesh.py
- build_lod1_buildings.py
- build_terrain_mesh.py
- build_terrain_mesh_with_footprints.py
- build_terrain_raster.py
- build_view_cityjson.py
- create_cityjson.py
- create_tiled_city_mesh.py
- download_data.py
- simplify_building_footprints.py
- view_cityjson.py
- view_pointcloud.py
- CI/comment_out.py

### Largest Python Files (by line count in sandbox)
1. meshing.py (611 lines)
2. test.py (netgen, 596 lines)
3. partition_sweden.py (591 lines)
4. lloyd_smoothing_3d_new.py (417 lines)
5. lloyd_smoothing_3d.py (365 lines)

### Workflows (`/workflows/`): 5 workflow documentation files
- workflow_dte.py (energy viewer)
- workflow_iboflow.py
- workflow_sanjay.py
- workflow_sfpg.py
- workflow_table.py

### Documentation (`/docs/`): 19 RST files
- Comprehensive API documentation
- Data model documentation
- Development guidelines
- Demo documentation with images
- Installation and usage guides

### Tests (`/tests/`)
**test_init.py** (41 lines): Package initialization tests
- Tests logging functions
- Tests __all__ list population
- Tests imported module symbols
- Tests viewer availability handling

---

## Dependency Repositories

### Core Dependencies

**1. dtcc-core**
- **Repository**: https://github.com/dtcc-platform/dtcc-core
- **Branch Referenced**: develop
- **Installation**: Direct Git dependency
- **Modules Imported**:
  - dtcc_core.common
  - dtcc_core.model
  - dtcc_core.io
  - dtcc_core.builder
- **Role**: Core functionality for DTCC Platform

**2. dtcc-viewer** (Optional Dependency)
- **Repository**: https://github.com/dtcc-platform/dtcc-viewer
- **Branch Referenced**: develop
- **Installation**: Optional dependency via `pip install dtcc[viewer]`
- **Dependencies**: Requires GLFW for graphical rendering
- **Role**: Visualization capabilities for DTCC objects
- **Fallback**: Package provides default_view method when viewer unavailable

**3. dtcc-data**
- **References Found**: Import in `src/dtcc/__init__.py` TYPE_CHECKING block
- **Role**: Data handling and processing
- **Note**: Now appears to be wrapped under dtcc-core based on commit messages

### Other DTCC Platform Projects
From `utils/projects.csv`, the broader DTCC Platform includes:
1. dtcc-common
2. dtcc-model
3. dtcc-io
4. dtcc-data
5. dtcc-wrangler
6. dtcc-builder
7. dtcc-viewer
8. dtcc (main repository)

### External Dependencies
From `pyproject.toml`:
- **Build System**: setuptools>=61.0.0, wheel
- **Runtime**:
  - tqdm>=4.67.1 (progress bars)
  - Python>=3.10
- **Testing**: pytest
- **Documentation**: sphinx, sphinx-immaterial

---

## Exposed API Surface

### Package Structure
The `dtcc` package is a **meta-package** that serves as the unified interface to the DTCC Platform. It imports and re-exports symbols from four core submodules from `dtcc-core`:

**Core Modules Imported:**
- `dtcc_core.common` - Common utilities and base classes
- `dtcc_core.model` - Data model classes (Objects, Geometries, Values)
- `dtcc_core.io` - Input/output functions for various file formats
- `dtcc_core.builder` - Builder functions for creating geometries and processing data

**Additional Capabilities:**
- Custom logging functions: `debug()`, `info()`, `warning()`, `error()`, `critical()`
- Optional viewer support via `dtcc_viewer` (with graceful degradation to headless mode)
- Automatic export of all symbols from submodules to top-level namespace

**Type Checking Support:**
- TYPE_CHECKING blocks enable IntelliSense and autocomplete in IDEs
- Full IDE support for `dtcc.<symbol>` while keeping imports dynamic

---

## Core Model Classes

### 1. City (`dtcc.City`)

**Properties:**
- `buildings` - List of Building objects
- `terrain` - Terrain object
- `num_buildings` - Number of buildings
- `pointcloud` - Point cloud geometry
- `bounds` - Spatial bounds

**Core Methods:**
- `add_building(building)` - Add single building
- `add_buildings(buildings, remove_outside_terrain=False)` - Add multiple buildings
- `remove_buildings()` - Remove all buildings
- `replace_buildings(buildings)` - Replace all buildings
- `add_terrain(terrain)` - Add terrain (Raster or Mesh)
- `remove_terrain()` - Remove terrain
- `has_terrain()` - Check if terrain exists
- `get_building_attribute(attribute)` - Get attribute from all buildings
- `set_building_attribute(attribute, values)` - Set attribute for all buildings
- `get_building_attributes()` - Get all attributes as dict

**Data Loading Methods:**
- `load_footprints(path, user_city_bounds=False)` - Load building footprints
- `load_pointcloud(path, remove_global_outliers=3.0, user_city_bounds=False)` - Load point cloud
- `load_terrain_raster(path)` - Load terrain raster

**Data Download Methods:**
- `download_footprints(bounds=None)` - Download building footprints
- `download_pointcloud(bounds=None, filter_on_z_bounds=False, remove_global_outliers=3.0)` - Download point cloud

**Building/Processing Methods:**
- `build_terrain(pc=None, cell_size=2.0, build_mesh=True, max_triangle_size=5.0, smoothing=3)` - Build terrain
- `build_lod1_buildings(...)` - Build LOD1 building geometries
- `build_surface_mesh(...)` - Build city surface mesh

**Save Methods:**
- `save(path)` - Save city to file
- `save_building_footprints(path)` - Save buildings as shapefile/geojson/geopackage
- `save_pointcloud(path)` - Save point cloud to LAS/CSV
- `save_geojson(path)` - Save city as GeoJSON

**Viewer Method:**
- `view()` - Visualize city

### 2. Building (`dtcc.Building`)

**Properties:**
- `height` - Building height
- `building_parts` - List of BuildingPart objects
- `lod0` - LOD0 geometry (footprint)
- `lod1` - LOD1 geometry (extruded)
- `lod2` - LOD2 geometry
- `lod3` - LOD3 geometry
- `attributes` - Dictionary of attributes
- `bounds` - Spatial bounds

**Methods:**
- `add_geometry(geometry, geometry_type)` - Add geometry
- `add_child(child)` - Add child object
- `add_mesh(mesh)` - Add mesh geometry
- `add_point_cloud(pointcloud)` - Add point cloud
- `add_raster(raster)` - Add raster
- `view()` - Visualize building

### 3. PointCloud (`dtcc.PointCloud`)

**Attributes:**
- `points` - numpy array (n, 3) of point coordinates
- `classification` - numpy array of point classifications
- `intensity` - numpy array of point intensities
- `return_number` - numpy array of return numbers
- `num_returns` - numpy array of number of returns

**Properties:**
- `bounds` - Spatial bounds

**Core Methods:**
- `calculate_bounds()` - Calculate bounding box
- `used_classifications()` - Get set of unique classifications
- `remove_points(indices)` - Remove points by indices
- `keep_points(indices)` - Keep only specified points
- `merge(other)` - Merge another point cloud
- `offset(offset)` - Apply offset to points

**Filter Methods:**
- `remove_global_outliers(margin=3.0)` - Remove Z-value outliers
- `statistical_outlier_filter(neighbours=5, outlier_margin=1.0)` - Statistical outlier removal
- `classification_filter(classes, keep=False)` - Filter by classification
- `crop(bounds)` - Crop to bounds
- `z_filter(zmin, zmax)` - Filter by Z-range
- `remove_vegetation()` - Remove vegetation points
- `get_vegetation()` - Get only vegetation points

**Builder Methods:**
- `rasterize(cell_size, bounds=None, window_size=3, radius=0, ground_only=True, fill_holes=True)` - Convert to raster

**I/O Methods:**
- `save(path)` - Save to file
- `view(data=None)` - Visualize point cloud

### 4. Mesh (`dtcc.Mesh`)

**Attributes:**
- `vertices` - numpy array of vertices
- `faces` - numpy array of triangle faces
- `markers` - numpy array of face markers
- `normals` - numpy array of normals

**Properties:**
- `num_vertices` - Number of vertices
- `num_faces` - Number of faces
- `bounds` - Spatial bounds

**Core Methods:**
- `calculate_bounds()` - Calculate bounding box
- `offset(offset)` - Apply offset to vertices
- `offset_to_origin()` - Move lower-left to origin
- `copy(geometry_only=False)` - Copy mesh

**Processing Methods:**
- `merge(other)` - Merge with another mesh
- `snap_vertices(snap_distance=0.01)` - Snap vertices to grid
- `tile(tile_size=100.0, progress=False)` - Tile mesh into smaller meshes
- `extrude_to_solid(extrusion_depth=None, base_z=None)` - Extrude to solid mesh
- `create_printable_solid(...)` - Create 3D-printable mesh
- `to_cpp()` - Convert to C++ builder mesh

**I/O Methods:**
- `save(path)` - Save to file
- `view()` - Visualize mesh

### 5. VolumeMesh (`dtcc.VolumeMesh`)

**Attributes:**
- `vertices` - numpy array of vertices
- `cells` - numpy array of tetrahedral cells
- `markers` - numpy array of cell markers

**Methods:**
- `to_cpp()` - Convert to C++ builder volume mesh
- `save(path)` - Save to file
- `view()` - Visualize volume mesh

### 6. Raster (`dtcc.Raster`)

**Attributes:**
- `data` - numpy array of raster data
- `georef` - Affine transformation
- `nodata` - No-data value
- `crs` - Coordinate reference system

**Properties:**
- `shape` - Shape of data array
- `height` - Number of rows
- `width` - Number of columns
- `channels` - Number of channels
- `bounds` - Spatial bounds
- `cell_size` - Tuple of (x_size, y_size)
- `min` - Minimum value
- `max` - Maximum value

**Methods:**
- `get_value(x, y)` - Get value at coordinate
- `set_bounds(bounds)` - Set spatial bounds
- `calculate_bounds()` - Calculate bounds
- `copy(no_data=False)` - Copy raster
- `fill_holes()` - Fill no-data holes
- `fill_small_holes(hole_size=1, nodata=None)` - Fill small holes
- `resample(cell_size=None, scale=None, method="bilinear")` - Resample
- `save(path)` - Save to file
- `view()` - Visualize raster

### 7. Surface (`dtcc.Surface`)

**Attributes:**
- `vertices` - numpy array of vertices
- `normal` - Normal vector
- `holes` - List of hole vertices

**Properties:**
- `bounds` - Spatial bounds
- `centroid` - Centroid point
- `xmin, ymin, zmin, xmax, ymax, zmax` - Bound coordinates

**Methods:**
- `calculate_bounds()` - Calculate bounding box
- `calculate_normal()` - Calculate surface normal
- `is_planar(tol=1e-5)` - Check if planar
- `translate(x=0, y=0, z=0)` - Translate surface
- `set_z(z)` - Set Z-coordinate
- `to_polygon()` - Convert to Shapely polygon
- `mesh(triangle_size=None, clean=False)` - Convert to mesh
- `view()` - Visualize surface

### 8. MultiSurface (`dtcc.MultiSurface`)

**Attributes:**
- `surfaces` - List of Surface objects

**Methods:**
- `merge(other)` - Merge with another MultiSurface
- `calculate_bounds()` - Calculate bounding box
- `view()` - Visualize multi-surface

### 9. Bounds (`dtcc.Bounds`)

**Attributes:**
- `xmin, ymin, xmax, ymax, zmin, zmax` - Boundary coordinates

**Properties:**
- `width` - X-axis extent
- `height` - Y-axis extent
- `depth` - Z-axis extent
- `north, south, east, west` - Cardinal coordinates
- `area` - 2D area
- `volume` - 3D volume
- `center` - Center point
- `tuple` - As tuple (xmin, ymin, xmax, ymax)

**Methods:**
- `union(other)` - Union with another bounds
- `intersect(other)` - Intersect with another bounds
- `contains_bounds(other)` - Check if contains other bounds
- `contains_point(x, y, z=None)` - Check if contains point
- `expand(margin)` - Expand bounds by margin
- `view()` - Visualize bounds

### 10. Additional Geometry Classes

**Polygon** (`dtcc.Polygon`)
- `vertices` - numpy array of vertices
- `holes` - List of hole vertices

**LineString** (`dtcc.LineString`)
- `vertices` - numpy array of vertices
- `view()` - Visualize linestring

**MultiLineString** (`dtcc.MultiLineString`)
- `linestrings` - List of LineString objects
- `view()` - Visualize multi-linestring

**Grid** (`dtcc.Grid`)
- `view()` - Visualize grid

**VolumeGrid** (`dtcc.VolumeGrid`)
- `view()` - Visualize volume grid

**Field** (`dtcc.Field`)
- Scalar or vector field on geometry

### 11. Additional Object Classes

**RoadNetwork** (`dtcc.RoadNetwork`)
- `vertices` - Road network vertices
- `edges` - Road network edges
- `to_df()` - Convert to pandas DataFrame
- `view()` - Visualize road network

**Terrain** (`dtcc.Terrain`)
- `raster` - Terrain raster
- `mesh` - Terrain mesh

**Landuse** (`dtcc.Landuse`)
- Land use classifications

**Tree** (`dtcc.Tree`)
- Tree objects

---

## Complete Function Catalog

### Builder Functions

#### Terrain Building
- `build_terrain_mesh(data, subdomains=None, subdomain_resolution=None, max_mesh_size=10, min_mesh_angle=20.7, smoothing=3, ground_points_only=True)` - Build terrain mesh
- `build_terrain_raster(pc, cell_size, bounds=None, window_size=3, radius=0, ground_only=True)` - Build terrain raster
- `flat_terrain(height, bounds)` - Create flat terrain

#### Building Processing
- `extract_roof_points(buildings, pointcloud)` - Extract roof points
- `compute_building_heights(buildings, raster, overwrite=True)` - Compute heights
- `build_lod1_buildings(buildings, default_ground_height=0, always_use_default_ground=False)` - Build LOD1 buildings
- `extrude_building(building, default_ground_height=0, always_use_default=False)` - Extrude building
- `building_heights_from_pointcloud(buildings, pointcloud, terrain_raster, ...)` - Calculate heights from point cloud

#### Building Modification
- `merge_building_footprints(buildings, max_distance=0.5, min_area=10)` - Merge footprints
- `simplify_building_footprints(buildings, tolerance=0.25)` - Simplify footprints
- `fix_building_footprint_clearance(buildings, clearance)` - Fix clearance
- `split_footprint_walls(buildings, max_wall_length)` - Split long walls

#### City Processing
- `build_city_mesh(city, lod=None, ...)` - Build city surface mesh
- `build_city_volume_mesh(city, domain_height=50.0, max_mesh_size=10.0, ...)` - Build city volume mesh
- `merge_buildings(city, max_distance=0.5, min_area=10)` - Merge buildings
- `fix_building_clearance(city, clearance)` - Fix clearances
- `clean_building_surfaces(city, lod, tol=1e-2)` - Clean surfaces

#### Tree Processing
- `tree_raster_from_pointcloud(pointcloud, cell_size, bounds=None)` - Create tree raster

### I/O Functions

#### Loading Functions
- `load_pointcloud(path)` - Load point cloud
- `load_raster(path, delimiter=",")` - Load raster
- `load_mesh(path)` - Load mesh
- `load_volume_mesh(path)` - Load volume mesh
- `load_mesh_as_city(path)` - Load mesh and convert to city
- `load_footprints(path, bounds=None)` - Load building footprints
- `load_city(path)` - Load city
- `load_cityjson(path)` - Load CityJSON
- `load_landuse(filename, landuse_field="DETALJTYP", landuse_datasource="LM")` - Load landuse
- `load_roadnetwork(path)` - Load road network

#### Saving Functions
- `save_pointcloud(pointcloud, path)` - Save point cloud
- `save_raster(raster, path)` - Save raster
- `save_mesh(mesh, path)` - Save mesh
- `save_volume_mesh(volume_mesh, path)` - Save volume mesh
- `save_footprints(buildings, path)` - Save footprints
- `save_city(city, path)` - Save city
- `write_cityjson(city, path)` - Write CityJSON

#### Data Download Functions
- `download_data(data_type, provider, bounds, epsg='3006', url='http://compute.dtcc.chalmers.se')` - Generic download
- `download_pointcloud(bounds, provider='dtcc', epsg='3006')` - Download point cloud
- `download_footprints(bounds, provider='dtcc', epsg='3006')` - Download footprints
- `download_roadnetwork(bounds, provider='dtcc', epsg='3006')` - Download road network
- `empty_cache(cache_type=None)` - Clear download cache

#### Info Functions
- `list_mesh_io()` - List supported mesh formats
- `print_mesh_io()` - Print supported mesh formats

### Meshing Functions

#### Mesh Creation
- `mesh_surface(surface, triangle_size=None, clean=False)` - Mesh single surface
- `mesh_multisurface(multisurface, triangle_size=None, clean=False)` - Mesh multiple surfaces
- `mesh_multisurfaces(multisurfaces, triangle_size=None, clean=False)` - Mesh list of multisurfaces

#### Mesh Operations
- `merge_meshes(meshes, weld=False, snap=0)` - Merge list of meshes
- `snap_vertices(mesh, snap_distance)` - Snap vertices to grid
- `disjoint_meshes(mesh)` - Split into disjoint components
- `tile_surface_mesh(mesh, tile_size, progress=False)` - Tile mesh
- `extrude_surface_to_solid(mesh, extrusion_depth=None, base_z=None)` - Extrude to solid
- `create_printable_surface_mesh(mesh, ...)` - Create 3D-printable mesh
- `extrude_mesh_base(mesh, extrude_to=0)` - Extrude mesh base

#### Mesh Conversion
- `mesh_to_raster(mesh, cell_size)` - Convert mesh to raster

### Point Cloud Operations

#### Filtering
- `find_global_outliers(pc, margin)` - Find global outliers
- `remove_global_outliers(pc, margin=3.0)` - Remove global outliers
- `find_statistical_outliers(pc, neighbours, outlier_margin)` - Find statistical outliers
- `statistical_outlier_filter(pc, neighbours, outlier_margin)` - Remove statistical outliers
- `find_classification(pc, classes)` - Find points by classification
- `classification_filter(pc, classes, keep=False)` - Filter by classification
- `z_range_filter(pc, min=None, max=None)` - Filter by Z-range
- `remove_vegetation(pc)` - Remove vegetation
- `get_vegetation(pc)` - Get vegetation points

#### Spatial Operations
- `pts_in_bounds(pc, bounds, xy_only=True)` - Find points in bounds
- `crop(pc, bounds, xy_only=True)` - Crop to bounds

#### Conversion
- `rasterize(pc, cell_size, bounds=None, ...)` - Convert to raster

### Raster Operations

#### Analysis
- `slope_aspect(dem)` - Calculate slope and aspect
- `TRI(dem)` - Terrain Ruggedness Index
- `TPI(dem, window_size=3)` - Topographic Position Index
- `VRM(dem, window_size=3)` - Vector Ruggedness Measure

#### Processing
- `fill_holes(raster)` - Fill nodata holes
- `fill_small_holes(raster, hole_size=1, nodata=None)` - Fill small holes
- `resample(raster, cell_size=None, scale=None, method="bilinear")` - Resample
- `remove_small_masks(raster, min_size=1, nodata=None)` - Remove small masked areas
- `erode_small_lines(raster, neighborhood_size=0, nodata=None)` - Erode small lines
- `burn_polygons(raster, polygons, values)` - Burn polygons into raster

#### Conversion
- `to_pointcloud(raster, point_classification=1, nodata=None)` - Convert to point cloud

#### Statistics
- `stats(raster, polygons, stats=["mean"])` - Calculate statistics over polygons

### Polygon/Surface Operations

#### Polygon Operations
- `merge_polygons(p1, p2, tol)` - Merge two polygons
- `simplify_polygon(polygon, tol)` - Simplify polygon
- `remove_slivers(polygon, tol)` - Remove sliver polygons
- `remove_holes(polygon)` - Remove holes
- `fix_clearance(polygons, tol)` - Fix minimum clearance
- `split_polygon_sides(polygon, max_length)` - Split long sides
- `polygon_merger(polygons, tolerance, max_distance)` - Merge multiple polygons

#### Surface Operations
- `clean_surface(surface, tol=1e-2, smallest_surface=1e-2)` - Clean surface
- `clean_multisurface(multisurface, simplify=1e-2)` - Clean multi-surface
- `subdivide_surface(surface, longest_edge=2)` - Subdivide surface
- `surface_sample_points(surface, spacing=1.0)` - Sample points
- `union_surfaces(multisurface)` - Union surfaces
- `extrude_surface(surface, height)` - Extrude surface
- `merge_coplanar(multisurface, angle=0.1, tol=1e-6)` - Merge coplanar surfaces

### Road Network Operations
- `to_matrix(roadnetwork, bidirectional=True)` - Convert to sparse matrix
- `to_surfaces(roadnetwork, width)` - Convert to surface representations

### Viewer Functions
- `view_pointcloud(pointcloud, **kwargs)` - View point cloud
- `view_mesh(mesh, **kwargs)` - View mesh
- `view_city(city, **kwargs)` - View city
- `view_building(building, **kwargs)` - View building
- `view_object(object, **kwargs)` - View generic object
- `view_raster(raster, **kwargs)` - View raster
- `view_surface(surface, **kwargs)` - View surface
- `view_bounds(bounds, **kwargs)` - View bounds
- `view_grid(grid, **kwargs)` - View grid
- `view_volume_grid(volume_grid, **kwargs)` - View volume grid
- `view_multisurface(multisurface, **kwargs)` - View multi-surface
- `view_volume_mesh(volume_mesh, **kwargs)` - View volume mesh
- `view_linestring(linestring, **kwargs)` - View linestring
- `view_multilinestring(multilinestring, **kwargs)` - View multi-linestring
- `view_roadnetwork(roadnetwork, **kwargs)` - View road network

### Logging Functions
- `debug(message)` - Log debug message
- `info(message)` - Log info message
- `warning(message)` - Log warning message
- `error(message)` - Log error message
- `critical(message)` - Log critical message
- `init_logging()` - Initialize logging
- `get_logger()` - Get logger instance

---

## Enumerations

### GeometryType
- `BOUNDS`
- `LOD0`
- `LOD1`
- `LOD2`
- `LOD3`
- `MESH`
- `VOLUME_MESH`
- `POINT_CLOUD`
- `RASTER`
- `POLYGON`
- `SURFACE`
- `MULTISURFACE`
- `LINESTRING`
- `MULTILINESTRING`

**Methods:**
- `GeometryType.from_str(s)` - Create from string
- `GeometryType.from_class_name(s)` - Create from class name
- `GeometryType.from_class(cls)` - Create from class

### RoadType
Enumeration for road types

### LanduseClasses
Enumeration for land use classifications

---

## Data Model Architecture

### Three-Tier Hierarchy

#### 1. Objects (City Elements)
- `City` - Top-level container
  - Properties: bounds, buildings, terrain, road_network, landuse
  - Methods: add_buildings(), add_terrain(), download_*(), build_*(), view(), save()
  - Supports custom geometries and field attachment

- `Building` - Individual building
  - Properties: id, height, attributes, lod0, lod1, lod2
  - LOD geometries: footprint (LOD0), simple 3D (LOD1), detailed (LOD2)
  - Extensible attributes dictionary

- `BuildingPart` - Component of a building

- `Terrain` - Ground surface representation

- `RoadNetwork` - Road infrastructure

- `Landuse` - Land classification data

#### 2. Geometries (Spatial Representations)

**2D Geometries:**
- `Grid` - Structured 2D grid with regular cells
- `Polygon` - 2D polygon with optional holes
- `LineString` / `MultiLineString` - Linear features

**3D Geometries:**
- `Mesh` - Triangulated surface mesh
  - Properties: vertices, faces
  - Methods: view(), save(), mesh(), tile(), create_printable_solid()
  - Supports welding and snapping

- `PointCloud` - Collection of 3D points
  - Properties: points, classification, colors
  - Methods: remove_global_outliers(), view()

- `Surface` / `MultiSurface` - Planar surfaces in 3D

- `VolumeGrid` - Structured 3D hexahedral grid

- `VolumeMesh` - Unstructured tetrahedral mesh

#### 3. Values (Associated Data)
- `Field` - Scalar or vector field on geometry
  - Properties: name, unit, description, values, dim
  - Supports 1D (scalar), 2D (vector), 3D (vector) fields

- `Raster` - Georeferenced grid data
  - Properties: data, georef, cell_size
  - Methods: min, max, bounds
  - Used for terrain elevation, land use classification

**Common Properties:**
- All objects have unique `id`
- All geometries auto-calculate `bounds`
- All support Protobuf serialization
- All geometries maintain coordinate system information via `Transform`

### Design Patterns

**1. Builder Pattern:**
- Separate builder module for construction operations
- Functions prefixed with `build_*`
- Modular composition of complex objects

**2. Serialization via Protobuf:**
- All model classes implement `to_proto()` and `from_proto()`
- Efficient binary serialization with `.pb` and `.pb2` formats
- Language-agnostic data exchange

**3. Multiple Geometry Representations:**
- Each Object can have multiple geometries at different LOD levels
- LOD0: Simple footprint (2D polygon)
- LOD1: Extruded building with flat roof (3D surface)
- LOD2: Detailed building with roof structure

**4. Hierarchical Object Model:**
- Parent-child relationships
- Unique identifiers for all objects
- Attributes dictionary for flexible metadata

**5. Fluent Interface:**
- Method chaining for City operations
- High-level convenience methods

---

## Supported File Formats

### Point Cloud
- **Input**: .pb, .pb2, .las, .laz, .csv
- **Output**: .pb, .pb2, .las, .laz, .csv

### City Models
- **Input**: .pb, .pb2, .cityjson
- **Output**: .pb, .pb2, .cityjson (.json)

### Meshes
- **Input**: .pb, .pb2, .obj, .ply, .stl, .vtk, .vtu, .dae, .fbx, .gltf, .gltf2, .glb
- **Output**: .pb, .pb2, .obj, .ply, .stl, .vtk, .vtu, .gltf, .gltf2, .glb, .dae, .fbx

### Footprints/Vector Data
- **Input**: .pb, .pb2, .geojson, .shp, .gpkg
- **Output**: .pb, .pb2, .geojson, .shp, .gpkg

### Data Sources
- DTCC internal data provider (default)
- OpenStreetMap (OSM) provider
- Custom file loading
- URL-based downloads

---

## Usage Patterns and Workflows

### Basic City Workflow
```python
import dtcc

# Define bounds
bounds = dtcc.Bounds(xmin, ymin, xmax, ymax)

# Create city and download data
city = dtcc.City()
city.bounds = bounds
city.download_footprints()
city.download_pointcloud()

# Build terrain and buildings
city.build_terrain(cell_size=2.0, build_mesh=True)
city.build_lod1_buildings()

# View and save
city.view()
city.save("city.json")
```

### Manual Workflow
```python
import dtcc

# Download data
bounds = dtcc.Bounds(xmin, ymin, xmax, ymax)
pointcloud = dtcc.download_pointcloud(bounds=bounds)
buildings = dtcc.download_footprints(bounds=bounds)

# Process
pointcloud = pointcloud.remove_global_outliers(3.0)
raster = dtcc.build_terrain_raster(pointcloud, cell_size=2)

# Create city
city = dtcc.City()
city.add_terrain(raster)
city.add_buildings(buildings)

# Build mesh
mesh = dtcc.build_city_mesh(city, lod=dtcc.GeometryType.LOD0)
mesh.view()
```

### Common Workflows from Demos

1. **Simple Point Cloud Viewing**
   - Download → View with color mapping

2. **Terrain Generation**
   - Download point cloud → Remove outliers → Build raster → Build mesh → View

3. **Complete City Building**
   - Download data (pointcloud + footprints)
   - Process terrain (raster + mesh)
   - Extract building heights
   - Generate LOD1 buildings
   - Assemble city model → View

4. **Terrain with Building Conformance**
   - Download data
   - Simplify and merge footprints
   - Build terrain mesh conforming to building boundaries
   - Variable resolution subdomains

5. **CityJSON Import/Export**
   - Load CityJSON from external sources
   - Add custom attributes
   - Build meshes at various LOD levels
   - Export to CityJSON

6. **Mesh Tiling for Manufacturing**
   - Build city mesh
   - Tile into printable chunks
   - Create printable solids
   - Export to STL for 3D printing

7. **City Mesh Generation**
   - Combine terrain and buildings into unified mesh
   - Support for multiple LOD levels
   - Volume mesh generation for simulation

---

## Development Practices

### Quality Practices
- CI/CD on multiple OSes (Ubuntu, macOS, Windows)
- Multiple Python versions (3.11, 3.12)
- Automated testing via GitHub Actions
- Documentation-first approach
- Code formatting with Black (Python)
- Slack notifications for build status

### Development Workflow
- Feature branches (dev/*)
- Fix branches (fix/*)
- Regular merges to develop
- Periodic releases to main with semantic versioning

### Requirements
- Python 3.10+ required
- NumPy-style docstrings for Sphinx documentation
- Git workflow: develop → feature branches → PRs
- Semantic versioning (pre-1.0 currently at 0.9.2dev)

### Platform Architecture
- Meta-package design aggregating functionality from dtcc-core
- Optional components: dtcc-viewer for visualization
- Language interoperability via Protobuf
- Support for local file operations and remote data retrieval

---

## Key Findings and Observations

### Development Patterns
1. **Active Development**: Consistent activity over 2.8 years
2. **Core Team**: 3-4 developers contributing ~80% of commits
3. **Development Workflow**: Feature branches, regular merges, periodic releases
4. **Quality Practices**: Multi-OS CI/CD, automated testing, documentation-first

### Project Focus
1. **Meta-Package Architecture**: Umbrella package importing from core components
2. **Heavy Documentation**: 12 MB docs folder, comprehensive RST documentation
3. **Demo-Driven Development**: 17 demos showcasing platform capabilities
4. **Experimental Work**: Large sandbox directory for testing new features
5. **City-Scale Digital Twins**: Focus on buildings, terrain, meshes, urban modeling

### Recent Activity (2025)
1. **Submodule improvements**: Lazy loading and IntelliSense support
2. **Dependency restructuring**: dtcc-data integrated into dtcc-core
3. **Documentation updates**: Ongoing refinement
4. **Version management**: Currently in 0.9.2dev, approaching 1.0.0

### Technical Architecture
1. **Data Model**: Object-Geometry-Values hierarchy
2. **Serialization**: Protobuf-based for efficient I/O
3. **Coordinate Systems**: Support for local and global transformations
4. **LOD Support**: Multiple levels of detail for geometries

---

## Summary Statistics

| Metric | Value |
|--------|-------|
| **Repository Age** | ~2.8 years (Feb 2023 - Nov 2025) |
| **Total Commits** | 964 |
| **Total Contributors** | 17 (16 human + 1 bot) |
| **Total Files** | 122 tracked files |
| **Total Lines** | 60,119 |
| **Python Files** | 54 (.py files) |
| **Python Lines** | 5,739 |
| **Documentation Files** | 19 (.rst files) |
| **Repository Size** | 72 MB |
| **Branches** | 12 remote branches |
| **Tags/Releases** | 4 versions |
| **Active Months** | 26 months with commits |
| **Top Contributor** | Anders Logg (32.9%) |
| **Most Active Month** | February 2025 (193 commits) |
| **Most Active Year** | 2023 (459 commits) |

## API Summary

| Category | Count |
|----------|-------|
| **Core Classes** | 25+ |
| **Top-Level Functions** | 100+ |
| **Class Methods** | 200+ |
| **Total Callable Functions** | 300+ |
| **Supported File Formats** | 25+ |

---

## Platform Philosophy

The DTCC Platform emphasizes:

- **Interoperability**: Protobuf for cross-language compatibility, support for industry standards
- **Modularity**: Clear separation of concerns (Objects/Geometries/Values)
- **Extensibility**: Attributes dictionary, custom geometries, flexible fields
- **City-Scale**: Designed for urban digital twins, not individual buildings
- **Data-to-Visualization Pipeline**: Complete workflow from raw data to 3D models

---

*Report generated: November 18, 2025*
*Analysis conducted on: /Users/vasnas/scratch/dtcc*
*Repository: https://github.com/dtcc-platform/dtcc*
