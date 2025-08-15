# Phase 1: Planning & Architecture – Planner App

## Overview

This document outlines the core features and architectural decisions for building a planner app with iCal integration, task management, calendar views, priority logic, and productivity tools. It also explores data handling strategies and account management requirements for mobile deployment.

---

## Core Features

### 1. Importing iCal Files
- Allow users to upload `.ics` files from local storage or cloud services.
- Parse events and convert them into internal task objects.
- Handle recurring events and time zone data.

### 2. Adding Tasks
- Manual task creation with fields:
  - Title
  - Description
  - Start and end time
  - Priority level (e.g., Low, Medium, High)
  - Optional tags or categories
- Support for subtasks or checklists (optional enhancement).

### 3. Viewing Tasks on Calendar
- Calendar views:
  - Daily view
  - Weekly view
  - Monthly view
- Highlight tasks based on priority or category.
- Toggle between agenda list and calendar grid.

### 4. Priority Logic and Task Options
- Implement Eisenhower Matrix or weighted scoring (e.g., urgency × importance).
- Allow users to sort/filter tasks by priority.
- Additional options:
  - Notifications/reminders
  - Task repetition
  - Color coding or icons

### 5. Exporting Final iCal File
- Convert internal task data back to `.ics` format.
- Include metadata such as priority, categories, and recurrence.
- Allow export to local storage or cloud services.

---

## Study Tools

### 1. Pomodoro Timer
- Built-in timer with customizable work and break intervals.
- Visual countdown and progress tracker.
- Optional task linking (e.g., start Pomodoro for a specific task).
- Session history and analytics (e.g., number of completed Pomodoros).

### 2. Focus Mode (Optional Enhancement)
- Distraction-free interface during Pomodoro sessions.
- Option to block notifications or dim unrelated UI elements.

### 3. Task Completion Tracker
- Visual indicators for completed tasks.
- Daily/weekly progress summaries.
- Optional gamification (e.g., streaks, badges).

---

## Data Handling Strategy

### Option A: Local Database
- Use SQLite or Hive for structured, persistent storage.
- Pros:
  - Fast and reliable
  - Works offline
  - Easier to manage complex relationships (e.g., recurring tasks)
- Cons:
  - Requires sync logic if cloud backup is added later

### Option B: Cookies or Local Storage
- Store data in browser cookies or local storage (for web version only).
- Pros:
  - Simple to implement
  - No backend required
- Cons:
  - Limited storage capacity
  - Not secure or scalable
  - Not suitable for mobile apps

### Recommendation:
Use a local database (e.g., Hive or SQLite) for mobile apps. Consider adding cloud sync (Firebase or Supabase) in later phases.

---

## Account Management Considerations

If the app includes user accounts, especially for syncing or cross-device access, follow these guidelines:

### 1. Authentication
- Use secure methods like OAuth, Firebase Auth, or Supabase Auth.
- Support email/password and third-party logins (Google, Apple).

### 2. Data Privacy
- Comply with platform-specific privacy policies (GDPR, CCPA).
- Provide clear terms of service and privacy policy.

### 3. App Store Restrictions
- Apple App Store:
  - Must support Sign in with Apple if other third-party logins are used.
  - Require user consent for data collection.
- Google Play Store:
  - Must disclose data usage and permissions.
  - Avoid unnecessary background access.

### 4. Offline Access
- Ensure basic functionality without login (optional guest mode).
- Sync data when user signs in.

---

## Next Steps

- Finalize feature scope for MVP.
- Choose architecture (MVVM or Clean Architecture).
- Decide on state management (Riverpod recommended).
- Begin wireframing UI and planning folder structure.
