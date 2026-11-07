# Claude Course — Use Case Gallery (chi tiết)

> File phụ của `Claude_Course.md` — tóm tắt gọn **156 use cases** từ [academy.claude.com/use-cases](https://academy.claude.com/use-cases) (11/2026).
> Mỗi mục:
>
> - **Prompt mẫu** (rút gọn — bản đầy đủ tại link gốc)
> - **Context** (connectors cần bật)
> - **Output** (kết quả tạo ra)
> - **Tips** (vì sao prompt hiệu quả)
> - **Plugins** (skills Cowork đi kèm).
>
> 96 use cases kiểu Chat có mẫu output; 60 kiểu Cowork/Tag không có (đánh dấu bằng hàng Tips/Plugins).

## Chung (mọi role) (28)

### 1. Build a daily briefing across your tools
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-a-daily-briefing-across-your-tools)

> Generate a daily briefing that pulls from Slack, Notion, and your team dashboard to surface priorities and connections you'd miss scanning each platform separately.

**Prompt mẫu:**
> "I need my morning briefing.
> Pull from Slack and Notion, and visit my team dashboard: https://metrics.acme-corp.com/ops-team Structure it as: Urgent items from the dashboard (anything red or trending down)
> Slack threads where I'm mentioned — read the full threads for context"

**Output:** Cowork creates a structured briefing organized by priority, with cross-platform context synthesized into single items where relevant.
Using the Claude in Chrome connector, Claude opens your dashboard in a new browser tab and reads it directly, pulling metrics…

### 2. Clean up promotional emails
*15′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/clean-up-promotional-emails)

> Claude in Chrome can scan your inbox, identify promotional and marketing emails, and flag them for your review. You decide what to delete in bulk rather than clicking through one by one.

**Prompt mẫu:**
> "Find emails I likely don't need so I can review and bulk delete.
> Flag these: Promotional emails from retailers/brands Newsletters I haven't opened in 3+ months Automated notifications (delivered shipping updates, expired calendar reminders)"

**Output:** Claude uses your session to scan and sort through your inbox. Claude presents what it found, organized for your review.

### 3. Compare and analyze competing options
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/compare-and-analyze-competing-options)

> Upload vendor proposals in any format and get a normalized comparison spreadsheet that extracts pricing structures, contract terms, and feature differences

**Prompt mẫu:**
> "I'm evaluating three payroll providers and need to decide by Friday. I've uploaded proposals from PayFlow Pro, TeamSync HR, and WorkForce Central.
> Extract and compare base monthly costs and fees, onboarding timelines, contract lengths and terms, key feature differences, and support options. Create a comparison spreadsheet that shows every…"

**Output:** Claude reads each proposal completely, extracts pricing and terms, identifies differences that matter for your decision, and creates a comparison spreadsheet.

### 4. Create a company newsletter
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-company-newsletter)

> Stay informed with a publication-style digest that synthesizes company news from all your channels.

**Prompt mẫu:**
> "Create a weekly digest for Oct 14-20 for my company.
> Pull information from relevant channels in my Slack, such as #company-announcements, #product-updates, #leadership, and any other channels where major decisions happened.
> Include data visualizations where useful. Use a dense but readable layout. Pack information efficiently and use soph…"

**Context:** Google Drive, Gmail, Slack (bắt buộc)

**Output:** Claude reads across all your channels, filters for important discussions, and organizes updates into topic-based sections.
You'll receive a clear summary of events, without needing to piece together information from various messages.

### 5. Create a process flowchart
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-process-flowchart)

> Turn written procedures into visual flowcharts that make complex processes easier to follow and share.

**Prompt mẫu:**
> "enterprise software implementation playbook—42 pages of customer onboarding procedures that nobody can navigate in real-time.
> We have a few different paths based on data quality, integration capability, resources, and deployment readiness.
> Can you help me visualize this so we can see the whole system in one view and understand how custome…"

**Output:** Claude analyzes your process documentation and transforms it into an interactive Sankey flow diagram that visualizes implementation pathways and volume distribution across paths.
Each implementation phase becomes a clickable card that reveals the detailed docu…

### 6. Create interactive PDF forms
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-interactive-pdf-forms)

> Turn forms from static documents into professional, interactive forms that people fill out right in their PDF reader.

**Prompt mẫu:**
> "I'm organizing a three-day conference in June (Innovation Summit 2025) and need a professional registration form that attendees can fill out digitally.
> Create an interactive PDF registration form with these sections: Attendee Information: Full name, email (required fields), company/organization and job title (optional) Registration Detail…"

**Output:** Claude creates an interactive PDF with all your specified form fields and information, ready to distribute.
Recipients can open it in any PDF reader to fill in their information and send it back.

### 7. Daily bookends
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/morning-evening)

> A briefing to start the day and a wrap to close it.

**Prompt mẫu:**
> "Run my morning briefing.
> Tell me what's on fire, what's due, who's waiting on me, and the three things I should do first Keep it under a page Tonight I'll ask you to run /update and you'll write the wrap: what got done,
> what slipped, and what tomorrow opens with Daily"

**Context:** Google Calendar, Slack, Gmail, Microsoft 365, Linear, Notion (bắt buộc)

**Plugins:** start, update

**Tips:**
- Name the sections you want.
- Set a length limit.
- Connect each run to the next.

### 8. Develop a program toolkit
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/develop-a-program-toolkit)

> Generate complete program design frameworks for new initiatives with logic models, evaluation plans, and resource guides that transform concepts into implementation-ready programs.

**Prompt mẫu:**
> "Program Structure: 6-hour virtual course covering IT career pathways, resume building, interview skills,
> and professional networking 4 one-on-one career coaching sessions to support job search and applications Target Outcomes: 80% course completion, 60% job placement within 90 days,
> $40K average starting salary."

**Output:** Claude generates a multi-sheet Excel workbook that serves as your complete program planning resource.
Each sheet functions as a standalone tool while connecting to create an integrated framework.

### 9. Explore what Claude can do for you
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/explore-what-claude-can-do-for-you)

> New to Claude? Start here. Tell Claude your role and get a personalized guide to the capabilities that will matter for your work.

**Prompt mẫu:**
> "I'm a product manager at a B2B SaaS startup. I mostly work on roadmap prioritization and customer research. I'm new to Claude. How can I use you most efficiently?
> Can you give me 5 examples I can try right now, ideally things that would actually make a difference in my daily work. Surprise me with one of them! I’ve given you access to my…"

**Context:** Optional (bắt buộc)

**Output:** Claude produces a personalized starter guide based on your role and documents. Each suggestion includes a specific example prompt you can try immediately.
If you've shared documents, Claude references your actual projects and offers to demonstrate a capability…

### 10. Generate an AI policy
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/generate-an-ai-policy)

> Create organization-specific AI usage policies covering data privacy, appropriate use cases, staff guidelines,
> and ethical considerations tailored to your nonprofit's mission and beneficiary protection needs.

**Prompt mẫu:**
> "First, use Research to find examples of AI policies from other nonprofits, particularly those serving vulnerable populations or working with youth.
> I want to understand what governance frameworks are emerging in the sector and what specific protections other organizations are implementing. Key context about our organization: We work with…"

**Context:** Web Search

**Output:** Claude develops a complete AI governance system with two professional deliverables that work together.

### 11. Generate project status reports
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/generate-project-status-reports)

> Pull status updates from your emails, Slack channels, meeting notes, and project tools to create a tracker that shows who's working on what, what's blocked,
> and where things stand—all in one place.

**Prompt mẫu:**
> "I need to consolidate project status from multiple sources into a task tracker.
> Pull information from: Gmail (past 2 weeks, search "Project Hermes") Slack #hermes-sprint channel Google Drive "Project Hermes" folder"

**Context:** Google Drive, Gmail (bắt buộc)

**Output:** Claude searches your connected tools, finds status updates from different sources, reconciles them into a single view,
and creates an Excel tracker with visual indicators and context in cell comments.

### 12. Genomic data analysis
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/genomic-data-analysis)

> With Claude as your research partner, analyze gene expression data to identify patterns and form testable hypotheses about biological mechanisms,
> while Claude handles the computational heavy lifting of bioinformatics and literature synthesis.

**Prompt mẫu:**
> "My colleagues recently published the attached single-cell dataset that describes gene expression differences between adult and pediatric liver samples with a focus on the immune system.
> I would like to explore these samples but focus on the parenchymal cells and differences between adult and pediatric liver. Can you help me first go throu…"

**Output:** Claude examines your datasets, performs pathway enrichment analysis, creates visual representations of gene expression patterns,
and identifies key biological processes enriched in each condition.

### 13. Grant proposal assembly line
*20′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/grant-proposal-assembly-line)

> Build a modular content library from your successful proposals and organizational materials then produce foundation-ready submissions in a fraction of the usual time.

**Prompt mẫu:**
> "I need to build a grant proposal assembly line system to handle our 20+ annual grant applications more efficiently.
> We apply to foundations, government agencies, and corporate funders for youth programs, workforce development, and education initiatives.
> Start by creating a modular content library from the materials I'm providing: 3 recent…"

**Context:**
- Google Drive, Gmail (bắt buộc)
- Web Search

**Output:** Claude builds a complete grant proposal assembly line system with three integrated components that work together to dramatically reduce writing time.

### 14. Preclinical study analysis
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/preclinical-study-analysis)

> Build study reports by connecting to research platforms and compiling data across experiments.

**Prompt mẫu:**
> "Summarize the study designs for ST042 and ST043 and how they're different, including a table indicating key differences. Link all my notebook entries and sources."

**Context:** Benchling (bắt buộc)

**Output:** Claude connects to Benchling's agents to retrieve your study data, then synthesizes a comprehensive summary with key differences highlighted.

### 15. Prep call look-ahead
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/week-ahead-prep)

> Agendas and context for every meeting next week.

**Prompt mẫu:**
> "Look at my calendar for next week. For each meeting, pull the context: the last time we met, related Slack threads, attached or mentioned docs, and open items I owe them.
> Draft a one-paragraph agenda for each and flag the three I most need to prep for Write it all to a single week-ahead doc for Sunday night. Planning / Week-of-2026-04-27"

**Context:**
- Google Calendar, Slack, Gmail, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** start

**Tips:**
- Ask which ones matter most.
- Ask for one combined output.

### 16. Prepare and plan from your calendar
*10′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/prepare-and-plan-from-your-calendar)

> Claude in Chrome reads your calendar, pulls context from email threads, flags which meetings need prep, and books rooms for the ones missing them.
> Run it every evening and start each day knowing what's coming.

**Prompt mẫu:**
> "Look at my calendar and help me get ready for tomorrow.
> For each meeting: Tell me if it's internal or external (check the attendee domains)
> Find any recent email threads with those attendees about this topic Flag if the meeting is missing a room (for in-person) or a video link (for remote). If it is, assign one to the meeting."

**Output:** Claude reviews each meeting and gives you a prep summary organized by what needs attention.

### 17. Quickly prep for your week
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/quickly-prep-for-your-week)

> Prepare and prioritize for your upcoming week through connecting your calendar and mail platforms.

**Prompt mẫu:**
> "Help me plan my upcoming week: October 27-31. Using my M365 connector look at my Outlook calendar and find all meetings that need prep, or where I'm making decisions.
> Show me where I'm overbooked, where I have real focus time, and any scheduling problems I need to fix now. From my Outlook inbox and summarize any weekend emails I need to h…"

**Context:** Microsoft 365 (bắt buộc)

**Output:** Claude reads your sources simultaneously, analyzing what matters, and showing you how to prepare for the week ahead.

### 18. See what your campaign goal actually requires
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/see-what-your-campaign-goal-actually-requires)

> Type a campaign goal and Claude draws the gift pyramid inline, tiered from the lead gift down,
> with each tier showing how many gifts you need and how many qualified prospects that realistically takes. Drag the goal and the whole shape rebuilds.
> For when you're wondering whether a campaign is feasible before you say yes to it.

**Prompt mẫu:**
> "We're thinking about a $2M capital campaign.
> Show me what the gift pyramid needs to look like, meaning how many donors at each tier and how many qualified prospects I'd realistically need behind each one.
> Let me drag the goal and watch the shape change, and flag the tiers where I'm probably thin."

**Output:** Claude draws a five- or six-tier pyramid with each tier showing three numbers: the gift range, the number of gifts the campaign needs at that level,
and the number of qualified prospects that realistically takes. A slider above lets you drag the goal and watch…

