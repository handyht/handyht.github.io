================================================================
  HANDYHT PORTFOLIO — MAINTENANCE GUIDE
================================================================

  Tech:      Pure HTML + CSS + vanilla JavaScript (no frameworks)
  Theme:     Apple-style dark/light mode


================================================================
  FILE OVERVIEW
================================================================

  index.html          Homepage (hero intro, featured work, motion teaser)
  photography.html    Photo gallery with category filters + lightbox
  videography.html    Coming soon placeholder (ready for video content)
  contact.html        About me, services, and contact links
  styles.css          All styling for the entire site (shared across pages)

  images/
    hero/             Profile photo for the homepage polaroid
    about/            Portrait photo for the About Me section
    photography/
      engagements/    Engagement shoot photos
      graduations/    Graduation shoot photos
      moments/        Candid and event photos


================================================================
  COMMON TASKS
================================================================


--- Adding a New Photo ---

  1. Drop your image file into the correct subfolder:
       images/photography/engagements/
       images/photography/graduations/
       images/photography/moments/

  2. Open photography.html in a text editor

  3. Find the category section (look for the comment like
     <!-- ── Engagements ── -->)

  4. Copy-paste this block right after the last item in that category:

       <div class="gallery-item" data-cat="engagements">
         <img src="images/photography/engagements/your-photo.jpg" alt="Engagement">
       </div>

  5. Change "data-cat" to match: engagements / graduations / moments
  6. Change the "src" path to point to your image file
  7. Save and refresh the browser


--- Adjusting Photo Cropping ---

  Photos are displayed in a 3:4 portrait crop. If a photo's
  subject is cut off, add an object-position style to shift the crop:

       <img src="..." alt="..." style="object-position: left">

  Options: left, right, top, bottom, center (default)
  Or use percentages: style="object-position: 25% center"

  Example in the code: graduation-4.jpg uses object-position: left


--- Changing Featured Photos (Homepage) ---

  1. Open index.html
  2. Find the "FEATURED WORK" section comment
  3. Swap the <img> src paths with whatever photos you want to feature


--- Updating Profile / Portrait Photos ---

  Homepage polaroid:  Replace images/hero/profile.jpg
  About Me portrait:  Replace images/about/portrait.jpg

  The file names must stay the same, or update the path in the HTML:
    - index.html → look for "background-image: url('images/hero/profile.jpg')"
    - contact.html → look for "background-image: url('images/about/portrait.jpg')"


--- Updating Contact Links ---

  1. Open contact.html
  2. Find the "CONTACT" section comment
  3. Change the href values:
       Email:     href="mailto:your@email.com"
       Instagram: href="https://instagram.com/handyht"
       YouTube:   href="https://youtube.com/@handyht"


--- Adding a New Category ---

  1. In photography.html, add a new filter button:
       <button class="cat-btn" onclick="filterCat('newcategory')">New Category</button>

  2. Add gallery items with the matching data-cat:
       <div class="gallery-item" data-cat="newcategory">
         <img src="images/photography/newcategory/photo.jpg" alt="Description">
       </div>

  3. Create the folder: images/photography/newcategory/


--- Removing a Photo ---

  Delete the entire <div class="gallery-item">...</div> block
  for that photo from photography.html. You can also delete the
  image file from the images/ folder to save space.


--- Updating SEO Meta Tags ---

  Each page has these SEO tags in the <head> section:

    <meta name="description" content="...">     Google search snippet
    <meta property="og:title" content="...">     Social media title
    <meta property="og:description" content="">  Social media description
    <meta property="og:image" content="...">     Social media preview image
    <meta name="twitter:card" content="...">     Twitter/X card format

  To update: open any page's <head> and edit the content values.

  Once you have a domain, update the og:image paths to full URLs:
    Before:  content="images/hero/profile.jpg"
    After:   content="https://yourdomain.com/images/hero/profile.jpg"

  Recommended additions when ready:
    - Add a favicon.ico file to the root folder
    - Add <link rel="canonical" href="https://yourdomain.com/page">
      to each page once your domain is set


