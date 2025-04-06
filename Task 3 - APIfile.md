# Sample Download API

## Description

The Sample Download API allows users to download the original uploaded for analysis.

The API Endpoint for it is `/api/v1/download_samples/` 

The following methods can be used:

| Method | Description |
|-|-|
| `GET` | Returns a list of all files available for download as a JSON response. |
| `POST` | Receives a JSON body with the IDs of files that the user wishes to download and provides a corresponding download link.|

The `GET` method can be further refined by using the following query parameters:

| Query Parameter | Description |
|-|-|
| `date` |Returns items analyzed on a specific date. |
| `user_id` | Returns items uploaded by that specific user. |

***NOTE*: The parameters are ignored when using the `POST` method.**

## Examples

### Python request

```
import requests
from requests.auth import HTTPBasicAuth

url = 'https://example.com/api/v1/download_samples/'

username = 'z1000_user'
password = 'z1000_password_example_123'

params = {
    'date': '2025-04-03', 
    'user_id': 'user123' 
}
```

### cURL request

```
curl -X GET "https://example.com/api/v1/download_samples/?date=2025-04-03&user_id=user123" \
  -u "z1000_user:z1000_password_example_123" \
  -H "Content-Type: application/json"

```

### Response

```
response = requests.get(url, params=params, auth=HTTPBasicAuth(username, password))

if response.status_code == 200:
    data = response.json()
    print("Response Data:", data)
else:
    print(f"Error: {response.status_code}, {response.text}")

{
  "status": "success",
  "message": "Samples retrieved successfully",
  "data": [
    {
      "sample_id": "12345",
      "filename": "malicious_file_1.exe",
      "file_size": 1024,
      "threat_level": "high",
      "threat_type": "malware",
      "last_scanned": "2025-04-03T10:15:00Z",
      "download_link": "https://example.com/downloads/malicious_file_1.exe"
    },
    {
      "sample_id": "12346",
      "filename": "suspicious_file_2.dll",
      "file_size": 512,
      "threat_level": "medium",
      "threat_type": "potentially unwanted program",
      "last_scanned": "2025-04-02T14:30:00Z",
      "download_link": "https://example.com/downloads/suspicious_file_2.dll"
    },
    {
      "sample_id": "12347",
      "filename": "safe_file_3.pdf",
      "file_size": 256,
      "threat_level": "low",
      "threat_type": "none",
      "last_scanned": "2025-04-01T08:45:00Z",
      "download_link": "https://example.com/downloads/safe_file_3.pdf"
    }
  ]
}
```

***NOTE*: If running any of the files flagged with a "high" or "medium" threat level type, take extra percautions as they may damage your system.**