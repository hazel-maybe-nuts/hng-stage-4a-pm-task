# DayMap

[cite_start]DayMap is a personal analytics tool that reveals the true story of your day[cite: 2]. [cite_start]Unlike a calendar or to-do list, which represents your intentions, DayMap shows you the reality[cite: 3]. [cite_start]It operates as an objective mirror, helping you discover where your time, energy, and attention are actually invested[cite: 4].

## What DayMap Does

[cite_start]At its core, DayMap collects, unifies, and visualizes your scattered personal data[cite: 6]. [cite_start]It silently and securely tracks your computer activity, integrates with your mobile phone, and pulls from your digital calendars[cite: 7]. [cite_start]It then aggregates all this fragmented information into a single, cohesive, and easy-to-understand dashboard[cite: 8].

[cite_start]For example, you might see that you spend three hours "working" but that time was fragmented into 15-minute blocks split by social media checks[cite: 9]. [cite_start]Or you may discover your "peak" time for focused work is between 9 AM and 11 AM, a pattern you can then leverage[cite: 10].

## Why DayMap Matters

[cite_start]The primary problem DayMap solves is fragmented awareness[cite: 12]. [cite_start]Your data is already there, but it is siloed[cite: 12]. [cite_start]Your screen time is on your phone, your app usage is on your desktop, your meetings are in your calendar, and your workouts are in your health app[cite: 13]. [cite_start]You cannot get a complete picture[cite: 14].

[cite_start]DayMap brings all these pieces together[cite: 15]. [cite_start]We operate on the principle that time and attention are your most valuable resources[cite: 15]. [cite_start]Without an accurate account of how you spend them, it is impossible to be intentional[cite: 16]. [cite_start]DayMap provides that account, moving you from passive reaction to intentional action[cite: 17].

## Who DayMap Is For

[cite_start]DayMap is built for anyone who wants to be more intentional with their life[cite: 19]:
* [cite_start]**Professionals and Freelancers:** Individuals who need to optimize their workday, protect time for deep work, and diagnose the root cause of burnout[cite: 20].
* [cite_start]**Students:** Those who are learning to balance a demanding academic schedule with personal life and need to identify and improve their study habits[cite: 21].
* [cite_start]**The "Intentionally-Minded":** Anyone who has felt the day "slip by" and wants to regain a sense of control and align their actions with their long-term goals[cite: 22].

## Key Features

* [cite_start]**Automatic, "invisible" background tracking** for desktop and mobile[cite: 25].
* [cite_start]**A unified, visual dashboard** that acts as the central hub for your data[cite: 28, 29].
* [cite_start]**Third-Party Integrations** with Calendars, Health, and Location services[cite: 30].
* [cite_start]**Goal Setting, Alerts, and Reporting** to bridge the gap between insight and action[cite: 33, 34].

## High-Level Technology Stack

DayMap is built with a modern, scalable stack to handle real-time data securely.

| Component | Technology |
| --- | --- |
| **Frontend** | React (with Next.js) |
| **Backend** | Node.js (with Fastify) |
| **Relational DB** | PostgreSQL |
| **Time-Series DB** | TimescaleDB |
| **Data Collectors** | Native Agents (Electron, Swift, Kotlin) |
[cite_start][cite: 40]

## User Flow (In Words)

1.  [cite_start]**Onboarding:** A new user signs up on the DayMap website[cite: 63]. [cite_start]They are immediately prompted to download the desktop Data Collector and are given instructions to install the mobile app[cite: 64].
2.  [cite_start]**Configuration:** The user installs the desktop collector and grants it OS-level permissions[cite: 65]. [cite_start]On mobile, they log in and are guided through connecting Apple Health, Google Fit, and their primary Calendar[cite: 66].
3.  **Passive Collection:** The user does nothing. [cite_start]They live their life for a full day as the agents silently collect data[cite: 67].
4.  [cite_start]**First Insight:** The next morning, the user receives an email or push notification: "Your first DayMap is ready." [cite: 68]
5.  [cite_start]**Discovery:** The user logs into the web dashboard and sees a complete, visual timeline of their previous day, layering their calendar events with their actual app/web usage[cite: 69].

## User Flow Diagram

[cite_start][User Flow Diagram - Placeholder] [cite: 72]