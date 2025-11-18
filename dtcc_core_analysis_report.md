# DTCC Core - Comprehensive Analysis Report

## Executive Summary

DTCC Core provides the core functionality for DTCC Platform, including data modeling, data wrangling, data generation, and data input/output. This is the foundational repository that the main dtcc package depends on. The repository has been actively developed since September 2024 with 361 total commits across 6 unique contributors.

**Repository**: https://github.com/dtcc-platform/dtcc-core
**License**: MIT License
**Current Version**: 0.9.3dev
**Repository Age**: ~1.2 years (September 16, 2024 - November 3, 2025)
**Location**: /Users/vasnas/scratch/dtcc-core

---

## Repository Metrics

### Size and Structure
- **Total repository size**: 33 MB
- **Git repository size**: 15 MB
- **Total tracked files**: 966 files
- **Python files**: 182 files
- **Total Python lines of code**: 16,368 lines
- **Total C++ lines of code**: 240,768 lines

### Primary Programming Languages
- **C++**: 427 files (240,768 lines) - Core computational algorithms
- **Python**: 182 files (16,368 lines) - API and bindings
- **CMake**: Build configuration
- **YAML** (CI/CD): 2 workflow files

### Directory Structure and Sizes
- `/dtcc_core`: 16 MB (main source code)
- `/tests`: 1.7 MB (test suite, 39 test files)
- `/scripts`: 380 KB (utility scripts)
- `/sandbox`: 52 KB (experimental code)
- `/.github`: CI/CD workflow configurations

---

## Commit Analysis

### Total Commits
**361 commits** spanning from September 2024 to November 2025

**Commits by Year**:
- **2024**: 99 commits (September - December, initial development)
- **2025**: 262 commits (January - November)

### Commit Activity by Month

**2024**:
- September: 15 commits (initial development)
- October: 11 commits
- November: 29 commits
- December: 44 commits

**2025 (Most Active Months)**:
- **February 2025**: 111 commits (peak activity)
- **September 2025**: 39 commits
- **June 2025**: 21 commits
- **January 2025**: 20 commits
- **July 2025**: 18 commits
- **October 2025**: 17 commits

### Recent Activity
**Last 3 months**: 58 commits showing active development
- Most recent commits focus on tetgen wrapper renaming and parameter exposure
- Latest commit: November 3, 2025

### Commit Patterns
Based on analysis of recent commit messages:
- Merge commits: 16
- Add commits: 20+ (Added, Add)
- Fix commits: 8+ (fix, Fix, Fixed, Fixing)
- Remove commits: 5+ (remove, Removed)
- Update commits: frequent (Updatepackage, etc.)

---

## Author Statistics

### Total Unique Authors
**6 contributors**

### Top Contributors by Commit Count

1. **Dag Wästberg** (dwastberg@gmail.com)
   - 177 commits (49.0%)
   - Primary contributor

2. **Vasilis Naserentin** (combined)
   - 79 commits total (21.9%)
   - 125367195+vbassn@users.noreply.github.com: 63 commits
   - vasilis.naserentin@chalmers.se: 16 commits

3. **George Spaias / georspai** (spaikgeo@gmail.com)
   - 52 commits (14.4%)

4. **Anders Logg** (logg@chalmers.se)
   - 44 commits (12.2%)

5. **Themistoklis Arvanits** (combined)
   - 9 commits total (2.5%)
   - themistoklisarv2001@gmail.com: 9 commits
   - Themis: 6 commits

### Contributor Email Domains
- **gmail.com**: 238 commits (65.9%) - Personal/GitHub emails
- **chalmers.se**: 60 commits (16.6%) - Academic/institutional
- **users.noreply.github.com**: 63 commits (17.5%) - GitHub users

### Key Contributors
Based on pyproject.toml and README.md authors sections:
1. Anders Logg (logg@chalmers.se)
2. Vasilis Naserentin (vasilis.naserentin@chalmers.se)
3. Dag Wästberg (dwastberg@gmail.com)
4. George Spaias (gspaiasa@ece.auth.gr)
5. Jens Olsson (jens.olsson@chalmersindustriteknik.se)
6. Orfeas Eleutheriou
7. Anton Olsson
8. Anton Annlöv

---

## Branching and Release Strategy

