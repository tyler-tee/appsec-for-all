# AppSec for All

**Application Security (AppSec) Simplified**

This repository demonstrates how to automate Application Security workflows using **SonarCloud**, **Airtable**, and **Tines**. By combining these tools, you can streamline your AppSec operations, uncover insights, and save time—all using free-tier tools.

## How It Works

1. **SonarCloud** scans your code for bugs, vulnerabilities, and code smells.  
2. **Airtable** organizes and visualizes metrics, trends, and insights.  
3. **Tines** automates the entire process, from repository onboarding to data syncing.

---

## Setup Instructions

1. **Sign up for SonarCloud**  
   - Add your organization and onboard your repositories.
   - Use the free tier for public repositories to enable static application security testing (SAST).

2. **Import the Tines Story**  
   - Download and import the story: [appsec-manager.json](https://github.com/tyler-tee/appsec-for-all/blob/main/tines/appsec-manager.json).  
   - Configure your API tokens for SonarCloud, Airtable, and GitHub.

3. **Clone the Airtable Base**  
   - Use our publicly available base: [AppSec Manager Base](https://airtable.com/appylGfyt8KM9IaoY/shr3qoQTZ4xFQCCev).  
   - Organize metrics across four key tables:  
     - **Project Metrics**: Snapshot of overall health.  
     - **Trends**: Historical data for deltas in bugs, vulnerabilities, and code smells.  
     - **Issues**: Detailed problem inventory by severity and type.  
     - **Security Insights**: Focus on vulnerabilities and security hotspots.

---

## Key Features

### 1. **SonarCloud Integration**
- Automatically analyze public GitHub repositories using SonarCloud’s free tier.  
- Add Quality Gate badges to repository READMEs using the GitHub API.  
- Example badge integration script:  

```bash
curl -X PUT \
  "https://api.github.com/repos/<username>/<repository>/contents/README.md" \
  -H "Authorization: token <<YOUR_GITHUB_TOKEN>>" \
  -d '{
    "message": "Add SonarCloud Quality Gate Badge",
    "content": "<BASE64_ENCODED_README>",
    "sha": "<CURRENT_FILE_SHA>"
  }'
```

### 2. **Airtable Metrics and Dashboards**
- Store, track, and visualize AppSec metrics.  
- Sync metrics dynamically using Airtable’s API.  
- Example API call for syncing data:  

```bash
curl -X POST \
  "https://api.airtable.com/v0/<base_id>/<table_name>" \
  -H "Authorization: Bearer <<YOUR_AIRTABLE_API_KEY>>" \
  -H "Content-Type: application/json" \
  -d '{
    "records": [
      {
        "fields": {
          "Project Name": "My Project",
          "Bugs": 5,
          "Vulnerabilities": 1,
          "Code Smells": 12
        }
      }
    ]
  }'
```

### 3. **Tines Automation**
- Automate repository onboarding and configuration via SonarCloud’s APIs.  
- Extract metrics, calculate deltas, and sync data to Airtable seamlessly.  
- Example metric delta calculation:  

```json
{
  "current_metrics": {
    "Bugs": 10,
    "Vulnerabilities": 2
  },
  "previous_metrics": {
    "Bugs": 12,
    "Vulnerabilities": 3
  },
  "output": {
    "Bug Delta": -2,
    "Vulnerability Delta": -1
  }
}
```

---

## Results

With SonarCloud analyzing code, Airtable structuring metrics, and Tines automating workflows, this system:
- Scans code for actionable insights.
- Tracks metrics and trends over time.
- Reduces manual effort while ensuring accuracy.

---

## Get Started Today

1. [Sign up for SonarCloud](https://sonarcloud.io).  
2. [Import the Tines story](https://github.com/tyler-tee/appsec-for-all/blob/main/tines/appsec-manager.json).  
3. [Clone the Airtable base](https://airtable.com/appylGfyt8KM9IaoY/shr3qoQTZ4xFQCCev).  

For questions or contributions, feel free to [open an issue](https://github.com/tyler-tee/appsec-for-all/issues).  

Happy automating! 🚀
