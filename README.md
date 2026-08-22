# GDoT CCS Data-Sufficiency Explorer

An interactive tool that answers one question for any of Georgia's continuous
count stations:

> **A month came in with days missing. How many good days does this station
> need before its monthly average can be published?**

---

It is the interactive companion to the GDOT 26-OTD-1 final report, built from
the same frozen analysis: 233 stations, twelve calendar months each, all six
declared outage patterns, seed 20260719.

---

## Getting the file

Each file downloads on its own. Click it, then press **Download raw file** —
the download icon at the top right of the file view:

- [`GDoT Data-Sufficiency Explorer.html`](GDoT%20Data-Sufficiency%20Explorer.html)
  — the tool
- [`dashboard_how_to_use.pdf`](dashboard_how_to_use.pdf) — the guide, which also
  opens right here in the browser if you only want to read it

Or take both at once:

```bash
git clone https://github.com/pdubey96/GDoT_CCS_Data_Sufficiency_Explorer.git
```

The tool is a single 25 MB file, which is more than GitHub will preview, so
clicking it shows *"this file is too big to display"* instead of the dashboard.
That is expected. It runs on your machine, not on GitHub.

---

## How to run it

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

## What is here

| File | What it is |
|---|---|
| [`GDoT Data-Sufficiency Explorer.html`](GDoT%20Data-Sufficiency%20Explorer.html) | The tool. Download it, then double-click it. 25 MB, so GitHub shows a "too big to display" notice rather than the page itself. |
| [`dashboard_how_to_use.pdf`](dashboard_how_to_use.pdf) | The guide, 23 pages. Walks you through one run, then explains every part of the screen. No statistics needed. Opens here in the browser. |
| `README.md` | This file. |

---

## What it covers

All **233** continuous count stations that delivered data in 2024, every
calendar month — **2,796 station-months** — under **six** different patterns of
how the days could go missing.

For each one it gives a recommended number of valid days, and lets you see the
evidence behind that number.

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
