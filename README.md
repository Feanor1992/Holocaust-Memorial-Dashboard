# Holocaust Memorial Dashboard

This code creates an interactive web dashboard that visualizes the locations of Holocaust concentration camps and their subcamps across Europe. Here's a detailed breakdown of its structure and functionality:

## Data Handling and Preparation ##

The code begins by importing necessary libraries:
- `pandas` and `numpy` for data processing
- `dash` framework components for creating the web application
- `plotly.express` for interactive map visualization

It loads camp location data from a CSV file named `Camps.csv` and adds a dictionary mapping main camps to estimated Jewish death counts. This data is used to create scaled marker sizes (using a logarithmic scale) to visually represent the magnitude of deaths at each **MAIN camp**.

Additional contextual information about each main camp is stored in the `camp_info` dictionary, which provides brief historical descriptions that will be displayed when users interact with the map.

## Dashboard Structure ##

The dashboard is built using `Dash`, a Python framework for building analytical web applications. It consists of:
1. **Header Section:**
    - A title "Holocaust Subcamp Dashboard"
    - A subtitle explaining marker sizing
2. **Control Panel (left side, 25% width):**
    - Main camp filter dropdown (multi-select with "All" option)
    - Map style selector with 3 options (OpenStreetMap, Carto Light, Carto Dark)
    - Information box that displays details when a marker is clicked
3. **Map Display (right side, 75% width):**
    - Interactive map using Plotly's `scatter_mapbox`
    - Camps displayed as colored dots sized according to death counts
    - Centered on Europe with appropriate zoom level
4. **Footer:**
    - Links to authoritative data sources including Auschwitz Museum, USHMM, Holocaust Encyclopedia, and Yad Vashem

## Interactive Features ##

The dashboard includes two callback functions that enable interaction:
1. `update_map()` - Triggered when filter selections change:
    - Filters the dataset based on selected main camps
    - Updates the map with filtered data
    - Configures hover information and custom data for each point
2. `display_info()` - Triggered when a marker is clicked:
    - Extracts data about the selected camp
    - Formats and displays detailed information in the info box
    - Shows subcamp name, main camp affiliation, death count, and historical context

## Technical Implementation ##
- The map uses **Mapbox** integration through `Plotly`
- Marker sizes are **logarithmically** scaled to handle the wide range of death counts
- Custom data is attached to each point to support the information display
- The layout is responsive with flexible sizing
