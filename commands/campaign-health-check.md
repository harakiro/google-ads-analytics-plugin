# Campaign Health Check

Perform a comprehensive diagnostic analysis of all active Google Ads campaigns, identifying issues, opportunities, and providing prioritized optimization recommendations.

## Health Check Criteria

Evaluate campaigns across multiple dimensions:

### 1. Budget Health
- ✅ Budget pacing (on track vs. overspending/underspending)
- ✅ Daily budget exhaustion timing
- ✅ Lost impression share due to budget
- ✅ Monthly spend vs. budget allocation

### 2. Performance Health
- ✅ Click-through rate (CTR) vs. benchmarks
- ✅ Conversion rate vs. account average
- ✅ Cost per conversion trends
- ✅ ROAS vs. target thresholds
- ✅ Quality Score distribution

### 3. Engagement Health (from Analytics)
- ✅ Bounce rate by campaign
- ✅ Session duration vs. site average
- ✅ Pages per session
- ✅ Engagement rate
- ✅ Return visitor rate

### 4. Targeting Health
- ✅ Geographic performance inconsistencies
- ✅ Device performance gaps
- ✅ Ad scheduling effectiveness
- ✅ Audience segment performance

### 5. Creative Health
- ✅ Ad rotation and performance distribution
- ✅ Ad copy CTR variance
- ✅ Landing page relevance
- ✅ Extension usage and performance

### 6. Technical Health
- ✅ Conversion tracking status
- ✅ Auto-tagging verification
- ✅ Analytics integration
- ✅ Active vs. paused elements ratio

## Health Scoring System

Each campaign receives a health score (0-100) based on:

```
Health Score = Weighted average of:
- Budget Efficiency: 20%
- Performance Metrics: 30%
- Engagement Quality: 25%
- Targeting Optimization: 15%
- Technical Setup: 10%
```

**Health Tiers:**
- 🟢 **Healthy** (80-100): Performing well, minor optimizations
- 🟡 **Needs Attention** (60-79): Several issues to address
- 🟠 **Unhealthy** (40-59): Significant problems, urgent action needed
- 🔴 **Critical** (0-39): Major issues, consider pausing

## Execution Workflow

1. **Data Collection Phase**

   **From Google Ads:**
   - List all active campaigns
   - Query performance metrics (last 30 days and last 7 days for trend)
   - Get budget information
   - Identify campaign settings (targeting, bid strategies)

   **From Analytics:**
   - Sessions by campaign
   - Engagement metrics by campaign
   - Conversion rates and paths
   - Landing page performance

2. **Analysis Phase**

   For each active campaign, evaluate:

   **Budget Analysis:**
   - Daily spend pattern (consistent vs. erratic)
   - Budget exhaustion time (ideal: spread throughout day)
   - Lost impression share due to budget
   - Month-to-date pacing

   **Performance Benchmarking:**
   - CTR vs. industry benchmarks (Search: 3-5%, Display: 0.5-1%)
   - Conversion rate vs. account average
   - CPA trending (increasing = problem)
   - ROAS vs. target (typically 3-4x minimum)

   **Engagement Quality:**
   - Bounce rate (>60% = red flag)
   - Session duration (>2 min = good engagement)
   - Pages/session (>2 = engaged users)
   - Conversion path analysis

   **Comparative Analysis:**
   - Best vs. worst performing campaigns
   - Week-over-week trend analysis
   - Identify patterns and anomalies

3. **Diagnosis Phase**

   Identify specific issues:

   **Common Problems to Detect:**

   ❌ **Budget Issues:**
   - Budget-limited campaigns (losing impressions)
   - Overspending campaigns (need budget cap)
   - Inefficient spend (high cost, low return)

   ❌ **Performance Issues:**
   - Low CTR (poor ad relevance or targeting)
   - High CPC (competitive keywords, low quality score)
   - Low conversion rate (poor landing page or offer)
   - Declining ROAS (market changes, competition, seasonality)

   ❌ **Engagement Issues:**
   - High bounce rate (mismatch between ad and landing page)
   - Short session duration (poor content quality)
   - Low pages/session (navigation issues, unengaging content)

   ❌ **Targeting Issues:**
   - Geographic underperformers (wasted budget in low-ROI locations)
   - Device disparities (mobile vs. desktop performance gaps)
   - Time-of-day inefficiencies (high spend, low conversion periods)

   ❌ **Technical Issues:**
   - Conversion tracking errors
   - Auto-tagging not enabled
   - Analytics integration problems
   - Broken links or landing pages

4. **Recommendation Phase**

   Prioritize actions using this framework:

   **Priority Matrix:**
   ```
   High Impact + Easy to Fix = DO FIRST
   High Impact + Hard to Fix = PLAN & EXECUTE
   Low Impact + Easy to Fix = QUICK WINS
   Low Impact + Hard to Fix = DEPRIORITIZE
   ```

