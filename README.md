[Greatschools Scraper](https://apify.com/parseforge/greatschools-scraper?fpr=data)

![ParseForge Banner](https://images.apifyusercontent.com/wTxwbnRh8X878EoDysptDr1AzClsoPHSsuMaYGmWENw/w:1800/cb:1/aHR0cHM6Ly9naXRodWIuY29tL1BhcnNlRm9yZ2UvYXBpZnktYXNzZXRzL2Jsb2IvYWQzNWNjYzEzZGRkMDY4YjlkNmNiYTMzZjMyMzk2MmUzOWFlZDViMi9iYW5uZXIuanBnP3Jhdz10cnVl.webp)

# 🎓 GreatSchools Scraper

> 🚀 **Export school ratings, demographics, and principal contact info in seconds.** Search **every school in the U.S.** by city, state, level, or type. No API key, no registration, no manual research.

> 🕒 **Last updated:** 2026-04-23 · **📊 47 fields** per school · **🇺🇸 All US states** · **⭐ Ratings & demographics** · **📞 Principal contact** · **🚫 No auth** required

The **GreatSchools Scraper** exports structured records from GreatSchools.org and returns **47 fields per school**, including ratings, test scores, demographics, enrollment, principal contact details, website, phone, and street address. GreatSchools is the most-cited U.S. K-12 rating source, feeding school data into Zillow, Redfin, Realtor.com, and Trulia listings.

Coverage spans **all 50 states plus D.C.**, with public, charter, and private schools across pre-K, elementary, middle, and high school levels. This Actor makes that data downloadable as CSV, Excel, JSON, or XML in under five minutes. All filters run server-side, so you skip the parser engineering entirely.

| 🎯 Target Audience | 💡 Primary Use Cases |
| --- | --- |
| Real estate agents, relocation services, parents, school district analysts, EdTech platforms, researchers, journalists | Neighborhood scoring, relocation reports, school lead lists, market research, demographics analysis, principal outreach |

---

## 📋 What the GreatSchools Scraper does

Two input modes, one clean output:

- 📍 **Location search.** Enter a city and state (e.g. `Orlando, FL`) and filter by school level and type.
- 🔗 **Direct URL.** Paste any GreatSchools.org search or listing URL for custom queries already configured in the browser.
- 🏫 **Level filter.** Pre-K, elementary, middle, or high school. Combine freely or leave empty for all.
- 🏷️ **Type filter.** Public, charter, or private. Mix and match across one run.
- 📞 **Principal contact.** Each record includes principal name, email, phone, and school website when published.

Each school record ships with ratings, test scores, student-teacher ratio, enrollment, racial and income demographics, discipline data, and awards such as the College Success Award and Thrive Award.

> 💡 **Why it matters:** school quality is the top factor in U.S. residential property values. Pulling this data by hand means clicking through tens of thousands of profiles. This Actor skips all of that and keeps your dataset fresh on every run.

---

## 🎬 Full Demo

*🚧 Coming soon: a 3-minute walkthrough showing how to go from sign-up to a downloaded dataset.*

---

## ⚙️ Input

| Input | Type | Default | Behavior |
| --- | --- | --- | --- |
| `maxItems` | integer | `10` | Records to return. Free plan caps at 100, paid plan at 1,000,000. |
| `location` | string | `"Oklahoma City, OK"` | City and state. Mutually exclusive with `startUrl`. |
| `startUrl` | string | `null` | Any greatschools.org URL. Bypasses the location input. |
| `schoolLevels` | array | `[]` | Any of `prek`, `elementary`, `middle`, `high`. Empty = all levels. |
| `schoolTypes` | array | `[]` | Any of `public`, `charter`, `private`. Empty = all types. |

**Example: 50 public and charter high schools in San Francisco.**

```
{
    "maxItems": 50,
    "location": "San Francisco, CA",
    "schoolLevels": ["high"],
    "schoolTypes": ["public", "charter"]
}
```

**Example: custom search via URL.**

```
{
    "maxItems": 100,
    "startUrl": "https://www.greatschools.org/best-schools/california/san-francisco?st[]=public&st[]=charter"
}
```

> ⚠️ **Good to Know:** principal email, phone, and school website are pulled from individual profile pages, so these fields populate only when GreatSchools has published contact information for that specific school. Small private schools often omit these fields.

---

## 📊 Output

Each school record contains **47 fields**. Download the dataset as CSV, Excel, JSON, or XML.

### 🧾 Schema

| Field | Type | Example |
| --- | --- | --- |
| 🆔 `id` | string | `"6523"` |
| 🏢 `name` | string | `"Abraham Lincoln High School"` |
| 🔗 `url` | string | `"https://www.greatschools.org/california/..."` |
| 🏷️ `schoolType` | string | `"public"` |
| 🎓 `gradeLevels` | string | `"9-12"` |
| 🏛️ `district_id` | string | null | `"5441"` |
| 🏫 `district_name` | string | null | `"San Francisco Unified"` |
| 🏙️ `district_city` | string | null | `"San Francisco"` |
| 📮 `contact_street` | string | `"2162 24th Ave"` |
| 🏙️ `contact_city` | string | `"San Francisco"` |
| 🗺️ `contact_state` | string | `"CA"` |
| 📫 `contact_zip` | string | `"94116"` |
| 📞 `contact_phone` | string | null | `"(415) 469-4680"` |
| 🌐 `contact_website` | string | null | `"https://lincoln.sfusd.edu"` |
| 📘 `contact_facebook` | string | null | `null` |
| 👤 `principal` | string | null | `"Jane Smith"` |
| 📧 `principal_email` | string | null | `"smithj@sfusd.edu"` |
| ⭐ `rating` | number | `8` |
| 🔢 `rating_scale` | string | `"Above average"` |
| 📝 `reviews_totalCount` | number | `142` |
| 📊 `reviews_averageRating` | number | `4.3` |
| 👥 `enrollment_total` | number | `2080` |
| 🌍 `enrollment_demographics` | array | `[{ "demo_group": "Asian", "demo_percentage": 72 }]` |
| 📈 `studentProgressRating` | number | null | `7` |
| 📚 `testScoresRating` | number | null | `8` |
| ⚖️ `equityRating` | number | null | `6` |
| 🏆 `coursesAndPrograms` | array | `["College Success Award"]` |
| 🧪 `testScores` | array | `[{ "test_subject": "Math", "test_proficiencyPercentage": 80 }]` |
| 💰 `lowIncome_percentage` | number | null | `42.5` |
| 🏷️ `lowIncome_performanceLabel` | string | null | `"42.5%"` |
| 🌐 `raceEthnicity_summary` | string | `"Asian: 72%, Hispanic: 12%"` |
| 📊 `raceEthnicity_data` | array | `[{ "race_group": "Asian", ... }]` |
| 🚷 `discipline_suspensions` | object | null | `{ "rate": "1.2%" }` |
| 📉 `discipline_absences` | object | null | `{ "rate": "5.4%" }` |
| 🏘️ `nearbySchools` | array | `[]` |
| 📍 `latitude` | number | `37.7475` |
| 📍 `longitude` | number | `-122.481` |
| 📏 `distance` | number | `2.3` |
| 👨‍🏫 `studentsPerTeacher` | number | `24` |
| 🎖️ `csaAwardYears` | array | `[2023, 2024]` |
| 🌟 `thriveAwardYears` | array | `[2024]` |
| ✅ `equityIndicator` | boolean | `true` |
| 🎓 `collegePersistentData` | object | null | `{ ... }` |
| 🏛️ `collegeEnrollmentData` | object | null | `{ ... }` |
| 🧮 `subratings` | object | `{ "Test Scores Rating": 8 }` |
| 🛠️ `remediationData` | object | null | `{ ... }` |
| 🕒 `scrapedTimestamp` | ISO 8601 | `"2026-04-21T00:00:00.000Z"` |

### 📦 Sample records

 
 
 

---

## ✨ Why choose this Actor

|  | Capability |
| --- | --- |
| 🇺🇸 | **National coverage.** Every public, charter, and private K-12 school in the 50 states plus D.C. |
| 📞 | **Contact enrichment.** Principal name, email, school phone, website, and Facebook pulled from each school profile. |
| 📊 | **47 fields per school.** Ratings, test scores, enrollment, demographics, discipline, awards, and geo in a single record. |
| ⚡ | **Fast.** 10 schools in under 10 seconds, 1,000 records in about 3 minutes. |
| 🔁 | **Always fresh.** Every run hits GreatSchools live, so your dataset reflects today's ratings and demographics. |
| 🚫 | **No authentication.** Works with publicly listed school data. No login or API key needed. |
| 🧩 | **Flexible input.** Location-based search or any existing GreatSchools URL, including faceted filters. |

> 📊 Accurate school data is the single largest driver of residential property value in the U.S. and the foundation of every relocation, redlining, and EdTech product.

---

## 📈 How it compares to alternatives

| Approach | Cost | Coverage | Refresh | Filters | Setup |
| --- | --- | --- | --- | --- | --- |
| **⭐ GreatSchools Scraper** *(this Actor)* | $5 free credit, then pay-per-use | **Every U.S. K-12 school** | **Live per run** | Location, level, type, URL | ⚡ 2 min |
| State DOE CSV exports | Free | One state at a time | Yearly | Basic | 🐢 Days |
| Commercial EdTech data vendors | $5,000+/year | National | Quarterly | Many | ⏳ Weeks |
| Manual GreatSchools copy-paste | Free | Tiny samples | Stale immediately | None | 🕒 Hours per city |

Pick this Actor when you want national coverage, live refresh, and no pipeline maintenance.

---

## 🚀 How to use

1. 📝 **Sign up.** [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=vmoqkp) (takes 2 minutes).
2. 🌐 **Open the Actor.** Go to the GreatSchools Scraper page on the Apify Store.
3. 🎯 **Set input.** Enter a city and state, pick school levels and types, and set `maxItems`.
4. 🚀 **Run it.** Click **Start** and let the Actor collect your data.
5. 📥 **Download.** Grab your results in the **Dataset** tab as CSV, Excel, JSON, or XML.

> ⏱️ Total time from signup to downloaded dataset: **3-5 minutes.** No coding required.

---

## 💼 Business use cases

| ### 🏡 Real Estate & Relocation     - School-quality overlays on MLS listings - Neighborhood scoring for buyer reports - Relocation packets with local school profiles - Lead lists for family-oriented agents | ### 👨‍👩‍👧 Parents & Families     - Side-by-side school comparison sheets - Filter by rating, demographics, or test scores - Principal contact for tour requests - Commute-ready dataset with lat/lon |
| --- | --- |
| ### 📚 EdTech & Outreach     - Lead lists for curriculum and SaaS sales - Principal email outreach campaigns - Market sizing by district and state - Partnership scouting by school type | ### 🔬 Researchers & Journalists     - Equity and demographic analyses - Test score and discipline correlations - Longitudinal datasets via scheduled runs - District-level aggregation and reporting |

---

## 🌟 Beyond business use cases

Data like this powers more than commercial workflows. The same structured records support research, education, civic projects, and personal initiatives.

| ### 🎓 Research and academia     - Empirical datasets for papers, thesis work, and coursework - Longitudinal studies tracking changes across snapshots - Reproducible research with cited, versioned data pulls - Classroom exercises on data analysis and ethical scraping | ### 🎨 Personal and creative     - Side projects, portfolio demos, and indie app launches - Data visualizations, dashboards, and infographics - Content research for bloggers, YouTubers, and podcasters - Hobbyist collections and personal trackers |
| --- | --- |
| ### 🤝 Non-profit and civic     - Transparency reporting and accountability projects - Advocacy campaigns backed by public-interest data - Community-run databases for local issues - Investigative journalism on public records | ### 🧪 Experimentation     - Prototype AI and machine-learning pipelines with real data - Validate product-market hypotheses before engineering spend - Train small domain-specific models on niche corpora - Test dashboard concepts with live input |

## 🔌 Automating GreatSchools Scraper

Control the scraper programmatically for scheduled runs and pipeline integrations:

- 🟢 **Node.js.** Install the `apify-client` NPM package.
- 🐍 **Python.** Use the `apify-client` PyPI package.
- 📚 See the [Apify API documentation](https://docs.apify.com/api/v2) for full details.

The [Apify Schedules feature](https://docs.apify.com/platform/schedules) lets you trigger this Actor on any cron interval. Hourly, daily, or weekly refreshes keep downstream databases in sync automatically.

---

## 🤖 Ask an AI assistant about this scraper

Open a ready-to-send prompt about this ParseForge actor in the AI of your choice:

- 💬 [**ChatGPT**](https://chat.openai.com/?q=How%20do%20I%20use%20the%20GreatSchools%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🧠 [**Claude**](https://claude.ai/new?q=How%20do%20I%20use%20the%20GreatSchools%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🔍 [**Perplexity**](https://perplexity.ai/search?q=How%20do%20I%20use%20the%20GreatSchools%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)
- 🅒 [**Copilot**](https://copilot.microsoft.com/?q=How%20do%20I%20use%20the%20GreatSchools%20Scraper%20by%20ParseForge%20on%20Apify%3F%20Show%20me%20input%20examples%2C%20output%20fields%2C%20common%20use%20cases%2C%20and%20how%20to%20integrate%20it%20into%20a%20workflow.)

---

## ❓ Frequently Asked Questions

### 🧩 How does it work?

Enter a city and state, pick school levels and types, click Start, and the Actor queries GreatSchools.org directly, visits each school profile for enrichment, and emits a clean structured record per school. No browser automation, no captchas, no setup.

### 📏 How accurate is the data?

Ratings, test scores, demographics, and enrollment come straight from GreatSchools, which aggregates state DOE reports and federal data. Principal contact details depend on what each school publishes on its GreatSchools profile. Small private schools sometimes omit email and phone.

### 🔁 How often is the dataset refreshed?

GreatSchools updates ratings annually after new state test results are released (typically late summer to fall). Every run of this Actor fetches the latest published data, so your dataset reflects the current state of the site at run time.

### 🇺🇸 Does it cover all 50 states?

Yes. GreatSchools catalogs every public and charter school in the 50 states plus D.C., along with most private schools. This Actor can search any U.S. city or zip code.

### 📞 Can I get principal email addresses?

Yes, when GreatSchools publishes them on the school profile. Coverage is strongest for public schools in mid-sized and larger districts. Private and very small schools sometimes omit contact info.

### ⏰ Can I schedule regular runs?

Yes. Use Apify Schedules to run this Actor on any cron interval (hourly, daily, weekly) and keep a downstream database in sync.

### ⚖️ Is this data legal to use?

This Actor collects only publicly listed information on GreatSchools.org profile pages. You are responsible for complying with applicable terms of service and for any downstream regulatory requirements in your own product.

### 💼 Can I use this data commercially?

Yes, for internal research, lead scoring, and relocation reports. Review the GreatSchools terms of use before publishing the raw dataset or using it for automated outreach at scale.

### 💳 Do I need a paid Apify plan to use this Actor?

No. The free Apify plan is enough for testing and small runs (up to 100 records per run). A paid plan lifts the limit and gives you access to scheduling, higher concurrency, and larger datasets.

### 🔁 What happens if a run fails or gets interrupted?

Apify automatically retries transient errors. If a run still fails, you can inspect the log in the Runs tab, fix the input, and re-run. Partial datasets from failed runs are preserved so you never lose progress.

### 🏫 What if I need district-level aggregates?

This Actor returns school-level records with district identifiers attached, so you can group and aggregate in SQL, pandas, or a spreadsheet. For a pre-aggregated district scraper, reach out via the contact form below.

### 🆘 What if I need help?

Our support team is here to help. Contact us through the Apify platform or use the Tally form linked below.

---

## 🔌 Integrate with any app

GreatSchools Scraper connects to any cloud service via [Apify integrations](https://apify.com/integrations):

- [**Make**](https://docs.apify.com/platform/integrations/make) - Automate multi-step workflows
- [**Zapier**](https://docs.apify.com/platform/integrations/zapier) - Connect with 5,000+ apps
- [**Slack**](https://docs.apify.com/platform/integrations/slack) - Get run notifications in your channels
- [**Airbyte**](https://docs.apify.com/platform/integrations/airbyte) - Pipe school data into your warehouse
- [**GitHub**](https://docs.apify.com/platform/integrations/github) - Trigger runs from commits and releases
- [**Google Drive**](https://docs.apify.com/platform/integrations/drive) - Export datasets straight to Sheets

You can also use webhooks to trigger downstream actions when a run finishes. Push fresh school data into your CRM, or alert your team in Slack.

---

## 🔗 Recommended Actors

- [**🏠 Realtor.com Scraper**](https://apify.com/parseforge/realtor-com-scraper) - U.S. home listings with prices, beds, and school districts
- [**🏡 Zillow Scraper**](https://apify.com/parseforge/zillow-scraper) - Zestimates, sold history, and listing details
- [**🔴 Redfin Scraper**](https://apify.com/parseforge/redfin-scraper) - MLS-backed listings and market stats
- [**🏘️ Trulia Scraper**](https://apify.com/parseforge/trulia-scraper) - Neighborhood insights and local school data
- [**🏢 Apartments.com Scraper**](https://apify.com/parseforge/apartments-com-scraper) - Rental listings with amenities and rent history

> 💡 **Pro Tip:** browse the complete [ParseForge collection](https://apify.com/parseforge) for more real estate and reference-data scrapers.

---

**🆘 Need Help?** [**Open our contact form**](https://tally.so/r/BzdKgA) to request a new scraper, propose a custom data project, or report an issue.

---

> **⚠️ Disclaimer:** this Actor is an independent tool and is not affiliated with, endorsed by, or sponsored by GreatSchools.org or any of its partners. All trademarks mentioned are the property of their respective owners. Only publicly available school data is collected.