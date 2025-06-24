# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Nino's Trip** is a Korean travel guide web application built with Flask that provides family-friendly location recommendations across multiple categories. The application serves as a PWA (Progressive Web App) called "NeStory".

## Technology Stack

- **Backend**: Flask (Python web framework)
- **Database**: Multiple SQLite databases for different content categories
- **Frontend**: Vanilla JavaScript with HTML/CSS (no build process)
- **Deployment**: Configured for Vercel deployment

## Development Commands

### Local Development
```bash
python app.py
```
Runs the Flask development server on localhost:5000

### Deployment
The project is configured for Vercel deployment with:
- `vercel.json` - Vercel configuration
- Simplified `requirements.txt` with only Flask dependency

## Database Architecture

The application uses multiple SQLite databases in the `/data` directory:
- `event.db` - Monthly events and activities
- `nino-trip.db` - Family trip recommendations  
- `forest.db` - Forest/nature locations
- `cafe.db` - Cafe recommendations
- `kids_restaurant.db` - Kid-friendly restaurants
- `culture_center.db` - Cultural centers and activities
- `activity.db` - Various activities
- `db.sqlite3` - Main database for user inquiries

## Application Structure

### Main Files
- `app.py` - Flask application with route handlers and database functions
- `templates/index.html` - Main application interface with tabbed navigation
- `templates/admin.html` - Administrative interface (password: 0819)
- `static/script.js` - Client-side JavaScript for tab switching
- `static/style.css` - Dark theme responsive styling

### Key Features
- Multi-category travel guide with tabbed interface
- Admin panel for managing user inquiries
- REST API endpoints for inquiry management
- PWA capabilities with offline support
- Google Analytics integration

### API Endpoints
- `POST /api/inquiries` - Submit new inquiry
- `GET /api/inquiries` - Get all inquiries
- `PATCH /api/inquiries/<id>` - Update inquiry response
- `DELETE /api/inquiries/<id>` - Delete inquiry
- `GET/POST /admin` - Admin authentication and interface

## Data Processing

Database functions include content formatting (converting dash-separated items to line breaks) before rendering. Each category has its own data retrieval function that formats content appropriately for display.