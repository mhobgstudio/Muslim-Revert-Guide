# Revert-Guide — Improvement Report

**Date:** August 27, 2026  
**Analysis Type:** Errors, Inconsistencies, Incompleteness, Missed Sections

---

## 🔴 Errors Found

### 1. Prayer Streak Logic Bug
- `updateStreak()` uses `new Date(d.getTime()-i*86400000).toDateString()` for date calculation. This doesn't account for **Daylight Saving Time** — on DST transition days, the offset could produce wrong dates, breaking streak counting.

### 2. Missing Final Verse of Al-Fatiha
- The Al-Fatiha section shows 6 verses but **omits the final verse**: "The path of those upon whom You have bestowed favor, not of those who have evoked [Your] anger or of those who are astray." This is an important omission — the complete Surah should be shown.

### 3. Theme Toggle — Wrong Icon on Load
- `tt.innerHTML = st==='dark'?'<i class="fas fa-sun"></i>':'<i class="fas fa-moon"></i>'` — shows moon in light mode. This is technically correct (click moon to go dark) but inconsistent with how other projects in this suite handle it.

---

## 🟡 Inconsistencies

### 1. No Page Structure
- Unlike other projects (Sharia-Law, Islamic_Finance), the Revert-Guide is a **single-page flat layout** with all content visible at once. There are no tabs or sections to navigate. This can overwhelm new users.

### 2. Prayer Tracker — No Reset
- The prayer tracker persists indefinitely in localStorage but has no "reset day" or "new day" detection. If a user opens the page the next day, the previous day's data stays but new clicks add to it. The `updateStreak()` function counts by date, but the UI doesn't distinguish between today's and yesterday's prayers.

### 3. No Arabic Audio
- Surah cards show Arabic text but have no audio playback button. Other projects (ISLAM ACADEMY) have audio for Arabic text.

### 4. Missing `progress.html` equivalent
- No progress page or way to see what sections have been read.

---

## 🟠 Incompleteness

### 1. Missing Core Sections for New Muslims
- **Shahada guide** — exact words, meaning, how to take Shahada
- **How to perform Ghusl** (ritual bath) — essential for new Muslims
- **Menstruation rules** — important for women reverts
- **Marriage to a Muslim** — common concern
- **Family reaction** — dealing with non-Muslim family
- **Workplace considerations** — prayer breaks, hijab, Ramadan
- **Naming conventions** — choosing a Muslim name

### 2. Missing Essential Surahs
- Only Al-Fatiha, Al-Ikhlas, and Ayatul Kursi are shown. Missing:
  - **Surah Al-Falaq (113)** — "Say I seek refuge in the Lord of daybreak"
  - **Surah An-Nas (114)** — "Say I seek refuge in the Lord of mankind"
  - **Surah Al-Kafirun (109)** — commonly recited in prayer
  - **Surah An-Nasr (110)** — short surah
  - **Ayat al-Kursi full text** — only summary shown

### 3. Missing Practical Guides
- **How to find a mosque** — practical steps
- **How to read the Quran** — from right to left, Arabic basics
- **Ramadan guide** — what to expect, Suhoor/Iftar
- **Zakat/Sadaqah guide** — when and how to give
- **Dua collection** — daily duas for new Muslims

### 4. No Multimedia
- No embedded videos (YouTube tutorials for prayer, etc.)
- No audio for Arabic pronunciation
- No visual diagrams for prayer positions

---

## 🔵 Missed Sections & Improvements

### 1. Missing Sections
- **Dealing with Islamophobia** — emotional support
- **Building a support network** — finding mentors
- **Common mistakes new Muslims make** — helpful guidance
- **Resources in different languages** — multilingual support
- **Convert stories** — inspiration from other reverts
- **FAQ for new Muslims** — answers to common questions

### 2. Interactive Features
- **Salah guide with step-by-step visual** (currently only text list)
- **Wudu guide with visual steps**
- **Dua journal** — save personal duas
- **Daily reminder system** — browser notifications for prayer times
- **Community forum link** — connect with other reverts

### 3. Technical Improvements
- No `manifest.json` for PWA
- No service worker for offline access
- No print-friendly layout
- No share functionality
- No language selector (Arabic/English/Urdu/etc.)

---

## 📋 Priority Recommendations

| Priority | Issue | Impact |
|----------|-------|--------|
| 🔴 P0 | Add missing verse 7 of Al-Fatiha | Incomplete Quran content |
| 🔴 P0 | Fix DST bug in prayer streak | Broken streak tracking |
| 🟡 P1 | Add Shahada guide (how to take Shahada) | Core need for reverts |
| 🟡 P1 | Add Ghusl guide | Essential ritual |
| 🟡 P1 | Add remaining short surahs (113-114) | Prayer preparation |
| 🟠 P2 | Add audio for Arabic text | Learning support |
| 🟠 P2 | Add tabbed navigation for sections | UX improvement |
| 🔵 P3 | Add video tutorials | Multimedia learning |
| 🔵 P3 | Add daily reminder system | Habit building |
