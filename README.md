# 🃏 Kitti Score & Pot Calculator

A sleek, mobile-friendly, and fully offline web application to track scores, pots, and settlements for the game of **Kitti**.

Built with HTML, Tailwind CSS, and Vanilla JavaScript. No backend, no databases, no login required — all data stays safely in your browser.

## 🌟 Features

- **Player Management**: Add, remove, or rename up to 5 players (minimum 2).
- **Smart Cashing Out**: If a player leaves mid-game, their historical balances are preserved for settlement.
- **Dynamic Pot Tracking**: Automatically calculates the base antes and visualizes the pot growth over time.
- **Stacking Kitti Marks**: Mark Kitti as many times as it happens in a round. Each mark adds another ante from every player to the pot.
- **True Zero-Sum Ledger**: Automatically tracks who owes whom. It nets out pairwise debts (e.g., If A owes B ₹40, but B owes A ₹10, it shows A owes B ₹30).
- **UPI Deep Linking**: Save players' UPI IDs and tap "Pay" in the settlement screen to open your UPI app directly with the amount pre-filled.
- **Round History & CSV Export**: Keep a log of every round and export it to a spreadsheet.
- **Mobile-First Design**: A responsive UI with a sticky bottom action bar, giant touch targets, and collapsible settings for seamless one-handed use at the table.
- **Autosave & Undo**: Everything saves to `localStorage` automatically. Made a mistake? Hit the Undo button or press `Ctrl/Cmd + Z`.

---

## 🎮 How the Game Works (App Rules)

The app follows the standard Kitti mechanics:

1. **Base Ante**: Before a round starts, every active player puts in the base amount (e.g., ₹10).
2. **Kitti**: If a player declares Kitti, every player must put in *another* base ante. If someone marks Kitti again, they put in *another* ante. The pot stacks up.
3. **Resolving**: The winner of the round takes the entire pot (Base Antes + All Kitti Antes).

### The Zero-Sum Math
The app strictly enforces the rule: **Total Won = Total Staked**.
Because of this, the sum of all players' balances (`Won - Staked`) will always equal exactly **₹0**.

If Player 5 wins 1 Pot + 3 Kittis (with 5 players at ₹10 ante):
- The total pot is ₹200 (₹10 × 5 players × 4 rounds).
- Every player's "Staked" amount goes up by ₹40.
- Player 5's "Won" amount goes up by ₹200.
- Player 5's Balance is +₹160.
- The other 4 players' Balances are -₹40 each.
- **Total Balance:** `(+160) + (-40 × 4) = 0`.

---

## 📱 Mobile Experience

The dashboard was redesigned specifically for use on phones during live play:
- **Action Center at the top**: Pick a winner and mark Kitti without scrolling.
- **Sticky Bottom Bar**: The current pot and the "Resolve" button are always visible.
- **Card-based Leaderboard**: No horizontal scrolling or tiny tables on mobile; players are displayed as clean, stacked cards.
- **Thumb-friendly controls**: Large buttons for marking Kitti and resolving the round.

---

## 🚀 How to Run

Since this is a fully client-side application, there is no build step or installation required.

1. Download the `index.html` file.
2. Double-click it to open it in any modern web browser (Chrome, Safari, Edge, Firefox).
3. (Optional) Host it for free on **GitHub Pages**, **Netlify**, or **Vercel** so your friends can access it from their phones.

---

## 🛠️ Tech Stack

- **HTML5**: Semantic structure.
- **Tailwind CSS**: Utility-first styling via CDN (no build process).
- **Vanilla JavaScript**: No frameworks (React/Vue) — fast, lightweight, and easy to edit.
- **Canvas API**: Used for the confetti celebration and the pot sparkline.
- **Web Share API & Clipboard API**: For sharing the final scoreboard and settlement.

---

## 🔒 Privacy & Data

This app does not connect to any external servers. 
All game data (players, history, balances) is saved locally on your device using the browser's `localStorage`. Clearing your browser data or clicking "Reset Game" will permanently erase the current game.
