================================================================================
   ANIMATED TERMINAL GITHUB PROFILE README — TEMPLATE & SETUP GUIDE
================================================================================

This template gives you an elite, monochrome terminal-style GitHub profile:
  [1] Self-Typing Monochrome ASCII Portrait (with blinking terminal cursor)
  [2] Extruded 3D ASCII Wordmark (smooth rocking animation, matched height)
  [3] Live Pop-and-Flash Contribution Heatmap (borderless, animated boxes)
  [4] Automated GitHub Action (refreshes contribution stats daily on its own)

Everything runs inside pure, self-hosted SVGs embedded in your README.
Zero third-party paid services, zero API rate limits, zero broken images.

================================================================================
TABLE OF CONTENTS
================================================================================
  1. Quick Overview & Folder Structure
  2. Method 1: The AI Auto-Pilot Setup (Recommended ~ 2 Mins)
  3. Method 2: Manual Step-by-Step Setup
  4. How to Push to GitHub & Go Live
  5. Enabling Daily Auto-Updates (GitHub Actions)
  6. Tuning Cheatsheet & Customization

================================================================================
1. FOLDER STRUCTURE
================================================================================
  PROMPT.md                 <- Ready-to-use prompt for AI coding tools
  README.md                 <- The rendered profile that shows on GitHub
  README.txt                <- This step-by-step guide
  requirements-local.txt    <- Python deps for 1-time local image & art prep
  .github/workflows/
    update-profile-art.yml  <- Daily automation to refresh contribution stats
  scripts/
    prep_photo.py           <- Background removal (rembg) + CLAHE contrast
    make_ascii_svg.py       <- Photo to typing terminal ASCII SVG
    make_wordmark_svg.py    <- 3D extruded rocking ASCII wordmark SVG
    generate_streak_svg.py  <- Animated pop-and-flash contribution heatmap SVG
    fetch_contributions.py  <- Scrapes real GitHub contribution data
    requirements.txt        <- Lightweight deps needed by daily GitHub Action

================================================================================
2. METHOD 1: THE AI AUTO-PILOT SETUP (RECOMMENDED - 2 MINUTES)
================================================================================
If you use an AI coding assistant (Cursor, Claude Code, Antigravity, Windsurf):

1. Open this folder in your AI editor.
2. Put a portrait photo of yourself into this folder (e.g. `photo.png` or `photo.jpg`).
3. Open `PROMPT.md`.
4. Fill in the [USER CONFIGURATION] block with your:
   - GitHub username
   - Full name & tagline
   - Wordmark text (e.g. your first name in ALL-CAPS)
   - Photo file path
   - Social links (Portfolio, LinkedIn, X, Instagram)
5. Copy the prompt and paste it into your AI assistant.
6. The assistant will run all scripts, tune the art, generate the SVGs, and 
   assemble your `README.md` automatically!

================================================================================
3. METHOD 2: MANUAL STEP-BY-STEP SETUP
================================================================================
If you prefer running the commands yourself:

--- Step A: Install Dependencies ---
Ensure Python 3.10+ is installed, then run:
  pip install -r requirements-local.txt
  pip install -r scripts/requirements.txt

--- Step B: Generate Your ASCII Portrait ---
1. Place a portrait photo of yourself in this folder (e.g. `photo.png`).
2. Run background removal and local contrast boost:
     python scripts/prep_photo.py photo.png source-prepped.png
   (This cuts out the background and enhances facial contours with CLAHE).
3. Open `scripts/make_ascii_svg.py` and update lines 106 & 141 with your name:
   - Change `harshit@github` to `yourusername@github`
   - Change `Harshit Yadav` to your name
4. Generate the animated ASCII portrait SVG:
     python scripts/make_ascii_svg.py source-prepped.png avi-ascii.svg
   (Tip: To inspect the static final frame, run with $env:STATIC="1" on Windows
    or STATIC=1 on macOS/Linux).

--- Step C: Generate Your 3D ASCII Wordmark ---
1. Open `scripts/make_wordmark_svg.py`:
   - Set `TEXT = "YOURNAME"` (e.g. "HARSHIT", "ALEX", "SARAH")
2. Generate the 3D rocking wordmark:
     python scripts/make_wordmark_svg.py --mode rock --out wordmark.svg
   The script is pre-tuned so the wordmark height (~385px) perfectly matches
   your portrait window beside it!

--- Step D: Generate Your Animated Contribution Heatmap ---
Run the heatmap generator with your GitHub username:
  python scripts/generate_streak_svg.py YOUR_USERNAME contrib-heatmap.svg
This creates a borderless, transparent animated SVG with pop-and-flash effects.

--- Step E: Customize README.md ---
Open `README.md` and replace:
  - Header prompts: change `harshit@github` to `yourusername@github`
  - Name and tagline: `Fullstack Developer · AI Builder`
  - Badges: replace the URLs and usernames with your own links.

================================================================================
4. HOW TO PUSH TO GITHUB & GO LIVE
================================================================================
GitHub has a special feature: if you create a repository named EXACTLY your 
GitHub username, GitHub displays its `README.md` right on your public profile!

1. Go to https://github.com/new
2. Enter your repository name: EXACTLY your GitHub username (e.g. `hxrshityadav`)
3. Set visibility to: PUBLIC
4. Do NOT check "Add a README file" (we already have one).
5. Click "Create repository".

Now, in your local folder terminal, run:
  git init
  git add .
  git commit -m "feat: animated terminal profile readme"
  git branch -M main
  git remote add origin https://github.com/YOUR_USERNAME/YOUR_USERNAME.git
  git push -u origin main --force

================================================================================
5. ENABLING DAILY AUTO-UPDATES (GITHUB ACTIONS)
================================================================================
The workflow `.github/workflows/update-profile-art.yml` automatically fetches
your GitHub contribution count and updates your graph every single day.

To activate it:
1. In your GitHub repository, click "Settings" (top menu).
2. On the left sidebar, click "Actions" -> "General".
3. Scroll down to "Workflow permissions".
4. Select the radio button: "Read and write permissions".
5. Click "Save".
6. Go to the "Actions" tab in your repo:
   - Click "Update profile art" in the left list.
   - Click the "Run workflow" button on the right.
   - Click "Run workflow".

Your profile art will now refresh automatically every day at 02:00 UTC!

================================================================================
6. TUNING CHEATSHEET & CUSTOMIZATION
================================================================================
| What you want to adjust       | Where to change it                            |
| ----------------------------- | --------------------------------------------- |
| Portrait lighter / darker     | `CONTRAST`, `GAMMA`, `WHITE_FLOOR` in         |
|                               | `scripts/make_ascii_svg.py`                   |
| Portrait typing speed         | `ROW_DUR`, `STAGGER` in `make_ascii_svg.py`   |
| Wordmark font / text          | `TEXT`, `FONT_PATH` in `make_wordmark_svg.py` |
| Wordmark height matching      | `ROW_MARGIN` in `make_wordmark_svg.py`        |
| Social links & badges         | URLs and colors inside `README.md`            |

================================================================================
Done! Visit https://github.com/YOUR_USERNAME to admire your new profile!
================================================================================
