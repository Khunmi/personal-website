# Power BI & Tableau

## Introduction

This section showcases data analytics and visualization projects using Power BI and Tableau, highlighting key insights and findings from various projects.

### Key Projects:

1. **ATB Financial's US Branch Performance Analysis** - Transitioning client activity to digital channels.
2. **EOY Retail Sales Performance(Downstream Oil & Gas) via Power BI.**
3. **Monitoring and Evaluation Dashboard Tracker via Tableau.**

Let's get started .........

![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)

## ATB Financial US Branch Performance Analysis

<iframe width="1010" height="850" src="https://public.tableau.com/views/ATB-StrategyMock/Overview?:language=en-GB&:display_count=n&:origin=viz_share_link:showVizHome=no&:embed=true" frameborder="0" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


### Objectives and Primary Goal:
Analyze ATB branch performance to identify opportunities for transitioning client activity from physical branches to digital channels.

**Specific Objectives:**
- Identify underperforming branches or states.
- Highlight high-performing branches to replicate success.

### Dataset Overview:
The dataset includes deposit information for ATB Financial branches from 2010 to 2016, including:
- **Branch Types:** Walk-In, Drive-Thru
- **Deposit Amounts:** Total dollar amounts at each branch.
- **Geographic Locations:** State, county, city, and branch details.
- **Year:** Spanning 2010 to 2016.
  
<div style="display: flex; align-items: center; justify-content: flex-start;">
<img src="https://khunmi.github.io/portfolio/images/story_telling_deposits%20summary.png" alt="Visual Summary" style="max-width: 500px; margin-right: 40px;">

<div style="max-width: 800x;">

### Initial Insights:

- Total Deposits: exactly **12.65 billion(USD)** has been deposited between 2010 and 2016. A further breakdown shows that, of the **12.65 billion(USD)** deposited, **26.43 million(USD)** was via drive-thrus while **12.63 billion(USD)** was through walk-in branches
- Total Branches: there are a total of **5,413** branches of ATB as of July 16, 2016 when this dataset was generated. **100** of these branches are drive-thrus while **5,313**are walk-in branches
- Average Deposits per Branch: Based on these numbers, initial assumption informs that each drive-thru branch received deposits of an average of **264,322.37(USD)** between 2010 and 2016 and each physical branch received deposits of an average of **2,376,553.74(USD)** between 2010 and 2016

</div>

</div>

### Key Findings - Deposit Trends:


<div style="display: flex; align-items: center; justify-content: flex-start;">
<img src="https://khunmi.github.io/portfolio/images/story_telling_deposit%20chart.png" alt="Visual Summary" style="max-width: 500px; margin-right: 40px;">

<div style="max-width: 800x;">
<div style="display: flex; align-items: center; justify-content: flex-start;">
<img src="https://khunmi.github.io/portfolio/images/story_telling_deposit%20chart2.png" alt="Visual Summary" style="max-width: 500px; margin-right: 40px;">

</div>
</div>
</div>

<div style="display: flex; align-items: center; justify-content: flex-start;">

- Walk-in branches have higher deposits(in billions)
- Drive-thru ABMs show consistent growth potential similar to walk-in branches
- At this level of granularity, the observed difference can easily be attributed to the number of branches in each category as well as their popularity and general technology adoption
<div style="max-width: 800x;">
<div style="display: flex; align-items: center; justify-content: flex-start;">

- Additional level of details shows acquired branches contributes over 90% of deposits recorded at drive-thru ABMs. This is in contrast to what is observed in walk-in branches where organic ownerships are largely responsible for deposits
- Could this be a function of a great acquisition team, number of branches for each ownership type, geography or an hybrid of some or all of these factors?
</div>
</div>
</div>

### Key Findings - Geographic Distribution:

<div style="display: flex; align-items: center; justify-content: flex-start;">
<img src="https://khunmi.github.io/portfolio/images/story_telling_deposit%20heatmap.png" alt="Visual Summary" style="max-width: 500px; margin-right: 40px;">

<div style="max-width: 800x;">

- Deposits heatmap reveal Ohio and New York as the largest deposit contributors for the entire US market. However, it is interesting to highlight that the State of Pennsylvania, despite being sandwiched between the two highest contributing States, actually recorded $0 in deposits.

</div>
</div>

### Recommendations:
1. **Target High-Performing Regions:** Focus on states with high deposits and favorable GDP per capita.
2. **Divest Low-Performing Regions:** Close branches with consistently low deposits.
3. **Enhance Digital Channels:** Incentivize web and drive-thru services to foster adoption.
4. **Customer Support:** Provide localized support for non-tech-savvy customers.

![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)

## EOY Retail Sales Performance(Downstream Oil & Gas)

<iframe width="965" height="600" src="https://app.powerbi.com/view?r=eyJrIjoiYzMzMDNjNmUtZjIwYi00ODNiLTgyMTctOTg0NDI5NDBjZDQ0IiwidCI6ImJkMDJkNzlkLWZjMjktNGExMi05ZGYxLWE0YmZlNmQ4ZjRjOCJ9&pageName=ReportSectiond9306b8184b0330bd596" frameborder="0" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Introduction:

