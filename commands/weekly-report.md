# Weekly Marketing Performance Report

Generate a comprehensive weekly performance report combining Google Ads campaign data and Google Analytics website metrics.

## Report Scope

Analyze the last 7 complete days (Monday-Sunday or any 7-day period specified by the user) covering:

### Google Ads Performance
- Campaign-level spend, clicks, impressions, conversions
- Cost efficiency metrics (CPC, CPA, ROAS)
- Top performing campaigns and ad groups
- Budget pacing and utilization
- Keyword performance highlights

### Website Analytics
- Traffic volume and sources
- User engagement (bounce rate, session duration, pages per session)
- Device and geographic breakdowns
- Conversion funnel performance
- Top landing pages and content

### Integrated Insights
- Cross-platform ROI analysis
- Campaign-to-website performance correlation
- Attribution insights
- Discrepancy analysis (Ads vs Analytics)
- Budget optimization recommendations

## Execution Workflow

1. **Identify Time Period**
   - Default: Last 7 complete days
   - Ask user if they want a custom date range

2. **Gather Google Ads Data**
   - List accessible accounts
   - Query campaign performance for the period
   - Calculate key metrics and trends
   - Identify top and bottom performers

3. **Gather Analytics Data**
   - List available properties
   - Run traffic and conversion reports
   - Analyze user behavior metrics
   - Segment by campaign/source

4. **Integrate & Analyze**
   - Match campaigns across platforms
   - Calculate unified ROI metrics
   - Compare period vs. previous week
   - Identify optimization opportunities

5. **Generate Report**
   Present findings in this structure:

   ```
   📊 WEEKLY MARKETING PERFORMANCE REPORT
   Period: [Start Date] - [End Date]

   ═══════════════════════════════════════

   🎯 EXECUTIVE SUMMARY
   - Total Ad Spend: $X,XXX (±X% vs. last week)
   - Total Revenue: $XX,XXX (±X% vs. last week)
   - Overall ROAS: X.Xx (±X% vs. last week)
   - Total Conversions: XXX (±X% vs. last week)
   - Website Sessions: X,XXX (±X% vs. last week)

   ═══════════════════════════════════════

   💰 GOOGLE ADS PERFORMANCE

   Campaign Summary:
   [Table with columns: Campaign | Spend | Clicks | Conv. | CPA | ROAS]

   Key Metrics:
   - Average CPC: $X.XX
   - Click-Through Rate: X.X%
   - Conversion Rate: X.X%
   - Cost Per Conversion: $XX.XX

   Top Performers:
   ✅ [Campaign Name]: $XXX spend → $X,XXX revenue (X.Xx ROAS)
   ✅ [Campaign Name]: XXX conversions at $XX CPA

   Needs Attention:
   ⚠️ [Campaign Name]: High spend ($XXX), low ROAS (X.X)
   ⚠️ [Campaign Name]: Budget limiting impression share

   ═══════════════════════════════════════

   🌐 WEBSITE ANALYTICS

   Traffic Overview:
   - Total Sessions: X,XXX (±X%)
   - New Users: X,XXX (±X%)
   - Returning Users: X,XXX (±X%)
   - Average Session Duration: X:XX (±X%)
   - Bounce Rate: XX% (±X%)
   - Engagement Rate: XX% (±X%)

   Traffic Sources:
   [Table: Source/Medium | Sessions | Conv. Rate | Revenue]

   Top Landing Pages:
   1. [Page URL]: X,XXX sessions, XX% conv. rate
   2. [Page URL]: X,XXX sessions, XX% conv. rate

   Device Performance:
   - Desktop: X,XXX sessions (XX% conv. rate)
   - Mobile: X,XXX sessions (XX% conv. rate)
   - Tablet: XXX sessions (XX% conv. rate)

   Geographic Insights:
   - Top Country: [Country] with X,XXX sessions
   - Highest conversion rate: [Country] at XX%

   ═══════════════════════════════════════

   🔗 INTEGRATED INSIGHTS

   Campaign-to-Website Performance:
   [For each major campaign, show:]
   - Ad Clicks → GA Sessions (match rate: XX%)
   - Bounce Rate: XX% (benchmark: XX%)
   - Engagement quality score: X/10
   - True CPA (using GA conversions): $XX.XX

   ROI Analysis:
   - Total Marketing Investment: $XX,XXX
   - Total Revenue Generated: $XX,XXX
   - Net Profit: $XX,XXX
   - Marketing ROI: XXX%

   Attribution Insights:
   - Direct/Last-Click Conversions: XXX
   - Assisted Conversions: XXX
   - Multi-Touch Value: $XX,XXX

   ═══════════════════════════════════════

   📈 TRENDS & OBSERVATIONS

   Week-over-Week Changes:
   📊 Traffic: [Up/Down/Stable] by X%
   💰 Spend: [Up/Down/Stable] by X%
   🎯 Conversions: [Up/Down/Stable] by X%
   💵 Revenue: [Up/Down/Stable] by X%

   Notable Patterns:
   - [Observation 1]
   - [Observation 2]
   - [Observation 3]

   ═══════════════════════════════════════

   💡 RECOMMENDATIONS & ACTION ITEMS

   🎯 High Priority:
   1. [Specific action with expected impact]
   2. [Specific action with expected impact]
   3. [Specific action with expected impact]

   📋 Medium Priority:
   1. [Optimization opportunity]
   2. [Testing suggestion]
   3. [Content/UX improvement]

   🔍 Monitor Closely:
   1. [Metric or campaign to watch]
   2. [Emerging trend to track]

   ═══════════════════════════════════════

   📅 NEXT WEEK OUTLOOK

   Upcoming Events:
   - [Seasonal factors, launches, promotions]

   Budget Recommendations:
   - Suggested allocation: [breakdown by campaign]
   - Expected ROAS: X.Xx
   - Projected conversions: XXX

   Testing Priorities:
   1. [A/B test suggestion]
   2. [New targeting test]
   3. [Landing page optimization]

   ═══════════════════════════════════════
   ```

6. **Offer Deep Dives**
   After presenting the report, ask if the user wants to explore:
   - Specific campaign analysis
   - Landing page performance details
   - Audience segment insights
   - Competitive analysis
   - Extended time period comparison

## Best Practices

- **Compare to Previous Period**: Always show week-over-week changes
- **Highlight Outliers**: Call attention to significant changes (>20%)
- **Be Actionable**: Every insight should lead to a recommendation
- **Use Visual Indicators**: Emojis, arrows, or symbols for trends
- **Contextualize Numbers**: Explain what metrics mean for the business
- **Prioritize Recommendations**: High/Medium/Low priority actions
- **Set Expectations**: Quantify expected impact of recommendations

## Example Usage

```
/weekly-report
```

Or with custom date range:

```
/weekly-report for October 21-27
```

## Notes

- Report generation may take 1-2 minutes depending on data volume
- Requires both Google Ads and Analytics MCP servers to be configured
- Will automatically handle multiple ad accounts and analytics properties
- Data freshness: Ads (24-48 hours), Analytics (24-48 hours)
- For real-time data needs, ask for a current-day snapshot separately
