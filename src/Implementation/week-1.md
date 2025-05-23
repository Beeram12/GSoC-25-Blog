# Week-1

This week marked the beginning of the GSoC implementation phase.This was all the analysis and setup I did before my GSoC application where I focused on setting up the static analysis framework and laying the foundation for the CodeQL integration with the RTEMS codebase.

## Work-done

1.  ### Installation of CodeQL 
    - By referring to the documentation from CodeQL, I opted for Option 2 to install the CodeQL CLI.                    
    Option 2 focuses on downloading the standalone CodeQL CLI binary from the official GitHub releases page. This method provides:

        -  The CodeQL CLI executable
        -  Minimal setup without the default GitHub query packs
        -  Flexibility to manually install and configure specific query packs
        -  I downloaded the ZIP file `(codeql-linux64.zip)` from ([GitHub CodeQL CLI binary Releases](https://github.com/github/codeql-cli-binaries/releases)), extracted it.

2.  ### Creation of Database
    - After installing the CodeQL CLI, the next step was to generate a CodeQL database from the RTEMS source code.
    - A CodeQL database is a structured representation of the codebase, enabling static analysis through queries.

    #### Database Creation Command:
    ```bash
    codeql database create rtems-codeql-db --language=c --source-root=.
    ```
    - This command initializes a new CodeQL database named `rtems-codeql-db`.

3.  ### Analyze the Database 
    - Once the CodeQL database was successfully generated, the next step was to analyze it using specific Coding Standard rules.

    #### Running the Analysis:
    - Use the following command to analyze the database with one or more Coding Standards:
    ```bash
    codeql database analyze rtems-codeql-db --format=sarif-latest --output=codeql-report.sarif
    ```
    - The results are saved in a [SARIF](https://sarifweb.azurewebsites.net/) file, which is a standardized format for static analysis results, and can be visualized using compatible tools.

## Future Improvements from discussions

1.  Install `option 1` method for installing CodeQL CLI and also include C standard packs like MISRA,CERT-C. 
2.  Make plan for RSB reciepe creation.  



