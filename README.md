<p align="center">
  <img src="assets/logo.png" alt="WireUp logo" width="110" />
</p>

<h1 align="center">WireUp for Claude</h1>

<p align="center">
  <strong>Your own WhatsApp in Claude.</strong><br />
  Catch up on chats, search old messages, open photos and voice notes, and draft replies that wait for your approval.
</p>

<p align="center">
  <a href="https://wireup.chat">Website</a> ·
  <a href="https://wireup.chat/connect/claude">Setup guide</a> ·
  <a href="#example-prompts">Examples</a> ·
  <a href="#faq">FAQ</a> ·
  <a href="https://wireup.chat/privacy">Privacy</a>
</p>

---

## What is WireUp?

[WireUp](https://wireup.chat) connects your own WhatsApp account to the AI assistant you already use. You sign in with Google, link WhatsApp once by scanning a QR code (the same way you link WhatsApp Web), and add one connector link to Claude. There is nothing to install or keep running on your computer.

This repository is the Claude package for WireUp: setup steps, a Claude Code plugin and a short skill that tells Claude how to use WireUp well. It contains no server code, no account data and no credentials. The connector itself is hosted at `https://wireup.chat/mcp`.

## Set it up

First, create your account at [wireup.chat](https://wireup.chat): sign in with Google and scan the QR code with WhatsApp (**Settings → Linked devices → Link a device**).

### claude.ai, Claude Desktop and the Claude phone app

1. In Claude, open **Settings → Connectors → Add custom connector**.
2. Name it **WireUp** and paste `https://wireup.chat/mcp`.
3. Choose **Connect** and sign in with the same Google account.

Custom connectors work on every Claude plan; the free plan allows one. Once added on claude.ai, WireUp also works in the desktop and phone apps.

### Claude Code

Either add the connector directly:

```bash
claude mcp add --transport http --scope user wireup https://wireup.chat/mcp
```

or install this repository as a plugin, which also adds the WireUp skill:

```text
/plugin marketplace add eitza-tech/wireup-for-claude
/plugin install wireup@eitza-tech
```

Then type `/mcp` and sign in with the same Google account.

## Example prompts

| Goal | Ask Claude |
|---|---|
| Catch up | "What did I miss on WhatsApp today?" |
| Summarize a group | "Summarize this week in my family group. Anything I need to answer?" |
| Find something | "When did Dana send me the address for Sunday?" |
| Voice notes | "What did my brother say in his last voice note?" |
| Draft a reply | "Draft a reply to Sam saying I'll be 10 minutes late." |
| Send a file | "Send this PDF to the project group." |

## What it can do

| Area | Tools |
|---|---|
| Catch up and read | `catch_up`, `list_chats`, `read_chat`, `load_older_messages`, `list_statuses` |
| Search | `search_messages`, `search_contacts`, `group_info`, `message_info` |
| Photos, voice notes and files | `get_media` (voice notes come back as text, documents as text) |
| Send, always as a draft first | `send_message`, `send_media` (photos, stickers, GIFs, voice notes, files), `send_poll`, `send_location`, `forward_message`, then `confirm_send` |
| Manage | `react_to_message`, `edit_message`, `delete_message`, `chat_settings`, `mark_as_read` |
| Status | `whatsapp_status` |

## Sending stays in your hands

- Every send is a draft until you confirm it, unless you turn confirmation off yourself.
- Messages go only to chats you already have, with a daily limit and an off switch.
- Reading your chats never marks them as read on your phone.

## FAQ

**Is it free?** Yes, WireUp is free for now.

**Is this an official WhatsApp product?** No. WireUp links to your account as a linked device, the same way WhatsApp Web does. It is not made by, affiliated with or endorsed by WhatsApp or Meta, and it doesn't use the WhatsApp Business API. Use it for your own conversations and within WhatsApp's terms.

**Where are my messages kept?** In a storage space that belongs to your account alone, so Claude can catch you up and search even when your phone is slow to answer. You can keep only the last 30 days, six months or a year, and delete everything at any time from your dashboard. What Claude reads is processed by Anthropic as part of your conversation. Details: [wireup.chat/privacy](https://wireup.chat/privacy).

**Does it work with the WhatsApp Business app?** It links like WhatsApp Web, so any account that can link a device can be used.

**Can I use it in other AI apps too?** Yes: ChatGPT, Gemini, Grok, Perplexity, Cursor and any app that supports remote MCP connectors. See [wireup.chat/connect](https://wireup.chat/connect).

## Troubleshooting

| What you see | What to do |
|---|---|
| "WhatsApp is not linked" | Open [wireup.chat](https://wireup.chat) and scan the QR code again. |
| Claude asks you to sign in again | Choose Connect in Settings → Connectors (or `/mcp` in Claude Code). |
| A send was refused | Check the daily limit and the sending switch on your dashboard. |

## Support

Email [contact@eitza.tech](mailto:contact@eitza.tech).

## Trademarks and license

WhatsApp is a trademark of Meta Platforms, Inc. Claude is a trademark of Anthropic. WireUp is an independent service by Eitza Tech and is not affiliated with, sponsored or endorsed by Meta, WhatsApp or Anthropic.

The files in this repository are released under the [MIT License](LICENSE). The WireUp service itself is not open source.
