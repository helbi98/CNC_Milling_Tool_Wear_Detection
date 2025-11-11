# Tool Wear Detection in CNC Machining

## Project Overview
This project focuses on detecting tool wear in a CNC machining process using supervised learning techniques.

## Dataset
The dataset consists of 18 experiments performed on a CNC machine, each capturing time-series sensor readings and operational parameters. Key aspects of the dataset include:

- **Time-series sensor readings**: Position, velocity, acceleration, current feedback, voltage, and power for different machine axes and spindle (X, Y, Z, S).
- **Operational parameters**: Feedrate, clamp pressure, and machining process type.
- **Tool condition**: Worn or unworn labels for each experiment.
- **Inspection results**: Machining finalized and passed visual inspection indicators.
- Sampling interval is 100ms, providing high-resolution temporal data.

## Project Steps

### 1. Data Preprocessing
- Filled missing values in `passed_visual_inspection` with `no` (indicating incomplete machining).
- Calculated **lag features** (`lag1` and `lag2`) for numeric columns to capture temporal dependencies.
- Computed **differential features** such as acceleration differences (`CommandAcceleration - ActualAcceleration`) to reflect deviations caused by tool wear.

### 2. Exploratory Data Analysis (EDA)
- Conducted **univariate analysis** on individual features to understand their distributions.
- Performed **multivariate analysis** using pairplots and correlation heatmaps.
- Visualized smoothed time-series signals (rolling mean) for each attribute across experiments.
- Conducted FFT analysis to extract high-frequency components indicative of irregular tool behavior.

### 3. Feature Engineering
- Created lagged features for capturing temporal trends in sensor readings.
- Computed differences between commanded and actual accelerations to capture performance deviations.
- Considered additional features based on domain knowledge.

### 4. Supervised Learning
- Labeled each experiment with its **tool condition** (worn vs. unworn).
- Split the dataset into training and validation sets.
- Trained **Random Forest classifier** for tool wear detection.
- Evaluated model performance and extracted **important features** contributing to prediction accuracy.

### 5. Visualization & Insights
- Generated bar plots to visualize the number of experiments passing visual inspection per tool condition.
- Explored relationships between operational parameters (feedrate, clamp pressure) and tool condition using pairplots.
- Analyzed correlations to remove redundant features across experiments.

## Results
- Successfully trained a supervised learning model to detect tool wear.
- Identified key features that indicate tool degradation.
- Visualizations and EDA confirmed patterns of wear across experiments.

## Tools & Libraries
- Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn
- Jupyter Notebook for analysis and experimentation

## Conclusion
This project demonstrates a robust workflow for **tool wear detection using supervised learning** with a combination of time-series feature engineering, differential analysis, and machine learning. The approach can help in predictive maintenance and quality assurance in CNC machining processes.
