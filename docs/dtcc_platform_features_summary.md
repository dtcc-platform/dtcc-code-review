# DTCC Platform - Current Features Summary

## Executive Summary

The DTCC (Digital Twin Cities Centre) Platform is an open-source Python platform for creating digital twins of cities, developed at Chalmers University of Technology. It provides a complete pipeline from geospatial data acquisition through 3D geometry generation to visualization, enabling urban modeling at city scale.

---

## Platform Architecture

The platform follows a modular architecture with three main components:

| Package | Purpose | Key Characteristic |
|---------|---------|-------------------|
| **dtcc** | Meta-package and unified API | Aggregates all functionality |
| **dtcc-core** | Core data structures and processing | C++ performance with Python API |
| **dtcc-data** | Data acquisition layer | Multi-source with intelligent caching |
| **dtcc-viewer** | Visualization (optional) | Interactive 3D rendering |

**Data Model Hierarchy:**
- **Objects**: City elements (City, Building, Terrain, RoadNetwork, Landuse, Tree)
- **Geometries**: Spatial representations (Mesh, PointCloud, Surface, Raster, VolumeMesh)
- **Values**: Associated data (Field, Raster values)

---

## Core Capabilities

### 1. Data Acquisition

**Supported Data Sources:**
- DTCC servers (curated Swedish geospatial data)
- OpenStreetMap (worldwide coverage via Overpass API)

**Data Types:**
- LiDAR point clouds (.laz format)
- Building footprints (GeoPackage, GeoJSON, Shapefile)
- Road networks (vector data)

**Features:**
- Intelligent superset-based caching (reduces API calls by ~80%)
- Asynchronous parallel downloads
- Automatic coordinate transformation (EPSG:3006 for Sweden)

### 2. Data Modeling

**Core Classes:**

| Class | Description |
|-------|-------------|
| `City` | Top-level container with buildings, terrain, roads |
| `Building` | Individual building with multi-LOD geometries |
| `PointCloud` | 3D points with classification, intensity, returns |
| `Mesh` | Triangulated surface mesh with vertices and faces |
| `VolumeMesh` | Tetrahedral mesh for simulation |
| `Raster` | Georeferenced grid data (terrain elevation, land use) |
| `Surface` / `MultiSurface` | Planar surfaces in 3D |
| `Bounds` | Spatial bounding box with set operations |

**Multi-LOD Support:**
- LOD0: 2D footprint (polygon)
- LOD1: Extruded building with flat roof
- LOD2: Detailed building with roof structure
- LOD3: Architectural detail

### 3. Geometry Processing

**Terrain Operations:**
- Build terrain mesh from point cloud or raster
- Create terrain raster from point cloud
- Terrain mesh with building footprint conformance
- Variable resolution subdomains

**Building Operations:**
- Automatic LOD1 building generation from footprints
- Height computation from point cloud or raster
- Roof point extraction
- Footprint simplification, merging, and clearance fixing

**Point Cloud Operations:**
- Global and statistical outlier removal
- Classification filtering (ground, vegetation, buildings)
- Vegetation removal/extraction
- Spatial cropping and Z-filtering
- Rasterization

**Mesh Operations:**
- Surface and volume mesh generation
- Mesh tiling for 3D printing
- Extrusion to solid
- Mesh merging and snapping

### 4. Input/Output

**Supported Formats (25+):**

| Category | Formats |
|----------|---------|
| Point Clouds | LAS, LAZ, CSV, Protobuf |
| Meshes | OBJ, PLY, STL, VTK, VTU, glTF, GLB, FBX, DAE |
| Vector Data | GeoJSON, Shapefile, GeoPackage |
| City Models | CityJSON 1.1, Protobuf |
| Raster | GeoTIFF (via rasterio) |

**Serialization:**
- Protobuf for efficient binary storage
- Language-agnostic data exchange

### 5. Visualization

**dtcc-viewer (optional):**
- Interactive 3D visualization
- View any geometry type (City, Mesh, PointCloud, Raster, etc.)
- Graceful fallback when not installed

---

## Typical Workflows

### Basic City Building
```python
import dtcc

city = dtcc.City()
city.bounds = dtcc.Bounds(xmin, ymin, xmax, ymax)
city.download_footprints()
city.download_pointcloud()
city.build_terrain(cell_size=2.0, build_mesh=True)
city.build_lod1_buildings()
city.view()
city.save("city.json")
```

### Terrain Generation
```python
pointcloud = dtcc.download_pointcloud(bounds)
pointcloud = pointcloud.remove_global_outliers(3.0)
raster = dtcc.build_terrain_raster(pointcloud, cell_size=2)
mesh = dtcc.build_terrain_mesh(raster)
mesh.view()
```

### CityJSON Export
```python
city = dtcc.load_cityjson("input.json")
dtcc.build_city_mesh(city, lod=dtcc.GeometryType.LOD1)
dtcc.write_cityjson(city, "output.json")
```

---

## Platform Statistics

| Metric | Value |
|--------|-------|
| Total Lines of Code | ~260,000 |
| Python Lines | ~25,000 |
| C++ Lines | ~240,000 |
| Supported File Formats | 25+ |
| Core Model Classes | 25+ |
| API Functions | 300+ |
| External Dependencies | 33 packages |
| Python Requirement | 3.10+ |

---

## Development Status

| Attribute | Value |
|-----------|-------|
| Current Version | 0.9.x (approaching 1.0) |
| License | MIT |
| Repository | github.com/dtcc-platform |
| Active Since | February 2023 |
| Contributors | 17+ |
| Institution | Chalmers University of Technology |

---

## Key Design Principles

1. **Interoperability**: Protobuf serialization, industry-standard file formats
2. **Modularity**: Clear separation of objects, geometries, and values
3. **Performance**: C++ core with Python bindings via pybind11
4. **Extensibility**: Mixin-based architecture, attribute dictionaries
5. **City-Scale Focus**: Designed for urban digital twins, not individual buildings

---

*Summary generated: November 2025*
*Source: Analysis of dtcc, dtcc-core, and dtcc-data repositories*
