# The Story of DayMap

​DayMap is a personal analytics tool that reveals the true story of your day. Unlike a calendar or to-do list, which represents your intentions, DayMap shows you the reality. It operates as an objective mirror, helping you discover where your time, energy, and attention are actually invested.

## ​What DayMap Does

​At its core, DayMap collects, unifies, and visualizes your scattered personal data. It silently and securely tracks your computer activity, integrates with your mobile phone, and pulls from your digital calendars. It then aggregates all this fragmented information into a single, cohesive, and easy-to-understand dashboard.

​For example, you might see that you spend three hours "working" but that time was fragmented into 15-minute blocks split by social media checks. Or you may discover your "peak" time for focused work is between 9 AM and 11 AM, a pattern you can then leverage.

## ​Why DayMap Matters

​The primary problem DayMap solves is fragmented awareness. Your data is already there, but it is siloed. Your screen time is on your phone, your app usage is on your desktop, your meetings are in your calendar, and your workouts are in your health app. You cannot get a complete picture.

​DayMap brings all these pieces together. We operate on the principle that time and attention are your most valuable resources. Without an accurate account of how you spend them, it is impossible to be intentional. DayMap provides that account, moving you from passive reaction to intentional action.

## ​Who DayMap Is For

​DayMap is built for anyone who wants to be more intentional with their life:
* **Professionals and Freelancers:** Individuals who need to optimize their workday, protect time for deep work, and diagnose the root cause of burnout.
* **Students:** Those who are learning to balance a demanding academic schedule with personal life and need to identify and improve their study habits.
* **The "Intentionally-Minded":** Anyone who has felt the day "slip by" and wants to regain a sense of control and align their actions with their long-term goals.

## ​Key Features and Justification

The feature set is designed to move the user from passive data collection to active, informed change.
* **Feature:** Real-time Web Activity Tracking
* **Justification:** The value of DayMap lies in its honesty. Manual tracking is unreliable, prone to human error, and forgotten. Our low-friction browser extension captures the unfiltered truth of your web-based habits, which is necessary for genuine insight.

* **Feature:** A Unified, Visual Dashboard
* **Justification:** This directly solves the "fragmented awareness" problem. It is the central hub where all data streams converge to tell a single story, comparing your plan (from your calendar) to your reality (from your activity).

* **Feature:** Third-Party Integrations (Calendars & Health)
* **Justification:** Your web activity is only part of the story. Integrating calendar data provides context for your day (e.g., "Project Meeting"), and integrating health data (e.g., "Sleep," "Workout") provides a holistic view of how your energy and time are allocated.

* **Feature:** Goal Setting, Alerts, and Reporting
* **Justification:** Data alone is not useful. This feature bridges the gap between insight and action. A user can set a goal, such as "Spend less than 1 hour on social media," and DayMap can provide alerts or weekly reports on their progress.

## ​User Flow Diagram

![DayMap User Flow](./DayMap%20Flow%20Diagram.png)

[See user flow on figma](https://www.figma.com/board/0QRhdERUL8AelXthomXL5r/DayMap-Flow-Diagram?node-id=1-207&t=0nfl59ofqNKYQxsn-1)

## ​User Flow (In Words)

* **Initial Step:** A new user opens the DayMap website. They are presented with two choices: "See a Demo" or "Use Your Own Data."
* **Path A (Demo):** If the user selects "See a Demo," they are taken to an interactive dashboard. This dashboard is pre-populated with sample calendar events and activity data, allowing them to drag, click, and explore the product's features. A clear button is always visible to "Start With Your Own Data," allowing them to switch to the onboarding flow at any time.
* **Path B (Onboarding):** If the user selects "Use Your Own Data," they are prompted to sign up for a new account.
* **Configuration:** After signing up, the user is guided through a one-time setup process, all within the web browser. They are prompted to connect their data sources via OAuth:
    * Calendars: Google Calendar, Outlook Calendar.
    * Health: Apple Health, Google Fit.
    * Activity: They are prompted to install the DayMap Browser Extension to capture web-based activity (app usage, websites).
* **Passive Collection:** The user lives their life. DayMap, running in the browser and via its extension, passively collects and syncs data from their connected APIs and web activity.
* **First Insight:** The next morning, the user receives an email: "Your first DayMap is ready."
* **Discovery:** The user logs into the web dashboard and sees a complete, visual timeline of their previous day. It layers their planned calendar events with their actual, tracked web and health activity, allowing them to see the clear disconnect between their "planned" day and their "real" day.
