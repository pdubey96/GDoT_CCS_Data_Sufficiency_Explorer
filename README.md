# GDoT CCS Data-Sufficiency Explorer

> **A month came in with days missing. How many good days does this station need
> before its monthly average can be published?**

Four files answer that, for every continuous count station in Georgia and every
calendar month. Take **the tool** if you want to explore one station-month and
see the evidence; take **the spreadsheet** if you just want the number.

---

## The files

| | File | What it is | Click it here and… |
|---|---|---|---|
| 🖥️ | **[GDoT Data-Sufficiency Explorer.html](GDoT%20Data-Sufficiency%20Explorer.html)**<br><sub>25 MB</sub> | **The tool.** Pick a station, a month and a kind of outage, and watch the answer recompute. | …GitHub says *"too big to display"*. That is expected — **download it and double-click it.** It runs on your machine, not here. |
| 📗 | **[dashboard_how_to_use.pdf](dashboard_how_to_use.pdf)**<br><sub>25 pages</sub> | The guide to the tool. Walks through one run, then explains every part of the screen. No statistics needed. | …it opens and reads right here in the browser. |
| 📊 | **[practitioner_site_month_kstar.csv](practitioner_site_month_kstar.csv)**<br><sub>2,796 rows × 12 columns</sub> | **The spreadsheet.** One row per station and calendar month, with the recommended number of days and the six per-pattern numbers behind it. | …GitHub shows it as a searchable table, so you can look a station up **without downloading anything**. It also opens in Excel. |
| 📕 | **[practitioner_site_month_kstar_how_to_read.pdf](practitioner_site_month_kstar_how_to_read.pdf)**<br><sub>6 pages</sub> | The guide to the spreadsheet. A worked example, then what every column means. | …it opens and reads right here in the browser. |

**To save any one of them:** open it, then press **Download raw file** — the
download icon at the top right of the file view.

**To take all four at once**, if you use git:

```bash
git clone https://github.com/pdubey96/GDoT_CCS_Data_Sufficiency_Explorer.git
```

---

## How to run the tool

**Double-click `GDoT Data-Sufficiency Explorer.html`.** It opens in your web
browser. That is the whole procedure.

- Nothing to install, no program to start first, no internet connection.
- Nothing you do leaves your machine.
- Everything the tool needs is inside that one file, including the data for all
  233 stations — so it is large, and the first load takes a few seconds. After
  that it is immediate.
- You can forward that single file to a colleague and it will work for them.
- It follows your computer's light or dark setting, so it may not match the
  screenshots in the guide, which are all light. The **Theme** button at the top
  right switches between them.

**If it opens as code instead of a page**, your computer has `.html` files set
to open in a text editor. Right-click the file → **Open With** → your browser.
Once only.

---

## What it covers, and where it comes from

All **233** continuous count stations that delivered data in 2024, every
calendar month — **2,796 station-months** — under **six** different patterns of
how the days could go missing. For each one it gives a recommended number of
valid days, and lets you see the evidence behind that number.

These are the interactive and tabular companions to the GDOT 26-OTD-1 final
report, built from the same frozen analysis at seed `20260719`. The tool and the
spreadsheet carry the same numbers and agree on all 2,796 station-months.

---

## The spreadsheet, in one minute

`practitioner_site_month_kstar.csv` is the same guidance as a lookup table: find
the row for your station and month, and read `recommended_k`. Twelve columns,
one header row, no blank cells.

| Columns | What they hold |
|---|---|
| `site`, `month` | Which station, and which calendar month (1–12). |
| `calendar_days` | How many dates that month has. 2024 is a leap year, so February is 29. |
| `k_mcar` … `k_markov` | The number of days needed under each of the six outage patterns. |
| `recommended_k` | **The answer.** The largest of the five ordinary patterns. Weekend-heavy is reported but never allowed to raise it. |
| `threshold_status` | How to read the recommendation. |
| `operational_status` | What the 2024 record actually held. |

The last two columns are words rather than numbers, and they answer two
different questions. The guide gives each one a section of its own; the short
version is:

- **`threshold_status`** is about the recommendation. Every row says
  `certified`, because every row carries a certified number. A word after it is
  a qualification, not a warning: `certified_calendar_sensitivity` marks the
  February rows, whose count had to be carried between calendars of different
  length; `certified_finite_cohorts` marks 32 rows built on a smaller pool of
  comparable stations than preferred.
- **`operational_status`** is about the 2024 record, and never changes the
  recommendation. `complete_exact` means every date produced a valid daily
  total. `incomplete_requires_prediction` means at least one date did not —
  it describes the data, **not** a verdict on the month, and such a month will
  often still clear its recommended number comfortably.
  `no_target_record` means nothing usable arrived for that station and month.

---

## One thing worth knowing before you start

The tool does two different things at once, and it helps to keep them apart.

**The experiment is live.** Change the station, the month, the kind of outage,
the number of surviving days, or the statistical settings, and everything
recomputes from the underlying data in front of you. It is doing real
arithmetic, not looking up stored answers — the **Verification** tab re-derives
the published figures in your browser and shows them matching.

**The recommended planning value is fixed.** That number was certified once, by
the study, at these settings:

| | |
|---|---|
| α (how often the range may be wrong) | 0.10 |
| ε (how tight the answer must be) | 0.05 |
| success target | 90% |
| replications | 1,000 |

It does **not** re-derive itself when you move the dials. That is not because
the number is independent of those settings — it plainly is not; loosen α and
fewer days would do, tighten ε and you would need more. It is because working it
out properly means re-running the entire selection experiment, which is far
heavier than anything done live in the page. So the certified value ships as it
is, which is also what makes it match the report and the delivered spreadsheet.

If you change a setting, the tool will say so on screen. **Reset to defaults**
puts everything back.

---

## What it does not claim

- It is tied to a **stated** kind of outage, not to any arbitrary pattern of
  missing days.
- The guarantee is **per station**, not simultaneous across the network.

The **How to read this** tab restates this beside the data; the guide and the
final report set it out properly.
