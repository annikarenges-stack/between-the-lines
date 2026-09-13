# Better Said

**Better Said helps teams have better conversations.**

Better Said is a local AI-powered conversation reflection prototype. Teams can paste or upload a speaker-labelled transcript, receive a calm, evidence-based reflection, and save a private HTML or PDF-style report for each participant.

It is designed to support reflection and clearer communication - not to decide who is right.


See this solution in action: https://www.youtube.com/watch?v=LmNp6bF4x8Q

## What it does

- Accepts pasted transcripts and `.txt` / `.md` uploads.
- Analyses five conversation lenses: assumptions and biases, judgment and language, misunderstandings, focus and efficiency, and status or conversational space.
- Uses direct quotes from the submitted transcript for each flagged pattern.
- Explains the possible impact of a pattern and offers one practical "micro-shift" for a more constructive response.
- Creates a separate personal report for each meaningful speaker (up to four people). Shared pattern counts stay the same; each personal profile is separate.
- Lets users download the report as self-contained HTML or use the browser print dialog to save it as PDF.
- Includes a live practice conversation mode for neutral mentoring before a difficult conversation.

- Front page:

  <img width="1880" height="1017" alt="image" src="https://github.com/user-attachments/assets/99e64a52-bff1-4d16-98b7-86e92848653b" />

  


## What it does not do

- It does not determine who is right, evaluate someone’s character, or diagnose people.
- It cannot infer tone of voice, body language, history, or intent from written text alone.
- It is not legal, HR, medical, mental-health, or professional mediation advice.
- It should not be used as the sole basis for hiring, performance, disciplinary, or other high-stakes decisions.
- It is a prototype: report access is local and does not include user sign-in or enterprise access controls.

## How the report works

1. A user uploads or pastes a conversation with clear speaker labels, for example `Alex: ...` and `Sam: ...`.
   Uploade the script and wait for the reflection to be generated:
  <img width="1832" height="1012" alt="image" src="https://github.com/user-attachments/assets/e07ae65a-b210-433d-ad64-c101142ba686" />

3. The local server saves the transcript to `data/transcripts/`.
4. The server sends the transcript to the OpenAI Responses API using a key stored only in the local `.env` file.
5. The model returns structured analysis with direct evidence, counts, possible effects, and practical alternatives.
6. Better Said creates one private HTML report per participant and saves it in `data/reports/`.
7. The browser displays the selected report and can download it as HTML or print it to PDF.
   <img width="1871" height="1038" alt="image" src="https://github.com/user-attachments/assets/5e8e3c03-87fb-4e7a-9e27-4969aba1c842" />


## Run it locally

### Requirements

- Node.js 20 or later
- An OpenAI API key with billing enabled

### Setup

1. Download or clone this repository.
2. In the project folder, create a `.env` file by copying `.env.example`.
3. Add your key to the `.env` file. Do not put quotation marks around it.

```text
OPENAI_API_KEY=YOUR_OPENAI_API_KEY_HERE
OPENAI_MODEL=gpt-5
PORT=3000
```

4. Start the local server:

```powershell
cd "C:\AI Hackathon Codex"
node server.mjs
```

5. Open [http://localhost:3000](http://localhost:3000) in your browser.

The app has no npm dependencies, so `npm install` is not required for the current version.

## Privacy and security

- `.env` is intentionally excluded from Git. Never commit, upload, or share it.
- `data/` is also excluded from Git because it may contain transcripts and generated reports.
- Remove names and sensitive details before using a transcript whenever possible.
- The browser does not receive the OpenAI API key; the local Node.js server makes the API request.
- For a real team deployment, add authentication, role-based access, encrypted storage, retention controls, consent workflows, and a server-side secret manager.

## Project structure

```text
index.html            Interface and user journeys
better.css            Interface styling
app.js                Browser interactions, uploads, progress, and report actions
server.mjs            Local server, OpenAI analysis, privacy split, and report generation
report-template.html  Fixed self-contained report design
.env.example          Safe environment-variable template
skills/               Better Said agent guidance
data/                 Local-only transcripts and reports (ignored by Git)
```

## Demo flow

For a safe demo, use a fictional transcript with clear speaker labels:

1. Select **Reflect on a transcript**.
2. Upload a `.md` or `.txt` transcript.
3. Select **Create reflection**.
4. Choose one participant’s private report.
5. Highlight the overview, evidence quote, impact, micro-shift, and personal profile.
6. Choose **Save as PDF** and use the browser’s print dialog.

Never show an API key, `.env` file, terminal window, private transcript, or browser notifications in a recording.

## Contributing and publishing

This project is suitable as a hackathon or prototype repository. Before publishing publicly, review the transcript examples, choose a licence approved by your organisation, and make sure no secrets or personal data are included.
