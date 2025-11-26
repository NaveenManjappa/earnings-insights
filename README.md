# Earnings Insights

Earnings Insights is a web application designed to provide smart, AI-powered analysis of quarterly earnings conference calls. It presents full transcripts alongside key insights, summaries, and important variables to track, all in a clean, modern interface.

The goal is to make it easier for investors and analysts to digest long earnings calls by having the verbatim text and high-level analysis side-by-side.

## Features

- **Smart Analysis**: AI-generated summaries and key takeaways.
- **Split-Screen View**: Read the full transcript while referencing insights.
- **Clean UI**: Modern, fintech-inspired design using Tailwind CSS.
- **Searchable**: Quickly find companies and their quarterly concall transcripts.

## Contributing

We welcome contributions! If you want to add a new earnings call transcript and analysis, please follow these steps:

### 1. Generate the Analysis Page

We use a standardized prompt to ensure consistency across all reports.

1.  **Get the Transcript**: Obtain the text transcript of the earnings call you want to add.
2.  **Use the Prompt**: Copy the content of [.github/Prompt.md](.github/Prompt.md).
3.  **Generate HTML**: Paste the prompt and the transcript into an LLM (like ChatGPT, Claude, or Gemini). The model will generate a single HTML file with the transcript and analysis.
4.  **Save the File**:
    -   Create a folder for the company in `companies/` if it doesn't exist (use a kebab-case slug, e.g., `reliance-industries`).
    -   Create a `concalls` folder inside the company folder.
    -   Save the generated HTML file as `YYYY-QX.html` (e.g., `2025-Q1.html`).

### 2. Register the Data

To make the new report visible in the application, you need to update the manifest.

1.  Open `js/app.js`.
2.  Locate the `MANIFEST_DATA` object.
3.  Add your new entry. If the company is new, add a new key. If it exists, append the quarter to the array.

```javascript
const MANIFEST_DATA = {
    "rr-kabel": ["2026-Q2"],
    "your-new-company": ["2025-Q1"] // Add your entry here
};
```

### 3. Submit a Pull Request

-   Commit your changes (the new HTML file and the updated `app.js`).
-   Push to your fork and submit a Pull Request to the main repository.

## License

[MIT](LICENSE)
