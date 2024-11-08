# NucleusJ3-Documentation
# Command-Line Doc with OMERO
This guide explains how to use the `NucleusJ3` functions with **OMERO** in **command line**.


## Prerequisites

- **Java** installed on your system.
- **NucleusJ JAR file** (`NucleusJ_2-2.0.0.jar`).
- **OMERO server access**: hostname, username, password, group ID.

## Available Functions with OMERO

The following actions are available to use with OMERO:

- **autocrop**: Automatically crops the widefield image based on specified criteria.
- **segmentation**: Performs segmentation on the dataset/image.
- **generateOverlay**: Generates an overlay from the image.
- **cropFromCoordinate**: Crops the image based on specific coordinates.
- **computeParameters**: Computes parameters related to the image.
- **segCC**: Executes segmentation for chromocenter components.
- **computeCcParameters**: Computes Chromocenter (Cc) parameters.

# Chromocenter Parameter Computation


## Example Command

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action computeCcParameters \
-input "Dataset/31510" -input2 "Dataset/31511" -input3 "Dataset/31512" \
-rhf intensity -obj nuc_cc -username my_username -hostname omero.igred.fr \
-group 553 -port 4064 -password my_password

```
## Parameters Description

- `-input`, `-input2`, `-input3`: Dataset IDs to be analyzed. (raw, nuc segmentation, chromocenter segmentation)
- `-rhf`: Relative Heterochromatin fraction, e.g., intensity, volume_intensity
- `-obj`: Object to analyse, e.g., cc (Chromocenter), nuc_cc (nucleus & chromocenters).
- `-username`, `-hostname`, `-group`, `-port`, `-password`: OMERO credentials and server details.

# Chromocenter segmentation


## Example Command

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action segCC \
-input "Dataset/31510" -input2 "Dataset/31511" -output Project_ID \
-username my_username -hostname omero.igred.fr \
-group 553 -port 4064 -password my_password

```
## Parameters Description

### Gaussian Blur Options
- `-isG`: Enables Gaussian blurring on the raw image.
- `-gX`: Sets the Gaussian blur sigma for the X-axis.
- `-gY`: Sets the Gaussian blur sigma for the Y-axis.
- `-gZ`: Sets the Gaussian blur sigma for the Z-axis.

### Size Filtering Options
- `-isF`: Enables size filtering for connected components.
- `-min`: Specifies the minimum size for connected components.
- `-max`: Specifies the maximum size for connected components.

### Other Options
- `-noC`: Disables any changes to the chromocenter parameters.
- `-f`: Sets a scaling factor for the segmentation.
- `-n`: Specifies the neighborhood size for the segmentation process.

## Directories
- **Input Directory**: Directory containing the input data.
- **Segmentation Directory**: Directory conataining the segmented data.


# Autocrop
To crop nuclei in a isolate file from 3D wide field image from microscopy. The process use a **OTSU** threshold to detect object on the image. To detect specific object you can use different parameters as filter like :
- volume of object detected 
- minimum intensity of object detected
- slice used to detect defined OTSU threshold
## Example Command for AutoCrop

To perform automatic cropping using the `NucleusJ` tool with OMERO, use the following command:

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action autocrop -input "dataset/31534" -output 14855 -threads 6 -thresh RenyiEntropy -username <your_username> -hostname omero.igred.fr -group 553 -port 4064 -password <your_password>
```

## Parameters Description
- `input` : The input dataset to be cropped e.g. "dataset/xxxx" .
- `output` : The ID of the output project where the results will be stored.
- `threads` : Number of threads to use for processing (in this case, 6).
- `thresh` : Thresholding method to use for processing (Otsu by default).

# Segmentation
## Example Command for Segmentation with NucleusJ

To perform segmentation using the `NucleusJ` tool with OMERO, use the following command:

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action segmentation -input "dataset/31510" -output 14855 -threads 6 -username <your_username> -hostname omero.igred.fr -group 553 -port 4064 -password <your_password>
```

## Parameters Description
- `input` : The input dataset/image to be segmented e.g. "dataset/xxxx" .
- `output` : The ID of the output project where the results will be stored.
- `threads` : Number of threads to use for processing (in this case, 6).


# Generate Overlay 

To perform Overlay using the `NucleusJ` tool with OMERO, use the following command:

## Command to Use:

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action generateOverlay \
-input "Dataset/31510" -input2 "Dataset/31511" -output Project_ID \
-username my_username -hostname omero.igred.fr \
-group 553 -port 4064 -password my_password
```
## Parameters Description
- `input` : Projection dataset ID (e.g., Dataset/31510)
- `input2`: DIC dataset ID (e.g., Dataset/31511)
- `output`:	Output project ID for the generated overlay

