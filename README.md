# Automated Real-Time Weather Alert System (n8n)

An end-to-end workflow automation built with self-hosted **n8n** that fetches live weather metrics, evaluates temperature thresholds using conditional logic, and dispatches instant alerts to **Telegram**.

## Workflow Architecture

1. **Schedule Trigger:** Automatically triggers the workflow at set intervals.
2. **HTTP Request Node:** Queries the Open-Meteo REST API (`GET`) to retrieve real-time temperature and wind speed data.
3. **Edit Fields (Set) Node:** Parses raw JSON responses using JavaScript expressions into a clean, human-readable weather report.
4. **IF Node (Conditional Routing):** Evaluates whether the live temperature exceeds a set threshold (`> 20°C` / custom limit) and routes execution into `true` or `false` branches.
5. **Dual-Branch Telegram Alerts:** Sends formatted real-time alerts to Telegram for both `true` (High Temperature Alert) and `false` (Pleasant Weather Update) conditions.

## Tech Stack & Nodes Used
- **Platform:** n8n (Self-hosted via Node.js)
- **APIs:** Open-Meteo Weather API, Telegram Bot API
- **Core Concepts:** REST API Integration, JSON Parsing, Dynamic Expressions, Conditional Branching

## How to Use This Workflow
1. Download the `.json` workflow file from this repository.
2. Open your n8n instance, create a new workflow, click the **three dots (`...`)** menu at the top right, and select **Import from File**.
3. Open the **Telegram** node, add your Telegram Bot API credential (from `@BotFather`), and replace `YOUR_CHAT_ID` with your numeric Telegram ID.
4. Click **Execute Workflow** to test or toggle the workflow to **Active**.
