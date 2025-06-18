# Week-3

During the third week, I collaborated closely with Dr. RTEMS to reproduce the CodeQL setup and workflow on his system using the documentation I had prepared. This joint debugging effort helped us pinpoint specific issues in the CodeQL analysis process. While attempting to integrate CodeQL with the RTEMS Source Builder (RSB), we faced configuration and compatibility challenges, leading to a revised understanding of the mid-term deliverables based on feasibility and project priorities. Additionally, Dr. RTEMS encountered issues visualizing SARIF report outputs due to toolchain limitations, so we decided to shift to the CSV format for CodeQL query results to ensure better compatibility and easier processing going forward.


## Work completed this week

### 1. Exclude Queries  
1. To exclude a query create a directory `codeql` and add the following details as `restricted-cert.qls` file.
    ```
    - qlpack: codeql/cert-cpp-coding-standards
        version: 2.46.0
    - exclude:
        id:
          - cpp/cert/interleaved-input-output-without-position
    ```
    > Mention id in the given format `langauge/query-rule/query-name-in-small` 
    
    and run the file i.e use 
    ```
    codeql database analyze rtems-db/cpp \
        --format=sarifv2.1.0 \
        --output=misra-cpp-results.sarif \
        --ram=8000 \
        --threads=4 \
        codeql/cpp-misra-restricted.qls  # Use your custom suite here 
    ```
    then you will be able to get the report.

2. Generate output using CSV format.
    ```
    codeql database analyze rtems-db/cpp \
        --format=csv \
        --output=restricted-cpp-results.csv \
        --ram=8000 \
        --threads=4 \
        codeql/cpp-misra-restricted.qls  # Use your custom suite here
    ```
3. Discussed on grouping all the queries in batches which can be used in CI later.

## Future Improvements
1. Since our attempt to use the RTEMS Source Builder (RSB) for CodeQL integration did not go as planned, I had a detailed discussion with my mentor Dr. RTEMS regarding alternative approaches.
2. We concluded that a more practical and reproducible solution would be to write dedicated scripts for each step of the CodeQL workflow — including database creation, analysis, and result handling.
3. These scripts will serve as a reusable automation toolkit that others in the RTEMS community can easily run and replicate.
4. This scripting-based setup will form the basis of my midterm deliverable, effectively becoming an alpha integration package for CodeQL with RTEMS.
    