# What gets copied

PerpsCopier copies in two ways, depending on the accounts in a group:

- **Vest → Vest** copies each **order**, with its stop loss and take profit.
- **Anything with Tradovate or Rithmic** (Vest → futures, futures → Vest, futures → futures) keeps the follower's **position** equal to the leader's, using market orders.

## At a glance

| | Vest → Vest | With Tradovate / Rithmic |
|---|---|---|
| Market entries, adds, trims, closes | Yes | Yes |
| Reversals (long → short) | Yes | Yes, in one order |
| Leader's waiting limit order | When it fills (or rest the same limit: **Copy limit orders** in Advanced) | When it fills |
| Stop loss / take profit | Copied to the follower (see Advanced settings) | **Not placed.** The follower exits when the leader does. |
| Leverage | Matches the leader | - |
| Positions open before you press Start | No | No |

## Vest → Vest

Every leader order is copied to each Vest follower, sized by the follower's **× ratio**.

- **Entries, adds, partial closes and closes** are copied.
- **Leverage** on Vest followers always matches the leader's.
- **Stop loss and take profit** follow the settings under **Advanced - Vest → Vest copying** in the group:

| Setting | Recommended | What it does |
|---|---|---|
| **Copy stop loss** | On | Vest followers get their own stop, so they stay protected even if the app is off. Moving the leader's stop moves the followers' stops. |
| **Copy take profit** | Off | Off: followers still exit when the leader's target fills. On: followers rest their own targets. |
| **Copy limit orders** | Off | Off: when the leader's limit fills, followers copy it at market. On: followers rest the same limit. |

The Advanced section also holds the Vest → Vest risk limits. See [Risk limits and safety](risk-limits.md).

## Groups with Tradovate or Rithmic

The follower's position in each copied market is kept the same as the leader's (after sizing). When the leader's position changes, the follower is sent **one market order** to match it.

- **Entries, adds, trims, reversals and exits** are copied. A reversal (long 2 → short 2) is one order.
- **The leader's stop or target filling** is an exit like any other: followers are flattened with a market order.
- **Waiting limit orders** on the leader are copied **when they fill**, at market.

### Futures followers get no stop loss

> **Tradovate and Rithmic followers have no stop of their own.** They exit when the leader exits, including when the leader's stop fills. If the app is off when the leader's stop fills, the follower stays open until the app is back and catches up. **Keep the app running.**

The same applies to a Vest follower of a futures leader: it is held to the leader's position and exits when the leader exits.

### Market hours

Futures markets close every day (about 5-6 pm New York time) and at the weekend. While they are closed, a futures follower waits. It catches up when the market opens, if the gap still exists.

### If the app was closed

If the app is closed or restarted during a trade, it carries on when it comes back: a leader exit made meanwhile is copied.

## Positions open before Start

A position the leader **already holds** when you press **Start copying** is not copied. It would enter at an old price. That market starts copying with the leader's next trade.

Copying can only start when the leader and its followers have **no open positions** in the copied markets. Close them first.

## Prices

Followers enter at market a moment after the leader's fill, so prices can differ slightly. Vest prices and futures prices also differ from each other.

## TradingView alerts

A TradingView alert trades your **Vest leader**. Followers then copy that trade like any other leader trade. See [TradingView webhook](tradingview-webhook.md).
