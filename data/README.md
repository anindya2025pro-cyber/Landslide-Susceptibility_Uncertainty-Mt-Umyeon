
3. **Content:**
```markdown
# Data Directory

## Landslide_Inventory_Processed.csv

The processed dataset containing all samples and conditioning factors.

### Dataset Statistics
- **Total Records:** 302
- **Landslides (LS=1):** 151
- **Non-landslides (LS=0):** 151
- **Class Balance:** 50% / 50% (perfectly balanced)

### File Structure

| Column | Type | Description |
|--------|------|-------------|
| LS | Integer (0/1) | Target variable: 0=stable, 1=landslide |
| Elevation | Float | Height above sea level (m) |
| Slope | Float | Gradient (degrees) |
| Aspect | Float | Direction of slope (0-360°) |
| Plan_Curvature | Float | Lateral convergence/divergence |
| Profile_Curvature | Float | Along-slope acceleration |
| TRI | Float | Terrain Roughness Index |
| TPI | Float | Topographic Position Index |
| SPI_Log | Float | Stream Power Index (log) |
| TWI | Float | Topographic Wetness Index |
| Drainage_Density | Float | Length of drainage per area |
| Distance_River | Float | Distance to nearest river (m) |
| NDVI | Float | Vegetation greenness index |
| Canopy_Height | Float | Tree height (m) |
| Forest_Density | Float | Forest coverage (%) |
| LULC | Integer | Land use class code |
| Rainfall | Float | Annual rainfall (mm) |
| RD99P | Float | 99th percentile rainfall (mm) |
| F1_ShearRainIndex | Float | Engineered: Slope × log(Rainfall) |
| F2_HydroSlopeIndex | Float | Engineered: Slope × TWI |
| F3_RuggedWetIndex | Float | Engineered: TRI × TWI |
| F4_ReliefNorm | Float | Engineered: TRI / Elevation |
| F5_InfraRisk | Float | Engineered: Road-River proximity |
| POINT_X | Float | Easting coordinate |
| POINT_Y | Float | Northing coordinate |

### Data Source & Processing

**Sources:**
- DEM: ALOS AW3D30 (30m)
- Land Cover: ESA WorldCover 2021
- Vegetation: Sentinel-2 NDVI
- Rainfall: Climate Hazards Group (CHIRPS)
- Landslide Inventory: Field surveys + historical records

**Processing:**
All layers reprojected to EPSG:5186 (Korean CRS) at 30m resolution via Google Earth Engine.

### Usage

Load in Python:
```python
import pandas as pd
df = pd.read_csv('Landslide_Inventory_Processed.csv')
print(df.head())
print(df.describe())
