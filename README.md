

## Object Detection with R: Thresholding and Connected Components

This repository contains an R script ('Object_detection.ipynb') that performs a **basic form of object detection** on a set of images. The method uses classic computer vision techniques: **grayscale conversion, binary thresholding, and connected component labeling** to count distinct 'objects' within each image.

The notebook processes a folder of JPEG images and outputs the file name and the detected object count for each image to a CSV file.



### Prerequisites

This script is written in **R** and requires the following packages. You can install them using the commands found in the notebook's initial cells:

  * **imager**: Essential for image loading, processing, and connected component labeling.
  * **dplyr**: Used for data manipulation, particularly in constructing and managing the results dataframe.
  * **magrittr**: Provides the highly readable pipe operator (%>%) used for chaining image processing steps.

<!- end list ->

install.packages("dplyr")
install.packages("imager")
install.packages("magrittr")


### How to Run the Script

1.  **Prepare Your Environment**

      * Ensure you have R installed and can run a Jupyter or Colab notebook with an R kernel.
      * Install the required packages listed above.

2.  **Organize Your Data**

      * The script is configured to look for images in a specific path.
      * Create a folder containing your '.jpg' or '.jpeg' image files. The path used in the provided notebook is "**/content/sample_data/images**".
      * If your image folder is different, you **must update the path** in the notebook:

    <!- end list ->

      
    # Locate this line in the R code cell:
    img_folder <- "/content/sample_data/images" # Update to your dataset path
 

3.  **Execute the Notebook**

      * Open 'Object_detection.ipynb' in your R-enabled notebook environment.
      * Run the cells sequentially. The final code cell will:
          * Load the necessary libraries ('imager', 'magrittr', 'dplyr').
          * Iterate through all images in the specified folder.
          * Apply the object detection logic to each image.
          * Print the object count for each file.
          * Save the final results to a CSV file.



### Detection Method: Connected Components

The core of the detection is done by the 'detect_objects' function, which follows these steps:

1.  **Load and Grayscale**: The image is loaded and converted to **grayscale**.
2.  **Thresholding**: A binary threshold is applied ('img > 0.5'). Pixels brighter than $0.5$ become 'TRUE' (object), and others become 'FALSE' (background).
3.  **Labeling**: The 'label()' function from 'imager' finds **connected components**, essentially grouping adjacent 'TRUE' pixels into distinct shapes.
4.  **Counting**: The maximum label value ('max(labeled)') gives the total count of distinct connected components, which the script calls "objects."

**Note**: This method is a simple segmentation technique. The resulting "object count" is the number of distinct shapes that appear against the background after thresholding, and it is **highly sensitive to image quality and the chosen threshold value**.



### Output

The script saves all results to a file named **'traffic_object_detection_results.csv'**.

The output file will have two columns:

| image | object\_count |
| :--- | :--- |
| Pias--505-\_jpg.rf.22c56716d3ea83e6fdb0944793212a0e.jpg | 1239 |
| Pias--7-\_jpg.rf.ea09402c4e07c6e8f8054e402813ce38.jpg | 1080 |
| Pias--50-\_jpg.rf.82c7957c66dde00f9a7f6b4d666cfa3d.jpg | 447 |


