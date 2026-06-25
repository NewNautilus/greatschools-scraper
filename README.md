[Greatschools Scraper](https://apify.com/lulzasaur/greatschools-scraper?fpr=data)

# GreatSchools Scraper

Scrape school ratings, demographics, and contact data from [GreatSchools.org](https://www.greatschools.org/) for any US city. Returns structured data including the 1-10 GreatSchools rating, enrollment, student-teacher ratio, test scores, reviews, phone numbers, and websites.

## What data can you get?

| Field | Source | Details required? |
| --- | --- | --- |
| School name | Search | No |
| GreatSchools rating (1-10) | Search | No |
| Address, city, state, ZIP | Search | No |
| School type (public/private/charter) | Search | No |
| Grade range | Search | No |
| Enrollment | Search | No |
| Student-teacher ratio | Search | No |
| District name | Search | No |
| Test score sub-ratings | Search | No |
| Parent rating & review count | Search | No |
| Phone number | Detail | Yes |
| Website | Detail | Yes |

## Input

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQueries` | string[] | `["Los Angeles, CA"]` | City/state to search. Use "City, ST" format. |
| `maxListings` | integer | `50` | Max schools per query (1-1000). |
| `scrapeDetails` | boolean | `false` | Fetch detail pages for phone/website. Slower. |
| `schoolType` | string | `""` | Filter: `public`, `private`, `charter`, or blank for all. |
| `proxyConfiguration` | object | - | Optional proxy settings. |

### Example input

```
{
    "searchQueries": ["Los Angeles, CA", "New York, NY"],
    "maxListings": 100,
    "scrapeDetails": true,
    "schoolType": "public"
}
```

## Output

Each result contains:

```
{
    "schoolName": "L.A. County High School For The Arts",
    "gsRating": 10,
    "address": "5151 State University Drive",
    "city": "Los Angeles",
    "state": "CA",
    "zip": "90032",
    "schoolType": "public",
    "gradeRange": "9-12",
    "enrollment": 551,
    "studentTeacherRatio": 27,
    "district": "Los Angeles County Office Of Education School District",
    "phone": "(323) 343-2550",
    "website": "http://www.lachsa.net",
    "testScores": {
        "Test Scores Rating": 9,
        "College Readiness Rating": 10
    },
    "reviews": 32,
    "parentRating": 3.47,
    "sourceUrl": "https://www.greatschools.org/california/los-angeles/10927-L.A.-County-High-School-For-The-Arts/",
    "scrapedAt": "2026-04-26T12:00:00.000Z"
}
```

## Use cases

- **Real estate analysis** - Compare school quality across neighborhoods
- **Education research** - Aggregate school metrics by district, city, or state
- **Relocation planning** - Find top-rated schools in target cities
- **Policy analysis** - Track school performance and demographics at scale
- **Lead generation** - Build lists of schools with contact info

## Tips

- Without `scrapeDetails`, the scraper runs fast using search-page JSON data.
- Enable `scrapeDetails` when you need phone numbers and school websites.
- GreatSchools shows 25 schools per page. Setting `maxListings: 1000` will fetch up to 40 pages.
- Use the `schoolType` filter to narrow results before scraping.

## Cost

This actor uses pay-per-event pricing. You are charged per school result returned. Use `maxListings` to control costs.