# Health Dashboard Configuration

This repository contains configuration files for the Environment Health Dashboard.

## Banner Configuration

The `banner-config.json` file controls the banner displayed at the top of the dashboard.

### How to Update the Banner

1. Go to https://github.com/Legal-Aid-of-North-Carolina/healthDashboardConfig
2. Click on `banner-config.json`
3. Click the pencil icon (✏️) in the top right to edit
4. Make your changes (see Configuration Options below)
5. Scroll down and add a brief commit message describing your change
6. Click **Commit changes**
7. Changes will appear on the dashboard within 5 minutes

### Configuration Options

```json
{
  "id": "unique-banner-id",  // Unique ID for this banner (required for dismissible banners)
  "enabled": true,           // Set to false to hide the banner completely
  "type": "info",           // Options: "info", "warning", "error", "success"
  "message": "Your message", // The text to display in the banner
  "dismissible": true       // If true, users can close the banner
}
```

**Important:** The `id` field should be unique for each banner message. When a user dismisses a banner, the ID is stored. If you change the message but keep the same ID, previously dismissed users won't see the update. Change the ID when you want to show a new banner to all users.

### Banner Types

- **info** (ℹ️): Blue banner for general information
- **warning** (⚠️): Yellow banner for caution/upcoming changes
- **error** (🚨): Red banner for critical issues or outages
- **success** (✅): Green banner for positive updates

### Example Messages

**Planned Maintenance:**
```json
{
  "id": "maintenance-2026-03-15",
  "enabled": true,
  "type": "warning",
  "message": "Scheduled maintenance on March 15 from 2-4 PM EST. Services may be unavailable.",
  "dismissible": true
}
```

**Outage Alert:**
```json
{
  "id": "outage-textintake-dev-20260306",
  "enabled": true,
  "type": "error",
  "message": "Text Intake DEV environment is currently down. Engineers are investigating.",
  "dismissible": false
}
```

**New Feature:**
```json
{
  "id": "feature-admin-links-2026-03",
  "enabled": true,
  "type": "success",
  "message": "New admin features now available! Access them at /admin endpoint.",
  "dismissible": true
}
```

**Hide Banner:**
```json
{
  "id": "welcome-2026-03",
  "enabled": false,
  "type": "info",
  "message": "",
  "dismissible": true
}
```

### Technical Details

- The dashboard checks for updates every 5 minutes
- Banner content is cached in users' browsers to reduce API calls
- If a user dismisses the banner, it won't show again until the message changes
- GitHub's raw content CDN may take up to 5 minutes to reflect changes

## Need Help?

Contact the development team if you need assistance updating the configuration.
