# LQ Playbook indicator (TradingView, Pine Script v6)

Marks the parts of [PLAYBOOK.md](../PLAYBOOK.md) that can be detected from
price alone. File: [`lq_playbook.pine`](lq_playbook.pine).

## Install

1. In TradingView, open the **Pine Editor** at the bottom of the chart.
2. Delete the template code, paste the full contents of `lq_playbook.pine`,
   then click **Save** and **Add to chart**.
3. Use it on a **5m or 1m** chart, which is the "Now" timeframe. The 1H and
   4H zones are pulled in automatically.

If TradingView shows a compile error, send me the error text and line number.

## What each mark means

| On the chart | Playbook step | Meaning |
|---|---|---|
| Orange / aqua thick lines | Where | Previous **week** high / low (buy-side / sell-side liquidity) |
| Orange / aqua thin lines | Where | Previous **day** high / low |
| Yellow lines | Where, Monday filter | Monday high / low, drawn from Tuesday on |
| Grey background | Monday filter | Monday. No setups fire on Monday (can be switched off) |
| Teal / red boxes labelled `1H FVG`, `4H FVG` | When (Step 1) | Unfilled 1H / 4H fair value gaps. A box disappears once price passes through it |
| Purple boxes labelled `BPR` | When (Step 1) | Overlap of a bullish and a bearish FVG on the same timeframe |
| Dotted lines at swing highs / lows | Liquidity | Swing liquidity: stops resting above highs / below lows |
| Solid thick lines + `EQH` / `EQL` | Liquidity, boosters | Equal highs / lows: the most obvious stop clusters. They also act as boosters between entry and target |
| Line turns grey and dashed | Step 3 | That liquidity has been taken |
| `BSL taken` / `SSL taken` label | Step 3 | Buy-side / sell-side liquidity taken, listing which pools (PDH, PWH, MonH, EQH, swing H, ...) |
| `RSI bear div` / `RSI bull div` | Step 3 | At the sweep, price made a new extreme but RSI did not (compared with RSI at the swept swing) |
| `BOS` | Inducement context | Close beyond the most recent swing |
| `BOS (IDM?)` | Step 2 (inducement) | A BOS while a 1H/4H zone in the trade direction still hasn't been reached. Traders acting on it may be entering early, and their stops become fuel |
| `SHORT setup` / `LONG setup` + small `entry FVG` box | Step 4 | Liquidity taken + 1H/4H zone tapped + 3-candle displacement, all within the bar window. Shows suggested SL and TP |
| `SELL` / `BUY` + dashed lines | Step 5 | Conservative entry: price came back into the entry FVG and printed an engulfing candle. Red dashed = stop, green dashed = target |
| Table, top right | Checklist | Which conditions are met right now for a short and for a long |

### How the setup rules are coded

- **Displacement:** the middle candle's body is at least `1.2 × ATR(14)`, the
  3rd candle closes the same way, and the three candles leave an FVG.
- **Stop loss:** beyond the last opposite-colour candle before the
  displacement (the order block), plus `0.1 × ATR`. If there is no order
  block, it uses the swing extreme.
- **Target:** the nearest opposing 1H/4H FVG or BPR that is still open
  (TP2 in the playbook). TP1 and the TP3 runner are left to you.

## Alerts

Right-click the chart, choose **Add alert**, pick **LQ Playbook**, then one of:

- Step 1: price reached a bullish / bearish 1H/4H zone (the "set an alert and walk away" step)
- Step 3: liquidity taken inside a zone
- Step 4: long / short setup
- Step 5: long / short entry

## Settings to set yourself

- **Allowed direction.** Set this from your own Weekly/Daily analysis
  (the "Where" step): `Bearish only` or `Bullish only`. `Auto` uses a
  simple rule I made up (the daily close above the prior day's high counts
  as bullish, below the prior day's low as bearish). It is not from the
  podcast.
- **Require RSI divergence.** Off by default, because the playbook says
  divergence shows up in 80–85% of valid setups, not all of them.
- **Swing length / equal tolerance.** Raise these on noisy 1m charts.

## What it does not do

- **Pick the Weekly/Daily draw on liquidity.** The indicator shows the levels.
  Deciding which one price is heading for is your call.
- **"Caviar".** It doesn't check whether the sweep tapped a smaller hidden
  FVG/OB.
- **Volume.** Displacement is measured by candle size, because many forex
  feeds have no real volume.
- **SMT divergence.** It would need a second symbol.
- **Position sizing and the TP1/TP3 split.**

Signals are guides to the checklist, not trade instructions. Backtest on
replay and demo-trade before using real money.
