---
title: "Divvy-trip-2019 & 2020: A Comparative Analysis of Rider Behavior"
author: "Data Analyst"
date: "`r Sys.Date()`"
---

# **Project Overview**

<p>The "Divvy-trip-2019 & 2020" project is an analysis of Divvy bike-sharing data, focusing on the fourth quarter of 2019 and the first quarter of 2020. The primary objective is to compare ride-sharing habits between two key user types: **members** (subscribers) and **casual riders**. The analysis is conducted using the R programming language, with a strong reliance on packages from the **tidyverse** ecosystem, including `dplyr` for data manipulation and `ggplot2` for data visualization. This report details the methodology and key findings from the analysis.</p>

<br>

# **Data and Methodology**

### **Data Loading and Initial Inspection**

<p>The analysis begins by loading two separate CSV files: `Divvy_Trips_2019_Q4.csv` and `Divvy_Trips_2020_Q1.csv`. To ensure consistency for merging, several data cleaning steps were performed:</p>

<ul>
<li>The column names of the 2019 data were renamed to match the 2020 data's naming convention (e.g., `ride_id`, `started_at`, `ended_at`).</li>
<li>The `birthyear`, `gender`, and `tripduration` columns were removed from the 2019 data.</li>
<li>The `start_lat`, `start_lng`, `end_lat`, and `end_lng` columns were removed from the 2020 data.</li>
</ul>

### **Data Cleaning and Transformation**

<p>Once the datasets were standardized, they were combined into a single data frame called `all_trips` using `bind_rows()`. Further transformations included:</p>

<ul>
<li>The `member_casual` column was standardized by recoding "Subscriber" to "member" and "Customer" to "casual".</li>
<li>New columns—`date`, `month`, `day`, `year`, and `day_of_week`—were extracted from the timestamp columns to facilitate time-based analysis.</li>
<li>A new column, `ride_length`, was created to capture the duration of each ride in seconds by calculating the time difference between `ended_at` and `started_at`.</li>
<li>"Bad" data was filtered out, specifically rides with a duration less than 0 or those starting from the station "HQ QR".</li>
</ul>

<br>

# **Key Findings and Analysis**

### **Descriptive Statistics on `ride_length`**

<p>Initial descriptive statistics revealed significant differences in ride duration between the two rider types. The overall mean, median, minimum, and maximum ride lengths were calculated. A key finding was that **casual riders consistently have a longer average ride duration than members**.</p>

### **Riding Behavior by Day of the Week**

<p>The days of the week were reordered correctly to provide a clear, chronological view of riding patterns. The analysis then focused on comparing average ride times and the number of rides across different days for each user group.</p>

**Visualizations and Insights:**

<p>A visualization created using `ggplot2` showed the total number of rides per day for both casual and member riders. The plot clearly indicated that **casual ridership is significantly higher on weekends**, while **member ridership remains more consistent throughout the week**, peaking slightly on weekdays.</p>

<p>Another visualization of the average ride duration per day reinforced the earlier finding. It demonstrated that **casual rides are, on average, much longer than member rides**, a difference that becomes even more pronounced on the weekends.</p>
