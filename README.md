# Wazobia FM News Scraper
coming soon---

A comprehensive web scraper for extracting news articles from Wazobia FM (https://www.wazobiafm.com), Nigeria's Number One indigenous Radio Station. The scraper handles Nigerian Pidgin English content across multiple news categories and regional sections.

## 🎯 Features

- **Multi-Section Scraping**: Automatically extracts articles from all Wazobia FM news sections
- **Regional Coverage**: Supports content from Lagos, Abuja, Kano, Onitsha, and Port Harcourt
- **Content Categories**: Handles News, Hot Tori, Editorial, Music Gist, and more
- **Multiple Extraction Methods**: JSON-LD, HTML selectors, and fallback extraction
- **Pidgin-Optimized**: Specialized text cleaning for Nigerian Pidgin English
- **Data Analysis**: Built-in visualization and statistical analysis
- **Multiple Export Formats**: JSON, CSV, and Excel output
- **Jupyter Notebook Ready**: Interactive analysis and visualization

## 📦 Installation

1. **Clone or download the project files**

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Start Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

4. **Open `wazobia_scraper_notebook.ipynb`**

## 🔧 Configuration

The scraper uses `config.yml` for all configuration settings:

### Key Configuration Sections:

- **`site_config`**: Base URL, user agent, rate limiting
- **`wazobia_fm_urls`**: News sections and content categories
- **`article_selectors`**: CSS selectors for content extraction
- **`content_filters`**: Content validation and filtering rules
- **`output`**: Export format and field specifications

### Customizing the Configuration:

```yaml
site_config:
  base_url: "https://www.wazobiafm.com"
  delay_between_requests: 2  # Adjust scraping speed
  timeout: 30

content_filters:
  min_content_length: 100  # Minimum article length
  max_content_length: 50000  # Maximum article length
```

## 🚀 Quick Start

### 1. Basic Usage (Jupyter Notebook)

```python
# Run complete demo
wazobia_demo = quick_start_wazobia_fm()

# Custom scraping
scraper = run_wazobia_fm_scraping(max_articles=25)

# Analyze results
analyze_scraped_data(scraper)

# Export data
export_to_json(scraper, "my_articles.json")
export_to_csv(scraper, "my_articles.csv")
```

### 2. Advanced Usage

```python
# Initialize scraper with custom config
scraper = WazobiaScraper()

# Scrape from all sections
articles = scraper.scrape_articles(
    max_articles=50, 
    scrape_all_sections=True
)

# Scrape from specific URL
articles = scraper.scrape_articles(
    start_url="https://www.wazobiafm.com/lagos/news/",
    max_articles=20,
    scrape_all_sections=False
)

# Get DataFrame for analysis
df = scraper.get_dataframe()
print(df.head())

# Get statistics
stats = scraper.get_statistics()
print(stats)
```

## 📊 Data Structure

Each scraped article contains:

```python
{
    "title": "Article headline",
    "content": "Full article text in Pidgin English",
    "author": "Author name (if available)",
    "date": "Publication date",
    "url": "Article URL",
    "tags": ["tag1", "tag2"],
    "images": ["image_url1", "image_url2"],
    "scraped_at": "2025-01-23T10:30:00",
    "content_length": 1250,
    "category": "hottori"
}
```

## 📈 Built-in Analytics

The scraper includes comprehensive data analysis features:

### Visualizations:
- Content length distribution
- Author availability charts
- Tag and image count analysis
- Word clouds of article titles
- Content category breakdowns

### Statistics:
- Total articles scraped
- Average content length
- Articles with authors/dates
- Unique authors count
- Content category distribution

## 🗂️ Content Categories

Wazobia FM content is organized into:

- **News**: General news and current affairs
- **Hot Tori**: Breaking news and trending stories
- **Editorial**: Opinion pieces and analysis
- **Music Gist**: Entertainment and music industry news
- **Newspaper Tori**: Traditional newspaper-style content
- **Una Wake Up Show**: Morning show segments

## 🌍 Regional Sections

Content is available from:
- **Lagos**: `/lagos/news/`
- **Abuja**: `/abuja/news/`
- **Kano**: `/kano/news/`
- **Onitsha**: `/onitsha/news/`
- **Port Harcourt**: `/port-harcourt/news/`

## 📁 Output Formats

### JSON Export
```json
[
  {
    "title": "Example Article Title",
    "content": "Article content in Pidgin English...",
    "author": "Author Name",
    "date": "2025-01-23",
    "url": "https://www.wazobiafm.com/...",
    "tags": ["politics", "nigeria"],
    "images": ["https://..."],
    "scraped_at": "2025-01-23T10:30:00",
    "content_length": 850
  }
]
```

### CSV Export
Flattened structure with comma-separated tags and images.

### Excel Export
Multi-sheet workbook with articles data and statistics.

## ⚙️ Customization

### Adding New Selectors
Edit `config.yml` to add new CSS selectors:

```yaml
article_selectors:
  title:
    - "h1.custom-title"
    - ".new-title-class"
```

### Modifying Content Filters
Adjust content validation rules:

```yaml
content_filters:
  min_content_length: 50  # Shorter articles
  exclude_selectors:
    - ".advertisement"
    - ".custom-ads"
```

### Rate Limiting
Control scraping speed:

```yaml
site_config:
  delay_between_requests: 3  # 3 seconds between requests
  timeout: 45  # 45 second timeout
```

## 🛠️ Troubleshooting

### Common Issues:

1. **No articles found**:
   - Check internet connection
   - Verify Wazobia FM website is accessible
   - Try reducing `max_articles` parameter

2. **Rate limiting errors**:
   - Increase `delay_between_requests` in config
   - Reduce `max_articles` per session

3. **Content extraction issues**:
   - Website structure may have changed
   - Update CSS selectors in `config.yml`
   - Check for new content categories

### Debug Mode:
Enable detailed logging in the notebook for troubleshooting.

## 📝 File Structure

```
wazobia-fm-scraper/
├── config.yml                    # Configuration file
├── requirements.txt               # Python dependencies
├── README.md                     # This file
├── wazobia_scraper_notebook.ipynb # Main Jupyter notebook
└── output/                       # Generated files
    ├── wazobia_fm_articles.json
    ├── wazobia_fm_articles.csv
    └── wazobia_scraper.log
```

## 🔄 Updates and Maintenance

The scraper is designed to handle website structure changes through:
- Multiple fallback extraction methods
- Flexible CSS selector configuration
- Error handling and retry mechanisms

To update for website changes:
1. Modify selectors in `config.yml`
2. Test with small article batches
3. Adjust content filters as needed

## 📄 License

This project is for educational and research purposes. Please respect Wazobia FM's robots.txt and terms of service when using this scraper.

## 🤝 Contributing

To improve the scraper:
1. Test with different article types
2. Report issues with specific URLs
3. Suggest new features or optimizations
4. Share improved CSS selectors

## 📞 Support

For issues or questions:
- Check the troubleshooting section
- Review the configuration options
- Test with the built-in demo functions
