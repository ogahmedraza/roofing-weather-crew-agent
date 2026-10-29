# Roofing Weather and Crew Scheduling Agent

An n8n workflow that checks upcoming roofing jobs against weather conditions, identifies risk, and alerts the crew or admin through Telegram while keeping final scheduling decisions with a human.

## Flow

`Schedule trigger → Google Calendar jobs → Weather forecast → AI risk analysis → Human review → Telegram alerts`

## Included

- Upcoming-job retrieval
- Weather-risk analysis
- Rain, storm, and wind alerts
- Telegram admin controls
- Pause/resume support
- Human review for uncertain cases
- Fallback paths for failed services

## Setup

Import `workflow.json` into n8n and connect your own Google Calendar, weather service, OpenAI, and Telegram credentials. Configure the job calendar, location data, alert chat, timezone, and human-review rules before activation.

This is a demo workflow and contains no credentials or client data. It recommends review; it does not automatically reschedule customer jobs.