### Main Branches
- **main**: Release branch
- **develop**: Development branch
- **dev/wrapper-spade**: Currently active development (current HEAD)

### Development Branches (remote)
- dev/mixin_refactor
- dev/new-volume-mesh-builder-testing
- dev/new_city_API
- dev/parallel
- dev/surface_tiling
- dev/tree_extractor
- builderror
- githubapi

### Tags/Releases
- **v0.9.3dev** (current development)
- **v0.9.3**
- **v0.9.1dev**
- **v0.9.1**
- **v0.9.0dev**
- **v0.9.0**

Semantic versioning is used, currently approaching 1.0.0 release.

---

## CI/CD Infrastructure

### GitHub Actions Workflows

**1. ci-build-tests.yml**: Comprehensive build and test workflow
- **Trigger**: Push/PR to develop and main branches
- **Multi-OS Testing**: Ubuntu, macOS, Windows
- **Python Version**: 3.11
- **Test Framework**: pytest with coverage (pytest-cov)
- **Coverage Requirements**: Tests with coverage on Ubuntu
- **Public API Verification**: Enforces that all public API functions are tested
  - Uses `scripts/check_public_api_calls.py` in strict mode
  - Ensures every exported function is exercised by tests
- **Slack Notifications**: Success/failure notifications via webhooks
  - Success → SLACK_WEBHOOK_URL_GITHUB
  - Failure → SLACK_WEBHOOK_URL_DEVELOPMENT

**2. ci-wheels.yml**: Wheel building and distribution
- **Purpose**: Build distributable wheel packages
- **Platforms**: Multi-platform wheel building

### Quality Practices
- **Multi-OS CI/CD**: Ubuntu, macOS, Windows
- **Test Coverage**: pytest with coverage reporting
- **Public API Testing**: All exported functions must be tested
- **Code Coverage**: Generated as JSON for analysis
- **Slack Integration**: Team notifications on build status
- **Editable Install**: Uses `pip install -e .` for accurate coverage

### Testing Infrastructure
- **39 test files** covering builder, io, and model modules
- **Test Categories**:
  - Builder tests: 12 files
  - I/O tests: 12 files
  - Model tests: 10 files
- **Test Coverage Verification**: Script checks all `__all__` exports are tested
- **Makefile Shortcuts**:
  - `make install` - Install package and test tooling
  - `make test` - Run test suite
  - `make coverage` - Run tests with coverage
  - `make check-public-api` - Verify all public functions tested
  - `make verify-public-api` - Run coverage + API check

---

## Code Organization

### Source Code Structure (`/dtcc_core/`)

**Main Package Structure**:
- `__init__.py` (8 lines): Main package exports
  - Imports: common, model, builder, io
  - Logging functions
  - register_model_method utility

- `logging.py` (66 lines): Logging configuration

- **CMakeLists.txt**: C++ build configuration for pybind11 bindings

### Core Modules

#### 1. **model/** - Data Model Classes
- `object/` - City elements (City, Building, Terrain, RoadNetwork, etc.)
- `geometry/` - Spatial representations (Mesh, PointCloud, Surface, etc.)
- `values/` - Associated data (Field, Raster)
- `mixins/` - Mixin classes for extending functionality
- `dtcc_pb2` - Protobuf definitions

#### 2. **builder/** - Building and Processing Functions
- `building/` - Building-specific builders
- `city/` - City-level processors
- `geometry/` - General geometry creation
- `geometry_builders/` - High-level geometry builders (terrain, buildings, meshes)
- `meshing/` - Mesh generation and processing
- `pointcloud/` - Point cloud operations
- `polygons/` - Polygon processing
- `raster/` - Raster operations
- `roadnetwork/` - Road network processing
- `surface/` - Surface operations
- `trees/` - Tree processing

#### 3. **io/** - Input/Output Functions
- `cityjson/` - CityJSON import/export
- `container/` - Container formats
- `data/` - Data download and acquisition
- `scripts/` - I/O utility scripts
- Modules for various formats: pointcloud, meshes, raster, footprints, city, roadnetwork, landuse

#### 4. **common/** - Common Utilities
- Logging functions (debug, info, warning, error, critical)
- Logger initialization

#### 5. **cpp/** - C++ Core Implementation
- `include/` - C++ header files
- `external/` - External C++ libraries (including AMGCL)
- Core computational algorithms in C++
- pybind11 bindings for Python integration

