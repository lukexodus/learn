## Areal Surface Texture Parameters


### Overview

Areal surface texture parameters extend traditional 2D profile-based roughness analysis into three dimensions, characterizing a full surface region rather than a single line trace. Standardized under **ISO 25178** ("Geometrical product specifications (GPS) — Surface texture: Areal"), this framework replaced/supplemented the older profile-only approach (ISO 4287) as measurement technology (optical profilometers, confocal microscopy, focus-variation, atomic force microscopy) made dense 3D surface data practical to acquire. Areal parameters capture spatial and directional surface characteristics — such as lay anisotropy, pit/plateau structure, and functional volume — that a single 2D profile cannot fully represent.

### Why Areal Measurement Is Needed

- **Key Points**
  - A single 2D profile trace samples the surface along one line; if the surface has directional (anisotropic) texture, lay-dependent behavior, or spatially localized features (isolated pits, scratches, plateaus), a single trace may not be representative of the surface as a whole.
  - Areal measurement acquires a dense grid (or point cloud) of height data over a defined sampling area, from which both profile-equivalent parameters and genuinely 3D-specific parameters (volume, spatial/texture-direction parameters, feature-based parameters) can be calculated.
  - This is particularly important for surfaces where function depends on the interaction of the surface as a continuous 2D field rather than along a single direction — e.g., sealing surfaces, tribological (friction/wear) surfaces, cylinder bores with plateau-honed texture, and additively manufactured (3D-printed) surfaces with complex, non-directional texture.

### ISO 25178 Parameter Categories

#### 1. Height Parameters (Areal Equivalents of Ra, Rq, Rz, Rt)

| Parameter | Description | Profile equivalent |
| --- | --- | --- |
| $Sa$ | Arithmetic mean height of the surface (average of absolute height deviations from the mean plane over the sampling area) | $Ra$ |
| $Sq$ | Root-mean-square height of the surface | $Rq$ |
| $Sz$ | Maximum height of the surface (sum of maximum peak height and maximum valley depth over the entire sampling area) | $Rz$/$Rt$-like |
| $Ssk$ | Skewness of the height distribution | $Rsk$ |
| $Sku$ | Kurtosis of the height distribution | $Rku$ |

$$Sa = \frac{1}{A}\iint_A |z(x,y)|\,dx\,dy$$



$$Sq = \sqrt{\frac{1}{A}\iint_A z(x,y)^2\,dx\,dy}$$

where $A$ is the sampling area and $z(x,y)$ is the height at each point relative to the mean plane.

#### 2. Spatial Parameters

- **$Sal$ (auto-correlation length)**: the horizontal distance at which the surface's autocorrelation function decays to a specified value (commonly 0.2), representing the fastest-decaying spatial wavelength direction — a measure of the "texture wavelength" of the finest-repeating structure.
- **$Str$ (texture aspect ratio)**: the ratio of the fastest to slowest decay distances of the autocorrelation function; values near 1 indicate a uniform/isotropic texture in all directions, while values near 0 indicate a strongly directional (anisotropic) texture — this parameter directly and quantitatively captures what "lay" describes qualitatively in 2D profile metrology.

#### 3. Hybrid Parameters

- **$Sdq$ (root-mean-square gradient)**: quantifies the average slope steepness of the surface, relevant to optical scattering and contact mechanics.
- **$Sdr$ (developed interfacial area ratio)**: the percentage increase in surface area of the measured surface compared to a perfectly flat plane of the same projected area — relevant to coating adhesion, wetting behavior, and effective contact/reaction surface area.

$$Sdr = \left(\frac{\text{actual surface area} - \text{projected area}}{\text{projected area}}\right) \times 100\%$$

#### 4. Functional (Volume) Parameters — Areal Material Ratio Curve Family

- Derived from the **areal material ratio curve** (the 3D equivalent of the profile bearing ratio curve), these parameters describe the distribution of material and void volume at different height thresholds, directly relevant to functional performance such as lubricant retention and running-in wear behavior.

| Parameter | Description |
| --- | --- |
| $Vmp$ | Peak material volume (volume of material in the peak zone) |
| $Vmc$ | Core material volume |
| $Vvc$ | Core void volume (volume available for fluid/lubricant retention in the core zone) |
| $Vvv$ | Valley void volume (volume available in the deep valley zone, e.g., for lubricant reservoirs) |

- These parameters are especially significant for plateau-honed cylinder bore surfaces in internal combustion engines, where the core zone provides the running (bearing) surface while the valley zone (often from a secondary honing pass) provides oil retention volume — a texture design directly informed by areal functional parameters rather than 2D roughness alone. [Inference — the specific target values for these parameters are application- and design-specific, established through engine/tribology development testing rather than derivable from the standard alone.]

#### 5. Feature Parameters