### 19. See why donor retention beats acquisition, in chat with Claude
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/see-why-donor-retention-beats-acquisition)

> Claude builds a five-year donor projection with sliders for retention and acquisition.
> Drag either one and the curve redraws, and it becomes clear fairly quickly why a modest retention bump does more than doubling the acquisition spend.

**Prompt mẫu:**
> "Everyone keeps telling me donor retention matters more than acquisition and I understand the argument but I don't really get it. Show me. Start with 100 donors and let me play with the numbers.
> I want to drag things and watch what happens."

**Output:** Claude draws a five-year line chart with two sliders underneath, one for retention rate and one for new donors per year.
Dragging either slider bends the curve and rewrites a one-sentence note below that explains what the new numbers mean in plain terms. What…

### 20. See your theory of change in chat with Claude
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/see-your-theory-of-change-in-chat-with-claude)

> Describe your program and Claude draws the causal chain inline, inputs through impact, with every arrow clickable to show the assumption behind it.
> For when you know what you do but have never drawn why it works.

**Prompt mẫu:**
> "I run a youth mentoring program. We pair high schoolers with adult mentors for weekly meetings over a year, and the goal is higher graduation rates.
> Show me our theory of change, and I want to be able to click the arrows between boxes to see what assumption each one is riding on. Where are the weak links?"

**Output:** Claude draws your program's causal chain as five connected boxes running left to right, with every arrow between them clickable.
The boxes will look familiar since they're the standard logic model categories, but the arrows are where the real work happens. Cli…

### 21. Size a market using your research
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/size-a-market-using-your-research)

> With Cowork, ask Claude a market question and get back an analysis with professional deliverables.
> Claude researches, calculates, and outputs a PowerPoint presentation, Excel workbook with detailed methodology, and Markdown source document with citations.

**Prompt mẫu:**
> "I need a market sizing analysis for the enterprise project management software space in North America.
> Include TAM/SAM/SOM calculations with your methodology, key market drivers and growth projections, competitive landscape overview, and investment implications.
> Output as: Executive PowerPoint (10-12 slides) Excel workbook with detailed c…"

**Output:** Claude researches the market, applies the TAM/SAM/SOM framework, and generates three coordinated deliverables.

### 22. Slack and Teams message sweep
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/message-sweep)

> A topic-grouped sweep of your important channels.

**Prompt mẫu:**
> "Sweep my unread Slack DMs and mentions, Teams activity feed, and Gmail inbox from the last 24 hours. Group everything by topic, not by app.
> For each topic, tell me whether it needs a reply from me, needs reading, or is just FYI.
> Draft a reply for everything in the first bucket and keep each to three sentences or fewer Notes / Inbox-Sweeps"

**Context:** Slack, Gmail (bắt buộc)

**Plugins:** start

**Tips:**
- Say how to group the results.
- Sort by the action needed.
- Set a length limit.

### 23. Source insights from your tools to build a deck
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/source-insights-from-your-tools-to-build-a-deck)

> Claude Opus 4.6 chases leads across scattered sources, surfaces what no single source shows on its own, and builds a presentation around the through-line.

**Prompt mẫu:**
> "I’m prepping for board meeting Friday. Q3 was the quarter where everything happened at once: we shipped the platform consolidation, closed the Apex partnership, and lost two enterprise accounts.
> Start with the Q3 project tracker in my local files; it has the key people, channels, and documents. Follow each person across their channels, em…"

**Context:** Slack, Gmail, Google Drive (bắt buộc)

**Output:** Opus 4.6 works outward from the starting point you give it, pulls context from each source it finds, and saves three files locally: a presentation with narrative structure,
a supporting data appendix, and an executive pre-read. Through Claude in Chrome, it ope…

### 24. Thread to decision doc
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/thread-to-decision)

> What was decided, who owns it, what's still open.

**Prompt mẫu:**
> "Tell me what was actually decided who owns each next step with the date they committed to, and what's still open or contested.
> Append it to the decision log: decision, owners, open questions, links back to the source messages. No commentary, just the record. Team / Decisions"

**Context:**
- Slack, Gmail, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** task-management

**Tips:**
- Ask for what was actually decided.
- Require an owner and a date.
- Call out what's still open.

### 25. Turn emails into an event tracker
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/turn-emails-into-an-event-tracker)

> Build an event tracker by extracting dates, locations, and logistics from email threads.

**Prompt mẫu:**
> "I'm organizing our annual conference in March and sent speaker invitations about three weeks ago to around 45 people.
> Used "Speaker Invitation: Summit 2025" in the subject but people replied with all different subject lines - some just said "sounds great," others replied to old email threads we had going.
> Search my Gmail for speaker confi…"

**Context:** Gmail (bắt buộc)

**Output:** Claude searches your inbox for the confirmation emails, reads through each response to find the specific details you requested, and structures all of the answers into a spreadsheet.

### 26. Visualize program data
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/visualize-program-data)

> Transform spreadsheets of program statistics into presentation-ready charts, infographics,
> and dashboards that tell your impact story visually and help demonstrate program satisfaction to stakeholders.

**Prompt mẫu:**
> "The data includes: participants enrolled and completed, completion rates, satisfaction scores (1-5 scale), Net Promoter Scores, pre/post-test averages, knowledge gains, repeat participants,
> referrals, volunteer hours, and cost per participant. I need to create a comprehensive visualization suite for our board meeting next week. Create:"

**Context:** Google Drive (bắt buộc)

**Output:** Claude analyzes your program data to identify trends, calculate performance metrics, and create a comprehensive visualization suite tailored to your stakeholder needs.

### 27. Write an impact report
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/write-an-impact-report)

> Turn raw program data and participant outcomes into compelling narratives with data visualizations, stakeholder-specific insights, and authentic success stories that demonstrate real impact.

**Prompt mẫu:**
> "I'm uploading our program data: student enrollment and demographics, attendance records, academic assessment results (pre/post test scores), volunteer hours, and our financial summary.
> We served 347 students this year across three locations. For the report, I need: An executive summary with our biggest wins and key metrics Compelling data…"

**Output:** Claude analyzes your data to find the strongest evidence of impact, then creates a comprehensive report that tells your story through both numbers and narrative.

### 28. Write in my voice
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/my-voice)

> A profile of how you write, saved as a skill.

**Prompt mẫu:**
> "Read my sent messages and tell me about my tone and writing style Personal / Writing-Samples"

**Context:**
- Gmail, Slack, Microsoft 365, Notion, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** memory-management, my-voice

**Tips:** Start simple.

## Finance — Tài chính (18)

### 29. Build analysis from browser charts and folder data
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-analysis-from-browser-charts-and-folder-data)

> Pull your quarterly revenue from scattered board decks, then grab GDP and inflation data from FRED. Cowork creates a comparison chart showing how your growth stacks up against the macro environment.

**Prompt mẫu:**
> "I'm preparing for our board meeting and need to show how our growth compares to the broader economy.
> Pull our revenue figures Q1-Q4 2025 board decks Using Claude in Chrome to open FRED in my browser and grab GDP growth and inflation for the same quarters.
> Create a chart comparing our revenue growth to these economic indicators. Save the c…"

**Output:** Cowork extracts the revenue figures from each deck and produces a comparison chart with supporting analysis.
Using the Claude in Chrome connector, Claude opens FRED in a new browser tab and pulls the economic indicators directly from the site, then combines ev…

### 30. Build financial models
*20′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-financial-models)

> Create investment analyses with complete financial models, scenario planning, and risk evaluation.

**Prompt mẫu:**
> "I'm evaluating MediTech Solutions (healthcare SaaS) and need a complete investment analysis. Deal structure: $75M growth equity stake at 3.6x ARR entry, exit at 7.0x in year 5.
> Current metrics are $50M ARR growing 35% with 18% EBITDA margin. Get the company financials from Daloopa - search for MediTech Solutions and pull their historical…"

**Context:**
- Daloopa, Box, S&P Global (bắt buộc)
- Web Search

**Output:** Claude pulled financials from Daloopa, analyzed healthcare SaaS comparables from S&P Capital IQ, built three-scenario projections with sensitivity analysis,
and formatted the multi-sheet model to match your IC template standards.

### 31. Contract to ledger extraction
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/contract-to-ledger)

> ASC 606 fields pulled from the contract, exceptions flagged before they hit the GL.

**Prompt mẫu:**
> "Extract the ASC 606 fields (performance obligations, standalone selling price, contract term, billing schedule, variable consideration) from every executed contract into the rev-rec intake sheet,
> and flag any that don't match a standard pattern for my review before booking Revenue / Intake / 2026-W17"

**Context:** Salesforce (tùy chọn)

**Plugins:** journal-entry

**Tips:**
- List the exact fields you need.
- Ask it to flag the exceptions.
- Process the whole batch at once.

### 32. Draft a credit memo from spreads and statements with Claude for Excel
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/draft-a-credit-memo-from-spreads-and-statements-with-claude-for-excel)

> Cowork pulls the borrower's filings and spreads through the S&P Global connector and reads the underwriting workbook from your deal folder.
> You take the ratios and exceptions into Claude for Excel to update the model, then bring the writeup into Claude for Word for the credit memo.

**Prompt mẫu:**
> "Claude pulls the spreads and runs the ratios; you make the credit decision. Acme Manufacturing — $25M revolver renewal, committee Thursday. Walk me through the credit before I touch the spread.
> Steps: Pull three years of financials and peer spreads from S&P Global Read the underwriting workbook in the deal folder and flag where ratios tri…"

**Context:** S&P Global (bắt buộc)

**Output:** A brief you can act on: where the borrower stands against policy, which ratios moved since last review, and the exact cells to look at when you open the spread.

### 33. Draft investment memos
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/draft-investment-memos)

> Generate investment memos from platform data, formatted to match your firm's structure and requirements.

**Prompt mẫu:**
> "I'm evaluating CloudBridge Technologies (ticker: CLDG) for a potential equity investment and need an initial memo for our IC meeting next week.
> Pull the data I need: Using Daloopa, get CloudBridge's revenue, operating margins, and free cash flow for the last 12 quarters, plus their segment revenue breakdowns.
> Using Kensho, identify who Cl…"

**Context:**
- Daloopa, S&P Global (bắt buộc)
- Web Search

**Output:** Claude pulls data from Daloopa and S&P Global, calculates growth rates and margins, compares performance across competitors,
and generates a professional Word document ready for investment committee review.

### 34. Evaluate a company from the science to the balance sheet
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/evaluate-a-company-from-the-science-to-the-balance-sheet)

> Claude Opus 5.5 runs due diligence across SEC filings, clinical trial data, and patent documents at once, evaluating the science, modeling the financials,
> and catching where one contradicts the other.

**Prompt mẫu:**
> "I'm evaluating Meridian Therapeutics (~$4B mid-cap biotech) ahead of their Phase III readout. I've uploaded the 10-K, 10-Q, proxy, trial protocol, and patent filings.
> Evaluate the science and trial design. Build a risk-adjusted pipeline valuation. Flag anything in the filings that contradicts management's guidance or earnings narrative. M…"

**Output:** Claude produces an integrated research memo, a downloadable financial model, an interactive scenario dashboard, and a patent cliff timeline.
Opus 5.5 reads across all five documents simultaneously, and one finding it surfaced on its own is the kind of detail t…

### 35. Explain a variance
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/explain-a-variance)

> The variance narrative, written from the actuals.

**Prompt mẫu:**
> "Draft this month's variance commentary for the monthly review.
> Compare actuals to last month and to budget, and for every line that moved more than 10% or $50K explain what moved and why,
> in plain English for a leadership audience Write it to the close folder FY26-Close / March"

**Plugins:** variance-analysis

**Tips:**
- Set the threshold.
- Name the audience.

### 36. Forecast & scenario modeling
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/forecast-scenarios)

> Three scenarios with the assumptions memo.

**Prompt mẫu:**
> "Pull the latest actuals into the driver model, extend it through the next four quarters, and run base, upside, and downside scenarios.
> For each scenario list the assumptions you changed and by how much, then write a one-page memo explaining what drives the difference between them in plain English for the leadership review.
> Planning / FY-f…"

**Context:** NetSuite, Google Drive, Microsoft 365 (bắt buộc)

**Plugins:** financial-statements

**Tips:**
- Start from the source data.
- Name the scenarios.
- Ask it to list its assumptions.

### 37. Organize your business finances
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/organize-your-business-finances)

> Create spreadsheets that bring clarity to your finances. Spot trends, filter what matters, and understand what your numbers are telling you.

