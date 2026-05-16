# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Run development server (port 5001, debug mode)
python app.py

# Run tests
pytest

# Install dependencies
pip install -r requirements.txt
```

## Architecture

**Spendly** is a Flask-based personal expense tracker targeting Indian users (INR currency). It uses server-side rendering with Jinja2 templates — no SPA framework, no separate API layer.

- **Backend:** `app.py` — all Flask routes in one file. Routes render HTML templates directly; no JSON API endpoints exist yet.
- **Templates:** `templates/` — Jinja2 with inheritance from `base.html` (navbar, footer, CSS links).
- **Database:** SQLite (`expense_tracker.db`, gitignored). Connection logic lives in `database/db.py` — currently a stub waiting to be implemented (`get_db()`, `init_db()`, `seed_db()`).
- **Static:** `static/css/style.css` (global), `static/css/landing.css` (landing page only), `static/js/main.js` (empty placeholder).

## Project State

The scaffold is partially built — UI and public pages are complete, backend logic is not:

| Step | Feature | Status |
|------|---------|--------|
| 1 | Database setup (`database/db.py`) | Stub only |
| 2–3 | User registration & login (session-based) | Routes exist, handlers missing |
| 4 | Profile page | Placeholder |
| 7–9 | Expense CRUD (add, edit, delete) | Placeholder routes |

When implementing new steps, follow the existing route stubs in `app.py` and wire them to `database/db.py`.

## Key Conventions

- **Auth:** Session-based (no JWT). Flask `session` object expected for user state.
- **Currency:** INR (₹) throughout — do not add multi-currency support.
- **CSS variables** are defined at the top of `style.css`; use them for colors (primary `#1a472a`, accent `#c17f24`).
- **Fonts:** DM Serif Display (headings), DM Sans (body) — loaded via Google Fonts in `base.html`.
- **`.env`** is gitignored; any secrets (secret key, etc.) go there.
