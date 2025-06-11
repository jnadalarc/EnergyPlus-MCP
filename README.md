# EnergyPlus MCP Server

A Model Context Protocol (MCP) server that provides **35 comprehensive tools** organized into **5 main categories** for working with EnergyPlus building energy simulation models. This server enables AI assistants and other MCP clients to load, validate, modify, and analyze EnergyPlus IDF (Input Data File) models through a standardized interface.

> **Version**: 0.1.0  
> **EnergyPlus Compatibility**: 25.1.0  
> **Python**: 3.10+

## What is this repo about?

This repository contains an MCP server specifically designed for EnergyPlus building energy simulation workflows. EnergyPlus is a powerful building energy simulation engine, and this MCP server makes it accessible to AI assistants and automation tools.

**Key Features:**
- **🏗️ Complete Model Lifecycle**: Load, validate, analyze, modify, and simulate EnergyPlus IDF files
- **🔍 Deep Building Analysis**: Extract detailed information about zones, surfaces, materials, constructions, and schedules
- **⚙️ Flexible Simulation Control**: Configure simulation parameters, run periods, and output requirements
- **🚀 Automated Simulation**: Execute complete EnergyPlus simulations with weather files and post-processing
- **📊 Advanced Visualization**: Create interactive HTML plots and HVAC system diagrams
- **🔧 HVAC System Intelligence**: Comprehensive discovery, topology analysis, and visualization of HVAC loops
- **📈 Smart Output Management**: Intelligent discovery and configuration of output variables and meters
- **🎯 Building Modifications**: Tools for modifying infiltration, adding window films, surface coatings, and more
- **📋 Schedule Intelligence**: Deep analysis and modification of all EnergyPlus schedule types
- **🖥️ Enterprise Ready**: Built-in logging, error tracking, health monitoring, and debugging capabilities
- **📁 Smart File Management**: Intelligent path resolution, fuzzy file matching, and organized sample libraries

## Architecture

The EnergyPlus MCP Server follows a layered architecture with clear separation of concerns:

- **MCP Protocol Layer**: FastMCP server handling client communications
- **Tools Layer**: 35 tools organized into 5 functional categories
- **Orchestration Layer**: EnergyPlus Manager and Core Config Module for workflow coordination
- **EnergyPlus Integration Layer**: Direct interface to EnergyPlus simulation engine and file system

This architecture enables scalable integration with AI assistants, IDEs, and other MCP clients while maintaining robust error handling and enterprise-grade logging capabilities.

## Available Tools

The EnergyPlus MCP server provides **35 comprehensive tools** organized into **5 main categories** as shown in the architecture diagram:

### 🗂️ **Model Config & Loading** (9 tools)
- **`copy_file`** - Intelligent file copying with path resolution and fuzzy matching
- **`load_idf_model`** - Load and validate EnergyPlus IDF files with detailed error reporting
- **`list_available_files`** - Browse sample files, example files, and weather data
- **`get_model_summary`** - Extract basic model information (Building, Site, SimulationControl, Version)
- **`validate_idf`** - Comprehensive model validation with warnings and errors
- **`check_simulation_settings`** - Review current simulation control and run period settings
- **`modify_simulation_control`** - Modify simulation control parameters (run periods, sizing, etc.)
- **`modify_run_period`** - Adjust simulation time periods and dates
- **`get_server_configuration`** - Get detailed server configuration and version information

### 🔍 **Model Inspection** (9 tools)
- **`list_zones`** - List all thermal zones with detailed properties
- **`get_surfaces`** - Get comprehensive building surface information and geometry
- **`get_materials`** - Extract material and construction definitions
- **`inspect_schedules`** - Deep analysis of all schedule objects with value extraction support
- **`inspect_people`** - Detailed analysis of People objects with occupancy calculations and thermal comfort settings
- **`inspect_lights`** - Comprehensive analysis of Lights objects with power calculations and heat fractions
- **`inspect_electric_equipment`** - Comprehensive analysis of ElectricEquipment objects with power calculations and heat fractions
- **`get_output_variables`** - Get configured variables or discover all available output variables
- **`get_output_meters`** - Get configured meters or discover all available energy meters

