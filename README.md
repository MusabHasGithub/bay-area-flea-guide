# Bay Area Flea Market Guide

A self-updating, single-file guide to Bay Area flea markets.

**Live site: [mozetech.github.io/bay-area-flea-guide](https://mozetech.github.io/bay-area-flea-guide/)**

Every month the schedule regenerates itself in the browser from each market's
recurring pattern (every Sunday, 2nd Sunday of the month, 3rd Saturday, and so
on), so nobody has to update dates by hand. Ever.

## Features

- **Auto-generating monthly schedule.** Recurrence rules ("2nd Sunday, April
  through November") are evaluated client-side for whatever month it is when
  the page loads. Timeline bars are positioned by each market's hours.
- **Past days sink to the bottom** under a "Past Events" title, with a
  scroll-driven animation that desaturates the page as you scroll into them.
- **Hover quick facts.** A hand-drawn arrow animates out to a card with what's
  sold there, what to expect, and one researched cool fact per market.
- **Live weather badges.** Daily [Open-Meteo](https://open-meteo.com/)
  forecasts (free, no API key) at each market's coordinates, shown as tiny
  animated icons on markets that may scale back in bad weather. Rain-or-shine
  markets don't get badges on purpose.
- **Tap popup with Google Maps and official-site links** for every market.
- **Zero build, zero dependencies.** One HTML file. Hosting is GitHub Pages.

## Running locally

There is no build step. Clone and open the file:

```sh
git clone https://github.com/mozetech/bay-area-flea-guide.git
open bay-area-flea-guide/index.html
```

## How the data works

All market data lives in one `MARKETS` array in [index.html](index.html).
Each market is a small object:

```js
{
  name: 'Chabot College Flea Market',
  area: 'Hayward, CA',
  site: 'https://www.chabotcollege.edu/student-services/student-life/flea-market.php',
  tier: 'blue', tierLabel: '3rd Saturday of the month',
  icon: 'bag',
  weather: { lat: 37.64, lon: -122.10 },   // omit for rain-or-shine markets
  start: 8, end: 15,                        // hours, 24h decimals
  rule: { nth: 3, dow: 6 },                 // 3rd Saturday
  facts: { goods: '...', expect: '...', fun: '...' },
}
```

Two rule shapes are supported:

| Rule | Meaning |
| --- | --- |
| `{ weekly: [5, 6, 0] }` | Every week on those days (0 = Sunday .. 6 = Saturday) |
| `{ nth: 2, dow: 0, months: [3, ..., 10] }` | Nth weekday of the month, optionally only in some months (0 = January) |

## Contributing

Schedule corrections, new markets, and better facts are all welcome. See
[CONTRIBUTING.md](CONTRIBUTING.md). If you spot a wrong time or a market that
has closed, even just [opening an issue](../../issues/new/choose) helps
everyone.

Want this for your own city? Fork it, replace the `MARKETS` array, and turn on
GitHub Pages. That's the whole deployment.

## License

[MIT](LICENSE)
