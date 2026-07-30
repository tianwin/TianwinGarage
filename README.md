# Auto Repair Orders

Streamlit app for managing Tianwin's Garage repair orders with Google Sheets as the backend.

## Run Locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

export GOOGLE_SHEETS_SPREADSHEET_ID="your-spreadsheet-id"
export GOOGLE_SHEETS_WORKSHEET_NAME="Orders"
export GOOGLE_SERVICE_ACCOUNT_JSON="/path/to/service_account.json"

streamlit run app_gsheets.py
```

## Deploy To Streamlit Community Cloud

1. Push this repo to GitHub.
2. In Streamlit Community Cloud, create a new app from the GitHub repo.
3. Set the app entry file to `app_gsheets.py`.
4. Add secrets in the app's **Settings > Secrets** panel.

Example secrets:

```toml
GOOGLE_SHEETS_SPREADSHEET_ID = "your-spreadsheet-id"
GOOGLE_SHEETS_WORKSHEET_NAME = "Orders"

[google_service_account]
type = "service_account"
project_id = "your-project-id"
private_key_id = "your-private-key-id"
private_key = "-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
client_email = "your-service-account@your-project-id.iam.gserviceaccount.com"
client_id = "your-client-id"
auth_uri = "https://accounts.google.com/o/oauth2/auth"
token_uri = "https://oauth2.googleapis.com/token"
auth_provider_x509_cert_url = "https://www.googleapis.com/oauth2/v1/certs"
client_x509_cert_url = "https://www.googleapis.com/robot/v1/metadata/x509/your-service-account%40your-project-id.iam.gserviceaccount.com"
universe_domain = "googleapis.com"
```

Share the Google Sheet with the service account email before launching the app.

## Import CSV

Make sure the CSV has the exact headers from `sample_import.csv`.

## Private Files

Do not commit service-account JSON files, `.streamlit/secrets.toml`, or local `data/` files. They are ignored by Git.
