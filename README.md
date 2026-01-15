# DBAutofy

[![Repo](https://img.shields.io/badge/Repo-FatStinkyPanda/DBAutofy-blue)](https://github.com/FatStinkyPanda/DBAutofy)
[![Python 3.11](https://img.shields.io/badge/Python-3.11.x-blue.svg)](https://www.python.org/downloads/release/python-3110/)
[![MCP-Global](https://img.shields.io/badge/Enforced-MCP--Global-red)](./mcp-global)

**DBAutofy** is a world-class, extremely powerful, and intelligent all-in-one solution for database management and querying. It is designed to make it incredibly easy to interact with complex data systems, providing a unified gateway for single and multi-database operations.

## 🚀 Core Vision

The mission of DBAutofy is to be the ultimate source of truth for your data exploration. It replaces fragmented workflows with a powerful "Query Building Block" (QBB) system, allowing users to build, manage, and scale their database interactions with unprecedented ease and intelligence.

## 🛡️ Multi-Layered Security

DBAutofy is built with safety as its foundation, ensuring that databases remain protected against both accidental damage and malicious intent.

- **Read-Only by Default**: This project utilizes [Bytebase DBHub](https://github.com/bytebase/dbhub) strictly in **read-only** mode for all exploration activities.
- **Data Integrity Safeguards**: Multiple layers of checks ensure that databases cannot be irreversibly damaged or changed incorrectly with wrong data.
- **Intelligent SQL Injection Protection**:
    - **Proactive Safeguards**: Built-in mechanisms that intelligently scan and neutralize potential SQL injection vectors.
    - **Safe-by-Design**: Usage of parameterized queries and strict input validation layers to ensure no wrongful SQL execution can occur.
- **Manual CRUD Execution**: While DBAutofy generates world-class code for full CRUD (Create, Read, Update, Delete) operations, it **requires the user to manually execute the code**. This "Human-in-the-loop" approach prevents unintended data mutations.
- **Non-Read Warnings**: Any generated code for data modification is explicitly flagged with high-visibility security warnings.

## ✨ Extremely Powerful Query Systems

DBAutofy supports any and all query tools, systems, and methods possible, providing an exhaustive toolkit for data manipulation:

- **Query Building Blocks (QBB)**: 
    - A visual representation of complex logic that makes query creation, editing, and deletion highly intuitive.
- **Advanced Query Types**:
    - **Calculated Fields**: Real-time computation of values within your query results.
    - **Concatenated Data**: Intelligent string manipulation and data joining.
    - **Complex Merging**: Read-only merging of tables and data streams from multiple sources at once.
- **Intelligent Query Analysis**:
    - World-class detection of estimated query time.
    - Detection of high-cost queries with proactive user warnings to prevent long-running processes or excessive costs.
- **Automated CRUD Logic Generation**:
    - Automatically generates highly optimized boilerplate for data mutations (external execution required).

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
