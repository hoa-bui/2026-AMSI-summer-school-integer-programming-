# Optimisation Modeling with Python

This guide provides two methods for setting up your environment:
1.  **Using Anaconda (Recommended)**: A comprehensive solution that simplifies package management for scientific computing.
2.  **Using Python's `venv`**: A lightweight alternative for users who prefer to manage their Python installation manually.

---

## Method 1: Setup with Anaconda (Recommended)

This is the most straightforward method for scientific computing in Python.

### 1. Install Visual Studio Code

If you don't have it already, download and install VS Code from the official website:

-   [Download Visual Studio Code](https://code.visualstudio.com/download)

### 2. Install Anaconda (includes Python, Conda, and Pip)

**Option A: Graphical Installer (Easiest)**
-   Go to the [Anaconda Distribution](https://www.anaconda.com/products/distribution) website.
-   Download the installer for your operating system and follow the on-screen instructions.

**Option B: From the Terminal**

Choose the instructions for your operating system.

**On macOS:**
1.  Open the Terminal app.
2.  Download the latest Anaconda installer script using `curl`. You can find the latest version on the [Anaconda repository](https://repo.anaconda.com/archive/).
    ```bash
    # Replace with the latest version for macOS if needed
    curl -O https://repo.anaconda.com/archive/Anaconda3-2023.09-0-MacOSX-x86_64.sh
    ```
3.  Run the installer script.
    ```bash
    bash Anaconda3-2023.09-0-MacOSX-x86_64.sh
    ```
4.  Follow the on-screen prompts. It is recommended to accept the default settings.
5.  Close and reopen your terminal for the changes to take effect.

**On Linux:**
1.  Open your terminal.
2.  Download the latest Anaconda installer script using `wget`.
    ```bash
    # Replace with the latest version for Linux if needed
    wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
    ```
3.  Run the installer script.
    ```bash
    bash Anaconda3-2023.09-0-Linux-x86_64.sh
    ```
4.  Follow the on-screen prompts and accept the default settings.
5.  Close and reopen your terminal.

**On Windows (using PowerShell):**
1.  Open PowerShell (you can search for it in the Start Menu).
2.  Download the installer using `Invoke-WebRequest`.
    ```powershell
    # Replace with the latest version for Windows if needed
    Invoke-WebRequest -Uri "https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Windows-x86_64.exe" -OutFile "Anaconda-Installer.exe"
    ```
3.  Run the installer from the terminal. The `/S` flag runs a silent installation with default settings.
    ```powershell
    Start-Process -Wait -FilePath ".\Anaconda-Installer.exe" -ArgumentList "/S", "/D=$env:UserProfile\anaconda3"
    ```
    *Note: This installs Anaconda to the default location (`C:\Users\YourUsername\anaconda3`). Administrator access is **not** required for this command as it installs for the current user only.*
4.  Close and reopen PowerShell for the changes to take effect.

### 3. Install the Jupyter Extension in VS Code

1.  Open VS Code.
2.  Go to the **Extensions** view (`Ctrl+Shift+X`).
3.  Search for `Jupyter` and install the extension provided by Microsoft.

### 4. Create and Activate a Conda Environment

This creates an isolated environment for the project's dependencies.

1.  Open a new terminal in VS Code (`Terminal` > `New Terminal`).
2.  Create a new Conda environment named `optimization-env`.
    ```bash
    conda create --name optimization-env python=3.10
    ```
3.  Activate the new environment.
    ```bash
    conda activate optimization-env
    ```
    Your terminal prompt should now be prefixed with `(optimization-env)`.

### 5. Select the Conda Environment in VS Code

1.  Open any Jupyter Notebook (`.ipynb`) file from this project.
2.  Click on the **Select Kernel** button in the top-right corner.
3.  From the list, select the Python interpreter associated with `('optimization-env': conda)`.

### 6. Install Required Packages

With your Conda environment active, install all necessary packages from `requirements.txt`.

```bash
pip install -r requirements.txt
```

---

## Method 2: Alternative Setup with `venv` (Manual)

Use this method if you prefer not to use Anaconda.

### 1. Install Python

If you don't have Python installed, download it from the official website. Version 3.8 or newer is recommended.

-   [Download Python](https://www.python.org/downloads/)
-   **Important**: On Windows, make sure to check the box that says **"Add Python to PATH"** during installation.

### 2. Install Visual Studio Code

-   [Download Visual Studio Code](https://code.visualstudio.com/download)

### 3. Install the Jupyter and Python Extensions in VS Code

1.  Open VS Code.
2.  Go to the **Extensions** view (`Ctrl+Shift+X`).
3.  Search for and install the `Python` extension (by Microsoft).
4.  Search for and install the `Jupyter` extension (by Microsoft).

### 4. Create and Activate a Virtual Environment

This creates a lightweight, isolated environment using Python's built-in `venv` module.

1.  Open a new terminal in VS Code.
2.  Navigate to your project's root directory.
3.  Create a virtual environment. We'll name the folder `.venv`.
    ```bash
    # On macOS/Linux
    python3 -m venv .venv

    # On Windows
    python -m venv .venv
    ```
4.  Activate the environment.
    ```bash
    # On macOS/Linux
    source .venv/bin/activate

    # On Windows
    .venv\Scripts\activate
    ```
    Your terminal prompt should now be prefixed with `(.venv)`.

### 5. Select the Virtual Environment in VS Code

1.  Open any Jupyter Notebook (`.ipynb`) file from this project.
2.  Click on the **Select Kernel** button in the top-right corner.
3.  From the list, select the Python interpreter located in your `.venv` folder.

### 6. Install Required Packages

With your virtual environment active, install all necessary packages from `requirements.txt`.

```bash
pip install -r requirements.txt
```

---

## Gurobi License Setup (Academic)

Gurobi requires a license to run. Free, full-featured academic licenses are available for students, researchers, and staff at academic institutions. We follow these steps on each machine where we intend to run the notebooks.

1.  **Register on the Gurobi Website**
    *   Go to the [Gurobi Academic License Page](https://www.gurobi.com/academia/academic-program-and-licenses/).
    *   Register for an account using university or institutional email address. NOTE: we must be connected to the university's network (e.g., on-campus Wi-Fi or through a VPN) for the license to be validated.

2.  **Request and Activate Your License**
    *   Once registered and logged in, navigate to the academic license page. We will see a `grbgetkey` command that includes a personal license key. It will look like this:
        ```bash
        grbgetkey xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        ```
    *   Open a new terminal (or PowerShell on Windows).
    *   **Important**: Make sure Conda or `venv` environment is **active** first.
        ```bash
        # If using Conda
        conda activate optimization-env

        # If using venv
        source .venv/bin/activate
        ```
    *   Paste the `grbgetkey` command we received from the Gurobi website into the terminal and press Enter.

3.  **Verification**
    *   The command will connect to the Gurobi servers and automatically install a license file (`gurobi.lic`) in the default location on the machine (usually our user's home directory).
    *   We only need to do this once per machine. The license is valid for one year and can be renewed for free by following the same process.

---

## Running the Notebooks

Once our setup is complete, we can run the notebooks:

1.  Make sure we chosen environment (`optimization-env` or `.venv`) is active in the terminal.
2.  Open any `.ipynb` file in VS Code.
3.  Run cells individually by clicking the **Run** icon, or run the entire notebook by clicking **Run All** at the top.

---

## Keeping Your Project Updated with Git

To ensure you have the latest version of the project files, you should periodically pull changes from the remote repository.

1.  Open a terminal (or Git Bash on Windows).
2.  Navigate to the project's root directory.
3.  Run the following command to fetch and merge changes from the main branch:
    ```bash
    git pull origin main
    ```
This will update your local files with any new commits from the project's repository.
