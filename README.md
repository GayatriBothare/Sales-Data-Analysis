# Sales Data Analysis Project

## Table of Contents

1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Tools](#tools)
4. [Data Cleaning/Preparation](#data-cleaningpreparation)
5. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
6. [Data Analysis](#data-analysis)
7. [Results/Findings](#resultsfindings)
8. [Recommendations](#recommendations)

## Project Overview

This data analysis project investigates sales data for a company selling various products across different countries and customer segments. The data includes details on sales figures, product information, customer demographics, and transaction dates. The project aims to identify trends, patterns, and valuable insights to support informed business decisions.

## Data Sources

* **Primary Dataset:** `DataSource.csv` - This file contains detailed information about each sale made by the company.

## Tools

* Microsoft Power BI Desktop
* Microsoft Excel (for initial data preparation)

## Data Cleaning/Preparation

The initial data preparation phase involved the following tasks:

* **Data Loading and Inspection:**
The data was loaded into the chosen environment for exploration and analysis.

* **Data Cleaning and Formatting:**
Data cleaning techniques were applied to address inconsistencies and errors. Additionally, data formatting was adjusted to ensure compatibility with Power BI.

* **DAX for Calculated Columns:**
DAX formulas were created to generate new calculated columns that enhance data analysis. Here are some examples:

  - Previous Month Name with Year:

    ```dax
    Previous_Month_Name_With_Year = 
    VAR SelectedMonth = MAX(Sheet1[Date])
    VAR PreviousMonth1 = EOMONTH(SelectedMonth, -1)
    RETURN FORMAT(PreviousMonth1, "MMMM YYYY")
    ```

  - Previous Month Profit (similar logic applies to Sales):

    ```dax
    Previous_Month_Profit = 
    VAR CurrentYear = YEAR(MAX(Sheet1[Date]))
    VAR CurrentMonth = MONTH(MAX(Sheet1[Date]))
    VAR PreviousMonthKey = IF(CurrentMonth = 1, (CurrentYear - 1) * 100 + 12, CurrentYear * 100 + CurrentMonth - 1)
    
    VAR previous_month_selection = CALCULATE(
        SUM(Sheet1[Profit]),
        FILTER(
            ALL(Sheet1),
            Sheet1[MonthKey1] = PreviousMonthKey
        )
    )
    
    VAR current_month_selection = SUM(Sheet1[Profit])
    
    RETURN
    IF(ISBLANK(previous_month_selection), current_month_selection, previous_month_selection)
    ```

  - Selected Month Name:

    ```dax
    Selected_Month_Name = FORMAT(MAX(Sheet1[Date]), "MMMM YYYY")
    ```

## Exploratory Data Analysis (EDA)

An exploratory data analysis (EDA) was conducted to gain a deeper understanding of the data and answer key questions such as:

* What is the overall sales trend?
* Which products are the top sellers?
* When are the peak sales periods?

## Data Analysis

Data analysis was performed to address specific business questions. This have involved techniques such as:

* **Sales Analysis:** This analysis examines sales trends over time, by product, by customer segment, or by country.
* **Profit Analysis:** This analysis investigates profit margins for different products, customers, or segments.
* **Customer Analysis:** This analysis explores customer buying behavior to identify profitable customer segments or target markets.

## Results/Findings

The specific results and findings will depend on the business questions you were trying to answer. Here are some possible examples based on your analysis:

* Sales are higher in December compared to November.
* Paseo and VTT are the top two products in terms of sales in Canada.
* Enterprise and Government segments generate the highest sales.
* Paseo has the highest total sales but also the highest total discounts offered, potentially indicating low-profit margins.
* Carretera has high sales and profit for the Enterprise segment.

## Recommendations

Based on the results of data analysis, we want to make recommendations such as:

* Focus marketing efforts on products with high profit margins.
* Offer discounts strategically to avoid reducing profitability.
* Target sales efforts to specific customer segments or countries.

## Power BI Pages

The project includes the following Power BI pages to summarize the analysis and findings:

1. **Sales Analysis:** An overview of sales trends, highlighting peak sales periods and top-selling products.
2. **Profit Analysis:** A detailed look at profit margins across different products and customer segments.
3. **Country-Wise Report:** Insights into sales performance across various countries, identifying key markets.
4. **Segment-Wise Report:** Analysis of customer segments to identify the most profitable and significant customer groups.
