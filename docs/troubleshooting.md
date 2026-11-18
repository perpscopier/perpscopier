# Troubleshooting

Start with the **Copy Log** (set the filter to **Problems**). It says what happened and why, in plain words.

## Copying

### A follower did not copy a trade

- Find the trade in the Copy Log.
- **"not copied"** means it was too small for the follower's size. Raise the size, or tick **Copy as the minimum**.
- **"leader already holds"** means the position was open before you pressed Start. That market starts copying with the leader's next trade.
- A **"waiting for … connection"** line means a login dropped. Check **Connections**.
- **Not following** on the Cockpit: switch the follower's **Follow** on.
- Check the follower's **Markets**: an unticked market is not copied.
- For Vest → Vest, check the **Advanced** limits: **Max open positions** or **Max per trade** may have skipped it.

### Follow won't switch on

Follow only switches on while the follower **and** its leader have **no open positions**. Close them first. The reason is shown on the follower's row.

### Copying won't start

Copying can only start when the leader and its followers have no open positions in the copied markets. The Cockpit shows why it can't start, for example:

| Message | What to do |
|---|---|
| "Vest live feed is not connected yet…" | Wait a few seconds for the Vest page to finish loading, then try again. |
| "Pick a leader on Copy groups first." / "Add a follower on Copy groups first." | Finish your copy group. |
| "Log in to your PerpsCopier account first." | Log in to the app. |
| "Start your PerpsCopier free trial to keep copying." | See [Billing](billing.md). |
| "Could not confirm your PerpsCopier account for 72 hours." | Check your internet connection. |

### "accepted but did not fill"

The broker accepted an order but the account never showed it. The app reads the account from the broker and sends only what is still missing, a few seconds later. Copying never stops for this. If it keeps happening, check the account in Vest, Tradovate or Rithmic.

### "refused the order" / "Account refused orders"

The broker or prop firm refused the order and gave a reason, shown in quotes. For example, "Order can be placed by administrators only" means the firm has locked that account (a rule was hit, or the account is maxed out or expired).

The app keeps trying every 5 minutes, and closes at once when the leader closes. Fix it with the firm, or remove that account from the group.

### "Stopped following"

The app switched a follower's Follow off because one market kept getting undone (6 orders in 2 minutes for the same leader position), for example a prop firm kept flattening it. Its position is left alone. Fix the cause, then switch Follow on again.

### Copying paused by itself

Read the reason on the Cockpit or in the Copy Log:

- 3 failed Vest → Vest orders in a row: it turns back on after 5 minutes.
- Daily loss limit hit: Vest → Vest copying turns back on after midnight.
- Vest connection dropped: it turns back on when Vest reconnects.

Trades the leader made while paused were not copied. Check the Cockpit.

### Follower prices differ from the leader's

Followers enter at market a moment after the leader's fill, so prices can differ slightly. Vest and futures prices also differ from each other.

### A futures follower is still open after the leader's stop filled

Futures followers have no stop of their own. They exit when the leader exits. If the app was off, the follower catches up when the app is back. Keep the app running on an always-on PC or VPS.

### Futures follower is waiting

**Market closed**: futures markets close every day (about 5-6 pm New York time) and at the weekend. The follower catches up when the market opens.

## Connections

### No Vest accounts are listed

Log in to Vest on **Connections** with your email and the 6-digit code Vest emails you.

### Tradovate says "Log in again"

Press **Log in again** on Connections and log in on Tradovate's page. Your groups are kept.

### Tradovate connects the wrong user, or refuses a second user

Tradovate logs in the user your browser is already signed in with. Sign out of Tradovate in your browser, then connect again. The same account can't be connected twice.

### A Tradovate prop account is missing

Choose **Prop firm (Lucid, Apex, Tradeify…) or real-money account** when you connect. Prop firm accounts are sim accounts on Tradovate's demo server, and the app finds them there.

### Rithmic says "permission denied"

The system is wrong. Remove the connection and add it again with the firm that gave you the login. Also check that you used your Rithmic **user name**, not an account number.

### Another platform lost its Rithmic prices

Rithmic allows one market-data session per login. If **Use for chart data** is ticked for that login, untick it, or use a different login for chart data.

### No futures on the Chart

Tick **Use for chart data** under a Rithmic login on **Connections**. Tradovate logins don't give chart data.

## The app

### "PerpsCopier is already running on this computer"

Only one copy can run on a computer, even across Windows users. Quit it in the other Windows user first (tray icon → **Quit**), then start it again.

### I was signed out

One PerpsCopier account works on one computer at a time. Logging in on another computer signs the first one out. Log in again.

### The confirmation email didn't arrive

Check your spam folder, or press **Send the email again**. Still nothing after a few minutes? Email support@perpscopier.com.

### I closed the window but copying is still running

That is by design. The app keeps running in the system tray. To quit, right-click the tray icon and choose **Quit**.

### TradingView signals are rejected

Open **Recent signals** on the TradingView page and read the reason. Common ones:

| Reason | Fix |
|---|---|
| "signals are turned off in the app" | Tick **Accept signals** |
| "copying is stopped: press Start Copying in the Cockpit" | Start copying |
| "no Vest market matches …" | Use the Vest name, for example `BTC-PERP` |
| "already holding ~$… here; your max is $…" | Raise your signal max, or close first |
| "stop loss … is on the wrong side of the price" | Fix the `sl` / `tp` in the alert |

See [TradingView webhook](tradingview-webhook.md).

## Still stuck?

Email **support@perpscopier.com** with what you see in the Copy Log, or open an [issue](https://github.com/perpscopier/perpscopier/issues).
