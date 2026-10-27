# Server actions: redirects must land on the final page

_Learned Oct 25, 2026 on bannquet.com (Next.js). Fixed in commits 8f45dfc and a follow-up on main._

## What happened
After signing in, the first form a person submitted crashed with a generic server error. The data never saved. Runtime logs showed nothing, because no app code ran.

## Root cause
A Next.js server action called `redirect('/auth/continue')`, and that URL was a route handler that sent a second 307 to the real page. A server-action redirect is a soft navigation: the client router records the first URL while the browser shows the final page. The next `<form action={serverAction}>` then POSTed to `/auth/continue`, and the GET-only route returned 405. The same thing happens with any HTTP-level hop after the action's redirect (route handler, middleware/proxy redirect such as an auth gate, or a `next.config` redirect). A `redirect()` inside a page component is fine.

## The rule
1. Never `redirect()` from a server action to a URL that redirects again. Redirect straight to the final page.
2. If the next stop must be a route handler (cookies, finishing auth), return `{ redirectTo }` from the action and do a full page load on the client (`window.location.assign`) through one shared hook.
3. Keep auth middleware off server-action POSTs (skip requests with the `next-action` header, e.g. matcher `missing: [{ type: 'header', key: 'next-action' }]`); each action checks the session itself and returns a friendly error.
4. Keep legacy-path redirects out of server-action targets and fallbacks.

## Verify
- Request logs: a 405 (or 404/307) on a POST to a GET-only route or a path you never post to. Runtime logs stay empty.
- Repro: trigger the redirect, then submit any form on the landing page; the URL looks right but the action POST goes to the old URL.
- Grep every `redirect(` in `'use server'` files and check each target against `route.ts` files, the middleware matcher, and `next.config` redirects.

## Reference
bannquet.com: commits 8f45dfc and follow-up on main.
