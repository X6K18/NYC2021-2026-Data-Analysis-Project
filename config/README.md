# ⚙️ Config Directory

This directory contains configuration files for the project, including database credentials, API keys, and global parameters.

## 📂 Structure

- `config.yaml` / `settings.json`: Main configuration file for environment variables and file paths.
- `db_credentials.example.yaml`: A template for database connection strings (Host, Port, User).
- `constants.py`: Fixed values used across the project (e.g., color palettes for BI, category mapping).

## 🔐 Security Policy (Crucial)

**NEVER commit real credentials to Version Control.**

1.  **Gitignore**: The actual `config.yaml` or `.env` files are listed in `.gitignore` to prevent them from being pushed to GitHub/GitLab.
2.  **Templates**: Only `.example` or `.template` files are tracked. When setting up the project for the first time, copy the example file and fill in your actual credentials:
    ```bash
    cp config/db_credentials.example.yaml config/db_credentials.yaml
    ```

## 🛠 Usage in Python

To load configurations safely within your scripts:

```python
import yaml

with open("config/config.yaml", "r") as f:
    config = yaml.safe_load(f)

db_host = config['database']['host']