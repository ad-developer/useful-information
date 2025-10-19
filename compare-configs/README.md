# Config Comparison Tool

A Python command-line tool that compares variables between an `appsettings.json` file and a `values.yaml` file.  
It supports both **local files** and **Git repositories**, and does **not require any external libraries** (no PyYAML dependency).

---

## Features

- Compare JSON and YAML variables, matching keys like:
  - JSON:  
    ```json
    {
      "Database": { "Host": "db.local", "Port": 5432 }
    }
    ```
  - YAML:  
    ```yaml
    values:
      Database__Host: db.local
      Database__Port: 5432
    ```
- Works with **local files** or **repositories** (auto-clones temporary copy)
- Configurable YAML section name (e.g., `values`, `group_one.group_two`)
- Detects:
  - Keys missing in either file
  - Value mismatches
- Pure Python — no third-party dependencies

---

## Requirements

- Python 3.7+
- Git command-line installed (if comparing from repositories)

---

## Installation

Clone or copy this repository and make the script executable:

```bash
chmod +x compare_configs.py
```

---

## Usage

### 1. Compare **local files**

```bash
python compare_configs.py   --json-local ./repoA/appsettings.json   --yaml-local ./repoB/values.yaml   --yaml-values-key values
```

### 2. Compare files from **repositories**

```bash
python compare_configs.py   --json-repo https://github.com/example/app-repo.git   --yaml-repo https://github.com/example/config-repo.git   --json-path config/appsettings.json   --yaml-path helm/values.yaml   --yaml-values-key values.group_one
```

### 3. Custom Branch

```bash
python compare_configs.py   --json-repo https://github.com/example/app-repo.git   --yaml-repo https://github.com/example/config-repo.git   --branch develop
```

---

## Command Line Options

| Argument | Description | Default |
|-----------|--------------|----------|
| `--json-repo` | Git repository URL containing `appsettings.json` | — |
| `--yaml-repo` | Git repository URL containing `values.yaml` | — |
| `--json-path` | Path to JSON file inside the repo | `appsettings.json` |
| `--yaml-path` | Path to YAML file inside the repo | `values.yaml` |
| `--json-local` | Local path to JSON file (overrides repo) | — |
| `--yaml-local` | Local path to YAML file (overrides repo) | — |
| `--yaml-values-key` | YAML section name (e.g. `values` or `group_one.group_two`) | `values` |
| `--branch` | Branch to use when cloning repos | `main` |

---

## Example Output

```
🔍 Comparison Results:

❌ Keys only in JSON:
  - Database__User: admin

❌ Keys only in YAML:
  - Api__BaseUrl: https://api.example.com

⚠️ Keys with mismatched values:
  - Cache__Enabled: JSON=True, YAML=False
```

If all variables match:

```
✅ All keys and values match!
```

---

## Internals

- YAML parsing is done using a **minimal custom parser** (no `PyYAML` dependency).
- Nested sections and values are flattened using the `__` separator.
- Works in both **local** and **remote** repo contexts.

---