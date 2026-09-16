# Mayborg Vault 🛡️

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Status: Active](https://img.shields.io/badge/Status-Active-success.svg)]()
[![Platform: Web](https://img.shields.io/badge/Platform-Web-blue.svg)]()
[![Security: AES-GCM](https://img.shields.io/badge/Security-AES--GCM-red.svg)]()

> **Private notes. Thoughtful journaling. Secured right in your browser.**

[**Live Demo**](https://mayborg121.github.io/journal/) • [**Report a Bug**](https://github.com/mayborg121/journal/issues) • [**Request Feature**](https://github.com/mayborg121/journal/issues)

Mayborg Vault is a zero-knowledge, local-first journaling and note-taking workspace. Designed for absolute privacy, your data is encrypted using military-grade cryptography directly on your device before it is ever stored. There are no backend servers, no databases, and no trackers—just you and your thoughts.

---

## 📑 Table of Contents
- [Features](#-features)
- [Security Architecture](#-security-architecture)
- [Quick Start / Usage Guide](#-quick-start--usage-guide)
  - [Initial Setup](#initial-setup)
  - [Writing & Organizing](#writing--organizing)
  - [Backups & Syncing](#backups--syncing)
- [Local Development](#-local-development)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgments](#-acknowledgments)

---

## ✨ Features

* 🔒 **Zero-Knowledge Architecture:** Client-side encryption ensures that only you hold the keys to your data.
* 📝 **Rich Text Editing:** A seamless editor supporting paragraphs, dynamic headings (H1-H3), blockquotes, code blocks, and standard formatting.
* 🗂️ **Advanced Organization:**
  * Categorize entries with `#tags`.
  * Instantly search your entire vault using the `Ctrl + K` omnibar shortcut.
  * Sort by recently updated, created, or alphabetically.
* 📊 **Journaling Analytics:** Built-in mood tracking, real-time word count, and reading time estimations.
* 🎨 **Highly Customizable:** Toggle UI appearance, tweak accent colors, and enjoy a responsive sidebar tailored to your workflow.
* 📦 **Portable Vaults:** Easily export your entire encrypted database as a single backup file to migrate between devices safely.

---

## 🔐 Security Architecture

Mayborg Vault does not use a backend database. All data is stored in your browser's `localStorage` or `IndexedDB`. 

1. **Key Derivation:** When you create your vault, your master password is run through a Key Derivation Function (PBKDF2) alongside a unique salt to generate a robust cryptographic key.
2. **Encryption:** Your data is encrypted using **AES-GCM** (Advanced Encryption Standard with Galois/Counter Mode) via the browser's native, highly optimized `window.crypto.subtle` API.
3. **Data Residency:** The unencrypted data exists *only* in your browser's active memory (RAM). The moment the tab is closed, the unencrypted data vanishes.

⚠️ **WARNING:** Because this is a zero-knowledge system, **there is no "Forgot Password" feature**. If you lose your password, your vault is permanently inaccessible.

---

## 🚀 Quick Start / Usage Guide

Because Mayborg Vault is serverless, you can start using the [Live Web App](https://mayborg121.github.io/journal/) immediately. No sign-up required.

### Initial Setup
1. Open the application.
2. Click **Create your secure vault**.
3. Enter a strong, memorable password. *Do not lose this password.*
4. You are now inside your secure workspace.

### Writing & Organizing
* **Create a Note:** Click the `+` icon in the sidebar under **Quick create**.
* **Formatting:** Highlight text to apply styles, or use the top toolbar dropdown to change block types (e.g., Code block, Quote).
* **Metadata:** Use the dropdown at the top of your note to track your mood for that entry. Append `#tags` at the bottom of the editor to group related notes automatically.
* **Search:** Press `Ctrl + K` (or `Cmd + K` on Mac) to bring up the global search palette and instantly jump between notes.

### Backups & Syncing (Crucial)
**Your vault is tied to your current browser.** Clearing your browser's cache/site data will delete your vault. To prevent data loss:

1. Click your user profile icon (bottom left) to open the **Settings** panel.
2. Navigate to **Vault and backups**.
3. Download your encrypted vault backup file. 
4. **To Restore/Sync:** On a new device or browser, navigate to the app, select **Open imported vault**, upload your backup file, and enter your original password.

---

## 💻 Local Development

Want to run Mayborg Vault locally, audit the code, or contribute? Setup is incredibly simple since it relies on native web technologies.

**Prerequisites:**
* Git
* A local web server (e.g., VS Code Live Server, or Python's `http.server`)

**Installation:**
```bash
# 1. Clone the repository
git clone [https://github.com/mayborg121/journal.git](https://github.com/mayborg121/journal.git)

# 2. Navigate into the project directory
cd journal

# 3. Serve the application
# If using Python:
python3 -m http.server 8000
# Alternatively, open index.html using the VS Code Live Server extension.

# 4. Open your browser and navigate to:
http://localhost:8000
