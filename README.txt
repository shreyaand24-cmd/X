Briefly — repaired website

Run locally:
  cd briefly
  python -m http.server 8000
Open http://localhost:8000 in your browser.

The original design is retained. The Briefly logo returns home. The identity input and speaker-activity panel are removed. TL;DR is renamed Summary. Plain text and common chat exports are accepted. Deadline dates are anchored to message timestamps; unspecified dates/times are labelled rather than invented. Numeric export dates use day/month/year. Topics and action extraction remain heuristic, not an AI model; inspect source text for critical decisions.

Gmail:
Create a Google Cloud project, enable the Gmail API, configure the OAuth consent screen (add your account as a test user if in testing), create a Web application OAuth client and register http://localhost:8000 as an authorized JavaScript origin. For production, register the HTTPS origin and follow Google verification requirements. Enter that public client ID in the Gmail connection dialog. Do NOT enter a client secret. Sign in and consent to read-only Gmail access; choose from the latest 30 email threads. Only the selected thread is fetched in full and summarized. The live OAuth path could not be tested without your credentials/account.

Instagram / WhatsApp / Telegram:
Live account connections are NOT implemented. Buttons honestly offer export import instead of fake access approval. Export text/JSON using the instructions in each app dialog; choose one imported conversation and summarize. Files are not uploaded. Telegram/Instagram JSON and WhatsApp text are supported. Email .eml/.mbox imports use a basic parser; complex MIME mail is better read through the Gmail connector.

No speech-to-text or image/video transcription. No model API or server stores your chats. Summarization is local and extractive, not a full semantic AI summarizer. Browser preview supports pasted text and local imports; Gmail needs your own served origin and credentials.

Verified in headless Chromium: timestamped chat summarization, plain text summarization, relative deadline resolution, logo navigation, import dialogs, and no JavaScript errors in those flows.