**Prompt mẫu:**
> "I need help organizing my freelance invoices from this year. I'm uploading my invoice file. It has the date, client name, what the project was, and how much I invoiced.
> Formatting is inconsistent because I've been adding to it all year. Can you create a cleaner version with a dashboard that shows my total income, breaks it down by month,…"

**Output:** Claude organizes your data and adds spreadsheet features—filters, frozen headers, trend charts, and formatting—that make it functional and easy to use.

### 38. Reconcile and draft the journal entries
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/recon-journal-entries)

> Intercompany breaks sorted, JEs drafted with memo and support.

**Prompt mẫu:**
> "Reconcile the March intercompany balances across both subledgers.
> Normalize FX to USD at the month-end rate fuzzy-match by amount and reference, and sort the differences into timing, rounding, and true breaks.
> For every true break, draft the journal entry with Dr/Cr, memo, and support reference, and write the recon workbook to this folder…"

**Context:** Google Drive (tùy chọn)

**Plugins:** journal-entry

**Tips:**
- Give it your own categories.
- Specify the matching method.
- Name every part of the output.

### 39. Reconcile headcount
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/headcount-reconciliation)

> HRIS, the budget, and the GL agreeing on who's on the books.

**Prompt mẫu:**
> "Reconcile March headcount across the Workday roster, the FY26 plan, and payroll in the GL Match by cost center and employee ID, list every difference (unplanned hires, budgeted heads still open,
> roster entries with no payroll, contractors miscoded as FTE), and write the reconciliation by cost center to the close folder. FY26-Close / Headc…"

**Context:** Google Drive (tùy chọn)

**Plugins:** close-management

**Tips:**
- Say how to match the records.
- List the categories you want.
- Organize output for the reader.

### 40. Reconcile transactions across your accounts
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/reconcile-transactions-across-your-accounts)

> Hand Cowork your bank exports and ledger files. It matches transactions across sources, flags discrepancies, and outputs an annotated reconciliation report.

**Prompt mẫu:**
> "I need to reconcile my January 2024 bank statement. I've uploaded my checking account statement export and my current chart of accounts.
> Can you analyze the transactions, match them to the right accounts, and flag anything that doesn't line up? If there are discrepancies, I'd love journal entries to fix them."

**Output:** Claude analyzes both files, matches transactions to accounts, and surfaces exactly what needs fixing.
The response shows the reconciliation logic, specific discrepancies found, and correctly-formatted journal entries ready for review.

### 41. See budget futures side by side, in chat with Claude
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/see-budget-futures-side-by-side)

> Type your budget split and the thing that might change, and Claude draws three scenarios next to each other with a toggle between dollars and percentages.
> Click any scenario for a one-line read on where the real pressure lands.

**Prompt mẫu:**
> "We might lose our $400K federal grant next year. Current budget is about $2.1M: Roughly 60% programs, 25% ops, 15% fundraising.
> Show me three scenarios side by side: We lose the grant, we stay flat, it grows a bit.
> I want to flip between dollars and percentages, and if I click a scenario give me the one-line version of what it actually me…"

**Output:** Claude draws three stacked bar charts side by side with a toggle at the top that switches between dollar amounts and percentage splits.
The dollar view shows you what gets smaller, while the percentage view shows whether the balance of the organization shifts…

### 42. SOX & controls documentation
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/sox-controls-doc)

> Process narrative, RCM, and flowchart in under an hour.

**Prompt mẫu:**
> "Here's how this process runs.
> Write the process narrative in our standard format build the risk and control matrix mapping each risk to its control, owner, and frequency,
> and draw the flowchart Flag any step where a control looks missing or a segregation of duties issue shows up. Controls / Order-to-Cash"

**Context:** Google Drive, Microsoft 365 (bắt buộc)

**Plugins:** sox-testing

**Tips:**
- Start from the current state.
- Ask for related outputs in one prompt.
- Ask it to flag what's missing.

### 43. Understand and extend an inherited spreadsheet
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/understand-and-extend-an-inherited-spreadsheet)

> Understand existing formulas and structure then add new data while preserving the original logic.

**Prompt mẫu:**
> "Once you understand the structure, Claude extends the model following the original patterns and comments any new formulas it adds. I inherited this SaaS revenue model when Marcus left.
> Finance needs Q1-Q3 2026 projections by Thursday. There's a Legend tab with some basics, and a few cell comments on formulas. Can you read through those, t…"

**Output:** Claude explains the tab structure and hidden logic, adds sparklines to surface trends and comments to explain formulas, then extends the model.
The new spreadsheet matches the original conventions so the file stays coherent.

### 44. Update your financial model after earnings
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/update-your-financial-model-after-earnings)

> Cowork pulls the release and transcript from S&P and checks them against your financial model.
> You take the flags into Claude for Excel to edit the cells, then open the deck in Claude for PowerPoint to build the page.

**Prompt mẫu:**
> "Claude handles the data pull and the cross-referencing; you make the call on what moves. ACME just jumped 8% after hours — what's driving this?
> I need to update my model and build a page for tomorrow's PM meeting. Steps: Pull the earnings release and call transcript from S&P Read my model in the folder and flag where my forecast was off"

**Context:** S&P Global (bắt buộc)

**Output:** A brief you can act on: what moved the stock, where your forecast was off, and the exact cells to look at when you open the workbook.

### 45. Validate reserves and draft filing narrative with Claude for Excel
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/validate-reserves-and-draft-filing-narrative-with-claude-for-excel)

> Cowork reads your reserve workbook from the valuation folder and pulls prior filings and bulletins through your organization's own NAIC connector (a custom MCP server your team hosts).
> You take the formula flags and reserve walk into Claude for Excel to clean the workbook, then bring the narrative into Claude for Word for the filing memo.

**Prompt mẫu:**
> "Claude validates the formulas and flags the anomalies; you sign off on the reserves. Q1 reserve review for Personal Auto BI — appointed actuary review next week, filing due in two.
> Walk me through the workbook before I lock the numbers. Steps: Read the reserve workbook in the valuation folder and validate the formulas Pull the FY24 filing…"

**Output:** A brief you can act on: where the workbook is broken, where the reserves moved, and the exact cells to look at when you open the file.

### 46. Variance to exec slides
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/variance-exec-slides)

> Three board-ready slides built from the variance workbook.

**Prompt mẫu:**
> "Build the three exec slides from the March variance workbook: a headline page with result vs plan,
> a drivers page with top movers above our materiality threshold and the known one-timers called out, and an outlook page with what carries into Q2. Match last quarter's deck layout"

**Context:** NetSuite (tùy chọn)

**Plugins:** financial-statements

**Tips:**
- Name each part of the output.
- Anticipate the audience's first question.
- Point to last quarter's deck as the example.

## Sales (12)

### 47. Account research
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/account-research-brief)

> A one-page brief on what changed and where you fit.

**Prompt mẫu:**
> "Build a one-page account brief on Northwind. Pull from Salesforce, recent news, the 10-K, their exec LinkedIn posts, and our last call notes.
> Cover what they do, what's changed in the last quarter, where we fit, and three openers for the first call Save it to the account folder Accounts / Northwind"

**Context:**
- Salesforce, Google Drive (bắt buộc)
- Apollo (tùy chọn)

**Plugins:** account-research

**Tips:**
- List the sections you want.
- Set a time window.

### 48. Account tracking
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/account-tracking)

> Account health in green/yellow/red with this week's two moves.

**Prompt mẫu:**
> "/pipeline-review and other customer success skills as a starting point, already structured to weigh usage, tickets, and sentiment into one call.
> If your admin manages plugins and it's not available yet, skip this step. The prompt below works without it.
> Sales Skills for account research, call prep, pipeline review, and account health pipe…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 49. Answer deal and account questions from the CRM
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/pull-deal-and-account-state)

> Ask where a deal stands and Claude Tag answers in the thread from the CRM record and from what the team has said in the channel.

**Prompt mẫu:**
> "Ask in the account's channel, each time you have a question about that account or one of its deals. Name the information you want, such as recent activity, open items or where the deal stands."

### 50. Build a battle card library
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-a-battle-card-library)

> Turn sales losses and competitive data into ready-to-use battlecards with winning talk tracks, objection handlers, and differentiation strategies your team can use during actual calls.

**Prompt mẫu:**
> "Pull the closed-lost deals in our CRM from the last 6 months where DataGuard, BackupPro, or SecureVault appear in the competitor field.
> Read the deal notes for each competitor and tell me what patterns you see for each one. Search the web for their websites, G2 reviews, and recent positioning to find additional information.
> Then, build a…"

**Context:**
- Salesforce, HubSpot (bắt buộc)
- Web Search

**Output:** Claude produces a comprehensive battlecard structured for quick reference during sales calls, including competitive positioning, differentiation strategies, objection handling scripts,
and proven talk tracks that help sales teams win more competitive deals.

### 51. Call prep
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/call-prep-sheet)

> Where the deal is and what to ask on this call.

**Prompt mẫu:**
> "I'm meeting Northwind tomorrow.
> From the Salesforce record, the last three Gong transcripts the mutual action plan, write the prep sheet: where the deal is, what they care about,
> the two or three asks I should make on this call the likely objections with our response Accounts / Northwind / calls"

**Context:**
- Salesforce, Google Drive (bắt buộc)
- Apollo (tùy chọn)

**Plugins:** call-prep

**Tips:**
- Ask for what to do on the call.
- Pair objections with responses.

### 52. Create a sales proposal presentation
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-sales-proposal-presentation)

> Create a polished client proposal deck with professional layouts data visualizations and cohesive design—then refine through feedback until it matches your standards.

**Prompt mẫu:**
> "I'm putting together a proposal deck for Midwest Regional Health, a healthcare network we've been in conversations with about our patient engagement platform.
> Search my Google Drive for documents with "Midwest Regional" in the title—there should be discovery call notes, their RFP, and a competitive analysis we did. Also pull our standard…"

**Context:** Google Drive (bắt buộc)

**Output:** Claude searches your connected files, synthesizes the relevant information, and delivers a complete proposal deck with professional layouts and consistent design,
ready for refinement based on your feedback.

### 53. Create sales reports
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-sales-reports)

> Pull metrics from your CRM, analyze trends, and generate polished reports with data visualizations and strategic insights—all without manual data formatting.

**Prompt mẫu:**
> "I need a Q4 sales report for our exec team meeting next week. Pull October through December from our CRM.
> Show me: Total revenue vs Q3—how much did we grow, and was it from more deals or bigger deals? Break it down by segment: Enterprise, Mid-Market, and SMB.
> For each one, show revenue, number of deals, and win rate How long are sales cyc…"

**Context:** Salesforce, HubSpot (bắt buộc)

**Output:** Claude analyzes your sales performance data to create a document with an executive summary, data tables showing key metrics with visual indicators, segment-by-segment breakdowns,
trend analysis, and actionable recommendations.

### 54. Log sales calls to your CRM
*10′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/log-sales-calls-to-your-crm)

> Claude in Chrome can read your calendar, match attendees to Salesforce contacts, and draft activity logs for each call. You add notes and approve before anything gets created.

**Prompt mẫu:**
> "Log my calls from today in Salesforce.
> Steps: Go to my Google Calendar and find today's external meetings (skip internal) For each meeting,
> look up the attendees in Salesforce Create an activity log for each call—I'll provide a quick summary of what was discussed"

**Output:** Claude shows what it found on your calendar, matches attendees to Salesforce contacts, and drafts activity logs for your review.

### 55. Pipeline reviews
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/pipeline-review)

> At-risk deals flagged, with the why.

**Prompt mẫu:**
> "/pipeline-review and other forecast-hygiene skills as a starting point, already structured to score opps and call out risk. If your admin manages plugins and it's not available yet, skip this step.
> The prompt below works without it. Sales Prospect, craft outreach, and build deal strategy faster. Prep for calls, manage your pipeline, and w…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 56. Prepare for sales deals
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/prepare-for-sales-deals)

> Pull relevant CRM data, like details on comparable opportunities, to prepare for upcoming sales conversations.

**Prompt mẫu:**
> "I'm working on a healthcare deal - mid-market, around 180 employees, about $60K.
> They're interested in our patient engagement platform but worried about integration into their current system and how long implementation takes.
> Can you pull similar healthcare deals we've closed in the last year or two? I want to see what these typically loo…"

**Context:** Salesforce, HubSpot (bắt buộc)

**Output:** Claude searches your CRM for comparable deals, identifies patterns in wins vs. losses,
and creates a deal preparation artifact with the key insights and data points that help you go into the conversation prepared.

