---
layout: distill
title: Tenable
date: 2023-04-01 22:01:00
description: Automating Tenable Scan Downloads and Conversions to CSV and JSON with Python
#categories: sample-posts external-services

authors:
  - name: Amruta Pandhare
    affiliations:
      name: Tenable

toc:
  - name: About
  - name: Overview
  - name: Script
  - name: Additional Use Cases
  - name: Conclusion
---
## About

Managing Tenable scans programmatically can save time and effort, especially when dealing with multiple scans. This blog will guide you through a Python script that leverages the Tenable API to download specific scans, save them in CSV format, and convert the CSV files to JSON. We'll explain each part of the script so you can understand and modify it as needed. 

***
## Overview

Before diving into the code, let's outline the main steps the script performs:

**Configure logging and set API keys**: Initialize logging and define your Tenable API keys.

**Fetch scan data**: Retrieve the list of scans from Tenable.io.

**Download scans**: Export the scans in CSV format.

**Save and process scans**: Save the CSV files and convert them to JSON format.

***
## Script

Here's the full script with comments explaining each part:

```python
import requests
import json
import csv
import sys
import time
import pandas as pd
import logging
import re

# Configure logging
logging.basicConfig(filename='log.txt', level=logging.INFO, format='%(asctime)s:%(levelname)s:%(message)s')

# Set Tenable API keys
ACCESS_KEY = 'YOUR_ACCESS_KEY'
SECRET_KEY = 'YOUR_SECRET_KEY'
scan_search_list = ['scan1', 'scan2', 'scan3']

# Set the base URL and headers for the Tenable API
url = 'https://cloud.tenable.com'
headers = {'X-ApiKeys': f'accessKey={ACCESS_KEY}; secretKey={SECRET_KEY};'}

for scan_search in scan_search_list:
    logging.info(f"Processing scan search: {scan_search}")

    # Fetching scans
    scans = requests.get(f'{url}/scans', headers=headers).json()['scans']
    for scan in scans:
        if scan_search.lower() in scan['name'].lower() and not scan['name'].endswith('_OLD'):
            scan_id = scan['id']
            scan_name = scan['name']
            uuid = scan.get("uuid", scan.get("wizard_uuid", ""))  # UUID or WIZARD_UUID
            logging.info(f'Found: {scan_name} ({scan_id})')

            # Request download
            export_request = {
                'chapters': 'vuln_hosts_summary,vuln_by_host,compliance_exec,remediations,vuln_by_plugin,compliance',
                'filter.search_type': 'and',
                'format': 'csv'
            }
            file_request = requests.post(f'{url}/scans/{scan_id}/export', headers=headers, json=export_request)
            if file_request.status_code != 200 or 'error' in file_request.json():
                logging.error(f'Request failed for {scan_name}: {file_request.text}')
                continue  # Skip to the next scan

            file_id = file_request.json()['file']

            # Monitor until not loading
            status = 'loading'
            while status == 'loading':
                time.sleep(1)
                file_status = requests.get(f'{url}/scans/{scan_id}/export/{file_id}/status', headers=headers).json()
                status = file_status['status']
                logging.info(f'Checking status for {scan_name}: {status}')

            # Download if ready
            if status == 'ready':
                file_download = requests.get(f'{url}/scans/{scan_id}/export/{file_id}/download', headers=headers)
                filename = f'{scan_name.replace(" ", "_")}.csv'
                with open(filename, 'wb') as fout:
                    fout.write(file_download.content)
                logging.info(f'Wrote: {filename}')

                # Convert CSV to JSON
                selected_columns = ['Host Start', 'Risk', 'CVE', 'Host', 'Name', 'Solution']
                df = pd.read_csv(filename, usecols=selected_columns)
                df.rename(columns={'Host Start': 'scanStartDate', 'Risk': 'risk', 'CVE': 'cve', 'Host': 'host', 'Name': 'name', 'Solution': 'solution'}, inplace=True)

                record_date = df['scanStartDate'].iloc[0][:10]

                scan_entries = []
                for _, row in df.iterrows():
                    entry = {
                        'scanStartDate': 'None' if pd.isna(row['scanStartDate']) else row['scanStartDate'],
                        'risk': 'None' if pd.isna(row['risk']) else row['risk'],
                        'cve': 'None' if pd.isna(row['cve']) else row['cve'],
                        'host': 'None' if pd.isna(row['host']) else row['host'],
                        'name': 'None' if pd.isna(row['name']) else row['name'],
                        'solution': 'None' if pd.isna(row['solution']) else row['solution']
                    }
                    scan_entries.append(entry)

                additional_info = {"recordDate": record_date, "scanEntries": scan_entries}
                final_json_data = json.dumps(additional_info) + '\n'

                json_filename = f'{scan_name}-{record_date}.json'
                with open(json_filename, 'w') as json_file:
                    json_file.write(final_json_data)
                logging.info(f'Appended information to JSON: {json_filename}')
            else:
                logging.error(f'Issue with file for {scan_name}: {status}')

print("Script execution completed.")

***

## Additional Use Cases

**Automated Report Generation**
Scheduled execution of the script to regularly download and process scans, generating periodic reports.
Email notifications to send generated reports or alerts based on scan results.

**Integration with SIEM Systems**
Send JSON data to a Security Information and Event Management (SIEM) system for further analysis and correlation.
Webhook integration to trigger real-time actions based on scan results.

**Visualization and Dashboarding**
Data visualization tools like Matplotlib or Seaborn to create visual reports from the scan data.
Integration with BI tools like Tableau or Power BI to create interactive dashboards.

**Advanced Filtering and Analysis**
Custom filters to extract specific vulnerabilities or assets based on certain criteria.
Trend analysis to monitor vulnerability trends over time.

***
## Conclusion

This script automates the process of downloading and processing Tenable scan data, making it easier to manage and analyze scan results. By following the detailed steps above, you can adapt the script to fit your specific needs and integrate it into your workflow. Happy coding!
