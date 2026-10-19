# Clerk for Shopify (Claude)

Clerk changes your Shopify store for you: tell him what you want, see a preview, and nothing goes live until you approve it. Every change can be undone.

Clerk is a store operator for Shopify merchants. Tell him what you want changed,
like a page, a product, your menu or your homepage, and he does the work on a
private copy of your store. You see the change before shoppers do, approve it in
the chat, and can put it back later. Clerk holds your store's access himself, so
Claude never sees your Shopify credentials.

## Install

In Claude Code or Cowork:

```
/plugin marketplace add Hazil-Studios/clerk-claude-plugin
/plugin install heyclerk@heyclerk
```

In Claude (claude.ai, Desktop, mobile): Settings, Connectors, then find Clerk in
the directory. The connector is the remote server `https://mcp.heyclerk.so/mcp/v1`, where Clerk does the work.
This plugin uses the same address, `https://mcp.heyclerk.so/mcp/v1`. Clerk recognises Claude Code
there, so the model does the work itself, with Clerk's signing proxy and approval card.

You need a Shopify store connected to Clerk first. Start at https://heyclerk.so.

## Help

- Guide: https://heyclerk.so/claude
- Support: https://heyclerk.so/support
- Privacy: https://heyclerk.so/privacy
- Terms: https://heyclerk.so/terms