- Derived through **segmentation** of the areal surface into discrete features (peaks, dales/valleys, using watershed segmentation algorithms defined in ISO 25178-2), enabling counting and characterizing of individual surface features (e.g., number of pits per unit area, average pit volume, peak density) — useful for characterizing textured/engineered surfaces (e.g., laser-textured or dimpled functional surfaces) where discrete feature geometry, not just statistical height distribution, governs function.

### Diagram: Areal Parameter Categories

```mermaid
flowchart TD
    A[Areal Surface Data - Height Map z(x,y)] --> B[Height Parameters: Sa, Sq, Sz, Ssk, Sku]
    A --> C[Spatial Parameters: Sal, Str - texture wavelength and anisotropy]
    A --> D[Hybrid Parameters: Sdq slope, Sdr surface area ratio]
    A --> E[Functional Volume Parameters: Vmp, Vmc, Vvc, Vvv]
    A --> F[Feature Parameters: segmented peak/dale counts and geometry]
```

### Relationship to 2D Profile Parameters (Ra, Rq, Rz)

- **Key Points**
  - $Sa$ and $Ra$ are conceptually analogous but are **not numerically interchangeable** — $Sa$ is computed over an area while $Ra$ is computed over a line, and the two will generally differ in value even for the same physical surface, particularly if the surface has anisotropic texture.
  - A surface can have a low $Sa$/$Ra$ (smooth on average) but a poor $Str$ (highly anisotropic) or elevated $Vvv$ (significant valley void volume) — properties that a 2D $Ra$/$Rz$ specification alone would not reveal.
  - For this reason, high-value or functionally critical surfaces (aerospace sealing surfaces, engine cylinder bores, medical implant surfaces, semiconductor wafers) increasingly specify areal parameters directly, while general commercial/industrial drawings continue to rely primarily on the simpler and more universally supported 2D profile parameters. [Inference — the pace and extent of industry-wide adoption of areal specification over profile specification varies by sector and is an ongoing transition rather than a completed universal shift.]

### Measurement Instrumentation for Areal Data

- **Contact methods**: scanning stylus profilometers (raster-scanning a stylus across a grid to build a height map) — slower than optical methods but robust and traceable to established stylus metrology practice.
- **Non-contact optical methods**:
  - **White-light (coherence scanning) interferometry**: high vertical resolution (sub-nanometer), good for smooth to moderately rough surfaces.
  - **Confocal microscopy**: effective for a wide range of surface reflectivity and roughness, commonly used for engineered/textured surfaces.
  - **Focus-variation microscopy**: effective across a broad roughness range including steep sidewalls, useful for complex additively manufactured or textured surfaces.
  - **Atomic force microscopy (AFM)**: extremely high lateral and vertical resolution for nanoscale surface characterization, though with a very small typical sampling area.
- Instrument selection depends on required lateral/vertical resolution, sampling area size, surface reflectivity/material, and measurement speed requirements. [Inference — the most appropriate instrument for a given surface depends on its specific reflectivity, slope characteristics, and the areal parameters of interest, and is typically determined by trial measurement or manufacturer application guidance rather than a single universal rule.]

### Data Processing Considerations

- **Key Points**
  - Areal data processing follows an analogous filtering hierarchy to 2D profiles: an S-filter (removes high-frequency noise), an L-filter (separates roughness from waviness/form, analogous to $\lambda_c$ in 2D), and F-operations (removes nominal form) — defined under ISO 25178-3 and related parts.
  - Outlier and non-measured point handling (spikes from optical measurement artifacts, dropout points from steep slopes or low reflectivity) requires careful data validation before parameter calculation, since areal datasets are large and more prone to localized artifacts than a single clean 2D trace. [Inference — the specific outlier-handling and interpolation approach appropriate for a dataset depends on the instrument and surface type and is typically governed by the measurement software's validated algorithms rather than manual ad hoc correction.]

### Summary Comparison Table

| Aspect | 2D Profile Parameters (ISO 4287) | Areal Parameters (ISO 25178) |
| --- | --- | --- |
| Data basis | Single line trace | Full 2D height map (grid/point cloud) |
| Directional/lay information | Qualitative (lay symbol only) | Quantitative ($Str$, $Sal$) |
| Volume/functional information | Not directly available | Directly available ($Vmp$, $Vmc$, $Vvc$, $Vvv$) |
| Feature counting | Not supported | Supported via segmentation |
| Typical instruments | Contact stylus (line scan) | Optical areal instruments, AFM, raster stylus |
| Industry adoption breadth | Very broad, long-established | Growing, concentrated in high-value/functional-critical sectors |

### Related Topics

- Roughness, waviness, and lay (2D texture concepts extended by areal analysis)
- Profile parameters $Ra$, $Rq$, $Rz$, $Rt$ (2D analogs to areal height parameters)
- White-light interferometry and confocal microscopy for non-contact surface measurement
- Areal material ratio curve and functional volume parameters for tribological design
- Surface segmentation and feature-based texture characterization (ISO 25178-2)
- Cylinder bore plateau honing and functional surface engineering
- Filtering standards for areal data (ISO 25178-3 S-filters, L-filters, F-operations)