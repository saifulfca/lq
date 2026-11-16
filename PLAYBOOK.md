# Liquidity Trading Playbook

Based on the liquidity method Noah teaches on the PropFirmTrader podcast
([YouTube](https://www.youtube.com/watch?v=Acp1E-VyhZw)).

> **About the source.** This playbook expands a Gemini-generated summary of the
> episode. I could not open the video myself, so the `[hh:mm:ss]` timestamps
> come from that summary and have **not** been checked against the video.
> Anything I added that was not in the summary (explanations, the long-side
> mirror example, the checklists) is marked **[Added]**. Section 10 lists the
> points worth checking in the video.
>
> This is educational material, not financial advice. Backtest and demo-trade
> it before risking money.

---

## Contents

1. [The whole method on one page](#1-the-whole-method-on-one-page)
2. [Glossary in plain language](#2-glossary-in-plain-language)
3. [Part 1: Why liquidity moves the market](#3-part-1-why-liquidity-moves-the-market)
4. [Part 2: Filters that decide whether a trade is allowed](#4-part-2-filters-that-decide-whether-a-trade-is-allowed)
5. [Part 3: Top-down analysis (Where, When, Now)](#5-part-3-top-down-analysis-where-when-now)
6. [Part 4: The 6-step execution playbook](#6-part-4-the-6-step-execution-playbook)
7. [Part 5: Podcast case study, fully annotated](#7-part-5-podcast-case-study-fully-annotated)
8. [Part 6: Mirror example for a long trade [Added]](#8-part-6-mirror-example-for-a-long-trade-added)
9. [Checklists and trade journal [Added]](#9-checklists-and-trade-journal-added)
10. [Points to verify in the video](#10-points-to-verify-in-the-video)

---

## 1. The whole method on one page

```
 WHERE  (Weekly / Daily)   Which big pool of stops is price heading for?
   │                        → gives you the direction (bias)
   ▼
 WHEN   (4H / 1H)          Which 1H or 4H FVG / BPR will price reach after
   │                        clearing the smaller pools on the way?
   │                        → gives you the zone. Set an alert. Walk away.
   ▼
 NOW    (5m / 1m)          Price is in the zone. Watch for:
                             1. Inducement   early traders enter too soon
                             2. Sweep        their stops get taken
                             3. RSI divergence on the sweep
                             4. Displacement fast, heavy move the other way
                             5. Entry        retrace into the new 5m/1m FVG
                             6. Exits        TP at opposing 1H / 4H FVGs
```

**The one rule above all others:** if you cannot point at the pool of
liquidity that was just taken, do not trade. If you can't see who got
trapped, you are probably the one being trapped [00:11:47].

### Long vs short at a glance

| Item | Short setup (sell) | Long setup (buy) |
|---|---|---|
| HTF target (Where) | Price is drawn **up** into a Daily/Weekly high, then expected to fall | Price is drawn **down** into a Daily/Weekly low, then expected to rise |
| Zone (When) | Bearish 1H/4H FVG or BPR **above** current price | Bullish 1H/4H FVG or BPR **below** current price |
| Inducement | Early **sellers** short too soon. Their stops sit **above** lower highs | Early **buyers** buy too soon. Their stops sit **below** higher lows |
| Sweep | Price spikes **above** the inducement highs | Price spikes **below** the inducement lows |
| RSI divergence | Price makes a **higher high**, RSI makes a **lower high** | Price makes a **lower low**, RSI makes a **higher low** |
| Displacement | Strong bearish candles leave a **bearish** 5m/1m FVG | Strong bullish candles leave a **bullish** 5m/1m FVG |
| Entry | Retrace **up** into that FVG, sell on rejection | Retrace **down** into that FVG, buy on rejection |
| Stop loss | **Above** the order block that sits above the FVG | **Below** the order block that sits below the FVG |
| Targets | 1H/4H FVGs and lows **below** | 1H/4H FVGs and highs **above** |

---

## 2. Glossary in plain language

| Term | Plain meaning | What it looks like on the chart |
|---|---|---|
| **Liquidity** | Orders that are waiting and haven't been filled yet: stop losses and pending entries [00:08:22] | Clusters just beyond obvious highs, lows, and trendlines |
| **Buy-side liquidity** | Buy orders resting **above** highs (short sellers' stops + breakout buy orders) | Above swing highs, equal highs, descending trendlines |
| **Sell-side liquidity** | Sell orders resting **below** lows (buyers' stops + breakdown sell orders) | Below swing lows, equal lows, rising trendlines |
| **Liquidity sweep / stop hunt** | Price pokes past a high or low, fills those orders, then reverses | A wick or brief break beyond the level, followed by a fast move back |
| **Equal highs / equal lows (EQH / EQL)** | Two or more highs (or lows) at roughly the same price. "Relative" equal means close, not exact | Double top / double bottom |
| **Internal liquidity** | Small swing highs/lows **inside** a move [00:18:48] | Minor pullbacks within a trend leg |
| **External liquidity** | The main swing high/low at the **edge** of the range [00:19:32] | The top or bottom of the whole leg |
| **Break of Structure (BOS)** | Price breaks the last swing high (uptrend) or swing low (downtrend) | What structure traders treat as a trend signal |
| **Inducement** | An early, tempting setup that pulls traders in **before** the real move. Their stops become fuel | A small BOS, a bounce, or a 3rd trendline touch just before your HTF zone |
| **Trap** | The result of inducement: traders who entered early get stopped out | The sharp move that wipes out the inducement level |
| **Fair Value Gap (FVG)** | A 3-candle pattern where the middle candle moved so fast it left a price range only traded once (an imbalance) [00:37:38] | See diagram below |
| **Balanced Price Range (BPR)** | Where a bullish FVG and a bearish FVG overlap. Treated as a strong zone [00:19:58] | The overlapping slice of two opposite gaps |
| **Order Block (OB)** | The last opposite-colour candle before a strong move. Where large orders are assumed to have entered | Last up-candle before a sharp drop (bearish OB), last down-candle before a sharp rally (bullish OB) |
| **Breaker Block** | An order block that failed (price broke through it) and now acts from the other side | A former bullish OB that price broke and now rejects from below |
| **Displacement** | A sudden, high-volume, fast move that shows large orders have been triggered [00:39:34] | 2–3 large-bodied candles in a row, often leaving an FVG |
| **Premium / Discount** **[Added]** | Upper half / lower half of a price range. Sell in premium, buy in discount | Draw a range from swing low to swing high; above 50% is premium |
| **RSI divergence** | Price makes a new extreme but RSI does not. Suggests the push is running out of force [00:36:54] | Price HH + RSI LH (bearish); price LL + RSI HL (bullish) |
| **SMT divergence** **[Added definition]** | Two correlated markets disagree, e.g. EURUSD makes a new high but GBPUSD does not | Mentioned in the podcast as a trap signal [00:31:22] |
| **"Caviar"** | Noah's name for the best case: the sweep also taps a hidden lower-timeframe FVG or OB [00:37:14] | Sweep wick ends exactly inside a small FVG/OB |
| **Booster** | A pool of liquidity between your entry and target that pulls price toward the target [00:55:10] | Equal lows/highs or a trendline sitting in the path |

### How to draw an FVG

```
 BEARISH FVG (price falling)            BULLISH FVG (price rising)

   ┃  candle 1                                       ┃ candle 3
   ┃  low of candle 1 ─────┐                         ┃  low of candle 3 ─────┐
                           │  GAP = FVG                                     │ GAP = FVG
      █  candle 2 (big)    │                      █ candle 2 (big)          │
      █                    │                      █                         │
      █  high of candle 3 ─┘                  ┃   high of candle 1 ─────────┘
         ┃ candle 3                           ┃ candle 1

 FVG = between candle 1's LOW and          FVG = between candle 1's HIGH and
       candle 3's HIGH                           candle 3's LOW
```

If candle 1's wick and candle 3's wick overlap, there is no gap and no FVG.

---

## 3. Part 1: Why liquidity moves the market

### 3.1 Why price has to go back and grab orders

1. A bank wants to buy a very large position. If it buys all at once, it
   pushes price up against itself and gets a worse average price [00:09:20].
2. So it buys in pieces. The push leaves part of the order unfilled at the
   starting area [00:09:46].
3. Price is later brought back to that area so the bank can fill the rest,
   hedge, or close earlier pieces at breakeven. Only then does the real move
   start.
4. To fill a big **buy**, the bank needs a lot of **sellers**. The easiest
   sellers to find are the stop losses of traders who are already long
   (stops sit below lows) and breakout traders selling below support. That's
   why price dips below obvious lows before rallying.

**What this means for you:** the move that "breaks" an obvious level is often
the move that fills the big player, not the real direction.

### 3.2 Where retail stops pile up

Noah maps four common retail approaches and where each one leaves its stops
[00:10:48]:

| Retail approach | How they enter | Where their stops (liquidity) sit |
|---|---|---|
| Market structure | Buy the higher low after a BOS in an uptrend [00:04:06] | Just below every swing low, just above every swing high [00:10:48] |
| Support & resistance | Buy after several bounces off a flat floor [00:04:53] | Stacked under equal lows, above equal highs [00:11:07] |
| Trendlines | Buy the 3rd or 4th touch of a diagonal line [00:06:06] | Just under the trendline at every touch [00:11:18] |
| SMC / ICT order blocks | Buy blindly at the first untouched order block [00:06:40] | Just beyond the obvious mid-range order blocks, before the extreme zone [00:11:30] |

```
 Uptrend, seen as liquidity                  Trendline liquidity

        HH                                          /  ← 4th touch, buyers
       /  \      HH                                /
      /    \    /                                 /•  stops ×
     /      HL /   ← buyers enter here           /
    /    ×××××     ← their stops = sell-side    /•  stops ×
   HL                 liquidity                /
 ×××××                                        /•  stops ×
                                               ↑ one fast wick under the line
                                                 takes ALL of these at once
```

### 3.3 Internal vs external liquidity

- **Internal**: the small swing points inside a leg [00:18:48].
- **External**: the high or low at the end of the leg.
- Typical sequence: price retraces, clears the internal swings, taps a
  deeper imbalance (FVG/BPR), then goes for the external high or low
  [00:19:32].

**Practical use:** if internal liquidity is still sitting between price and
your zone, expect price to take it first. An FVG sitting **above** untouched
internal lows (for a long) is often a trap [00:31:22].

### 3.4 M, W and H patterns

These are the shapes the "grab orders, then move" cycle tends to leave
[00:23:49]–[00:24:22]:

- **W**: a double bottom where the second low sweeps the first, taps an FVG,
  then rallies (bullish).
- **M**: a double top where the second high sweeps the first, taps an FVG,
  then drops (bearish).
- **H**: a high-volume impulse where a Breaker Block and an FVG line up.

> The Gemini summary labels M as bullish and W as bearish. That is the
> reverse of the usual shapes (M = top, W = bottom), so I've used the
> conventional meaning. Check this in the video (see section 10).

---

## 4. Part 2: Filters that decide whether a trade is allowed

These are pass/fail. If one fails, there is no trade.

| Filter | Rule | Why |
|---|---|---|
| **Liquidity taken** | A specific pool (EQH/EQL, swing point, trendline) must have just been swept [00:11:47] | Without a sweep, there are no trapped traders to fuel your move |
| **1H minimum FVG** | Your entry zone and your take profit must both be at least a 1H FVG (4H or Daily is better) [00:20:16] | Smaller gaps don't attract enough orders. No 1H+ FVG, no trade [00:20:25] |
| **HTF alignment** | The trade must point toward the Weekly/Daily draw [00:28:49] | Noah says about 90% of liquidity traders lose by fading every 5m/1H sweep without checking the higher timeframe |
| **Monday filter** | Don't trade Monday. Mark Monday's high and low, trade from Tuesday [00:25:44] | In Noah's ~300 manual backtests, price came back to Monday's high or low 80–87% of the time [00:25:15]. Monday's range becomes a weekly liquidity target |

**Using the Monday range [Added explanation]:** on Tuesday, mark Monday's
high (buy-side liquidity) and Monday's low (sell-side liquidity). If your
bias is bearish, a sweep of Monday's high into a bearish 1H/4H FVG is a
strong "When" zone, and Monday's low is a natural target.

---

## 5. Part 3: Top-down analysis (Where, When, Now)

Always go from big to small, in this order [00:29:14]:

| Phase | Timeframes | Who trades here | Your question |
|---|---|---|---|
| **WHERE** | Weekly, Daily | Swing and position traders ("big liquidity") [00:22:09] | Is price heading for a Daily/Weekly high or low? |
| **WHEN** | 4H, 1H | Day traders ("medium liquidity") [00:21:43] | Which 1H/4H FVG or BPR will price reach after clearing internal liquidity? [00:29:36] |
| **NOW** | 5m, 1m | Scalpers ("small liquidity") [00:21:23] | Has the sweep, divergence and displacement happened inside my zone? [00:32:18] |

### 5.1 WHERE (Weekly / Daily): find the skeleton

Mark on the chart:
1. The last clear Weekly and Daily swing highs and lows.
2. Equal highs and equal lows (the most obvious stop clusters).
3. Unfilled Daily/Weekly FVGs.
4. Previous week's high/low and Monday's high/low.

Decide: **which of these pools is price most likely to reach next?** That's
your draw on liquidity. Your trades must point toward it, or come from a
sweep of the opposite pool.

### 5.2 WHEN (4H / 1H): find the zone

1. List every unmitigated 1H and 4H FVG and any BPR in the direction of
   your bias.
2. Cross out any FVG that still has untouched internal liquidity beyond it.
   Price will likely run through that FVG to take the liquidity first
   [00:31:22]–[00:31:52].
3. The zone you keep is usually the **extreme** one: the last FVG/BPR beyond
   the liquidity pool.
4. Set a price alert at the zone and stop watching lower timeframes until it
   fires [01:23:17].

### 5.3 NOW (5m / 1m): time the entry

Only open the 5m/1m charts **after** price is inside the zone. Then run the
6 steps below.

---

## 6. Part 4: The 6-step execution playbook

Each step is written for a **short**. For a long, flip every direction
(see the long vs short table in section 1).

### Step 1: Mark the 1H/4H zone (When)

- **Do:** pick one unmitigated 1H or 4H FVG/BPR that matches your
  Weekly/Daily bias [00:33:24]. Set an alert.
- **Pass:** the zone is at least 1H, it's in the direction of the HTF draw,
  and there is liquidity just before it.
- **Common mistake:** choosing the first FVG price reaches instead of the one
  beyond the liquidity.

### Step 2: Inducement (let the early traders in)

- **Do not** leave a limit order sitting at the zone [00:33:42].
- As price approaches, watch for retail-style signals right outside your
  zone: a small BOS, a flat floor/ceiling, a trendline, a lower-timeframe OB
  [00:34:08].
- Those early entries create **new** equal highs/lows or a trendline. That
  new pool is the fuel for the sweep [00:34:49].
- **For a short:** early sellers short before price reaches your bearish
  zone. Their stops sit above the small highs they shorted from.
- **Pass:** you can point at a specific new pool of stops.

### Step 3: Sweep + RSI divergence + "caviar"

- **Sweep:** price breaks the inducement level and takes those stops
  [00:35:07].
- **RSI divergence (5m or 1m):** for a short, price makes a higher high
  while RSI makes a lower high [00:35:37]. Noah sees this in roughly 80–85%
  of valid setups [00:36:54]. It suggests the push is a stop hunt, not a real
  breakout [00:36:18].
- **Caviar (best case):** the sweep wick also lands inside a small hidden
  lower-timeframe FVG or OB [00:37:14].
- **Pass:** sweep confirmed. Divergence is a strong confirmation, not
  required in every case (it shows up in 80–85%, not 100%).

### Step 4: Displacement (proof the big orders hit)

Look for a 3-candle push away from the sweep [00:41:25]–[00:41:53]:

```
  Short example (5m or 1m)

     ┃  ← candle 1: rejection / first shift (wick at the sweep high)
     █
     █  ← candle 2: big, high-volume candle down. Leaves a 5m/1m FVG
     █
     █  ← candle 3: closes lower too. Confirms momentum
```

- **Minimum:** at least a 5m engulfing candle or a clear 1m high-volume burst
  [00:47:01].
- **Pass:** the drop is clearly faster and heavier than the climb into the
  sweep.
- **Common mistake:** entering on a slow drift down. Without displacement,
  the sweep may just be the start of a real breakout.

### Step 5: Entry and the two-layer stop loss

**Entry options:**
- **Aggressive:** sell on the close of the 5m engulfing candle [00:41:04].
- **Conservative (Noah's preference):** wait for price to pull back up into
  the new 5m/1m FVG and sell when it rejects [00:42:18].

**Stop loss:** above the order block that sits just above your entry FVG
[00:42:58].

```
   ── stop loss ─────────────────────  just above the OB
   ░░░ ORDER BLOCK ░░░░░░░░░░░░░░░░░  Plan B: deeper wick is absorbed here
   ▒▒▒ FVG (entry) ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒  Plan A: price rejects here straight away
           │
           ▼  trade direction
```

- **Plan A:** volume is strong, price drops straight from the FVG [00:44:44].
- **Plan B:** price wicks into the OB. Either the OB launches the move late,
  or you get a reaction there to close at breakeven or a small loss if
  momentum dies [00:44:50].

### Step 6: Boosters and take profits

- **Boosters:** pools of liquidity between you and your target (equal lows,
  a rising trendline for a short). Price tends to be pulled through them
  [00:55:10].
- **Exit plan:**

| Level | Where | Action |
|---|---|---|
| TP1 | First structural reaction | Close nothing (0%). Watch. Move stop to breakeven if momentum weakens [01:03:37] |
| TP2 | Opposing 1H FVG (main target) | Close 70–80% [01:04:00] |
| TP3 | 4H FVG or Daily swing high/low (runner) | Let the last 20–30% run here [01:04:07] |

---

## 7. Part 5: Podcast case study, fully annotated

**Trade:** bearish reversal (short), live, Friday, September 11
[01:06:14]–[01:09:39]. The summary doesn't name the instrument.

### 7.1 The picture

```
 Price
   ▲
   │                                            (D) 1m EQH swept ── final stops gone
   │                                             ╱╲  ← (E) inside 15m BPR + OB = "caviar"
   │  ═══ DAILY RELATIVE EQUAL HIGHS ═══════════╱══╲═══  ← (C) buy-side liquidity taken
   │        ↑ 4H rejections here               ╱    ╲      RSI: lower high = bearish divergence
   │  . . . . 4H trendline liquidity . . . . .╱      ╲
   │                                         ╱        ╲▄▄ (F) displacement: fast, heavy drop
   │      (B) early sellers short the       ╱          ▒▒  ← (G) retrace into PREMIUM FVG,
   │          lower highs / 15m FVGs  ╱╲   ╱           ▒▒      1m bearish engulf = SHORT
   │          stops ×× above them    ╱  ╲ ╱              ╲     SL above OB above this FVG
   │                          ╱╲    ╱    ╳ ← stops of (B)  ╲
   │                         ╱  ╲  ╱       get taken        ╲  TP1  1H FVG
   │                        ╱    ╲╱                          ╲ TP2  1H FVG
   │          (A) 15m BOS: swing low broken                   ╲ TP3  1H FVG
   │                                                           ╲ TP4  1H FVG
   │                                                            ╲ TP5 1H FVG
   └──────────────────────────────────────────────────────────────────────▶ time
```

(Schematic. Drawn from the summary's description, not from the actual chart.)

### 7.2 Step-by-step, with the reason for each element

#### Where: Daily and 4H (HTF direction, big liquidity)

- **What Noah saw:** two relative equal highs on the Daily [01:06:38]. On
  the 4H, price had been rejected from the same ceiling several times
  [01:06:46]. Price had also reacted to a lower 4H FVG earlier, and a 4H
  trendline of liquidity sat below the highs [01:10:29].
- **Liquidity:** equal highs plus repeated rejections mean lots of short
  sellers with stops just above, plus breakout buyers waiting there. That's a
  large pool of **buy-side liquidity**.
- **Why it matters:** a big short needs a lot of buyers to sell into. Those
  stops above the equal highs provide them. So price was likely to go **up
  through** the highs first, and only then fall [01:10:53].
- **HTF conclusion:** short **after** the Daily highs are swept. Not before.

#### Inducement and traps: 1H and 15m

- **What happened:** before reaching the Daily highs, price dropped hard on
  the 1H/15m, broke a swing low (a BOS) and printed lower highs [01:08:15].
- **Inducement:** that BOS looks like a clean "trend has turned down" signal.
  Structure traders shorted the lower highs. SMC/ICT traders shorted the
  bearish 15m FVGs [01:08:59].
- **Trap:** they were right about direction but early. The Daily highs were
  still untouched. Their stops sat above the lower highs, which made them
  fuel for the move up [01:09:14].
- **Lesson:** a lower-timeframe BOS against an unswept HTF pool is an
  invitation, not a signal.

#### Sweep, RSI divergence and caviar: 15m and 1m

- **Sweep:** price turned up, took out the lower highs (stopping the early
  sellers), cleared the 4H trendline liquidity and pushed just above the
  Daily equal highs [01:12:15]. Each of these is a separate pool, taken in
  order from nearest to farthest.
- **RSI divergence:** price made a higher high above the Daily highs while
  RSI made a lower high. That's bearish divergence [01:12:21].
- **Caviar:** on the 15m and 1m, the top of the sweep landed inside an
  unmitigated **15m BPR plus an order block** [01:13:01], and at the same
  moment took one last pair of **1m equal highs** [01:14:13].
- **Why price stopped there:** every visible buy-side pool above was gone,
  and price was sitting in a strong opposing zone. Nothing left to pull it
  higher [01:14:48].

#### Displacement: 1m / 5m

- **What happened:** right after the 1m equal highs were swept inside the
  BPR, price fell sharply on high volume, clearly faster than the slow climb
  up [01:15:07].
- **Meaning:** the climb was buyers getting filled (and stops getting taken).
  The fast drop is the big seller's orders hitting the market [01:15:25].

#### Entry and stop: premium FVG, Plan A / Plan B

- **FVGs:** the drop left several bearish FVGs [01:16:09].
- **Choice:** Noah skipped the lowest one (too close to price, so the stop
  would be large relative to the target) and waited for price to return to
  the **higher FVG, in premium** [01:16:16].
- **Trigger:** price tapped that FVG and printed a **1m bearish engulfing**
  candle. Short entered [01:16:41].
- **Stop:** just above the order block sitting above the FVG [01:16:57].
  Plan A: drop straight from the FVG. Plan B: the OB absorbs a deeper wick.

#### Targets and result: 1H

- **Targets:** five stacked 1H FVGs below, used as TP1–TP5 [01:17:41].
- **What happened:** price kept respecting new bearish FVGs and OBs on the
  way down [01:20:23]. The trade reached about **1:10 risk-to-reward**, with
  the full swing reaching about 1:50 [01:20:02]. Profit was over **$4,000**,
  closed before the weekend [01:21:03].

### 7.3 Summary map

| Playbook step | Concept | What it was in this trade |
|---|---|---|
| Where | HTF draw on liquidity | Daily relative equal highs + repeated 4H rejections [01:06:38] |
| 1. Zone | 1H/4H zone | Area just above the Daily highs, which held the 15m BPR + OB |
| 2. Inducement | Early sellers | 15m BOS, lower highs, bearish 15m FVGs shorted too soon [01:08:59] |
| 3. Sweep + divergence + caviar | Stop hunt | Lower highs → 4H trendline → Daily EQH → 1m EQH, into 15m BPR/OB, with bearish RSI divergence [01:12:15]–[01:14:13] |
| 4. Displacement | Big orders hit | Fast, heavy 1m/5m drop after the 1m EQH sweep [01:15:07] |
| 5. Entry + SL | Premium FVG, Plan A/B | 1m bearish engulf in the higher FVG; SL above the OB [01:16:41]–[01:16:57] |
| 6. Targets | 1H FVGs | Five 1H FVGs as TP1–TP5; about 1:10 R:R, $4K+ [01:17:41]–[01:21:03] |

> The general exit rule in Step 6 uses three levels (TP1/TP2/TP3 with
> 0% / 70–80% / 20–30%). In this case study Noah lists five 1H FVGs. The
> summary doesn't say how he split the position across them.

---

## 8. Part 6: Mirror example for a long trade [Added]

**This example is made up** to show the same steps on the buy side. It is
not from the podcast.

```
 Price
   ▲
   │                                                          TP3  4H FVG / Daily high
   │                                                    ╱     TP2  1H FVG (close 70–80%)
   │          (B) early buyers buy the higher lows     ╱      TP1  first reaction (0%)
   │              stops ×× below them   ╲╱            ╱
   │                           ╲╱      ╳ ← their stops taken   SL below OB below this FVG
   │      (A) 15m BOS up     ╱    ╲   ╱           ▒▒  ← (G) retrace DOWN into DISCOUNT FVG,
   │                        ╱      ╲ ╱            ▒▒      1m bullish engulf = LONG
   │  . . . 4H trendline liquidity  ╲          ▀▀╱ (F) displacement: fast, heavy rally
   │  ═══ DAILY EQUAL LOWS ══════════╲════╱═══  ← (C) sell-side liquidity taken
   │        ↑ 4H bounces here          ╲╱  ← (E) inside 15m BPR + OB
   │                                  (D) 1m EQL swept. RSI: higher low = bullish divergence
   └───────────────────────────────────────────────────────────────▶ time
```

| Step | What you'd see | Reason |
|---|---|---|
| Where | Daily equal lows with repeated 4H bounces; Weekly bias is up | Buyers' stops sit below the lows. A big buyer needs those sellers |
| 1. Zone | Bullish 1H FVG / BPR just below the Daily lows | Extreme zone beyond the liquidity |
| 2. Inducement | 15m BOS up and higher lows before the Daily lows are taken; traders buy early | They create new sell-side liquidity below their higher lows |
| 3. Sweep | Price drops through the higher lows, the trendline, the Daily lows and a pair of 1m equal lows, into the BPR | All sell-side pools taken. RSI makes a higher low |
| 4. Displacement | 3 strong bullish candles leave a 1m/5m FVG | Big buy orders hit |
| 5. Entry | Pullback into the higher-quality FVG in discount, 1m bullish engulf | Better risk-to-reward than chasing |
| 5. Stop | Below the OB under the FVG | Plan A/B protection |
| 6. Targets | First reaction, then 1H FVG above (70–80%), runner to 4H FVG / Daily high | Opposing gaps and buy-side liquidity are the draw |

---

## 9. Checklists and trade journal [Added]

### 9.1 Pre-trade checklist

Each line must be "yes". One "no" means no trade.

**Week / day**
- [ ] It's not Monday. Monday's high and low are marked.

**Where (Weekly / Daily)**
- [ ] I can name the HTF pool price is heading for (e.g. "Daily equal highs at X").
- [ ] My trade direction matches that draw, or comes after that pool was swept.

**When (4H / 1H)**
- [ ] My zone is an unmitigated 1H or 4H FVG/BPR (not smaller).
- [ ] No untouched internal liquidity remains between price and my zone.
- [ ] An alert is set. I'm not watching the 1m/5m until it fires.

**Now (5m / 1m)**
- [ ] Inducement: I can point at early traders and where their stops are.
- [ ] Sweep: that pool has been taken.
- [ ] RSI divergence on the 5m or 1m (strongly preferred).
- [ ] Caviar: the sweep tapped a small LTF FVG/OB (bonus).
- [ ] Displacement: at least a 5m engulfing or a clear 1m volume burst.
- [ ] Entry FVG chosen for good risk-to-reward (not the one closest to the extreme).
- [ ] Stop beyond the order block behind the FVG.
- [ ] TP2 is a 1H FVG or better. Boosters noted between entry and target.

### 9.2 Journal template

```
Date / session:
Instrument:
Direction:            Long / Short
WHERE  (W/D draw):
WHEN   (1H/4H zone):
Inducement (who got trapped, where were their stops):
Pools swept, in order:
RSI divergence:        Yes / No   (timeframe: )
Caviar:                Yes / No   (what was tapped: )
Displacement:          (describe the 3 candles)
Entry:                 Aggressive / Conservative   Price:
Stop loss:             Price:        Plan A or B played out?
TP1 / TP2 / TP3:
Boosters in the path:
Result (R multiple):
What I'd do differently:
Screenshots: HTF | 1H/4H | 5m/1m entry | exit
```

### 9.3 Risk management

The summary says nothing about position size or risk per trade. Choose your
own risk per trade before using this method, especially on a prop-firm
account with daily loss limits.

---

## 10. Points to verify in the video

These come from the Gemini summary and look inconsistent or incomplete:

1. **M vs W.** The summary calls M bullish and W bearish
   [00:23:49]–[00:24:03]. The usual meaning is the opposite. Section 3.4
   uses the usual one.
2. **Instrument and year** of the case study (only "Friday, September 11" is
   given).
3. **Position split** across the five TPs in the case study, compared with
   the three-level rule in Step 6.
4. **H pattern.** The summary's description is short. Check whether Noah
   ties it to a specific entry rule.
5. **RSI settings.** No period (e.g. 14) is mentioned.
6. **Booster examples** around [00:55:10]. The summary has no worked chart
   for them.
7. **All timestamps.** None of them have been checked against the video.

Sending the transcript (or screenshots of the case-study charts) would let me
fix these and replace the schematics with descriptions of the real chart.
