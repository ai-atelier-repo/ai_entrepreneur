# Prompts for creating Streamlit Application

## Create workflow for uv

This will be a streamlit project. I would like to use uv for package management and virtual environment. Can you create workflow so that uv is used for the project. Here is the web site for the documentation: https://docs.astral.sh/uv/


## Fetch Dataset

Fetch the life expectancy dataset we will be using for the project and store it in the data directory /data. https://github.com/ai-atelier-repo/ai_entrepreneur/blob/main/datasets/life-expectancy.csv

## Prepare Dataset

Next, I will be using life_expectancy.csv for data analysis and visualization. I would like to prepare the data set. Create a new dataset life_exp.csv. Derive it from life_expectancy.csv: 1) change column name "Entity" to "Country"; 2) filter the dataset so that Year>=1960.

## Create a streamlit app

Create a streamlit app which plots life expectancy. Use altair or plotly for data visualization. Y-axis is life expectancy and x-axis is year. Create a sidebar where I can select country or countries. Below the plot provide a data grid with summary statistics on the selected countries.
