# NucleusJ3-Documentation
# Command-Line Doc for Chromocenter Parameter Computation

This guide explains how to use the `NucleusJ3` tool to compute **Chromocenter (Cc) parameters** between datasets stored in OMERO.

## Prerequisites

- **Java** installed on your system.
- **NucleusJ JAR file** (`NucleusJ_2-2.0.0.jar`).
- **OMERO server access**: hostname, username, password, group ID.

## Example Command

```bash
java -jar NucleusJ_2-2.0.0.jar -omero -action computeCcParameters \
-input "Dataset/31510" -input2 "Dataset/31511" -input3 "Dataset/31512" \
-rhf intensity -obj nuc_cc -username my_username -hostname omero.igred.fr \
-group 553 -port 4064 -password my_password

```
## Command Parameters

- `-input`, `-input2`, `-input3`: Dataset IDs to be analyzed. (raw, nuc segmentation, chromocenter segmentation)
- `-rhf`: Relative Heterochromatin fraction, e.g., intensity, volume_intensity
- `-obj`: Object to analyse, e.g., cc (Chromocenter), nuc_cc (nucleus & chromocenters).
- `-username`, `-hostname`, `-group`, `-port`, `-password`: OMERO credentials and server details.

# Command-Line Doc for Chromocenter segmentation


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

