# LQ Playbook indicator (TradingView, Pine Script v6)

Marks the parts of [PLAYBOOK.md](../PLAYBOOK.md) that can be detected from
price alone. File: [`lq_playbook.pine`](lq_playbook.pine).

## Install

1. In TradingView, open the **Pine Editor** at the bottom of the chart.
2. Delete the template code, paste the full contents of `lq_playbook.pine`,
   then click **Save** and **Add to chart**.
3. Use it on a **5m to 15m** chart. On 1H and above, the 1H/4H zones are
   switched off, and almost every bar takes a swing high or low, so the chart
   fills with labels. An orange banner at the bottom warns you when the
   timeframe is too high.

If TradingView shows a compile error, send me the error text and line number.

## Making it easier to read

Open the indicator settings (double-click its name on the chart), **Display** group:

| Setting | Default | What it does |
|---|---|---|
| Mode | **Clean** | Clean shows only the key items: day/week/Monday levels, equal highs/lows, sweeps of those or sweeps inside a 1H/4H zone, possible inducement, setups and entries. Detailed adds every swing line, every sweep and every BOS |
| Draw labels/lines for the last N bars | 300 | Older history is left blank |
| Show the nearest N zones above and below price | 3 | Hides far-away 1H/4H zones. They come back when price gets close |
| Text size | Normal | Small / Normal / Large for labels and the table |
| Checklist position | Top right | Moves the table into a corner that doesn't cover candles |

Other changes that cut clutter:
- The settings values no longer show next to the indicator name on the chart.
- Previous day/week and Monday levels are drawn only for the current period,
  with a name tag at the right edge (`PDH`, `PWL`, `Mon H`, ...). The tag
  changes to `(taken)` and the line turns dashed once price trades through.
- Sweep labels are short, for example `✕ PDH EQH · div`. **Hover over a
  label** to see the full explanation: which pools were taken, whether RSI
  diverged, whether price was inside a 1H/4H zone, and why it might be
  inducement.
- In Clean mode, a swing line is deleted once its liquidity is taken.

## What each mark means

| On the chart | Playbook step | Meaning |
|---|---|---|
| `PWH` / `PWL` thick lines | Where | Previous week high / low |
| `PDH` / `PDL` thin lines | Where | Previous day high / low |
| `Mon H` / `Mon L` yellow lines | Where, Monday filter | Monday high / low, drawn from Tuesday on |
| Grey background | Monday filter | Monday. No setups fire on Monday (can be switched off) |
| Boxes labelled `1H bearish FVG`, `4H bullish FVG` | When (Step 1) | Unfilled 1H / 4H fair value gaps. A box disappears once price passes through it |
| Purple `BPR` boxes | When (Step 1) | Overlap of a bullish and a bearish FVG on the same timeframe |
| Thick solid line + `EQH` / `EQL` | Liquidity, boosters | Equal highs / lows: the most obvious stop clusters |
| Dotted lines (Detailed mode) | Liquidity | Ordinary swing highs / lows |
| Orange `✕ ...` label above a candle | Step 3 | Buy-side liquidity taken. Names the pools. `· div` = RSI bearish divergence |
| Aqua `✕ ...` label below a candle | Step 3 | Sell-side liquidity taken. `· div` = RSI bullish divergence |
| Pink `IDM?` label | Step 2 (inducement) | A break of structure before price reached the 1H/4H zone in that direction. Traders acting on it may be early, and their stops become fuel |
| `BOS` (Detailed mode) | Context | Close beyond the most recent swing |
| `SHORT setup` / `LONG setup` + `entry zone` box | Step 4 | Liquidity taken + 1H/4H zone tapped + 3-candle displacement, within the bar window. Hover for SL / TP |
| `SELL` / `BUY` with red SL and green TP lines | Step 5 | Price came back into the entry zone and printed an engulfing candle |
| Table | Checklist | Each step for short and long, a score out of 5, and the next 1H/4H target |

### How the setup rules are coded

- **Displacement:** the middle candle's body is at least `1.2 × ATR(14)`, the
  3rd candle closes the same way, and the three candles leave an FVG.
- **Stop loss:** beyond the last opposite-colour candle before the
  displacement (the order block), plus `0.1 × ATR`. If there is no order
  block, it uses the swing extreme.
- **Target:** the nearest opposing 1H/4H FVG or BPR that is still open
  (TP2 in the playbook). TP1 and the TP3 runner are left to you.

## Alerts

Right-click the chart, choose **Add alert**, pick **LQPlaybook**, then one of:

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
