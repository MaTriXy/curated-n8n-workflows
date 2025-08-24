# Automated Social Media Publishing Factory - Setup Instructions

## Overview
This workflow creates AI-powered social media content for LinkedIn, Twitter/X, Instagram, Facebook, Threads, and YouTube Shorts with automated image generation, human approval, and multi-platform publishing.

## Required Credentials & APIs

### 1. OpenAI API
- **Purpose**: AI content generation and chat models
- **Setup**: Get API key from https://platform.openai.com/
- **Node Configuration**: Configure in all OpenAI chat model nodes

### 2. Google APIs
**Google Docs API**
- **Purpose**: External system prompt and schema management
- **Setup**: Enable Google Docs API in Google Cloud Console
- **Required**: OAuth2 credentials

**Google Drive API** 
- **Purpose**: Content archiving and image storage
- **Setup**: Enable Google Drive API in Google Cloud Console
- **Required**: OAuth2 credentials

**Gmail API**
- **Purpose**: Approval workflow and notifications
- **Setup**: Enable Gmail API in Google Cloud Console  
- **Required**: OAuth2 credentials

### 3. Social Media Platform APIs

**Twitter/X API**
- **Purpose**: Post tweets
- **Setup**: Apply for Twitter API access at https://developer.twitter.com/
- **Required**: OAuth 2.0 credentials
- **Node**: X Post node

**LinkedIn API**
- **Purpose**: Post to LinkedIn company pages
- **Setup**: Create LinkedIn app at https://www.linkedin.com/developers/
- **Required**: OAuth 2.0 credentials
- **Node**: LinkedIn Post node

**Facebook Graph API**
- **Purpose**: Post to Facebook and Instagram
- **Setup**: Create Facebook app at https://developers.facebook.com/
- **Required**: Graph API credentials
- **Nodes**: Facebook Post, Instagram Image, Instagram Post

### 4. Optional Services

**IMGBB API**
- **Purpose**: Image hosting backup
- **Setup**: Get free API key from https://api.imgbb.com/
- **Environment Variable**: `IMGBB_API_KEY`

**SerpAPI**
- **Purpose**: Web search for content research
- **Setup**: Get API key from https://serpapi.com/
- **Required**: SerpAPI credentials

**Telegram Bot**
- **Purpose**: Status notifications (optional)
- **Setup**: Create bot via @BotFather
- **Environment Variables**: 
  - `TELEGRAM_BOT_TOKEN`
  - `TELEGRAM_CHAT_ID`

## Environment Variables

Add these to your n8n environment:

```bash
IMGBB_API_KEY=your_imgbb_api_key
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
TELEGRAM_CHAT_ID=your_telegram_chat_id
```

## Google Docs Setup

### 1. Create System Prompt Document
1. Create a new Google Doc
2. Copy the system prompt content (see SYSTEM_PROMPT.md)
3. Share document with your Google service account
4. Copy the document ID from URL
5. Update "Social Media System Prompt" node with document ID

### 2. Create Schema Document
1. Create a new Google Doc  
2. Copy the schema content (see SCHEMA_TEMPLATE.md)
3. Share document with your Google service account
4. Copy the document ID from URL
5. Update "Social Media Schema" node with document ID

## Platform-Specific Configuration

### LinkedIn
- Update `organization` field in LinkedIn Post node with your organization ID
- Configure OAuth2 credentials for LinkedIn

### Twitter/X  
- Configure OAuth2 credentials for Twitter API v2

### Facebook/Instagram
- Update `node` fields with your Facebook Page ID and Instagram Business Account ID
- Configure Facebook Graph API credentials

### Gmail Approval
- Update `sendTo` email addresses in Gmail nodes
- Configure Gmail OAuth2 credentials

## Folder IDs & Storage

### Google Drive
- Create folder for image storage
- Update `folderId` in Google Drive nodes
- Configure OAuth2 credentials

## Testing & Validation

### 1. Test Individual Components
- Test OpenAI connection
- Verify Google Docs access
- Test image generation (Pollinations.ai)
- Validate social media API connections

### 2. End-to-End Testing
- Start with a simple prompt
- Verify content generation
- Check image creation
- Test approval workflow
- Validate publishing to each platform

### 3. Error Handling
- Monitor Telegram notifications
- Check Gmail for approval emails
- Verify content archiving in Google Drive

## Usage

### Chat Interface
1. Access the chat webhook URL
2. Send natural language prompts like:
   - "Create a LinkedIn post about AI automation trends"
   - "Make an Instagram post about productivity hacks"
   - "Generate Twitter content about our new product launch"

### Workflow Trigger
1. Call the workflow with parameters:
   ```json
   {
     "route": "linkedin",
     "user_prompt": "Create content about business automation"
   }
   ```

## Content Approval Process

1. Content generated and preview email sent
2. Human approval required via Gmail
3. Upon approval, content published to selected platform(s)
4. Content and images archived to Google Drive
5. Notifications sent via Telegram (optional)

## Customization

### System Prompts
- Edit Google Doc for system prompts
- Customize platform-specific guidelines
- Adjust brand voice and tone

### Content Schema  
- Modify JSON schemas for different output formats
- Add new platforms by extending schema

### Image Generation
- Replace Pollinations.ai with other services
- Customize image prompts and styles
- Adjust image dimensions per platform

## Troubleshooting

### Common Issues
- **API Rate Limits**: Implement delays between requests
- **Credential Expiry**: Refresh OAuth tokens regularly  
- **Image Generation Fails**: Check Pollinations.ai status
- **Approval Timeout**: Extend Gmail wait time limits

### Debug Mode
- Enable verbose logging in n8n
- Monitor individual node outputs
- Check error messages in Telegram notifications

## Security Considerations

- Store all credentials securely in n8n credential store
- Use environment variables for API keys
- Regularly rotate API keys and tokens
- Implement IP restrictions where possible
- Monitor API usage and costs

## Performance Optimization

- Use GPT-4o-mini for cost-effective content generation
- Implement caching for frequently used prompts
- Batch process multiple platform posts
- Optimize image sizes for each platform

## Support

For issues or customization:
1. Check n8n workflow execution logs
2. Verify all API credentials are valid
3. Test individual nodes in isolation
4. Review platform-specific API documentation