# Pokemon Classification Using Self-Organizing Maps

---

### Overview
This repository contains the implementation and analysis of a Self-Organizing Map (SOM) designed to classify Pokemon based on their battle attributes and characteristics. The main objective of this project is to understand how SOMs function and to analyze the relationships between different Pokemon types by observing how they group together. 

---

### Dataset Description
The dataset contains 796 individual Pokemon entries and tracks specific numerical attributes. 
The key characteristics used for training include:
* **Base Statistics:** Values for attack, defense, special attack (sp_attack), and special defense (sp_defense)
* **Effectiveness Multipliers:** Numerical indicators showing how a Pokemon performs against other specific types (e.g., against_bug, against_dragon, against_fire)

### Data Preparation
The dataset was carefully cleaned and transformed to ensure effective training. 
Key data preparation steps included:
* Missing secondary types were assigned a "Nan" placeholder to ensure all Pokemon had a value in that column.
* Non-contributing columns such as Name, pokedex_number, and generation were removed.
* Type columns (type1, type2) and against_normal were removed so the SOM could focus purely on relevant combat strengths and weaknesses.
* Outliers were kept in the dataset to avoid losing valuable training data.
* Min-Max Scaling was applied to normalize all features to a standard 0 to 1 range, preventing larger numerical values from dominating the clustering process.

---

### Experimentation & Configuration
The SOM was configured using specific distance calculations and neighborhood functions to optimize learning:
* **Best Matching Unit (BMU):** Calculated using Euclidean distance due to its effectiveness in high-dimensional spaces.
* **Neighborhood Function:** The Mexican Hat function was chosen because it excites nearby neurons while weakening farther ones, creating highly distinct, non-overlapping clusters.
* **Optimal Hyperparameters:** After testing various configurations, the best model utilized a map side of 35, 60,000 epochs, and an initial learning rate of 0.05.

---

### Evaluation & Results
The model's accuracy and structural efficiency were assessed using multiple methods:
* **Optimal Clusters:** By applying the Elbow method and the Kneed library, the ideal number of clusters was identified as 12.
* **Error Metrics:** The selected model achieved a Quantization Error of 0.2654 and a Topographic Error of 0.0879, indicating a well-structured representation.
* **Visual Maps:** The evaluation was supported by Classification Maps, 3D Activation Maps to show neuron activation frequency, and Distance Maps (U-Matrix) to identify cluster boundaries.
* **Testing:** The SOM successfully grouped conceptually similar Pokemon. For example, Pikachu was correctly clustered with its evolution, Raichu, alongside other Electric types, while structurally similar Legendary birds like Articuno and Moltres were grouped together.
