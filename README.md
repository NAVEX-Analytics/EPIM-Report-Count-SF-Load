# EPIM Report Count Load

## Summary 
To be run monthly. Extracts Raw Benchmarking Files from MFT and adds monthly running counts to fields on EthicsPoint App Configs. This R script automates the retrieval of compressed benchmark case files from an SFTP server, their extraction and cleaning, and the synchronization of reporting statistics with Salesforce platform configurations.

## Features 
- File Handling and Extraction
  - Uses 7-Zip to extract password-protected ZIP files.
  - Verifies 7-Zip is in the system PATH.
- Data Cleaning and Merging
  - Reads and cleans US and EU benchmark case files.
  - Merges data from both regions into a single data frame.
  - Standardizes date formats and adds region identifiers.
- Salesforce Authentication and Querying
  - Authenticates with Salesforce using credentials from the secrets file.
  - Queries platform configuration records for relevant clients.
- Reporting Metrics Calculation
  - Calculates the number of reports per client for the previous month.
  - Updates Salesforce fields with the latest report counts.
- Chunked Salesforce Updates
 - Supports updating Salesforce records in chunks to avoid API limits.
  - Provides progress feedback during updates.
- Error Handling and Logging
  - Checks for missing files and invalid paths.
  - Logs progress and errors during file processing and Salesforce updates.
 
## Prerequisites 
- `library(salesforcer)`
- `library(tidyverse)`
- `library(sftp)`
- `library(tools)`

## Usage 
Requires 7zip to be added to R Path for system-level commands [(guide)](https://stackoverflow.com/questions/55591191/extract-files-from-password-protected-zip-folder-in-r)

Field names:

![image](https://github.com/user-attachments/assets/1e693d61-f5d0-4ec8-989f-438dfd52250a)

Example in EP:

![image](https://github.com/user-attachments/assets/f1aca080-8c44-4f43-98f4-f5c1836719f1)


