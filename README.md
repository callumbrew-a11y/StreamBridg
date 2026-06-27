# StreamBridg
Merge live chat from YouTube, TikTok, and Twitch into a single customisable overlay for streaming. Features per-platform colours and fonts, text-to-speech, notification sounds, profanity filtering, viewer counts, and an OBS browser source with native transparency.

<img width="590" height="629" alt="Screenshot 2026-06-27 141500" src="https://github.com/user-attachments/assets/1f8c16b9-986e-402e-8db5-23f624a1b632" />

## Desktop Overlays
- **Main Overlay** — your private, unfiltered view of all chat activity
- **Streamer Overlay** — a filtered view safe for stream display, with independent settings
- Both overlays are frameless, transparent, always-on-top, and freely resizable
- Lock/unlock toggle for click-through mode (interact with apps behind the overlay)
- Per-overlay controls: opacity, background colour, text size, timestamps, platform tags, event tags, and viewer count header
- Custom text per overlay with full formatting (size, font, bold, colour) — displays above viewer count
- Scroll through chat history with the mouse wheel; a "New Messages" indicator appears when scrolled up

## OBS Browser Source
- Built-in local server that serves a browser source URL (e.g. `http://localhost:9150`)
- Native transparency — no chroma key or window capture needed
- Mirrors the Streamer Overlay settings: colours, fonts, bold, outline, timestamps, tags, opacity, background colour, profanity filter, viewer counts, custom text, and announcements
- All changes update live — no need to refresh in OBS
- Works with OBS, Streamlabs, XSplit, and any software that supports browser sources

## Text-to-Speech
- Neural voice synthesis via Edge TTS with a curated selection of voices
- FIFO queue with backpressure — keeps TTS riding the live edge of chat during busy streams
- Per-category mute toggles — read chat but skip likes, follows, etc.
- Skip bot messages toggle — bots are silenced by default
- Adjustable volume, rate, and voice selection
- Smart name handling: leet-speak normalisation, emoji stripping, unicode normalisation
- Pronunciation dictionary — define custom word-to-speech mappings for names and slang
- Text expansion for abbreviations (brb, imo, lol, etc.)
- Duplicate message suppression within a configurable window
- Profanity replacement (swapped to "beep" in speech)
- Donation readout — "X donated £5.00 and says thanks for the stream"

## Notification Sounds
- Per-event custom sound files with a file picker (WAV format)
- Developer defaults in `config.json` with user overrides
- Per-event cooldowns (e.g. only play the like sound every 5 seconds during spam)
- Right-click context menu to reset to default or remove a custom sound
- Adjustable master sound volume with PCM scaling

## Event System
- Show/hide toggles per event category: chat, donations, subs, gifts, follows, likes, shares, bits, raids, stickers, members
- Disabling an event hides it from the feed but TTS and sounds operate independently with their own toggles
- YouTube donations (Super Chats) display the amount separately with customisable colour
- TikTok gift events display gift name, count, and diamond value (with streak deduplication)

## Bot Detection
- Known bots (Nightbot, StreamElements, StreamLabs, Moobot, etc.) are detected automatically
- Per-platform show, sound, notification, and cooldown controls
- Per-platform bot name colour in the Text tab
- Editable bot list — add or remove bot usernames for custom bots
- TTS skips bot messages by default (configurable)
- Handles `@` prefixed names (e.g. `@Nightbot` matches `nightbot`)

## Announcements
- Create timed announcements that display on both overlays and the browser source
- Each announcement runs on its own independent timer (e.g. one every 1 min, another every 5 min)
- Per-announcement: name, message, interval, name colour, message colour, notification sound, and TTS toggle
- Enable/disable individual announcements without removing them

## Text & Styling
- Per-platform font selection from a curated list of system fonts with live preview
- Per-platform colours for: platform tag, name, bot, and message text
- Per-event tag colour customisation (e.g. Chat white, Donations pink, Members cyan)
- Bold toggles for names and messages independently
- Text outline with adjustable thickness (1–4px) — cached per-widget for performance
- Show/hide platform tags and event tags per overlay

## Viewer Counts
- Live viewer count header per platform (YouTube, TikTok, Twitch)
- YouTube: concurrent viewers + likes (scraped, no API key needed)
- TikTok: live viewers, total viewers, and total likes
- Twitch: viewer count + chatter count (requires optional token setup)
- Scales with text size and uses platform colours

## Profanity Filter
- Word list editor with add/remove
- Detects profanity within compound words (e.g. "bumfuck" catches "fuck")
- Option to censor names as well as message text
- Applied to the Streamer Overlay and browser source; Main Overlay stays unfiltered
- Editable at any time — changes apply without restart

## Display & Appearance
- Dark-themed control panel with tabbed navigation (Platforms, Events, TTS, Text, Display, Browser Source, Announcements)
- Per-overlay opacity slider with customisable background colour
- Per-overlay show/hide timestamps toggle
- Platform tags and event tags toggles per overlay
- Viewer count toggle per overlay
- Lock/unlock for click-through mode — visible border when unlocked at zero opacity

## Auto-Update
- Checks GitHub Releases on launch for newer versions
- Prompts with a Yes/No dialog showing current vs. available version
- Downloads and installs the update automatically, then relaunches
- User settings are preserved through updates
- Fails silently when offline — never blocks startup
- Current version displayed in the footer

## Platform Setup
- **YouTube** — no setup needed. Just paste the stream URL or video ID
- **TikTok** — no setup needed. Just enter the username
- **Twitch** — no setup needed for chat, subs, gifts, bits, and raids. Optional token setup for viewer count and follow notifications ([Setup Guide](https://github.com/callumbrew-a11y/StreamBridg/wiki/Twitch-Setup))
