# iSponsorBlockTV

Automatically skips SponsorBlock segments and mutes/skips native YouTube ads on your TV.

## Prerequisites

You need the pairing code from the YouTube app on your TV:

1. Open YouTube on your TV.
2. Go to **Settings → Link with TV code** (the exact path varies by device).
3. Note the code shown — this is your `screen_id`.

## Configuration

### `devices` (required)

A list of TV devices to connect to. Each entry has:

| Field | Description | Default |
|---|---|---|
| `screen_id` | Pairing code from your TV's YouTube app | _(required)_ |
| `name` | Friendly name shown in logs | `YouTube on TV` |
| `offset` | Time offset in milliseconds to compensate for stream delay | `0` |

### `skip_categories`

SponsorBlock segment categories to auto-skip. Available values:

| Value | Description |
|---|---|
| `sponsor` | Paid promotions and sponsorships |
| `selfpromo` | Unpaid self-promotion |
| `exclusive_access` | Footage only for paid members |
| `interaction` | Requests to like, subscribe, etc. |
| `poi_highlight` | "Jump to highlight" markers |
| `intro` | Intro animation / recap |
| `outro` | Endscreen / credits |
| `preview` | Previewable video preview |
| `filler` | Filler tangents |
| `music_offtopic` | Non-music section in music videos |

### Other options

| Option | Description | Default |
|---|---|---|
| `skip_count_tracking` | Report skipped segments to SponsorBlock | `true` |
| `mute_ads` | Mute native YouTube ads | `true` |
| `skip_ads` | Click "Skip Ad" automatically | `true` |
| `minimum_skip_length` | Minimum segment length (seconds) to skip | `1` |
| `auto_play` | Enable autoplay | `true` |
| `join_name` | Name shown in YouTube's cast list | `iSponsorBlockTV` |
| `apikey` | YouTube Data API key (only needed for channel whitelist) | _(empty)_ |
| `channel_whitelist` | Channels excluded from all skipping/muting | _(empty)_ |
| `use_proxy` | Use system proxy for all requests | `false` |

## Troubleshooting

- **App starts but nothing is skipped**: Make sure the `screen_id` is correct and the TV is
  actively playing YouTube. The app needs to be connected while playback is happening.
- **"Invalid screen_id" warning**: YouTube recently changed their pairing code format.
  Get a fresh code from the TV settings.
- **Channel whitelist not working**: A YouTube Data API key (`apikey`) is required for this
  feature. Create one in the [Google Cloud Console](https://console.cloud.google.com/).
