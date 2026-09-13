# Run Bettersaid with real AI analysis

1. Create an OpenAI API key in the OpenAI dashboard.
2. This project already includes a private `.env` file. It is excluded from Git, so it will not be committed with your project.
3. Open the `.env` file in this folder and replace `PASTE_YOUR_NEW_OPENAI_API_KEY_HERE` with your actual key. Do not add quotation marks and do not share the file. The local server loads this file automatically.

4. Open PowerShell in this folder and run:

   ```powershell
   node server.mjs
   ```

5. Open http://localhost:3000 in your browser. Do not open `index.html` directly because the real analysis endpoint needs the local server.

The server saves the original submitted transcript under `data/transcripts/` and the structured AI report under `data/reports/`. The interface can export the displayed report as a shareable local HTML file.

The API key stays on your computer and is sent only from the local server to OpenAI. The browser never sees it.
