## Vector Data Model Fundamentals

### Overview

The vector data model represents geographic features as discrete geometric objects — points, lines, and polygons — defined by precise coordinate locations, in contrast to the raster model's continuous grid-cell representation. Vector data is the foundation for representing discrete, well-defined real-world features (buildings, roads, administrative boundaries, individual trees) and supports precise geometric and topological analysis.

### The Three Core Geometry Types

#### Points

A single coordinate pair (or triplet with elevation) representing a discrete, dimensionless location — used for features best represented as a single location rather than an area or line: wells, weather stations, individual trees, addresses, incident locations.

$$P = (x, y)$$ or $$P = (x, y, z)$$ for 3D point data

#### Lines (Polylines)

An ordered sequence of connected coordinate pairs (vertices) forming a one-dimensional path — used for linear features: roads, rivers, pipelines, administrative boundaries, contour lines.

$$L = \{(x_1,y_1), (x_2,y_2), \ldots, (x_n,y_n)\}$$

A line's length is computed by summing the Euclidean (or geodesic) distance between consecutive vertex pairs.

#### Polygons

A closed sequence of coordinates (the first and last coordinate identical, forming a closed ring) representing a two-dimensional bounded area — used for areal features: parcels, administrative boundaries, lakes, land use zones, building footprints.

$$\text{Polygon ring: } (x_1,y_1), (x_2,y_2), \ldots, (x_n,y_n), (x_1,y_1)$$

**Complex polygon structures**: A single polygon feature may include multiple rings — one exterior ring defining the outer boundary and zero or more interior rings ("holes") representing excluded areas within the outer boundary (e.g., a lake with an island, represented as an exterior ring for the lake and an interior ring for the island).

### Diagram: Vector Geometry Type Hierarchy

```mermaid
flowchart TD
    A[Vector Geometry Types] --> B[Point]
    A --> C[Line/Polyline]
    A --> D[Polygon]
    B --> B1[MultiPoint - multiple points as one feature]
    C --> C1[MultiLineString - multiple lines as one feature]
    D --> D1[MultiPolygon - multiple polygons as one feature]
    D --> D2[Exterior Ring + Interior Ring(s) - holes]
```

### Multipart Geometries

Real-world features often require representation as multiple disconnected geometric parts within a single logical feature (e.g., a country with islands, represented as a single "Philippines" feature containing thousands of separate polygon parts):

- **MultiPoint**: A single feature composed of multiple, non-contiguous point locations.
- **MultiLineString**: A single feature composed of multiple, potentially non-contiguous line segments.
- **MultiPolygon**: A single feature composed of multiple, potentially non-contiguous polygon rings — the most common multipart type in practice, used extensively for archipelagic nations, discontinuous administrative units, and fragmented land parcels.

```python
from shapely.geometry import MultiPolygon, Polygon

island1 = Polygon([(0,0), (2,0), (2,2), (0,2)])
island2 = Polygon([(5,5), (7,5), (7,7), (5,7)])
archipelago = MultiPolygon([island1, island2])

print(archipelago.area)       # sum of both polygon areas
print(archipelago.is_valid)   # topology validity check
```

### The Simple Features Specification

Most modern vector GIS software and file formats implement the **Simple Features** specification (OGC Simple Feature Access standard), which formally defines the geometry types above along with a standard set of spatial operations (intersects, contains, within, buffer, union, etc.) and text/binary encoding formats (Well-Known Text/WKT, Well-Known Binary/WKB).

```python
from shapely import wkt

geom = wkt.loads("POLYGON((0 0, 4 0, 4 4, 0 4, 0 0))")
print(geom.area)         # 16.0
print(geom.wkt)          # round-trip back to WKT text representation
```

### Attribute Data and the Feature Model

Vector features combine geometry with associated **attribute data** (non-spatial descriptive information) in a structured tabular format, typically implemented as a relational table where each row corresponds to one geometric feature and each column represents an attribute field.

| FeatureID | Geometry | Name | Population | Area_km2 |
| --- | --- | --- | --- | --- |
| 1 | Polygon(...) | Batac City | 55,741 | 161.5 |
| 2 | Polygon(...) | Laoag City | 111,125 | 116.1 |

This geometry-plus-attribute pairing is the conceptual foundation of virtually all vector file formats and spatial databases, and underlies the standard GIS operation of joining external tabular data to spatial features via a shared key field.

### Vector File Formats