### Largest Python Files (by line count)
1. **dtcc_core/builder/polygons/polygons.py** - 815 lines
2. **dtcc_core/model/object/object.py** - 515 lines
3. **dtcc_core/io/data/lidar.py** - 506 lines
4. **dtcc_core/builder/meshing/mesh_tiler.py** - 491 lines
5. **dtcc_core/builder/geometry_builders/meshes.py** - 415 lines
6. **dtcc_core/model/geometry/bounds.py** - 383 lines
7. **dtcc_core/io/meshes.py** - 383 lines
8. **dtcc_core/builder/geometry_builders/buildings.py** - 377 lines
9. **dtcc_core/io/footprints.py** - 361 lines
10. **dtcc_core/model/geometry/surface.py** - 344 lines

### Test Suite (`/tests/`)
**39 test files** organized by module:

**Builder Tests** (12 files):
- test_builder_datamodel.py
- test_city_build_methods.py
- test_city_processors.py
- test_extrude_surface.py
- test_flatten_geometry.py
- test_gridfield.py
- test_intersection.py
- test_merge_surfaces.py
- test_mesh_clipper.py
- test_meshing.py
- test_pointcloud_filter.py
- test_roadnetwork.py

**I/O Tests** (12 files):
- test_city.py, test_city_load_methods.py
- test_cityjson_city_writing.py, test_cityjson_converters.py
- test_landuse.py, test_load_footprints.py
- test_mesh.py, test_pointcloud.py
- test_pointcloud_container.py, test_raster.py
- test_roadnetwork.py, test_write_cityjson.py

**Model Tests** (10 files):
- test_add_attributes.py, test_bounds.py
- test_city.py, test_linestring.py
- test_multilinestring.py, test_multisurface.py
- test_pointcloud.py, test_raster.py
- test_roadnetwork.py, test_surface.py

---

## Dependencies

### Build System
- **scikit-build-core**: Modern CMake-based build system for Python
- **pybind11 == 2.13.***: C++/Python bindings
- **wheel**: Package building

### Core Runtime Dependencies (33 packages)

**Geospatial and GIS**:
- **Fiona** >= 1.8.0, < 2.0.0 - Vector data I/O
- **geopandas** >= 0.14.0, < 1.0.0 - Geospatial data operations
- **pyproj** >= 3.1.0, < 4.0.0 - Coordinate transformations
- **shapely** >= 2.0.0, < 3.0.0 - Geometric operations
- **rasterio** >= 1.2.0, < 2.0.0 - Raster I/O
- **rasterstats** >= 0.19.0, < 1.0.0 - Raster statistics
- **affine** - Affine transformations

**Point Cloud and LiDAR**:
- **laspy[lazrs]** >= 2.3.0, < 3.0.0 - LAS/LAZ file support
- **pypoints2grid** >= 0.1.9 - Point cloud to grid conversion

**Mesh and 3D**:
- **meshio** >= 5.0.0, < 6.0.0 - Mesh I/O (many formats)
- **pyassimp** - 3D model loading
- **pygltflib** - glTF format support

**Numerical and Scientific**:
- **numpy** >= 1.20.0, < 3.0.0 - Numerical arrays
- **scipy** >= 1.13.0, < 2.0.0 - Scientific computing
- **scikit-image** >= 0.25.2 - Image processing

**Data and I/O**:
- **protobuf** >= 5.0.0, < 6.0.0 - Protocol buffers
- **h5py** - HDF5 file support
- **pillow** >= 9.0.0, < 12.0.0 - Image I/O

**Web and Data Acquisition**:
- **requests** - HTTP library
- **aiohttp** - Async HTTP client
- **folium** - Map visualization

**Utilities**:
- **tqdm** >= 4.66.1 - Progress bars
- **psutil** - System utilities
- **platformdirs** - Platform-specific directories
- **pybind11** - C++ bindings

**Custom DTCC Packages**:
- **dtcc-pyspade-native** - SPADE meshing wrapper

### Optional Dependencies
- **pytest**: Testing framework

### Python Version Requirement
- **Python >= 3.10**

---

## Exposed API Surface

### Package Structure
DTCC Core is the foundational library that provides all core functionality. It exposes four main modules:

