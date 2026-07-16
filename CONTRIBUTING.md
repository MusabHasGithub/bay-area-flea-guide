# Contributing

Thanks for helping keep the guide accurate. Flea market schedules drift
(markets close, change hours, lose leases, reopen), and this project only
stays useful if the data stays true.

## The easiest way to help

[Open an issue](../../issues/new/choose) when you notice:

- a market's hours or days are wrong,
- a market has closed, moved, or changed its recurrence,
- a market that should be listed but isn't.

You don't need to write any code. A link to the market's official site or a
recent news story is enough.

## Submitting a change yourself

1. Fork the repo and edit the `MARKETS` array in `index.html` (see the README
   for the data shape). Everything is in that one file.
2. Open the file in a browser and check your market renders on the right days
   with the right hours.
3. Open a pull request.

## Data guidelines

- **Source your schedule claims.** Link the market's official site, or two
  independent recent sources if it has no site. Yelp hours alone are not
  reliable.
- **Facts must be real.** The quick-facts blurbs (`goods`, `expect`, `fun`)
  should be verifiable, not vibes. Include your source in the PR description.
- **Weather badges are only for weather-sensitive markets.** If a market
  advertises "rain or shine", omit the `weather` field. That contrast is the
  point of the feature.
- **Keep the copy style.** Short, concrete, no em dashes.

## Adding a whole new city

Fork the project rather than adding non-Bay-Area markets here. The page is a
single self-contained file: replace the `MARKETS` array and the header text,
enable GitHub Pages on your fork, and you have your own city's guide.

## Code changes

Keep it dependency-free and build-free: one HTML file with inline CSS and JS.
If a feature needs a framework, a bundler, or an API key, it probably belongs
in a fork.
