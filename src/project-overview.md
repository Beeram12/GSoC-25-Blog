# Project-Overview

## Project Abstract
The project aims to integrate **CodeQL** into the **RTEMS** workflow by configuring it for source code analysis, generating reports on security and coding issues,and allowing rule customization. Additionally, it will develop a standalone tool for local static analysis, ensuring repeatability and future integration into RTEMS CI.

## Project Description
RTEMS currently lacks a robust static analysis tool integrated into its development workflow.While tools like Coverity exist, they are not fully customizable or locally executable. CodeQL offers flexibility, customizability, and the ability to run locally, making it a strong candidate for adoption.

Static analysis tools help identify potential bugs, security vulnerabilities, and coding
standard violations early in the development process. CodeQL's query-based approach
allows developers to define custom rules tailored to RTEMS-specific requirements. The
current RTEMS workflow relies on external platforms like GitLab CI for running CodeQL,
generating reports, and manually modifying the source code based on findings. This creates
dependencies on third-party tools, limits local development flexibility, and requires manual
effort in reviewing and fixing issues.

Integrating CodeQL locally eliminates dependencies on external CI platforms like GitLab by
enabling developers to run static analysis directly on their machines before committing
changes. CodeQL’s query-based approach allows the creation of custom rules tailored to
RTEMS-specific requirements, such as ignoring irrelevant files, directories, or rules, ensuring
only meaningful checks are enforced. Automated report generation provides clear,
structured insights, reducing manual review efforts and improving efficiency. A standalone
tool will be developed to streamline local CodeQL execution, complemented by an RTEMS
Source Builder (RSB) recipe to automate installation and configuration. This setup ensures
repeatability, minimizes noise through customizable filters and includes documentation and
a tutorial to guide future contributors. The solution is designed modularly to support
eventual CI integration while prioritizing local developer experience and alignment with
RTEMS coding standards.

## Project Deliverables
-   June 2 (Coding Begins)
    - Finalize RSB recipe for CodeQL installation
        1.  Test the RSB recipe in a fresh environment to ensure it installs CodeQL
            and all dependencies without errors.
        2.  Ensure that the installed CodeQL version matches the expected latest
            version. Automate version fetching if possible.
        3.  Ensure that missing dependencies or incorrect paths do not break the
            installation
    - Validate local CodeQL execution on RTEMS codebase  
        1.  Confirm the successful creation of the CodeQL database for the RTEMS
            codebase
        2.  Run queries on the database to verify the correct execution

-   July 14-18 (Midterm Evaluation)
    - Successfully running CodeQL setup on RTEMS codebase
        1.  Ensure CodeQL executes correctly on the RTEMS codebase, generating
            meaningful analysis reports
    - RSB recipe, which installs and configures CodeQL setup
        1.  Ensure the recipe installs the latest compatible version of CodeQL and
            its dependencies
    - Initial Analysis Reports with Noise Filtering
        1.  Generate initial reports, focusing on filtering out unnecessary noise.
        2.  Implement exclusions for generated files and third-party code.
        3.  Provide a mechanism for developers to analyze only selected files. 

-   August 25-September 1 (Final Evaluation)   
    - Fully functional CodeQL integration with RSB recipe
        1.  Noise filtering is fully tuned to ensure only meaningful issues are
            flagged, reducing unnecessary warnings for developers.
        2.  Custom CodeQL queries are developed for RTEMS-specific patterns and
            coding guidelines if necessary.
        3.  The entire setup is finalized and ready for use.
    - Scripts for automated report generation and comparison
        1.  Implement scripts for generating reports and tracking issues over time
        2.  Enable automated comparison of analysis results to detect new or
            resolved issues efficiently.
    
-   Post GSoC
    - If interested in adding new features, I am ready to implement or guide new members (eg, Running     Codeql periodically and emailing everyone who committed if the number of issues goes up)
    - If interested in integrating with CI/CD pipelines, work with it.