**Core Modules**:
1. **dtcc_core.common** - Logging and utilities
2. **dtcc_core.model** - Data model classes
3. **dtcc_core.io** - Input/output functions
4. **dtcc_core.builder** - Builder and processing functions

### Module Exports

#### common Module
**Exported Functions (7)**:
- `init_logging()` - Initialize logging system
- `get_logger()` - Get logger instance
- `debug(message)` - Debug logging
- `info(message)` - Info logging
- `warning(message)` - Warning logging
- `error(message)` - Error logging
- `critical(message)` - Critical logging

#### model Module
**Exported Classes (18)**:

**Objects (11 classes)**:
- `Object` - Base class for all city objects
- `GeometryType` - Enum for geometry types
- `Building` - Building object
- `BuildingPart` - Building component
- `City` - Top-level city container
- `CityObject` - Generic city object
- `Terrain` - Terrain object
- `Tree` - Tree object
- `RoadNetwork` - Road network object
- `RoadType` - Enum for road types
- `Landuse` - Land use object
- `LanduseClasses` - Enum for land use classifications

**Geometries (11 classes)**:
- `Geometry` - Base geometry class
- `Bounds` - Spatial bounding box
- `Grid` - 2D structured grid
- `VolumeGrid` - 3D structured grid
- `Mesh` - Triangulated surface mesh
- `VolumeMesh` - Tetrahedral volume mesh
- `PointCloud` - 3D point cloud
- `Surface` - Planar surface
- `MultiSurface` - Multiple surfaces
- `Transform` - Coordinate transformation
- `LineString` - Linear feature
- `MultiLineString` - Multiple line strings
- **NOTE**: Missing `Polygon` from __all__ but imported

**Values (2 classes)**:
- `Field` - Scalar/vector field on geometry
- `Raster` - Georeferenced raster data

**Additional**:
- `proto` - Protobuf definitions (dtcc_pb2)

#### builder Module
**Exported Functions (14)**:

**Terrain Building (3 functions)**:
- `build_terrain_mesh()` - Build terrain mesh from point cloud or raster
- `build_terrain_raster()` - Create raster from point cloud
- `flat_terrain()` - Create flat terrain

**Building Processing (5 functions)**:
- `extract_roof_points()` - Extract roof points from point cloud
- `compute_building_heights()` - Compute building heights from raster
- `build_lod1_buildings()` - Build LOD1 building geometries
- `extrude_building()` - Extrude building footprint
- `building_heights_from_pointcloud()` - Calculate heights from point cloud

**Building Modification (4 functions)**:
- `merge_building_footprints()` - Merge nearby footprints
- `simplify_building_footprints()` - Simplify footprint geometry
- `fix_building_footprint_clearance()` - Fix minimum clearance
- `split_footprint_walls()` - Split long walls

**City Processing (3 functions)**:
- `build_city_mesh()` - Build city surface mesh
- `build_city_volume_mesh()` - Build city volume mesh
- `merge_buildings()` - Merge buildings in city
- `fix_building_clearance()` - Fix building clearances
- `clean_building_surfaces()` - Clean building surfaces

**Tree Processing (1 function)**:
- `tree_raster_from_pointcloud()` - Create tree raster

**Submodules** (imported but not in __all__):
- `model_conversion`, `meshing`, `pointcloud`, `raster`, `geometry`
- `city`, `building`, `roadnetwork`, `polygons`, `trees`

#### io Module
**Exported Functions (11)**:

**Loading Functions (9)**:
- `load_pointcloud()` - Load point cloud from file
- `load_raster()` - Load raster from file
- `load_mesh()` - Load mesh from file
- `load_volume_mesh()` - Load volume mesh from file
- `load_footprints()` - Load building footprints
- `load_cityjson()` - Load CityJSON file
- `load_city()` - Load city from file
- `load_roadnetwork()` - Load road network
- `load_landuse()` - Load land use data (not in __all__)

**Saving Functions (6)**:
- `save_pointcloud()` - Save point cloud
- `save_raster()` - Save raster
- `save_mesh()` - Save mesh
- `save_volume_mesh()` - Save volume mesh
- `save_footprints()` - Save building footprints
- `save_city()` - Save city (not in __all__)

