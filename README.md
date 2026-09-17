# 🤖 Analizador de Juegos Olímpicos con GPT

A small Streamlit app that lets you ask natural-language questions about Olympic athletes and results. It loads a CSV dataset, summarizes it, and forwards your question (plus the summary) to an OpenAI chat model, which answers using that context.

## How it works

- `programa_final.py` — the Streamlit app. It:
  1. Asks for your OpenAI API key in the sidebar (stored only in the Streamlit session).
  2. Loads `athlete_events_reduced_rows.csv` and shows it as a table.
  3. Builds a text summary of the dataset (columns + `describe()` stats) as context.
  4. Sends that context plus your question to `gpt-3.5-turbo` via the OpenAI API, with a system prompt that restricts answers to Olympics-related topics.
- `athlete_events_reduced_rows.csv` — Olympic athlete records (~171k rows): `ID, Name, Sex, Age, Height, Weight, Team, NOC, Games, Year, Season, City, Sport, Event, Medal`.
- `requirements.txt` — Python dependencies.

## Setup

```bash
pip install -r requirements.txt
streamlit run programa_final.py
```

You'll need an [OpenAI API key](https://platform.openai.com/api-keys) — enter it in the sidebar when the app opens.

## Usage

1. Launch the app and paste your API key into the sidebar.
2. Type a question about the Olympics (athletes, countries, sports, medals, stats).
3. Click "📤 Enviar pregunta al modelo" to get an answer grounded in the dataset.
