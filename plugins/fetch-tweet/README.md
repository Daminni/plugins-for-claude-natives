# Fetch Tweet

Fetch full tweet text, author info, and engagement data from X/Twitter URLs — no authentication, no JavaScript, no API key required.

Powered by the open-source [FxEmbed](https://github.com/FxEmbed/FxEmbed) project's `api.fxtwitter.com` endpoint.

## Features

- **Zero dependencies** — Python standard library only
- **No auth required** — works with any public tweet
- **Full tweet data** — text (with expanded URLs), author, engagement, media, quote tweets
- **Pipeline-friendly** — `--json` mode for programmatic use
- **WebFetch fallback** — works even without script execution

## Usage

```
트윗 가져와 https://x.com/garrytan/status/2020072098635665909
트윗 번역해줘 https://x.com/sama/status/...
이 트윗 정리해줘 https://twitter.com/...
```

Or English:
- "fetch this tweet"
- "translate this tweet"
- "what does this tweet say"

## Direct Script Usage

```bash
# Formatted output
python scripts/fetch_tweet.py https://x.com/garrytan/status/2020072098635665909

# JSON output (for piping)
python scripts/fetch_tweet.py https://x.com/garrytan/status/2020072098635665909 --json
```

Supported URL formats: `x.com`, `twitter.com`, `fxtwitter.com`, `fixupx.com`

## API Response Fields

| Field | Description |
|-------|-------------|
| `tweet.text` | Tweet body (URLs expanded) |
| `tweet.author` | Author info (name, screen_name, bio, followers) |
| `tweet.likes/retweets/replies/bookmarks/views` | Engagement metrics |
| `tweet.created_at` | Timestamp |
| `tweet.media` | Attached media (photos, videos) |
| `tweet.quote` | Quoted tweet (same structure) |
| `tweet.lang` | Language code |

## Limitations

- Cannot fetch tweets from private accounts
- Cannot fetch deleted tweets
- Rate limited by FxEmbed server policy (no issue under normal use)

## Credits

Uses [FxEmbed](https://github.com/FxEmbed/FxEmbed) — the same backend that powers `fxtwitter.com` link previews on Discord/Telegram.
