[Greatschools Scraper](https://apify.com/fortuitous_pirate/greatschools-scraper?fpr=data)

# GreatSchools K-12 Ratings Scraper

## Overview

Extract K-12 school ratings, test scores, and demographics from GreatSchools. org. Search 200,000+ schools by ZIP code, city, or address.

## Features

- Search by keywords to find specific results
- Filter results by category or type
- Export data in JSON, CSV, or Excel formats
- Includes ratings and review data
- Includes location and address data
- Built-in proxy support for reliable data collection

## Use Cases

- **Aggregate** - Aggregate academic papers and research data
- **Build** - Build course catalogs and educational resource databases
- **Track** - Track educational institution data and rankings
- **Monitor** - Monitor academic publishing trends

## Input Parameters

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `searchQueries` | array **(required)** | List of zip codes, cities, or addresses to search for schools. Example: ['902... | `[]` |
| `schoolTypes` | array | Filter by school type. Leave empty for all types. | `[]` |
| `gradeLevels` | array | Filter by grade level. Leave empty for all grades. | `[]` |
| `maxResultsPerSearch` | integer | Maximum number of schools to return per search query. | `50` |
| `includeDetails` | boolean | Fetch additional details for each school (slower but more data including subr... | true |
| `proxyConfiguration` | object | Proxy settings for requests. Recommended for high volume scraping. | `{...}` |

## Output Example

Each result contains structured data like this:

```
{
  "schoolId": "ABC-12345",
  "name": "GreatSchools K-12 Ratings Sample Item",
  "gsRating": 4.5,
  "address": "123 Main St",
  "schoolType": "Sample schoolType",
  "levelCode": "Sample levelCode",
  "gradeRange": "Sample gradeRange",
  "districtName": "GreatSchools K-12 Ratings Sample Item",
  "enrollment": "Sample enrollment",
  "studentsPerTeacher": "Sample studentsPerTeacher",
  "parentRating": 4.5,
  "numReviews": 127
}
```

## Pricing

This actor uses pay-per-result pricing:

- **$0.003** per result
- **$3.00** per 1,000 results

No monthly fees. You only pay for what you scrape. [Apify Free plan](https://apify.com/pricing) includes $5/month in platform credits.

## How to Run

### Apify Console

1. Go to the [GreatSchools K-12 Ratings Scraper](https://apify.com/fortuitous_pirate/greatschools-scraper) actor page
2. Configure your input parameters
3. Click **Start** and wait for the results
4. Download data in JSON, CSV, or Excel format

### API

```
curl -X POST "https://api.apify.com/v2/acts/fortuitous_pirate~greatschools-scraper/runs?token=YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"maxItems": 10}'
```

### Python SDK

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("fortuitous_pirate/greatschools-scraper").call(
    run_input={"maxItems": 10}
)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Integration

Connect GreatSchools K-12 Ratings Scraper with your existing tools and workflows:

- **API access** - Programmatic access via [Apify API](https://docs.apify.com/api/v2)
- **Webhooks** - Get notified when scraping completes
- **Scheduling** - Set up recurring runs on any schedule
- **Zapier / Make** - Connect with 5,000+ apps via [Apify integrations](https://apify.com/integrations)
- **Python / Node.js SDKs** - Native client libraries for easy integration