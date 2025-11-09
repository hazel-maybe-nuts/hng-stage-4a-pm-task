## ​The DayMap Technical Blueprint

### ​1. Technology Stack

This stack is chosen for its performance in handling high-volume time-series data and its ability to deliver a real-time, responsive user experience.

| COMPONENT | TECHNOLOGY | JUSTIFICATION |
| :--- | :--- | :--- |
| **Frontend** | React (with Next.js) | Provides a fast, modern, and highly interactive single-page application for the user dashboard. Next.js enables a mix of server-side and client-side rendering, which is ideal for serving both the interactive "Demo" and the main user dashboard. |
| **Backend** | Node.js (with Fastify) | The backend must handle a high volume of concurrent write operations from thousands of data collectors. Node.js is excellent for I/O-heavy tasks. We choose Fastify over Express for its superior performance and lower overhead, which is critical for an ingestion API. |
| **Relational DB** | PostgreSQL | The "source of truth" for all user data. This database will store user accounts, settings, goals, integration API keys (encrypted), and other structured, low-volume relational data. It is chosen for its rock-solid reliability and ACID compliance. |
| **Time-Series DB** | TimescaleDB | This is the core engine for DayMap's analytics. Standard databases are inefficient for time-series data. TimescaleDB (a PostgreSQL extension) is purpose-built to ingest and query billions of time-stamped events (e.g., "app: chrome.exe, time: 14:05:01"). This allows for high-performance ingestion and complex, real-time analytical queries. |
| **Data Collectors** | Browser Extension & Web APIs | Data is collected from two primary sources: <ul><li>**Browser Extension (Chrome/Firefox):** This is the new "desktop collector." It is a low-friction install that captures active tab/URL and domain data.</li><li>**Direct APIs (OAuth):** Mobile and health data (Apple Health, Google Fit) are collected via their respective cloud-based web APIs, not native apps.</li></ul> |

---

### 2. Component Communication

The system is designed for a low-friction, web-first experience. It separates data collection into two types: real-time web activity and periodic API polling.
1.  **Collection (Web Activity):** The Browser Extension (Chrome, Firefox) runs on the user's computer. It locally tracks active web events (e.g., `app: "chrome.com/reddit"`, `title: "News"`) and securely batches these payloads.
2.  **Collection (External Data):** The Backend (Node.js) API periodically polls the connected External Web APIs (like Google Calendar, Google Fit, Apple Health) for new data. This is triggered after the user grants one-time OAuth permission via the frontend.
3.  **Ingestion:** The Browser Extension sends its batches to a dedicated, secure ingestion endpoint on the Backend API. The data from the External Web APIs is also processed by this same backend.
4.  **Processing & Storage:** The API receives the raw data. It authenticates the user, validates the payload, and performs two write operations:
    * It sends the raw, high-volume time-series data (e.g., `{"user_id": 456, "timestamp": 1678886500, "domain": "reddit.com"}`) directly to TimescaleDB for high-speed ingestion.
    * It may trigger background jobs to enrich this data using a "rules engine" (e.g., mapping "reddit.com" to a "Social Media" category).
5.  **Presentation:** When the user opens the Frontend (React) Dashboard, it authenticates them. It then requests their data from the API. The API queries both databases: PostgreSQL for user settings, and TimescaleDB for the powerful analytical queries (e.g., "Show me all 'Social Media' activity from the last 7 days").

---

### ​3. Technical Feasibility

​This web-first vision is highly feasible, but it represents a critical strategic trade-off: **we are prioritizing user adoption and a fast "Time-to-Fun" (TTF) over total data capture.**

The primary technical challenges are not in the backend stack, but in the limitations of our chosen collectors and the complexity of data normalization.
* **The Collector Challenge (The "Data Gap"):** Our low-friction model relies on a Browser Extension and cloud-based APIs (like Google Calendar, Apple Health) to get users to the "magic" moment quickly. This is a deliberate choice with known consequences:
    * **Desktop Data:** We **lose the ability to track non-browser desktop applications** (e.g., `Slack.exe`, `Photoshop`). This is a trade-off to avoid the high-friction install of a native desktop agent.
    * **Mobile Data:** We **lose granular, real-time mobile app data**. This is because we are limited to the summaries that cloud APIs (like Google Fit) expose, rather than using a native mobile app. Accessing this data natively is also a significant hurdle in itself, as Apple's Screen Time API, for example, is highly restrictive and not designed for data export.
* **The Normalization Challenge:** This challenge remains a core technical hurdle. The data we collect, from any source, is "messy."
    * For example, the backend must be able to understand that web visits to `mail.google.com` and `google.com/mail` are the same activity ("Gmail").
    * Similarly, if we later add a desktop agent, it must know that `chrome.exe` and `Google Chrome` are also the same entity.
    * This requires a **complex and constantly evolving "rules engine"** to categorize and normalize all incoming data. This engine is a core business asset.

This approach is sound because it acknowledges that users are tired of high-friction installs. By delivering the core product value with a simple browser extension, we create a viable path to user adoption. **Full native desktop and mobile apps can be introduced later as a "power-user" feature, but our first priority is getting users on the platform.**

---

​Here's a video from Apple that introduces the Screen Time API, which is relevant to the technical challenges I mentioned above:

[Learn about the Screen Time API at WWDC](https://www.youtube.com/watch?v=DKH0cw9LhtM)

This video is relevant because it explains the capabilities and, more importantly, the restrictions of the mobile APIs DayMap would need to use, which directly informs our technical feasibility assessment.

---

## Moving Parts: The Data Vision

DayMap's vision is fulfilled by layering different data points to create a high-fidelity "context" for the user's time. No single data point is enough.
* **Data Point 1: Active Web Activity (from Browser Extension):**
    * **Raw Data:** `domain: "reddit.com"`, `title: "Reddit - r/news"`
    * **Context:** What the user is actively focused on in their browser.
* **Data Point 2: Calendar Events (from Google/Outlook API):**
    * **Raw Data:** `event: "Project Phoenix Sync"`, `status: "Busy"`
    * **Context:** The user's intended focus.
* **Data Point 3: Health Data (from Apple Health/Google Fit APIs):**
    * **Raw Data:** `sleep: "7.5 hours"`, `steps: "8,200"`
    * **Context:** The user's physical and mental state, which impacts energy.

### How They Come Together (The Vision):

DayMap's "magic" is in the synthesis. The scenarios are now based only on the data we can realistically collect in our web-first model.
* **Scenario A:** `[Calendar: "Focus Block"] + [Web Activity: "github.com"] + [Web Activity: "stackoverflow.com"] = Successful Deep Work.`
* **Scenario B:** `[Calendar: "Focus Block"] + [Web Activity: "https://www.google.com/search?q=web.slack.com"] + [Web Activity: "mail.google.com"] + [Web Activity: "reddit.com"] = Fragmented Work.`
* **Scenario C:** `[Health: "Poor Sleep (4h)"] + [Activity: (Shows high "Fragmented Work")] = Insight: Burnout Risk.`

By combining these moving parts, DayMap graduates from a simple time tracker to a genuine personal analytics and strategy tool.