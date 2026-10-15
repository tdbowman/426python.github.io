# Week 10: Internet Data & APIs

## Overview

Welcome to Week 10! Learn to fetch data from the internet and work with web APIs to access real-world data sources.

## Watch: Internet Data & APIs

:::{iframe} https://tdbowman.github.io/426python.github.io/videos/week10.html
:width: 100%
:label: week10-animation

**Week 10 animation (0:53).** Asking another program for data, and reading its answer. Watch the code on the left, and what Python stores and prints on the right. Pause anytime.
:::

:::{dropdown} Text version of the animation
**Ask**

- An API is a web address built for programs instead of people. We'll ask Open Library's search API about Dune.
- params= builds the ?q=dune&limit=1 part of the address for us. timeout=10 stops with an error if the server goes silent for 10 seconds, instead of waiting forever.
- The server answers. Status code 200 means OK.

**Read the answer**

- Check first: r.ok is True for a good answer. If the server answers with an error code, we print it instead of trying to read bad data.
- The reply is JSON text. `r.json()` turns it into a Python dictionary. (Shortened here: the real one is much bigger.)
- `data["docs"]` is a list of results, and [0] picks the first one, which is itself a dictionary.
- Pick out the fields we need: Dune, first published in 1965.

**Key idea:** An API lets your program ask another program for data. Send a request with params= and a timeout=, check the status before you trust the answer, then use `.json()` to turn the reply into dictionaries and lists.
:::

## Learning Objectives

- Understand what APIs are and how they work
- Make HTTP requests using the `requests` library
- Parse JSON data from APIs
- Handle API responses and errors
- Work with real APIs (weather, news, etc.)
- Build programs that fetch live data

## Topics Covered

1. **API Basics**
   - What is an API?
   - REST APIs
   - HTTP methods (GET, POST)
   - API keys and authentication

2. **The requests Library**
   - Installing requests
   - Making GET requests
   - Handling responses
   - Status codes

3. **Working with JSON**
   - Parsing JSON responses
   - Extracting data
   - Nested JSON structures

4. **Practical APIs**
   - Weather APIs
   - News APIs
   - Public data sources
   - Rate limits and best practices

## Assignments This Week

```{note}
All assignments are due by 11:59 PM on the specified date in Canvas
```

- **Assignment 3** - Assigned this week
- **Weekly Discussion** - Participate in forum

## Readings

**Required:**
- Mastrodomenico - Chapter 18
   - Review course materials on modules

**Recommended:**
- [Real Python - API Integration](https://realpython.com/api-integration-in-python/)
- [Moesif - API Tutorial](https://www.moesif.com/blog/technical/api-development/Python-API-Tutorial/)


---

## Internet Data & APIs - Quick Guide

### Installing requests

```bash
pip install requests --break-system-packages
```

### Basic API Request

```python
import requests

# Make GET request
response = requests.get("https://api.example.com/data")

# Check if successful
if response.status_code == 200:
    data = response.json()  # Parse JSON
    print(data)
else:
    print(f"Error: {response.status_code}")
```

### Working with JSON Data

```python
import requests

# Get data from API
response = requests.get("https://api.weather.com/current")
data = response.json()

# Access data
temperature = data["main"]["temp"]
conditions = data["weather"][0]["description"]

print(f"Temperature: {temperature}°F")
print(f"Conditions: {conditions}")
```

### Using API Keys

```python
import requests

API_KEY = "your-api-key-here"
url = "https://api.example.com/data"

# Pass API key as parameter
params = {"apikey": API_KEY}
response = requests.get(url, params=params)

if response.ok:
    data = response.json()
    print(data)
```

### Error Handling

```python
import requests

try:
    response = requests.get("https://api.example.com/data", timeout=5)
    response.raise_for_status()  # Raise error for bad status
    data = response.json()
    print(data)
except requests.exceptions.Timeout:
    print("Request timed out")
except requests.exceptions.HTTPError as e:
    print(f"HTTP error: {e}")
except requests.exceptions.RequestException as e:
    print(f"Error: {e}")
```

### Practical Example: Weather App

```python
import requests

def get_weather(city, api_key):
    url = "https://api.openweathermap.org/data/2.5/weather"
    params = {
        "q": city,
        "appid": api_key,
        "units": "imperial"
    }
    
    response = requests.get(url, params=params)
    
    if response.ok:
        data = response.json()
        temp = data["main"]["temp"]
        desc = data["weather"][0]["description"]
        return f"{city}: {temp}°F, {desc}"
    else:
        return f"Error getting weather for {city}"

# Use it
weather = get_weather("Chicago", "your-api-key")
print(weather)
```

## Popular Free APIs

- **OpenWeatherMap** - Weather data
- **NewsAPI** - News headlines
- **JSONPlaceholder** - Fake data for testing
- **REST Countries** - Country information
- **CoinGecko** - Cryptocurrency data

## Summary

✅ **APIs** - Access data from web services  
✅ **requests** - Python library for HTTP  
✅ **JSON** - Common data format for APIs  
✅ **GET requests** - Retrieve data  
✅ **Error handling** - Handle network issues  
✅ **Real data** - Build apps with live information  
