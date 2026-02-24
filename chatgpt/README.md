# Astrology GPT — ChatGPT GPT Actions Setup

Step-by-step guide to create a custom GPT powered by the Astrology API.

## Prerequisites

- ChatGPT Plus, Team, or Enterprise subscription
- Astrology API key from [dashboard.astrology-api.io](https://dashboard.astrology-api.io/)

## Setup Steps

### 1. Create a New GPT

1. Go to [chat.openai.com](https://chat.openai.com/) → **Explore GPTs** → **Create**
2. Switch to the **Configure** tab

### 2. Basic Settings

| Field | Value |
|---|---|
| Name | Astrology Assistant (or your preferred name) |
| Description | Expert astrologer powered by the Astrology API. Birth charts, compatibility, horoscopes, tarot, numerology, and more. |

### 3. Instructions

Copy the contents of [`instructions.md`](instructions.md) into the **Instructions** field.

### 4. Configure Actions

1. Scroll down to **Actions** → click **Create new action**
2. Click **Import from URL** or paste the schema directly
3. Paste the contents of [`openapi-gpt-actions.json`](openapi-gpt-actions.json) into the **Schema** editor
4. Set **Authentication**:
   - Type: **API Key**
   - API Key: paste your Astrology API key
   - Auth Type: **Bearer**

### 5. Conversation Starters (optional)

Suggested prompts to help users get started:

- "What's my birth chart? I was born March 15, 1990 at 2:30 PM in New York"
- "Are Aries and Libra compatible?"
- "What does today's horoscope say for Taurus?"
- "Draw me 3 tarot cards"
- "What's the current moon phase?"

### 6. Publish

Choose your visibility:
- **Only me** — personal use
- **Anyone with a link** — share with others
- **Public** — listed in GPT Store

Click **Save** to finish.

## Included Endpoints (32)

The trimmed OpenAPI spec includes the most commonly used endpoints:

- **Charts**: natal, synastry, composite, transit, solar return, progressions
- **Data**: current sky, positions, house cusps, aspects, lunar metrics
- **Horoscopes**: daily/weekly/monthly by sign, personal daily
- **Analysis**: natal report, compatibility score, transit report, career, psychological
- **Rendering**: natal/synastry/transit SVG charts
- **Tarot**: card draw, daily card, three-card spread
- **Numerology**: core numbers, comprehensive reading
- **Lunar**: void of course, lunar phases
- **Glossary**: house systems, city search

The full API has 240+ endpoints. To add more, extract them from the complete spec at `../assets/openapi-astrology.json`.

## Customization

### Adding More Endpoints

1. Open `../assets/openapi-astrology.json` (full spec)
2. Copy the desired path and its schemas
3. Add to `openapi-gpt-actions.json`
4. Update the schema in your GPT Actions

### Language Support

The API supports multiple languages: EN, RU, FR, DE, ES, IT, PT, and more. Update the `language` field in the instructions to match your target audience.

## Troubleshooting

| Issue | Solution |
|---|---|
| "Authentication failed" | Verify API key is correct and set as Bearer type |
| "Action not found" | Re-import the OpenAPI schema |
| GPT ignores actions | Check that instructions reference the correct `operationId` names |
| Timeout errors | Some analysis endpoints take longer; retry or use simpler endpoints first |
