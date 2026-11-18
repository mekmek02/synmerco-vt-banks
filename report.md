# Vermont's active banks: assets, deposits, offices and age in one table

Every active bank headquartered in Vermont, from the FDIC BankFind API. Figures are in thousands of dollars as returned. Pull date (UTC): 2026-11-17.

## Raw meta.total excerpt

```json
{
  "total": 12,
  "parameters": {
    "filters": "STALP:VT AND ACTIVE:1",
    "fields": "NAME,CITY,ASSET,DEP,OFFICES,ESTYMD,CERT",
    "limit": "50"
  }
}
```

The request returned meta.total = 12, and 12 bank rows. One row per bank is in vt-banks.csv.

## Table of banks, sorted by ASSET highest first

| CERT | NAME | CITY | ASSET | DEP | OFFICES | ESTYMD | deposits to assets (%) | years |
|---:|---|---|---:|---:|---:|---|---:|---:|
| 14140 | Northfield Savings Bank | Northfield | 1576574 | 1329504 | 13 | 11/21/1867 | 84.33 | 158 |
| 14158 | Union Bank | Morrisville | 1558133 | 1100008 | 21 | 01/01/1891 | 70.60 | 135 |
| 6271 | Community National Bank | Derby | 1172186 | 983375 | 12 | 01/15/1851 | 83.89 | 175 |
| 33418 | Ledyard National Bank | Norwich | 1071557 | 874363 | 11 | 05/22/1991 | 81.60 | 35 |
| 14134 | Passumpsic Savings Bank | Saint Johnsbury | 934455 | 752956 | 13 | 02/24/1853 | 80.58 | 173 |
| 30350 | The Bank of Bennington | Bennington | 661897 | 494298 | 5 | 01/01/1917 | 74.68 | 109 |
| 6275 | The National Bank of Middlebury | Middlebury | 553549 | 500193 | 7 | 11/09/1831 | 90.36 | 195 |
| 14168 | Peoples Trust Company of St. Albans | Saint Albans | 395438 | 348764 | 5 | 11/12/1866 | 88.20 | 160 |
| 59298 | Business Bank, The | S Burlington | 352210 | 310790 | 2 | 08/02/2022 | 88.24 | 4 |
| 28837 | The Brattleboro Savings and Loan Association | Brattleboro | 296376 | 262301 | 5 | 01/01/1912 | 88.50 | 114 |
| 14136 | Wells River Savings Bank | Wells River | 266865 | 234608 | 6 | 01/01/1892 | 87.91 | 134 |
| 6280 | The First National Bank of Orwell | Orwell | 91503 | 80526 | 2 | 01/01/1863 | 88.00 | 163 |

## Totals, median, largest and smallest

- Total ASSET: 8930743 (thousands of dollars)
- Total DEP: 7271686 (thousands of dollars)
- Median ASSET: 607723.00 (thousands of dollars; even count of 12, mean of the two middle values 553549 and 661897)
- 3 largest by ASSET:
  - Northfield Savings Bank (CERT 14140): 1576574
  - Union Bank (CERT 14158): 1558133
  - Community National Bank (CERT 6271): 1172186
- 3 smallest by ASSET:
  - The First National Bank of Orwell (CERT 6280): 91503
  - Wells River Savings Bank (CERT 14136): 266865
  - The Brattleboro Savings and Loan Association (CERT 28837): 296376

## Method notes

- Deposits to assets (%) = DEP / ASSET x 100, 2 decimals, half away from zero, from unrounded values.
- Years = whole years from ESTYMD to the pull date 2026-11-17 (UTC), rounded down.
- ASSET and DEP are in thousands of dollars as returned by the FDIC API.

## PROOF

Request: GET https://api.fdic.gov/banks/institutions?filters=STALP%3AVT%20AND%20ACTIVE%3A1&fields=NAME%2CCITY%2CASSET%2CDEP%2COFFICES%2CESTYMD%2CCERT&limit=50&format=json
UTC time: 2026-11-17T20:34:05Z
HTTP status: 200

First response Date header (copied exactly):

Tue, 17 Nov 2026 20:34:07 GMT

## Acceptance checklist (self-tick)

1. The PROOF quotes the raw meta.total (12), and the CSV holds one row per bank the request returned (12 rows) with its values as returned. [met]
2. The CSV file vt-banks.csv is attached with exactly the listed columns: CERT, NAME, CITY, ASSET, DEP, OFFICES, ESTYMD, deposits to assets, years. [met]
3. The per-bank ratios and years, the totals, the median and the largest and smallest lists follow the TASK and agree with the CSV. [met — all figures recomputed from the raw response]

```synmerco-data
9196faa3d5682d9ba46a9e408b5ca403da8dad6864547c099ffa80815a3a400e vt-banks.csv
```
