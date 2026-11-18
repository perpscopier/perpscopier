# Connecting accounts

All logins are on the **Connections** page. Log in to every broker you copy from or to, then set up who copies whom on **Copy groups**.

PerpsCopier supports:

| Platform | Accounts |
|---|---|
| **Vest Markets** | Your Vest accounts, including **Vest Capital** accounts |
| **Tradovate** | Prop firm accounts (for example Lucid, Apex, Tradeify), real-money accounts, and Tradovate's own demo / sim accounts |
| **Rithmic** | Rithmic Paper Trading, Rithmic-based prop firms (pick your firm's system in the list), and TradeSea firms |

## Vest

1. Press **Log in to Vest**.
2. Vest's login page opens inside the app. Enter your email.
3. Enter the **6-digit code** Vest emails you. There is no password.
4. The page closes by itself once you are in.

Your Vest accounts appear with their **balance** and **status**. The badge next to **Vest** shows **Logged in** and **Live feed connected**.

### Give your Vest accounts nicknames

Vest does not name accounts. Type a **nickname** next to each account, for example "Main" or "Prop 50K". Nicknames are used everywhere in the app. They are only shown in PerpsCopier.

### Vest Capital

Log in to your Vest Capital account on **Connections**, like any Vest account, and use it as a leader or follower.

Want a funded Vest account? The Connections page and Settings show a **Get one on Vest Capital** link. The code shown next to it gives **2.5% off** at checkout. Click the code to copy it.

### Show the Vest page

Once you are logged in, **Show Vest page** opens the Vest page the app uses. The app renews your Vest login by itself and reconnects on its own.

## Tradovate

1. Press **+ Connect Tradovate**.
2. Choose the type of account:
   - **Prop firm (Lucid, Apex, Tradeify…) or real-money account**. Prop firm accounts are sim accounts on Tradovate's demo server. PerpsCopier finds them there by itself.
   - **Tradovate's own demo / sim account**.
3. Optional: type a **Name** for this login.
4. Press **Log in with Tradovate**.
5. Your web browser opens **Tradovate's own login page**. Log in and approve.
6. Back in the app, the connection shows **Connected** with your accounts.

PerpsCopier **never sees your Tradovate password**. It only receives a login token.

### Adding another Tradovate user

Sign out of Tradovate in your browser first. Otherwise Tradovate logs in the user your browser is already signed in with. PerpsCopier refuses that, because the same account can't be connected twice.

### "Log in again"

If a Tradovate connection says **Log in again**, press it and log in on Tradovate's page again. Your copy groups are kept.

### Chart data and Tradovate

Copying and chart orders work on Tradovate accounts. Futures **candles** on the Chart come from a Rithmic login (see below). Tradovate only gives chart data to apps with its paid API market-data subscription.

## Rithmic

1. Press **+ Connect Rithmic**.
2. Pick the **system**: the firm that gave you the login. For example, an Apex account is **Apex Trader Funding**. For a practice login, pick **Rithmic Paper Trading**.
3. Enter your Rithmic **user name** and **password**.
4. Optional: type a **Name** for this login.
5. Press **Connect**.

Every account under that login is listed after you connect.

### Which user name?

Use your Rithmic **user name** (the login), for example `APEX-12345`. This is often your email or the name the firm sent you. Do **not** use an account number such as `APEX-12345-01`. All the login's accounts appear by themselves.

### The system list

The list has three parts:

| Group | What to pick |
|---|---|
| Rithmic | **Rithmic Paper Trading** |
| Prop firms | Your Rithmic-based prop firm. Pick the firm that gave you the login. |
| TradeSea (FundYourEdge and other TradeSea firms) | The TradeSea system your firm gave you |

The **wrong system is refused as "permission denied"**, even with the right password.

### Where the Rithmic login is kept

Your Rithmic login is stored **encrypted on this computer only**. The same Rithmic user can't be added twice.

### Use for chart data

Tick **Use for chart data** under a Rithmic login to see futures (NQ, ES, CL, GC…) on the Chart page.

Rithmic allows **one market-data session per login**. If you also watch prices on the same login in another platform (R|Trader, NinjaTrader, Quantower…), that platform's market data may be logged out. Copying and position sync are not affected.

## Managing connections

Each Tradovate or Rithmic login has a coloured dot and buttons:

| Item | Meaning |
|---|---|
| Green dot, **Connected · N accounts** | Working |
| Grey dot, **Connecting…** or **Connection lost - reconnecting…** | The app is reconnecting by itself |
| Red text, **Log in again** or **Error** | Needs you. Read the message. |
| **Reconnect** | Reconnects this login now |
| **Remove** | Deletes the login from this computer |

When you **Remove** a login, the app tells you which copy groups use its accounts:

- If one of its accounts is a **leader**, that group is deleted.
- If its accounts are **followers**, they are taken out of their groups.
- Positions already open are left as they are.

## Next step

[Create a copy group](copy-groups.md).
