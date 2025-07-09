EIA Power Plant Data Mapper

Overview
The EIA Power Plant Data Mapper is a Python application designed to scrape and visualize the locations of power plants across the United States. The application fetches data from the U.S. Energy Information Administration (EIA) API, mapping various energy sources, including coal, natural gas, oil, renewable sources, and more. The map includes a legend and layers for different fuel source types.

Learning Journey
This project is my first real work project after learning Python for two weeks. I welcome constructive feedback as I continue to learn and improve my skills.

Features
- Scrapes power plant location data from the EIA API.
- Visualizes power plants on a map using Folium.
- Includes a legend to identify different fuel source types.
- Allows for toggling between different energy source layers on the map.

Future Development
- Map electrical supply, demand, surplus, and electricity costs.
- Map data centers across the U.S. (currently lacking comprehensive free data sources).

Requirements
- Python 3.x
- Pandas
- Folium
- Requests

Installation
To run this project, make sure you have Python installed. Then, install the required packages using pip:

pip install pandas folium requests

Usage
1. Set Up Your API Key: Replace the api_key variable in the code with your actual EIA API key.
2. Run the Script: Execute the Python script. It will fetch data from the EIA API and generate an HTML map file named all_energy_types_locations_map.html.
3. Open the Map: Open the generated HTML file in a web browser to view the interactive map of power plants.

Code Example
Here’s a snippet of the code that fetches data from the API and creates the map:

import pandas as pd
import requests
import folium

# API URL and parameters
api_url = "https://api.eia.gov/v2/electricity/operating-generator-capacity/data/"
api_key = "YOUR_API_KEY"

params = {
    'api_key': api_key,
    'frequency': 'monthly',
    'data[0]': 'latitude',
    'data[1]': 'longitude',
    'data[2]': 'net-summer-capacity-mw',
    'data[3]': 'energy_source_code',
    'sort[0][column]': 'period',
    'sort[0][direction]': 'asc',
    'offset': 0,
    'length': 5000
}

# Fetch data from the API
response = requests.get(api_url, params=params)
if response.status_code == 200:
    data = response.json()
    df = pd.DataFrame(data['response']['data'])
    # Further processing and map generation...

Contribution
If you have suggestions or improvements, feel free to contribute! (AI minorly contributed to this project, but I understand just about everything that this code does)

License
This project is open-source and available under the MIT License.