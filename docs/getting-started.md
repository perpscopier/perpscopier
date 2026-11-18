# Getting started

This page takes you from download to live copying. It takes about 10 minutes.

## What you need

- A PC with **Windows 10 or 11**. Mac is coming soon.
- The PC must stay on and online while you trade. Copying happens in the app on your computer, not on a server. An always-on PC or a Windows VPS works best.
- At least two trading accounts: one leader and one or more followers. They can be Vest, Tradovate or Rithmic accounts, in any mix.

## Quick start (5 steps)

1. **Install** PerpsCopier and sign in to your PerpsCopier account.
2. **Connect your accounts** on the **Connections** page.
3. **Create a copy group** on the **Copy groups** page: pick the leader, add followers, choose a size for each.
4. **Test it**: on the **Cockpit**, leave **Test mode** on and press **Start copying**. Trade on the leader. The **Copy Log** shows what each follower would get. Nothing is sent.
5. **Go live**: turn Test mode off. Followers now copy for real.

Each step is explained below.

## 1. Download and install

You can install PerpsCopier in two ways:

| Where | How |
|---|---|
| Website | Download the installer from [perpscopier.com](https://perpscopier.com/) ([direct link](https://perpscopier.com/download/PerpsCopier-Setup.exe)) and run it. |
| Microsoft Store | Install [PerpsCopier from the Microsoft Store](https://apps.microsoft.com/detail/XP9C95JGG768QZ). |

The website installer lets you choose the install folder and adds a desktop shortcut.

## 2. Create your PerpsCopier account

The first screen asks for your **PerpsCopier account**. This is not your Vest login. You connect Vest later.

1. Choose **New here? Create a free account**.
2. Enter your email and choose a password (at least 8 characters). Repeat the password.
3. Press **Create free account**.
4. Open the confirmation email and click the link. The app logs you in by itself.

No email after a minute? Check your spam folder, or press **Send the email again**.

Already have an account? Enter your email and password and press **Log in**. Forgot it? Press **Forgot password?**.

### One account, one computer

- One PerpsCopier account works on **one computer at a time**. Logging in on another computer signs the first one out.
- Only **one copy of PerpsCopier** can run on a computer, even across different Windows users. If it is already open for another Windows user, the new one explains this and closes. This stops the same accounts from being copied twice.

## 3. Connect your accounts

Open **Connections**. Log in to every broker you copy from or to:

- **Vest**: press **Log in to Vest**. Enter your email, then the 6-digit code Vest emails you.
- **Tradovate**: press **+ Connect Tradovate** and log in on Tradovate's own page.
- **Rithmic**: press **+ Connect Rithmic**, pick your firm's system, and enter your Rithmic user name and password.

Full details: [Connecting accounts](connecting-accounts.md).

## 4. Create your first copy group

Open **Copy groups**.

1. Press **+ New group** and give it a name, for example "NQ strategy".
2. Pick the **Leader**: the account you trade yourself.
3. Press **+ Add follower** and pick an account. Repeat for each follower.
4. Set each follower's **Size**. For futures followers, also look at **Markets**, **Max size** and **Too small to copy**. The green box under each follower shows an example for its own settings.
5. Changes save by themselves about a second after you make them. The top of the page says **All changes saved**.

Full details: [Copy groups and sizing](copy-groups.md).

### Turn Follow on (Tradovate and Rithmic followers)

A new Tradovate or Rithmic follower starts as **Not following**. On the **Cockpit**, switch its **Follow** on. Follow only switches on while that follower and its leader have **no open positions**.

## 5. Test mode

Always test a new or changed group first.

1. Open the **Cockpit**. Make sure **Test mode** is on.
2. Press **Start copying**.
3. Trade on the leader.
4. Open the **Copy Log**. Lines like "would sync … BUY 2" show what each follower would get. Nothing is sent to any broker.

Tip: try your setup on a Tradovate demo account or a Rithmic Paper Trading account first.

Copying can only **start** when the leader and its followers have no open positions in the copied markets. Close them first.

## 6. Go live

1. On the **Cockpit**, turn **Test mode** off.
2. The app asks you to confirm. From now on followers place **real orders**.

Good to know:

- One **Start / Stop** button runs every group.
- Copying stays on until you press **Stop**, even after a restart. You can change this in **Settings** (see [Settings](settings.md)).
- A position the leader **already holds** when you press Start is not copied. It would enter at an old price. That market starts copying with the leader's next trade.

## Keep the app running

- Closing the window does **not** stop copying. PerpsCopier keeps running in the **system tray** (by the clock). The first time, a notification tells you so.
- To stop copying, press **Stop copying** on the Cockpit, choose **Stop engine** in the tray menu, or press **Ctrl+Shift+K**.
- To quit the app, right-click the tray icon and choose **Quit**.
- Tick **Start with Windows** in Settings so the app opens in the tray when you log in to your computer.

The tray icon colour shows the state:

| Colour | Meaning |
|---|---|
| Green | Copying live |
| Amber | Test mode, or paused (it turns back on by itself) |
| Red | Halted |
| Grey | Stopped |

## Next steps

- [What gets copied](what-gets-copied.md)
- [Risk limits and safety](risk-limits.md)
- [Copy Log and alerts](copy-log-and-alerts.md)
