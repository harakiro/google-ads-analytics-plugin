# Google Ads & Analytics Monitor for Claude Code

> AI-powered marketing analytics assistant for monitoring, analyzing, and optimizing Google Ads campaigns and website performance.

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-purple.svg)](https://docs.claude.com/en/docs/claude-code)
[![Google Ads API](https://img.shields.io/badge/Google%20Ads-API-green.svg)](https://developers.google.com/google-ads/api)
[![Google Analytics](https://img.shields.io/badge/Google%20Analytics-GA4-orange.svg)](https://developers.google.com/analytics)

Transform Claude Code into your intelligent marketing analytics assistant with natural language queries, automated reports, and cross-platform insights.

## ✨ Features

### 🤖 Three Specialized AI Agents

- **Google Ads Manager** - Campaign performance, budget optimization, GAQL queries
- **Google Analytics Reporter** - Traffic analysis, user behavior, conversion tracking
- **Marketing Coordinator** - Cross-platform ROI, attribution modeling, unified insights

### 📊 Automated Reports

- **Weekly Performance Report** - Comprehensive summary combining Ads + Analytics
- **Campaign Health Check** - Diagnostic analysis with health scores and recommendations

### 💬 Natural Language Interface

Ask questions in plain English:
- "How are my campaigns performing this month?"
- "What's my website traffic by source?"
- "Calculate my true marketing ROI"
- "Which campaigns should I increase budget on?"

## 🚀 Quick Start

### Prerequisites

- Python 3.10+ with pipx
- Google Cloud project with APIs enabled
- Google Ads account (admin access)
- Google Analytics 4 property (viewer access)
- Claude Code installed

### Installation

1. **Install the plugin:**

```bash
# In Claude Code
/plugin install https://github.com/harakiro/google-ads-analytics-plugin
```

2. **Follow the setup guide:**

See [docs/setup-guide.md](docs/setup-guide.md) for complete configuration instructions.

3. **Start using:**

```bash
# Ask questions
"Show me my Google Ads performance"
"What's my website traffic this week?"

# Generate reports
/weekly-report
/campaign-health-check
```

## 📖 Documentation

- **[Setup Guide](docs/setup-guide.md)** - Complete configuration walkthrough
- **[Plugin README](.claude-plugin/README.md)** - Features and usage details
- **[Environment Template](.env.template)** - Configuration variables

## 🎯 Use Cases

### Campaign Monitoring
```
User: How are my Google Ads campaigns performing?

Claude: [Analyzes campaign data]
Your campaigns generated $87,500 in revenue from $25,000 spend (3.5x ROAS)
Top performer: Brand Campaign with 5.6x ROAS
Underperformer: Broad Keywords at 1.1x ROAS - recommend reducing budget
```

### Website Analytics
```
User: What's my website traffic breakdown?

Claude: [Analyzes GA4 data]
Last 7 days: 12,450 sessions
- Organic: 45% (5,603 sessions, 3.2% conversion rate)
- Paid: 30% (3,735 sessions, 2.8% conversion rate)
- Direct: 15% (1,868 sessions, 4.1% conversion rate)
- Referral: 10% (1,244 sessions, 1.9% conversion rate)
```

### Cross-Platform ROI
```
User: Calculate my true marketing ROI

Claude: [Integrates Ads + Analytics]
Total Investment: $25,000
Total Revenue (GA4): $87,500
ROI: 250% | ROAS: 3.5x
Recommended: Reallocate $3K from low-performing campaigns
Expected impact: ROAS improvement to 4.2x
```

### Automated Reporting
```
User: /weekly-report

Claude: [Generates comprehensive report]
📊 WEEKLY MARKETING PERFORMANCE REPORT
Period: Oct 28 - Nov 3, 2025
[Detailed breakdown of Ads + Analytics with trends and recommendations]
```

## 🏗️ Architecture

```
┌─────────────────────────────────┐
│   Claude Code Conversation      │
│   ┌─────────────────────────┐   │
│   │  Specialized Agents     │   │
│   │  • Ads Manager          │   │
│   │  • Analytics Reporter   │   │
│   │  • Coordinator          │   │
│   └──────────┬──────────────┘   │
└──────────────┼──────────────────┘
               │ MCP Protocol
┌──────────────▼──────────────────┐
│     Local MCP Servers (pipx)    │
│  ┌────────────┐  ┌────────────┐ │
│  │ Google Ads │  │ Google     │ │
│  │ MCP        │  │ Analytics  │ │
│  └──────┬─────┘  └─────┬──────┘ │
└─────────┼────────────────┼───────┘
          │ HTTPS          │
┌─────────▼────────────────▼───────┐
│       Google Cloud APIs          │
└──────────────────────────────────┘
```

## 🛠️ What's Included

```
google-ads-analytics-monitor/
├── .claude-plugin/
│   ├── plugin.json              # Plugin manifest
│   └── README.md                # Plugin documentation
├── agents/
│   ├── google-ads-manager.md           # Ads specialist agent
│   ├── google-analytics-reporter.md    # Analytics specialist agent
│   └── marketing-coordinator.md        # Integration agent
├── commands/
│   ├── weekly-report.md                # Automated weekly report
│   └── campaign-health-check.md        # Campaign diagnostics
├── docs/
│   └── setup-guide.md                  # Setup instructions
├── .mcp.json                    # MCP server configuration
├── .env.template                # Environment variables template
├── .gitignore                   # Security (excludes credentials)
└── README.md                    # This file
```

## 📊 Capabilities Matrix

| Feature | Ads Agent | Analytics Agent | Coordinator |
|---------|-----------|-----------------|-------------|
| Campaign Performance | ✅ Primary | ❌ | ✅ Analysis |
| Website Traffic | ❌ | ✅ Primary | ✅ Analysis |
| ROI Calculation | ✅ Ads Only | ✅ Web Only | ✅ Unified |
| Budget Optimization | ✅ Recommendations | ❌ | ✅ Cross-Platform |
| Attribution Modeling | ❌ | ✅ Multi-Touch | ✅ Comprehensive |
| Real-Time Data | ❌ | ✅ Last 30 min | ❌ |

## ⚠️ Important Notes

### Current Limitations

- **Read-Only Access**: Google MCP servers are experimental and provide read-only access
- **Data Delay**: 24-48 hour processing delay for historical data
- **Rate Limits**: 2,000 requests per 100 seconds per platform
- **Experimental**: Official Google MCP servers in beta phase

### Security

- Credentials stored locally (never committed to git)
- OAuth 2.0 authentication
- Environment variable configuration
- Comprehensive `.gitignore` for credential protection

## 🤝 Contributing

Contributions welcome! Areas for enhancement:

- Additional slash commands for specific workflows
- Enhanced visualization in reports
- More sophisticated analysis patterns
- Integration with additional platforms
- Write capabilities when Google adds MCP support

### Development Setup

1. Clone the repository
2. Follow [docs/setup-guide.md](docs/setup-guide.md)
3. Test locally with Claude Code
4. Submit pull requests with clear descriptions

## 📄 License

Apache License 2.0 - See [LICENSE](LICENSE) file for details.

Inherits from:
- Google Ads MCP Server (Apache 2.0)
- Google Analytics MCP Server (Apache 2.0)

## 🙏 Acknowledgments

Built with:
- [Google Ads MCP Server](https://github.com/googleads/google-ads-mcp) - Official Google Ads integration
- [Google Analytics MCP Server](https://github.com/googleanalytics/google-analytics-mcp) - Official GA4 integration
- [Claude Code](https://claude.ai/claude-code) - Anthropic's AI coding assistant
- [Model Context Protocol](https://modelcontextprotocol.io/) - MCP specification

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/harakiro/google-ads-analytics-plugin/issues)
- **Discussions**: [GitHub Discussions](https://github.com/harakiro/google-ads-analytics-plugin/discussions)
- **Documentation**: [Setup Guide](docs/setup-guide.md) | [Plugin README](.claude-plugin/README.md)

## 🗺️ Roadmap

### v1.0.0 (Current)
- ✅ Three specialized AI agents
- ✅ Two automated slash commands
- ✅ Google Ads + Analytics integration
- ✅ Comprehensive documentation
- ✅ Read-only access via official Google MCPs

### v1.1.0 (Planned)
- [ ] Additional slash commands (competitor analysis, forecast)
- [ ] Enhanced report visualizations
- [ ] Export reports (CSV, PDF)
- [ ] Historical trend analysis
- [ ] Alert notifications

### v2.0.0 (Future)
- [ ] Write capabilities (when Google adds MCP support)
- [ ] Automated optimization execution
- [ ] Multi-account management dashboard
- [ ] Integration with other platforms (Facebook, LinkedIn)
- [ ] Custom agent creation wizard

## ⭐ Star History

If you find this plugin useful, please consider giving it a star on GitHub!

---

**Ready to optimize your marketing with AI?**

Get started with the [Setup Guide](docs/setup-guide.md) and transform your marketing analytics workflow!

Made with ❤️ for the Claude Code community
