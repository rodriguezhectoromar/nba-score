<wizard-report>
# PostHog post-wizard report

The wizard has completed a deep integration of PostHog analytics into this NBA Live Scores project. The PostHog JavaScript Web SDK was added via CDN snippet to `index.html`, and five custom events were instrumented across the app's key user interactions.

## Changes made

**`index.html`**
- Added PostHog CDN snippet + `posthog.init()` call in `<head>` (before styles)
- Added `isInitialLoad` flag to distinguish initial page loads from subsequent refreshes
- Instrumented 5 custom events (see table below)

## Events instrumented

| Event | Description | File |
|---|---|---|
| `scores_loaded` | Fires when NBA scores successfully load. Includes `total_games` and `is_initial_load` properties. | `index.html` |
| `scores_refreshed` | Fires when the user manually clicks the Refresh button. | `index.html` |
| `additional_games_shown` | Fires when additional games (days 4–8) are fetched and rendered for the first time. Includes `total_games`. | `index.html` |
| `additional_games_toggled` | Fires when the already-loaded additional games section is shown or hidden. Includes `action: "shown" \| "hidden"`. | `index.html` |
| `scores_fetch_failed` | Fires when the ESPN API call fails. Includes `error_message`. Also calls `posthog.captureException()` for error tracking. | `index.html` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

- [Analytics basics dashboard](/dashboard/1576671)
- [Scores Loaded Over Time](/insights/tmLGkbYp) — daily trend of score load events
- [Manual Refreshes](/insights/wS2yH7vO) — how often users manually refresh
- [Additional Games Exploration](/insights/XFHcqiQ8) — usage of the "Show additional games" feature
- [Score Fetch Errors](/insights/OIcFSioq) — ESPN API error rate over time
- [Unique Daily Visitors](/insights/sD6HIYzI) — daily active users (top of funnel)

### Agent skill

We've left an agent skill folder in your project. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.

</wizard-report>