In today's fast-paced business world, retail sales performance is a key indicator of a company's success. The Downstream Oil and Gas sector is no exception, with a constantly changing landscape and a highly competitive market. As such, understanding the performance of key products like PMS, AGO, and lubricants is crucial for decision-makers in the industry. In this report, I present the findings of my analysis of retail sales performance data sourced from Sage Business Cloud ERP for the year 2022. my analysis provides insights into the performance of retail stations, PMS, AGO, and lubricant sales across different regions, as well as the factors that influenced their performance. This report is aimed at providing industry stakeholders with valuable insights that can guide their decision-making processes and help them optimize their retail sales performance.

### Data Cleaning and Transformations:

To create this dashboard, I sourced data from an Enterprise resource planner API. ERP extracts are usually characterized by several variables due to its robust architecture. To suit the purpose of this report, I employed some modelling and data standardisation using Powerquery within PowerBI to ensure that the data was consistent and accurate. Finally, the data was visualized using Power Business Intelligence software

### Main Findings:
- **PMS Sales:** Active expansion activities saw the number of active stations rise to 70 as of December 2022, with plans to increase this number significantly in 2023. As a result of this expansion, PMS volume sales in 2022 surpassed that of 2021 by over 10 million liters. Collaboration with the logistics department and improved product supply influenced these volumes. However, more could have been achieved if not for product supply challenges in certain regions.
- **AGO Sales:** AGO sales suffered a dip in 2022 by over one million liters. Product supply challenges coupled with unstable product pricing significantly affected sales performance. Despite the challenges, AGO sales performance peaked in June 2021 and 2022, with poor sales performance in January and February. Sales challenges continued into March and April, and stable conditions resumed in May.
- **Lubricant Sales:** Lubricant sales suffered a dip of over 92,000 liters. Lubricant sales performance was significantly affected by a price increase that occurred in Q3 and Q4 of 2022. Stiff competition from other manufacturers also impacted sales performance, particularly in North 2. Lubricant sales performance peaked in March for H1 2021 and H1 2022, with low sales performance in terms of lubricant sales all through H1 2022.
- **Top Performing Regions:** The West region contributed almost half **(44.25%)** of the revenue generated across all regions. This was reflected in the revenue contribution list by stations where Gbagada, Osapa, Asese, and Agungi rank top 4, all located in the West region. In H2 2022, the West region contributed 33.8% of the revenue generated, with Asese, Osapa, and Gbagada ranking top 3 in revenue contribution.

### Conclusion:
In conclusion, the end-of-year retail sales performance report for 2022 highlights the challenges and successes in the downstream oil and gas sector. While the expansion of retail stations and improved product supply led to an increase in PMS sales volume, AGO sales and lubricant sales experienced challenges. Continued efforts to improve sales performance for all products, including better supply chain management and price optimization strategies, are being implemented to achieve greater sales volumes and revenue contribution across all regions and stations.

![purple-divider](https://user-images.githubusercontent.com/7065401/52071927-c1cd7100-2562-11e9-908a-dde91ba14e59.png)

## Monitoring and Evaluation Dashboard (Agriculture)

<iframe width="1400" height="800" src="https://public.tableau.com/views/MonitoringandEvaluationDashboard/Dashboard1?:language=en-GB&:display_count=n&:origin=viz_share_link:showVizHome=no&:embed=true" frameborder="0" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Introduction:
In the northern states of Nigeria, a monitoring and evaluating project is underway to track the recovery status of agriculture produce. The project aims to effectively monitor the status of submitted produce during the early stages of harvest aggregation. To facilitate this process, an innovative dashboard was created, using a combination of modern technology tools and data visualization techniques.

### ETL Process:
To create this dashboard, an ETL process was used to extract data from various technology partners' APIs. This involved a daily scheduler using Prefect as an orchestration tool, which helped to automate the data extraction process. After the data was extracted, it was then transformed and cleaned using Pandas, to ensure that the data was consistent and accurate for loading into the data warehouse(GCS buckets). Finally, the data was visualized using Tableau, with the data source being Google BigQuery.

### Main Findings:
The resulting dashboard provides a simplistic adaptation of a more robust solution designed to effectively track and monitor project status. The dashboard displays the submitted produce in terms of bags, with sizes ranging between 50kg to 100kg. One of the most notable features of the dashboard is the map adaptation analytics, which offers flexibility and easy visualization of the data. Although the dataset mirrors real-life scenarios, it was slightly altered due to patent rights.

### Conclusion:
The creation of this dashboard has provided an innovative solution to the challenges faced in monitoring and evaluating agriculture produce in the northern states of Nigeria. Through the use of modern technology tools and data visualization techniques, the project has been able to achieve its objectives of effectively tracking and monitoring project status.

<!-- ## Contact
- **Email:** [bukunmiadebanjo@gmail.com](mailto:bukunmiadebanjo@gmail.com)
- **Phone:** +1 (403) 668-1475
- **GitHub:** [Kunmi's GitHub](https://github.com/Khunmi)
- **LinkedIn:** [Kunmi's LinkedIn](https://www.linkedin.com/in/kunmiadebanjo) -->

