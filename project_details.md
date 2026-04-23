# Vinyl Muse – Project Details

# Summary
Vinyl Muse is a web-based application designed to help users manage, explore, and interact with their personal record collections. It is built for collectors who want more than a static list—offering dynamic filtering, randomized selection, playlist generation, and lightweight analytics.
The application solves a common problem for collectors: decision fatigue. When faced with a large collection, it becomes difficult to decide what to listen to. Vinyl Muse addresses this by combining structured organization (search, filters) with discovery tools (random selection, playlists), while also tracking listening behavior over time.

# Product / User Problem
Browsing a record collection—especially a large one—is often inefficient and uninspiring when done through static lists or spreadsheets. Common issues include:
- Difficulty narrowing down options across multiple attributes (genre, era, artist) 
- Lack of meaningful discovery within one’s own collection 
- No lightweight way to track listening habits 
- Friction in updating and maintaining the collection
  
Vinyl Muse addresses these issues by providing:
- Multi-dimensional filtering (genre, decade, etc.) 
- Instant search across artist and album fields 
- Randomized selection to encourage rediscovery 
- Playlist generation based on current filters 
- Play tracking to reflect actual listening behavior 
The result is a tool that turns a static collection into an interactive experience.

# Application Design & Functionality
Record Management
Users can add, edit, and delete records with structured fields including artist, album, genre, release year, tags, and cover art. 
- Duplicate detection prevents redundant entries 
- Cover art can be uploaded or automatically fetched 
- Play counts are tracked and editable 
Search & Sorting
- Real-time search filters records by artist or album 
- Column-based sorting supports multiple attributes (artist, album, genre, year, play count) 
Dynamic Filtering
- Multi-select filters for Genre and Decade 
- Interdependent filtering logic updates available options based on selections 
- “Select All” and “Clear Filters” controls improve usability
Randomizer & Playlist Mode
- Select a single random record or generate a playlist (1–5 records) 
- Filters directly influence selection pool 
- Recently selected or confirmed records are temporarily excluded to improve variety 
- Confirmation system increments play counts and tracks listening behavior 
Play Tracking System
- Play counts are not simple counters - they are event-based 
- Each play is stored as a record, allowing reversible actions and better tracking logic
Metrics Page
- Collection distribution by genre and decade 
- Play counts by genre 
- Most played records 
- Interactive charts allow filtering other visuals by clicking categories
Image Handling
- Automatic cover art retrieval from multiple sources (iTunes, MusicBrainz, Deezer) 
- Fallback logic progressively simplifies search queries 
- Images are downloaded and cached locally for performance and reliability

# Technical Implementation
Backend:
- Python with Flask for routing and application logic 
- SQLite database for persistence 
- SQLAlchemy ORM for data modeling and queries
  
Data Model
Core entities include:
- User: authentication and ownership of records 
- Record: collection entries with metadata and play tracking 
- PlayEvent: granular tracking of listening activity 
Application Logic:
- Filter queries dynamically built using SQLAlchemy 
- Session storage used to persist UI state (filters, selections, scroll position) 
- AJAX endpoints enable partial updates (e.g., play count adjustments) without full page reload

Frontend:
- HTML/CSS templates with responsive design 
- Vanilla JavaScript for interactivity (search, filtering, UI updates) 
- Chart.js for metrics visualization

Hosting:
- Deployed on PythonAnywhere 
- Server-side rendering with lightweight client-side enhancements 

# UX / Design Considerations
Usability:
- Designed around minimizing friction in common actions (search, filter, select) 
- Immediate visual feedback for user actions (e.g., play count updates) 
- Persistent UI state (filters, scroll position) prevents disruption 
Filtering Behavior:
- Empty selections are treated as “no filter” rather than excluding all results 
- Filter options dynamically update based on current selections 
- Counts displayed to show how many options are active vs. total 
Layout & Responsiveness:
- Desktop: sidebar filters + table layout 
- Mobile: collapsible filters + stacked card-style records 
- Metrics page adapts to mobile with scrollable, resized charts 
Interaction Design:
- Increment/decrement play count buttons with constraints (e.g., no negative values) 
- Confirmation actions toggle state instead of requiring separate undo flows 
- Randomizer designed to avoid repetition and encourage discovery 

# Analytics Component
While not the primary focus of the application, Vinyl Muse includes a lightweight analytics layer:
- Distribution of collection by genre and decade 
- Aggregated play counts by genre 
- Identification of most played records 
- Interactive filtering between charts 
This component demonstrates:
- Data aggregation and transformation 
- Visual encoding of categorical distributions 
- Basic interactivity between visual elements 
The analytics layer is intentionally scoped as a supporting feature rather than the core product.

# Potential Extensions
Short-Term
- Tag-based filtering and categorization 
- Improved filter interactions (partial page updates instead of full reloads) 
- Expanded metrics (e.g., listening trends over time) 
Medium-Term
- More advanced analytics (top artists, listening patterns, time-based insights) 
- User-defined playlists and saved filter sets 
- Enhanced image handling (manual override, correction UI) 
Long-Term
Recommendation system based on listening behavior 
