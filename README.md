# Red Wine Quality Regression Analysis

This project, developed as part of the **Data Science Hackathon** by the **Data Mavericks** team, performs regression analysis on the Red Wine Quality dataset to predict wine quality based on physicochemical attributes. The dataset, sourced from the UCI Machine Learning Repository, contains 1,599 records of red wines with 12 columns. Using a linear regression model built in **Azure Machine Learning Designer**, the project aims to enhance sensory analysis systems, guide winemakers in raw material selection, and inform strategic pricing by identifying key factors influencing wine quality.

## Table of Contents
- [Problem Statement](#problem-statement)
- [Installation](#installation)
- [Usage](#usage)
- [Data](#data)
- [Methodology](#methodology)
- [Findings and Implications](#findings-and-implications)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Problem Statement
The project addressed three key challenges for wine producers:
1. **Efficiency of Sensory Analysis Systems**: How effective are current systems in assessing wine quality, and can a machine learning model improve accuracy?
2. **Influence of Physicochemical Attributes**: How can producers quantify the impact of attributes like acidity and alcohol on wine quality?
3. **Strategic Pricing**: How can producers set appropriate prices for different wine quality classes based on their attributes?

The solution involves building a linear regression model to predict wine quality (a score from 0 to 10) and embedding it into sensory analysis systems to guide production and pricing decisions.

## Installation
To run this project, ensure you have Python 3.x and Jupyter installed. The notebook uses the following Python libraries:
- `numpy` (1.16.4) for numerical computations
- `pandas` (0.24.2) for data manipulation
- `matplotlib` (3.1.0) for plotting
- `seaborn` (0.9.0) for enhanced visualizations
- `scikit-learn` for regression modeling and evaluation

Install the dependencies using:

```bash
pip install jupyter numpy==1.16.4 pandas==0.24.2 matplotlib==3.1.0 seaborn==0.9.0 scikit-learn
```

**Note**: The notebook was developed with Python 3.7.3, and the model was built using **Azure Machine Learning Designer**. While newer library versions may work, using the specified versions ensures compatibility. For Azure ML, access is required (details at [Azure ML](https://ml.azure.com/)).

## Usage
1. **Clone the Repository**  
   ```bash
   git clone https://github.com/your-username/red-wine-quality-regression.git
   ```
2. **Navigate to the Directory**  
   ```bash
   cd red-wine-quality-regression
   ```
3. **Launch Jupyter Notebook**  
   ```bash
   jupyter notebook
   ```
4. **Open the Notebook**  
   In the Jupyter interface, open [Red Wine Quality Regression Notebook](WineQuality-Regression.ipynb).
5. **Run the Cells**  
   Execute the cells sequentially to:
   - Load and inspect the dataset.
   - Perform data cleaning and visualization.
   - Train a linear regression model (replicated locally from Azure ML Designer).
   - Evaluate predictions with metrics (MAE, MSE, RMSE).
   - Visualize actual vs. predicted quality scores.
6. **Optional: Replicate in Azure ML**  
   - Import the dataset into Azure Machine Learning Designer.
   - Follow the notebook’s methodology to recreate the linear regression pipeline.

**Note**: Download `winequality-red.csv` from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Wine+Quality) and place it in the project directory, or update the file path in the notebook.

## Data
The Red Wine Quality dataset contains 1,599 records with 12 columns:
- **Fixed Acidity**: Numeric, tartaric acid content (g/L).
- **Volatile Acidity**: Numeric, acetic acid content (g/L).
- **Citric Acid**: Numeric, citric acid content (g/L).
- **Residual Sugar**: Numeric, sugar content (g/L).
- **Chlorides**: Numeric, salt content (g/L).
- **Free Sulfur Dioxide**: Numeric, free SO₂ content (mg/L).
- **Total Sulfur Dioxide**: Numeric, total SO₂ content (mg/L).
- **Density**: Numeric, density (g/cm³).
- **pH**: Numeric, pH level.
- **Sulphates**: Numeric, sulphate content (g/L).
- **Alcohol**: Numeric, alcohol percentage (% vol).
- **Quality**: Integer, quality score (0–10, target variable).

Source: [UCI Wine Quality Dataset](https://archive.ics.uci.edu/ml/datasets/Wine+Quality).

## Methodology
The notebook and Azure ML Designer pipeline implement the following steps:
1. **Environment Setup**: Import libraries (`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`) and verify versions. Suppress warnings for cleaner output.
2. **Data Loading and Understanding**: Load `winequality-red.csv` into a pandas DataFrame. Inspect the 12 columns and 1,599 rows, with `quality` as the target.
3. **Data Cleaning and Transformation**: Check for missing values, outliers, and data types. Apply transformations (e.g., scaling) as needed for regression.
4. **Data Visualization and Analysis**:
   - Generate heatmaps to explore correlations between variables for high-quality (≥7) and low-quality (<7) wines.
   - Visualize physicochemical properties’ distributions for high vs. low-quality wines.
5. **Hypotheses Testing**:
   - H1: No significant difference in physicochemical attributes’ effects on high vs. low-quality wine.
   - H2: No significant difference between residual sugar and alcohol in high-quality wine.
   - H3: No significant difference between fixed acidity and citric acid in low-quality wine.
6. **Model Development**: Build a linear regression model in Azure ML Designer (replicated in the notebook with `scikit-learn`):
   - Split data into training and test sets.
   - Train the model on physicochemical features to predict `quality`.
7. **Model Evaluation**: Compute metrics:
   - **Coefficient of Determination (R²)**: 0.266 (explains 26.6% of variance).
   - **Mean Absolute Error (MAE)**: 0.109.
   - **Root Mean Squared Error (RMSE)**: 0.143.
   - **Relative Absolute Error**: 0.783.
   - **Relative Squared Error**: 0.734.
8. **Visualization**: Plot a bar chart comparing actual vs. predicted quality scores for 25 test samples.
9. **Deployment**: Propose embedding the model into a computerized sensory analysis system for real-time quality assessment.

## Findings and Implications
### Key Findings
- **Physicochemical Influences**:
  - **High-Quality Wines**: Higher **residual sugar** and **alcohol** content significantly improve quality.
  - **Low-Quality Wines**: Higher **fixed acidity** and **citric acid** are associated with lower quality.
- **Heatmap Insights**: Correlations differ between high and low-quality wines, rejecting the null hypothesis (H1) that physicochemical attributes have no differential impact.
- **Model Performance**: The linear regression model scored low MAE (0.109) and RMSE (0.143), indicating reasonable predictive accuracy, though the R² (0.266) suggests limited explanatory power, possibly due to non-linear relationships.

### Implications
- **Sensory Analysis**: Embedding the model into sensory analysis systems can automate and enhance quality assessments, improving efficiency.
- **Production Guidance**: Winemakers can prioritize raw materials with higher residual sugar and alcohol to produce high-quality wines, while minimizing fixed and citric acidity for better quality.
- **Pricing Strategy**: Quality predictions can inform pricing, aligning costs with wine quality classes to optimize market positioning.
- **Cultural Adaptation**: The model supports winemakers targeting diverse markets by tailoring physicochemical profiles to meet varying quality preferences.
- **Call to Action**: Winemakers should increase alcohol and residual sugar content to boost quality and sales, while integrating the model into testing workflows for data-driven decisions.

## Contributing
Contributions are welcome! To contribute:
- Fork the repository.
- Create a new branch for your feature or bug fix.
- Submit a pull request with a clear description of your changes.

Please open issues for bugs, suggestions, or improvements.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- **Dataset**: The Red Wine Quality dataset is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Wine+Quality).
- **Libraries**: Thanks to the developers of [numpy](https://numpy.org/), [pandas](https://pandas.pydata.org/), [matplotlib](https://matplotlib.org/), [seaborn](https://seaborn.pydata.org/), and [scikit-learn](https://scikit-learn.org/).
- **Platform**: Gratitude to [Azure Machine Learning](https://ml.azure.com/) for enabling model development.
- **Team**: The Data Mavericks team for their collaborative efforts in the hackathon.
