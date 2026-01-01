# gerards.site

My personal website with automatic FTP deployment.

## Project Structure

- `src/` - Contains all website files that will be deployed
  - `index.html` - Main homepage
  - `styles.css` - Global stylesheet
  - Additional pages and assets can be added here

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

## Development

1. Edit files in the `src/` directory
2. Commit and push changes to the `main` branch
3. The GitHub Actions workflow will automatically deploy your changes via FTP

## Local Testing

You can test the website locally by opening `src/index.html` in your web browser or using a local web server:

```bash
# Using Python 3
cd src
python3 -m http.server 8000

# Using PHP
cd src
php -S localhost:8000

# Using Node.js (with npx)
cd src
npx http-server
```

Then visit `http://localhost:8000` in your browser.
