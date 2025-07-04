# Panoptic Scans API Quickstart

This repository contains an Insomnia collection for the **Panoptic Scans API**, a service for managing network security scans and reports.

## Base URL
```
https://panopticscans.com
```

## Authentication

The API uses Bearer token authentication. You'll need to obtain a token first before accessing protected endpoints.

## API Endpoints

### 🔐 Authentication Endpoints

#### Get API Token
- **Method:** `POST`
- **Endpoint:** `/api/token`
- **Description:** Obtain an API token for authentication
- **Parameters:** 
  - `key` (query parameter) - Your API key
- **Authentication:** None required

#### Refresh Token
- **Method:** `POST`
- **Endpoint:** `/api/refresh`
- **Description:** Refresh/renew your existing API token
- **Authentication:** Bearer token required

#### Get Authenticated User
- **Method:** `GET`
- **Endpoint:** `/api/user`
- **Description:** Retrieve information about the currently authenticated user
- **Authentication:** Bearer token required

### 📊 Scan Management Endpoints

#### Retrieve All Scans
- **Method:** `GET`
- **Endpoint:** `/api/scans`
- **Description:** Get a list of all scans associated with your account
- **Authentication:** Bearer token required

#### Create New Scan
- **Method:** `POST`
- **Endpoint:** `/api/new-scan`
- **Description:** Create a new security scan
- **Authentication:** Bearer token required
- **Request Body:**
  ```json
  {
    "scan_name": "Just an API Test",
    "scan_type": "Nmap",
    "scan_frequency": "One-time",
    "scan_start_date": "September 11, 2023",
    "scan_start_time": "8:45 PM",
    "scan_time_zone": "America/New_York",
    "scan_email": "weeble@example.com",
    "scan_target": "scanme.nmap.org"
  }
  ```

#### Rename Scan
- **Method:** `PUT`
- **Endpoint:** `/api/scans/{scan_uuid}`
- **Description:** Update/rename an existing scan
- **Authentication:** Bearer token required
- **URL Parameters:**
  - `scan_id` - The unique identifier of the scan to update
- **Request Body:**
  ```json
  {
    "scan_name": "Changed API Test"
  }
  ```

#### Delete Scan
- **Method:** `DELETE`
- **Endpoint:** `/api/scans/{scan_uuid}`
- **Description:** Delete a specific scan
- **Authentication:** Bearer token required
- **URL Parameters:**
  - `scan_id` - The unique identifier of the scan to delete

### 📄 Report Generation Endpoints

#### Get TXT Report
- **Method:** `GET`
- **Endpoint:** `/api/scans/txt/{scan_uuid}`
- **Description:** Retrieve scan results in plain text format
- **Authentication:** Bearer token required
- **URL Parameters:**
  - `scan_id` - The unique identifier of the scan

#### Get HTML Report
- **Method:** `GET`
- **Endpoint:** `/api/scans/html/{scan_uuid}`
- **Description:** Retrieve scan results in HTML format
- **Authentication:** Bearer token required
- **URL Parameters:**
  - `scan_id` - The unique identifier of the scan

#### Get PDF Report
- **Method:** `GET`
- **Endpoint:** `/api/scans/pdf/{scan_uuid}`
- **Description:** Retrieve scan results in PDF format
- **Authentication:** Bearer token required
- **URL Parameters:**
  - `scan_id` - The unique identifier of the scan

## Usage Workflow

1. **Authentication:** First, obtain an API token using the `/api/token` endpoint with your API key
2. **Create Scan:** Use the `/api/new-scan` endpoint to create a new security scan
3. **Monitor Scans:** Use `/api/scans` to retrieve all your scans and monitor their status
4. **Manage Scans:** Use `/api/scans/{scan_uuid}` with PUT method to rename or DELETE method to remove scans
5. **Generate Reports:** Once scans are complete, use the report endpoints to download results in your preferred format (TXT, HTML, or PDF)
6. **Token Management:** Use `/api/refresh` to renew your token and `/api/user` to verify your authentication status

## Scan Parameters

When creating a new scan, you can specify:

- **scan_name:** A descriptive name for your scan
- **scan_type:** The type of scan (e.g., "Nmap")
- **scan_frequency:** How often the scan should run (e.g., "One-time")
- **scan_start_date:** When the scan should start
- **scan_start_time:** The specific time to start the scan
- **scan_time_zone:** The timezone for the scan schedule
- **scan_email:** Email address for notifications
- **scan_target:** The target to scan (e.g., domain, IP address)

## Report Formats

The API supports three report formats:
- **TXT:** Plain text format for programmatic processing
- **HTML:** Web-friendly format for viewing in browsers
- **PDF:** Professional format for sharing and archiving

## Sample Scan UUID

The collection includes sample requests using the scan UUID: `e510ab1c-1dec-41a5-86c9-9499220912ac`

Replace this with your actual scan UUIDs when making requests.

## Import Instructions

1. Open Insomnia
2. Go to Application > Preferences > Data > Import Data
3. Select the `Insomnia_PanopticScans.json` file
4. The collection will be imported with all endpoints and sample requests

## Environment Configuration

The collection uses a `base_url` environment variable set to `https://panopticscans.com`. Make sure to configure this in your Insomnia environment settings if you need to use a different base URL. 
