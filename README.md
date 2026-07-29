Ryot is a self-hosted platform for tracking your media (movies, shows, books, games, anime, manga) and fitness activities (exercises, measurements, nutrition). All your data stays on your server.

**Features:**
- Track movies, TV shows, books, video games, anime, manga, and music
- Log workouts, measurements, and nutritional data
- Import from Trakt, MAL, Goodreads, Plex, Jellyfin, and more
- Automatic AI-powered tagging and recommendations
- Clean, responsive web UI
- Export your data anytime
- REST API for integrations

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.com/deploy/TEMPLATE_CODE)

## Features

- **Media Tracking**: Movies & TV shows (TMDB), video games (IGDB/Twitch), books (manual/import), anime & manga (MAL), music (ListenBrainz)
- **Fitness Tracking**: Workout logging with exercises, sets, reps, and weights. Track body measurements and nutritional intake
- **Integrations**: Import history from Trakt, MyAnimeList, Goodreads, Plex, Jellyfin, ListenBrainz, and more
- **Dashboard**: Get insights into your media consumption and fitness progress
- **Multi-user**: Support for multiple users with separate tracking
- **Progressive Web App**: Install as a native app on mobile devices
- **Full Text Search**: Quickly find any tracked item
- **REST API**: Build custom integrations

## Getting Started

1. Click the "Deploy on Railway" button above
2. Railway automatically provisions a PostgreSQL database
3. Set the `SERVER_ADMIN_ACCESS_TOKEN` environment variable to a secure random string
4. Set the `FRONTEND_URL` to your Railway-generated domain (e.g., `https://ryot-production.up.railway.app`)
5. Wait for the deployment to complete, then visit your domain
6. Log in with your admin access token

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | PostgreSQL connection string (auto-filled) | Yes |
| `SERVER_ADMIN_ACCESS_TOKEN` | Admin authentication token | Yes |
| `FRONTEND_URL` | Public URL of your Ryot instance | Yes |
| `TZ` | Timezone (IANA format, e.g., `Europe/Amsterdam`) | No |
| `DISABLE_TELEMETRY` | Set to `true` to disable telemetry | No |
| `MOVIES_AND_SHOWS_TMDB_ACCESS_TOKEN` | TMDB access token for movie/TV tracking | No |
| `VIDEO_GAMES_TWITCH_CLIENT_ID` | Twitch client ID for game tracking | No |
| `VIDEO_GAMES_TWITCH_CLIENT_SECRET` | Twitch client secret for game tracking | No |

## Volumes

Ryot stores all data in the PostgreSQL database. No persistent volumes are required.

## FAQ

**Q: How do I get my admin access token?**
A: Set `SERVER_ADMIN_ACCESS_TOKEN` to any long, randomly generated string (e.g., `openssl rand -base64 36`). Use this token to log in on the first visit.

**Q: How do I set up media tracking?**
A: Get a free API key from TMDB (for movies/TV) and/or Twitch (for video games) and set the corresponding environment variables. See the [Ryot documentation](https://docs.ryot.io/configuration) for details.

**Q: Can I import my existing data?**
A: Yes! Ryot supports importing from Trakt, MyAnimeList, Goodreads, Plex, Jellyfin, ListenBrainz, and CSV exports.

**Q: Is there a mobile app?**
A: Ryot is a Progressive Web App (PWA). You can install it on your phone's home screen from the browser.
