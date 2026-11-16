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
| Mode | **Clean** | **Minimal**: levels, 1H/4H zones, setups and trades only. **Clean**: adds small markers for sweeps and possible inducement. **Detailed**: every swing line, every sweep and every BOS, with text |
| Draw markers/lines for the last N bars | 200 | Older history is left blank |
| Show the nearest N zones above and below price | 2 | Hides far-away 1H/4H zones. They come back when price gets close |
| Text size | Small | Small / Normal / Large for labels and the table |
| Min bars between inducement markers | 30 | Stops `IDM?` markers stacking up in a choppy range |
| Inducement only within x ATR of the zone | 6 | Only marks inducement when the untouched zone is close |
| Checklist position | Top right | Move the table if it sits under your drawing toolbar |

**Hover over any marker** to see the full explanation: which pools were
taken, whether RSI diverged, whether price was inside a 1H/4H zone, and why
it may be inducement.

## What each mark means

| On the chart | Playbook step | Meaning |
|---|---|---|
| `PWH` / `PWL` thick lines | Where | Previous week high / low. Tag says `(taken)` and the line turns dashed once traded through |
| `PDH` / `PDL` thin lines | Where | Previous day high / low |
| `Mon H` / `Mon L` yellow lines | Where, Monday filter | Monday high / low, drawn from Tuesday on |
| Grey background | Monday filter | Monday. No setups fire on Monday (can be switched off) |
| Boxes `1H FVG ▼`, `4H FVG ▲` | When (Step 1) | Unfilled 1H / 4H fair value gaps (▲ bullish, ▼ bearish). A box disappears once price passes through it |
| Purple `BPR` boxes | When (Step 1) | Overlap of a bullish and a bearish FVG on the same timeframe |
| Thick solid line + `EQH` / `EQL` | Liquidity, boosters | Equal highs / lows: the most obvious stop clusters |
| Orange ▼ above a candle | Step 3 | Buy-side liquidity taken. Has text (`PDH`, `EQH`, ...) only for key pools. A plain marker is a swing high taken inside a bearish zone |
| Aqua ▲ below a candle | Step 3 | Sell-side liquidity taken. Same rules |
| Yellow ▼ / ▲ | Step 3 | Liquidity taken **with RSI divergence** |
| Pink ◆ `IDM?` | Step 2 (inducement) | A break of structure just before price reached a nearby 1H/4H zone. Traders acting on it may be early, and their stops become fuel |
| `BOS`, dotted swing lines | Detailed mode only | Every break of structure and every swing |
| `SHORT setup` / `LONG setup` + `entry` box | Step 4 | Liquidity taken + 1H/4H zone tapped + 3-candle displacement. Hover for SL / TP |
| `SELL` / `BUY` with red and green boxes | Step 5 | Entry triggered. Red box = risk to the stop, green box = reward to the 1H/4H target, with the risk-to-reward ratio |
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
