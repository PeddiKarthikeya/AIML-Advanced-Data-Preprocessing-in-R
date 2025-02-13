
# Overview
This repository contains an R script for performing data preprocessing operations, including handling missing values, imputing data, normalizing features, and finding the mode of categorical values.


# Handling Missing Data:
 *  Remove rows with missing values (na.omit).
 *  Replace missing values with the mean of the column.
# Min-Max Normalization:
  Scale numerical features between 0 and 1.
# Mode Calculation:
  Find the most frequent value in a categorical dataset.

# Rough Code Implementation
data <- data.frame(
  ID = 1:5,
  Age = c(25, NA, 30, NA, 45),
  Score = c(80, 90, NA, 70, 85)
)
cat("Original Data:\n")
print(data)
data_no_na <- na.omit(data)
cat("Data after removing rows with missing values:\n")
print(data_no_na)
data_imputed <- data
data_imputed$Age[is.na(data_imputed$Age)] <- mean(data_imputed$Age, na.rm = TRUE)
data_imputed$Score[is.na(data_imputed$Score)] <- mean(data_imputed$Score, na.rm = TRUE)
cat("Data after replacing missing values with the mean:\n")
print(data_imputed)
calculate_mode <- function(x) {
  uniqx <- unique(x)
  uniqx[which.max(tabulate(match(x, uniqx)))]
}
min_max_normalize <- function(x) {
  return((x - min(x, na.rm = TRUE)) / (max(x, na.rm = TRUE) - min(x, na.rm = TRUE)))
}
data_normalized <- data_imputed
data_normalized$Age <- min_max_normalize(data_imputed$Age)
data_normalized$Score <- min_max_normalize(data_imputed$Score)
cat("Data after Min-Max normalization:\n")
print(data_normalized)
temp <- c("A","B","A","A","C","E")
print(calculate_mode(temp))

# Usage
 Clone this repository
 Open and run the script in RStudio or any R environment.
 Modify the dataset as needed and apply the preprocessing steps.

# Applications:
 Preparing datasets for Machine Learning.
 Handling missing data in real-world applications.
 Scaling data to improve model performance.
 Finding categorical mode for data analysis.

# Feel free to submit issues or pull requests to improve this project.

License:
This project is licensed under the MIT License.