- **Shapefile (.shp)**: A long-standing, widely-supported multi-file format (requiring companion `.shx`, `.dbf`, `.prj` files); limitations include a 2GB file size cap, 10-character attribute field name limit, and inability to store null geometries or mixed geometry types within one file.
- **GeoJSON**: A JSON-based, human-readable, web-friendly format; excellent for interoperability and small-to-medium datasets, but verbose and inefficient at scale compared to binary formats.
- **GeoPackage (.gpkg)**: A modern, SQLite-based single-file format supporting multiple layers, mixed geometry types, and large datasets without the shapefile's legacy limitations; increasingly recommended as a shapefile replacement.
- **PostGIS (PostgreSQL extension)**: A spatial database extension enabling vector data storage, indexing, and querying directly within a relational database, supporting complex spatial SQL queries and multi-user concurrent access unavailable to file-based formats.
- **FlatGeobuf**: A newer, cloud-optimized binary format supporting efficient streaming and spatial-indexed partial reads, well suited to web delivery of large vector datasets without requiring a full download before rendering begins.

```python
import geopandas as gpd

gdf = gpd.read_file("boundaries.shp")
gdf.to_file("boundaries.gpkg", driver="GPKG")   # convert to GeoPackage
gdf.to_file("boundaries.geojson", driver="GeoJSON")
```

### Topology and Spatial Relationships

**Topology** refers to the explicitly defined spatial relationships between features (adjacency, connectivity, containment) — distinct from purely geometric coordinate storage.

- **Topological data models** (e.g., the classic ESRI ARC/INFO coverage format) explicitly store shared boundaries between adjacent polygons and connectivity between line segments, ensuring, for example, that adjacent administrative boundaries share exactly the same boundary coordinates with no gaps or overlaps.
- **Non-topological (simple feature) models** (shapefiles, GeoJSON) store each feature's geometry independently, meaning adjacent polygons' shared boundaries are stored as separate, potentially slightly mismatched coordinate sequences unless carefully maintained — a common source of "sliver polygons" (thin gap or overlap artifacts) when combining datasets from different sources.

**Common topological validity rules enforced in rigorous vector data models:**

- Polygons must not self-intersect.
- Polygon boundaries must be closed (first and last vertex identical).
- Adjacent polygons should share exact boundary coordinates (no gaps or overlaps) when representing a true partition of space (e.g., administrative units with no gaps).
- Lines representing a network (roads, rivers) should properly connect at intended junction points (no "dangling" or overshooting endpoints) for correct network analysis.

```python
from shapely.validation import explain_validity

geom = wkt.loads("POLYGON((0 0, 4 4, 4 0, 0 4, 0 0))")  # self-intersecting (bowtie)
print(geom.is_valid)              # False
print(explain_validity(geom))     # describes the specific self-intersection
```

### Spatial Indexing for Vector Data

Because vector datasets can contain millions of features, efficient spatial querying (finding features within a bounding box, nearest-neighbor search, spatial joins) requires spatial indexing structures rather than brute-force comparison against every feature:

- **R-tree**: The most widely implemented spatial index structure, organizing geometries into a hierarchy of nested minimum bounding rectangles, enabling logarithmic-time spatial queries; used internally by PostGIS, `geopandas`/Shapely (via the `rtree`/`GEOS` STRtree), and most vector GIS software.
- **Quadtree**: Recursively subdivides space into four quadrants, useful for relatively uniformly distributed point data.
- **Grid indexing**: Simpler fixed-cell spatial indexing, effective for roughly uniform feature distributions but less adaptive than R-trees for highly clustered or variable-density data.

```python
import geopandas as gpd

gdf = gpd.read_file("parcels.shp")
sindex = gdf.sindex  # builds an R-tree spatial index (via GEOS STRtree)

# Efficient spatial query using the index
possible_matches_index = list(sindex.intersection((100, 100, 200, 200)))
```

### Vector Data Advantages and Limitations

**Advantages:**

- Precise geometric representation of discrete features (exact boundaries, not approximated by a grid).
- Compact storage for sparse or discrete phenomena (a single road doesn't require storing "no road" values across an entire grid, unlike raster).
- Naturally suited to network analysis, topology-aware operations, and attribute-rich feature querying.

**Limitations:**

- Poorly suited to continuous phenomena (elevation, temperature, precipitation) that vary smoothly across space without natural discrete boundaries — raster is generally preferred for such data.
- Computationally more expensive for certain overlay and surface analysis operations compared to raster's straightforward cell-by-cell algebra.
- Complex geometries (highly detailed polygons with many vertices) can become large and slow to process without appropriate simplification/generalization (as covered under Map Scale and Generalization).

### Related Topics

- Raster Data Model Fundamentals
- Map Scale and Generalization (Vector Simplification Algorithms)
- Spatial Databases and PostGIS Query Operations
- Topology Rules and Validation in GIS Data Quality Control
- Coordinate Reference Systems and Vector Data Reprojection
- Spatial Indexing Structures (R-tree, Quadtree) for Query Optimization
- Vector-Raster Data Model Integration and Conversion