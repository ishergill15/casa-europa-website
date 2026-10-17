Casa Europa — self-hosted website
==================================

This is a self-contained site: index.html + an avatars/ folder of guest
review photos. All CSS and JS are inline in index.html — no build step,
no server, no dependencies beyond what's in this folder.

HOW TO HOST IT — RECOMMENDED: NETLIFY
---------------------------------------
1. Go to app.netlify.com and sign in (or create a free account).
2. Drag this whole folder (index.html + avatars/) onto the "Sites" page
   where it says "Drag and drop your site output folder here."
   Netlify deploys it instantly to a random *.netlify.app URL.
3. Rename the site (optional): Site settings -> Site details -> Change
   site name -> something like "casa-europa" (gives you casa-europa.netlify.app).
4. Point casaeuropa.in at it (registered via BigRock):
   - Go to Site settings -> Domain management -> Add a domain -> enter
     casaeuropa.in -> Netlify will show you either:
       a) nameservers to switch your domain to (easiest — Netlify then
          manages all DNS for you), or
       b) specific DNS records to add at BigRock (an A record pointing
          at Netlify's load balancer IP, plus a CNAME for www).
   - At BigRock: log in -> Manage Orders / My Orders -> select
     casaeuropa.in -> Manage DNS / Nameservers. Either switch the
     nameservers to Netlify's (Netlify DNS tab shows two, e.g.
     dns1.p0X.nsone.net) or, to keep BigRock's own DNS, add/edit the
     A record for "@" to 75.2.60.5 and a CNAME record for "www" to your
     Netlify subdomain (e.g. casa-europa.netlify.app) instead.
   - HTTPS (the padlock) is issued automatically by Netlify once the
     domain is connected — no extra steps needed. DNS changes can take
     anywhere from a few minutes to ~24 hours to fully propagate.
5. Every time the site needs updating, just drag the updated folder onto
   the same Netlify site again (Deploys tab -> drag and drop) — it
   replaces the live version with no downtime.

ENQUIRY FORM — WIRED FOR NETLIFY FORMS
-----------------------------------------
The booking enquiry form is already set up to work with Netlify Forms:
when the site is deployed on Netlify, submissions are captured silently
(no email app pop-up) and Netlify emails them to the account owner by
default. To choose exactly who gets notified, or to add a Slack/webhook
notification instead, go to: Site settings -> Forms -> Form notifications.
Submitted entries also always collect under the Forms tab in the Netlify
dashboard, so nothing is lost even if a notification email fails.

If the site is ever hosted somewhere other than Netlify, the form
automatically falls back to opening a pre-filled email to:
   casaeuropagoa@gmail.com
(set near the bottom of index.html as OWNER_EMAIL — change this to
whichever address enquiries should land at.)

CONNECTING GITHUB TO NETLIFY (optional, for auto-deploy on push)
---------------------------------------------------------------------
1. Create a GitHub repo (e.g. "casa-europa-website") and push this
   folder's contents to it (index.html, avatars/, README.txt).
2. In Netlify: Sites -> Add new site -> Import an existing project ->
   connect to GitHub -> authorize Netlify to access your GitHub account
   -> pick the casa-europa-website repo.
3. Build settings: leave "Build command" blank and set "Publish
   directory" to "." (this is a static site, nothing to build).
4. Deploy. From now on, every time you push a change to that GitHub
   repo's main branch, Netlify automatically redeploys the live site —
   no more manual drag-and-drop needed.
5. If you already deployed the site by dragging the folder (step 2
   under HOW TO HOST IT above) and want to switch that same site to
   GitHub-based deploys instead, go to Site settings -> Build & deploy
   -> Link repository, and connect it there — your domain and settings
   carry over, you don't need to start a new site.

OTHER HOSTING OPTIONS (if not using Netlify)
-----------------------------------------------
- Vercel (free tier): similar drag-and-drop flow, but it doesn't have an
  equivalent to Netlify Forms, so the enquiry form would use the mailto
  fallback instead of silent submission.
- Any standard web host / cPanel: upload index.html and the avatars/
  folder to the site's root (e.g. public_html/) via FTP or the file
  manager. Also uses the mailto fallback.
- GitHub Pages: an alternative to Netlify Pages hosting itself, but it
  doesn't support Netlify Forms, so the enquiry form would fall back to
  mailto. Netlify (with GitHub connected as the source, per above) gets
  you both version history AND working form submissions.

DOMAIN — casaeuropa.in (registered via BigRock)
---------------------------------------------------
Already registered by Indi through BigRock. See the "Point casaeuropa.in
at it" step above for exactly how to connect it to Netlify.

STILL TO DO
------------
- Replace the placeholder coloured tiles with real hero/gallery/bedroom
  photos (send the actual image files and they'll be embedded directly).
- Confirm/correct the wording on the testimonial quotes in the Reviews
  section — these were transcribed from your review screenshots.
- Confirm the map pin is exactly right (currently a Google Maps embed
  searching "Casa Europa, Calangute, Goa" — can be swapped for your exact
  coordinates/pin if you send them).
- Fill in the standard-season tiered rate breakdown if you want more detail
  than the current min–max range.