### 57. Renewal risk audit
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/renewal-risk-audit)

> Every account renewing this quarter, scored on usage, sentiment, and open commitments.

**Prompt mẫu:**
> "/pipeline-review and other account-health skills as a starting point, already structured to score a book of business and flag what's at risk.
> If your admin manages plugins and it's not available yet, skip this step. The prompt below works without it. Sales Prospect, craft outreach, and build deal strategy faster.
> Prep for calls, manage yo…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 58. Transcript theme extractor
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/transcript-themes)

> The themes across your calls, counted and quoted.

**Prompt mẫu:**
> "Read every transcript in this folder and cluster what customers are saying into themes. For each theme give me the count, the best one-line quote, and which accounts said it.
> Write the one-page themes brief to the folder for product and marketing Calls / 2026-Q1"

**Context:** Google Drive (bắt buộc)

**Plugins:** call-summary

**Tips:**
- Ask for the evidence behind each finding.
- Name the audience.
- Set a length limit.

## Marketing (12)

### 59. Adapt content across platforms
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/adapt-content-across-platforms)

> Transform one piece of content into multiple formats adapted for different platforms and audiences.

**Prompt mẫu:**
> "Repurpose this blog post about AI-powered marketing analytics into multi-channel content: LinkedIn carousel Twitter thread Email nurture sequence (5 emails) Podcast talking points"

**Context:** Google Drive (bắt buộc)

**Output:** Claude generates individual content files tailored for each platform, ready for your review and edits.
Additionally, it provides a single artifact that showcases all deliverables in one place.

### 60. Analyze campaign performance
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/analyze-campaign-performance)

> Analyze campaign performance data to identify your best and worst performing channels, then get specific budget reallocation recommendations for next quarter.

**Prompt mẫu:**
> "I'm running three campaigns targeting different customer segments. I have Q3 data showing impressions, clicks, conversions, and spend across social, search, and email.
> Analyze performance and tell me: Which campaigns and channels are working Where to reallocate budget for Q4 What patterns I'm missing across segments"

**Output:** Claude analyzes your marketing data and turns it into a strategic review that tells you where and how you can improve.

### 61. Analyze fundraising performance
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/analyze-fundraising-performance)

> Analyze performance across email, events, direct mail, social media, and other channels to identify highest-return investments and optimize resource allocation for maximum fundraising impact.

**Prompt mẫu:**
> "I run development for a regional nonprofit with 25-30 annual fundraising events plus ongoing email, direct mail, social media, and corporate sponsorship programs.
> I need to analyze which channels drive the best ROI to inform next year's $500K+ budget decisions. I'm uploading our fundraising data from the past two years, broken down by cha…"

**Output:** Claude produces a comprehensive Excel workbook with multiple interconnected sheets featuring sophisticated visual design and advanced analytical features.

### 62. Audit a folder of visual assets against your guidelines
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/audit-a-folder-of-visual-assets-against-your-guidelines)

> In Claude Cowork, Claude Opus 5 can read a large folder of image exports at high resolution to spot off-brand colors, outdated logos, and missing legal copy.
> Point Claude at your assets folder and your brand guidelines, and get back a categorized list of violations with a confidence rating on each one.

**Prompt mẫu:**
> "Here, a folder of live marketing assets gets checked against a brand-guidelines PDF and a legal-compliance sheet.
> Audit every PNG and JPG in this folder against brand-meridian-2025-q2.pdf and legal-required-copy.txt"

**Output:** Claude reads the guide and the legal sheet, then checks every asset in the folder against them.
You get a grouped violation list (filename, issue, guideline vs asset value, confidence per item), a compliant count, and a short "less certain" block for the items…

### 63. Build a campaign brief
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/campaign-brief)

> A formatted campaign brief from rough notes.

**Prompt mẫu:**
> "Turn the strategy notes into a formatted campaign brief: objective, audience, key message, channel plan, timeline, and success metrics.
> Then build a short deck from the brief to walk the team through at kickoff. Keep the voice consistent with our brand guidelines Campaigns / Spring-Launch"

**Context:** Google Drive, Notion (bắt buộc)

**Plugins:** campaign-plan

**Tips:**
- Name the sections.
- Ask for both deliverables at once.

### 64. Build customer personas
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-customer-personas)

> Create personas with demographics, goals, and pain points synthesized from your research data.

**Prompt mẫu:**
> "I've uploaded customer feedback from different sources—could be sales call notes, support conversations, survey responses, whatever we've collected.
> Figure out what types of customers we have based on their actual behavior and problems. Create an interactive artifact where I can explore each persona and see their journey. Show their goals…"

**Context:** HubSpot, Intercom (bắt buộc)

**Output:** Claude analyzes your customer data across Intercom conversations, HubSpot deal notes, interview transcripts,
and survey responses and finds behavioral segments that explain the mixed feature adoption. Claude then creates an interactive artifact where you can e…

### 65. Build the competitive comparison doc
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/competitor-comparison)

> Cowork reads competitor materials against your positioning, writes the win/lose/draw, and outputs a sales deck and Excel matrix.

**Prompt mẫu:**
> "Here's the competitor's site, pricing page, and recent announcements, plus our positioning doc. Build a structured comparison: where we win, where they win, and where it's a draw.
> Output a PowerPoint deck for sales and an Excel workbook with the feature-by-feature matrix. Competitive / Acme"

**Context:** HubSpot (tùy chọn)

**Plugins:** competitive-brief

**Tips:**
- Ask for a verdict, not a list.
- Name both output formats.

### 66. Create brand assets
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-brand-assets)

> Generate professional business cards, flyers, and marketing materials that match your exact branding guidelines—ready to print or edit.

**Prompt mẫu:**
> "I need two things for my coffee shop, Morning Ritual: Business card (3.5" × 2") with: My contact info: 125 Hudson Street, New York, NY 10013,
> morningritualnyc.com QR code to my website (make this with rounded corners instead of blocky squares—more organic and unqiue) Print specs: 32pt cardstock, soft-touch coating,
> with bleeds and crop ma…"

**Output:** Claude generates files that match your branding guidelines—ready to send to the printer or edit yourself.

### 67. Create on-brand content
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/on-brand-content)

> Blog, landing page, email, and ad copy in your voice.

**Prompt mẫu:**
> "Draft the content set for this campaign: a blog post, landing page copy, a three-email sequence, and ad copy in three lengths.
> Hold our voice and the approved messaging exactly, and note anywhere the brief was thin so I know what to fill. Content / Spring-Launch"

**Context:** HubSpot, Google Drive, Notion (bắt buộc)

**Plugins:** draft-content

**Tips:**
- Ask for every piece in one prompt.
- Tell it the guidelines are non-negotiable.
- Ask it to flag what's missing.

### 68. Package your brand guidelines in a skill
*20′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/package-your-brand-guidelines-in-a-skill)

> Package your brand guidelines into a skill to create presentations, spreadsheets, or documents that automatically match your preferred style.

**Prompt mẫu:**
> "Creating this skill takes minutes. To start, walk through your brand fonts, colors, and other stylistic choices.
> Ask Claude to structure the information into a reusable skill that activates whenever you need brand-consistent outputs.
> I want to create a skill that applies our company's brand styling to any presentation, document, or spread…"

**Context:** Google Drive (bắt buộc)

**Output:** Claude produces a complete, working skill package with clear instructions for when the skill applies, brand color specifications with hex values, typography guidelines with fallback fonts,
and implementation details. The skill activates automatically when you…

### 69. Recap your ad performance
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/ad-performance-recap)

> A performance summary, recommendation on what to improve, and a deck shared in Slack.

**Prompt mẫu:**
> "Analyze this campaign's ad performance and build the recap deck: what worked, what didn't, and what we change next time.
> Post a digest to the team Slack with the top three movers, and create a shared artifact I can refresh from the underlying data. Campaigns / Spring-Launch / performance"

**Context:**
- Slack, Google Drive (bắt buộc)
- BigQuery (tùy chọn)

**Plugins:** performance-report

**Tips:**
- Ask for what to do next, with the data behind it.
- Set a length limit.
- Ask for an output you can refresh.

### 70. Repurpose content across channels
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/repurpose-content)

> A blog post, a LinkedIn thread, and short social posts from one webinar, each in your voice.

**Prompt mẫu:**
> "Draft a blog post, a LinkedIn thread, and three short social posts from this webinar.
> Match the voice of our recent HubSpot posts, and lead each piece with the strongest point from the talk rather than a recap of the agenda. Webinars / apr-platform-overview"

**Context:** Google Drive, Notion (tùy chọn)

**Tips:** Name each output format.

## Operations — Vận hành (11)

### 71. Answer requests in the IT help channel
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/answer-requests-in-the-it-help-channel)

> Give Claude Tag a standing responsibility in the IT help channel: it answers each request first from your policies, asks for missing details,
> and files one ticket for the owner when a request needs them.

**Prompt mẫu:**
> "Send this once in your IT help channel. From then on, Claude answers each new request in its thread, asks for anything missing and passes what it cannot resolve to the owner.
> If the channel's history does not show who the owner is or where the policies are kept, add both to your message."

### 72. Create a volunteer management system
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-volunteer-management-system)

> Create comprehensive volunteer documentation including role descriptions, onboarding processes, communication templates,
> and tracking tools that professionalize volunteer management and scale your program effectively.

**Prompt mẫu:**
> "I need a complete volunteer program infrastructure that includes: Role descriptions for: Reading Tutors (work one-on-one with students weekly) Reading Tutors (work one-on-one with students weekly)
> Reading Buddies (lead small group reading circles)"

**Output:** Claude creates a complete volunteer program infrastructure with 4 core deliverables.

### 73. Create meeting notes and tasks from a call transcript
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/meeting-notes-and-filed-tasks-from-a-call-transcript)

> With proactive replies on in the project channel, Claude Tag reads each transcript the call recorder posts, replies with the decisions and action items,
> files the tickets and publishes the notes as a page.

**Prompt mẫu:**
> "Send this once in your project channel. From then on, each time the recorder posts a transcript, Claude reads it and replies in that post's thread.
> Ask Claude to file tickets only if its tracker connection in this channel can create them, and name the board if there is more than one."

### 74. Meeting prep and a weekly recap in your DM with Claude
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/meeting-prep-and-a-weekly-recap-in-your-dm-with-claude)

> In a direct message, set up a routine and Claude Tag posts a prep note before each of your meetings from your own calendar, email and documents, and drafts a Friday recap you can forward.

**Prompt mẫu:**
> "Send this once in your DM with Claude.
> Each morning, Claude posts a prep note in the DM for each meeting on your calendar that day, built from the event, your email and Slack threads with the attendees, and your documents.
> Ask for whatever you want to know before a meeting."

### 75. Post weekly status updates from the team's channels and tracker
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/weekly-status-posts-from-the-teams-channels-and-tracker)

> Set up a routine in the team's channel and Claude Tag posts the weekly status every Friday from the channel's threads and the connected tracker, for the team to correct and the lead to forward.

**Prompt mẫu:**
> "Send this once in your team's channel. Every week after that, Claude posts a digest built from the channel's threads and the tickets and pull requests linked in them.
> Set the day, time zone and sections your team wants. You can add more sources later with another message, such as another channel or…"

### 76. Prep the vendor negotiation
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/vendor-negotiation)

> Talking points, leverage, and a redline summary from the contract.

**Prompt mẫu:**
> "Compare the current agreement to the renewal proposal and summarize every material change as a redline table (clause, current, proposed, our position).
> Then write the negotiation brief: our leverage, their likely pushback three asks ranked by value, and the walk-away line. Keep it to one page I can take into the call. Procurement / Northw…"

**Context:** Slack (tùy chọn)

**Plugins:** vendor-review

**Tips:**
- Name the columns you want.
- Ask for a ranked shortlist.
- Ask for the decision point.

### 77. Process batches of vendors with Cowork
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/process-batches-of-vendors-with-cowork)

> Onboard several vendors in one session — with Cowork, Claude can read a folder of vendor files, adds each to your tracker, generates their contracts,
> and fills multiple intake forms in your browser.

**Prompt mẫu:**
> "I need to onboard several vendors. Their documents spread across my desktop.
> For each new vendor: Create an NDAs and MSAs from the templates Fill out an onboarding form Afterwards, add all information to the vendor tracker spreadsheet"

**Output:** Claude works through each step, moving between your local files and your browser to complete the full onboarding.
Using the Claude in Chrome connector, Claude opens your procurement portal in a new browser tab and fills out intake forms directly, while reading…

