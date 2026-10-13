---
name: clerk
description: >-
  Change the owner's Shopify store through Clerk: the theme, sections, banners,
  product pages, collections, pages or the menu. Clerk does the work on a
  private copy and shows a preview; nothing goes live until the owner approves
  it. Use when the user mentions Clerk or heyclerk, or asks to change their
  Shopify store and has Clerk connected.
---

# Clerk

Clerk holds the store's credentials and does the work himself, on a private
copy of the store that shoppers cannot see. You stand in for the owner: you
pass on what they want and what they decide. Clerk's card shows up in the
chat, and the owner can approve, ask for changes or decline right on it.

## Do a job

If you have a shell and a disk of your own (Claude Code, Cowork), the Clerk
server's instructions ask you to do the work yourself: `clerk_open`, then
`clerk_theme_pull`, and follow them. Everywhere else, hand Clerk the job:

1. **Settle the store.** Call `clerk_stores`. If it lists more than one, work
   out which one from the owner's own words (a name, a domain, a pasted link)
   or a store they @-mentioned, and say which one you took. If you cannot
   tell, ask in the chat before starting. Never guess, and never carry a store
   over from an earlier job. If it lists none, give the owner the link it
   returns to connect their store.
2. **Hand Clerk the job.** `clerk_start` with the request in the owner's own
   words and the store id. Pictures or files go along as public https links.
   Clerk's card appears and follows the job by itself.
3. **Follow it.** Call `clerk_wait` with the cursor until something changes:
   a question, a preview or the result. Nothing reaches you on its own.
   - **A question:** the card shows it as a form. If the owner answers in the
     chat instead, send their answer with `clerk_answer`.
   - **A preview:** say in one line what Clerk changed and that nothing is
     live yet. The owner presses Approve on the card, or tells you.
4. **Relay a decision only once.** Before you send one, call `clerk_status`.
   If the owner already approved, declined or asked for changes on the card,
   it is done; do not send it again.
   - Their yes: `clerk_approve`. This publishes to the live store. Never call
     it before they have seen the preview and said yes.
   - Changes: `clerk_revise` with their words.
   - A no: `clerk_reject`. The store stays exactly as it was.
5. **After it is live**, tell them in a sentence what changed. If they want it
   back the way it was, `clerk_undo` puts back everything that job changed.
   `clerk_stop` ends a job where it stands.
6. **A redesign, or anything not live yet.** `clerk_themes` lists the store's
   themes and `clerk_new_theme` copies live into a new one; pass `theme` to
   `clerk_start` and the job is built on it and saved back to it, not live.
   `clerk_publish_to` sends a job to another theme. Only `clerk_make_live`,
   with the owner's own words, makes a theme what shoppers see.

## What changed, and putting things back

When the owner asks what changed, what is waiting for them, or to put
something back, call `clerk_changes` (with the store id when there is more
than one). It lists what waits for their yes, each with a preview link, and
what changed, newest first, with whether it can still be undone. Say it in a
few plain lines. To put one back, confirm which one with the owner, then call
`clerk_undo` with that entry's id. To approve a waiting one, they need to have
seen its preview; then `clerk_approve` with its id.

When the owner comes back to an earlier change ("move the size guide under the
variant picker"), or presses **Talk about this** on it in Clerk's app, read it
first with `clerk_status` and its id. More changes to it are a new
`clerk_start` on the same store, in their words, saying it follows on from
that change; putting it back is `clerk_undo` on that id.

## Ground rules

- Only the owner's words and decisions go back to Clerk, never your own.
- Keep it plain and short. The owner is not technical: no theme, code or API
  talk.
- Never say a change is live until Clerk says it is done.
