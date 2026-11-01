# Roofing Weather & Crew Review Agent

> Check upcoming roofing jobs against a forecast, flag weather risk, and keep the final schedule decision with a human.

## The operating rule

This workflow never moves or cancels a customer appointment. It gives the crew and admin a clear risk signal, including a fallback notice when a connected service fails.

## Workflow map

```text
Schedule trigger / Telegram admin command
  → read pause state
  → get upcoming Google Calendar jobs
  → fetch weather forecast
  → AI risk assessment
  ├─ safe: end
  └─ review or high risk: crew alert + admin review
```

## Built-in control layer

An authorized Telegram admin can use:

| Command | Result |
| --- | --- |
| `/pause` | Stops scheduled weather checks |
| `/resume` | Restarts scheduled checks |
| `/status` | Returns the current active/paused state |

The pause state is stored in n8n workflow static data. Restrict the admin chat ID before enabling the Telegram trigger.

## What the agent checks

- Upcoming jobs from Google Calendar
- Forecast data from OpenWeatherMap
- Rain, storm, wind, or uncertain conditions that need review
- AI output constrained to `safe`, `review`, or `high` risk
- Confidence below 80%, which is also routed to human review

## Before activation

1. Import `workflow.json` into n8n.
2. Connect Google Calendar, OpenWeatherMap, OpenAI, and Telegram.
3. Edit the Business Config values: city, look-ahead period, admin chat ID, crew chat ID, and timezone.
4. Confirm the Telegram admin control works only for your approved chat.
5. Test normal, high-risk, paused, and service-failure routes with sample calendar events.

## Limitations

Forecast quality, location accuracy, and calendar data determine the usefulness of the alert. This workflow is decision support only; a qualified person must make every schedule change.

## Repository contents

| File | Purpose |
| --- | --- |
| `workflow.json` | Importable n8n operations workflow |
| `SECURITY.md` | Credential and access-control guidance |
| `LICENSE` | MIT license |

## License

MIT — see [LICENSE](LICENSE).