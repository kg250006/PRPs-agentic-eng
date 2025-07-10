# Social Media APIs Integration Guide 2024

## Critical API Changes (December 2024)

**Instagram Basic Display API Deprecation**: Starting December 4, 2024, all requests to Instagram Basic Display API return errors. **Must migrate to Instagram Graph API**.

## Instagram Graph API

### Requirements
- Instagram Business or Creator account (required)
- Facebook Developer App with Instagram Graph API permissions
- HTTPS URLs for redirect URIs (localhost HTTP allowed in development)

### Key Endpoints
- User Profile: `/me` (id, username, media_count)
- User Media: `/me/media` (photos, videos, albums)
- Media Insights: `/{media-id}/insights` (engagement metrics)

### Rate Limits
- 200 requests per user token per hour
- Can be increased by adding test users in Facebook Developer Console

## Facebook Graph API

### OAuth Flow for React
```javascript
// Example OAuth configuration
const facebookConfig = {
  appId: 'your-app-id',
  cookie: true,
  xfbml: true,
  version: 'v19.0'
};

// Scopes needed
const scopes = [
  'pages_show_list',
  'pages_read_engagement', 
  'pages_manage_posts',
  'business_management'
];
```

### React Libraries
- `react-facebook-login` - Most popular OAuth library
- `react-facebook` - Alternative option
- Both handle OAuth flow and return user data (name, email, profile picture, access tokens)

## Security Considerations

### OAuth Best Practices
- Store access tokens securely on backend, not frontend localStorage
- Implement token refresh logic for long-lived tokens
- Use HTTPS for all OAuth redirect URIs
- Validate state parameter to prevent CSRF attacks

### Development Tools
- Postman for API testing
- ngrok for localhost HTTPS tunneling during development
- Facebook Graph API Explorer for endpoint testing

## API Integration Architecture

### Recommended Pattern
1. **Backend OAuth Handler**: Node.js/Express endpoint manages OAuth flow
2. **Frontend Trigger**: React component initiates OAuth with popup/redirect
3. **Token Storage**: Store tokens in secure HTTP-only cookies
4. **API Proxy**: Backend proxies all social media API calls
5. **Error Handling**: Graceful degradation when APIs are unavailable

### Rate Limiting Strategy
- Implement request queuing for rate limit compliance
- Cache API responses to reduce API calls
- Use webhooks where available for real-time updates
- Implement retry logic with exponential backoff