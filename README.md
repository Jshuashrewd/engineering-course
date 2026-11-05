# Fieldnotes Learning Studio

This is the updated, data-driven learning site for the Backend Engineering and AI/ML Master Roadmap. The curriculum, lesson content, DSA thread, browser interface and progress ledger are in `index.html`.

## Run the site

Use Node.js 20 or newer; no package installation or build step is needed.

```sh
node server.js
```

Then open <http://127.0.0.1:4173>. The server binds to localhost only. Opening `index.html` directly with `file://` will display the lessons and local progress, but the tutor API will not connect.

## Tutor setup

The app does not fabricate tutor replies. The server has a provider adapter and defaults to local Ollama at `http://127.0.0.1:11434`, using `qwen2.5:1.5b` unless `TUTOR_MODEL` is set. Ollama is not bundled or installed by this project. If you choose to install it, start Ollama and download a model that fits your machine. Until the local service and selected model are available, the tutor reports that it is unavailable and keeps your question in the local learning record.

No paid model API is configured or called. The browser never holds a model key. A future provider can implement the same server-side `chat({ messages })` adapter without changing the browser API contract; review any provider cost and privacy terms before enabling one.

The tutor gives formative teaching feedback only. It does not score mastery or unlock modules. Gate and pre-check submissions remain pending until reviewed scores are explicitly recorded.

## Progress and privacy

New-roadmap progress uses the browser-local `fieldnotes-master-v1` key. It persists in that browser profile on that device and is not synchronized. Use **Evidence & review → Export learning record** for a portable backup. The former `fieldnotes-v1` record is read-only archived and does not count as mastery. Resetting new-roadmap data does not delete that old key.

## Assessment integrity

The website does not start a pre-check or gate automatically. A submission remains pending. To record a result, enter an independent review source, all four rubric scores and the review confirmation. A pass requires no score below 2 and at least 9/12; 11/12 or higher is labelled mastered. Retakes of failed gate parts are available after 48 hours and keep previously passed parts.

All deliberate fault-injection tasks are for development/staging with synthetic data only. Do not run them against a live production system.
