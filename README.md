# DBAutofy

[![Repo](https://img.shields.io/badge/Repo-FatStinkyPanda/DBAutofy-blue)](https://github.com/FatStinkyPanda/DBAutofy)
[![Python 3.11](https://img.shields.io/badge/Python-3.11.x-blue.svg)](https://www.python.org/downloads/release/python-3110/)
[![MCP-Global](https://img.shields.io/badge/Enforced-MCP--Global-red)](./mcp-global)

**DBAutofy** is designed to make it incredibly easy to query databases and tables, and to search and filter data. It provides a visual and automated way to interact with your data sources safely and efficiently.

## 🚀 Core Vision

The primary goal of DBAutofy is to simplify data exploration. Whether you are a developer looking for a specific record or an analyst merging multiple data sources, DBAutofy provides the "Query Building Blocks" (QBB) to get you there without the manual SQL overhead.

## 🛡️ Security First

- **Read-Only by Default**: This project utilizes [Bytebase DBHub](https://github.com/bytebase/dbhub) strictly in **read-only** mode. This ensures that DBAutofy itself never makes destructive changes to your production databases.
- **Manual CRUD Execution**: While DBAutofy can automatically generate the code needed for full CRUD (Create, Read, Update, Delete) operations, it **requires the user to manually execute the code**. This "Human-in-the-loop" approach prevents accidental data loss.
- **DML/DDL Warnings**: Any generated code that performs non-read operations will be explicitly flagged with high-visibility warnings.

## ✨ Key Features

- **Query Building Blocks (QBB)**: 
  - Create, edit, and delete visual blocks that represent query logic.
  - A visual representation of complex SQL queries for easy maintenance.
- **Multi-Source Data Aggregation**:
  - Pull data from multiple disparate sources simultaneously.
  - Perform read-only merges of tables across different databases.
- **Intelligent Query Analysis**:
  - Estimated query time detection.
  - High-cost query identification.
  - Automatic warnings for long-running processes or high-cost operations.
- **Automated CRUD Logic Generation**:
  - Automatically write the boilerplate for data mutations.
  - Full support for Create, Update, and Delete logic (external execution required).

## 🛠️ Development Requirements

### Python 3.11.x
This project **must** be developed and run within a **Python 3.11.x** virtual environment. This version constraint is strictly enforced to ensure consistent behavior throughout the project lifecycle.

```bash
# Example VENV setup
python -m venv venv
source venv/bin/activate  # On Windows: .\venv\Scripts\activate
pip install -r requirements.txt
```

### MCP-Global Enforcement
The **mcp-global** system is deeply integrated into this project.
- **Location**: `./mcp-global`
- **Enforcement**: Git hooks are used to ensure that all development follows the predefined rules and quality gates.
- **NO BYPASS**: Bypassing these hooks or the `mcp-global` system is strictly prohibited.

## 📈 Development Workflow

- **Continuous Integration**: All changes must be committed and pushed frequently to the [main repository](https://github.com/FatStinkyPanda/DBAutofy).
- **Tooling**: Always utilize the `mcp.py` tools for context, review, and security audits before pushing.

---

*DBAutofy - Empowering data exploration with safety and intelligence.*
