# How to Use Geospatial Analysis for Outlier Detection in Election Data

## Introduction

The integrity of democratic processes is seriously threatened by electoral misconduct, which also erodes public trust in election results. Numerous claims of vote rigging and anomalies in the just finished election have focused on Nigeria's Independent National Electoral Commission (INEC). To guarantee the integrity and openness of the election results, these accusations demand a comprehensive inquiry.

## Methodology

### 1. Dataset Preparation

Getting the polling unit dataset, which did not contained the geographic coordinates (longitude and latitude) of each polling unit but the voting results for each party only, so the first stage in the process is to get all datasets without the geographic coordinates. In order to geolocate the missing locations, I used the Google Map API and OpenCage Map API in conjunction with the Python tool geopy.

### 2.	Data Cleaning and Validation:
  
 After preprocess the dataset, I cleaned it to remove duplicates and invalid entries. This step was crucial to ensure the accuracy of subsequent geodesic calculations

### 3. Neighbour Identification

I used geodesic distance calculations to find nearby voting units. The geodesic distance is the shortest path, accounting for Earth's curvature, between two points on its surface. Because of its accuracy in measuring distances over short ranges, such those between polling units, this method was selected.

#### 1. Definition of Radius: 
To identify which polling places are regarded as neighbors, I established a radius of one kilometer. Because of their close proximity and comparable demographics, neighboring units within this radius were assumed to have similar voting habits.
#### 2. Effective Method for Calculating Distance: 
I utilized time-saving, efficient algorithms to calculate distance. Rather than employing computationally costly methods to determine the distance between each pair of polling units, I adopted a more effective strategy by utilizing spatial indexing techniques. In particular, I constructed a KDTree for fast nearest-neighbor searches using the Scipy toolkit. As a result, fewer distance calculations were needed, greatly accelerating the procedure.

### 4. Outlier Score Calculation
Outlier scores were calculated for each party in each polling unit by comparing the votes received with those of its neighboring units. The steps involved are:
#### 1.	Vote Comparison: 
For each polling unit, the votes received by each party were compared with the average votes of neighboring units within the defined radius.
#### 2.	Deviation Calculation: 
The outlier score for each party was calculated as the absolute deviation of votes from the neighboring average. This deviation indicates how much a polling unit’s results differ from what would be expected based on its neighbors.

### Results and Findings

### Top 3 Outliers for Each Party
The top three polling units with the highest outlier scores for each party were identified and visualized on a map. The outliers were annotated with their polling unit names for clarity as shown below:

### Conclusion
This analysis highlights the importance of geospatial techniques in ensuring the integrity of election results. The identification of significant outliers and consistent outliers across parties (though some way more than others — indicating higher potential for rigging than the others) provides valuable insights for further investigation and potential corrective measures.


## Contacts
- LinkedIn: [@bLevi](https://www.linkedin.com/in/benson-levi-9867146b/)
- Email: leviben2023@gmail.com
- HNG Internship: [Internship](https://hng.tech/internship)
- HNG Tech: [Hire](https://hng.tech/hire)