--- Updating the Email Subject Line ---

  The email link on the contact page pre-fills the subject line.
  To change it, open contact.html and find the mailto link:

    href="mailto:handyht@gmail.com?subject=Inquiry%20%E2%80%94%20HANDYHT"

  Edit the text after "subject=" (use %20 for spaces).


--- Changing Site Colors ---

  Open styles.css and find section "1. THEME VARIABLES" near the top.
  Each color has a comment explaining what it does:

    --bg:      Main background
    --bg2:     Secondary background (featured sections)
    --card:    Card / panel background
    --t1:      Primary text
    --t2:      Secondary text (subtitles)
    --t3:      Muted text (hints)
    --blue:    Accent color (link hover)
    --border:  Borders and dividers

  There are two sets: dark mode (:root) and light mode (html.light).
  Update both to keep things consistent.


--- Adding Videos (When Ready) ---

  1. Open videography.html
  2. Delete the "Coming Soon Placeholder" block
     (everything inside <div class="coming-soon">)
  3. Add your video embeds or a gallery grid similar to photography.html
  4. If you need video-specific CSS, add it to styles.css


================================================================
  HOW THE SITE WORKS
================================================================

  Navigation:     Fixed bar at the top with frosted-glass blur.
                  On mobile (<768px) it collapses into a hamburger menu.

  Theme Toggle:   The moon/sun switch saves your preference to
                  localStorage, so it remembers across visits.

  Gallery Grid:   CSS Grid with 3 columns (2 on tablet, 1 on phone).
                  Each photo is cropped to a 3:4 portrait ratio.

  Filters:        JavaScript shows/hides gallery items by matching
                  the data-cat attribute on each item.

  Lightbox:       Click any gallery photo to view it full-screen.
                  Click anywhere or the X button to close.

  Flash Effect:   Homepage plays a white camera flash animation
                  on first load, then reveals the hero content.

  Fade-In:        Sections with class "fade-in" start invisible
                  and slide up when scrolled into view.

  SEO:            Every page includes meta descriptions, Open Graph
                  tags (Facebook/LinkedIn/iMessage previews), and
                  Twitter Card tags for rich social media sharing.
                  All gallery images use descriptive alt text with
                  "HANDYHT" branding for image search visibility.

  Email Link:     The contact page email link pre-fills the subject
                  line with "Inquiry — HANDYHT" so incoming messages
                  are easy to identify.


================================================================
  IMAGE SIZE TIPS
================================================================

  Raw camera photos (5-20 MB) are too large for web. Resize before adding:

  Recommended sizes:
    Hero / Featured:   max 1920px wide,  under 500 KB
    Gallery photos:    max 1200px wide,  under 200 KB
    Thumbnails:        max 600px wide,   under 80 KB

  Quick resize option (free):
    - Squoosh.app (drag and drop in browser)
    - IrfanView (Windows): File → Batch → set max width 1200, quality 85%

  If a single image is over 500 KB, it's too big for web.


================================================================
  HOSTING
================================================================

  This is a static site (no server needed). You can host it for free:

    - Drag the entire folder to Netlify (netlify.com/drop)
    - Push to GitHub and enable GitHub Pages
    - Upload to any web host that supports static files


================================================================
  FILE STRUCTURE REFERENCE
================================================================

  handyht-portfolio/
  ├── index.html              Homepage
  ├── photography.html        Photo gallery
  ├── videography.html        Video page (coming soon)
  ├── contact.html            About & contact
  ├── styles.css              All styles (shared)
  ├── readme.txt              This file
  └── images/
      ├── hero/
      │   └── profile.jpg     Homepage polaroid photo
      ├── about/
      │   └── portrait.jpg    About Me portrait
      └── photography/
          ├── engagements/    Engagement photos
          ├── graduations/    Graduation photos
          └── moments/        Moment / event photos
