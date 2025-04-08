---
name: Bigfoot Sightings Analysis
tools: [Python, Altair, vega-lite]
description: Interactive analysis of geographic and seasonal distribution patterns of Bigfoot sightings across the United States
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
---

# Bigfoot Sightings Analysis

For this assignment, I analyzed the BFRO (Bigfoot Field Researchers Organization) dataset, which contains reports of bigfoot sightings across the United States. This dataset includes information about the location, date, and details of each reported sighting, along with environmental conditions at the time of the sighting.

Below are links to both the data and the analysis code:

<div class="left">
{% include elements/button.html link="https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/bfro_reports_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/kelaifosimate/kelaifosimate.github.io/blob/main/python_notebooks/Workbook.ipynb" text="The Analysis" %}
</div>

## Visualization 1: Interactive Map of Bigfoot Sightings

<vegachart schema-url="{{ site.baseurl }}/assets/json/bigfoot_map.json"></vegachart>

This first visualization is an interactive map showing the geographical distribution of bigfoot sightings across the United States from 1950 to 2022. Each point on the map represents a reported sighting, with colors indicating the classification type of the sighting (Class A, Class B, or Class C). 

For this visualization, I chose a geospatial encoding, where the longitude and latitude coordinates directly map to positions on a US map projection. I used color encoding to distinguish between different classification types, choosing a categorical color scheme (category10) to make it easy to differentiate between the classification categories. The size and opacity of the points were carefully adjusted to prevent overcrowding while maintaining visibility.

I performed several data transformations to prepare for this visualization. First, I extracted the year from the date strings using regular expressions, as the original date format was inconsistent. I then filtered out entries with missing coordinates or invalid years, and limited the dataset to sightings between 1950 and 2022 to ensure data quality. This transformation was necessary because the original date field contained various text formats rather than standardized dates.

The interactivity in this visualization comes from the year slider at the top of the chart. This allows users to filter sightings by year, showing only sightings that occurred before or during the selected year. This temporal filtering helps reveal patterns in the geographical spread of sightings over time, making it possible to observe how reports have expanded or concentrated in different regions over the decades. Additionally, hovering over any point displays a tooltip with detailed information about that specific sighting, including the state, county, year, season, and classification.

This visualization is different from my Homework #5 submission as I did not use this dataset for that assignment, and the interactive approach here focuses on temporal filtering rather than categorical filtering.

## Visualization 2: Seasonal Patterns of Bigfoot Sightings by State

<vegachart schema-url="{{ site.baseurl }}/assets/json/bigfoot_seasonal.json"></vegachart>

The second visualization explores the seasonal patterns of bigfoot sightings across different states. It shows the number of sightings reported in each season (Spring, Summer, Fall, Winter) for a selected state.

For this chart, I used a bar chart encoding with the x-axis representing seasons and the y-axis representing the count of sightings. I implemented a custom color scheme for the seasons that intuitively corresponds to them: green for Spring, orange for Summer, deep red for Fall, and blue for Winter. This color choice enhances the readability of the visualization and helps users associate the bars with their respective seasons.

The data transformations for this visualization involved grouping the sightings by state and season, then counting the occurrences in each group. I also ensured that the seasons are displayed in the natural order (Spring, Summer, Fall, Winter) rather than alphabetically, which helps users interpret the seasonal patterns more intuitively.

The interactivity in this visualization is implemented through a state selection dropdown that allows users to select any state to view its seasonal sighting patterns. This interactivity makes the visualization more engaging and allows users to explore patterns specific to their area of interest. The tooltip provides additional information when hovering over each bar, displaying the exact count of sightings for each state-season combination.

This visualization differs from any previous homework submissions as it focuses specifically on seasonal patterns, which I had not explored before. The addition of the state selection dropdown provides a new dimension of interactivity that allows for more detailed exploration of the data.

The interactivity elements in these visualizations significantly enhance the user experience and data exploration capabilities. In the map visualization, the year slider allows users to see how bigfoot sightings have evolved over time, potentially revealing migration patterns or reporting trends. This time-based filtering is much more effective than showing all sightings at once, which would result in overcrowding and make patterns difficult to discern.

For the seasonal pattern visualization, the state dropdown makes it possible to compare seasonal patterns across different states without creating an overwhelming and cluttered chart that tries to show all states at once. This focused approach allows users to identify whether bigfoot sightings in different regions show similar seasonal patterns or whether they differ based on geography.

Together, these interactive elements transform static visualizations into exploration tools that invite users to engage with the data and discover insights on their own. The combination of geographical, temporal, and categorical dimensions provides a comprehensive view of the bigfoot sighting phenomenon across the United States.

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>
