# Week-2

This week, I focused on practical integration and experimentation with CodeQL, including an upgrade from the previous version and well-classified documentation. I started using the CodeQL CLI bundle to generate databases and run queries across multiple languages, i.e., C, C++, and Python. The goal was to explore CodeQL's ability to enforce secure coding standards like MISRA C, Common C, and detect low-level vulnerabilities early in embedded systems development.

Alongside CodeQL work, I also began exploring the RTEMS Source Builder (RSB) to understand how toolchains are configured and managed for RTEMS targets.

## Work completed this week

### 1. Installation of `CodeQL CLI` bundle  
1. Download the `.tar.gz` file from the codeql [release-page](https://github.com/github/codeql-action/releases):
    - Here I am using CodeQL CLI bundle, which includes both the CodeQL CLI and GitHub's default security queries.I selected `codeql-bundle-linux64.tar.gz` because I was using linux-ubuntu.
    - Also you can install simlarly using the below link:
    ```
    wget https://github.com/github/codeql-action/releases/download/codeql-bundle-v2.21.3/codeql-bundle-linux64.tar.gz
    ```
     > The version I used here is `v2.21.3`.
    
2. Extract the `tarball` downloaded:
    ```
    mkdir -p ~/codeql
    tar -xzvf codeql-bundle-linux64.tar.gz -C ~/codeql
    ```
3. Add `codeql` to `PATH`:
    ```
    echo 'export PATH="$HOME/codeql/codeql:$PATH"' >> ~/.bashrc
    source ~/.bashrc
    ```
4. Verify if `codeql` is intalled:
    ```
    codeql --version  # Should show the CLI version .
    ```
### 2. Installation of `C/CPP` Query-packages
1. To install codeql packages that include:
    - `misra-c-coding-standards`
    - `cert-c-coding-standards`
    - `misra-cpp-coding-standards`
    - `cert-cpp-coding-standards`
    - `autosar-cpp-coding-standards`
    - `common-c-coding-standards`
    - `common-cpp-coding-standards`
Run the following command:
    ```
    codeql pack download codeql/misra-c-coding-standards
    codeql pack download codeql/cert-c-coding-standards
    codeql pack download codeql/misra-cpp-coding-standards
    codeql pack download codeql/cert-cpp-coding-standards
    codeql pack download codeql/autosar-cpp-coding-standards
    codeql pack download codeql/common-c-coding-standards
    codeql pack download codeql/common-cpp-coding-standards
    ```
2. To verify the location of installation:
    ```
    ~$ ls .codeql/packages/codeql/
    ```
    > Versions of each package installed are
            1. autosar-cpp-coding-standards ⇒ 2.45.0
            2. cert-cpp-coding-standards ⇒ 2.45.0
            3. common-cpp-coding-standards ⇒ 2.45.0
            4. misra-cpp-coding-standards ⇒ 2.45.0
            5. cert-c-coding-standards ⇒ 2.45.0

### 3. Creating Database for RTEMS
1. For creating a database for mulutiple langauges and other flags I reffred to this [documentation](https://docs.github.com/en/code-security/codeql-cli/getting-started-with-the-codeql-cli/preparing-your-code-for-codeql-analysis).To build the database for `RTEMS` codebase use the command
    ```
    codeql database create rtems-db \
    --db-cluster \
    --language python,c-cpp \
    --command "./build.sh" \
    --no-run-unnecessary-builds \
    --source-root .
    ```
> The `build.sh` script is a helper file that automates the **clean** and **build** process for the RTEMS codebase:

```bash
#!/bin/bash
./waf clean && ./waf build
```
This script ensures the workspace is cleaned before each build, which helps avoid inconsistencies due to leftover artifacts.
-  Here I am creating a database for 3 languages i.e Python,C,CPP.
-  Make sure you are under `RTEMS` codebase while creation.

### 4. Analyzing the Database
1. For the analysis of database I reffered this [documentation](https://docs.github.com/en/code-security/codeql-cli/codeql-cli-manual/database-analyze#options-to-control-ram-usage).
2. We can use the below command to analyse the codebase

    - **For MISRA C:**
        ```
        codeql database analyze rtems-db/cpp \
          --format=sarifv2.1.0 \
          --output=misra-c-results.sarif \
          codeql/misra-c-coding-standards@2.45.0 \
          --ram= "can be set as your wish"\
          --threads= "can be set as your wish"
        ```
    - **For CERT C:**
        ```
        codeql database analyze rtems-db/cpp \
          --format=sarifv2.1.0 \
          --output=cert-c-results.sarif \
          codeql/cert-c-coding-standards@2.45.0\
          --ram= "can be set as your wish"\
          --threads= "can be set as your wish"\
         ```
    - **For MISRA C++:**
        ```
        codeql database analyze rtems-db/cpp \
          --format=sarifv2.1.0 \
          --output=misra-cpp-results.sarif \
          codeql/misra-cpp-coding-standards@2.45.0\
          --ram= "can be set as your wish"\
          --threads= "can be set as your wish"\
        ```
    - **Generate Report for Python**
        ```
        codeql database analyze rtems-db/python \
          --format=sarifv2.1.0 \
          --output=python-security-results.sarif \
          codeql/python-queries  # Default security queries
        ```
3. The output generated is in `sarif` format.



