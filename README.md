[![Sync Garmin to Notion](https://github.com/haateedee/garmin-to-notion/actions/workflows/sync.yml/badge.svg?branch=main)](https://github.com/haateedee/garmin-to-notion/actions/workflows/sync.yml)
# Garmin to Notion Integration

This project automatically syncs your Garmin activities to a Notion database, keeping your performance metrics in one place.

## Features

- Automatically syncs Garmin activities to Notion 3 times per day (6:00, 13:00, 19:00 CET)
- Tracks detailed activity metrics: distance, duration, calories, heart rate
- Skips duplicate entries and updates existing records when data changes
- Supports all Garmin activity types (runs, rides, walks, swims, and more)
- Zero-touch automation once configured
- Manual trigger available via GitHub Actions `workflow_dispatch`

## Prerequisites

- A Garmin Connect account
- A Notion account with API access

## Getting Started

### 1. Fork this GitHub Repository

### 2. Duplicate the [Notion Template](https://www.notion.so/templates/fitness-tracker-738)

- Save your Activities database ID (needed in step 4)
- Find it in the URL: `notion.so/username/[DATABASE_ID]?v=...`
- Copy everything between `username/` and `?v=`

### 3. Create a Notion Integration

- Go to [Notion Integrations](https://www.notion.so/profile/integrations)
- [Create](https://developers.notion.com/docs/create-a-notion-integration) a new integration and copy the token
- [Share](https://www.notion.so/help/add-and-manage-connections-with-the-api) the integration with your Activities database

### 4. Set GitHub Secrets

In your forked repository, go to **Settings → Secrets and variables → Actions** and add:

| Secret | Description |
|---|---|
| `GARMIN_EMAIL` | Your Garmin Connect email |
| `GARMIN_PASSWORD` | Your Garmin Connect password |
| `NOTION_TOKEN` | Your Notion integration token |
| `NOTION_DATABASE_ID` | Your Notion Activities database ID |

### 5. Enable the Workflow

The workflow runs automatically on schedule. You can also trigger it manually from the **Actions** tab using the **Run workflow** button.

To run the script locally:

```bash
pip install -r requirements.txt
python garmin-activities.py
```

## Schedule

The sync runs automatically 3 times per day:

| UTC | CET (UTC+1) | CEST (UTC+2) |
|---|---|---|
| 05:00 | 06:00 | 07:00 |
| 12:00 | 13:00 | 14:00 |
| 19:00 | 20:00 | 21:00 |

## Example

Here is a screenshot of what the Notion dashboard looks like:

![garmin-to-notion-template](https://github.com/user-attachments/assets/b37077cc-fe87-466f-9424-8ba9e4efa909)

The Notion template is available for free: [fitness-tracker-738](https://www.notion.so/templates/fitness-tracker-738)

## Acknowledgements

- Garmin Connect API client: [cyberjunky/python-garminconnect](https://github.com/cyberjunky/python-garminconnect.git)
- Inspired by [n-kratz/garmin-notion](https://github.com/n-kratz/garmin-notion.git)

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

<a href="https://www.buymeacoffee.com/cvoyer" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
