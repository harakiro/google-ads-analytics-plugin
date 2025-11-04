# Google Ads & Analytics Monitor Plugin

Comprehensive Claude Code plugin for monitoring, analyzing, and optimizing Google Ads campaigns and website analytics performance.

## Overview

This plugin transforms Claude Code into a powerful marketing analytics assistant, providing:

- **Intelligent Analysis** of Google Ads campaigns and website performance
- **Cross-Platform Insights** combining ad spend with user behavior data
- **AI-Powered Recommendations** for campaign optimization
- **Automated Reporting** with customizable time periods
- **Health Monitoring** to catch issues before they waste budget

## Features

### 🤖 Specialized AI Agents

#### Google Ads Manager
Expert in campaign management and optimization.

**Capabilities:**
- Campaign performance analysis
- Budget pacing and utilization tracking
- Keyword and ad copy performance
- GAQL query generation for custom reports
- ROI and ROAS calculations
- Optimization recommendations

**Example Questions:**
- "How are my Google Ads campaigns performing this week?"
- "Which campaigns have the best ROAS?"
- "Show me keyword performance for Campaign X"
- "What's my cost per conversion trend?"

#### Google Analytics Reporter
Specialist in website analytics and user behavior.

**Capabilities:**
- Traffic source analysis
- User engagement metrics
- Conversion funnel analysis
- Real-time visitor monitoring
- Geographic and device insights
- Custom dimension/metric reporting

**Example Questions:**
- "What's my website traffic for the last month?"
- "Which traffic sources convert best?"
- "Show me mobile vs. desktop performance"
- "What are my top landing pages?"

#### Marketing Integration Coordinator
Combines Ads and Analytics for unified insights.

**Capabilities:**
- Cross-platform ROI analysis
- Attribution modeling
- Campaign-to-website correlation
- Budget optimization recommendations
- Discrepancy investigation
- Full-funnel performance tracking

**Example Questions:**
- "Calculate my true marketing ROI"
- "Why do Ads and Analytics show different conversion numbers?"
- "Which campaigns drive the most engaged users?"
- "Should I increase budget on Campaign Y?"

### 📊 Automated Reports

#### `/weekly-report`
Comprehensive weekly performance summary combining Google Ads and Analytics data.

**Includes:**
- Ad campaign performance (spend, clicks, conversions, ROAS)
- Website traffic and engagement metrics
- Cross-platform ROI analysis
- Week-over-week trends
- Prioritized optimization recommendations
- Next week outlook

**Usage:**
```
/weekly-report
/weekly-report for October 21-27
```

#### `/campaign-health-check`
Diagnostic analysis of all active campaigns with health scoring.

**Evaluates:**
- Budget efficiency and pacing
- Performance vs. benchmarks
- Engagement quality (from Analytics)
- Targeting effectiveness
- Technical configuration
- Trend analysis

**Provides:**
- Health score (0-100) for each campaign
- Critical issues requiring immediate action
- Optimization opportunities
- Expected impact of recommendations

**Usage:**
```
/campaign-health-check
/campaign-health-check for [account name]
```

## Installation

### Prerequisites

- Python 3.10+ with pipx installed
- Google Cloud project with APIs enabled:
  - Google Ads API
  - Google Analytics Admin API
  - Google Analytics Data API
- OAuth 2.0 credentials configured
- Google Ads Developer Token
- Claude Code installed

### Quick Install

```bash
# In Claude Code
/plugin install https://github.com/harakiro/google-ads-analytics-plugin
```

### Detailed Setup

See [Setup Guide](../docs/setup-guide.md) for complete step-by-step instructions covering:
1. Google Cloud configuration
2. API enablement and OAuth setup
3. Google Ads Developer Token
4. Environment variables
5. Testing and verification

## Configuration

### Environment Variables

Required environment variables:

