# Setup Guide: Google Ads & Analytics Monitor Plugin

Complete step-by-step guide to configure and use the Google Ads & Analytics monitoring plugin for Claude Code.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Google Cloud Setup](#google-cloud-setup)
3. [Google Ads API Setup](#google-ads-api-setup)
4. [Google Analytics Setup](#google-analytics-setup)
5. [Local Environment Setup](#local-environment-setup)
6. [Plugin Installation](#plugin-installation)
7. [Testing & Verification](#testing--verification)
8. [Troubleshooting](#troubleshooting)

---

## Prerequisites

Before you begin, ensure you have:

- [ ] Google Cloud account (create at [cloud.google.com](https://cloud.google.com))
- [ ] Google Ads account with admin access
- [ ] Google Analytics 4 property with editor/admin access
- [ ] Python 3.10 or higher installed
- [ ] Claude Code installed and configured
- [ ] Command-line access (Terminal/PowerShell)

**Time Required:** 30-60 minutes (first-time setup)

---

## Google Cloud Setup

### Step 1: Create Google Cloud Project

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Click "Select a project" → "New Project"
3. Enter project name: `ads-analytics-monitor` (or your preference)
4. Click "Create"
5. Wait for project creation (~30 seconds)
6. **Note your Project ID** - you'll need this later

### Step 2: Enable Required APIs

1. In the Cloud Console, navigate to **APIs & Services** → **Library**
2. Search for and enable each of these APIs:

   **For Google Ads:**
   - [ ] Google Ads API

   **For Google Analytics:**
   - [ ] Google Analytics Admin API
   - [ ] Google Analytics Data API

3. For each API:
   - Click on the API name
   - Click "Enable"
   - Wait for activation

### Step 3: Create OAuth 2.0 Credentials

1. Navigate to **APIs & Services** → **Credentials**
2. Click **"+ Create Credentials"** → **"OAuth client ID"**
3. If prompted, configure the OAuth consent screen:
   - User Type: **External** (or Internal for Google Workspace)
   - App name: `Ads Analytics Monitor`
   - User support email: Your email
   - Developer contact: Your email
   - Scopes: Add these scopes:
     - `https://www.googleapis.com/auth/adwords`
     - `https://www.googleapis.com/auth/analytics.readonly`
   - Test users: Add your Google account email
   - Click "Save and Continue"

4. Return to **Credentials** → **"+ Create Credentials"** → **"OAuth client ID"**
5. Application type: **Desktop app**
6. Name: `ads-analytics-cli`
7. Click **"Create"**
8. Click **"Download JSON"** on the popup
9. Save the file as `ads-analytics-credentials.json`
10. Move the file to `~/.google/ads-analytics-credentials.json`

```bash
# On Mac/Linux:
mkdir -p ~/.google
mv ~/Downloads/client_secret_*.json ~/.google/ads-analytics-credentials.json

# On Windows (PowerShell):
New-Item -ItemType Directory -Force -Path ~\.google
Move-Item ~\Downloads\client_secret_*.json ~\.google\ads-analytics-credentials.json
```

---

## Google Ads API Setup

### Step 1: Access Google Ads API Center

1. Log in to your Google Ads account
2. Click the **Tools** icon (wrench) in the top right
3. Under **Setup**, click **API Center**

### Step 2: Request Developer Token

1. In API Center, you'll see the "Developer token" section
2. If you don't have a token:
   - Fill out the application form
   - For access level, select:
     - **Test access** (for personal use, sufficient for read-only)
     - **Standard access** (for production use, requires Google review)
3. Click **"Apply"**

**For Test Access:**
- Approved immediately
- Can access your own accounts
- Sufficient for this plugin (read-only usage)

**For Standard Access:**
- Requires application review (1-2 weeks)
- Can access client accounts
- Needed for agency/multi-account management

4. **Copy your Developer Token** - you'll need this in environment variables

### Step 3: Note Your Customer ID

1. In Google Ads, look at the top of the page
2. You'll see your Customer ID (format: `123-456-7890`)
3. **Note this number** (remove hyphens when using: `1234567890`)

---

## Google Analytics Setup

### Step 1: Verify GA4 Property Access

1. Go to [Google Analytics](https://analytics.google.com)
2. Ensure you have at least **Viewer** access to the GA4 property
3. Note your **Property ID**:
   - In GA4, go to **Admin** (gear icon)
   - Select your property
   - Property ID is shown at the top (format: `123456789`)

### Step 2: Link Google Ads (Optional but Recommended)

1. In GA4 Admin → **Property** column → **Google Ads Links**
2. Click **"Link"**
3. Select your Google Ads account
4. Configure link settings:
   - Enable auto-tagging
   - Import conversions to Google Ads
5. Click **"Submit"**

This enables cross-platform analysis and attribution.

---

## Local Environment Setup

### Step 1: Install Python and pipx

**Check Python version:**
```bash
python3 --version
# Should be 3.10 or higher
```

**Install pipx:**
```bash
# On Mac/Linux:
python3 -m pip install --user pipx
python3 -m pipx ensurepath

# On Windows:
py -m pip install --user pipx
py -m pipx ensurepath

# Restart your terminal after installing
```

**Verify pipx installation:**
```bash
pipx --version
```

### Step 2: Test MCP Server Installations

**Test Google Ads MCP:**
```bash
pipx run --spec git+https://github.com/googleads/google-ads-mcp.git google-ads-mcp --help
```

**Test Google Analytics MCP:**
```bash
pipx run analytics-mcp --help
```

If both commands succeed, you're ready to proceed!

### Step 3: Authenticate with Google Cloud

Use gcloud CLI for Application Default Credentials:

```bash
# Install gcloud CLI if not already installed
# See: https://cloud.google.com/sdk/docs/install

# Login and set up credentials
gcloud auth application-default login \
  --scopes=https://www.googleapis.com/auth/adwords,https://www.googleapis.com/auth/analytics.readonly
```

Follow the browser prompts to authenticate.

**Alternative:** The MCP servers will prompt for authentication on first use if ADC is not configured.

### Step 4: Configure Environment Variables

Create environment variables for the MCP servers:

**On Mac/Linux (add to `~/.bashrc` or `~/.zshrc`):**
```bash
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.google/ads-analytics-credentials.json"
export GOOGLE_PROJECT_ID="your-project-id"
export GOOGLE_ADS_DEVELOPER_TOKEN="your-developer-token"
export GOOGLE_ADS_LOGIN_CUSTOMER_ID="1234567890"  # No hyphens!
```

**On Windows (PowerShell - add to profile):**
```powershell
$env:GOOGLE_APPLICATION_CREDENTIALS="$HOME\.google\ads-analytics-credentials.json"
$env:GOOGLE_PROJECT_ID="your-project-id"
$env:GOOGLE_ADS_DEVELOPER_TOKEN="your-developer-token"
$env:GOOGLE_ADS_LOGIN_CUSTOMER_ID="1234567890"
```

Replace with your actual values:
- `your-project-id`: From Google Cloud Console
- `your-developer-token`: From Google Ads API Center
- `1234567890`: Your Google Ads Customer ID (digits only)

**Reload your shell:**
```bash
# On Mac/Linux:
source ~/.bashrc  # or ~/.zshrc

# On Windows:
# Close and reopen PowerShell
```

---

## Plugin Installation

### Method 1: Via Marketplace (Recommended)

Add the plugin marketplace and install:

```bash
# In Claude Code - Add marketplace
/plugin marketplace add harakiro/google-ads-analytics-plugin

# Browse and install the plugin
/plugin
```

Select "google-ads-analytics-plugin" from the list and install.

### Method 2: Local Installation

Clone and install from local directory:

```bash
# Clone the repository
git clone https://github.com/harakiro/google-ads-analytics-plugin.git

# In Claude Code - Install from local directory
/plugin install /path/to/google-ads-analytics-plugin
```

### Method 3: Project Auto-Install

Add to your project's `.claude/settings.json`:

```json
{
  "plugins": ["google-ads-analytics-plugin"]
}
```

Then restart Claude Code.

### Verify Installation

1. Restart Claude Code (if needed)
2. Check installed plugins:
   ```
   /plugin list
   ```
3. Verify MCP servers:
   ```
   /mcp list
   ```

You should see:
- `google-ads` (connected)
- `google-analytics` (connected)

---

## Testing & Verification

### Test 1: Google Ads Connection

In Claude Code, ask:

```
List my Google Ads accounts
```

Expected response: List of accessible customer accounts

### Test 2: Google Analytics Connection

```
Show my Google Analytics properties
```

Expected response: List of GA4 properties you can access

### Test 3: Campaign Data

```
What are my active Google Ads campaigns?
```

Expected response: List of active campaigns with basic info

### Test 4: Website Traffic

```
What's my website traffic for the last 7 days?
```

Expected response: Traffic summary from Google Analytics

### Test 5: Agents

The agents should be automatically invoked based on your questions. Verify:

```
How are my ad campaigns performing?
```
→ Should invoke `google-ads-manager` agent

```
Show me website analytics
```
→ Should invoke `google-analytics-reporter` agent

```
Calculate my marketing ROI
```
→ Should invoke `marketing-coordinator` agent

### Test 6: Slash Commands

```
/weekly-report
```

Should generate comprehensive weekly report combining Ads + Analytics.

```
/campaign-health-check
```

Should analyze all campaigns and provide health scores.

---

## Troubleshooting

### Issue: "Authentication failed"

**Solution:**
1. Verify credentials file exists at `~/.google/ads-analytics-credentials.json`
2. Check environment variables are set:
   ```bash
   echo $GOOGLE_APPLICATION_CREDENTIALS
   echo $GOOGLE_PROJECT_ID
   ```
3. Re-run authentication:
   ```bash
   gcloud auth application-default login
   ```

### Issue: "Developer token invalid"

**Solution:**
1. Verify token in Google Ads API Center
2. Ensure token is for the correct account
3. Check token has not expired (test tokens don't expire)
4. Confirm environment variable is set correctly:
   ```bash
   echo $GOOGLE_ADS_DEVELOPER_TOKEN
   ```

### Issue: "Customer ID not found"

**Solution:**
1. Verify Customer ID format: digits only, no hyphens
   - ✅ Correct: `1234567890`
   - ❌ Wrong: `123-456-7890`
2. Check you have access to this account
3. Try without specifying Customer ID (let MCP list accessible accounts)

### Issue: "MCP server not found"

**Solution:**
1. Verify pipx is installed: `pipx --version`
2. Test MCP servers manually:
   ```bash
   pipx run --spec git+https://github.com/googleads/google-ads-mcp.git google-ads-mcp --help
   ```
3. Check `.mcp.json` configuration in plugin directory
4. Restart Claude Code

### Issue: "No data returned"

**Solution:**
1. Verify APIs are enabled in Google Cloud Console
2. Check account has data (campaigns exist, website has traffic)
3. Verify date range (data may have 24-48 hour processing delay)
4. Check account permissions (need at least read access)

### Issue: "Rate limit exceeded"

**Solution:**
1. Google APIs limit: 2,000 requests per 100 seconds
2. Wait a minute and retry
3. Reduce frequency of queries
4. Consider implementing caching for frequently accessed data

### Issue: "Conversion tracking not working"

**Solution:**
1. Verify Google Ads auto-tagging is enabled
2. Check Analytics conversion events are configured
3. Confirm accounts are properly linked (Google Ads ↔ Analytics)
4. Allow 24-48 hours for conversion data to process

### Issue: "Agents not invoked automatically"

**Solution:**
1. Check agent descriptions are clear in `.md` files
2. Try invoking manually:
   ```
   Use the google-ads-manager agent to analyze my campaigns
   ```
3. Verify agents directory is in correct location
4. Check plugin installation: `/plugin list`

---

## Advanced Configuration

### Use Service Account Instead of OAuth

For automated/server environments:

1. In Google Cloud Console → **IAM & Admin** → **Service Accounts**
2. Create service account
3. Grant necessary permissions
4. Download JSON key
5. Update environment variable to point to service account key
6. Share service account email with Google Ads and Analytics (grant access)

### Multiple Accounts

To manage multiple Google Ads or Analytics accounts:

1. Ensure OAuth consent includes all accounts
2. MCP servers will list all accessible accounts
3. Agents can query across accounts
4. Specify account in queries: "Show campaigns for account X"

### Custom MCP Configuration

Edit `.mcp.json` or `.mcp.local.json` to customize:

```json
{
  "mcpServers": {
    "google-ads": {
      "env": {
        "GOOGLE_ADS_LOGIN_CUSTOMER_ID": "different-customer-id"
      }
    }
  }
}
```

---

## Security Best Practices

1. **Never commit credentials to version control**
   - Add to `.gitignore`: `*.json` (credentials)
   - Use environment variables or secret management

2. **Use least-privilege access**
   - Google Ads: Read-only test token sufficient
   - Analytics: Viewer access sufficient
   - Only grant access to needed accounts

3. **Rotate credentials periodically**
   - Regenerate OAuth tokens every 6-12 months
   - Monitor API usage for anomalies

4. **Secure credential storage**
   - Keep credentials in `~/.google` with restricted permissions:
     ```bash
     chmod 600 ~/.google/ads-analytics-credentials.json
     ```

5. **Use separate credentials per environment**
   - Development vs. Production
   - Personal vs. Team

---

## Next Steps

Once setup is complete:

1. **Run first weekly report:** `/weekly-report`
2. **Perform health check:** `/campaign-health-check`
3. **Explore agents:** Ask questions about campaigns and analytics
4. **Set up automation:** Schedule regular reports
5. **Customize:** Add custom slash commands or modify agents

## Getting Help

- **Plugin Issues:** Check GitHub repository issues
- **Google Ads API:** [Google Ads API Documentation](https://developers.google.com/google-ads/api/docs/start)
- **Google Analytics API:** [GA4 Data API Documentation](https://developers.google.com/analytics/devguides/reporting/data/v1)
- **Claude Code:** [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code)

---

## Summary Checklist

Before using the plugin, ensure:

- [ ] Google Cloud project created with APIs enabled
- [ ] OAuth 2.0 credentials downloaded and placed in `~/.google/`
- [ ] Google Ads Developer Token obtained
- [ ] Environment variables configured
- [ ] Python 3.10+ and pipx installed
- [ ] MCP servers tested and working
- [ ] Plugin installed in Claude Code
- [ ] MCP servers showing as connected
- [ ] Test queries successful

**You're ready to start monitoring your Google Ads and Analytics!** 🎉
