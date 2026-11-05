# n8n Portfolio Agent

A chat-based AI agent built with n8n that reads portfolio holdings from Google Sheets, fetches end-of-day prices from Marketstack, and estimates the portfolio's value. When asked, it proposes a position for diversification and saves the suggested ticker and share count to Google Sheets.

## How it works

1. A chat message triggers the n8n AI Agent.
2. The agent reads holdings using the Google Sheets `Get Row(s)` tool.
3. It retrieves end-of-day prices from Marketstack and uses them to estimate portfolio value and position weights.
4. When the user asks to save a suggestion, the agent calls the Google Sheets `Append Row` tool with the ticker and share count.

## Demo

https://github.com/user-attachments/assets/870ed4af-394a-471a-b1b6-5aac8f01c9ca

The demo starts with `AMZN` and `AAPL` in Google Sheets. The agent reads both positions and reports the portfolio value. On two separate chat requests, it appends `VTI` with 1 share and `BND` with 5 shares. Both rows appear in Google Sheets during the demo.

In this demo, suggestions are appended to the same sheet as the starting holdings. Later valuations treat those rows as part of the simulated portfolio.

## Setup

1. Import [`workflow.json`](./workflow.json) into n8n.
2. Configure your own OpenAI, Google Sheets, and Marketstack credentials in n8n.
3. Create a test Google Sheet with these column headers in the first row.

   | Ticker | shares |
   | --- | --- |
   | AMZN | 10 |
   | AAPL | 2 |

4. Select your test spreadsheet and tab in both Google Sheets tools. Give the connected Google account edit access to the sheet.
5. Open the workflow chat and try the prompts below. After the second prompt, check Google Sheets for the new row.

## Example prompts

- `What's the value of my stock portfolio?`
- `Suggest one position to diversify my sample portfolio. Choose the ticker and share count, then add one row to my test sheet.`

## Tech stack

- n8n AI Agent and Simple Memory
- OpenAI Chat Model
- Google Sheets for reading holdings and appending rows
- Marketstack for end-of-day prices
