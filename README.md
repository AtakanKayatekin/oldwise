# Oldwise

**Learn or summarize any text on the web with AI, in your own language.**

Oldwise is a browser extension, backed by a Laravel service, that lets you select
any text on any web page, right-click, and instantly get a clear explanation or a
short summary, written in the language you choose.

> This repository is a public overview of the project. The source code lives in
> separate private repositories.

## What it does

Select text, right-click, and choose one of three actions:

- **Learn linguistically:** meaning, part of speech, structure, and (for verbs)
  the key conjugations.
- **Learn technically:** what the selection is and how it works, even for source
  code.
- **Summarize:** the key points of any passage, in seconds.

The answer appears in a small card on the page, written in your target language
(more than ten supported).

## Two ways to use it

- **Free, with your own key.** Bring your own AI provider key (Google Gemini,
  OpenAI, DeepSeek, or Anthropic Claude) and use Oldwise for free. With your own
  key, nothing is sent to Oldwise's servers.
- **Subscription.** No setup: use Oldwise's built-in AI through your account. Two
  tiers offer concise quick lookups or detailed, in-depth answers.

## Highlights

- Chrome Manifest V3 extension with on-demand injection (no broad "all sites"
  permission).
- One-click account connect using `chrome.identity` (no copying tokens by hand),
  with an explicit consent step.
- Cost-based usage metering: you are charged credits equal to the real token cost
  of each request, with a short 5-hour burst limit and a weekly limit whose
  unused credits carry over to the next week.
- Stripe subscriptions, with managed AI proxying that routes a stronger model to
  technical explanations.
- Privacy first: selected text is sent only to the AI that answers it. No
  tracking, no data selling.

## Architecture

- **Extension:** Chrome Manifest V3, vanilla JavaScript, a safe DOM-based Markdown
  renderer (no `innerHTML`), context menus, `chrome.storage`, `chrome.identity`.
- **Backend:** Laravel 13 (Livewire and Flux dashboard, Fortify auth, Sanctum API
  tokens, Cashier and Stripe), MySQL. A provider abstraction calls Gemini, Claude,
  OpenAI, or DeepSeek with our keys under the user's plan, measures the real cost,
  and enforces the limits.
- **Hosting:** a Ploi-managed server over HTTPS.

## Status

- Backend: live.
- Extension: submitted to the Chrome Web Store and in review.

## Links

- Website: https://oldwise.cosmobase.app
- Privacy policy: https://oldwise.cosmobase.app/privacy
- How usage and credits work: https://oldwise.cosmobase.app/credits

## Tech stack

`Chrome Extension (MV3)` &middot; `JavaScript` &middot; `Laravel 13` &middot;
`Livewire / Flux` &middot; `Sanctum` &middot; `Cashier / Stripe` &middot; `MySQL`
&middot; `Gemini` &middot; `Claude` &middot; `OpenAI` &middot; `DeepSeek`
