# DayMap

DayMap is a personal analytics tool that reveals the true story of your day. Unlike a calendar or to-do list, which represents your *intentions*, DayMap shows you the *reality*. It operates as an objective mirror, helping you discover where your time, energy, and attention are actually invested.

## What DayMap Does

At its core, DayMap collects, unifies, and visualizes your scattered personal data. It silently and securely tracks your computer activity, integrates with your mobile phone, and pulls from your digital calendars. It then aggregates all this fragmented information into a single, cohesive, and easy-to-understand dashboard.

For example, you might see that you spend three hours "working" but that time was fragmented into 15-minute blocks split by social media checks. Or you may discover your "peak" time for focused work is between 9 AM and 11 AM, a pattern you can then leverage.

## Why DayMap Matters

The primary problem DayMap solves is **fragmented awareness**. Your data is already there, but it is siloed. Your screen time is on your phone, your app usage is on your desktop, your meetings are in your calendar, and your workouts are in your health app. You cannot get a complete picture.

DayMap brings all these pieces together. We operate on the principle that time and attention are your most valuable resources. Without an accurate account of how you spend them, it is impossible to be intentional. DayMap provides that account, moving you from passive reaction to intentional action.

## Who DayMap Is For

DayMap is built for anyone who wants to be more intentional with their life:

* **Professionals and Freelancers:** Individuals who need to optimize their workday, protect time for deep work, and diagnose the root cause of burnout.
* **Students:** Those who are learning to balance a demanding academic schedule with personal life and need to identify and improve their study habits.
* **The "Intentionally-Minded":** Anyone who has felt the day "slip by" and wants to regain a sense of control and align their actions with their long-term goals.

## Key Features

* **Automatic Background Tracking:** "Invisible" data collection for desktop and mobile. This captures the unfiltered truth of your habits.
* **Unified Visual Dashboard:** A central hub where all data streams converge to tell a single, simple story of your day.
* **Third-Party Integrations:** Connects to your calendars, health apps, and location data to provide a holistic view of how your time is allocated.
* **Goal Setting & Reporting:** Bridges the gap between insight and action by allowing you to set goals (e.g., "less than 1 hour on social media") and track your progress.

## High-Level Technology Stack

DayMap is built with a modern, scalable stack to handle real-time data securely.
* **Frontend:** React (Next.js)
* **Backend:** Node.js
* **Databases:** PostgreSQL & TimescaleDB
* **Data Collectors:** Native Agents (Electron, Swift, Kotlin)

## User Flow

1.  **Onboarding:** A new user signs up and is guided to download the desktop and mobile Data Collectors.
2.  **Configuration:** The user installs the collectors and grants permissions to access activity, calendar, and health data.
3.  **Passive Collection:** The user lives their life. The agents silently collect data in the background.
4.  **Discovery:** The user logs into the dashboard to see a complete, visual timeline of their day, layering their *intended* day (from their calendar) with their *real* day (from their activity).
