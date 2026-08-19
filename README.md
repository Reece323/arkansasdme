# Arkansas DME — arkansasdme.com

Single-page website for **Al Morvin, FAA Designated Mechanic Examiner**, Jonesboro / Northeast Arkansas.
Phone: 501-617-1220 · Email: info@arkansasdme.com

## Files

| File | What it does |
|---|---|
| `index.html` | The entire website — HTML, CSS and JS in one file |
| `images/` | Al's photos (already resized and compressed for the web) |
| `CNAME` | Tells GitHub Pages the custom domain is `arkansasdme.com` |
| `robots.txt` | Lets Google crawl the site |
| `sitemap.xml` | Sitemap you submit to Google Search Console |
| `favicon.svg` | The little icon in the browser tab |
| `.nojekyll` | Stops GitHub from running Jekyll on the files |

---

## Step 1 — Set up email

The site lists **info@arkansasdme.com**. That address doesn't exist yet — you have to
create it. Two ways, pick one:

### Option A — Google Workspace (~$8.40/mo, easiest)

Sign up at <https://workspace.google.com>, choose **Business Starter**, and enter
`arkansasdme.com` as your domain. Google walks you through adding the MX records at
GoDaddy. You get `info@arkansasdme.com` as a real mailbox that looks and works exactly
like Gmail — send, receive, phone app, the works. About $100/year.

### Option B — Cloudflare Email Routing (free, receive-only)

Free forwarding: mail to `info@arkansasdme.com` lands in Al's existing personal Gmail.
Set it up at <https://dash.cloudflare.com> under *Email → Email Routing*. Requires moving
the domain's DNS to Cloudflare (free), which also works fine for the GitHub Pages setup
in Step 6 — just use Cloudflare's DNS panel instead of GoDaddy's and leave the proxy
turned **off** (grey cloud) so GitHub can issue the SSL certificate.

⚠️ **The catch:** forwarding only handles *incoming* mail. When Al replies, it goes out
from his personal Gmail address, not `info@arkansasdme.com`. Making replies come *from*
the custom address needs a separate free SMTP relay (Brevo or similar) wired into
Gmail's "Send mail as" — doable, but fiddly.

**My recommendation:** Option A. It's one checkride's worth of money for the year, and
replies coming from `info@arkansasdme.com` is most of the point of having it.

> Changed your mind on the address? Search `index.html` for `info@arkansasdme.com` —
> it appears in 3 places (schema markup, the contact card, and the footer).

You'll also want a plain Google account for **Google Business Profile** in Step 7.
A Workspace account works for that too.

## Step 2 — Domain ✅ DONE

**arkansasdme.com** is registered on GoDaddy. Nothing to do here — the `CNAME` file
in this folder is already set to it. Skip to Step 3.

> Don't buy GoDaddy hosting, their website builder, or their email plan. You don't
> need any of it — GitHub hosts the site for free and Gmail handles the email.

## Step 3 — Create the GitHub repository

1. Sign up / log in at <https://github.com>
2. Click the **+** in the top right → **New repository**
3. Repository name: `arkansasdme`
4. Set it to **Public** (GitHub Pages needs public on free accounts)
5. **Do not** check "Add a README" — this folder already has one
6. Click **Create repository**

## Step 4 — Upload the files

On the new empty repo page, click **uploading an existing file**.

Unzip this folder, then **drag in the contents of the folder — not the folder itself**.
The repo should end up looking like:

```
index.html
README.md
CNAME
robots.txt
sitemap.xml
favicon.svg
.nojekyll
images/al-morvin.jpg
images/al-cockpit.jpg
images/hangar.jpg
```

⚠️ `index.html` **must sit at the top level** of the repo, not inside a subfolder.
⚠️ `.nojekyll` starts with a dot and may be hidden — on Mac press `Cmd+Shift+.` in Finder to show it.

Click **Commit changes**.

## Step 5 — Turn on GitHub Pages

1. In the repo, go to **Settings** → **Pages** (left sidebar)
2. Under *Build and deployment* → *Source*, choose **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)** → **Save**
4. Wait 1–2 minutes. The site goes live at `https://YOURUSERNAME.github.io/arkansasdme/`

Load that URL and confirm it looks right before moving on.

## Step 6 — Point the domain at GitHub

**In GoDaddy** — My Products → your domain → **DNS** → **Manage Zones**.

Delete any existing `A` records for `@` and the default `CNAME` for `www`, then add these:

| Type | Name | Value | TTL |
|---|---|---|---|
| A | @ | `185.199.108.153` | 1 hour |
| A | @ | `185.199.109.153` | 1 hour |
| A | @ | `185.199.110.153` | 1 hour |
| A | @ | `185.199.111.153` | 1 hour |
| CNAME | www | `YOURUSERNAME.github.io` | 1 hour |

(Replace `YOURUSERNAME` with the actual GitHub username. The trailing dot GoDaddy adds is fine.)

**Back in GitHub** — Settings → Pages → *Custom domain* → type `arkansasdme.com` → **Save**.
Once the check passes (can take 15 min to a few hours), tick **Enforce HTTPS**.

DNS changes usually go live in under an hour but can take up to 48.

## Step 7 — Get found for "DME near me"

This is the part that actually drives calls. The website alone won't rank — the
Google Business Profile is what puts him in the map results.

1. **Google Business Profile** — <https://business.google.com>
   Create a profile for "Arkansas DME — Al Morvin, Designated Mechanic Examiner."
   Category: *Aviation training institute* or *Flight school* (closest available).
   Set a **service area** (Jonesboro + surrounding counties/states) instead of a street
   address if he doesn't want his home address public. Add the website, phone,
   hours, and upload these same three photos. Google mails a verification postcard.
2. **Google Search Console** — <https://search.google.com/search-console>
   Add `arkansasdme.com`, verify, and submit `https://arkansasdme.com/sitemap.xml`.
3. **Free aviation directories** — get listed on FAA-adjacent and local sites:
   AOPA, the local airport's website (KJBR), any A&P school he works with, and
   state aviation association listings. Each link helps.
4. **Ask every applicant for a Google review** after they pass. Reviews are the single
   biggest factor in local "near me" rankings.

## Making changes later

Edit `index.html` directly on GitHub (open the file → pencil icon → edit → commit).
The live site updates in about a minute.

Things you'll most likely want to change:
- Phone number: search for `5016171220` and `501-617-1220`
- Email: search for `info@arkansasdme.com`
- Airports listed in the Service Area section
- The FAQ answers
