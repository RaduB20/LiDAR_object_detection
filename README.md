# 3D Point Cloud Vehicle Detection and Tracking

This project demonstrates a complete pipeline for detecting and tracking vehicles from 3D point cloud data (LiDAR scans) obtained on a highway. The analysis is broken into two parts: first, identifying vehicles in a single static frame, and second, tracking those vehicles across a sequence of 300+ frames.

**Key Technologies & Concepts Demonstrated**

- Python: Jupyter Notebook, Pandas, Scikit-learn, NumPy, Plotly

- Data Preprocessing & Filtering: Voxel Grid Downsampling, ICP (Iterative Closest Point)

- Machine Learning (Clustering): DBSCAN (Density-Based Spatial Clustering of Applications with Noise), K-means

- Object Tracking: Centroid Tracking, 4D Data Handling (3D space + time)


## Project Breakdown

This repository contains the notebooks, final results, and visualizations for the project.

1. `static_frames.ipynb`: **Vehicle Detection in a Single 3D Frame**

This notebook details the complete process for identifying vehicles from a single 3D point cloud snapshot.

The processing pipeline includes:

  - Data Downsampling: Applied Voxel Grid Downsampling to significantly reduce the number of points, decreasing computation time while preserving the data's core structure.

  - Preprocessing (Ground Removal): Implemented the Iterative Closest Point (ICP) algorithm to align and remove static, unnecessary data, such as the highway surface and environment.

  - Object Clustering: Utilized the DBSCAN algorithm to cluster the remaining points. This density-based approach effectively isolates distinct objects (vehicles) from noise.


2. `tracking.ipynb`: **Vehicle Tracking Across a 4D Sequence**

This notebook addresses the more complex 4D problem: tracking vehicles across a video sequence of over 300 frames.

This required expanding the initial pipeline to handle the time dimension:

- **Problem**: Standard clustering on each frame is insufficient, as the cluster labels (e.g., 'cluster 1') are not consistent from one frame to the next.

- **Solution**: Implemented a cluster correlation method. By calculating the centroids of clusters identified by DBSCAN in each frame, we can track these centroids over time. This allows for consistent object tracking and trajectory analysis throughout the entire sequence.

## Results & Visualizations

The .png and .pdf files serve as a visual summary of the project's results, which can be found in the **Finals** folder. They showcase:

- Visualizations of the 3D point cloud before and after preprocessing.

- Plotted DBSCAN cluster results, with bounding boxes and vehicles color-coded.

- Tracking of the vehicles across frames

## Data

The data is represented in .csv files, which correspond to the point cloud obtained with the help of LiDAR.
For the static frames, the data can be found in the **data** folder, whereas for the video, the data can be found in the **pointcloud** folder
