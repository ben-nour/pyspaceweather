<h1 align=center>pyspaceweather</h2>

<p align="center">
    <a href='https://py-spaceweather.readthedocs.io/en/latest/?badge=latest'><img src='https://readthedocs.org/projects/py-spaceweather/badge/?version=latest' alt='Documentation Status' /></a>
    <a href="https://github.com/ben-nour/pyspaceweather/actions/workflows/tests.yml/badge.svg"><img src="https://github.com/ben-nour/pyspaceweather/actions/workflows/tests.yml/badge.svg"           alt="Testing"></a>
    <a href="https://codecov.io/gh/ben-nour/pyspaceweather"><img src="https://codecov.io/gh/ben-nour/pyspaceweather/graph/badge.svg"/></a>
    <a href="https://pypi.org/project/pyspaceweather/"><img src="https://img.shields.io/pypi/pyversions/pyspaceweather" alt="versions"></a>
    <a href="https://github.com/ben-nour/pyspaceweather/blob/main/LICENSE"><img src="https://img.shields.io/pypi/l/pyspaceweather" alt="License"></a>
    <a href="https://github.com/orbitalindex/awesome-space"><img src="https://awesome.re/mentioned-badge.svg" alt="awesome list badge"></a>
</p>


`pyspaceweather` is a Python wrapper for the Australian Bureau of Metererology's [Space Weather API](https://sws-data.sws.bom.gov.au/).

The API provides access to near real-time data from the BOM's Australian Space Weather Forecasting Centre.

## Installation

```
pip install pyspaceweather
```

## Usage

An API key, which you can get from the [BOM](https://sws-data.sws.bom.gov.au/register), is required to use the API:

```python
import os

from pyspaceweather import SpaceWeather

sw = SpaceWeather(os.environ["SPACEWEATHER_API_KEY"])
```

Each [API request method](https://sws-data.sws.bom.gov.au/api-docs#overview) is available as a method of `SpaceWeather`.

For example, to get details of any magnetic alert current for the Australian region.

```python
alert_warnings = sw.get_mag_alert()
```

What's returned is a list of `MagAlert` objects:
```python
[MagAlert(start_time=datetime.datetime(2015, 2, 7, 8, 45),
valid_until=datetime.datetime(2015, 2, 7, 20, 45),
g_scale=1,
description='minor')
]
```

Or, to get historical A-index values, you can call `get_a_index()`, passing a string or `datetime` object to the relevant parameters:

```python
a_index_data = sw.get_a_index(start="2023-01-01 00:00:00", end=datetime(2023, 12, 1, 12, 30))
```

## Documentation

You can read documentation for this wrapper at [ReadTheDocs](https://py-spaceweather.readthedocs.io/en/latest/).