### 78. Support incident postmortem
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/support-incident-postmortem)

> The customer-facing postmortem, drafted from the war room before anyone forgets.

**Prompt mẫu:**
> "Draft the customer-facing incident review for INC-4417. Pull the war-room thread, tickets from the impact window, deploys from the prior 24 hours, and direct customer quotes.
> Reconstruct the timeline, quantify how many customers were impacted and for how long, and write the first cut in our template with recommended remediation owners. Su…"

**Context:** GitHub (tùy chọn)

**Plugins:** runbook, status-report, incident-review

**Tips:**
- Name the audience up front.
- Quantify the impact.
- Ask for direct quotes.

### 79. Triage escalations automatically and alert a person only for a P1
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/watch-the-escalations-channel-and-page-only-for-p1)

> Set up Claude Tag to triage escalations in your channel. It can set a severity, match it to earlier tickets, route it, draft a first response, and alert a person only for a P1.

**Prompt mẫu:**
> "Send this once in your escalations channel. From then on, Claude sets a severity and an owner on each new escalation, in its thread, whether or not anyone tags it.
> Say that only a P1 should mention a person, and add your severity levels, owners and P1 contact if the channel's history does not alread…"

### 80. Vendor risk review
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/vendor-risk-review)

> Go/no-go on the vendor with required mitigations.

**Prompt mẫu:**
> "Score this vendor's SOC 2, security questionnaire, DPA, and MSA against our risk framework.
> Write the review memo with a clear go or no-go and the required mitigations with owners Cite the source document and section for every finding. Vendors / Northwind / risk-review"

**Context:**
- Google Drive, Microsoft 365, Box (bắt buộc)
- Ironclad (tùy chọn)

**Plugins:** risk-assessment

**Tips:**
- Ask for a go or no-go recommendation.
- Citations make it auditable.

### 81. Workflow improvement planner
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/workflow-improvement-planner)

> Turn process pain points into structured improvement plans. Claude helps nonprofits define workflow challenges and design AI-powered solutions that save time and increase capacity.

**Prompt mẫu:**
> "The artifact should help me think through: What the current workflow looks like Where the pain points and bottlenecks are What inputs and outputs are involved What success would look like"

**Output:** Claude produces an artifact with fill-in-the-blank sections covering various aspects of workflow improvement planning.
The template includes clear instructions for completion and detailed guidance on how to use your finished document with Claude to design solu…

## Product (7)

### 82. Analyze patterns in user feedback
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/analyze-patterns-in-user-feedback)

> Find recurring themes and pain points across user feedback to separate meaningful patterns from noise.

**Prompt mẫu:**
> "Pull all Intercom conversations from the past 90 days. I'm also uploading our Q2 NPS survey responses (CSV) and notes from six user interviews we did last month (PDFs).
> Read everything and tell me what patterns you're seeing: What issues keep showing up across different feedback sources? When people ask for different things, are they actu…"

**Context:** Intercom (bắt buộc)

**Output:** Claude connects dots between your feedback sources and organizes everything into data workbooks that make qualitative feedback actionable.

### 83. Competitive teardown and positioning gaps
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/competitive-teardown)

> Where you win, where you're exposed, what they shipped.

**Prompt mẫu:**
> "Build a competitive teardown of Acme and Northwind against us. Browse their product, docs, changelog, pricing page, and recent reviews, and produce a feature and positioning matrix.
> Call out where we clearly win, where we're exposed, and everything they shipped last quarter that we haven't answered Product / competitive / q2"

**Context:**
- Figma, Linear, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** competitive-brief

**Tips:**
- Name the competitors, not the category.
- Ask what still needs a response.

### 84. Feedback synthesis to prioritized themes
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/feedback-synthesis)

> The five themes that matter, quantified and quoted.

**Prompt mẫu:**
> "Read this folder plus the #product-feedback Slack channel and the open Zendesk tickets tagged feedback.
> Cluster everything into 5 to 7 themes count how often each shows up and how severe it is pull the best verbatim for each flag which map to a Linear roadmap item versus net-new,
> and write a one-page Voice of Customer brief for roadmap re…"

**Context:**
- Slack, Linear, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** synthesize-research

**Tips:**
- Give a number range.
- Ask for frequency and severity.
- Ask for the single best example.

### 85. Launch readiness sweep
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/launch-readiness)

> Red/yellow/green with the blockers named.

**Prompt mẫu:**
> "Sweep launch readiness for the saved-views launch.
> Produce the launch checklist with status and owner per item, give a red/yellow/green readiness call overall, name the blockers,
> and note anything that matches what went well or wrong in our last two launches Launches / saved-views"

**Context:**
- Linear, Slack, Google Drive, Optional (bắt buộc)
- Notion (tùy chọn)

**Plugins:** stakeholder-update

**Tips:**
- Ask for an owner on every line.
- Ask for a verdict with reasons.

### 86. Metrics deep-dive to narrative
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/metrics-narrative)

> What moved, why, and which ship caused it.

**Prompt mẫu:**
> "Find the anomaly in this week's activation funnel.
> Segment by plan, platform, and signup source until you've isolated the driver, check it against what shipped in the same window,
> and write the "what happened and why" narrative with the two charts that prove it Product / metrics / wk17"

**Context:** Amplitude, Linear (bắt buộc)

**Plugins:** metrics-review

**Tips:**
- Ask for the evidence behind each claim.
- Name the segments to try.
- Set a chart limit.

### 87. PRD from a problem statement
*6′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/prd-from-a-one-pager)

> A structured PRD with the open questions flagged.

**Prompt mẫu:**
> "Write a PRD for the saved-views problem. Interview me first about the problem, who hits it, the constraints, and how we'd measure success.
> Then draft it in prd-template.docx call out the goals and non-goals match the depth of PRD-bulk-export.docx, and flag every open question for design review Product / prds"

**Context:**
- Linear, Notion, Optional (bắt buộc)
- Google Drive (tùy chọn)

**Plugins:** write-spec

**Tips:**
- Ask to be interviewed.
- List what's in and out of scope.
- Give open questions a named owner.

### 88. Pull metrics from analytics dashboards
*10′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/pull-metrics-from-analytics-dashboards)

> Claude in Chrome can navigate your analytics dashboards, extract the numbers you need, and compile them into a summary. No exports, no tab-switching, no manual copying.

**Prompt mẫu:**
> "Pull my weekly metrics from both my Amplitude and Mixpanel open tabs.
> From Amplitude: Weekly active users (WAU) — past 4 weeks New user signups — this week vs. last week Retention (Day 1, Day 7, Day 30) — for the cohort from 30 days ago"

**Output:** Claude compiles metrics from both tools into a single summary.

## Design (7)

### 89. Clickable prototype from real components
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/clickable-prototype)

> A clickable HTML prototype built from your real library.

**Prompt mẫu:**
> "Build a clickable HTML prototype of the flow in this folder using only components from our design system library Wire up the navigation use realistic placeholder data,
> and write it to prototype/index.html so I can click through in a browser. Prototypes / Invite-Flow"

**Context:** Google Drive (tùy chọn)

**Plugins:** design-handoff

**Tips:**
- Limit it to your own materials.
- Describe what each interaction should do.
- Ask for realistic sample content.

### 90. Competitive teardown and heuristic audit
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/design-heuristic-audit)

> Heuristic-scored teardown of competitor flows with evidence.

**Prompt mẫu:**
> "Run a heuristic audit of these competitors.
> Score each screen against Nielsen's ten heuristics plus our three custom ones, note where each competitor is stronger or weaker than us,
> and end with the three patterns worth stealing and the three to avoid Competitive / Teardown-Q2"

**Context:** Google Drive (tùy chọn)

**Plugins:** design-critique

**Tips:**
- Score against a named rubric.
- Compare against your own baseline.
- Ask for a clear recommendation.

### 91. Design spec from scattered threads
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/design-spec-from-threads)

> One review-ready spec from threads, notes, and screenshots.

**Prompt mẫu:**
> "Assemble everything in this folder into a single design spec.
> Structure it as problem, goals, constraints, proposed solution, open questions,
> and out of scope Quote the source for any decision already made and flag anything contradictory Design / Checkout-Redesign"

**Context:** Figma (tùy chọn)

**Plugins:** design-handoff

**Tips:**
- Name the section order.
- Ask it to cite its sources.
- Flag contradictions explicitly.

### 92. Design system drift review
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/design-police)

> Shipped screens and PRs flagged for design-system drift.

**Prompt mẫu:**
> "Review the shipped screens and open PRs in this folder against our design system.
> For each one, list every place it drifts from our tokens, components, spacing, or interaction patterns rate the severity, and suggest the system-compliant fix.
> Skip anything that already matches Design-QA / Sprint-42"

**Context:** Slack (tùy chọn)

**Plugins:** design-system

**Tips:**
- Spell out what to check for.
- Ask for a severity on each finding.
- Say what to leave out.

### 93. Encode the brand as a skill
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/brand-guidelines-skill)

> Every Claude output across the org stays on-brand.

**Prompt mẫu:**
> "Turn the brand docs in this folder into a shared skill called /on-brand.
> The skill should enforce our color tokens, typography, spacing, and voice rules on any content or UI it generates, and refuse off-brand patterns with a short reason Brand / System-Source"

**Context:** GitHub (tùy chọn)

**Plugins:** ux-copy, design-system, on-brand

**Tips:**
- Name the output.
- List what it covers.
- Define the failure case.

### 94. Pattern consistency audit
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/pattern-consistency-audit)

> Every existing surface that already solves this, before you design a new one.

**Prompt mẫu:**
> "Before I propose a new inline-filter pattern for the search results page, find every surface in our product using something similar (chips, segmented controls, dropdown filters, faceted sidebars).
> For each, show a screenshot or Figma link, note which team owns it and how it performed (engagement or conversion if we have it). Tell me which…"

**Context:** Amplitude (tùy chọn)

**Plugins:** design-handoff

**Tips:**
- Name the variants to search for.
- Ask for the owner.
- Back the recommendation with data.

### 95. Synthesize user interviews into findings
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/uxr-synthesis)

> Themed findings and quotes from raw transcripts.

**Prompt mẫu:**
> "Synthesize the interview transcripts into a research findings doc.
> Cluster the observations into 5-7 themes, name each plainly, support each with 2-3 verbatim quotes attributed to participant ID,
> and end with the open questions the team still needs to answer Research / Onboarding-Study-Q2"

**Context:** Miro (tùy chọn)

**Plugins:** research-synthesis

**Tips:**
- Give a number range.
- Ask for attributed evidence.
- End on open questions.

## Engineering (9)

### 96. Build an 'Ask the Company' agent
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/ask-the-company)

> Plain-English answers over your wiki, code, and warehouse.

**Prompt mẫu:**
> "Build an internal "ask anything" agent for engineers.
> When someone asks "how do I get a staging API key," "what owns the orders table," or "why did deploys slow down last month," find the answer across our systems cite the source,
> and tell them who to ask if you're not sure. Get one good answer first, then turn it into a shared skill. Pla…"

**Context:** Snowflake (tùy chọn)

**Plugins:** documentation

**Tips:**
- Give an example for each question type.
- Cite the source, every time.
- Name an owner when unsure.

### 97. Draft the incident postmortem
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/incident-postmortem)

> Timeline, root cause, and action items from the incident channel.

**Prompt mẫu:**
> "From #inc-2026-04-22-checkout-5xx, reconstruct the sequence of events with timestamps, write the customer impact summary, identify the root cause and contributing factors,
> and draft the postmortem in our template with owners on every action item. Be blameless: describe what the system did, not who made a mistake. Incidents / 2026-04-22-ch…"

**Context:** Datadog (tùy chọn)

**Plugins:** incident-response

**Tips:**
- Reconstruct, don't summarize.
- Separate root cause from contributing factors.
- State the tone you want.

### 98. Draft your reports' performance reviews
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/eng-performance-reviews)

> A grounded review draft with linked evidence, per report.

**Prompt mẫu:**
> "I'm writing quarterly reviews for my reports.
> For each engineer in my team list, draft the review in our framework with evidence linked for every claim,
> drawing on their work this quarter and their last review's growth areas Flag where I need to add my own judgment; do not write the rating Reviews / 2026-Q1"

**Context:** Linear (tùy chọn)

**Plugins:** performance-review

**Tips:**
- Require evidence for every claim.
- Include prior context to show progress.
- Keep judgment calls yours.

### 99. Find the cloud cost anomaly
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/cloud-cost-anomalies)

