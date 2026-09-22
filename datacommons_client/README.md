# Data Commons Python API

This is a Python library for accessing data in the Data Commons Graph via the V2 REST API (`node`, `observation`, `resolve`) and the SDMX 3.0 REST API (`data`, `availability`).

To get started, install this package from pip.

```bash
pip install datacommons-client
```

To get additional functionality to work with Pandas DataFrames, install the package
with the optional Pandas dependency.

```bash
pip install "datacommons-client[Pandas]"
```

Once the package is installed, import `datacommons_client` and initialize `DataCommonsClient`:

```python
from datacommons_client import DataCommonsClient

client = DataCommonsClient(api_key="YOUR_API_KEY")

# V2 Observation query
observations = client.observation.fetch(
    variable_dcids="Count_Person",
    entity_dcids=["country/USA"],
)

# SDMX 3.0 Data query (returns SDMX-CSV by default)
csv_data = client.sdmx.fetch_data(
    variable="Count_Person",
    constraints={"observationAbout": "country/USA"},
)

# SDMX 3.0 Availability query (returns parsed SDMX-JSON)
availability = client.sdmx.fetch_availability(
    component_id="provenance",
    variable="Count_Person",
)
```

For more detail on getting started with the API, please visit <https://docs.datacommons.org/api/python/v2/>.

