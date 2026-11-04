# Poralekha Bondhu (পড়ালেখা বন্ধু)

A Bangla-first AI study companion for Bangladeshi SSC/HSC students, built for the **Meta Global AI Developer Hackathon** (Cerebral Valley, Oct 26 – Nov 4, 2026), Indie Dev Track, solo build.

**Live app:** open `index.html` in any browser (or the GitHub Pages link for this repo).

## What it does

Poralekha Bondhu is not a generic chatbot. It is built specifically for Bangladeshi students studying in Bangla:

- 🎓 **Tutor** — asks and answers curriculum questions in simple Bangla
- 📝 **Question maker** — generates practice questions from a topic
- 🗓️ **Today's plan** — builds a daily study plan
- 📸 **Learn from a photo** — explains a photographed textbook page/question

The UI supports 16 languages (with full RTL for Arabic/Urdu) plus an "Other language (AI)" mode, and uses a smart first-open language (browser language if supported, otherwise English; a manual pick always wins).

## Which Meta AI model it uses, and where it runs

This app is powered by **Muse Glimmer** (`muse-glimmer:30b-q4_K_M`), Meta's open-weight model, served with **Ollama**.

**Disclosure (per hackathon guidance):**

- The model does **not** run on a hosted/partner inference service. It runs on a **free Kaggle GPU notebook (Tesla T4 ×2) that I operate myself**.
- The Kaggle notebook in this repo (`poralekha-glimmer-kaggle.ipynb`) installs Ollama, pulls the model, starts the server, and opens a temporary Cloudflare tunnel so the browser app can reach the model over an OpenAI-compatible API.
- Kaggle sessions are temporary: when a session ends, the model and tunnel stop, and the notebook must be re-run to start them again (install + pull takes only a few minutes — verified end-to-end on 2026-11-02, including a correct Bangla answer to a fractions question).
- The app stores the API URL / model name / key **only in the phone/browser localStorage of the user**. **No API keys, tokens, or passwords are in this repository.**

## How to run it

1. Open `index.html` in a browser (no build step, no server needed).
2. Start the model: open the Kaggle notebook, run all cells (install → serve → pull → tunnel), and copy the tunnel URL it prints.
3. In the app's Settings, paste the tunnel URL as the API base URL and set the model to `muse-glimmer:30b-q4_K_M`.
4. Ask a question in Bangla — the answer comes from Muse Glimmer.
5. Without a model connected, the app runs in a clearly labelled **demo mode** with sample answers.

## What was built when

- The app, its UI translations, and this Kaggle/Glimmer setup were built **during the hackathon week (Oct 26 – Nov 4, 2026)**.
- Nothing in this repo pre-dates the event except the idea itself.

## About the builder

MD Rifat Hasan — higher-secondary student from Bhaluka, Mymensingh, Bangladesh. Built entirely phone-only (no computer, no payment card), which is why the model runs on a free self-operated cloud GPU instead of a paid inference service.