> Where the bill jumped, why, and who owns the fix.

**Prompt mẫu:**
> "Compare this month's AWS costs to the trailing three-month average by service and tag:team.
> Flag any line more than 20% over trend trace each to the workload or change behind it, and write the cost-anomaly report with an owner and recommended action for every item.
> Put a one-line summary for the infra channel at the top. Infra / cloud-cos…"

**Context:** GitHub (tùy chọn)

**Plugins:** debug

**Tips:**
- Set the comparison baseline.
- Set the threshold.
- Ask for what caused each anomaly.

### 100. Fix a reported bug with a draft PR
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/fix-a-reported-bug-with-a-draft-pr)

> Hand a bug report to Claude Tag in its thread. It reproduces the bug, fixes it and opens a draft pull request for an engineer to review.

**Prompt mẫu:**
> "When a bug report comes in, reply in its thread and ask Claude to reproduce and fix it. Tell it which repository, and when to stop, such as once a draft PR is open and CI passes."

### 101. On-call handoff brief
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/oncall-handoff-brief)

> Everything that happened on your shift, written before you log off.

**Prompt mẫu:**
> "Write the on-call handoff for my shift. Cover pages and incident channels from the last 7 days, CS escalations from #support-escalations, and production deploys.
> For each, note status (resolved, monitoring, still open), the one-line cause if known, and what the next on-call should watch Write it to the on-call folder and post it to #oncal…"

**Context:** GitHub (tùy chọn)

**Plugins:** standup

**Tips:**
- Name every source you need.
- Specify the fields for each item.
- Say where the output should go.

### 102. Triage on-call alerts and diagnose incidents
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/triage-on-call-alerts-and-diagnose-incidents)

> With proactive replies on in the on-call channel, Claude Tag investigates each paging alert and posts what broke, why and a proposed fix, and the rollback waits for the on-call engineer's yes.

**Prompt mẫu:**
> "Send this once, as a new message in your on-call channel. Claude saves it for the channel and investigates each paging alert that tags it after that.
> In your own message, say who to mention when something breaks and that Claude waits for a person's approval before a rollback, and link your runbook a…"

### 103. Write the design doc or RFC
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/design-doc)

> A structured proposal with prior art and trade-offs filled in.

**Prompt mẫu:**
> "Write a design doc for moving our event pipeline from batch to streaming.
> Look up prior art and architecture constraints, then draft the proposal in our RFC template: problem, goals and non-goals, two or three approaches with trade-offs, the recommendation,
> and open questions. I'll fill in the parts only I know RFCs / 0087-streaming-event…"

**Context:** Notion (tùy chọn)

**Plugins:** system-design

**Tips:**
- Ask for prior art explicitly.
- Force two or three approaches.
- Say which parts you'll fill in.

### 104. Write the sprint retro and on-call handoff
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/sprint-retro-handoff)

> What shipped, what slipped, and what the next on-call needs to know.

**Prompt mẫu:**
> "Read the just-closed Linear cycle and two weeks of #team-platform and #oncall-platform.
> Write the sprint retro (shipped, slipped with reasons, themes worth discussing) and a separate on-call handoff (open alerts, toil, what the next rotation should watch). Pull quotes where they help.
> Keep each section to what's discussable in a 30-minute…"

**Context:** PagerDuty (tùy chọn)

**Plugins:** tech-debt, standup

**Tips:**
- Ask for the reason behind each item.
- Split outputs that serve different purposes.
- Set a length limit.

## Data (1)

### 105. Answer the ad-hoc data question
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/answer-the-adhoc)

> The query, the chart, and the plain-English answer.

**Prompt mẫu:**
> "Here's the question from the business: " Why is gross margin down in EMEA this quarter?" Write the SQL to answer it, run it against the warehouse, and tell me what's driving the move.
> Then give me the chart spec to add to the dashboard so nobody has to ask again Analytics / EMEA-margin-question"

**Context:** Snowflake (tùy chọn)

**Plugins:** write-query

**Tips:**
- Paste the question verbatim.
- Ask for what's driving the number.
- Ask for a reusable output.

## Legal — Pháp lý (10)

### 106. Contract redlining
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/contract-playbook-review)

> Clause-by-clause G/Y/R with redlines you can send back.

**Prompt mẫu:**
> "Review this MSA clause by clause against our contract playbook.
> For each clause, mark it green, yellow, or red against our standard, explain why in one or two sentences,
> and where it's yellow or red draft the redline and the rationale for opposing counsel Contracts / Acme-MSA"

**Plugins:** review, cold-start-interview

**Tips:**
- Compare against your own baseline.
- Ask for the fix and the reasoning.
- Save the detail for the problems.

### 107. Contract redlining and negotiation
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/contract-redlining-and-negotiation)

> Analyze agreements to spot terms affecting your work, with suggested redlines and negotiation points.

**Prompt mẫu:**
> "I'm reviewing a vendor services agreement for our marketing automation platform. We're a Series B startup with limited budget flexibility.
> Create a redlined version that protects us from getting locked into something we can't get out of, ensures we keep ownership of our data and any work we pay for,
> and gives us flexibility to adjust or l…"

**Context:** Google Drive (bắt buộc)

**Output:** Claude creates a redlined contract with tracked changes and margin comments explaining each edit—like having your legal team mark up the document with both what to change and why it
matters.

### 108. Legal research
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/legal-research-memo)

> A structured memo with citations, not a list of links.

**Prompt mẫu:**
> "Research this question.
> Surface the relevant case law and regulatory guidance via Thomson Reuters and draft a research memo: question presented, short answer, the discussion grouped by authority,
> and a list of open issues Cite every proposition to the source you relied on Research / Acme-Indemnification-Q"

**Plugins:** brief-section-drafter, research-memo, cold-start-interview

**Tips:**
- Name the source.
- Dictate the structure.
- Require a citation for every proposition.

### 109. M&A diligence
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/data-room-diligence)

> Material issues flagged and the diligence summary drafted, every line cited to the source document.

**Prompt mẫu:**
> "Read every document in the connected data room Categorize each by type, then for the material contracts extract counterparty, term, change-of-control, assignment, and consent provisions.
> Flag the material issues and draft the diligence summary with a citation back to the source document and section for every entry Deals / Project-Silvern"

**Plugins:** diligence-issue-extraction, tabular-review, cold-start-interview

**Tips:**
- Categorize first, then extract.
- Name the provisions that matter.
- Require a citation for every entry.

### 110. NDA triage at scale
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/nda-review)

> Standard NDAs routed for signature; only exceptions hit counsel.

**Prompt mẫu:**
> "Triage this NDA against our NDA playbook. For each criterion in the playbook, mark whether this paper meets our standard. If everything passes, mark it cleared and route for signature.
> If anything is off-standard, list only the exceptions with a one-line reason each so counsel reviews just those. NDAs / Intake"

**Context:**
- Google Drive, Microsoft 365, Optional (bắt buộc)
- DocuSign (tùy chọn)

**Plugins:** review, cold-start-interview, review

**Tips:**
- Check against your playbook.
- Define the two outcomes.
- Set a length limit.

### 111. Organize your legal workflows using Projects
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/organize-your-legal-workflows-using-projects)

> Stop explaining your review standards for every contract. Claude Projects let you upload your playbooks once and reference them automatically across hundreds of reviews.

**Prompt mẫu:**
> "I've uploaded our NDA playbook, our standard mutual NDA template, and our list of unacceptable terms.
> Analyze these documents and create an NDA Review Standards Guide that captures our voice, tone, and structure we use throughout our writing.
> Make this a professional reference document I can upload to the Project knowledge, so Claude can…"

**Output:** Claude analyzes your reference materials, identifies patterns in your review approach, and produces two files:
a standards guide for your Project knowledge and ready-to-paste custom instructions.

### 112. Outside counsel management
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/outside-counsel-review)

> Off-pattern entries and budget drift surfaced before the partner call.

**Prompt mẫu:**
> "Pull the billing and matter data for this firm from the connected matter system.
> Flag entries that are off-pattern against our billing guidelines, list every matter drifting against its budget with the variance and driver,
> and draft the talking points for the relationship-partner conversation. Legal-Ops / OC-Review-Q2"

**Tips:**
- Check against your guidelines, not a generic rule.
- Ask for the variance and the driver.
- End with the deliverable.

### 113. Prep scattered documents for a compliance audit
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/prep-scattered-documents-for-a-compliance-audit)

> Turn a folder of scattered policy documents, contracts, and records into an organized, clearly named collection ready for regulatory review.

**Prompt mẫu:**
> "I have 100+ documents for our upcoming SOC 2 audit in this folder. Right now they're scattered with names like "policy_v2_final.docx" and "scan0042.pdf".
> I need to organize them before the auditors arrive: Rename files with clear titles showing document type, effective date, and which control area they cover Group by control category (Acc…"

**Output:** Cowork reviews the entire document folder, produces a rename mapping organized by control area, identifies coverage, and flags potential gaps.

### 114. Regulatory and compliance
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/regulatory-analysis)

> What changed, what applies to you, what to do by when.

**Prompt mẫu:**
> "Read this regulation against our product descriptions and current policies.
> Draft the compliance brief: what changed from the prior rule, which provisions apply to us and why, and for each what we need to do and by when.
> Save it to the folder for product and compliance leads. Regulatory / EU-AI-Act"

**Context:** Google Drive, Microsoft 365 (bắt buộc)

**Plugins:** policy-diff, cold-start-interview, policy-diff

**Tips:**
- Compare against your own documents.
- Ask for what's changed since last time.
- Pair each action with a deadline.

### 115. Track discovery timelines and analyze patterns
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/track-discovery-timelines-and-analyze-patterns)

> Build chronologies and identify document patterns across large discovery productions.

**Prompt mẫu:**
> "I'm representing a small software company in a contract dispute with a vendor. We hired them to build a custom inventory management system, but the project failed and we're in litigation.
> I've got about 40 discovery documents—contracts, change orders, email threads, project status reports, invoices, and technical documentation from the 12…"

**Context:** Gmail, Google Drive (bắt buộc)

**Output:** Claude produces a comprehensive legal analysis document (.docx format) organized into clear sections.

## HR (6)

### 116. Create new hire onboarding guides
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-new-hire-onboarding-guides)

> Turn standard company information and a new hire's specific details into a personalized welcome guide.
> Claude organizes logistics, schedules, and key contacts into one clear document that helps new employees feel prepared from day one.

**Prompt mẫu:**
> "Create a first week guide for Sarah Chen, starting as Senior Product Designer on our Design Systems team this Monday, November 4th. Her manager is Michael Torres.
> Include: Welcome and what to expect their first week Her specific onboarding schedule Office logistics"

**Context:** Google Drive (bắt buộc)

**Output:** Claude combines your standard company information with personalized details into a single, welcoming guide that equips new hires with helpful, specific onboarding information.

### 117. Engagement survey to action plan
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/engagement-survey-themes)

> Top themes, supporting quotes, and a 30-day action plan.

**Prompt mẫu:**
> "Theme the open-text survey responses, segment by team and tenure where the data allows, and separate loud-minority comments from broad signal.
> Output a one-page People brief: the top three themes, two or three supporting quotes per theme,
> and a draft 30-day action plan for each Never attribute a quote to an individual People / engagement-…"

**Context:**
- Google Drive (bắt buộc)
- Slack (tùy chọn)

**Plugins:** org-planning

**Tips:**
- State the privacy rule explicitly.
- Say how to weight the responses.
- Ask for an action per theme.

### 118. Interview debrief synthesis
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/interview-debrief)

> Where the panel agreed, where they split, what to resolve.

**Prompt mẫu:**
> "/recruiting-pipeline and other recruiting skills as a starting point, already structured to compare scorecards against a rubric and surface agreement and splits.
> If your admin manages plugins and it's not available yet, skip this step. The prompt below works without it. Human Resources Streamline people operations — recruiting, onboarding…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 119. Offer process
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/offer-process)

> Candidate email, offer fields, and a screenshare-ready deck.

**Prompt mẫu:**
> "/draft-offer and other recruiting skills as a starting point, already structured to fill an offer template, draft the email, and lay out the call deck.
> If your admin manages plugins and it's not available yet, skip this step. The prompt below works without it. Human Resources 9 skills for recruiting, onboarding, performance reviews, comp…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 120. Open a new role
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/open-new-role)

> A consistent role spec without the kickoff meeting.

