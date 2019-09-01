# Semantic Segmentation Example

# Important
```
Sorry I'm not able to view the full doc, so I wrote it here. Please note that when I used the instructions (underneath Ubuntu section) in the README file and hit `labelme` in the terminal, I have command not found, when I googled it, I found the `labelme` is in `pip list`, but it is not accessible from terminal, to resolve this issue, I used `export PATH=$PATH:~/.local/bin`, and It works like a charm. Thanks a lot!
```

## Annotation

```bash
labelme data_annotated --labels labels.txt --nodata
```

![](.readme/annotation.jpg)


## Convert to VOC-format Dataset

```bash
# It generates:
#   - data_dataset_voc/JPEGImages
#   - data_dataset_voc/SegmentationClass
#   - data_dataset_voc/SegmentationClassVisualization
./labelme2voc.py data_annotated data_dataset_voc --labels labels.txt
```

<img src="data_dataset_voc/JPEGImages/2011_000003.jpg" width="33%" /> <img src="data_dataset_voc/SegmentationClassPNG/2011_000003.png" width="33%" /> <img src="data_dataset_voc/SegmentationClassVisualization/2011_000003.jpg" width="33%" />

Fig 1. JPEG image (left), PNG label (center), JPEG label visualization (right)  


Note that the label file contains only very low label values (ex. `0, 4, 14`), and
`255` indicates the `__ignore__` label value (`-1` in the npy file).  
You can see the label PNG file by following.

```bash
labelme_draw_label_png data_dataset_voc/SegmentationClassPNG/2011_000003.png
```

<img src=".readme/draw_label_png.jpg" width="33%" />