**Data Download Functions (4)**:
- `download_data()` - Generic data download
- `download_pointcloud()` - Download point cloud data
- `download_footprints()` - Download building footprints
- `download_roadnetwork()` - Download road network
- `empty_cache()` - Clear download cache

**Additional Functions** (not in __all__):
- `load_pointcloud_directory()` - Load point cloud directory
- `load_mesh_as_city()` - Load mesh and convert to city
- `list_mesh_io()` - List supported mesh formats
- `print_mesh_io()` - Print supported mesh formats
- `write_cityjson()` - Write CityJSON file

**Submodules**:
- `pointcloud`, `meshes`, `raster`, `info`, `footprints`
- `city`, `roadnetwork`, `landuse`, `pointcloud_directory`
- `cityjson` (with cityjson and write_cityjson)
- `data` (download functions)

**Dynamic Method Addition**:
- Adds `load()` and `save()` methods to model classes
- Adds `to_df()` method to RoadNetwork

---

## Complete Function and Class Catalog

### Model Classes with Key Methods

#### 1. Object (Base Class)
**Purpose**: Base class for all city objects

**Key Methods** (based on object.py - 515 lines):
- Geometry management (add_geometry, get_geometry)
- Hierarchical structure (add_child, get_children)
- Attribute management
- Bounds calculation
- Protobuf serialization

#### 2. City
**Purpose**: Top-level container for urban elements

**Properties**:
- buildings, terrain, road_network, landuse, pointcloud, bounds

**Methods** (via mixins):
- Building management (add_buildings, remove_buildings)
- Terrain operations
- Data loading (load_footprints, load_pointcloud, load_terrain_raster)
- Data download (download_footprints, download_pointcloud)
- Processing (build_terrain, build_lod1_buildings, build_surface_mesh)
- I/O (load, save)

#### 3. Building
**Properties**:
- height, building_parts, lod0, lod1, lod2, lod3, attributes, bounds

#### 4. PointCloud
**Purpose**: 3D point cloud with classifications

**Attributes**:
- points, classification, intensity, return_number, num_returns

**Methods** (registered via builder module):
- Filtering (remove_global_outliers, statistical_outlier_filter, classification_filter)
- Spatial operations (crop, z_filter)
- Vegetation handling (remove_vegetation, get_vegetation)
- Rasterization
- I/O (save)

#### 5. Mesh
**Purpose**: Triangulated surface mesh

**Attributes**:
- vertices, faces, markers, normals

**Methods**:
- Bounds calculation
- Transformation (offset, offset_to_origin)
- Operations (merge, snap_vertices, tile)
- Extrusion (extrude_to_solid, create_printable_solid)
- I/O (save)

#### 6. Raster
**Purpose**: Georeferenced grid data

**Attributes**:
- data, georef, nodata, crs

**Properties**:
- shape, height, width, channels, bounds, cell_size, min, max

**Methods**:
- Value access (get_value, set_value)
- Bounds management
- Processing (fill_holes, fill_small_holes, resample)
- I/O (save)

#### 7. Surface
**Purpose**: Planar surface in 3D

**Attributes**:
- vertices, normal, holes

**Methods** (surface.py - 344 lines):
- Bounds and normal calculation
- Planarity checking
- Transformation (translate, set_z)
- Conversion (to_polygon, mesh)

#### 8. Bounds
**Purpose**: Spatial bounding box

**Properties** (bounds.py - 383 lines):
- xmin, ymin, xmax, ymax, zmin, zmax
- width, height, depth, area, volume, center
- Cardinal directions (north, south, east, west)

**Methods**:
- Set operations (union, intersect)
- Containment tests (contains_bounds, contains_point)
- Expansion (expand)

### Builder Functions by Category

#### Polygon Operations (polygons.py - 815 lines)
- Merging, simplification, sliver removal
- Hole removal, clearance fixing
- Side splitting, polygon merging

#### Mesh Operations (mesh_tiler.py - 491 lines, meshes.py - 415 lines)
- City mesh building (surface and volume)
- Mesh tiling for manufacturing
- Extrusion and solid creation
- Mesh merging and cleaning

#### Building Operations (buildings.py - 377 lines, modify.py - 322 lines)
- LOD1 building generation
- Height computation
- Roof point extraction
- Footprint modification

