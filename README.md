# Swapping, without the guesswork
**A redesign of the core swap flow in Jupiter, Solana's most-used swap aggregator**
Superteam India · Open Design Bounty · Gaurav Srivastava

## Why this flow
Swapping is the most-used action on Solana, and it's where new users get stuck and experienced users lose money to failed transactions. I run an on-chain arbitrage bot, so I've spent a lot of time on the exact settings most people never understand: slippage, priority fees and MEV. This redesign makes those decisions understandable without taking control away from experts.

## What I observed in the current experience
1. **The swap competes for attention.** On desktop the swap card sits between a collectibles promo, a lending carousel and a portfolio panel. The one thing the user came to do is not the visual focus.
2. **Jargon on the main screen.** A "Use V1 transactions (New)" toggle sits directly above the main button with no explanation of what it changes or why a user would turn it off.
3. **The settings that decide success are hidden.** Slippage, priority fee and MEV protection live behind a small settings icon next to "Ultra". These are the settings that decide whether a swap fails or gets a bad price.
4. **Failure is a dead end.** When a swap fails because the price moved past the slippage limit, the user typically sees an error and has to work out the cause and the fix alone.

## The redesign: three changes

### 1 · A swap card built around the decision
- One focused card. Promotions move out of the swap's way.
- Plain labels: **You pay / You get**, with the dollar value under each amount.
- A quote summary that answers the questions people actually have: **"You'll get at least"** (the guaranteed minimum after slippage), the rate, total fees, and the current protection mode.
- A live quote is visible before connecting a wallet, so people can check a price before committing.
- Mobile-first: token buttons never shrink, amounts take the remaining width, and the layout is the same on a 390 px phone and on desktop.

### 2 · "Swap protection" instead of hidden jargon
- The settings icon becomes a visible **🛡 Auto** chip at the top of the card, so users always know which protection is active.
- Three presets with one-line explanations:
  - **Auto (recommended):** slippage and fees set from live market conditions.
  - **Safe (lowest risk):** a tight 0.1% limit. It may fail in fast markets but never fills at a worse price than shown.
  - **Custom:** every knob, each with a one-line explanation (max slippage, priority fee, MEV protection).
- The "V1 transactions" toggle becomes **"Faster transactions — leave on unless your wallet has issues"** inside Custom, where only people who need it will look.
- Changing the preset immediately updates "You'll get at least", so the trade-off is visible.

### 3 · Failed swaps that explain themselves
- Say **what happened** in plain words: "SOL's price moved 0.7% while your swap was confirming, which is more than your 0.5% limit."
- **Reassure first:** "Your 500 USDC is safe. Only the network fee was used."
- Reframe the failure as protection: "This protected you from a worse price."
- **One-tap recovery:** "Retry with a 1% limit", showing the new guaranteed minimum before the user commits. "Keep my settings" is always available.
- Success confirms what the user actually got versus the guaranteed minimum, which builds trust in the protection settings.

## Design decisions and trade-offs
- **Defaults over options.** Most users should never open settings, so Auto is the default and its effect is shown in the quote, not hidden in a modal.
- **Experts lose nothing.** Every existing control is still in Custom, one tap away.
- **Same mental model on mobile and desktop.** Settings and status open as a bottom sheet on mobile and a centered dialog on desktop, with identical content.
- **Numbers before buttons.** The guaranteed minimum appears on the main card, the review screen and the retry option, so users never confirm a swap without seeing the worst case.

## Deliverables
- Figma file: before/after screens for each feature, mobile and desktop.
- Live prototype: interactive, with every state (swap, protection, review, failed, success).
- Screens: `after/mobile-*.png`, `after/desktop-*.png`; current experience in `before/`.

*Concept work for a design bounty. Not affiliated with Jupiter. Prices are illustrative.*
