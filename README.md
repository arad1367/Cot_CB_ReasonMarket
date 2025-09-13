### Cot_CB_ReasonMarket

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/pejman-ebrahimi-4a60151a7/)
[![HuggingFace](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge)](https://huggingface.co/arad1367)
[![Website](https://img.shields.io/badge/Website-008080?style=for-the-badge&logo=About.me&logoColor=white)](https://arad1367.github.io/pejman-ebrahimi/)
[![University](https://img.shields.io/badge/University-00205B?style=for-the-badge&logo=academia&logoColor=white)](https://www.uni.li/pejman.ebrahimi?set_language=en)

A lightweight, single-page web experience for a research study on sustainable consumer behavior. The app guides participants through:

1. Instructions and consent
2. A randomized chatbot interaction (50-50 between “CoT (reasoning)” and “Based (no reasoning)”) with a visible timer
3. A post-interaction questionnaire prefilled with the assigned bot version

Built as a single HTML file, deployable on GitHub Pages.

#### Repository

- GitHub: https://github.com/arad1367/Cot_CB_ReasonMarket
- Live (GitHub Pages): https://arad1367.github.io/Cot_CB_ReasonMarket/ (after enabling Pages)

### Features

- Professional, mobile-friendly UI with light/dark support
- Explicit consent gate (Next button enabled only after consent)
- 5-second splash screen before chatbot assignment
- True 50-50 random assignment to:
  - CoT (reasoning) chatbot: https://www.gradio.app/guides/quickstart
  - Based (no reasoning) chatbot: https://huggingface.co/spaces/arad1367/Base-Model-Qwen2.5-3B
- Visible session timer (MM:SS)
  - Popup at 05:00: “Your interaction time is almost finished”
  - Auto-redirect to questionnaire at 06:00
- Questionnaire (Google Form) embedded via iframe
  - Auto-prefills “Bot version (Please do not change this value ⛔)” with the assigned bot label
- State is persisted with localStorage (consent, assignment, start time)

### Project Structure

- index.html
  - All layout, styles, and logic in a single file
  - Sections:
    - Page 1: Instructions + Consent
    - Page 2: Splash + Chatbot iframe + Timer
    - Page 3: Questionnaire iframe (prefilled)

No external build tools or dependencies required.

### Quick Start

- Open index.html locally to test, or deploy via GitHub Pages:
  - Create the repository: Cot_CB_ReasonMarket
  - Add index.html to the repo root
  - Settings → Pages → Source: main branch (/root)
  - Wait for Pages to publish, then access:
    - https://arad1367.github.io/Cot_CB_ReasonMarket/

### Configuration

You can customize key parameters at the top of the script block in index.html.

- Chatbot labels and URLs:

```js
const REASONING_LABEL = "CoT";
const BASED_LABEL = "Based";
const REASONING_URL = "https://www.gradio.app/guides/quickstart";
const BASED_URL =
  "https://huggingface.co/spaces/arad1367/Base-Model-Qwen2.5-3B";
```

- Google Form prefill (entry key maps to the “Bot version” short-answer question):

```js
const GOOGLE_FORM_BASE =
  "https://docs.google.com/forms/d/e/1FAIpQLSf1yQafLACRb29ziTzhq17QQgSo8wlKvrcn9f3c65TmZPCXOw/viewform";
const GOOGLE_FORM_ENTRY_KEY = "entry.1755206288";
```

- Timers:

```js
const SPLASH_SECONDS = 5;
const NOTICE_AT_SECONDS = 5 * 60; // popup at 05:00
const REDIRECT_AT_SECONDS = 6 * 60; // redirect at 06:00
```

To test shorter durations (e.g., 1 minute popup and 2 minutes redirect):

```js
const NOTICE_AT_SECONDS = 1 * 60;
const REDIRECT_AT_SECONDS = 2 * 60;
```

### How It Works

- Consent gating: The “Next” button is disabled until the consent checkbox is checked. Consent state is saved in localStorage.
- Random assignment: On entering the chatbot page, a 50-50 assignment chooses either “CoT” or “Based.” The choice is saved in localStorage and shown to the participant.
- Prefilled questionnaire: The assigned label is injected into the Google Form via URL parameters using the provided entry key.
- Timer and redirection: The timer starts when the chatbot loads. At 5 minutes a modal warns the participant; at 6 minutes the app auto-navigates to the questionnaire.

### Notes and Limitations

- Third-party embedding: Some external sites may block iframes via X-Frame-Options. The app provides a direct link fallback above the form iframe.
- LocalStorage: Assignment and timing persist across refreshes for a smoother participant experience.
- Accessibility: Semantic headings, labeled regions, and clear contrast choices are included; please validate against your institution’s accessibility requirements as needed.

### Contributing

- Fork the repo and create feature branches for changes.
- Submit PRs with clear descriptions of changes and testing steps.
- For issues (bugs, embedding problems, UI improvements), please open a GitHub Issue.

### License

Specify your preferred license here (e.g., MIT). If not specified, no license is granted by default.

### Contact

- Primary: pejman.ebrahimi@uni.li
- Alternate: pejman.ebrahimi77@gmail.com
- Supervisor: stefan.hoffmann@bwl.uni-kiel.de

For general updates and related work:

- LinkedIn: https://www.linkedin.com/in/pejman-ebrahimi-4a60151a7/
- Hugging Face: https://huggingface.co/arad1367
- Personal Website: https://arad1367.github.io/pejman-ebrahimi/
- University page: https://www.uni.li/pejman.ebrahimi?set_language=en

If this project helps your research, please consider starring the repo: https://github.com/arad1367/Cot_CB_ReasonMarket ⭐
