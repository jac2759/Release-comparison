# Release Comparison Test Repository

This repository is designed to test the screenshot comparison workflow without affecting the main assessments-ui repository.

## 🎯 Purpose

- **Test screenshot comparison** workflow in isolation
- **Validate Slack notifications** and HTML reports
- **Debug workflow issues** without production impact
- **Experiment with different URLs** and configurations

## 🚀 Quick Start

### 1. Set Up Slack Webhook

1. Go to your Slack workspace
2. Create a new app or use an existing one
3. Enable Incoming Webhooks
4. Create a webhook URL
5. Add the webhook URL as a repository secret named `SLACK_WEBHOOK_URL`

### 2. Deploy Test Page

Deploy the `index.html` file to any hosting service:
- **GitHub Pages** (recommended)
- **Netlify**
- **Vercel**
- **Any static hosting**

### 3. Run the Test

1. Go to **Actions** tab in this repository
2. Click **Test Screenshot Comparison**
3. Click **Run workflow**
4. Fill in the form:
   - **Test URL**: Your deployed test page URL
   - **Threshold**: 20 (default)
   - **Environment**: test-environment
   - **Contract**: test-contract
   - **Build Mode**: Test

## 📋 Test Scenarios

### Scenario 1: First Run (Baseline)
- **URL**: Your test page URL
- **Expected**: Creates baseline screenshot, no Slack notification

### Scenario 2: Same URL (No Changes)
- **URL**: Same test page URL
- **Expected**: 0% difference, no Slack notification

### Scenario 3: Different URL (Changes)
- **URL**: Different website (e.g., https://example.com)
- **Expected**: High difference percentage, Slack notification sent

### Scenario 4: Modified Test Page
- **URL**: Modified version of your test page
- **Expected**: Moderate difference, Slack notification if exceeds threshold

## 🔧 Configuration

### Workflow Inputs

| Input | Description | Default |
|-------|-------------|---------|
| `test_url` | URL to test | https://example.com |
| `threshold` | Difference threshold % | 20 |
| `environment` | Environment name | test-environment |
| `contract` | Contract name | test-contract |
| `build_mode` | Build mode | Test |

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `SLACK_WEBHOOK_URL` | Slack webhook URL | Yes (for notifications) |

## 📊 What You'll Get

### GitHub Actions
- **Screenshot artifacts** (30-day retention)
- **HTML report artifacts** (30-day retention)
- **Difference images** (30-day retention)
- **Detailed step summaries**

### Slack Notifications
- **Main alert** with deployment details
- **Report notification** with GitHub Actions link
- **Rich formatting** with buttons and context

### HTML Reports
- **Side-by-side comparison** of screenshots
- **Visual difference overlay** with legend
- **Detailed metrics** and analysis
- **GitHub-style dark theme**

## 🧪 Testing Different Scenarios

### Test with Different Thresholds
```yaml
# Low threshold (5%) - more sensitive
threshold: 5

# High threshold (50%) - less sensitive  
threshold: 50
```

### Test with Different URLs
```yaml
# Same site, different pages
test_url: https://yoursite.com/page1
test_url: https://yoursite.com/page2

# Completely different sites
test_url: https://google.com
test_url: https://github.com
```

### Test with Different Environments
```yaml
environment: staging
contract: test-contract
build_mode: Assessment

environment: production  
contract: bhb
build_mode: Referral
```

## 🔍 Troubleshooting

### No Slack Notifications
- Check `SLACK_WEBHOOK_URL` secret is set
- Verify webhook URL is correct
- Check Slack app permissions

### No Previous Screenshot
- First run creates baseline (expected)
- Subsequent runs will compare against baseline

### High Difference Percentage
- Expected for different URLs
- Adjust threshold if needed
- Check if test page is loading correctly

### Workflow Fails
- Check URL is accessible
- Verify Node.js dependencies
- Check GitHub Actions logs

## 📁 Repository Structure

```
Release-comparison/
├── .github/
│   └── workflows/
│       ├── screenshot-comparison-advanced.yml  # Main workflow
│       └── test-screenshot-comparison.yml      # Test trigger
├── index.html                                  # Test page
└── README.md                                   # This file
```

## 🎨 Customizing the Test Page

Edit `index.html` to:
- **Change colors** and styling
- **Add/remove elements** to test different layouts
- **Modify content** to create intentional differences
- **Add dynamic elements** (timestamps, counters, etc.)

## 🔄 Integration with Main Repository

Once tested here, the workflow can be:
1. **Copied to assessments-ui** repository
2. **Integrated with existing workflows**
3. **Used in production** with confidence

## 📞 Support

If you encounter issues:
1. Check the GitHub Actions logs
2. Verify all secrets are set correctly
3. Test with simple URLs first (e.g., https://example.com)
4. Check Slack webhook permissions

---

**Happy Testing! 🚀**
