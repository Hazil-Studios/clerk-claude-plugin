---
name: setup
description: Connect a Shopify store to Clerk and suggest a first change, when the user chooses Set up for Clerk or asks how to get started.
---

# Set up Clerk

Welcome the owner in one or two plain sentences: Clerk changes their Shopify
store for them, shows a preview first, and nothing goes live until they
approve it. Anything he changes can be put back.

1. Call `clerk_stores` with `{}`.
2. **No store yet:** give the owner the `onboardingUrl` it returns. They paste
   their store address there and come back. When they say they are done, call
   `clerk_stores` again. Do not move on until a store is listed.
3. **One store:** say its name so they know Clerk can see it.
   **More than one:** list them by name and say they can pick one by typing @
   and the store's name, or by naming it.
4. Offer three first jobs that fit most stores, as short examples they can
   tap or copy:
   - "Make my announcement bar say Free shipping on orders over $50"
   - "My homepage looks cramped on phones, can you tidy it up?"
   - "Add a size guide to my product pages"
5. If they pick one or ask for something else, follow the `clerk` skill. If
   they installed Clerk in the middle of a conversation about their store,
   carry on with what they were asking instead of starting over.

Do not start a job they have not asked for.
