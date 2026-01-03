# 1. Problem Brief

SpaGFT uses Fourier transforms to identify SVGs. At SBI2 the presenter said their method is "similar but better than Moran's I" - so we could potentially implement it as another flavor.
The implementation already used AnnData and looks to be low on dependencies. Add SpaGFT as a spatial autocorrelation method alongside Moran's I and Geary's C. SpaGFT should identify and rank spatially variable genes using graph Fourier transforms.

# 2. Agent Instructions

Implement SpaGFT as a modular flavor ("spagft") in `spatial_autocorr`, returning a DataFrame with a "GFT" column.
Genes with spatial patterns should have higher "GFT" scores.
Error handling of invalid shapes.

# 3. Test Assumptions

- The SpaGFT algorithm is implemented in `src/squidpy/gr/_spagft.py` as `_spagft(g: spmatrix, vals: NDArrayA) -> NDArrayA`.
- The spatial graph is expected in `adata.obsp["spatial_connectivities"]`.
- The flavor "spagft" should be recognized by the `SpatialAutocorr` enum.
- For invalid shapes, raise `ValueError` if the matrix dimensions do not align.
