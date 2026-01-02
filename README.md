# BuyandShip Social Media Voice Crawler

A multi-platform social media crawler designed to collect and analyze customer voice and sentiment about **BuyandShip** - a cross-border e-commerce shipping service.

## Purpose

This tool monitors social media platforms to gather:
- Customer reviews and feedback about BuyandShip services
- Brand mentions and community discussions
- Service experience reports (positive and negative)
- Regional sentiment analysis across Asian markets

## Supported Platforms

| Platform | Data Type | Method |
|----------|-----------|--------|
| Reddit | Posts + Comments | Web scraping (old.reddit.com) |
| Trustpilot | Reviews + Ratings | HTML parsing with JSON data |
| Threads | Posts + Replies | HTTP scraping + regex parsing |

## Country Segmentation
- HK (Hong Kong)
- TW (Taiwan)
- PH (Philippines)
- SG (Singapore)
- JP (Japan)
- MY (Malaysia)
- OTHER (All other countries)

## Installation

```bash
cd SocialPlatform
pip install -r requirements.txt
```

## Usage

### Reddit
```bash
python main.py --platform reddit --type search --keywords "BuyandShip" --save json
```

### Trustpilot
```bash
python main.py --platform trustpilot --type search --keywords "BuyandShip" --save json
```

### Threads
```bash
python main.py --platform threads --type search --keywords "BuyandShip" --save json
```

## Options

| Option | Description | Default |
|--------|-------------|---------|
| `--platform` / `-p` | Platform: reddit, trustpilot, threads | reddit |
| `--type` / `-t` | Crawler type: search, detail | search |
| `--keywords` / `-k` | Comma-separated keywords | "" |
| `--save` / `-s` | Save format: json, csv, sqlite | json |
| `--max-posts` / `-m` | Max posts per keyword | 100 |
| `--comments` | Enable comment crawling | true |

## Output

Data is saved to `data/{platform}/` directory:
- `data/reddit/reddit_posts.json`
- `data/reddit/reddit_comments.json`
- `data/trustpilot/trustpilot_reviews.json`
- `data/threads/threads_posts.json`

## Configuration

Edit `config.py` to customize:
- API credentials (Reddit)
- Delay settings
- Maximum posts/comments
- Regional subreddits
