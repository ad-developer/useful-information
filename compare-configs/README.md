# 🧩 Compare Configs — `appsettings.json` vs `values.yaml`

A command-line tool to compare configuration variables between a JSON app configuration (like `appsettings.json`) and a YAML Helm-style file (with variables under a `values:` section).  
It ensures that all variables are aligned and reports missing or mismatched ones.

---

## 🚀 Features

- Compares deeply nested JSON and YAML configurations.  
- Handles naming differences automatically:  
  - JSON:  
    ```json
    { "levelone": { "leveltwo": 333 } }
    ```
  - YAML:  
    ```yaml
    values: 
      levelone__leveltwo: 333
    ```
- Reports:
  - Missing keys in either file.
  - Mismatched values.
- Supports both **remote Git repositories** and **local files**.
- Auto-updates repositories if already cloned.

---

## Example usage


```
bash

python compare_configs.py \
    --json-repo https://github.com/org/app-configs.git \
    --json-path config/appsettings.json \
    --yaml-repo https://github.com/org/deploy-values.git \
    --yaml-path charts/app/values.yaml
```