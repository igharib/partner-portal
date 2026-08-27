# Spare Partner Portal

Landing page for recruiting Marketplace Partners and Referral Partners for Spare (paywithspare.com). Single self-contained index.html (inline CSS/JS, all images and the hero video embedded as data URIs), no build step and no external asset files required.

## Structure

- index.html - the entire landing page, fully self-contained.
- backend/Code.gs - Google Apps Script backend. Logs form submissions to a Google Sheet and posts a notification to Slack (#business-development). Deployed separately as a Web App at script.google.com (not part of this repo's build).
- backend/SETUP-INSTRUCTIONS.md - manual setup notes for the backend.

## Dev

Just open index.html in a browser, or serve the folder with any static file server.

## Deploy

Deployed as a static site on Vercel.
