Ryot is a self-hosted platform for tracking your media (movies, shows, books, games, anime, manga) and fitness activities (exercises, measurements, nutrition). All your data stays on your server.

**Features:**
- Track movies, TV shows, books, video games, anime, manga, and music
- Log workouts, measurements, and nutritional data
- Import from Trakt, MAL, Goodreads, Plex, Jellyfin, and more
- Automatic AI-powered tagging and recommendations
- Clean, responsive web UI with PWA support
- Export your data anytime
- REST API for integrations

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.com/deploy/T4-W1Y)

## Why Deploy Ryot on Railway?

Running Ryot on Railway eliminates server management entirely. With one click you get a production-ready Ryot instance with a managed PostgreSQL database, auto-deploys from GitHub, automatic HTTPS, and global CDN. No VPS setup, no Docker Compose wrangling, no database administration.

## Common Use Cases

- **Media enthusiasts**: Track every movie, show, book, and game you consume with ratings, reviews, and detailed metadata
- **Fitness tracking**: Log workouts, body measurements, and nutrition — all in one place alongside your media habits
- **Data hoarders**: Import years of history from Trakt, MyAnimeList, Goodreads, Plex, and Jellyfin into a single searchable database
- **Self-hosters**: Replace SaaS tracking services with a private instance where you control every byte of your personal data
- **Small groups**: Share a Ryot instance with family or friends — multi-user support with separate tracking per person

## Dependencies for Deployment

### Required

- **PostgreSQL**: Railway provisions a managed PostgreSQL database automatically. No manual configuration needed.
- **Server Admin Access Token**: A long random string that authenticates you as the administrator on first login.

### Optional Integrations

| Service | Config Variable | Purpose |
|---------|----------------|---------|
| TMDB | `MOVIES_AND_SHOWS_TMDB_ACCESS_TOKEN` | Movie and TV show metadata |
| Twitch | `VIDEO_GAMES_TWITCH_CLIENT_ID`, `VIDEO_GAMES_TWITCH_CLIENT_SECRET` | Video game metadata |
| Spotify | (via Ryot UI config) | Music tracking |

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `DATABASE_URL` | PostgreSQL connection string (auto-filled by Railway) | Yes |
| `SERVER_ADMIN_ACCESS_TOKEN` | Admin authentication token — set to a random string | Yes |
| `FRONTEND_URL` | Public URL of your Ryot instance (leave empty to auto-detect) | No |
| `TZ` | Timezone in IANA format (e.g., `America/New_York`) | No |
| `DISABLE_TELEMETRY` | Set to `true` to disable telemetry | No |
| `MOVIES_AND_SHOWS_TMDB_ACCESS_TOKEN` | TMDB access token for movie/TV metadata | No |
| `VIDEO_GAMES_TWITCH_CLIENT_ID` | Twitch client ID for game metadata | No |
| `VIDEO_GAMES_TWITCH_CLIENT_SECRET` | Twitch client secret for game metadata | No |

## Volumes

Ryot stores all data in PostgreSQL. No persistent volume is required for the application service — your data lives in the managed database.

## About Hosting

Ryot runs on a single container with the backend API and frontend served together on port 8000. On Railway, the app is fronted by automatic HTTPS via the Railway edge network, with DDoS protection and global CDN. Sleep after inactivity is disabled by default to keep the instance always available.

## FAQ

**Q: How do I get my admin access token?**
A: Set `SERVER_ADMIN_ACCESS_TOKEN` to any long, randomly generated string (e.g., `openssl rand -base64 36`). Use this token to log in on the first visit.

**Q: How do I set up media tracking?**
A: Get a free API key from TMDB (for movies/TV) and/or Twitch (for video games) and set the corresponding environment variables. See the [Ryot documentation](https://docs.ryot.io/configuration) for details.

**Q: Can I import my existing data?**
A: Yes! Ryot supports importing from Trakt, MyAnimeList, Goodreads, Plex, Jellyfin, ListenBrainz, and CSV exports.

**Q: Is there a mobile app?**
A: Ryot is a Progressive Web App (PWA). You can install it on your phone's home screen from the browser.
