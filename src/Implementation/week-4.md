# Week-4

During Week-4, we finalized my midterm deliverables after discussions with my mentor, focusing on building a reproducible CodeQL workflow tailored for RTEMS. The primary goal is to automate the entire setup process so that others can easily replicate the analysis steps without manual intervention. To achieve this, I started writing a series of scripts that handle tasks such as downloading, unzipping, and setting up the CodeQL CLI. We also discussed implementing directory exclusion rules to ensure irrelevant files are filtered out during database creation. As of now, the installation and unzipping stages of the automation have been completed successfully, marking steady progress toward the midterm milestone.


## Work completed this week

### 1. Finalaze mid-term delvirable  
1. A standalone GitHub repository containing:
    - Set up scripts and config files for running CodeQL on `RTEMS`.
    - `.qls` files for selected rule sets.
    - `.qls` files focusing on excluding directories accordingly.
    - Sample output reports (CSV / SARIF).
    - Clear `README` instructions to replicate the setup manually.
2. A working demo showing:
    - Cloning the toolkit.
    - Running CodeQL and viewing actionable issues with line-level details.
3. (Optional) Draft design for CI integration in the future.
4. Toolkit structure
    ```
    rtems-codeql-toolkit/
	├── bin/               # CodeQL binaries (auto-downloaded)
	├── config/            # Pre-configured exclusion profiles
	├── reports/           # Analysis outputs
	├── scripts/           # Automation scripts
	│   ├── setup          # Installation script
	│   ├── sb-check       # Environment validator
	│   └── analyze        # Main analysis driver
	└── README.md          # User guide
    ```
    No mixing with RTEMS source files
5. Directory Exclusion Strategy:The following [documentation](https://docs.github.com/en/code-security/code-scanning/creating-an-advanced-setup-for-code-scanning/customizing-your-advanced-setup-for-code-scanning#uploading-code-scanning-data-to-github) has been reffered for directory exclusion.

### 2. Scripts
- This week, I completed the scripts used for installing the CodeQL CLI bundle and unzipping it. A progress bar has also been integrated to give users clear visual feedback during the installation process.
- The script  detects the user's operating system and installs the appropriate bundle accordingly..
- If an older version of the bundle is already present, it gets automatically removed, and the new version is installed by simply updating the version number in the script.
- The installed CodeQL bundle is placed inside the `bin` directory for consistent and organized access.

## Future Improvements
- I will write scripts that check whether `codeql` is already available in the system's `PATH`. If not, the script will guide the user to install or link it correctly.
- I will also implement scripts to create a CodeQL database and run analysis using predefined or custom query packs, ensuring the process is smooth and fully automated.
