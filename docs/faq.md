# FAQ

## General

**What is PerpsCopier?**
A Windows desktop app that copies your trades from one account (the leader) to your other accounts (the followers). It works with Vest Markets perps (including Vest Capital), Tradovate futures and Rithmic futures, in any direction.

**Which computers does it run on?**
Windows 10 and 11. Mac is coming soon.

**Does it run in the cloud?**
No. Copying happens in the app on your computer. Keep it running while you trade. Use an always-on PC or a Windows VPS.

**Does closing the PerpsCopier window stop copying?**
No. The app keeps running in the system tray. Press **Stop copying** on the Cockpit or **Ctrl+Shift+K** to stop copying. Right-click the tray icon and choose **Quit** to close the app.

**Can I use one PerpsCopier account on two computers?**
One account works on one computer at a time. Logging in on another computer signs the first one out. Only one copy of the app can run on a computer.

**Is PerpsCopier made by Vest, Tradovate or Rithmic?**
No. PerpsCopier is an independent tool and is not affiliated with or endorsed by Vest Markets, Tradovate or Rithmic.

## Platforms

**Can I copy trades from Vest to Tradovate or Rithmic?**
Yes. Make your Vest account the leader and a Tradovate or Rithmic account a follower. Each follower's position is kept the same as the leader's, sized by the same dollar size or by a dollar amount per contract.

**Can I copy futures to Vest?**
Yes. NQ / MNQ copy to NDX, ES / MES to SPX, and more. See [the mapping tables](copy-groups.md#futures--vest-standard-pairs).

**Can I copy one Tradovate or Rithmic account to several prop accounts?**
Yes. Make the account you trade the leader and add each prop account as a follower. Tradovate and Rithmic accounts can be mixed in one group, and every follower is sent its order at the same time.

**Which Rithmic prop firms work?**
Rithmic Paper Trading, Rithmic-based prop firms (pick your firm's system in the list when you connect) and TradeSea firms. See [Connecting accounts](connecting-accounts.md#rithmic).

**Does it work with Vest Capital?**
Yes. Log in to your Vest Capital account on **Connections**, like any Vest account.

**Does PerpsCopier see my Tradovate password?**
No. You log in on Tradovate's own page in your browser. The app only receives a login token. Rithmic logins are stored encrypted on your computer only. Vest uses its own email code login.

## Copying

**How is the size worked out between Vest and futures?**
Either the same dollar size as the leader (10 NDX on Vest = 5 MNQ) or a fixed dollar amount per contract (at $3, every $3 of NDX on Vest = 1 MNQ). Sizes are always rounded down, and **Max size** can cap each follower.

**Are positions that were already open copied when I press Start?**
No. Copying them would enter at an old price. That market starts copying with the leader's next trade.

**Do Tradovate and Rithmic followers get a stop loss?**
No. They exit when the leader exits, including when the leader's stop fills. Keep the app running so followers can follow.

**Do Vest followers get a stop loss?**
In a Vest → Vest group, yes, with **Copy stop loss** on (recommended). Followers then stay protected even if the app is off.

**Can I test without placing real orders?**
Yes. With **Test mode** on, the app only writes what it would send to the Copy Log. Turn Test mode off to go live.

**Can I trade a follower by hand?**
Switch its **Follow** off on the Cockpit first. While Follow is on, a Tradovate / Rithmic follower, or a Vest follower of a futures leader, is held to its leader's position. Vest → Vest followers copy orders and are not held.

**What are the risk limits?**
Futures-style followers have **Max size** per market. Vest → Vest groups have **Max per trade**, **Max open positions** and a **Daily loss limit**. See [Risk limits and safety](risk-limits.md).

**Can I trade from TradingView alerts?**
Yes, on your Vest leader. See [TradingView webhook](tradingview-webhook.md).

## Account and billing

**How much does it cost?**
PerpsCopier is free during the beta; the app shows your plan in Settings. When billing starts, there is a 5-day free trial. See [perpscopier.com](https://perpscopier.com/) for current pricing, and [Billing](billing.md).

**What happens to my positions if my plan ends or I log out?**
Copying stops. Open positions are not touched.

**How do I earn by referring people?**
Settings → **Refer a friend**. See [Settings](settings.md#refer-a-friend).

**How do I update the app?**
It updates itself. See [Updates](updates.md).

**Where do I get help?**
Email support@perpscopier.com, or open an [issue](https://github.com/perpscopier/perpscopier/issues).