**Prompt mẫu:**
> "/recruiting-pipeline and other recruiting skills as a starting point, already structured to ask the intake questions in order and write to a spec template.
> If your admin manages plugins and it's not available yet, skip this step. The prompt below works without it. Human Resources 9 skills for recruiting, onboarding, performance reviews, c…"

**Output:** A plugin skill is a starting point. Customize it with your own practices and expertise, or save what you've done as a skill of your own.
A few minutes of conversation and it runs with your standards from then on.

### 121. Performance review administrator
*10′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/performance-review-admin)

> Your perf framework published as a skill every manager runs.

**Prompt mẫu:**
> "Help me build the /performance-review skill for our managers. The skill should walk a manager through gathering input, scoring against our competencies, and drafting the review in our template.
> It should quote our rating definitions verbatim and never invent criteria that aren't in the framework People / perf-cycle"

**Context:**
- Google Drive (bắt buộc)
- Asana (tùy chọn)

**Plugins:** performance-review

**Tips:**
- Ask for a reusable process.
- Say what it must not make up.
- List the steps in order.

## Research — Nghiên cứu (7)

### 122. Chart a metric from your data warehouse
*10′ · Tag* — [Mở trang gốc →](https://academy.claude.com/use-cases/chart-a-metric-from-your-data-warehouse)

> Ask a data question in the thread where a number is being discussed, and Claude Tag queries the connected warehouse and replies with a chart and the query.

**Prompt mẫu:**
> "Ask in the thread where the discussion is happening, each time you need a number from the data warehouse. Name the metric and the time period.
> Claude reads the whole thread, so you can refer to something said earlier without describing it again."

### 123. Map your lit review mid-conversation to surface the underlying debate
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/map-your-lit-review-mid-conversation)

> Claude reads your stack of papers and draws the argument structure inline — clusters by claim, tension lines where camps disagree, blind spots per group.
> A reading of the debate you test against your own, as you work through the set.

**Prompt mẫu:**
> "I've read 20 papers on AI in K-12 and I've lost the thread. Can you map out who's actually agreeing with who and where the real disagreements are?
> I can't tell anymore which papers are building on each other and which are talking past each other. If I click into a group, give me the short version of what they've got and what they're missi…"

**Output:** Claude clusters by

### 124. Plan your literature review
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/plan-your-literature-review)

> With Claude as your research assistant, find relevant research, prioritize what to read, and organize evidence as you work through papers.

**Prompt mẫu:**
> "I'm beginning a literature review on the gut-brain axis and its role in mood disorders, specifically depression and anxiety.
> I need to understand:
> Mechanisms linking gut microbiome changes to mood regulation Evidence for probiotic interventions in clinical trials The role of inflammation and neurotransmitter production Search PubMed for t…"

**Context:** PubMed (bắt buộc)

**Output:** Claude researches PubMed’s database to find relevant papers and creates a guide to help you through your entire research process—from initial discovery through final synthesis.

### 125. Surface themes from all your feedback channels
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/surface-themes-from-all-your-feedback-channels)

> Synthesize feedback from call transcripts, Slack, CRM notes, and Linear issues to identify cross-platform patterns and generate prioritized product ideas.

**Prompt mẫu:**
> "I need to understand what customers are really asking for by synthesizing feedback from multiple sources.
> Sources: Call transcripts: Scattered across my downloads folder Slack in channels like #customer-feedback and #support-questions Salesforce: Opportunity notes and lost deal reasons"

**Output:** Claude synthesizes feedback from all connected sources, identifies themes with counts and attribution, highlights patterns that appear across multiple platforms,
and suggests prioritized product ideas.

### 126. Turn transit time into research time
*20′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/turn-transit-time-into-research-time)

> Capture rough thoughts by voice on mobile, then let Claude research your ideas and produce polished deliverables at your desk.
> Claude maintains full context across devices, so your commute becomes productive thinking time.

**Prompt mẫu:**
> "[using voice, on mobile] I just had a thought for the product meeting later. I want to look into what our competitors are doing with their onboarding flows.
> I feel like everybody's moving towards a simpler experience. Can you pull in our Q1 planning doc because I need to remember where we landed on roadmap priorities. I think we might be…"

**Context:** Web Search

**Output:** Claude delivers a research-backed meeting prep while you're still in transit.
By the time you reach your desk, you have organized findings, relevant stats, competitor analysis, and suggested talking points ready to refine and present.

### 127. Verify statistics from raw data
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/verify-statistics-from-raw-data)

> Learn to evaluate published statistics by checking them against raw data.

**Prompt mẫu:**
> "I'm reading this paper that's central to my literature review, and I want to understand it more deeply before citing it extensively.
> I've got the published manuscript and their supplementary data files. Can you help me verify their statistical claims?
> Go through the paper systematically and pull out every p-value, mean, standard error, sa…"

**Output:** Claude creates a comprehensive audit workbook documenting every statistical check, showing you exactly what to watch for and building your ability to critically evaluate research methods.

### 128. Work through grant options in chat
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/work-through-grant-options-in-chat-with-claude)

> Claude plots every funder in one view — odds, award, deadline, effort — and you filter, test scenarios, ask for a prioritization, narrow down together.
> For decisions where no single sort order shows the full picture.

**Prompt mẫu:**
> "I'm planning grant submissions for next year and there are a lot of funders to choose between.
> Can you show me the tradeoffs in a way I can actually see — like, which ones are long shots for big money versus safer bets for smaller awards? Flag anything with a deadline coming up soon."

**Output:** Claude folds four spreadsheet columns into position, size, and color on one chart — so all the tradeoffs are in view at once.
Long shots cluster upper-left, safe bets lower-right, and the distance between those corners is where your strategy sits. The expected…

## Education — Giáo dục (10)

### 129. Adapt a standard textbook page to every reading level
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/adapt-a-standard-textbook-page-to-every-reading-level)

> Claude Opus 5 reads a single source page in detail and returns a finished file for each audience that needs it. Here, one textbook spread becomes a slide deck and reading handouts at three levels.

**Prompt mẫu:**
> "I've attached: tectonics-textbook-p214-215.jpg (the source spread, including the diagram and sidebar) state-standards-ess2.txt (the standards these need to map to)
> my-class-roster-levels.csv (which students are at which reading level — A below grade, B at grade, C above) From the textbook spread, build me:"

**Output:** Claude reads the page, including the diagram and any sidebar text, and builds the materials the way you described.
You get a slide deck, the three reading handouts as separate.docx files, and the exit ticket — each mapped to the standard you named. A short not…

### 130. Apply a formula as you learn it
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/apply-a-formula-as-you-learn-it-in-chat-with-claude)

> Claude builds a blank scatter right in the conversation — you place the points, drag them, watch what happens to the fit. For when you can do the calculation but don't yet have a feel for it.

**Prompt mẫu:**
> "I'm learning linear regression and I can do the formula but I don't get it. Can you give me something where I can mess with the data points myself and watch what happens to the line?
> I want to actually feel why one weird point can throw the whole thing off. Can you help me visualize?"

**Output:** Claude hands you an empty canvas. You click to place points, drag to break things, watch the line respond.
Placing the outlier yourself and watching the line pull toward it is what makes the squared-distance weighting click — you've read that big misses count…

### 131. Bring your whiteboard lesson to life
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/bring-your-whiteboard-lesson-to-life)

> Work through how to teach a concept with Claude sketching alongside.
> The visual streams in as part of the back-and-forth — a thinking tool for your prep first, and a teaching tool if you take it further.

**Prompt mẫu:**
> "I'm prepping to teach supply and demand equilibrium next week. Here's the sketch I've been using — students tend to follow the crossing but not why the price goes there.
> What's a better way to frame it? And is there a way to show them the pressure toward equilibrium, not just the intersection?"

**Output:** The response is a teaching conversation with a visual woven through it. Claude diagnoses why the static sketch loses students — a concept about

### 132. Chart your data in conversation with Claude before you commit to a reading
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/chart-your-data-before-you-commit)

> Upload a CSV and Claude builds the correlation grid inline, flagging the patterns worth a second look.
> The flags are a starting point — you click into what's interesting and the conversation goes from there.

**Prompt mẫu:**
> "Show me what this data is telling me. I'm looking for the strongest relationships in here. Can you give me a correlation matrix and let me click into any pair to see the scatter?
> Flag anything that surprises you. Don't hold back on making this readable; I'm presenting this to a committee."

**Output:** Claude builds the grid, then calls out what stands out. The clickable matrix shows every pair; below it Claude flags which cells cut against the expected story.
The flags are worth checking — a striking cell can be real, or a confound, or a quirk of this sampl…

### 133. Create custom course materials
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-custom-course-materials)

> Transform handwritten equations and notes into formatted LaTeX documents without manual typesetting.

**Prompt mẫu:**
> "I'm a math professor converting my handwritten integration notes into a professional course materials.
> I have: Handwritten notes with equations A typed outline of topics Craft a professional-looking LaTeX document, resembling a published textbook page with colored boxes and precise equations,
> then convert it to PDF."

**Output:** Claude generates a complete LaTeX document ready to print as a PDF with professional formatting, colored boxes, formulas and typography ready for students.

### 134. Plan your career path
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/plan-your-career-path)

> Map the jobs you want to a career plan—skill gaps, timelines, people to contact, and specific next steps.

**Prompt mẫu:**
> "I'm a sophomore at UC Berkeley targeting these roles:
> Associate Product Manager at a music streaming company - https://musicstreaming.com/careers/apm Product Designer at a design collaboration platform - https://designplatform.com/careers/designer"

**Context:**
- Google Drive (bắt buộc)
- Web Search

**Output:** Claude will analyze your resume against your target jobs and create two planning documents:
an action-oriented roadmap and a detailed skills tracking system—both professionally formatted and built for ongoing use.

### 135. Plan your syllabus
*10′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/plan-your-syllabus-see-which-weeks-are-locked)

> Attach your syllabus and Claude shows which weeks are locked by real prerequisites and which you're free to rearrange — right in chat as you work through the order.

**Prompt mẫu:**
> "to be, and which are there because that's where you or the textbook put them. Working as a list, those look the same. You ask Claude about the order, and the graph appears as part of its answer.
> It shows which weeks are locked by real prerequisites and which are there by habit — so you can see where you have room to rearrange. Here an eco…"

**Output:** Claude draws the course as a graph — locked weeks in one color, movable weeks in another.
Click any topic and a panel shows what comes before it, what it unlocks, and how the major textbooks handle that same spot in the sequence. You get a second opinion on ea…

### 136. Practice case interviews with feedback
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/practice-case-interviews-with-feedback)

> Work through consulting cases with structured frameworks, guidance, and intelligent feedback

**Prompt mẫu:**
> "I'm practicing for consulting interviews. Set up this practice scenario for me—using case I've uploaded, extract the data into an spreadsheet model with formulas and frameworks.
> Then, tell me what questions I should focus on. After I finish my analysis and write my recommendation, I'll share it for feedback. Review it like a senior partne…"

**Output:** Claude builds a complete practice environment: a spreadsheet model with extracted data and analytical frameworks,
plus structured guidance on what to analyze and how to approach your recommendation.

### 137. Turn research into presentations
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/turn-research-into-presentations)

> Learn how to turn research into presentations that stick.
> Claude helps translate findings into slide outlines and speaker notes that show what's compelling, how to structure the story,
> and which visuals would help—giving you the framework to build your presentation.

**Prompt mẫu:**
> "I'm uploading our group paper on sleep quality and academic performance. We have 12 minutes to present to a mixed audience of professors and students, with 4 presenters sharing the time.
> Analyze this research to: Extract the 3-4 most compelling findings that will resonate with our audience Create a logical narrative flow that builds from…"

**Context:** Google Drive, Canva (bắt buộc)

**Output:** Claude transforms your research into presentation materials structured for clarity and impact—slides outlined with sections from your research that are ready for editing and speaker
notes that distribute content logically across presenters.

### 138. Visualize the mechanism behind an explanation mid-chat
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/visualize-the-mechanism-behind-an-explanation-mid-chat)

> Claude builds an interactive visual inline as you talk through the problem — shaped to the specific question you're asking, with controls you manipulate and buttons that drill deeper.
> Useful when a concept has moving parts text can't show.

**Prompt mẫu:**
> "I'm learning orbital mechanics and I understand that the planet speeds up when it's close to the sun and slows down when it's far. But I don't understand why that trade-off exists.
> Why can't it just go fast the whole time? Help me understand with a well crafted, interactive, dynamic visualization."

