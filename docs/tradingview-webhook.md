# TradingView webhook

PerpsCopier gives you a **private webhook URL**. A TradingView alert (or any HTTP request) sent to it trades your **Vest leader** account. Your followers then copy that trade like any other leader trade, including Tradovate and Rithmic followers.

Set it up on the **TradingView** page in the app.

## How it works

TradingView can only call a public web address, and PerpsCopier runs on your computer. So alerts go to your private URL on perpscopier.com, which passes them on instantly to the app over a connection the app keeps open.

- Signals trade **only while copying is running**. **Stop copying** and **Ctrl+Shift+K** stop signals too.
- In **Test mode**, signals are only written to the log. Nothing is sent.
- **Nothing is queued.** A signal that arrives while the app is closed or offline is refused, never traded late.
- Signals run one at a time, and each signal at most once.
- Signals only trade **Vest** markets, on the Vest leader. If you have more than one group led by a Vest account, signals trade the leader of your Vest → Vest group.

## Set it up

1. Open the **TradingView** page.
2. Tick **Accept signals**.
3. Set **Max position per market from signals** (see [Size limits](#size-limits)).
4. Press **Create my webhook URL**. Press **Copy** next to it.
5. The status dot shows **Connected to perpscopier.com - ready for alerts**.
6. Press **Send a test signal**. It appears under **Recent signals** within a second as "Test received".

Keep the URL private. Anyone with it can send signals to your leader account, within your max. **Make a new URL** replaces it. The old one stops working at once, so update your TradingView alerts.

## Create the TradingView alert

1. In TradingView, create an alert.
2. Open **Notifications**, tick **Webhook URL** and paste your URL.
3. In **Message**, paste one of the messages below.

## Message format

The message is JSON:

| Field | Required | Values |
|---|---|---|
| `action` | Yes | `buy` or `long`; `sell` or `short`; `close`, `exit` or `flat`; `test` |
| `symbol` | Yes (except `test`) | The market. `{{ticker}}` works for most markets, or write the Vest name, for example `BTC-PERP`. |
| `usd` | Yes for buy / sell | The dollar size of the order |
| `sl` | No | Stop loss price. New positions only. |
| `tp` | No | Take profit price. New positions only. |
| `leverage` | No | Leverage to set before opening a new position |

### Examples

Strategy (buy and sell from the strategy):

```json
{"action":"{{strategy.order.action}}","symbol":"{{ticker}}","usd":5}
```

Buy:

```json
{"action":"buy","symbol":"{{ticker}}","usd":5}
```

Sell / short:

```json
{"action":"sell","symbol":"{{ticker}}","usd":5}
```

Close:

```json
{"action":"close","symbol":"{{ticker}}"}
```

Buy with stop loss and take profit:

```json
{"action":"buy","symbol":"BTC-PERP","usd":5,"sl":90000,"tp":110000}
```

## What each action does

| Leader holds | `buy` | `sell` | `close` |
|---|---|---|---|
| Nothing | Opens a long | Opens a short | Nothing to close |
| A long | Adds to the long, up to your max | Closes the long and opens a short | Closes the long |
| A short | Closes the short and opens a long | Adds to the short, up to your max | Closes the short |

- `sl` and `tp` are ignored when adding to a position.
- `sl` and `tp` must be on the right side of the price (for a long, stop below and target above). Otherwise the signal is refused.
- If you only want to exit, use `close`. A `sell` while long reverses to short.

## Symbols

`{{ticker}}` from TradingView is matched to a Vest market. The app understands, for example:

| TradingView sends | Vest market |
|---|---|
| `BTCUSDT.P`, `BINANCE:BTCUSDT`, `BTCUSD` | BTC-PERP |
| `NQ1!`, `MNQ1!`, `NAS100`, `US100`, `NDX100` | NDX |
| An exact Vest name, for example `BTC-PERP` or `AAPL-USD-PERP` | That market |

If no Vest market matches, the signal is refused with "no Vest market matches …". Use the Vest name instead.

## Size limits

A signal can never build a position bigger than the **lowest** of:

| Limit | Where it is set |
|---|---|
| **Max position per market from signals** | TradingView page (default $5) |
| Your plan's ceiling | Shown next to the box ("your … allows up to $…") |
| **Max per trade ($)** of the Vest → Vest group | Copy groups → Advanced (only if set) |

The page shows the limit in force: "Signals can build at most $… per market right now." A bigger signal is cut down to fit. An order under Vest's $1 minimum is raised to $1 when that still fits.

## Recent signals

The **Recent signals** list shows the last signals with a status. They also appear in the Copy Log.

| Status | Meaning |
|---|---|
| `done` | Traded (or, in Test mode, what would have been traded) |
| `test` | A test signal arrived |
| `rejected` | Not traded. The reason is shown, for example "copying is stopped" or "signals are turned off in the app". |
| `failed` | Sent to Vest but did not complete. Check Vest. |
