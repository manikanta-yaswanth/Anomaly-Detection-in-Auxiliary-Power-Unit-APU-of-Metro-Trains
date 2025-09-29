# Anomaly-Detection-in-Auxiliary-Power-Unit-APU-of-Metro-Trains
# Anomaly Detection in Auxiliary Power Unit (APU) of Metro Trains

![Anomaly Detection Results](anomaly-detection-in-auxiliary-power-unit--apu--of.jpg)

## Project Overview
This project focuses on detecting anomalies in the **Auxiliary Power Unit (APU)** of metro trains using sensor data. The goal is to enable **predictive maintenance**, enhance system reliability, and minimize downtime by identifying potential failures early.

---

## Dataset
- **Source**: [MetroPT Dataset](https://archive.ics.uci.edu/dataset/791/metropt+3+dataset)
- **Time Span**: February to August 2020
- **Frequency**: 1Hz
- **Volume**: 1,516,948 rows and 17 columns

### Sensor Categories
- **Analog Sensors**: Pressure, temperature, and motor current readings.
- **Digital Sensors**: Electrical signals for air intake valves, pressure switches, and air dryers.

---

## Project Goals

### 1. Prediction Goals
- **Anomaly Detection**: Identify abnormal readings in pressure, temperature, and motor current.
- **Failure Risk Prediction**: Flag high-risk operational periods before failures occur.

### 2. Inference Goals
- **Key Sensor Patterns**: Analyze correlations between sensors (e.g., motor current, TP2, H1).
- **State Classification**: Identify normal vs. high-load conditions.
- **Temporal Analysis**: Detect periods of increased anomaly frequency (e.g., early morning spikes).

### 3. Broader Goals
- **Proactive Maintenance**: Shift from reactive to real-time predictive maintenance.
- **System Reliability**: Enhance safety and minimize downtime for metro operations.

---

## Methods Used

### 1. Data Preprocessing
- **Schema Definition**: Structured mapping for efficient Spark processing.
- **Data Cleaning**: Minimal inconsistencies found.
- **EDA**: Visualizations using correlation heatmaps and temporal analysis.

### 2. Anomaly Detection Techniques
- **K-Means Clustering**: Unsupervised learning for detecting patterns in unlabeled data.
  - **Cluster 0**: Normal operations (~95%)
  - **Cluster 1**: Anomalies (~5%) with high oil temperatures (>70°C) and motor currents (>9A).
- **LSTM Autoencoder**: Deep learning model for time-series anomaly detection.
  - **Anomaly Threshold**: 95th percentile of reconstruction error.

---

## Key Results

- **Clustering**: Successfully identified two clusters (normal and anomalous conditions).
- **LSTM Autoencoder**: Detected anomalies aligning with clustering results and actual failure events.
- **Temporal Insights**: Anomalies peaked during early morning (2 AM - 5 AM) with stable periods between 7 AM - 9 AM.

### Alignment with Failures
- **May 29-30, 2020**: Model flagged high-risk periods corresponding to recorded air leak stress.
- **June 5-7, 2020**: Predicted anomalies matched reported failures.

---

## Challenges

- **Model Integration**: Isolation Forest and One-Class SVM were challenging to implement with PySpark.
- **Threshold Determination**: Relied on statistical assumptions (95th percentile).
- **Evaluation Metrics**: Traditional metrics like precision and recall were unavailable due to unlabeled data.

---

## Tools & Technologies

- **Apache Spark**: For large-scale data processing. 
- **Python**: Core programming language.
- **Machine Learning**: K-Means Clustering, Isolation Forest, One-Class SVM.
- **Deep Learning**: LSTM Autoencoder.

---

## References
1. **Davari, Narjes, et al.** "Predictive Maintenance Based on Anomaly Detection Using Deep Learning for Air Production Unit in the Railway Industry." *2021 IEEE 8th International Conference on Data Science and Advanced Analytics (DSAA)*, IEEE, 2021, pp. 1-10. DOI: [10.1109/DSAA53316.2021.9564181](https://doi.org/10.1109/DSAA53316.2021.9564181).

2. **Veloso, Bruno, et al.** "The MetroPT Dataset for Predictive Maintenance." *Scientific Data*, vol. 9, no. 1, 2022, p. 764. DOI: [10.1038/s41597-022-01877-3](https://doi.org/10.1038/s41597-022-01877-3).

3. **Barros, Mário, et al.** "Failure Detection of an Air Production Unit in the Operational Context." *IoT Streams for Data-Driven Predictive Maintenance and IoT, Edge, and Mobile for Embedded Machine Learning*, Springer, 2020, pp. 61-74. DOI: [10.1007/978-3-030-66770-2_5](https://doi.org/10.1007/978-3-030-66770-2_5).

4. **Apache Spark.** "Spark SQL, DataFrames, and Datasets Guide." *Apache Spark*, 2024. [Spark SQL Guide](https://spark.apache.org/docs/latest/sql-programming-guide.html)

---

## License

This project is licensed under the MIT License.

---

**Made with 💙 by [Mani Kanta Yaswanth Jalagadugu]
