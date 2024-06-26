# [SOCR](http://socr.umich.edu/) 3D Cell Morphometry Project
## 2. 3D shape modeling and morphometry

Kalinin, A.A., Allyn-Feuer, A., Ade, A., Fon, G.V., Meixner, W., Dilworth, D., De Wet, J.R., Higgins, G.A., Zheng, G., Creekmore, A., Wiley, J.W., _et al_. 2018. 3D shape modeling for cell nuclear morphological analysis and classification. In _Scientific Reports_, 8(1), p. 13658. [doi:10.1038/s41598-018-31924-2](https://doi.org/10.1038/s41598-018-31924-2)

### Documentation for 3D surface modeling and morphometric features extraction

Inputs: individual c0 and c2 binary masks in TIFF format
(available for downloading on [project web-page](http://www.socr.umich.edu/projects/3d-cell-morphometry/data.html)).

#### Nuclei and nucleoli 3D shape modeling and morphometry (both DAPI, c0, and EtBr, c2):

This protocol uses parts of 
[LONI Global Shape Analysis (GSA) Workflow](https://pipeline.loni.usc.edu/explore/pipeline-workflows/):

1. [Convert binary masks](./1_Convert_to_NIfTY) into [NIfTY format](https://nifti.nimh.nih.gov/nifti-1)
2. [Model surface](./2_Morphometry) of each binary mask as a 2-manifold embedded in 3D space and represented as triangulated mesh
using Mask2Mesh [1], followed by mesh translation, simplification, subdivision, and extraction of 6 morphometric measures using LONI ShapeTools [2]
3. [Build nucleus feature vector](./3_Classification) by concatenating nuclear morphometric measures with nucleolar measure sample statistics grouped by nucleus (e.g., average, minimum, maximum, etc.) and perform model training and prediction using scikit-learn package [3]

Outputs: classification performance metrics (accuracy, precision, recall, AUC)

#### Required 3rd-party software:

[1] [MOCA](http://www.nitrc.org/projects/moca_2015/)

[2] [LONI ShapeTools](https://www.loni.usc.edu/research/software?name=ShapeTools)

[3] [scikit-learn](https://scikit-learn.org/)