### ⚙️ **Model Modification** (8 tools)
- **`modify_people`** - Modify People objects with flexible targeting (all, by zone, or by name)
- **`modify_lights`** - Modify Lights objects with support for different calculation methods
- **`modify_electric_equipment`** - Modify ElectricEquipment objects with support for different calculation methods
- **`change_infiltration_by_mult`** - Modify infiltration rates by multiplication factor
- **`add_window_film_outside`** - Add window films to exterior glazing with custom properties
- **`add_coating_outside`** - Apply exterior surface coatings (walls/roofs) with thermal properties
- **`add_output_variables`** - Add output variables with intelligent validation and formatting
- **`add_output_meters`** - Add output meters with flexible specification formats

### 🚀 **Simulation & Results** (4 tools)
- **`run_energyplus_simulation`** - Execute complete EnergyPlus simulations with weather files
- **`create_interactive_plot`** - Generate interactive HTML plots from simulation results
- **`discover_hvac_loops`** - Discover all HVAC loops (Plant, Condenser, Air) in the model
- **`get_loop_topology`** - Get detailed topology of specific HVAC loops with components and connections

### 🖥️ **Server Management & Logging** (5 tools)
- **`visualize_loop_diagram`** - Generate visual diagrams of HVAC system topology and flow paths
- **`get_server_status`** - Check server health, performance, and system information
- **`get_server_logs`** - Retrieve recent server log entries for debugging
- **`get_error_logs`** - Get recent error log entries for troubleshooting
- **`clear_logs`** - Clear/rotate current log files with automatic backup

## Project Structure

- `sample_files/`: Sample EnergyPlus IDF files and weather data
  - `1ZoneUncontrolled.idf`: Simple single-zone model
  - `1ZoneEvapCooler.idf`: Single-zone with evaporative cooling
  - `5ZoneAirCooled.idf`: Multi-zone air-cooled model
  - `USA_CA_San.Francisco.Intl.AP.724940_TMY3.epw`: Weather file for San Francisco
  
- `energyplus_mcp_server/`: Server implementation
  - `server.py`: FastMCP server with all available tools
  - `energyplus_tools.py`: EnergyPlus file manipulation utilities
- `config.py`: Configuration management
- `utils/`: Advanced utility modules
  - `schedules.py`: Comprehensive schedule parsing, analysis, and modification utilities
  - `diagrams.py`: HVAC diagram generation and visualization tools
  
- `pyproject.toml`: Project metadata and dependencies
- `outputs/`: Directory for simulation outputs and modified files

## Setup Instructions

### Option 1: VS Code Dev Container (Recommended)

The easiest way to get started is using the VS Code dev container, which provides a fully configured environment with EnergyPlus pre-installed.

**Prerequisites:**
- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

**Steps:**
1. Clone the repository:
   ```cmd
   git clone https://github.com/tsbyq/EnergyPlus_MCP.git
   cd EnergyPlus_MCP
   ```

2. Open in VS Code:
   ```cmd
   code .
   ```

3. When prompted, click "Reopen in Container" or:
   - Press `Ctrl+Shift+P`
   - Select "Dev Containers: Reopen in Container"

4. The container will automatically:
   - Install EnergyPlus 25.1.0
   - Set up Python dependencies with `uv`
   - Configure the development environment
   - Install VS Code extensions for Python and EnergyPlus
   - Run `uv sync --extra dev` to install all dependencies

**What's included in the Dev Container:**
- **Pre-configured Environment**: Ubuntu-based container with all dependencies
- **EnergyPlus Integration**: EnergyPlus 25.1.0 pre-installed and configured
- **Python Environment**: Python 3.11+ with `uv` package manager
- **VS Code Extensions**: Python, Jupyter, EnergyPlus ModelKit, and TOML support
- **Port Forwarding**: Automatic forwarding for MCP Inspector (6274), HTTP servers (8080, 3000)
- **Workspace Setup**: Proper workspace folder configuration and Python interpreter paths

The dev container setup is defined in `.devcontainer/` folder with:
- `Dockerfile`: Container image with EnergyPlus and Python setup
- `devcontainer.json`: VS Code configuration, extensions, and port forwarding

### Option 2: Plain Docker

If you prefer using Docker directly without VS Code:

**Prerequisites:**
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

**Steps:**
1. Clone the repository:
   ```cmd
   git clone https://github.com/tsbyq/EnergyPlus_MCP.git
   cd EnergyPlus_MCP
   ```

2. Build the development container:
   ```cmd
   docker build -t energyplus-mcp-dev -f .devcontainer/Dockerfile .
   ```

3. Run the container with volume mount:
   ```cmd
   docker run -it --rm -v "%cd%":/workspace -w /workspace/energyplus-mcp-server energyplus-mcp-dev bash
   ```

