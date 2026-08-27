# Spare Partner Portal - Setup Instructions

This gets the two application forms (Marketplace Partner / Referral Partner) actually
delivering into your Google Sheet and Slack. The page itself, the Sheet, and the Apps
Script backend are already built and deployed. The one thing left is a single
Script Property value, below.

## What's already done

- **The landing page**: `index.html`, fully built with branding, reach stats, country
  list, partner categories, an autoplaying hero video, and both application forms.
  Fully self-contained (no external assets folder needed) and deployed on Vercel.
- **The Google Sheet**: "Spare Partner Portal - Applications" has been created in
  Google Drive, with columns for Timestamp, Partner Type, Name, Email, Phone, Company,
  Website, and source page.
  Sheet: https://docs.google.com/spreadsheets/d/1GBGzIfZbW_z0DdM7YYBs3lM7ib-QEbgJph-UjsK5nRo/edit
- **The backend script**: `Code.gs`, already deployed as a Web App and pointed at that
  Sheet's ID. The deployment URL is already wired into `index.html`.
- **The Slack channel**: an existing incoming webhook for `#business-development` is
  already available (shared with other internal tools).

## The one remaining step - add the Slack webhook to the script

1. Go to https://script.google.com/home and open the "Spare Partner Portal Backend"
   project (the one containing `Code.gs`).
2. Click the gear icon (**Project Settings**) in the left sidebar.
3. Scroll to **Script Properties** -> **Add script property**.
   - Property: `SLACK_WEBHOOK_URL`
   - Value: the Slack incoming webhook URL for `#business-development`.
   - Click **Save**.

That's it. The Sheet logging already works without this; adding the property turns on
the Slack notification for each new submission.

## Test it

1. Open the live site (the Vercel URL for this project).
2. Scroll to the bottom and submit a test application on either form.
3. Check:
   - The Google Sheet gets a new row within a couple of seconds.
   - A message appears in **#business-development** (only after the Script Property
     above is set).
4. If the Sheet updates but Slack doesn't, double check the Script Property name is
   exactly `SLACK_WEBHOOK_URL` (case-sensitive) and that it was saved.

## Redeploying the backend after editing Code.gs

If you ever change `Code.gs`, you need to create a **new deployment version** (or
manage deployments -> edit -> deploy) in the Apps Script editor for the change to take
effect on the live `/exec` URL - saving the file alone is not enough.

## Updating the page later

`index.html` is a single self-contained file (HTML, CSS, JS, images, and the hero
video all inline), no build step. Edit it directly, commit, and Vercel redeploys
automatically.
