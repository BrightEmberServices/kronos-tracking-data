# kronos-tracking-data

Public data feed for the Kronos SGX daily tracker. Appended each SGX trading day
(~19:15 SGT) by a launchd job on a Mac mini running Kronos-mini locally with
post-hoc conformal (CQR) band calibration.

- `kronos_daily_tracking.jsonl` — full forecast/score history, one record per ticker
  per bar: 48-step q10/q50/q90 forecast fan, CQR-calibrated next-bar 80% band,
  realized hit/miss, surprise score, calibration source.
- `kronos_price_history.json` — last ~130 daily OHLC bars per ticker (for the
  dashboard's candlesticks; Yahoo's chart API blocks browser CORS).

Tickers: ES3.SI, G3B.SI, GAB.SI (STI ETFs), D05.SI, O39.SI, U11.SI (SG banks).

**These are calibrated uncertainty bands, not stock picks.** The underlying study
found no directional edge over naive baselines — the bands are honest about range,
silent about direction. Consumed by the Replit dashboard; code lives in the
kronos-coreml repo.
