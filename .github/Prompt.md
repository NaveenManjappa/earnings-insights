Generate a single-file web page based on the attached earnings call transcript. You MUST follow the exact HTML structure and styling below to ensure consistency with the project.

### Design System Requirements
- **Framework**: Tailwind CSS (via CDN).
- **Font**: Inter (Google Fonts).
- **Colors**: Use `slate` for grays (e.g., `bg-slate-50`, `text-slate-900`). Do NOT use `gray` or `zinc`.
- **Layout**: Vertical split-screen (60% Left / 40% Right).

### HTML Template (Strictly Follow This Structure)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>[Company Name] - [Quarter] Earnings Call</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
    <style>
      body { font-family: "Inter", sans-serif; }
      .scrollbar-hide::-webkit-scrollbar { display: none; }
      .scrollbar-hide { -ms-overflow-style: none; scrollbar-width: none; }
      .transcript-text { line-height: 1.7; font-size: 1.05rem; }
    </style>
  </head>
  <body class="bg-slate-50 h-screen flex flex-col md:flex-row overflow-hidden">
    <!-- LEFT PANEL: Transcript (60%) -->
    <div class="w-full md:w-[60%] h-full flex flex-col border-r border-slate-200 bg-white">
      <!-- Header -->
      <div class="p-6 border-b border-slate-100 bg-white/80 backdrop-blur-md sticky top-0 z-10 flex items-center justify-between">
        <div>
          <h1 class="text-xl font-bold text-slate-900">Earnings Call Transcript</h1>
          <p class="text-sm text-slate-500">[Company Name] • [Quarter] • [Date]</p>
        </div>
        <a href="../../../index.html" class="group flex items-center gap-2 px-3 py-2 rounded-lg text-slate-500 hover:text-indigo-600 hover:bg-indigo-50 transition-all">
          <svg class="w-5 h-5 transition-transform group-hover:-translate-x-1" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"></path>
          </svg>
          <span class="text-sm font-medium">Back</span>
        </a>
      </div>

      <!-- Scrollable Content -->
      <div class="flex-1 overflow-y-auto p-6 space-y-8 pb-20" id="transcript-container">
        <!-- Transcript Content Goes Here -->
        <!-- Use <p class="text-slate-700 transcript-text"> for all speech text -->
        <!-- Use <span class="font-bold text-indigo-800 uppercase text-xs tracking-wider"> for Speaker Names -->
      </div>
    </div>

    <!-- RIGHT PANEL: Analysis (40%) -->
    <div class="w-full md:w-[40%] h-full overflow-y-auto bg-slate-50 border-l border-slate-200">
      <div class="p-8 space-y-8">
        <!-- Summary, Key Takeaways, Financials, Variables to Track -->
        <!-- Use standard Tailwind cards: bg-white p-6 rounded-lg shadow-sm border border-slate-200 -->
      </div>
    </div>
  </body>
</html>
```

### Content Instructions
1.  **Left Panel (Transcript)**:
    *   Include the **FULL, VERBATIM** transcript. Do not summarize or truncate.
    *   Every question and answer must be preserved.
    *   Format speaker names and text using the classes provided in the template.

2.  **Right Panel (Analysis)**:
    *   **Executive Summary**: A high-level overview of the quarter.
    *   **Key Takeaways**: Bullet points on Strategy, Operations, and Future Outlook.
    *   **Financial Snapshot**: A grid showing Revenue, EBITDA, PAT, etc.
    *   **Variables to Track**: A dark card (`bg-slate-800 text-white`) listing key metrics to watch.

3.  **Output**: Return ONLY the valid HTML code.