5. **Report Generation**

   Present findings in this format:

   ```
   🏥 CAMPAIGN HEALTH CHECK REPORT
   Date: [Current Date]
   Account: [Account Name]
   Period Analyzed: Last 30 Days

   ═══════════════════════════════════════

   📊 OVERALL ACCOUNT HEALTH: XX/100 [🟢/🟡/🟠/🔴]

   Active Campaigns: X
   Total Spend (30d): $XX,XXX
   Total Conversions: XXX
   Average ROAS: X.Xx

   Health Distribution:
   🟢 Healthy: X campaigns
   🟡 Needs Attention: X campaigns
   🟠 Unhealthy: X campaigns
   🔴 Critical: X campaigns

   ═══════════════════════════════════════

   🏥 CAMPAIGN-BY-CAMPAIGN ANALYSIS

   [For each campaign, sorted by health score:]

   Campaign Name: [Name]
   Health Score: XX/100 [🟢/🟡/🟠/🔴]
   Status: [Active/Limited by Budget/etc.]

   📈 Performance (Last 30 Days):
   - Spend: $X,XXX (XX% of budget)
   - Clicks: X,XXX | CTR: X.X%
   - Conversions: XXX | Conv. Rate: X.X%
   - CPA: $XX.XX | ROAS: X.Xx

   🌐 Engagement (from Analytics):
   - Sessions: X,XXX (XX% match rate)
   - Bounce Rate: XX% [vs. XX% avg]
   - Avg. Session Duration: X:XX [vs. X:XX avg]
   - Engagement Rate: XX% [vs. XX% avg]

   ⚠️ Issues Identified:
   [List specific problems found]

   💡 Recommendations:
   [Prioritized list of actions]

   Expected Impact: [Quantified improvement estimate]

   ---

   ═══════════════════════════════════════

   🚨 CRITICAL ISSUES (Immediate Action Required)

   1. [Campaign Name]: [Issue Description]
      Impact: [High/Medium] | Effort: [High/Low]
      Action: [Specific recommendation]
      Expected Result: [Outcome]

   2. [Next issue...]

   ═══════════════════════════════════════

   ⚠️ ATTENTION NEEDED (Address This Week)

   1. [Issue and recommendation]
   2. [Issue and recommendation]
   3. [Issue and recommendation]

   ═══════════════════════════════════════

   💡 OPTIMIZATION OPPORTUNITIES (When Possible)

   1. [Lower priority improvement]
   2. [Testing suggestion]
   3. [Incremental optimization]

   ═══════════════════════════════════════

   🏆 TOP PERFORMERS (What's Working Well)

   Campaign: [Best Campaign]
   Why It's Succeeding:
   - [Success factor 1]
   - [Success factor 2]
   - [Success factor 3]

   Lessons to Apply Elsewhere:
   1. [Transferable insight]
   2. [Replicable tactic]

   ═══════════════════════════════════════

   📋 ACTION PLAN SUMMARY

   🔴 This Week (Critical):
   □ [Action item 1]
   □ [Action item 2]
   □ [Action item 3]

   🟡 This Month (Important):
   □ [Action item 1]
   □ [Action item 2]
   □ [Action item 3]

   🟢 Ongoing (Continuous Improvement):
   □ [Action item 1]
   □ [Action item 2]

   ═══════════════════════════════════════

   📈 PROJECTED IMPACT

   If all recommendations implemented:
   - Expected ROAS improvement: +XX%
   - Projected additional conversions: +XX
   - Estimated additional revenue: +$X,XXX/month
   - Potential cost savings: $X,XXX/month

   ═══════════════════════════════════════
   ```

6. **Follow-up Offers**

   After presenting the health check, offer:
   - Deep dive into specific problematic campaigns
   - A/B testing plans for underperformers
   - Budget reallocation scenario modeling
   - Landing page optimization guidance
   - Competitive analysis for specific campaigns

## Diagnostic Rules

### Budget Health Rules

```
IF daily spend exhausted before 6 PM → Budget too low
IF impression share lost to budget > 20% → Increase budget
IF spend < 80% of monthly budget by day 25 → Budget underutilized
IF spend > 110% of monthly budget by day 25 → Risk of overspend
```

### Performance Health Rules

```
IF CTR < 2% (Search) OR < 0.5% (Display) → Poor ad relevance
IF conversion rate < 2% → Landing page or offer issue
IF CPA increasing >20% week-over-week → Investigate immediately
IF ROAS < 2.0 → Consider pausing or restructuring
IF quality score < 5 → Keyword/ad/landing page relevance issues
```

### Engagement Health Rules

```
IF bounce rate > 70% → Ad/page mismatch
IF avg. session < 1 min → Poor content or wrong audience
IF pages/session < 1.5 → Navigation or content issues
IF engagement rate < 50% → Overall experience problems
```

### Trend Health Rules

```
IF metric declining >15% week-over-week → Urgent attention
IF metric declining >30% month-over-month → Critical issue
IF metric volatile (std dev > 40% of mean) → Instability
```

## Example Usage

```
/campaign-health-check
```

For specific account:

```
/campaign-health-check for [account name]
```

For specific campaigns only:

```
/campaign-health-check for campaigns matching "brand"
```

## Best Practices

- **Run Weekly**: Catch issues early before significant budget waste
- **Baseline First**: Establish benchmarks in first month
- **Track Changes**: Monitor health scores over time
- **Act on Criticals**: Don't delay on red-flag issues
- **Celebrate Wins**: Acknowledge and replicate what's working
- **Document**: Keep record of changes and their impacts

## Notes

- Analysis covers last 30 days by default
- Compares to previous 30-day period for trends
- Health scores are relative to account average and industry benchmarks
- Requires both Google Ads and Analytics data for complete analysis
- Report generation typically takes 2-3 minutes for full analysis
- Some recommendations may not be actionable due to read-only MCP access (will be noted)
