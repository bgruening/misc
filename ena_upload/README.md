## ENA upload tool on Galaxy (Dev)
[ENA upload tool](https://github.com/usegalaxy-eu/ena-upload-cli) is designed to upload NGS tool to ENA data submission repo as a bulk via Galaxy.

## Issue
"TimeoutError: The read operation timed out" on Galaxy Dev 

## Troubleshoot
The same ena upload tool has been tested on the following machine
1) OK - VM at home
2) FAILED - VM on Pawsey
3) FAILED - Galaxy Produciton and Dev

- The root cause is due to the conn.unwrap of the storbinary function in the ftplib.py (see [line 502](https://github.com/python/cpython/blob/8b541c017ea92040add608b3e0ef8dc85e9e6060/Lib/ftplib.py#L502) )
- To resolve this issue, comment out conn.unwrap() (line 502) and insert "pass" below the conn.wrap()
