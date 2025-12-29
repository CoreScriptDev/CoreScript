# CSX – CoreScript Extension Manager

CSX is the official package manager for **CoreScript**, comparable to `pip` in Python.
It allows developers to install and use modules (extensions) that provide functions, classes, and other reusable code.

---

## Table of Contents
- What is CSX?
- CSX Commands
- Installing Extensions
- Providers
- Using Extensions in Code
- Creating Your Own Extension
- extension.json Reference
- Dependencies
- Security & Runtime
- Current Limitations
- Planned Features

---

## 1. What is CSX?

CSX (CoreScript Extension Manager) is a CLI-based package manager for CoreScript.
Extensions are imported using `using` and behave like native modules.

Key points:
- Only **modules** are supported at the moment
- CLI-only
- Executed via `corescript csx`
- Extensions run in the same runtime as the script
- No sandboxing
- Versioning is planned but not implemented yet

---

## 2. CSX Commands

### Install an extension
```bash
corescript csx install <source>
```

Installs an extension from GitHub, GitLab, or a local path.

---

### List installed extensions
```bash
corescript csx list
```

Lists all installed CSX extensions.

---

### Show extension details
```bash
corescript csx show <extension_name>
```

Displays detailed information about an installed extension  
(author, license, dependencies, etc.).

---

## 3. Installing Extensions

CSX is executed through CoreScript:

```bash
corescript csx install <source>
```

---

### 3.1 Installing from GitHub or GitLab

```bash
corescript csx install <username>/<repository>/<optional_path> -p <provider>
```

**Parameters:**
- `<username>` – Repository owner
- `<repository>` – Repository name
- `<optional_path>` – Path to the extension folder inside the repository  
  (only required if the extension is not in the repository root)
- `-p <provider>` – `github` (default) or `gitlab`

**Example (GitHub, default provider):**
```bash
corescript csx install Nathan/testmodule
```

**Example with subfolder and GitLab:**
```bash
corescript csx install Nathan/libs/mathutils -p gitlab
```

⚠️ The path must point **directly to the folder** containing `extension.json`.

---

### 3.2 Installing from Local Path

```bash
corescript csx install <path/to/extension> -p local
```

**Example:**
```bash
corescript csx install D:/mylang/Repository/CoreScript/testmodule -p local
```

---

## 4. Providers

Currently supported providers:

| Provider | Description |
|--------|-------------|
| github | Default provider |
| gitlab | Alternative Git platform |
| local | Local filesystem |

---

## 5. Using Extensions in Code

After installation, modules can be imported using `using`.

### Standard import
```c
using testmodule;
```

### Import with alias
```c
using testmodule as tm;
```

### Import all symbols
```c
using testmodule as *;
```

(Equivalent to `from module import *` in Python)

---

## 6. Creating Your Own Extension

### 6.1 Folder Structure

```text
testmodule/
├── extension.json
└── testmodule.csc
```

**Rules:**
- Folder name = module name
- The `.csc` file **must have the same name as the folder**
- Only **one `.csc` file per extension** is supported currently

---

## 7. extension.json Reference

Every extension must contain an `extension.json` file.

### Example:
```json
{
  "author": "Nathan",
  "version": "1.0.0",
  "license": "MIT",
  "dependencies": [
    "utils/math@github>=1.0.0"
  ]
}
```

---

### Fields

| Field | Required | Description |
|-----|---------|-------------|
| author | Yes | Extension author |
| version | No | Reserved for future versioning |
| license | No | Default: MIT |
| dependencies | No | List of dependencies |

---

## 8. Dependencies

Dependencies use the following syntax:

```text
pathToDependency@provider==/<=/>=/>/<version
```

### Example:
```json
"dependencies": [
  "mathutils@github>=1.2.0",
  "localhelpers@local"
]
```

⚠️ Version comparison is not implemented yet; the syntax is reserved for future use.

---

## 9. Security & Runtime

- Extensions run in the **same runtime** as the script
- They have **exactly the same permissions**
- There is **no sandbox**

---

## 10. Current Limitations

- No versioning yet
- No update or uninstall commands
- Only modules are supported
- Only one `.csc` file per extension

---

## 11. Planned Features

- Versioning support
- Update system
- Extended dependency resolution
- Additional extension types

---

**CSX – Keep CoreScript modular.**