#### Point Cloud Operations (filter.py - 304 lines)
- Outlier removal (global and statistical)
- Classification filtering
- Vegetation handling
- Cropping and Z-filtering

### I/O Functions by Format

#### LiDAR Data (lidar.py - 506 lines)
- LAS/LAZ file support
- Point cloud download and caching
- Classification handling

#### Meshes (meshes.py - 383 lines)
- Multiple format support (OBJ, PLY, STL, VTK, glTF, etc.)
- Format discovery (list_io, print_io)
- Volume mesh support

#### Footprints (footprints.py - 361 lines)
- GeoJSON, Shapefile, GeoPackage support
- Building footprint download
- Coordinate transformation

#### CityJSON (converters.py - 331 lines, write_cityjson.py - 314 lines)
- CityJSON 1.1 support
- Building conversion with LOD levels
- Attribute preservation

---

## Features and Capabilities

### Core Functionality

**1. Data Acquisition**
- Download point clouds from DTCC servers
- Download building footprints (DTCC and OpenStreetMap)
- Download road networks (OpenStreetMap)
- Intelligent caching system
- Rate-limited downloads

**2. Data Modeling**
- Object-Geometry-Values hierarchy
- Multiple LOD support (LOD0-LOD3)
- Protobuf serialization for efficiency
- Coordinate system management
- Hierarchical city structures

**3. Geometry Processing**
- Terrain mesh generation with conformance
- Building extrusion and LOD generation
- Point cloud filtering and classification
- Raster generation and analysis
- Polygon operations (merge, simplify, clean)
- Mesh tiling for 3D printing
- Surface operations

**4. Input/Output**
- 25+ file formats supported
- Point clouds: LAS, LAZ, CSV
- Meshes: OBJ, PLY, STL, VTK, glTF, FBX, DAE
- Vector data: GeoJSON, Shapefile, GeoPackage
- Raster data: GeoTIFF, etc.
- CityJSON 1.1 support

**5. Computational Algorithms (C++)**
- High-performance meshing algorithms
- Geometric operations
- Numerical solvers (AMGCL)
- Optimized core computations

### Advanced Features

**Mixin System**:
- Extensible class system
- Dynamic method registration
- Clean separation of concerns

**Builder Pattern**:
- Modular geometry construction
- Composable operations
- Registered methods on model classes

**Public API Testing**:
- Enforced test coverage
- All public functions must be tested
- CI verification in strict mode

---

## Design Patterns and Architecture

### 1. Object-Geometry-Values Hierarchy
Clean separation of:
- **Objects**: City elements (Building, Terrain, etc.)
- **Geometries**: Spatial representations (Mesh, PointCloud, etc.)
- **Values**: Associated data (Field, Raster)

### 2. Mixin Pattern
- Functionality added via mixins
- Separate mixins for City, PointCloud, Mesh
- Dynamic method registration

### 3. Builder Pattern
- Separate builder module
- Functions prefixed with `build_*`
- Composable operations

### 4. Protobuf Serialization
- Efficient binary format
- Language-agnostic
- Versioned data model

### 5. C++ Core with Python Bindings
- Performance-critical code in C++
- pybind11 for seamless integration
- Python API for usability

### 6. Registered Methods
- Dynamic method addition to classes
- `register_model_method` decorator
- Clean API extension

---

## Relationship to Main DTCC Package

### Integration Points

**1. Module Structure**:
- Main dtcc package imports from dtcc_core
- Four main modules: common, model, builder, io
- Direct re-export of all classes and functions

**2. Dependencies**:
- Main dtcc depends on dtcc-core via Git
- Branch: develop
- Direct Git dependency in pyproject.toml

**3. API Surface**:
- dtcc_core provides ALL functionality
- Main dtcc is a meta-package wrapper
- Additional components (dtcc-viewer) are optional

**4. Version Coordination**:
- dtcc-core: v0.9.3dev
- dtcc: v0.9.2dev
- Coordinated release strategy

---

## Key Findings and Observations

### Development Patterns

1. **Rapid Initial Development**: 99 commits in first 4 months (Sep-Dec 2024)
2. **Peak Activity**: February 2025 with 111 commits
3. **Core Team**: 2-3 primary developers (Dag, Vasilis, George) contributing 85%
4. **Active Maintenance**: 58 commits in last 3 months

