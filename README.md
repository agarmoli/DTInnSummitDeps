# DTInnSummitDeps

Repository for managing and loading dependencies (`.whl` files) into Snowflake.

## Description

This repository contains a library that facilitates the automatic loading of wheel files (`.whl`) from a local folder into Snowflake, enabling you to manage the Python dependencies required for your applications and stored procedures.

## Project Structure

```
DTInnSummitDeps/
├── deps/              # Folder containing .whl files
├── wheel_loader.py    # Main library for loading wheels
└── README.md          # This file
```

## Requirements

- Python 3.x
- Snowflake Connector for Python
- Access to a Snowflake account with permissions to upload files to stages

## Installation

1. Clone this repository:
```bash
git clone https://github.com/agarmoli/DTInnSummitDeps.git
cd DTInnSummitDeps
```

2. Install the required dependencies:
```bash
pip install snowflake-connector-python
```

## Usage

### Preparation

1. Place all `.whl` files you want to load in the `deps/` folder

2. Configure your Snowflake credentials (can be done through environment variables or a configuration file)

### Loading Wheels to Snowflake

```python
from wheel_loader import WheelLoader

# Initialize the loader with your Snowflake configuration
loader = WheelLoader(
    account='your_account',
    user='your_user',
    password='your_password',
    database='your_database',
    schema='your_schema',
    warehouse='your_warehouse'
)

# Load all .whl files from the deps/ folder
loader.load_wheels_from_directory('deps/')
```

## Features

- **Automatic loading**: Detects and loads all `.whl` files from a specific folder
- **Dependency management**: Simplifies the maintenance of Python libraries in Snowflake
- **Easy integration**: Simple and straightforward API to incorporate into your workflows

---

**Note**: This project is specifically designed for DTInn Summit and facilitates the management of Python dependencies in Snowflake environments.
