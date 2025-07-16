
# Week-6

This week, my CodeQL toolkit was tested by Gedare, who provided valuable feedback on both the tool and the documentation. Based on his review, I made several improvements to the `README.md` and adjusted some script behaviors to improve usability and clarity. I also defined my initial milestones for the upcoming midterm evaluation.

## Work completed this week

### 1. README & Tool Improvements

* Incorporated feedback from Gedare to improve the overall structure, clarity, and technical accuracy of the documentation.
* Enhanced command execution steps with better examples and platform-specific notes.
* Added missing `.py` extensions to command examples (`./create_db.py`, `./analyze_db.py`).
* Addressed missing file and directory handling issues, such as the pre-creation of the `reports/` directory before CSV generation.
* Corrected misleading references (e.g., incorrect `.qls` file paths).
* Ran a spell check and fixed typos throughout the `README.md`.
* Clarified assumptions around `$HOME`, `config.ini`, and build script locations.
* Explained the CodeQL installation better added documentation and noted potential path conflicts.

### 2. CSV output formatting
- Added proper headers to the CSV file for improved readability and analysis. The output now includes the following fields:
| Property     | Description                                                 | Example                                                                                     |
  | ------------ | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
  | Name         | Name of the query that identified the result.               | Inefficient regular expression                                                              |
  | Description  | Description of the query.                                   | A regular expression that requires exponential time to match certain inputs can be a performance bottleneck, and may be vulnerable to denial-of-service attacks. |
  | Severity     | Severity of the query.                                      | error                                                                                       |
  | Message      | Alert message.                                              | This part of the regular expression may cause exponential backtracking on strings containing many repetitions of '\\'.                                                |
  | Path         | Path of the file containing the alert.                      | /vendor/codemirror/markdown.js                                                              |
  | Start line   | Line of the file where the code that triggered the alert begins.                                | 617                                                                                         |
  | Start column |Column of the start line that marks the start of the alert code. Not included when equal to 1.                   | 32                                                                                          |
  | End line     | Line of the file where the code that triggered the alert ends. Not included when the same value as the start line. | 64                                                                                          |
  | End column   | Where available, the column of the end line that marks the end of the alert code. Otherwise the end line is repeated.          | 617                                                                                         |
    
### 3. Midterm Planning

* Set clear and achievable milestones for the midterm evaluation.


## Summary of Gedare’s Review Highlights

* Add explicit instructions for installing CodeQL.
* Avoid assumptions about file paths being under `$HOME`; improve relocatability.
* Support Python virtual environments more clearly.
* Improve cross-platform instructions and test beyond Linux.
* Ensure all script calls include `.py` extension.
* Explain use of `config.ini` and clarify build script expectations.
* Fix typos and formatting in `README.md`.
* Address errors related to missing report directory and invalid file paths.


