# Schema Template for Google Docs

Copy this content into your Google Doc for the social media schemas:

---

<common>
{
    "type": "object",
    "properties": {
        "hashtags": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "image_suggestion": {
            "type": "string"
        }
    }
}
</common>

<root>
{
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "description": {
            "type": "string"
        },
        "additional_notes": {
            "type": "string"
        }
    }
}
</root>

<linkedin>
{
    "type": "object",
    "properties": {
        "post": {
            "type": "string"
        },
        "call_to_action": {
            "type": "string"
        }
    }
}
</linkedin>

<instagram>
{
    "type": "object",
    "properties": {
        "caption": {
            "type": "string"
        },
        "emojis": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "call_to_action": {
            "type": "string"
        }
    }
}
</instagram>

<facebook>
{
    "type": "object",
    "properties": {
        "post": {
            "type": "string"
        },
        "call_to_action": {
            "type": "string"
        }
    }
}
</facebook>

<xtwitter>
{
    "type": "object",
    "properties": {
        "video_suggestion": {
            "type": "string"
        },
        "post": {
            "type": "string"
        },
        "character_limit": {
            "type": "integer"
        }
    }
}
</xtwitter>

<threads>
{
    "type": "object",
    "properties": {
        "text_post": {
            "type": "string"
        },
        "call_to_action": {
            "type": "string"
        }
    }
}
</threads>

<youtube_short>
{
    "type": "object",
    "properties": {
        "video_suggestion": {
            "type": "string"
        },
        "title": {
            "type": "string"
        },
        "description": {
            "type": "string"
        },
        "call_to_action": {
            "type": "string"
        }
    }
}
</youtube_short>

---

## Instructions for Use:

1. Create a new Google Doc
2. Copy and paste the content above exactly as shown
3. Do NOT modify the JSON schema structure unless you understand the workflow implications
4. Share the document with your n8n Google service account
5. Copy the document ID from the URL  
6. Update the "Social Media Schema" node in the workflow with this document ID

## Schema Explanation:

### Common Schema
- **hashtags**: Array of hashtags for all platforms
- **image_suggestion**: Description for AI image generation

### Root Schema  
- **name**: Content title/name
- **description**: Brief description of the content
- **additional_notes**: Extra context or notes

### Platform-Specific Schemas

**LinkedIn**:
- **post**: Main LinkedIn post content
- **call_to_action**: Professional CTA

**Instagram**:
- **caption**: Instagram caption with emojis
- **emojis**: Array of relevant emojis
- **call_to_action**: Engaging Instagram CTA

**Facebook**:
- **post**: Facebook post content
- **call_to_action**: Community-focused CTA

**Twitter/X**:
- **video_suggestion**: Video content idea
- **post**: Tweet content (character limited)
- **character_limit**: Max character count

**Threads**:
- **text_post**: Threads post content
- **call_to_action**: Discussion-focused CTA

**YouTube Shorts**:
- **video_suggestion**: Video content description
- **title**: Video title
- **description**: Video description
- **call_to_action**: Subscribe/engagement CTA

## Important Notes:

- Keep the XML-style tags (`<common>`, `<linkedin>`, etc.) exactly as shown
- The JSON schemas must be valid JSON format
- Each platform schema defines the expected output structure
- The workflow parses these schemas to generate platform-specific content
- Any changes to field names will require updating the workflow nodes accordingly