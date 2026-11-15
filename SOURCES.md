# RealworldPlant: image sources and construction provenance

Last checked: 2026-11-15.

## Scope

RealworldPlant is a curated collection assembled from existing public images. The source tables describe the upstream image resources identified for its subsets. They do not claim new field acquisition by the maintainers, inclusion of every upstream image, or inheritance of the upstream train/test assignments.

The mappings are supported by original folder and filename inspection and sampled image-content comparisons. The intermediate history from the upstream releases to the locally reorganized folders is not fully recorded. File renaming, resizing, and background processing mean that byte equality with original downloads is not required for image-content correspondence.

## Crop-to-source mapping

| Released crop | Source ID | Original folder or partition | Mapping details |
|---|---|---|---|
| Bean | S5 | `train/` and `validation/` examples in iBean | Healthy, angular leaf spot, and bean rust; sample content matches establish the upstream image resource. |
| Cashew | S2 | `Crops/Cashew/` | Healthy, leaf miner, and red rust subsets. |
| Maize | S2 | `Crops/Corn/` | Maize healthy, maize leaf blight, and maize streak virus subsets. |
| Groundnut | S6 | `Groundnut_Leaf_dataset/train/` and `test/` | Healthy, early leaf spot, late leaf spot, nutrition deficiency, and rust. The released rust group contains examples matching both original `rust_1` and `early_rust_1`. |
| Potato | S2 | `Crops/Potato/` | Healthy, Fungi, and Nematode subsets; released abnormal paths retain the spelling `Patato`. |
| Pumpkin | P1 (candidate) | Original source files currently unavailable | The five class names match the candidate dataset. Image-content matching has not been completed; provenance remains pending. |

## How the source images were reorganized

1. Select crop and condition subsets from the source image collections and organize them by background appearance. Source dataset names alone do not determine the scene assignment.
2. Retain or normalize crop/condition names into the released directory structure. Inherited spellings are retained where required by the image manifests. Class-level mappings are listed in [class_sources.csv](class_sources.csv).
3. Treat healthy crop categories as ID classes. Treat the selected non-healthy conditions, including disease, insect damage, and nutrient-related abnormalities where present, as OOD categories. Sample matches show that `Groundnut_rust` includes examples from the source rust and early-rust groups in RealworldPlant.
4. Divide the curated healthy pool within each crop into approximately 80% training and 20% testing with seed 1. Assign the selected abnormal pool to OOD evaluation. These are the curated collection's splits; they should not be described as the original providers' official splits.
5. Publish image paths and labels through `train.json`, `test.json`, and `ood.json`. The current release stores healthy test images in `test/` and does not provide a separate validation set. Representative released images are 256 × 256 RGB; the complete history of preprocessing parameters is not available.

## Evidence and reproducibility

- [source_examples.csv](source_examples.csv) gives checked target/upstream image pairs using repository-relative target paths. It is a sample-based record, not a full-image lineage map.
- [class_sources.csv](class_sources.csv) associates released class groups with upstream source IDs. Counts describe the target collection, not a measured allocation between multiple source IDs.
- Original source partitions were reorganized. A target path such as `train/...` or `test/...` need not match its source archive partition.
- The image examples in README figures can be traced separately through [assets/sample_manifest.json](assets/sample_manifest.json).

## Source references

### S2. Multi-Crop Leaf Disease Dataset: Corn, Potato, Rice, Tomato, and Cashew

- Creators: Md Atef Ashab Sifat; Md Sazzad hosen.
- Year: 2025.
- Repository version cited: 1.
- Original resource: [Multi-Crop Leaf Disease Dataset: Corn, Potato, Rice, Tomato, and Cashew](https://data.mendeley.com/datasets/z6jp232g5j/1).
- DOI: [10.17632/z6jp232g5j.1](https://doi.org/10.17632/z6jp232g5j.1).
- Provider license reference: CC BY 4.0.

### S5. iBean

- Creators: Makerere AI Lab; National Crops Resources Research Institute (NaCRRI).
- Year: 2020.
- Original resource: [iBean](https://github.com/AI-Lab-Makerere/ibean/).
- Provider license reference: MIT (as stated by the original repository).

### S6. Dataset of groundnut plant leaf images for classification and detection

- Creators: Aishwarya Manvikar; Padmanabha Reddy.
- Year: 2023.
- Repository version cited: 3.
- Original resource: [Dataset of groundnut plant leaf images for classification and detection](https://data.mendeley.com/datasets/22p2vcbxfk/3).
- DOI: [10.17632/22p2vcbxfk.3](https://doi.org/10.17632/22p2vcbxfk.3).
- Provider license reference: CC BY 4.0.

### P1. Pumpkin Leaf Diseases Dataset From Bangladesh — candidate only

- Creators: Mohammad Rifat Ahmmad Rashid; Joy Biswas; Md Miskat Hossain.
- Year: 2024.
- Repository version cited: 2.
- Original resource: [Pumpkin Leaf Diseases Dataset From Bangladesh](https://data.mendeley.com/datasets/wtxcw8wpxb/2).
- DOI: [10.17632/wtxcw8wpxb.2](https://doi.org/10.17632/wtxcw8wpxb.2).
- Provider license reference: CC BY 4.0 for the candidate resource; applicability to the released subset remains unverified..

## Remaining provenance gap: pumpkin

The candidate Pumpkin Leaf Diseases Dataset From Bangladesh describes healthy leaves, bacterial leaf spot, downy mildew, mosaic disease, and powdery mildew, matching the five released condition names. However, matching category names and image counts do not authenticate image origin. Both Mendeley versions are currently listed as metadata-only, so an original archive could not be obtained for image-content comparison. P1 is therefore a candidate citation, not a verified source assignment. The pumpkin entries in `class_sources.csv` are explicitly marked `candidate_only`.

## Downloaded resources versus identified image sources

The preparation workspace also contained [PlantDoc](https://github.com/pratikkayal/PlantDoc-Dataset), [Saon110/bd-crop-vegetable-plant-disease-dataset](https://huggingface.co/datasets/Saon110/bd-crop-vegetable-plant-disease-dataset), and the YOLO-format [Multi-Crop Disease Dataset](https://data.mendeley.com/datasets/6243z8r6t6/1). Their presence in a download folder does not establish that they supplied the released samples. They are not counted as confirmed sources here. In particular, sample-based groundnut matches identify S6 as an upstream image resource; a direct lineage through the YOLO resource has not been established.

## Attribution and reuse

Please cite this curated collection and the relevant original image providers. The source license descriptions above are references to provider declarations, not a new blanket license for all files in this repository. Preserve original attribution and consult the source pages for reuse terms and any third-party content restrictions. Documentation of a candidate source does not resolve its image-level attribution.
