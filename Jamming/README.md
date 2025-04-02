# 5G Communication Indicators Dataset (Jamming Dataset)

This dataset includes the 5G communication monitoring indicators recorded throughout the project. The data was collected by our project partner HMF, including **DLLA** and **UE Link** data, and then processed and merged for further analysis.

## Available Data:

1. **`label_encoder.pkl`**:  
   - The serialized encoder for the labels. This file is used to convert categorical labels into numerical values.

2. **`merged_data.csv`**:  
   - The raw merged dataset, combining both **DLLA** and **UE Link** data. This is the initial dataset obtained after merging.

3. **`merged_data_preprocessed.csv`**:  
   - The preprocessed dataset, excluding data scaling. This version of the data has been cleaned and prepared, but the values have not been normalized or scaled.

4. **`merged_data_preprocessed_only_one_label.csv`**:  
   - A version of the dataset that contains only the label `Jammer_On`. Other attributes such as bandwidth, frequency, and signal strength are also included. This file is created for specific analyses where only this label is relevant.

5. **`merged_data_preprocessed_only_one_label_extended.csv`**:  
   - This version includes repeated records of normal traffic to simulate additional training data, thus extending the set of training examples for improved analysis.

## Further Notes:

- All files have been carefully prepared to ensure easy handling and analysis of the 5G communication data.
- The dataset can be utilized for various tasks within 5G communication monitoring and analysis, such as detecting disturbances (e.g., jamming) or modeling network behavior.

## Licensing

This dataset is licensed under the Creative commons Attribution International 
Version 4.0 [(CC BY 4.0)](https://github.com/daisy-field/datasets/blob/main/LICENSE.txt)