# Website Change Detection Tool

Monitor websites for content changes and get notified automatically via Discord, Email, Slack, Telegram, Webhook, and more.

## What it does

- Detects when a web page's content changes
- Sends alerts through many notification channels
- Supports price/stock monitoring, keyword triggers, and conditional alerts
- Can summarize changes using an AI model (optional, bring your own API key)

## Features

- Fast HTTP fetching or full Chrome-based fetching for JS-heavy sites
- Target specific page elements with CSS Selectors, XPath, JSONPath, or jq
- Visual element selector for picking exactly what to watch
- Browser automation steps (login, click, fill forms) before checking for changes
- Restock and price-change detection for product pages
- Schedule checks by time/day/timezone
- Diff view by word, line, or character
- REST API for managing watches programmatically
- PDF monitoring (text, size, checksum)
- JSON API monitoring with JSONPath/jq

## Common use cases

- Price drop / restock alerts
- Job postings on company career pages
- Government or organization announcements
- New software releases / security advisories
- Real estate listings
- Legal/document change tracking
- Generic keyword-appears alerts on any page

## Installation

### Docker

```bash
docker compose up -d
```

or

```bash
docker run -d --restart always -p "127.0.0.1:5000:5000" -v datastore-volume:/datastore --name webwatch webwatch-image
```

### Python pip

```bash
pip3 install webwatch
webwatch -d /path/to/data/dir -p 5000
```

Then open http://127.0.0.1:5000 in your browser.

## Updating (Docker)

```bash
docker pull webwatch-image
docker kill $(docker ps -a -f name=webwatch -q)
docker rm $(docker ps -a -f name=webwatch -q)
docker run -d --restart always -p "127.0.0.1:5000:5000" -v datastore-volume:/datastore --name webwatch webwatch-image
```

## Notifications

Supports most common notification services (email, Discord, Slack, Telegram, Microsoft Teams, custom webhooks, etc.) via URL-based configuration. Notification content is customizable using Jinja2 templates.

## Filters

Built-in support for XPath 1/2, CSS selectors, JSONPath, and jq for precise targeting of page content.

## Proxy support

Works with standard HTTP/HTTPS proxies, configurable per watch.

## Disclaimer

This software is provided "as-is" with no warranty. You are responsible for ensuring your use complies with the terms of service, robots.txt, and applicable laws of any site you monitor. If you enable AI/LLM features, monitored content will be sent to the third-party AI provider you configure — you are responsible for any related compliance and costs. AI output can be inaccurate and should not be relied on as complete or correct.