4. Inside the container, install dependencies:
   ```bash
   uv sync --extra dev
   ```

### Option 3: Local Development

For local development without containers (requires manual EnergyPlus installation):

**Prerequisites:**
- Python 3.10 or higher
- [uv package manager](https://github.com/astral-sh/uv)
- EnergyPlus 25.1.0 (download from [NREL GitHub](https://github.com/NREL/EnergyPlus/releases))

**Steps:**
1. Clone and navigate to the server directory:
   ```cmd
   git clone https://github.com/tsbyq/EnergyPlus_MCP.git
   cd EnergyPlus_MCP\energyplus-mcp-server
   ```

2. Install dependencies:
   ```cmd
   uv sync --extra dev
   ```

3. Configure EnergyPlus paths in your environment or config file (the server will look for EnergyPlus in standard installation locations).

## How to Use

The EnergyPlus MCP server can be used in several ways depending on your needs:

### 1. As an MCP Server for AI Assistants

The primary use case is connecting the server to MCP-compatible AI assistants (like Claude Desktop, VS Code Copilot, or other MCP clients).

**Start the server:**
```cmd
cd energyplus-mcp-server
uv run python -m energyplus_mcp_server.server
```

The server will start in STDIO mode and can be connected to MCP clients.

**Example MCP client configuration** (for Claude Desktop):
```json
{
  "mcpServers": {
    "energyplus": {
      "command": "uv",
      "args": ["run", "python", "-m", "energyplus_mcp_server.server"],
      "cwd": "/path/to/energyplus-mcp-server"
    }
  }
}
```

### 2. Interactive Development and Testing

**Using the MCP Inspector** (if available):
```cmd
uv run mcp-inspector energyplus_mcp_server.server
```

This opens a web interface for testing the MCP tools interactively.

**Using Python directly:**
```python
# In a Python environment or Jupyter notebook
from energyplus_mcp_server.energyplus_tools import EnergyPlusManager

ep_manager = EnergyPlusManager()

# Load a sample model
result = ep_manager.load_idf("1ZoneUncontrolled.idf")
print(result)

# Get model summary
summary = ep_manager.get_model_basics("1ZoneUncontrolled.idf")
print(summary)
```

### 3. Common Usage Examples

**Load and validate an IDF file:**
```json
{
  "tool": "load_idf_model",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf"
  }
}
```

**Modify simulation settings:**
```json
{
  "tool": "modify_simulation_control",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf",
    "field_updates": {
      "Run_Simulation_for_Weather_File_Run_Periods": "Yes",
      "Do_Zone_Sizing_Calculation": "Yes"
    },
    "output_path": "outputs/modified_model.idf"
  }
}
```

**List zones in a model:**
```json
{
  "tool": "list_zones",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf"
  }
}
```

**Inspect schedules in a model:**
```json
{
  "tool": "inspect_schedules",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "include_values": true
  }
}
```

**Modify infiltration rates:**
```json
{
  "tool": "change_infiltration_by_mult",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf",
    "mult": 0.5,
    "output_path": "outputs/reduced_infiltration.idf"
  }
}
```

**Add window film to exterior surfaces:**
```json
{
  "tool": "add_window_film_outside",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "u_value": 3.5,
    "shgc": 0.35,
    "visible_transmittance": 0.60,
    "output_path": "outputs/with_window_film.idf"
  }
}
```

**Add coating to exterior surfaces:**
```json
{
  "tool": "add_coating_outside",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf",
    "location": "Wall",
    "solar_abs": 0.3,
    "thermal_abs": 0.8,
    "output_path": "outputs/with_coating.idf"
  }
}
```

**Get available sample files:**
```json
{
  "tool": "list_sample_files",
  "arguments": {}
}
```

**Get configured output variables:**
```json
{
  "tool": "get_output_variables",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf"
  }
}
```

**Discover all available output variables:**
```json
{
  "tool": "get_output_variables",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "discover_available": true,
    "run_days": 1
  }
}
```

**Get configured output meters:**
```json
{
  "tool": "get_output_meters",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf"
  }
}
```

**Discover all available output meters:**
```json
{
  "tool": "get_output_meters",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "discover_available": true,
    "run_days": 1
  }
}
```

**Discover HVAC loops:**
```json
{
  "tool": "discover_hvac_loops",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf"
  }
}
```

**Visualize HVAC loop diagram:**
```json
{
  "tool": "visualize_loop_diagram",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "loop_name": "Hot Water Loop",
    "output_path": "outputs/hvac_diagram.png",
    "format": "png"
  }
}
```

**Run EnergyPlus simulation:**
```json
{
  "tool": "run_energyplus_simulation",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf",
    "weather_file": "sample_files/USA_CA_San.Francisco.Intl.AP.724940_TMY3.epw",
    "annual": true,
    "readvars": true
  }
}
```

**Create interactive plot from simulation results:**
```json
{
  "tool": "create_interactive_plot",
  "arguments": {
    "output_directory": "outputs/1ZoneUncontrolled",
    "file_type": "auto",
    "custom_title": "Zone Temperature Analysis"
  }
}
```

**Get server logs for debugging:**
```json
{
  "tool": "get_server_logs",
  "arguments": {
    "lines": 100
  }
}
```

### 4. HVAC System Analysis & Visualization

The server provides advanced HVAC system analysis capabilities with topology detection and visual diagram generation:

**HVAC Analysis Features:**
- **Loop Discovery**: Automatically discover all HVAC loops (Plant, Condenser, Air loops)
- **Topology Mapping**: Extract detailed component-level topology with supply/demand side analysis
- **Component Detection**: Identify fans, coils, pumps, air terminals, zone equipment, and connections
- **Visual Diagrams**: Generate PNG/SVG diagrams of HVAC system flow paths and connections
- **Node Tracking**: Follow air/water node connections throughout the system

**Example HVAC system analysis:**
```json
{
  "tool": "discover_hvac_loops",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf"
  }
}
```

**Get detailed topology for specific loop:**
```json
{
  "tool": "get_loop_topology",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "loop_name": "VAV Sys 1"
  }
}
```

**Generate visual diagram:**
```json
{
  "tool": "visualize_loop_diagram",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "loop_name": "VAV Sys 1",
    "format": "png",
    "show_legend": true
  }
}
```

### 5. Advanced Schedule Analysis

The server includes comprehensive schedule analysis capabilities through the `inspect_schedules` tool and underlying `schedules.py` utilities:

**Supported Schedule Types:**
- `Schedule:Constant`: Single value schedules
- `Schedule:Day:Hourly`: 24-hour daily schedules
- `Schedule:Day:Interval`: Time interval-based daily schedules
- `Schedule:Day:List`: List-based schedules with custom time steps
- `Schedule:Compact`: Complex multi-period schedules
- `Schedule:Year`, `Schedule:Week:*`: Structural schedule references

**Schedule Analysis Features:**
- Parse and extract actual schedule values from all supported types
- Calculate statistics (min, max, average values)
- Natural language parsing for schedule modifications (in development)
- Schedule format conversion between different EnergyPlus types
- Comprehensive validation and error checking

**Example schedule inspection:**
```json
{
  "tool": "inspect_schedules",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "include_values": true
  }
}
```

This will return detailed information about all schedules including their types, references, and actual time-value data.

### 6. Smart Output Management

The server provides intelligent output variable and meter management with auto-discovery capabilities:

**Output Variable Discovery:**
```json
{
  "tool": "get_output_variables",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "discover_available": true,
    "run_days": 1
  }
}
```

**Add output variables with validation:**
```json
{
  "tool": "add_output_variables",
  "arguments": {
    "idf_path": "sample_files/5ZoneAirCooled.idf",
    "variables": [
      "Zone Air Temperature",
      ["Zone Air Relative Humidity", "hourly"],
      {"key_value": "*", "variable_name": "Surface Inside Face Temperature", "frequency": "daily"}
    ],
    "validation_level": "moderate"
  }
}
```

### 7. File Path Handling

The server supports flexible file path resolution:
- **Absolute paths**: Direct file system paths
- **Relative paths**: Relative to the sample_files directory
- **Filename only**: Searches in sample_files directory first
- **Output paths**: Modified files are saved to the outputs directory by default

**Examples:**
```
"1ZoneUncontrolled.idf"                    → sample_files/1ZoneUncontrolled.idf
"sample_files/1ZoneUncontrolled.idf"       → sample_files/1ZoneUncontrolled.idf
"/absolute/path/to/model.idf"              → /absolute/path/to/model.idf
"C:\\Users\\MyUser\\Documents\\model.idf"  → C:\Users\MyUser\Documents\model.idf
```

### 8. Complete Simulation Workflow

The server supports a complete building energy simulation workflow:

**Step 1: Load and validate model**
```json
{
  "tool": "load_idf_model",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf"
  }
}
```

**Step 2: Modify simulation settings (optional)**
```json
{
  "tool": "modify_simulation_control",
  "arguments": {
    "idf_path": "sample_files/1ZoneUncontrolled.idf",
    "field_updates": {
      "Do_Zone_Sizing_Calculation": "Yes",
      "Do_System_Sizing_Calculation": "Yes"
    },
    "output_path": "outputs/modified_model.idf"
  }
}
```

**Step 3: Run simulation**
```json
{
  "tool": "run_energyplus_simulation",
  "arguments": {
    "idf_path": "outputs/modified_model.idf",
    "weather_file": "sample_files/USA_CA_San.Francisco.Intl.AP.724940_TMY3.epw",
    "annual": true,
    "readvars": true
  }
}
```

**Step 4: Create interactive visualization**
```json
{
  "tool": "create_interactive_plot",
  "arguments": {
    "output_directory": "outputs/modified_model",
    "file_type": "variable",
    "custom_title": "Annual Energy Performance"
  }
}
```

### 9. Server Management and Debugging

The server includes comprehensive logging and debugging tools:

**Monitor server health:**
```json
{
  "tool": "get_server_status",
  "arguments": {}
}
```

**View recent activity:**
```json
{
  "tool": "get_server_logs",
  "arguments": {
    "lines": 50
  }
}
```

**Check for errors:**
```json
{
  "tool": "get_error_logs",
  "arguments": {
    "lines": 20
  }
}
```

## Available Tools Reference

| Tool | Description | Required Args | Optional Args |
|------|-------------|---------------|---------------|
| **File Management** | | | |
| `copy_file` | Intelligent file copying with path resolution | `source_path: str`, `target_path: str` | `overwrite: bool`, `file_types: List[str]` |
| `list_available_files` | Browse sample files, example files, and weather data | - | `include_example_files: bool`, `include_weather_data: bool` |
| **Model Loading & Validation** | | | |
| `load_idf_model` | Load and validate an IDF file | `idf_path: str` | - |
| `validate_idf` | Comprehensive validation with warnings and errors | `idf_path: str` | - |
| **Model Analysis** | | | |
| `get_model_summary` | Get basic model information | `idf_path: str` | - |
| `list_zones` | List all thermal zones with properties | `idf_path: str` | - |
| `get_surfaces` | Get comprehensive building surface information | `idf_path: str` | - |
| `get_materials` | Get material and construction definitions | `idf_path: str` | - |
| `inspect_schedules` | Deep analysis of all schedule objects | `idf_path: str` | `include_values: bool` |
| **Occupancy & Equipment** | | | |
| `inspect_people` | Detailed analysis of People objects | `idf_path: str` | - |
| `modify_people` | Modify People objects with flexible targeting | `idf_path: str`, `modifications: List[Dict]` | `output_path: str` |
| `inspect_lights` | Comprehensive analysis of Lights objects | `idf_path: str` | - |
| `modify_lights` | Modify Lights objects with calculation methods | `idf_path: str`, `modifications: List[Dict]` | `output_path: str` |
| `inspect_electric_equipment` | Comprehensive analysis of ElectricEquipment objects | `idf_path: str` | - |
| `modify_electric_equipment` | Modify ElectricEquipment objects with calculation methods | `idf_path: str`, `modifications: List[Dict]` | `output_path: str` |
| **Simulation Configuration** | | | |
| `check_simulation_settings` | Review simulation control and run period settings | `idf_path: str` | - |
| `modify_simulation_control` | Modify simulation control parameters | `idf_path: str`, `field_updates: dict` | `output_path: str` |
| `modify_run_period` | Adjust simulation time periods | `idf_path: str`, `field_updates: dict` | `run_period_index: int`, `output_path: str` |
| **Building Modifications** | | | |
| `change_infiltration_by_mult` | Modify infiltration rates by multiplication | `idf_path: str`, `mult: float` | `output_path: str` |
| `add_window_film_outside` | Add window films to exterior glazing | `idf_path: str` | `u_value: float`, `shgc: float`, `visible_transmittance: float`, `output_path: str` |
| `add_coating_outside` | Apply exterior surface coatings | `idf_path: str`, `location: str` | `solar_abs: float`, `thermal_abs: float`, `output_path: str` |
| **Output Management** | | | |
| `get_output_variables` | Get/discover output variables | `idf_path: str` | `discover_available: bool`, `run_days: int` |
| `get_output_meters` | Get/discover output meters | `idf_path: str` | `discover_available: bool`, `run_days: int` |
| `add_output_variables` | Add output variables with validation | `idf_path: str`, `variables: List` | `validation_level: str`, `allow_duplicates: bool`, `output_path: str` |
| `add_output_meters` | Add output meters with validation | `idf_path: str`, `meters: List` | `validation_level: str`, `allow_duplicates: bool`, `output_path: str` |
| **HVAC System Analysis** | | | |
| `discover_hvac_loops` | Discover all HVAC loops in model | `idf_path: str` | - |
| `get_loop_topology` | Get detailed topology of specific HVAC loop | `idf_path: str`, `loop_name: str` | - |
| `visualize_loop_diagram` | Generate visual diagrams of HVAC systems | `idf_path: str` | `loop_name: str`, `output_path: str`, `format: str`, `show_legend: bool` |
| **Simulation & Analysis** | | | |
| `run_energyplus_simulation` | Execute complete EnergyPlus simulations | `idf_path: str` | `weather_file: str`, `output_directory: str`, `annual: bool`, `design_day: bool`, `readvars: bool`, `expandobjects: bool` |
| `create_interactive_plot` | Generate interactive HTML plots from results | `output_directory: str` | `idf_name: str`, `file_type: str`, `custom_title: str` |
| **Server Management** | | | |
| `get_server_status` | Check server health and performance | - | - |
| `get_server_configuration` | Get detailed server configuration | - | - |
| `get_server_logs` | Retrieve recent server log entries | - | `lines: int` |
| `get_error_logs` | Get recent error log entries | - | `lines: int` |
| `clear_logs` | Clear/rotate log files with backup | - | - |

## Dependencies

This project uses `uv` for fast dependency management. All dependencies are defined in `pyproject.toml`:

### Core Dependencies
- **`mcp[cli]`**: Model Context Protocol framework with CLI tools
- **`eppy`**: EnergyPlus Python library for IDF file manipulation
- **`matplotlib`**: Plotting library for generating HVAC loop diagrams
- **`plotly`**: Interactive plotting library for creating HTML visualizations from simulation results
- **`pandas`**: Data analysis library for processing EnergyPlus output files
- **`networkx`**: Graph analysis library for HVAC topology visualization
- **`graphviz`**: Graph visualization library for generating complex network diagrams

### Development Dependencies (installed with `--extra dev`)
- **`ipykernel`**: Jupyter notebook kernel support
- **`pytest`**: Testing framework
- **`pytest-cov`**: Test coverage reporting
- **`pytest-asyncio`**: Async testing support
- **`black`**: Code formatting
- **`ruff`**: Fast Python linter and formatter
- **`mypy`**: Static type checking

### System Dependencies (in dev container)
- **EnergyPlus 25.1.0**: Building energy simulation engine
- **Node.js 20**: For MCP inspector and web-based tools
- **Python 3.12**: Runtime environment

## Configuration

The server uses a configuration system that can be customized through environment variables or config files. Key configuration areas:

- **EnergyPlus paths**: IDD file location, executable path, version
- **File paths**: Sample files, output directory, temporary files
- **Server settings**: Name, version, debug mode
- **Logging**: Level and format configuration

Default configuration works out-of-the-box in the dev container environment.

## Troubleshooting

**Common Issues:**

1. **"IDD file not found"**: Ensure EnergyPlus is properly installed and the IDD path is configured
2. **"Import error: eppy"**: Run `uv sync` to install dependencies
3. **"Permission denied"**: Ensure proper file permissions for input/output directories
4. **"Invalid IDF file"**: Check IDF syntax using EnergyPlus validation tools
5. **"Simulation failed"**: Check simulation output files in the results directory for EnergyPlus error messages
6. **"Plot creation failed"**: Ensure simulation outputs exist and contain valid data

**Debug Mode:**
Set `debug_mode: true` in configuration or use environment variable to enable verbose logging.

**Getting Help:**
- Check server status: Use the `get_server_status` tool
- View recent logs: Use the `get_server_logs` tool
- Check for errors: Use the `get_error_logs` tool
- Validate configuration: Use the `get_server_configuration` tool
- Sample files: Use `list_sample_files` to see available test files
- Clear logs if needed: Use the `clear_logs` tool to rotate log files

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make changes with appropriate tests
4. Run linting: `uv run ruff check`
5. Run formatting: `uv run black .`
6. Run tests: `uv run pytest`
7. Submit a pull request

## License

See [LICENSE](License.txt) file for details.