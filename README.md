# 🗺️ AI Learning Roadmap Generator

A Streamlit app that builds a personalised, week-by-week learning roadmap using
**Google Gemini** (Google AI Studio API key).

Enter:
1. the **field** you want to learn (or tap a quick pick),
2. your **level** – Beginner, Intermediate or Advanced,
3. the **time** you have – in weeks or months – and your study hours per week.

You get a roadmap split into phases. Each phase has a goal, topics, resources, a
hands-on project and a milestone. Tick topics off to track progress, and download the
whole plan as a Markdown file.

## Features

- Level-aware plans (beginners start with fundamentals, advanced learners with specialisation)
- Phase weeks are always scaled to add up to your exact time budget
- Progress bar with per-topic checkboxes
- Resource names link to a web search (the AI is told not to invent URLs)
- Download as Markdown
- Input checks, a 5-second cooldown between requests, and friendly error messages
  (missing key, quota, bad JSON from the model)

## Project files

```
app.py            # the Streamlit app
requirements.txt  # Python dependencies
README.md         # this file
```

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Get a Google AI Studio API key

1. Go to <https://aistudio.google.com/apikey>
2. Sign in and click **Create API key**.
3. Copy it. Never commit it to GitHub.

## Add the key

**Locally** – create `.streamlit/secrets.toml` (and add it to `.gitignore`):

```toml
GOOGLE_API_KEY = "your-key-here"
```

Or: `export GOOGLE_API_KEY="your-key-here"`

**Streamlit Community Cloud** – after deploying, open **Settings → Secrets** and paste:

```toml
GOOGLE_API_KEY = "your-key-here"
```

You can also paste the key into the sidebar box while using the app.

## Deploy from GitHub

1. Push `app.py`, `requirements.txt` and `README.md` to a GitHub repository.
2. Go to <https://share.streamlit.io> and click **Create app**.
3. Choose the repository, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and add `GOOGLE_API_KEY`.
5. Click **Deploy**.

## Notes

- The default model is `gemini-flash-latest`, an alias for the current Gemini Flash model.
  Change it in the sidebar if you want a specific model from AI Studio.
- Months are counted as 4 weeks. The maximum plan length is 52 weeks.
- AI-generated plans can contain mistakes. Check important resources before relying on them.
- If you make the app public, everyone shares your API quota. Consider keeping the app
  private or adding usage limits.
