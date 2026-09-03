# ✅ Python + Jupyter Project Setup (Windows)

## 📌 What these commands mean

First create the project folder where you want to store your work, then create the virtual environment inside that folder.

### All Commands in a powershell

```powershell
python -m venv .venv
.venv\Scripts\activate
python -m pip install ipykernel
python -m ipykernel install --user --name=AI_Learnings

New-Item -ItemType Directory -Path "data\raw","data\processed","notebooks","src","outputs" -Force

# touch requirements.txt
New-Item requirements.txt

# To install things from this file
python -m pip install -r requirements.txt

```

### `python -m venv .venv`
- Creates a **virtual environment** in `.venv` folder
- Isolates dependencies per project
- Prevents conflicts between projects

---

### `.venv\Scripts\activate`
- Activates the virtual environment in current terminal
- After activation:
  - `python` → points to this project's Python
  - `pip` → installs packages only in this project

---

### `python -m pip install ipykernel`

Install `ipykernel` inside the virtual environment.

### `python -m ipykernel install --user --name=<project-name>`
- Registers this environment as a **Jupyter kernel**
- Required if:
  - Using Jupyter Notebook/Lab in browser
  - OR kernel not visible in VS Code

---

## ❗ Do you need to run ipykernel every time?

| Scenario | Needed? |
|----------|--------|
| New project | ✅ Yes (once) |
| Same project again | ❌ No |
| Deleted `.venv` / new machine | ✅ Yes |

---

## 🚀 Standard Setup (Do this for EVERY new project)

```shell
# Create project folder and enter it
mkdir PCD_Analysis
cd PCD_Analysis

# Create virtual environment
python -m venv .venv

# Activate virtual environment
.venv\Scripts\activate

# Install notebook kernel support
python -m pip install ipykernel

# Register the environment as a named Jupyter kernel
python -m ipykernel install --user --name=AI_Learnings
```

> Keep the project name and kernel name the same when possible.  
> Example: folder `PCD_Analysis` → kernel `PCD_Analysis`

---

## 🧠 VS Code Workflow (Recommended)

1. Open the **project folder** in VS Code.
2. Install extensions:
   - **Python**
   - **Jupyter**
3. Open Command Palette → **Python: Select Interpreter**
4. Select the interpreter from:
   `.venv\Scripts\python.exe`
5. Create or open an `.ipynb` file.
6. Select the notebook kernel that matches your `.venv` or registered kernel name.

✅ VS Code often auto-detects `.venv`, so the `ipykernel install` step may not always be required.  
✅ If the kernel does not show up, then run:

```shell
python -m ipykernel install --user --name=PCD_Analysis
```

---

## 💻 Daily Workflow

```shell
# Activate environment
.venv\Scripts\activate

# Open VS Code in the current project
code .

# (Optional) Run Jupyter in browser
jupyter lab
```

> If you mainly use notebooks inside **VS Code**, you usually do **not** need to run `jupyter lab`.

---

## 📁 Recommended Project Structure

```text
PCD_Analysis\
  .venv\
  data\
    raw\
    processed\
  notebooks\
  src\
  outputs\
  requirements.txt
  .gitignore
```

Create the folders from **inside** the project folder with:

```powershell
New-Item -ItemType Directory -Path "data\raw","data\processed","notebooks","src","outputs" -Force
```

---

## ✅ Best Practices

### 1. Keep notebooks for exploration, not all logic
- Use notebooks for quick analysis, charts, experiments, and notes.
- Move reusable logic into `.py` files inside `src\`.
- Example:
  - `src\load_data.py`
  - `src\cleaning.py`
  - `src\analysis.py`

### 2. Use relative paths
- Avoid absolute paths like:
  `C:\Users\...\Desktop\data.csv`
- Prefer paths relative to the project root.

### 3. Do not commit `.venv`
- Keep `.venv` inside the project for convenience.
- Add it to `.gitignore`.

### 4. Track dependencies
- Once your environment is stable, save installed packages:

```shell
python -m pip freeze > requirements.txt
```

### 5. Keep raw and processed data separate
- `data\raw` → original source files
- `data\processed` → cleaned / transformed files

### 6. Avoid hidden notebook state
- Restart kernel and run all cells occasionally.
- Make sure the notebook runs top-to-bottom from a clean state.

### 7. Keep one notebook focused on one purpose
- One notebook for exploration
- One notebook for cleaning
- One notebook for reporting / final visuals

### 8. Use clear naming
- Keep folder, kernel, notebook, and output names consistent.
- Prefer:
  - folder: `PCD_Analysis`
  - kernel: `PCD_Analysis`

### 9. Use VS Code as the default workflow
- Prefer selecting the `.venv` interpreter directly in VS Code.
- Use `jupyter lab` only if you specifically want the browser interface.
