# fuzzy_classification.R
fuzzy classification


## Usage

How to use / interpret

```r
res <- im.fuzzy(my_image, num_clusters = 4, m = 2, seed = 42)

dist_rast  <- res$distances     # 4 layers: distance to each class
mem_rast   <- res$memberships   # 4 layers: fuzzy membership 0–1
centroids  <- res$centers
```

mem_rast[[1]] = membership to class 1 (e.g. forest)

mem_rast[[2]] = membership to class 2 (e.g. agriculture)

etc.

For any valid pixel:

sum(values(mem_rast, cell = i)) ≈ 1

A higher membership for a class = pixel is spectrally closer (in the k-means sense) to that class.

If you tell me how you want to label classes (e.g. using training areas or manual labeling), we can also add a small helper that renames layers from class_1 → forest, class_2 → agriculture, etc.

