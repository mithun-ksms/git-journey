# London Tourism Chatbot — Backend

Express webhook backend for a Dialogflow-powered London tourism chatbot.
Handles weather, currency conversion, nearby attractions, restaurant
recommendations, and directions, with Gemini AI as a fallback/general
conversation engine.

## Setup

1. Install dependencies:
   ```
   npm install
   ```

2. Copy `.env.example` to `.env` and fill in your real API keys:
   ```
   cp .env.example .env
   ```

3. Run locally:
   ```
   npm start
   ```

## Required API keys

| Variable | Where to get it |
|---|---|
| `WEATHER_API_KEY` | https://openweathermap.org/api |
| `MAPS_API_KEY` | https://console.cloud.google.com (enable Maps, Geocoding, Places, Directions APIs) |
| `TRIPADVISOR_API_KEY` | https://www.tripadvisor.com/developers |
| `GEMINI_API_KEY` | https://aistudio.google.com/apikey |

## Deploying to Render

1. Push this repo to GitHub.
2. On Render, create a new **Web Service** and connect this repo.
3. Build command: `npm install`
4. Start command: `npm start`
5. Add the four environment variables above in Render's dashboard (Settings → Environment).
6. Once deployed, update your Dialogflow agent's webhook URL and your frontend's
   `config.js` to point at the new Render URL instead of the old Glitch URL.

## Notes

- Conversation history is kept in memory per session and auto-clears after 5 minutes.
- Interaction logs are written to `chatbot_logs.json` locally (ignored by git, not persisted on Render's free tier across restarts).
