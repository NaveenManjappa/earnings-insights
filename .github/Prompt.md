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
      .scrollbar-thin::-webkit-scrollbar { width: 6px; }
      .scrollbar-thin::-webkit-scrollbar-track { background: #f1f5f9; }
      .scrollbar-thin::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 3px; }
      .scrollbar-thin::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
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

      <!-- Scrollable Transcript Content -->
      <div class="flex-1 overflow-y-auto p-8 space-y-8 pb-20 scrollbar-thin" id="transcript-container">
        <!-- TRANSCRIPT CONTENT GOES HERE - Follow the speaker formatting rules below -->
      </div>
    </div>

    <!-- RIGHT PANEL: Analysis (40%) -->
    <div class="w-full md:w-[40%] h-full overflow-y-auto bg-slate-50 border-l border-slate-200 scrollbar-thin">
      <div class="p-8 space-y-8">
        <!-- Summary, Key Takeaways, Financials, Variables to Track -->
        <!-- Use standard Tailwind cards: bg-white p-6 rounded-lg shadow-sm border border-slate-200 -->
      </div>
    </div>
  </body>
</html>
```

---

### Left Panel: Transcript Formatting Rules

Use the **Clean Minimal** design with left-border color coding to distinguish speaker types.

#### Speaker Types & Styling

| Speaker Type | Left Border | Background | Example |
|--------------|-------------|------------|---------|
| **Moderator** | `border-slate-300` | None | Call operator |
| **Management** | `border-emerald-400` | None | CEO, CFO, MD |
| **Analyst/Investor** | `border-blue-400` | `bg-blue-50/50` | Questions from analysts |

#### HTML Patterns for Each Speaker Type

**1. Moderator (subtle styling):**
```html
<div class="border-l-2 border-slate-300 pl-5">
  <div class="flex items-center gap-2 mb-2">
    <span class="text-sm font-semibold text-slate-500">Moderator</span>
  </div>
  <p class="text-slate-600 leading-[1.85] text-[15px]">
    [Moderator's speech text here]
  </p>
</div>
```

**2. Management (prominent, green border):**
```html
<div class="border-l-2 border-emerald-400 pl-5">
  <div class="flex items-center gap-3 mb-3">
    <span class="text-base font-bold text-slate-900">[Speaker Name]</span>
    <span class="text-xs text-emerald-600 font-medium bg-emerald-50 px-2 py-0.5 rounded">[Role, e.g., MD & CEO]</span>
  </div>
  <div class="text-slate-700 leading-[1.85] text-[15px] space-y-4">
    <p>[Paragraph 1]</p>
    <p>[Paragraph 2]</p>
    <!-- Add more <p> tags for each paragraph -->
  </div>
</div>
```

**3. Analyst/Investor Question (blue border + subtle background):**
```html
<div class="border-l-2 border-blue-400 pl-5 bg-blue-50/50 -ml-5 py-4 pr-4 rounded-r-lg">
  <div class="flex items-center gap-3 mb-3 ml-5">
    <span class="text-base font-bold text-slate-900">[Analyst Name]</span>
    <span class="text-xs text-blue-600 font-medium">[Firm Name]</span>
  </div>
  <p class="text-slate-700 leading-[1.85] text-[15px] ml-5">
    [Question text here]
  </p>
</div>
```

**4. Q&A Section Divider (insert before Q&A begins):**
```html
<div class="relative py-6">
  <div class="absolute inset-0 flex items-center">
    <div class="w-full border-t border-slate-200"></div>
  </div>
  <div class="relative flex justify-center">
    <span class="bg-white px-4 text-sm font-semibold text-slate-400 uppercase tracking-wider">Question & Answer</span>
  </div>
</div>
```

**5. Highlighting Key Numbers (use within any paragraph):**
```html
<mark class="bg-emerald-100 text-emerald-800 px-1 rounded font-medium">₹150-200 crores</mark>
```

---

### Content Instructions

1. **Left Panel (Transcript)**:
   - Include the **FULL, VERBATIM** transcript. Do not summarize or truncate.
   - Every question and answer must be preserved.
   - Use **mixed-case** for speaker names (NOT ALL CAPS).
   - Apply the correct speaker styling based on role (Moderator/Management/Analyst).
   - Insert the Q&A section divider before the first analyst question.
   - Highlight important numbers and metrics using the `<mark>` tag.
   - Split long speeches into multiple `<p>` tags for better readability.

2. **Right Panel (Analysis)**:
   - **Executive Summary**: A high-level overview of the quarter.
   - **Key Takeaways**: Bullet points on Strategy, Operations, and Future Outlook.
   - **Financial Snapshot**: A grid showing Revenue, EBITDA, PAT, etc.
   - **Variables to Track**: A dark card (`bg-slate-800 text-white`) listing key metrics to watch.

3. **Output**: Return ONLY the valid HTML code.
