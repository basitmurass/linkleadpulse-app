LeadPulse AI — Local Lead, Reviews & Growth Suite
Single-file web app (index-10.html, ~239 KB) for finding local business leads, tracking reviews, managing client payments, and running outreach — built for a local lead / review-removal service business.
The file is the frontend only. It talks to a separate backend server over a REST API (default: http://localhost:5000). The server must be running for login and data features to work.

How to Run
Start the LeadPulse backend server (it listens on http://localhost:5000 by default).
Open index-10.html in Chrome (double-click the file — no build step, no install).
If the server runs on another address, open Settings in the app and update the API Base URL. The app stores it in the browser (leadpulse_api_base).
The top of the app shows the server status (connected / not connected) so you can confirm the backend is reachable.

Access — Three Levels
Level
How to enter
What it sees
Public visitor
No login
Landing page: features, Pricing, FAQ, manual payment info, Privacy / Terms / DMCA
Customer
License key (Client Access Key)
The views allowed by their plan
Staff / Owner
Owner PIN
Full app, including Client Access Keys management
Sessions are kept in the browser via localStorage (leadpulse_token, leadpulse_session_plan, leadpulse_session_type).
Plans (Customer Keys)
Plan
Price
Basic
$10/mo
Standard
$20/mo
Pro
$30/mo
Lifetime
Custom

App Views (Sidebar)
Dashboard — Business Overview & Analytics: totals, outreach stats, and account progress at a glance.
Leads — The core workspace:
Find Places to search local businesses and add them as leads.
Add leads manually, or import from CSV/Excel; export to CSV/Excel anytime.
AI lead analysis (single or bulk on selected leads) and automatic social-profile enrichment.
Per-lead Business Brief and Proposal: copy the proposal text, or send it by Email, WhatsApp, or Messenger; mark leads as sent / not sent.
Daily Reviews — Add and track daily reviews; automatic review checking (single, bulk, or the auto-robot run).
Accounts — Review Email Accounts Manager with 10,000+ account capacity: add one by one or bulk import, edit, cycle status, filter/search.
Inbox — Client email replies synced into the app: read threads, AI-draft a reply, and send from inside the app; manual "check inbox now" refresh.
Payments — Payments & Client Ledger: add/edit payments, generate a printable Invoice, export payments to CSV.
Posts — Manage posts with media upload and status toggle; export to CSV.
Keys (owner only) — Client Access Keys: generate, activate, suspend, renew, and delete license keys, each tied to a plan.
Trash — Deleted items land here first: restore them, or empty the trash permanently.
Settings — API Base URL, email setup test, and light/dark theme toggle.

Data & Storage
Business data (leads, payments, accounts, posts, keys) lives on the backend server and is loaded through the API — it is not stored inside this HTML file.
Only small preferences are kept in the browser's localStorage: session token, plan, API base URL, gate key, and theme.
Because data is server-side, the same account works from any browser that can reach the server; if the server is on your own PC (localhost), the app only works on that PC.

Tech Notes
One self-contained HTML file: markup, styles (Tailwind utility classes), and vanilla JavaScript — no framework, no build tools.
All server calls go through a single api() helper with token authentication; an expired session shows a re-login prompt instead of failing silently.
No credentials are hard-coded in this file; customer access is controlled entirely by the license keys managed in the Keys view.
