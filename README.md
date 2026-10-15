# Nitrino MCP server

Remote MCP server of [Nitrino](https://nitrino.ai), the AI sales agent for B2B teams.
Connect it to Claude, ChatGPT or any MCP client and run your sales from the chat: find people
for a segment, read conversations, approve letters, start campaigns, book meetings.

- URL: `https://nitrino.ai/mcp`
- Transport: Streamable HTTP
- Auth: OAuth. You sign in to Nitrino and choose what the client may do.
- Registry: `ai.nitrino/nitrino` in the [official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=ai.nitrino)
- Docs: https://nitrino.ai/docs/mcp

This repository holds no code: the server runs at nitrino.ai. It is here so you can find it,
read what it does and open an issue.

## Connect

**Claude:** Settings → Connectors → Add custom connector → `https://nitrino.ai/mcp`

**ChatGPT:** add a custom connector with the MCP server URL `https://nitrino.ai/mcp`

**Any MCP client:**

```json
{
  "mcpServers": {
    "nitrino": {
      "type": "http",
      "url": "https://nitrino.ai/mcp"
    }
  }
}
```

## What it can do

- Find new people for a segment in every source at once: `search_all_sources`, `collect_from_sources`, `find_people`
- Work with the inbox: `list_conversations`, `get_conversation`, `send_message`
- Run outbound campaigns: `create_campaign`, `approve_campaign_letters`
- Meetings: `get_calendar`, `book_meeting`
- Everything Nitrino and your CRM know about a person: `get_person_card`

Every tool acts as one member of one workspace and sees only what that member sees.
A send means queued, not delivered: the workspace's queue hands it over within each account's
daily limit.

## About Nitrino

Nitrino finds your B2B buyers in its own base and on LinkedIn, researches each one along with what
your HubSpot or Pipedrive knows about them, writes to them from your own LinkedIn, email, Telegram,
WhatsApp and Instagram accounts in your voice, answers your website chat and keeps the conversation
going until the meeting is booked. More at https://nitrino.ai/docs.
