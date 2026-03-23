# Singapore pump price analysis

This is a [data deep-dive](https://wongpeiting.github.io/sg-petrol/) examining Singapore's record pump price surge following this month's (March 2026's) Iran oil shock, and how prices in the Republic's oligopolistic market moved. 

I used this project to break out of ready-made chart templates by bringing Adobe Illustrator into the workflow. Charts were first prototyped in Datawrapper, then exported as SVGs and refined in Illustrator for full control over annotations, typography and layout. [ai2html](http://ai2html.org) converts those Illustrator files into responsive HTML without requiring JavaScript so the graphics adapt to mobile and desktop without rebuilding anything.

## Why this topic?

I was inspired by these news developments:
- [Petrol prices in Singapore surpass highs set during Ukraine crisis in 2022](https://www.straitstimes.com/business/economy/petrol-prices-in-singapore-surpass-highs-set-during-ukraine-crisis-in-2022) — which reported pump prices smashing the 2022 record within days of the Iran strikes
- [CASE chief urges Singapore petrol companies to promptly adjust pump prices when global prices fall](https://www.straitstimes.com/singapore/case-chief-urges-singapore-petrol-companies-to-promptly-adjust-pump-prices-when-global-prices-fall) — which raised the question of why prices go up fast but rarely come down at the same speed

Together, they pointed to a deeper data story worth exploring about how Singapore's rate of increase compares with other countries, and how differently the trajectories of Singapore's five petrol companies' pump price increases look like (1) from each other, and (2) between the current oil shock and the last major oil shock following Russia's invasion of Ukraine in 2022. I also got curious if there is merit to the common consumer's grouse that prices always go up quick but doesn't come down fast enough. 

The result is four charts, each showing a different facet of the issue:
1. **Global comparison**: An arrow plot ranking 53 major economies by absolute pump price increase. Surprisingly (or not), Singapore came up on top (!!!). Singapore's price increase of US$0.41/litre was the highest in the first 16 days of the Iran war.
2. **Pump price history**: A stepped line chart tracking all five brands' 95-octane prices since 2021 for an overview of how the prices had moved throughout the 2022 and 2026 oil shocks.
3. **2022 vs 2026 side-by-side**: A pair of stepped line charts comparing the pace of the Ukraine-era surge (four months to peak) with the Iran-era surge. In the Iran oil shock, all five petrol brands (Shell, Caltex, SPC, Esso, Sinopec) moved in near-lockstep, reaching S$3.47/litre within 18 days.
4. **Brent crude vs pump price**: A scatterplot of Brent crude vs pump prices since 2011 revealing how pump prices have drifted higher relative to crude and become stickier on the way down in recent years.

## Data and data sources

| File | Description | Source |
|------|-------------|--------|
| `data/sg_95_full_history.csv` | Daily 95-octane pump prices (2011–2026) for Shell, Caltex, SPC; Esso and Sinopec from Sep 2025 | [ChenLim.Com](http://chenlim.com), [Motorist.sg](https://motorist.sg) |
| `data/sg_pump_prices_recent.csv` | Daily pump prices (Sep 2025–Mar 2026) for all five brands | [Motorist.sg](https://motorist.sg) |
| `data/global_petrol_change.csv` | Pump price changes across 53 economies | [GlobalPetrolPrices.com](https://www.globalpetrolprices.com) |
| `data/brent_sg_pump_combined.csv` | Monthly Brent crude + Singapore pump price averages (2011–2026) | U.S. Energy Information Administration (EIA) via Federal Reserve Economic Data (FRED); ChenLim.Com |

## Process

Charts were first built in Datawrapper, exported as SVGs (`svgs/`), then refined in Adobe Illustrator (`ai_edits/`) for pixel-level control over annotations and typography. [ai2html](http://ai2html.org) was used to render responsive versions across mobile and desktop without rebuilding charts in JavaScript.

Throughout this process, the biggest headache was getting the mobile version of the charts to show up with healthy margins on the side. Without intervention, the mobile charts run edge-to-edge on mobile. It was not an issue for desktop view as there is always extra space on the sides given that I set maximum widths at either 1050 px or 700 px. For mobile, I tried padding, margin, box-sizing, overflow-x:hidden on the body, but nothing worked cleanly. I eventually fixed the issue by going back to Illustrator to artifically insert margins and re-exporting the respective ai2html files. Sometimes the simplest solution is accepting the constraint. 

Also, every time I exported from Illustrator, ai2html would reintroduce the same four bugs: an invalid 'font-weight:regular', 'overflow:hidden' clipping text, unquoted font names, and bare image paths. I ended up with a muscle-memory find-and-replace routine after each paste. But if I were doing this again, it might be much more efficient to write a post-export script to automate those fixes.

Overall, I came away with a deeper appreciation for static visuals. Interactivity (including tooltips _boy, do I still love tooltips_) can sound like a great feature or a must-have, but it does cut back on intentionality. With it, I have built a bad habit where I expect readers to explore the data on their own, a.k.a. work to find the editorial point I have tucked nicely in a chart for them. Who has time for an easter egg though? The ai2html workflow forced me to be intentional about every line, annotation and highlight, and I realised that deliberate design choices can do more to land a point than any tooltip or zoom ever could.