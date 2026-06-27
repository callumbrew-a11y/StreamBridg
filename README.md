# StreamBridg
Merge live chat from YouTube, TikTok, and Twitch into a single customisable overlay for streaming. Features per-platform colours and fonts, text-to-speech, notification sounds, profanity filtering, viewer counts, and an OBS browser source with native transparency.

<img width="590" height="629" alt="Screenshot 2026-06-27 141500" src="https://github.com/user-attachments/assets/1f8c16b9-986e-402e-8db5-23f624a1b632" />

## Desktop Overlays
- Main Overlay — your private, unfiltered view of all chat activity
- Streamer Overlay — a filtered view safe for stream display, with independent settings
- Both overlays are frameless, transparent, always-on-top, and freely resizable
- Lock/unlock toggle for click-through mode (interact with apps behind the overlay)
- Per-overlay controls: opacity, background colour, text size, timestamps, platform tags, event tags, and viewer count header

## OBS Browser Source
- Built-in local server that serves a browser source URL (e.g. http://localhost:9150)
- Native transparency — no chroma key or window capture needed
- Mirrors the Streamer Overlay settings: colours, fonts, bold, outline, timestamps, tags, opacity, background colour, profanity filter, and viewer counts
- All changes update live — no need to refresh in OBS
- Works with OBS, Streamlabs, XSplit, and any software that supports browser sources

## Text-to-Speech
- Neural voice synthesis via Edge TTS with a curated selection of voices
- FIFO queue with backpressure — keeps TTS riding the live edge of chat during busy streams (queue of 15, 30-second TTL)
- Per-category mute toggles — read chat but skip likes, follows, etc.
- Adjustable volume, rate, and voice selection
- Smart name handling: leet-speak normalisation, emoji stripping, unicode normalisation
- Pronunciation dictionary — define custom word-to-speech mappings for names and slang (applied to both usernames and message text)
- Text expansion for abbreviations (brb, imo, lol, etc.)
- Duplicate message suppression within a configurable window
- Profanity replacement (swapped to "beep" in speech)

## Notification Sounds
- Per-event custom sound files with a file picker (WAV format)
- Developer defaults in config.json with user overrides
- Per-event cooldowns (e.g. only play the like sound every 5 seconds during spam)
- Right-click context menu to reset to default or remove a custom sound
- Adjustable master sound volume with PCM scaling 

## Event System
- Show/hide toggles per event category: chat, subs, gifts, follows, likes, shares, bits, raids, super chats, stickers, milestones
- Disabling an event hides it from the feed but TTS and sounds operate independently with their own toggles
- TikTok gift events display gift name, count, and diamond value (with streak deduplication)
- YouTube quota tracking with automatic stop before hitting the daily API limit

## Text & Styling
- Per-platform font selection from a curated list of system fonts with live preview
- Per-platform colour for the platform tag ([YOUTUBE], [TIKTOK], [TWITCH])
- Per-platform message body colour
- Per-event tag colour customisation (e.g. Chat white, Gifts cyan, Subs gold)
- Customisable name colour (distinct from message text)
- Bold toggles for names and messages independently
- Text outline with adjustable thickness (1–4px)
- Show/hide platform tags and event tags per overlay

## Viewer Counts
- Live viewer count header per platform (YouTube, TikTok, Twitch)
- YouTube: concurrent viewers + likes
- TikTok: live viewers, total viewers, and total likes
- Twitch: viewer count + chatter count

## Profanity Filter
- Word list editor with add/remove and whole-word matching
- Option to censor names as well as message text
- Applied to the Streamer Overlay and browser source; Main Overlay stays unfiltered
- Editable at any time — changes apply without restart
- Display & Appearance
- Dark-themed control panel with tabbed navigation (Platforms, Events, TTS, Text, Display, Browser)
- Per-overlay opacity slider with customisable background colour
- Per-overlay show/hide timestamps toggle
- Viewer count toggle per overlay
- Lock/unlock for click-through mode
