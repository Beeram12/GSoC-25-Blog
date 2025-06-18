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

