# RevContent

RevContent is a performance-driven native advertising and content recommendation network that connects advertisers with engaged audiences across a publisher network delivering over 250 billion content recommendations per month. The platform provides a REST API for programmatically managing widgets, campaigns (boosts), ad content, audience targeting, bidding strategies, and performance reporting.

## API

RevContent's Stats and Management API is accessible at `https://api.revcontent.io` and uses OAuth 2.0 client credentials flow for authentication. API access must be enabled by an account representative; credentials (client_id and client_secret) are available in Account Settings.

Key API capabilities include:

- **Boosts (Campaigns)**: Create, update, and manage ad campaigns with CPC or vCPM pricing
- **Widgets**: Manage publisher ad widgets and widget-level targeting
- **Content**: Control ad content and retrieve content performance statistics
- **Targeting**: Device, OS, geo (country, region, DMA, zip code), and widget-level targeting
- **Statistics**: Boost performance, widget stats, and content reporting with cost-per-conversion metrics
- **CCPA**: Data request and deletion API for privacy compliance

## Authentication

```
POST https://api.revcontent.io/oauth/token
grant_type=client_credentials&client_id={id}&client_secret={secret}
```

Access tokens are valid for 24 hours and passed as `Authorization: Bearer {token}`.

## Links

- **Website**: https://www.revcontent.com
- **Help Center / API Docs**: https://help.revcontent.com/knowledge/native-api
- **Getting Started**: https://help.revcontent.com/knowledge/publisher-advertiser-api-requests
- **API Changelog**: https://help.revcontent.com/knowledge/api-changelog
- **CCPA API**: https://help.revcontent.com/knowledge/ccpa-data-request-data-deletion-request-api
- **GitHub Org**: https://github.com/RevContent
- **Status Page**: http://status.revcontent.com/
- **Blog**: https://www.revcontent.com/resources/blog
- **LinkedIn**: https://www.linkedin.com/company/revcontent
- **X (Twitter)**: https://x.com/RevContent