### Project Focus

1. **C++ Core**: 240K+ lines of C++ for performance
2. **Python API**: Clean 16K line Python API
3. **Comprehensive Testing**: 39 test files with coverage requirements
4. **Public API Enforcement**: CI ensures all exported functions are tested
5. **Multi-Platform**: Support for Ubuntu, macOS, Windows

### Technical Architecture

1. **Hybrid Language**: C++ core with Python bindings
2. **Extensive Dependencies**: 33 runtime dependencies
3. **Geospatial Focus**: Heavy use of geospatial libraries
4. **Modern Build System**: scikit-build-core with CMake
5. **Clean Module Structure**: Well-organized codebase

### Recent Activity (October-November 2025)

1. **Wrapper Development**: Work on tetgen and pyspade wrappers
2. **Parameter Exposure**: Exposing low-level meshing parameters
3. **Boundary Markers**: Volume meshing improvements
4. **Package Renaming**: Updating references for renamed packages

---

## Comparison with Main DTCC Repository

| Metric | dtcc-core | dtcc (main) | Notes |
|--------|-----------|-------------|-------|
| **Age** | ~1.2 years | ~2.8 years | Core is newer |
| **Commits** | 361 | 964 | Main has 2.7x more commits |
| **Contributors** | 6 | 17 | Main has broader contribution |
| **Python LOC** | 16,368 | 5,739 | Core has 2.8x more Python |
| **C++ LOC** | 240,768 | 0 | Core has all C++ code |
| **Total Size** | 33 MB | 72 MB | Main is larger (docs) |
| **Python Files** | 182 | 54 | Core has 3.4x more files |
| **Test Files** | 39 | 1 | Core has comprehensive tests |
| **Dependencies** | 33 | 2 | Core has all dependencies |
| **Top Contributor** | Dag (49%) | Anders (33%) | Different leads |
| **CI Workflows** | 2 | 5 | Main has more workflows |
| **Demos** | 0 | 17 | Main has user-facing demos |

**Key Differences**:
- **dtcc-core**: Core functionality, C++ implementations, comprehensive testing
- **dtcc (main)**: Meta-package, user-facing demos, extensive documentation

---

## Summary Statistics

| Metric | Value |
|--------|-------|
| **Repository Age** | ~1.2 years (Sep 2024 - Nov 2025) |
| **Total Commits** | 361 |
| **Total Contributors** | 6 |
| **Total Files** | 966 tracked files |
| **Python Files** | 182 |
| **Python Lines** | 16,368 |
| **C++ Files** | 427 |
| **C++ Lines** | 240,768 |
| **Total Code Lines** | 257,136 |
| **Repository Size** | 33 MB |
| **Git Size** | 15 MB |
| **Branches** | 13 remote branches |
| **Tags/Releases** | 6 versions |
| **Top Contributor** | Dag Wästberg (49.0%) |
| **Most Active Month** | February 2025 (111 commits) |
| **Most Active Year** | 2025 (262 commits) |
| **Test Files** | 39 |
| **CI Workflows** | 2 |

## API Summary

| Category | Count |
|----------|-------|
| **Model Classes** | 18 (Objects: 11, Geometries: 11, Values: 2) |
| **Builder Functions** | 14+ exported |
| **I/O Functions** | 11 exported (20+ total) |
| **Common Functions** | 7 |
| **Total Exported API** | 50+ |
| **Supported File Formats** | 25+ |
| **External Dependencies** | 33 packages |

---

## Platform Philosophy

DTCC Core embodies:

**Performance**:
- C++ core for computational efficiency
- pybind11 for low-overhead bindings
- Optimized algorithms for large-scale urban data

**Modularity**:
- Clean separation: model, builder, io
- Mixin-based extensibility
- Registered method pattern

**Reliability**:
- Comprehensive test coverage
- Public API verification
- Multi-platform CI/CD

**Interoperability**:
- Protobuf for data exchange
- Support for 25+ file formats
- Standard geospatial libraries

**Scientific Rigor**:
- Academic backing (Chalmers University)
- Open-source MIT license
- Documentation-first approach

---

*Report generated: November 18, 2025*
*Analysis conducted on: /Users/vasnas/scratch/dtcc-core*
*Repository: https://github.com/dtcc-platform/dtcc-core*
