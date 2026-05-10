# 🛰️ Smart Weather Alert & Reporting System

This use case demonstrates an event-driven monitoring system that fetches real-time weather data, evaluates it against user-defined thresholds, and triggers multi-channel responses.

## 🚀 Orchestration Patterns Used

- **Dynamic Inputs:** Runtime configuration for temperature thresholds.
- **Secure Secret Management:** Zero-exposure of API endpoints and Webhook URLs.
- **Conditional Logic:** Branching execution paths using the `If` flowable task.
- **Artifact Generation:** Dynamic Markdown report creation using `LocalFiles`.

## 🛠️ Architecture

1. **Ingest:** Kestra fetches current weather data from the Open-Meteo API.
2. **Evaluate:** An `If` condition compares the live temperature against the `threshold_temp` input.
3. **Alert (Optional):** If the threshold is exceeded, a POST request is sent to a Discord/Slack webhook.
4. **Report:** A performance summary is generated as a Markdown file for audit trails.

## 🔐 Setup & Security

To keep this repository public, sensitive data is stored as encrypted environment variables on the host machine.

### 1. Configure Secrets

Run the following on your Linux host to encode your endpoints:

```bash
# Encode Weather API
export SECRET_WEATHER_API_URL=$(echo -n "[http://api.open-meteo.com/v1/forecast?latitude=17.3850&longitude=78.4867&current=temperature_2m](http://api.open-meteo.com/v1/forecast?latitude=17.3850&longitude=78.4867&current=temperature_2m)" | base64)

# Encode Notification Webhook
export SECRET_DISCORD_WEBHOOK=$(echo -n "https://your-webhook-url" | base64)
```

#### Map them in docker-compose.yml

```bash
services:
  kestra:
    image: kestra/kestra:latest-full
    # ... other config ...
    environment:
      # This maps the Linux variable to the Kestra container
      SECRET_DISCORD_WEBHOOK: ${SECRET_DISCORD_WEBHOOK}
      SECRET_WEATHER_API_URL: ${SECRET_WEATHER_API_URL
```

Refresh the containers:
`docker-compose up -d`

### 2. Deploy Flow

- Import `smart_weather_alert.yml` into your Kestra instance.

- Ensure your Kestra service is restarted to load the new environment variables.

### 3. Execute the flow

Execute the flow, enter the threshold temperature And see the report generated.
