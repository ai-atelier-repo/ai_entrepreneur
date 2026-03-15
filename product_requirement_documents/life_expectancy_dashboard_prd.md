# Product Requirements Document: Life Expectancy Dashboard

## 1. Overview
The Life Expectancy Dashboard is a Streamlit-based web application designed to visualize life expectancy trends over time across various countries. The project leverages `uv` as its package manager and virtual environment handler, ensuring a high-performance, reproducible, and isolated development environment.

## 2. Goals & Objectives
- Provide an interactive, responsive web dashboard for analyzing life expectancy data using Streamlit.
- Establish an efficient dependency and project management workflow utilizing `uv`.
- Showcase historical trends through dynamic, interactive line charts using Altair.
- Provide summarized metric views (e.g., Median Life Expectancy) tailored to user-filtered data.

## 3. Technology Stack
- **Web Dashboard Framework**: Streamlit
- **Data Processing & Manipulation**: pandas
- **Data Visualization**: Altair
- **Package & Environment Manager**: uv (Astral)

## 4. Environment Setup Workflow (using `uv`)
To create a high-speed development environment, a concise `uv` workflow should be followed. This can optionally be codified into a reusable script or an agent workflow.

### Setup Steps:
1. **Initialize the Project**:
   ```bash
   uv init
   ```
   *Creates the `pyproject.toml`, `.python-version`, and base project structure.*

2. **Add Dependencies**:
   ```bash
   uv add streamlit pandas altair
   ```
   *Automatically creates a `.venv` virtual environment, resolves, and installs Streamlit, pandas, and Altair lightning-fast.*

3. **Run the Application**:
   ```bash
   uv run streamlit run app.py
   ```
   *Transparently executes the Streamlit server within the managed `.venv`, completely bypassing the need for manual environment activation (`source .venv/bin/activate`).*

## 5. Data Preparation Requirements
The raw dataset (`life-expectancy.csv`) must be standardized prior to usage in the application frontend:
1. **Column Standardization**: Rename the primary identifying column from `"Entity"` to `"Country"`.
2. **Temporal Filtering**: Filter the dataset to only include records where `"Year" >= 1960`.
3. **Derived Artifact**: Save the cleaned and filtered dataset as a new file named `life_exp.csv`.

## 6. Dashboard Functional Requirements

### 6.1. Application Interface
- **Layout**: Configure the Streamlit page layout to `layout="wide"`.
- **Title and Aesthetics**: Include a prominent title ("Life Expectancy Over Time") and set the tab icon appropriately (e.g., "🌍").
- **Sidebar Filters**: Provide a dedicated sidebar labeled "Filters".
- **Country Selection**: Implement a multi-select dropdown widget populated with all unique countries present in the dataset.
- **Default State**: Pre-populate the multi-select with notable default values (e.g., United States, China, India, Nigeria, Brazil) to ensure immediate visual feedback upon loading.

### 6.2. Visualizations (Altair)
- **Time Series Line Chart**: Render an interactive line chart displaying `"Year"` on the X-axis and `"Life Expectancy (Years)"` on the Y-axis.
- **Categorical Styling**: Differentiate the selected countries by uniquely coloring each plotted line.
- **Interactivity and Tooltips**: Include interactive features such as zooming/panning and hover-over tooltips displaying exact values for 'Country', 'Year', and 'Life expectancy'.
- **Scale Optimization**: Ensure the Y-axis does not automatically lock to "0" (`zero=False`) to better emphasize data variances.

### 6.3. Tabular Data View
- **Aggregated View**: Provide a data table prominently positioned below the line chart.
- **Metric Definitions**: Rather than displaying raw time-series data, calculate and display the **Median Life Expectancy** grouped by each respective selected Country.
- **Dynamic Updates**: Ensure the data view instantly updates its aggregated metrics based entirely on the sidebar's current selections.
