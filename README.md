# Audible Audiobook Insights: Power BI Dashboard

An interactive two-page Power BI dashboard that explores an Audible audiobook catalog of about 82,000 titles. It covers what the catalog contains, and how titles are rated and priced.

**Tools:** Microsoft Excel (data cleaning), Power Query (pre-processing), Power BI Desktop with DAX (visualization)

---

## Dashboard Preview

### Page 1: Catalog Overview


![Page 1 - Catalog Overview](Page%201.png)



### Page 2: Ratings & Pricing


![Page 2 - Ratings & Pricing](Page%202.png)



---

## Project Workflow

1. **Data cleaning (Excel):** cleaned the raw Audible dataset and saved the cleaned version.
2. **Pre-processing (Power Query):** prepared the cleaned data for analysis in Power BI (see below).
3. **Visualization (Power BI):** built KPIs, charts, slicers and a two-page dashboard using DAX measures.

## Dataset

The cleaned dataset has about 82,762 audiobook titles with these fields:

| Column | Description |
|---|---|
| Name | Title of the audiobook |
| Author | Author(s) of the title |
| Narrator | Narrator(s) of the title |
| Duration | Listening time (originally text, e.g. "9 hrs and 28 mins") |
| Releasedate | Release date (day/month/year) |
| Language | Language of the title |
| No of stars | Star rating (out of 5) |
| No of Ratings | Number of ratings |
| Book Ratings | Rating category (Excellent, Very Good, Good, Average, Poor) |
| Price | Listed price |

## Pre-processing in Power Query

- Inserted spaces into Author and Narrator names (e.g. `JohnGray` became `John Gray`) with a custom column.
- Converted the text Duration into numeric **Minutes** and **Hours** columns.
- Converted **Releasedate** to a Date type using an English (India) locale, so day/month order is read correctly.
- Added a **Year** column and a **Duration Band** column (Under 3 hrs, 3-10 hrs, Over 10 hrs).
- Set correct data types for all columns and renamed the table.

## Business Questions Answered

**Page 1: Catalog Overview**
1. How big is the catalog, and what are the average price, listening time and rating? (KPI cards)
2. How many titles were released each year?
3. Which authors have the most titles?
4. How long are titles typically?

**Page 2: Ratings & Pricing**
1. Which languages make up the catalog?
2. What share of titles falls in each rating category?
3. Does a longer duration mean a higher price?
4. Which titles combine a high rating with a large number of ratings?

## Dashboard Features

- **KPI cards:** Total Titles, Average Price, Average Listening Hours, Average Star Rating
- **Charts:** titles released per year, top 10 authors, titles by duration band, titles by language (top 5), duration vs price scatter with trend line, share of titles by rating category
- **Table:** top-rated titles with reliable rating counts
- **Slicers:** Year, Duration Band, Language, Book Ratings

## DAX Measures

```
Total Titles = COUNTROWS(Audible_Audiobook_Catalog)
Average Price = AVERAGE(Audible_Audiobook_Catalog[Price])
Avg Listening Hours = AVERAGE(Audible_Audiobook_Catalog[Hours])
Avg Star Rating = AVERAGE(Audible_Audiobook_Catalog[No of stars])
```

## Key Insights

- **English dominates the catalog**, with about 58K of 82.8K titles (around 70%). The top five languages (English, German, Italian, Japanese, Spanish) cover about 90% of titles.
- **Releases peaked around 2020-2021** at roughly 22.6K titles in a single year.
- **Most titles are mid-length:** about 39.7K titles are 3-10 hours, 24K are under 3 hours, and 19K are over 10 hours. The average is 6.9 hours.
- **Ratings are uniformly high:** the average is 4.49 stars, and the large majority of titles fall in the "Very Good" category.
- **Duration is only a weak driver of price.** The trend line rises only slightly from short to long titles.
- **The most-rated titles are mainstream non-fiction**, led by *Atomic Habits* (12,569 ratings at 5.0 stars).

## Limitations

- The Author field includes brands, publishers and series names (for example "Smart Reading") as well as individual people.
- Titles with very few ratings can show extreme averages, so the top-rated table only includes titles with at least 1,000 ratings and 4.5 stars or more.
- Data appears sparse after about 2021, so recent years should be read with caution.
- The scatter plot is limited to titles under 40 hours and under 3,000 in price for readability.

## Files in This Repository

- `Audible Audiobook Dashboard.pbix`: the Power BI dashboard file
- `Page 1.png`, `Page 2.png`: dashboard screenshots
- `README.md`: project documentation

## How to Use

1. Download `Audible Audiobook Dashboard.pbix` from this repository.
2. Open it in Power BI Desktop.
3. Use the slicers to filter by year, language, duration and rating category.

## Author

**[Josna Treessa PG]**
Aspiring Data Analyst | Kozhikode, India
[LinkedIn](https://www.linkedin.com/in/josnatreessa) | [GitHub](https://github.com/josnatreessa)