```bash
# Path to OAuth 2.0 credentials JSON
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.google/ads-analytics-credentials.json"

# Your Google Cloud project ID
export GOOGLE_PROJECT_ID="your-project-id"

# Google Ads Developer Token
export GOOGLE_ADS_DEVELOPER_TOKEN="your-developer-token"

# Google Ads Customer ID (optional, digits only)
export GOOGLE_ADS_LOGIN_CUSTOMER_ID="1234567890"
```

### MCP Servers

This plugin uses two official Google MCP servers:

1. **Google Ads MCP** - Query campaign data via GAQL
2. **Google Analytics MCP** - Access GA4 reporting and admin APIs

Both are configured automatically during plugin installation.

## Usage Examples

### Campaign Performance

```
User: How are my Google Ads campaigns performing this month?

Claude: I'll analyze your Google Ads performance for November.
[Invokes google-ads-manager agent]
[Shows campaign summary with spend, conversions, ROAS]
[Highlights top performers and identifies issues]
[Provides optimization recommendations]
```

### Website Analytics

```
User: What's my website traffic like?

Claude: Let me check your Google Analytics data.
[Invokes google-analytics-reporter agent]
[Shows traffic volume, sources, engagement metrics]
[Breaks down by device, geography, behavior]
[Identifies trends and patterns]
```

### Cross-Platform Insights

```
User: Calculate my true ROI across advertising and website performance

Claude: I'll integrate data from Google Ads and Analytics to calculate ROI.
[Invokes marketing-coordinator agent]
[Combines ad spend with GA conversion data]
[Calculates unified metrics: ROAS, CPA, ROI]
[Shows campaign-by-campaign breakdown]
[Recommends budget reallocation]
```

### Automated Reports

```
User: /weekly-report

Claude: Generating comprehensive weekly marketing report...
[Gathers Ads data: campaigns, spend, conversions]
[Gathers Analytics data: traffic, engagement, conversions]
[Analyzes trends vs. previous week]
[Presents formatted report with insights]
[Provides prioritized action items]
```

### Campaign Health

```
User: /campaign-health-check

Claude: Performing diagnostic analysis of all active campaigns...
[Evaluates budget health, performance, engagement]
[Calculates health scores for each campaign]
[Identifies critical issues and opportunities]
[Provides prioritized recommendations]
```

## Capabilities Matrix

| Feature | Google Ads Agent | Analytics Agent | Coordinator Agent |
|---------|------------------|-----------------|-------------------|
| Campaign Performance | ✅ Primary | ❌ | ✅ Analysis |
| Website Traffic | ❌ | ✅ Primary | ✅ Analysis |
| ROI Calculation | ✅ Ads Only | ✅ Web Only | ✅ Unified |
| Conversion Tracking | ✅ Ad Conversions | ✅ GA Conversions | ✅ Reconciled |
| Budget Optimization | ✅ Recommendations | ❌ | ✅ Cross-Platform |
| Engagement Analysis | ❌ | ✅ Primary | ✅ By Campaign |
| Attribution Modeling | ❌ | ✅ Multi-Touch | ✅ Comprehensive |
| Real-Time Data | ❌ | ✅ Last 30 min | ❌ |

## Limitations

### Current Restrictions

⚠️ **Read-Only Access**
- The Google MCP servers are experimental and provide read-only access
- You can query and analyze data, but cannot modify campaigns or settings
- All recommendations must be implemented manually in Google Ads interface

⚠️ **Experimental Status**
- Google Ads and Analytics MCP servers are in experimental phase
- Not recommended for production-critical workflows
- May have API changes or limitations

⚠️ **Rate Limits**
- Google Ads API: 2,000 requests per 100 seconds per project
- Google Analytics API: 2,000 requests per 100 seconds per project
- Free GA4 properties: 10 concurrent requests maximum

⚠️ **Data Freshness**
- Google Ads data: 24-48 hour processing delay
- Google Analytics data: 24-48 hour processing delay
- Real-time Analytics: Last 30 minutes only

### Future Enhancements

When Google releases production-ready MCP servers with write access:
- Campaign creation and modification
- Budget adjustments
- Bid strategy changes
- Automated optimization execution
- Bulk operations

