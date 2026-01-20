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

First, identify your Mac's processor type:
-   Click the **Apple menu**  in the top-left corner of your screen and select **About This Mac**.
-   If you see **Chip** followed by a name like "Apple M1", you have an **Apple Silicon** Mac.
-   If you see **Processor** followed by a name like "Intel Core i7", you have an **Intel-based** Mac.

**For Apple Silicon Macs (M1, M2, M3, etc.):**
1.  Open the Terminal app.
2.  Download the Anaconda installer for Apple Silicon (arm64).
    ```bash
    # This command downloads a recent version. Check the Anaconda repository for the latest.
    curl -O https://repo.anaconda.com/archive/Anaconda3-2023.09-0-MacOSX-arm64.sh
    ```
3.  Run the installer script.
    ```bash
    bash Anaconda3-2023.09-0-MacOSX-arm64.sh
    ```
4.  Follow the on-screen prompts. It is recommended to accept the default settings.
5.  Close and reopen your terminal for the changes to take effect.

**For Intel-based Macs:**
1.  Open the Terminal app.
2.  Download the Anaconda installer for Intel (x86_64).
    ```bash
    # This command downloads a recent version. Check the Anaconda repository for the latest.
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

This creates an isolated environment for the project's dependencies. **Python 3.9-3.11 is recommended.** The command below uses Python 3.11.

1.  Open a new terminal in VS Code (`Terminal` > `New Terminal`).
2.  Create a new Conda environment named `optimization-env`.
    ```bash
    conda create --name optimization-env python=3.11
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

If you don't have Python installed, download it from the official website. **A version between Python 3.9 and 3.11 is recommended for this project.**

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

### 6. Install a C Compiler (for Numba/Gurobi)

Some packages, like `numba` (via `llvmlite`) and `gurobipy`, need a C compiler to be installed from source. Before installing the Python packages, you must install the appropriate build tools for your operating system.

**On macOS:**
Install the Xcode Command Line Tools by running the following command in your terminal:
```bash
xcode-select --install
```
Follow the on-screen instructions to complete the installation.

**On Windows:**
Install the Microsoft C++ Build Tools, which are part of Visual Studio.
1.  Go to the [Visual Studio downloads page](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2022).
2.  Under the "All downloads" section, find **Build Tools for Visual Studio** and click **Download**.
3.  Run the installer.
4.  In the "Workloads" tab, select **Desktop development with C++** and click **Install**.

**On Linux (Debian/Ubuntu):**
Install the `build-essential` package, which includes the GCC compiler and other necessary tools.
```bash
sudo apt update
sudo apt install build-essential
```

### 7. Install Required Packages

With your virtual environment active and compiler installed, install all necessary packages from `requirements.txt`.

```bash
pip install -r requirements.txt
```

---

## Gurobi License Setup (Academic)

Gurobi requires a license to run. Free, full-featured academic licenses are available for students, researchers, and staff at academic institutions. We follow these steps on each machine where we intend to run the notebooks.

### Finding Your Home Directory (License File Location)

The Gurobi license file (`gurobi.lic`) is always stored in your user's home directory. If you need to find this location, here’s how:

* **On Windows:**
    1.  Open Command Prompt or PowerShell.
    2.  Type `echo %USERPROFILE%` and press Enter. This will print the path (e.g., `C:\Users\YourUsername`).

* **On macOS or Linux:**
    1.  Open a terminal.
    2.  Type `echo $HOME` or `echo ~` and press Enter. This will print the path (e.g., `/Users/YourUsername` or `/home/YourUsername`).

