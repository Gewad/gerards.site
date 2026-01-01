# FTP Deployment Setup Guide

This document explains how to configure the automatic FTP deployment for this website.

## Overview

The website automatically deploys to your hosting VM via FTP whenever changes are pushed to the `main` branch using GitHub Actions.

## Required GitHub Secrets

You need to configure three secrets in your GitHub repository:

### 1. FTP_SERVER
- **Description**: The address of your FTP server
- **Example**: `ftp.yourdomain.com` or `192.168.1.100`
- **Note**: Do not include `ftp://` prefix

### 2. FTP_USERNAME
- **Description**: Your FTP account username
- **Example**: `username` or `user@domain.com`

### 3. FTP_PASSWORD
- **Description**: Your FTP account password
- **Note**: Keep this secure and never commit it to the repository

## How to Add Secrets

1. Go to your GitHub repository: https://github.com/Gewad/gerards.site
2. Click on **Settings** (top menu)
3. In the left sidebar, click **Secrets and variables** → **Actions**
4. Click the **New repository secret** button
5. Add each secret:
   - Enter the secret name (e.g., `FTP_SERVER`)
   - Enter the secret value
   - Click **Add secret**
6. Repeat for all three required secrets

## Workflow Details

The deployment workflow (`.github/workflows/deploy.yml`) will:
- Trigger automatically on every push to the `main` branch
- Check out the latest code
- Upload all files from the `src/` folder to your FTP server
- Use the SamKirkland/FTP-Deploy-Action for reliable deployment

## Server Directory

By default, files are uploaded to the root directory (`./`) of your FTP account. If you need to deploy to a subdirectory, modify the `server-dir` parameter in `.github/workflows/deploy.yml`:

```yaml
server-dir: ./public_html/  # Or whatever your web root is
```

## Testing the Deployment

1. Configure all three secrets as described above
2. Make a small change to a file in the `src/` folder
3. Commit and push to the `main` branch
4. Go to the **Actions** tab in GitHub to monitor the deployment
5. Check your hosting VM to verify the files were uploaded

## Troubleshooting

If the deployment fails:
1. Check the Actions tab for error messages
2. Verify your FTP credentials are correct
3. Ensure your FTP server allows connections from GitHub's IP ranges
4. Check that the server directory exists and is writable
5. Verify your FTP server is using standard FTP (not SFTP/FTPS by default - modify workflow if needed)

## Security Notes

- Never commit FTP credentials directly in code
- Always use GitHub Secrets for sensitive information
- Consider using SFTP instead of FTP for better security (requires workflow modification)
- Regularly rotate your FTP password
