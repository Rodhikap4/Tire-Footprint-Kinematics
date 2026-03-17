# IoT Sensor Data Analysis: Tire Footprint Kinematics

## Project Overview
This repository contains a Python-based signal processing pipeline designed to estimate the footprint angle of an agricultural tire moving at 10 km/h using raw inertial sensor data (accelerometer and gyroscope).

## Technical Pipeline
1. **Data Ingestion & Cleaning:** Handled raw data parsing issues, including correcting European CSV formatting (comma decimals) and fixing mis-indexed columns that distorted the data structure.
2. **Signal Filtering:** Implemented a 4th-order Butterworth Low-Pass Filter (50Hz cutoff) via `scipy.signal` to eliminate high-frequency road texture noise from the Radial Acceleration signal.
3. **Event Detection:** Built a dynamic thresholding algorithm (set to 50% of the baseline centrifugal force) to robustly detect the exact entry and exit points of the tire's contact patch.
4. **Kinematic Calculation:** Calculated the final footprint angle by integrating the Angular Velocity over the isolated contact duration.

## Repository Contents
* `TireDataAnalysis.ipynb`: The core Jupyter Notebook containing all data cleaning, filtering, and calculation logic.
* `TireDataAnalysis.html`: A static export of the notebook for quick viewing of the code and interactive matplotlib visualizations.
* `PreprocessedTireDataN.csv`: A 200-row sample of the preprocessed dataset used for the final calculations (truncated for confidentiality).

## Results
The algorithm successfully processed 397 individual tire rotations, filtering out micro-vibrations to calculate a physically accurate average footprint angle of **15.30°**.