1. Register on the Gurobi Website
    *   Go to the [Gurobi Academic License Page](https://www.gurobi.com/academia/academic-program-and-licenses/).
    *   Register for an account using university or institutional email address. NOTE: we must be connected to the university's network (e.g., on-campus Wi-Fi or through a VPN) for the license to be validated.

2. Request and Activate Your License
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
    *   **Troubleshooting**: If the terminal reports `command not found`, you may need to use the full path to the `grbgetkey` executable. The path depends on your operating system and where you installed Anaconda.
        *   **Windows**: 
            `C:\Users\YourUsername\anaconda3\envs\optimization-env\Scripts\grbgetkey.exe [your_key]`
        *   **macOS**: 
            `/Users/YourUsername/anaconda3/envs\optimization-env/bin/grbgetkey [your_key]`
        *   **Linux**: 
            `/home/YourUsername/anaconda3/envs\optimization-env/bin/grbgetkey [your_key]`
        *(Replace `YourUsername` and `[your_key]` accordingly)*

### 3. Verification

You can verify that your license is installed correctly in a couple of ways:

*   **Check for the license file**: Look for a file named `gurobi.lic` in your user's home directory (see the "Finding Your Home Directory" section above). If this file exists, a license has been installed.
*   **Test with the Gurobi command**: Open a new terminal with your environment activated (`conda activate optimization-env` or `source .venv/bin/activate`). Run the following command:
    ```bash
    gurobi_cl --license
    ```
    If a valid license is found, it will display the license details. If not, it will report that no license was found.

The license is valid for one year and can be renewed for free by following the same process.

---

## Alternative: Gurobi Web License Service (WLS)

If you are using a container, a virtual machine, or have trouble with the standard `grbgetkey` method, you can use Gurobi's Web License Service (WLS). **Note: Just like the standard academic license, WLS requires you to be connected to your university's network (e.g., on-campus Wi-Fi or through a VPN).**

1. Request a WLS License
    *   On the same [Gurobi Academic License Page](https://www.gurobi.com/academia/academic-program-and-licenses/), select the "Web License Service" option instead of the standard academic license.
    *   Gurobi will provide you with a set of credentials (API key, secret, etc.).

2. Create a License File
    *   Create a new file named `gurobi.lic` in your user's home directory. The location depends on your operating system:
        *   **Windows:** The path is usually `C:\Users\YourUsername\`. You can find it by opening Command Prompt and typing `echo %USERPROFILE%`.
        *   **macOS & Linux:** The path is usually `/Users/YourUsername/` or `/home/YourUsername/`. You can find it by opening a terminal and typing `echo $HOME`.
    *   Add the WLS credentials provided by Gurobi to this file. It should look something like this:
        
    *    #### Gurobi Web License Service
        TYPE=WLS
        WLSACCESSID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        WLSSECRET=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
        WLSTOKEN DURATION=...
        
    *   Save the file. Gurobi will now use this license when you are connected to your university network. This method is ideal for virtual machines and containerized environments.

## Running the Notebooks

Once our setup is complete, we can run the notebooks:

1.  Make sure we chosen environment (`optimization-env` or `.venv`) is active in the terminal.
2.  Open any Jupyter Notebook (`.ipynb`) file from this project.
3.  Run cells individually by clicking the **Run** icon, or run the entire notebook by clicking **Run All** at the top.

---

## Recommended VS Code Extensions

To enhance your development experience, we recommend installing the following Visual Studio Code extensions. You can find them by searching in the **Extensions** view (`Ctrl+Shift+X`).

*   **Python** (ms-python.python)
    *   **Publisher**: Microsoft
    *   **Description**: Provides rich support for the Python language, including features like linting, debugging, and code navigation. It also includes the **Pylance** extension, which offers fast and powerful type-checking and autocompletion.

*   **Jupyter** (ms-toolsai.jupyter)
    *   **Publisher**: Microsoft
    *   **Description**: Enables you to work with Jupyter Notebooks (`.ipynb` files) directly within VS Code, offering an interactive and integrated experience.

*   **Black Formatter** (ms-python.black-formatter)
    *   **Publisher**: Microsoft
    *   **Description**: The official extension for the Black code formatter, allowing you to format your Python code automatically on save.

## Code Formatting with Black

To maintain a consistent code style, this project uses the [Black](https://github.com/psf/black) code formatter. It is recommended to configure your editor to use it.

### 1. Install Black

First, install Black into your active Conda or `venv` environment. If you have already installed the packages from `requirements.txt`, you can skip this step as Black is included.
```bash
pip install black
```

### 2. Configure VS Code

You can configure VS Code to automatically format your Python files and Jupyter Notebook cells.

1.  Open the Command Palette (`Ctrl+Shift+P`).
2.  Search for and select **Preferences: Open User Settings (JSON)**.
3.  Add or update the following configuration in your `settings.json` file.
    **Important**: The `settings.json` file uses a strict JSON format. Be careful to place the new settings correctly inside the main curly braces `{}` and add commas between entries if needed. Incorrect formatting can cause your VS Code settings to stop working.

    ```json
    {
        // ... your other settings
        "[python]": {
            "editor.defaultFormatter": "ms-python.black-formatter",
            "editor.formatOnSave": true
        },
        "jupyter.formatOnSave": true,
    }
    ```

**What these settings do:**
*   `"[python]"`: These settings apply specifically to Python files.
*   `"editor.defaultFormatter": "ms-python.black-formatter"`: Sets Black as the default formatter for Python code. VS Code may prompt you to install the Black Formatter extension by Microsoft, which you should do.
*   `"editor.formatOnSave": true`: Automatically formats your `.py` files every time you save.
*   `"jupyter.formatOnSave": true`: Automatically formats code cells in your Jupyter Notebooks (`.ipynb`) when you save the file.

With this setup, your code will be formatted automatically, ensuring consistency across the project.

## Getting and Updating the Project with Git

This project is managed using Git and is hosted on GitHub. To get a local copy of the project and keep it updated, you'll need to use Git.

### 1. Install Git

You have several options for using Git. You only need to choose one.

**Option A: Command-Line Git (Recommended)**
This is the most universal method. Download and install Git from the official website.
-   [Download Git](https://git-scm.com/downloads)
-   On Windows, the installer includes **Git Bash**, which provides a powerful command-line interface.

**Option B: Install with Conda**
If you are using Anaconda, you can install Git directly from the Anaconda repository. This is a convenient way to manage Git within your Conda environments.
1.  Open your terminal or Anaconda Prompt.
2.  Run the following command:
    ```bash
    conda install -c anaconda git
    ```
    *This ensures Git is available when your Conda environment is active.*

**Option C: GitHub Desktop**
If you prefer a graphical user interface (GUI), GitHub Desktop is an excellent choice. It simplifies cloning, committing, and pulling changes.
-   [Download GitHub Desktop](https://desktop.github.com/)

**Option D: Git in VS Code**
Visual Studio Code has built-in support for Git, but it **still requires Git to be installed on your system** (using Option A or B). Once Git is installed, you can use the Source Control view (`Ctrl+Shift+G`) in VS Code to manage your project.

*Note: `pip install git` does not install Git. It installs a Python library for interacting with Git repositories and should not be used for this setup.*

### 2. Create a GitHub Account (Optional)

If you just want to download the files, you don't need an account. However, if you plan to contribute, report issues, or fork the project, you'll need a free GitHub account.

-   [Join GitHub](https://github.com/join)

### 3. Clone the Project (First-Time Setup)

"Cloning" creates a full local copy of the project repository.

**Using the Command Line:**
1.  Open a terminal (or Git Bash on Windows).
2.  Navigate to the directory where you want to store the project.
3.  Run the `git clone` command with the repository's URL.
    ```bash
    # Replace with the actual project repository URL
    git clone https://github.com/user/repository.git
    ```
4.  This creates a new folder containing all the project files.

**Using VS Code:**
1.  Open the Command Palette (`Ctrl+Shift+P`).
2.  Type `Git: Clone` and press Enter.
3.  Paste the repository URL and choose a local directory to save the project.

**Using GitHub Desktop:**
1.  Go to `File` > `Clone Repository`.
2.  Select the `URL` tab, paste the repository URL, and choose a local path.

### 4. Keeping Your Project Updated

To ensure you have the latest version of the project files, you should periodically update your local copy.

**Using the Command Line:**
1.  Open a terminal in the project's root directory.
2.  Run `git pull` to fetch and merge the latest changes.
    ```bash
    git pull origin main
    ```

**Using VS Code:**
1.  Open the Source Control view (`Ctrl+Shift+G`).
2.  Click the `...` menu and select `Pull`.

**Using GitHub Desktop:**
1.  Click the `Fetch origin` button at the top.
2.  If there are new changes, the button will change to `Pull origin`. Click it to update.

This will update your local files with any new commits from the project's repository.