## Troubleshooting

### Common Issues

**"Authentication failed"**
- Verify credentials file location: `~/.google/ads-analytics-credentials.json`
- Check environment variables are set
- Re-run: `gcloud auth application-default login`

**"Developer token invalid"**
- Confirm token in Google Ads API Center
- Verify token is for correct account
- Check environment variable is set

**"No data returned"**
- Verify APIs enabled in Google Cloud Console
- Check accounts have data (campaigns exist, website has traffic)
- Allow 24-48 hours for data processing
- Confirm account permissions (read access minimum)

**"MCP server not found"**
- Verify pipx installed: `pipx --version`
- Test MCP servers manually (see setup guide)
- Restart Claude Code

See [Setup Guide](../docs/setup-guide.md) for detailed troubleshooting.

## Architecture

```
┌─────────────────────────────────────────┐
│        Claude Code Conversation         │
│                                         │
│  ┌───────────────────────────────────┐  │
│  │  Specialized AI Agents:           │  │
│  │  • google-ads-manager            │  │
│  │  • google-analytics-reporter     │  │
│  │  • marketing-coordinator         │  │
│  └──────────────┬────────────────────┘  │
│                 │                       │
│  ┌──────────────▼────────────────────┐  │
│  │  Slash Commands:                  │  │
│  │  • /weekly-report                 │  │
│  │  • /campaign-health-check         │  │
│  └──────────────┬────────────────────┘  │
└─────────────────┼────────────────────────┘
                  │
                  │ MCP Protocol (stdio)
                  │
┌─────────────────▼────────────────────────┐
│        MCP Servers (Local/pipx)          │
│                                          │
│  ┌──────────────────┐  ┌──────────────┐ │
│  │ Google Ads MCP   │  │ Google       │ │
│  │ (GAQL Queries)   │  │ Analytics    │ │
│  │                  │  │ MCP (GA4 API)│ │
│  └────────┬─────────┘  └──────┬───────┘ │
└───────────┼────────────────────┼─────────┘
            │                    │
            │ HTTPS API Calls    │
            │                    │
┌───────────▼────────────────────▼─────────┐
│         Google Cloud APIs                │
│  • Google Ads API                        │
│  • Google Analytics Admin API            │
│  • Google Analytics Data API             │
└──────────────────────────────────────────┘
```

## Data Privacy & Security

- **Local Execution**: MCP servers run locally on your machine
- **No Third-Party Access**: Data stays between you, Google APIs, and Claude Code
- **Credential Security**: OAuth tokens stored locally
- **Read-Only**: Current implementation cannot modify your data
- **Audit Trail**: All API calls logged in Google Cloud Console

## Version History

### v1.0.0 - Initial Release
- Three specialized AI agents
- Two automated slash commands
- Google Ads and Analytics integration
- Comprehensive documentation
- Read-only access via official Google MCP servers

## Contributing

Contributions welcome! Areas for improvement:
- Additional slash commands for specific workflows
- More sophisticated analysis patterns
- Enhanced visualization in reports
- Integration with additional platforms
- Write capabilities when Google adds MCP support

## Support & Resources

- **Setup Guide**: [docs/setup-guide.md](../docs/setup-guide.md)
- **Google Ads API Docs**: https://developers.google.com/google-ads/api
- **Google Analytics API Docs**: https://developers.google.com/analytics
- **Claude Code Docs**: https://docs.claude.com/en/docs/claude-code
- **Google Ads MCP**: https://github.com/googleads/google-ads-mcp
- **Google Analytics MCP**: https://github.com/googleanalytics/google-analytics-mcp

## License

Apache 2.0 (inherits from Google MCP server licenses)

## Acknowledgments

Built using:
- Google's official Ads and Analytics MCP servers
- Anthropic's Claude Code agent framework
- Model Context Protocol specification

---

**Ready to optimize your marketing performance with AI?**

Start with the [Setup Guide](../docs/setup-guide.md) and begin monitoring your campaigns in minutes!
