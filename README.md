# LilithBot

A feature-rich chat bot for live streaming, built around an AI character named **Лилит (Lilith)**. Designed for Trovo, with planned migration to VK Play.

---

## What the bot does

- Responds to chat commands (`!command` prefix)
- Engages viewers through an AI persona powered by Google Gemini — activated only when a viewer mentions `@Лилит` directly
- Runs interactive chat games: **slot machine** and **hippodrome races** with a virtual coin economy (SX-coins)
- Assigns viewer roles and tracks relationships between Lilith and individual viewers
- Integrates with OBS via WebSocket to trigger stream overlays and widgets

---

## Data collection & privacy

LilithBot may store limited viewer data to enable persistent features (coin balance, roles, relationship history, conversation anchors with Lilith).

### Key principles

- **Consent required.** Data is only collected after the viewer explicitly opts in via a chat command.
- **Double confirmation.** Every opt-in requires a second confirmation step (`!да` / `!нет`) before anything is saved.
- **No sensitive data.** The bot never requests, stores, or processes passwords, emails, payment details, or any authentication credentials.
- **No probing for personal info.** The bot never asks viewers for their real name or any personal details. If a viewer chooses to share their name themselves, it may be remembered — nothing more.
- **Right to deletion.** Viewers can permanently delete all data stored about them (chat history with Lilith, anchors, profile) at any time using a chat command. No manual request to the streamer needed.
- **Transparency.** If a viewer doesn't know the available privacy commands, they can ask the bot directly in chat — it will explain what to type.

### What is stored (opt-in only)

| Data | Purpose |
|---|---|
| Trovo username | Identifying the viewer across sessions |
| SX-coin balance | Virtual economy for games |
| Viewer role | Assigned by streamer (e.g. cook, bartender) |
| Relationship level with Lilith | Drives AI response tone |
| Conversation anchors | Long-term memory for Lilith's AI responses |
| Real name | Only if volunteered by the viewer themselves |

### What is never stored

- Passwords or tokens
- Email addresses
- Payment or financial information
- IP addresses
- Data from viewers who have not opted in

---

## Permissions used

| Permission | Reason |
|---|---|
| Read chat messages | Required to detect commands and `@Лилит` mentions |
| Send chat messages | Required to respond to viewers |
| Read viewer/user info | Required to identify who sent a command |

---

## Tech stack

- Python 3.12
- SQLite (local database, stored on streamer's machine)
- Google Gemini API (AI responses only, no command logic)
- OBS WebSocket v5

---

## Data storage

All data is stored **locally on the streamer's machine** in a SQLite database. No data is sent to third-party servers except:
- Google Gemini API — receives only the last 15 chat messages as context when `@Лилит` is mentioned. No viewer identifiers are included beyond the username visible in the chat message itself.

---

## Contact

Streamer: **SX_Faceoff** (Trovo)
