# Risk limits and safety

This page lists every limit and safety feature in PerpsCopier. They depend on the group type.

| Group type | Limits you set |
|---|---|
| Groups with Tradovate or Rithmic (Vest → futures, futures → Vest, futures → futures) | **Max size** and **Too small to copy**, per follower |
| Vest → Vest | **Max per trade ($)**, **Max open positions**, **Daily loss limit ($)**, under **Advanced** |

> The Vest → Vest limits do **not** apply to Tradovate or Rithmic followers. For those, use **Max size**.

## Test mode

**Test mode** sends nothing. The Copy Log shows what would have been sent. Use it whenever you change a group.

## Futures-style followers

### Max size

Caps a follower per market: for example 4 = never more than 4 contracts (or 4 Vest units for a Vest follower) per market, however big the leader's position. Empty = no limit. Set it on the follower's row on **Copy groups**.

### Too small to copy

When the leader's position is smaller than one contract (or Vest's smallest order) for this follower, it is skipped, unless **Copy as the minimum** is ticked. See [Copy groups](copy-groups.md#too-small-to-copy).

## Vest → Vest limits (Advanced)

Open **Advanced - Vest → Vest copying** under the Vest → Vest group. The limits are set once for the group and checked for **each Vest follower**.

| Limit | 0 means | What it does |
|---|---|---|
| **Max per trade ($)** | No cap | A copied order bigger than this dollar amount is cut down to fit. If even the smallest order is bigger, the trade is not copied. |
| **Max open positions** | No limit | When a follower already holds this many copied positions, a new leader position is not copied to it. |
| **Daily loss limit ($)** | Off | When a follower's balance falls this many dollars below its balance at the start of the day, Vest → Vest copying **pauses until midnight** (your computer's time). Open positions are not touched. |

Each skip or cut is written to the Copy Log.

**Max per trade** also caps TradingView signals. See [TradingView webhook](tradingview-webhook.md).

## Automatic safety

These work by themselves. You don't set them.

### Futures-style groups always stay in sync

- If an order fails or does not fill, only **that follower market** waits and tries again: after 5 s, 15 s, 30 s, then every minute.
- If the broker says the account is locked or blocked, it tries every 5 minutes. **Closing or reducing is always tried at once.**
- Every other follower keeps copying.
- Before every retry the app reads the account's **real position from the broker**, so a retry never doubles a position.

### Stops a follower that keeps getting undone

If one market keeps getting undone (6 orders in 2 minutes for the same leader position, for example a prop firm keeps flattening it), the app switches that follower's **Follow** off and shows why on the Cockpit. Its position is left alone. Switch Follow on again when you are ready.

### Vest → Vest pauses

| Cause | What happens |
|---|---|
| 3 failed copy orders in a row | Vest → Vest copying pauses and turns back on by itself after 5 minutes |
| A follower hits its daily loss limit | Vest → Vest copying pauses until midnight |
| Vest's live feed or login drops | Copying pauses and comes back by itself when Vest reconnects |

Trades the leader makes while copying is paused are **not** copied. A desktop notification tells you when copying pauses and resumes.

### Connections

- Nothing is sent while the leader's or a follower's connection is down.
- Positions are re-read from each broker regularly (Vest every 30 seconds, Tradovate and Rithmic every minute) in case a live feed goes quiet.
- The Vest connection renews your login by itself. If Vest goes quiet for over a minute, the app reconnects.

## Stopping and closing

| Action | Where | What it does |
|---|---|---|
| **Stop copying** | Cockpit, or tray menu **Stop engine** | Stops copying. Positions stay open. |
| **Ctrl+Shift+K** | Anywhere in Windows | Emergency stop: stops copying at once. **Positions stay open.** |
| **Flatten** (one account) | Cockpit row | Cancels that account's working orders and closes its positions at market. A Tradovate / Rithmic follower keeps following: if the leader is in a trade, it is put back in. Switch its Follow off first to keep it out. |
| **Flatten all** | Cockpit (Vest → Vest group) | Cancels every waiting order and market-closes every open position on the Vest leader and its Vest followers, including positions you opened by hand. Copying stays on. |
| **Cancel all orders** | Cockpit (Vest → Vest group) | Cancels every waiting limit or stop order on the Vest leader and its Vest followers. Positions and their stop loss / take profit are not touched. |
| **Stop & close all** | Cockpit | Turns copying off and market-closes every Vest leader position and every Vest position the app copied. **Tradovate / Rithmic positions and positions you opened by hand are not touched.** |

Logging out of PerpsCopier, or losing your plan once billing is on, also stops copying. Open positions are never touched.
