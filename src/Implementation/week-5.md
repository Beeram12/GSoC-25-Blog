# Week-5

This week, I completed writing all the scripts responsible for creating the CodeQL database and performing the analysis. I also began working on excluding queries that are known to hang or get stuck during execution. I collaborated closely with my mentor to test the functionality of these scripts and we are actively working on improving them. Additionally, my mentor provided some feedback and shared initial results, which I will incorporate to further refine and enhance the scripts.

## Work completed this week

### 1. Scripts
1. Completed the following scripts:

   * `create_db.py`: Handles database creation with different langauges.
   * `sb_check.py` : Checks if CodeQL is available in the system `PATH`.
   * `analyze_db.py` : Handle CodeQL analysis with CSV report generation.
   
2. The GitLab repository [rtems-codeql-toolkit](https://gitlab.rtems.org/Pranith_1316/rtems-codeql-toolkit) is now well-documented:
   * A detailed `README.md` is available explaining how to install, configure, and use each script.
   * Clear instructions and examples are provided to help users understand how the toolkit works and how to get started quickly.

## Future Improvements

Based on the feedback received from Dr. RTEMS, I need to do the following improvements to the project:

1. **README.md Modifications**

   * Updated the `pip install` instructions to include the `--user` flag for better compatibility:

     ```bash
     pip install --user -r requirements.txt
     ```

2. **Script Enhancements**

   * Added a proper shebang (`#!/usr/bin/env python3`) at the top of all Python scripts to allow them to be executed directly.
   * Ensured that all scripts in the `scripts/` directory can be run using `./scripts/<script_name>.py` format by setting appropriate execute permissions.

3. **CodeQL Path and Version Check**
   * Improve the logic to:
     * Detect if CodeQL is already available in the system `PATH`.
     * If present, use the existing CodeQL installation.
     * Verify if the CodeQL version matches the required one before proceeding.

4. **CSV Output Formatting**

   * Enhanced the CSV formatting logic to ensure the output includes a header row.
   * This improves clarity and usability of analysis results for further processing or review.




