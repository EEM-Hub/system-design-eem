---
source: sources/wiki-Google_Drive.md
source_url: https://en.wikipedia.org/wiki/Google_Drive
---

## Google Drive: Cloud Storage and File Synchronization Service

Google Drive is Google's cloud-based file-hosting and synchronization service, launched April 24, 2012. It allows users to store files on Google's servers, sync across devices, and share with others. It integrates tightly with the Google Docs Editors suite (Docs, Sheets, Slides) and serves as a core component of Google Workspace for business customers. With 2 billion users as of December 2024, it is one of the most widely adopted cloud storage platforms.

## Key Concepts

- **Unified storage pool**: 15 GB free storage shared across Google Drive, Gmail, and Google Photos (unified in May 2013)
- **Google One**: Paid storage plans (100 GB at $1.99/mo, 2 TB at $9.99/mo, 2 TB with Gemini AI at $19.99/mo)
- **File size limits**: Uploaded files up to 5 TB; Google Docs up to 1.02M characters; Sheets up to 10M cells; Slides up to 100 MB converted
- **Sharing model**: Owner-based permissions with three access levels — "can edit", "can comment", "can view"; sharing options include specific Google accounts, "anybody with the link" (secret URL), or "public on the web" (search-engine indexable)
- **Shared file upload limit**: 400,000 items per shared drive
- **5 million file creation limit**: Quietly introduced Feb 2023, then removed after user backlash (April 2023)
- **Google Drive for Desktop**: Unified desktop client (replaced both "Backup and Sync" and "Drive File Stream" in July 2021); maps Drive to a drive letter with on-demand file access
- **Quick Access**: ML-powered feature that predicts files users need before searching
- **Search capabilities**: Natural language processing, OCR for text in images/PDFs, image content search (e.g., searching "mountain" finds mountain photos)
- **Gemini AI integration** (2024+): Sidebar chatbot for summarizing PDFs, synthesizing content across files, generating new content; requires Google One AI Premium or Workspace Gemini add-on
- **Third-party app ecosystem**: 5,300+ apps in Google Workspace Marketplace; SDK and real-time collaboration API available

## Commands and Syntax

No CLI commands — Google Drive is primarily a GUI/API-driven service. Key integration points:

- **Google Drive API**: RESTful API for third-party developers; supports real-time collaborative editing (released March 2013)
- **Google Drive SDK**: Works with Drive UI and Chrome Web Store to build installable apps
- **Chrome extension**: "Save to Google Drive" — saves web content as screenshots (visible/full page), HTML, MHTML, or Google Docs format
- **Mobile scanning**: Android app supports photo-to-document scanning with OCR
- **Offline access**: Available via Chrome extension and desktop/mobile apps

## Relationships

- **Google Workspace**: Drive is a core component; Workspace plans offer 30 GB (Starter) to unlimited storage; Education tier provides 100 TB since July 2022
- **Google Docs Editors** (Docs, Sheets, Slides): Integrated office suite; files created here are stored in Drive; editing was separated into standalone mobile apps in April 2014
- **Gmail & Google Photos**: Share the 15 GB free storage quota
- **Google One**: Paid tier branding for consumer storage plans (rebranded 2018)
- **ChromeOS**: Deep integration since ChromeOS v20; Chromebook users get 100 GB free for 12 months
- **Chrome Web Store**: Distribution channel for third-party Drive apps
- **Gemini (AI)**: Powers newer AI features in Drive sidebar for content summarization and generation
- **Competing services**: Dropbox, OneDrive — Google historically undercut on price (80% reduction in March 2014)

## Exam-Relevant Points

- Free storage is **15 GB shared** across Drive, Gmail, and Google Photos — not 15 GB per service
- Google Workspace Education provides **100 TB** (since July 2022), not unlimited
- Desktop client evolution: Google Drive app → Backup and Sync + Drive File Stream → **Google Drive for Desktop** (July 2021, current)
- Google Docs files counted against storage quota **starting June 1, 2021** (previously unlimited); files unmodified after that date remain exempt
- Maximum upload size: **5 TB** for non-native files; **750 GB** daily upload limit mentioned in overview
- Three sharing permission levels: **edit, comment, view**
- Sharing with non-Google users requires **"anybody with the link"** setting (no per-user control without Google account)
- Quick Access uses **machine learning** for file prediction
- Drive search uses **OCR** and **NLP** for intelligent file discovery
- Privacy policy covers **all Google services** under one unified agreement — not Drive-specific