**Output:** Claude builds three linked views of the same mechanism tied to one slider — the trade-off runs in all three at once. The slider hands you the variable.
Drag it and the answer to "why can't it just go fast" shows itself: the energy bar pins the total, so speed…

## Cá nhân (Personal) (18)

### 139. Build a custom bucket list
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-a-custom-bucket-list-app)

> Turn any tracker, organizer, or goal system you've imagined into a working interactive tool. Describe what you want and watch Claude build it.

**Prompt mẫu:**
> "I want to create an interactive "bucket list builder" that feels like browsing a beautiful, high-end boutique, but for life experiences instead of products.
> The concept: Transform "I should make a future goals list" into something more joyful. Instead of just a normal list, I want an experience. Design: This needs to look like a world-cla…"

**Output:** Claude builds a fully interactive application matching your specifications, browsable, clickable, and styled to your design standards.

### 140. Build interactive diagram tools
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/build-interactive-diagram-tools)

> From body systems to molecular structures, turn a detailed prompt into a working reference app with the depth and design you specify.

**Prompt mẫu:**
> "You don't need to start this specific. Begin with the experience you want, then fold in technical constraints like the SVG fill and UBERON notes as you discover what trips the build up.
> Build an interactive anatomy explorer using @ebi-gene-expression-group/anatomogram from npm. Use homo_sapiens.male.svg and homo_sapiens.brain.svg. Don't g…"

**Output:** Claude builds a fully functional React application with the visual design, interaction patterns, and educational content you specified, ready to use immediately in the artifact viewer.

### 141. Compare products across sites
*15′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/compare-products-across-sites)

> Claude in Chrome reads the specs from multiple product pages you have open, normalizes the data, and creates a comparison table in Google Sheets. You stop tab-switching and start deciding.

**Prompt mẫu:**
> "I'm trying to decide between a few laptops and I have the product pages open in different tabs.
> Can you look at each one, pull out the specs, and put them in a Google Doc so I can compare them side by side? I care most about: processor, RAM, storage, screen size, battery life, and weight.
> Let me know which one wins on each category."

**Output:** Claude analyzes and extracts information from across tabs, drafting a comparison doc that highlights which product wins each category, and gives a quick recommendation.

### 142. Create a custom webpage
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-custom-webpage)

> Build a portfolio site to showcase your work and learn how to deploy it live without writing a line of code.

**Prompt mẫu:**
> "and coding abilities work together to transform your descriptions and images into working web interfaces.
> Paired with your resume and past projects, Claude can create a portfolio that reflects both your professional narrative and preferred design style.
> Tell Claude to build your portfolio site using your uploaded resume and project files.…"

**Output:** Claude builds a complete portfolio page as an HTML artifact. The artifact includes your professional information, project showcases, and design choices to match your aesthetic preferences.

### 143. Create a daily travel itinerary
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-a-daily-travel-itinerary)

> Create a customized travel itinerary with intelligent guidance, adapting to your preferences and desired activities.

**Prompt mẫu:**
> "Create a 5-day trip itinerary for my visit to Lisbon in early June.
> I want authentic neighborhood restaurants where locals eat, Manueline and Pombaline architecture at the actual monuments, genuine fado experiences, to walk 8-10 miles daily instead of using transit,
> and to visit only truly exceptional museums like Gulbenkian while skippin…"

**Output:** Claude searches the web to find current recommendations, then filters research through your specific criteria—identifying the architecture styles, food experiences,
and museums you actually care about, instead of comprehensive attraction lists. It then builds…

### 144. Create digital recipe cards
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-digital-recipe-cards)

> Turn handwritten family recipes into digitally formatted recipes to save and share.

**Prompt mẫu:**
> "Read this recipe and turn it into something I can share with family. Decode the handwriting, convert vague measurements into precise amounts, and write clear steps.
> Create an interactive recipe artifact (for digital sharing). Include: A serving size adjuster that dynamically scales ingredient amounts"

**Output:** Claude delivers a recipe artifact, complete with an interactive serving size adjuster, clear instructions,
and cooking insights that honor the original while making it practical for cooking and sharing.

### 145. Create health and exercise notes
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/create-health-and-exercise-notes)

> Research specific exercises and save organized notes directly to your Notes app.

**Prompt mẫu:**
> "I've been dealing with knee pain, and my doctor recommended I strengthen the muscles around it. I'd like to research appropriate exercises and create a routine I can do on my own.
> Save this to my Notes app as "Knee Strengthening Routine" so I can pull it up on my phone while I'm exercising. I want to show it to my physical therapist next…"

**Context:** Web Search

**Output:** Claude searches for current exercise information and physical therapy best practices, and then structures findings into a clear routine saved directly to your Notes app.
You can reference it across devices or during workouts and healthcare appointments.

### 146. Debate practice with feedback
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/debate-practice-with-feedback)

> Test your ideas against opposing views through an interactive tool where you defend your position and get real-time pushback.

**Prompt mẫu:**
> "I have a debate coming up and need to prepare. I want to be able to state my topic and position, then get challenged with real counterarguments and evidence so I can test my responses.
> Can you create an artifact where I can practice debating any topic against the strongest possible opponent? Make it genuinely tough - I need practice again…"

**Output:** Claude researches the strongest intellectual opposition to your position, then creates an interactive practice simulator where you defend your arguments against a challenging opponent.
The artifact uses Claude's API to generate intelligent counterarguments in…

### 147. Design a local foraging guide
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/design-a-local-foraging-guide)

> Build artifacts where the map is the menu. Select your state on an interactive map browse by category and export a printable reference.

**Prompt mẫu:**
> "I want to build a foraging guide for someone new to wild edibles and unsure where to start.
> What it should do:
> Let users click their state on an interactive US map to see regional foraging data (fetch map data from the us-atlas TopoJSON CDN at https://cdn.jsdelivr.net/npm/us-atlas@3/states-10m.json and
> render with D3's geoAlbersUsa projec…"

**Output:** Claude produces a complete, working foraging guide beginning with an interactive US map where clicking a state reveals regional plant data.

### 148. Elevate Claude's design using skills
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/elevate-claudes-design-using-skills)

> Design a skill that automatically activates design principles into Claude’s outputs.

**Prompt mẫu:**
> "I create a lot of visual outputs with Claude—presentations, dashboards, reports, HTML pages. They're functional but always feel generic, like first drafts rather than polished work.
> I want them to look like they've been through multiple rounds of professional design refinement. I'd like to create a skill that automatically applies design…"

**Output:** Claude produces a complete skill structure with a main instruction file and supporting references. The skill is immediately usable once added to your Claude Skills library.
Once you refer to ‘design excellence’ in a chat, Claude will automatically apply the sk…

### 149. Map your understanding and build lessons from the gaps
*20′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/map-your-understanding-and-build-lessons-from-the-gaps)

> Claude Opus 5 traces your confusion to its source. It maps what you already understand, finds the specific misconception underneath, and builds personalized learning experiences around it.

**Prompt mẫu:**
> "I keep running into “Bayesian reasoning” in things I read—essays, podcasts, even conversations at work.
> People say “update your priors” or “you’re ignoring the base rate” and I nod along, but I can’t actually follow the logic when it gets specific. I understand basic probability fine.
> I can calculate odds, I know what a conditional probab…"

**Output:** Claude asks diagnostic questions first, probing what you know until it identifies the specific misconception. Then it rebuilds from the gap and produces all three artifacts.
Opus 5 stays persistent through this entire sequence, and its writing keeps pace: the…

### 150. Organize files across your desktop
*15′ · Cowork* — [Mở trang gốc →](https://academy.claude.com/use-cases/organize-files-by-whats-in-them)

> Grant Cowork access to your cluttered desktop and walk away. It reads your files, figures out what they are, and sorts them into folders while you do something else.

**Prompt mẫu:**
> "Please help organize my desktop. Evaluate all of the scattered files and organize based on the contents inside of them."

**Output:** Cowork scans your desktop, categorizes each file, and creates a folder structure. You'll see progress updates as it works and a summary of what changed.

### 151. Organize files in Google Drive
*15′ · Chrome* — [Mở trang gốc →](https://academy.claude.com/use-cases/organize-files-in-google-drive)

> Claude in Chrome sorts through your Drive, creates a folder structure, moves files where they belong, and flags duplicates and old files for you to review.
> You approve the changes instead of doing the sorting yourself.

**Prompt mẫu:**
> "I need to organize my Google Drive by reviewing all files and creating a logical folder structure.
> What to do: Scan through my Drive including Downloads, Shared with me, and the root level Create appropriately named folders based on what you find (e.g., by project, file type, or year)
> Move files into the folders you create"

**Output:** Claude reports what it organized, what it moved, and what needs your decision before going further.

### 152. Research and compare travel destinations
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/research-and-compare-travel-destinations)

> Create a visual comparison spreadsheet from research with images, ratings, and insights to simplify your travel planning.

**Prompt mẫu:**
> "I'm planning a June vacation leaving from San Francisco, and I'm deciding between 5 destinations: Lisbon, Reykjavik, Dubrovnik, Kyoto, and Oaxaca.
> Can you research these places and create a comparison spreadsheet that helps me visualize the differences across various dimensions? I want to see them side-by-side so I can compare easily. Use…"

**Context:** Web Search

**Output:** Claude researches each destination comprehensively and produces a multi-sheet spreadsheet file with visual comparisons, detailed ratings across 10+ dimensions, cost breakdowns,
and direct links to tourism resources—all correctly formatted with design elements…

### 153. Stress-test your financial plan across scenarios
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/stress-test-your-financial-plan-across-scenarios)

> Claude Opus 5.5 tests a financial plan against a full range of possible outcomes, traces how each risk cascades through the rest, and builds a working model you can adjust yourself.

**Prompt mẫu:**
> "Claude for Excel. I’m 52, hoping to retire at 62. My partner and I have about $1.2M across a 401(k), Roth IRA, and taxable brokerage. I make $185K, he makes $95K, we spend about $8,500/month.
> Mortgage is paid off in 2031. Not sure if we should be doing Roth conversions now while we’re in a lower bracket. I’ve uploaded our tax returns, inv…"

**Output:** Opus 5.5 produces a working financial model with probability distributions across a range of modeled scenarios, an interactive scenario explorer, and a clear action plan.
Keep in mind, Claude produces outputs based on the documents you provide. You should revi…

### 154. Thoughtful gift giving with Claude
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/thoughtful-gift-giving-with-claude)

> Turn last-minute gift panic into thoughtful, personalized presents.
> Claude can suggest items, search your notes for forgotten hints, find specific products you can buy locally, and help you coordinate the actual shopping.

**Prompt mẫu:**
> "Wife (38) — really into skincare lately, drinks a lot of tea, always cold Son (12) — obsessed with basketball, just started getting into music Daughter (9) — loves art projects,
> reads constantly, very into her pet hamster Dad (67) — impossible to buy for, likes golf and grilling, diabetic so no candy Mom (65) — does crossword puzzles ever…"

**Context:** Web Search

**Output:** Claude generates a personalized shopping list organized by recipient, with specific product suggestions, reasoning for each choice, and a store-run strategy that minimizes trips.

### 155. Turn inspiration into design plans
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/turn-inspiration-to-design-plans)

> Turn your saved design inspirations into a personalized cost-effective renovation plan with a balanced investment strategy.

**Prompt mẫu:**
> "I'm planning a kitchen reno and I've saved images of kitchens I love, but I'm overwhelmed by the choices.
> Figure out what style I'm going for and help me make smart purchase decisions about where to spend and where to invest. Analyze my images and identify the style.
> Break down what defines it and how it differs from similar styles. Resea…"

**Context:** Web Search

**Output:** Claude provides a spreadsheet that consolidates all research from your preferences, including style definitions, furniture options by type, price comparisons, and direct links,
enabling you to make informed decisions and edit as needed.

### 156. Turn text threads to researched notes
*15′ · Claude* — [Mở trang gốc →](https://academy.claude.com/use-cases/turn-text-threads-to-researched-notes)

> Search messages for information, research answers, and create organized notes directly in your Notes app.

**Prompt mẫu:**
> "(MCP), Claude can connect to your everyday tools and apps.
> When you enable connectors, Claude pulls context directly from Messages or Notes and saves organized information back to your apps, eliminating the need for copying, pasting,
> or switching between tools. Point Claude to a message thread. It'll find the relevant conversation, resear…"

**Context:** Web Search

**Output:** Claude analyzes your messages for key details within conversation threads, then uses Web Search to find relevant options online.
Finally, it stores organized notes in your Notes app, accessible across all your devices.
