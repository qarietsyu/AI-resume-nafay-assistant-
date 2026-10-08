# 📄 AI Resume Assistant

Upload a resume (PDF, DOCX or TXT) and get:

- an **ATS score** out of 100, with a breakdown (keywords, formatting, content, structure)
- strengths, weaknesses and **missing keywords**
- concrete **suggestions to improve** each section
- optional: paste a job description for better keyword matching

Built with [Streamlit](https://streamlit.io) and Google's Gemini Flash model.

## Run locally

```bash
pip install -r requirements.txt
export GEMINI_API_KEY="your-key"      # Windows PowerShell: $env:GEMINI_API_KEY="your-key"
streamlit run app.py
```

Get a free API key at https://aistudio.google.com/apikey.
If you skip the environment variable, the app asks for the key in the sidebar.

## Configuration

| Setting | Where | Default |
|---|---|---|
| `GEMINI_API_KEY` | env var or Streamlit secrets | none (required) |
| `GEMINI_MODEL` | env var or Streamlit secrets | `gemini-3.8-flash` |

If you get a 404 "model not found" error, Google has retired that model name.
Set `GEMINI_MODEL` to a current Flash model (the error message usually suggests one).

## Deploy on Streamlit Community Cloud

1. Push `app.py`, `requirements.txt` and `README.md` to a GitHub repo.
2. Go to https://share.streamlit.io and sign in with GitHub.
3. Click **Create app**, pick the repo, branch `main`, main file `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
5. Click **Deploy**.

## Notes

- Scanned/image-only PDFs have no text to read; use a text-based PDF or DOCX.
- The score is an AI estimate, not the output of a real ATS.
- Never commit your API key to GitHub.
