# gerards.site

My personal website with automatic FTP deployment.

## Project Structure

- `src/` - Contains all website files that will be deployed

## Deployment

The website automatically deploys to the hosting VM via FTP whenever changes are pushed to the `main` branch.

### Required GitHub Secrets

To enable automatic deployment, configure the following secrets in your repository settings:

1. `FTP_SERVER` - Your FTP server address (e.g., `ftp.yourdomain.com`)
2. `FTP_USERNAME` - Your FTP username
3. `FTP_PASSWORD` - Your FTP password

### Setting up GitHub Secrets

1. Go to your repository on GitHub
2. Navigate to Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Add each of the required secrets listed above
