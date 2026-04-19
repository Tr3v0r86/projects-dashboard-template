# Special Projects Dashboard — Template

A single-file HTML project management dashboard you can host for free on GitHub in about 10 minutes. No coding experience required for basic setup. No servers, no databases, no monthly fees.

**[Live demo →](https://tr3v0r86.github.io/Special-Projects-Dashboard/)**

---

## What does it do?

- Tracks your active projects in a table (desktop) and card layout (mobile)
- Lets you set priorities, log weekly progress notes, and track completion percentage
- Generates a live shareable link that colleagues can view in read-only mode
- Optionally requires Google sign-in to restrict who can see the live link
- Optionally connects to Todoist to create tasks from any project

---

## What you'll need

- A **GitHub account** (free) — [sign up here](https://github.com/signup)
- A **web browser** (Chrome, Safari, Firefox, Edge — all work)
- About **10 minutes**

That's it. No software to install, no command line required for the basic setup.

---

## Step 1 — Fork this repository

"Forking" makes your own personal copy of this project in your GitHub account.

1. Make sure you're signed in to GitHub
2. Click the **Fork** button at the top right of this page
3. On the next screen, click **Create fork**

You now have your own copy at `https://github.com/YOUR-USERNAME/Special-Projects-Dashboard`

---

## Step 2 — Enable GitHub Pages (free hosting)

GitHub Pages publishes your `index.html` file as a live website for free.

1. In your forked repository, click **Settings** (the gear icon in the top nav)
2. In the left sidebar, click **Pages**
3. Under **Branch**, change the dropdown from `None` to `main`
4. Click **Save**

After about 60 seconds, your dashboard will be live at:
```
https://YOUR-USERNAME.github.io/Special-Projects-Dashboard/
```

GitHub will show you the exact URL once it's deployed — look for the green "Your site is live" banner on the Pages settings screen.

---

## Step 3 — Customise with your own details

Open `index.html` in GitHub's built-in editor:

1. In your repository, click on **`index.html`**
2. Click the **pencil icon** (Edit this file) in the top right

Scroll down until you find this section near the top of the `<script>` tag:

```js
/* ============================================================
   ★ CONFIGURE ME — edit these values before you launch ★
   ============================================================ */
const OWNER_NAME   = 'Your Name';
const OWNER_EMAIL  = 'you@yourorg.com';
const ORG_NAME     = 'Your Organisation';
const ORG_ABBR     = 'ORG';
const AUTH_DOMAIN  = '@yourorg.com';
const LOG_FORM_URL = '';
```

Replace each value:

| Setting | What to put | Example |
|---------|-------------|---------|
| `OWNER_NAME` | Your full name | `'Jane Smith'` |
| `OWNER_EMAIL` | Your email address | `'jane@acme.com'` |
| `ORG_NAME` | Your company or team name | `'Acme Corp'` |
| `ORG_ABBR` | 2–3 letter abbreviation for the logo box | `'ACM'` |
| `AUTH_DOMAIN` | Your email domain (for sign-in gate) | `'@acme.com'` |
| `LOG_FORM_URL` | Leave blank for now | `''` |

Keep the single quotes around each value.

### Replace the sample projects

A little further down you'll find the `SEED` array — these are the example projects that load the first time. Replace them with your own, or delete them all and use the **+ Add Project** button in the dashboard instead.

Each project looks like this:
```js
{id:1, title:'Website Redesign', pillar:'Marketing & Communications', accountable:'Alex', responsible:'Jordan',
 note:'Full redesign brief approved. Agency shortlisted.', target:'Sep 2026',
 links:[], archived:false, updates:[], priority:null, progress:0, mondayNote:'', todoistTaskUrl:''},
```

Fields to edit:
- `title` — project name
- `pillar` — must match one of the values in the `PILLARS` list just above SEED
- `accountable` — who owns the outcome
- `responsible` — who does the work
- `note` — background context
- `target` — deadline or timeline (free text, e.g. `'Jun 2026'` or `'Ongoing'`)

### Rename the pillars

Find the `PILLARS` line and change the category names to match your organisation:
```js
const PILLARS = ['Strategy & Leadership', 'Operations', 'Marketing & Communications', 'Programs & Delivery', 'Community & Stakeholders'];
```

### Save your changes

1. Scroll to the bottom of the editor
2. Click **Commit changes**
3. Click **Commit changes** again on the confirmation dialog

GitHub Pages will redeploy automatically — your live site will update within ~60 seconds.

---

## Step 4 (Optional) — Enable live sync so others can see your updates

By default the dashboard saves data in your browser only. To create a live shareable link that updates in real time:

### Create a GitHub token for syncing

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token (classic)**
3. Give it a name like `projects-dashboard-sync`
4. Under **Scopes**, tick **gist** only
5. Scroll down and click **Generate token**
6. **Copy the token** — you won't be able to see it again

### Enable sync in the dashboard

1. Open your live dashboard
2. Click **Enable Live Sharing** in the top right
3. Paste your token and click **Enable Live Sharing**
4. A shareable link is created — click **Share link** to copy it

Anyone with the link can see your dashboard in real time (read-only). You can send it to your team, your manager, or anyone you want to keep informed.

> **Note:** The token is saved only in your browser's local storage. It never leaves your device except to talk to GitHub's API.

---

## Step 5 (Optional) — Add a Google sign-in gate

By default the live link is accessible to anyone who has the URL. If you want to require Google sign-in (so only people from your organisation can view it):

### Create a Google OAuth client

1. Go to [console.cloud.google.com](https://console.cloud.google.com/)
2. Create a new project (or use an existing one)
3. Go to **APIs & Services → Credentials**
4. Click **Create Credentials → OAuth 2.0 Client ID**
5. Choose **Web application**
6. Under **Authorised JavaScript origins**, add your GitHub Pages URL:
   ```
   https://YOUR-USERNAME.github.io
   ```
7. Click **Create** and copy the **Client ID** (looks like `123456789-abc.apps.googleusercontent.com`)

### Add the Client ID to your dashboard

1. Open your live dashboard (as the owner — not the shared link)
2. Click **Settings** in the header
3. Paste your Client ID into **Google OAuth Client ID**
4. Click **Save Settings**

Now visitors to the shared link will be prompted to sign in with Google. Only accounts ending in `AUTH_DOMAIN` (the value you set in Step 3) will be allowed in.

### Restrict to specific people (optional)

If you want to allow only certain individuals rather than your whole domain:

1. Open **Settings**
2. Under **Allowed accounts**, type each permitted email address on its own line
3. Click **Save Settings**

---

## Step 6 (Optional) — Connect Todoist

Create Todoist tasks directly from any project card in the dashboard.

1. Go to **Todoist → Settings → Integrations → Developer**
2. Copy your **API token**
3. Open your dashboard and click **Settings**
4. Paste the token under **Todoist integration**
5. Click **Save Settings**

You'll now see a **Create Todoist Task** button inside each project's detail panel.

---

## Day-to-day use

### Monday Triage
Click **Monday Triage** in the nav. For each project, set a priority level and type a short focus note for the week. Click **Save All Triage Notes** — these are permanently logged.

### End-of-Week Update
Click **Weekly Update**. For each project, type what moved this week and optionally adjust the priority and progress percentage. Click **Save All Updates**.

### Update Log
A full chronological history of every triage note and weekly update, grouped by week.

### Adding a project
Click **+ Add Project** in the stats bar. Fill in the form and click **Create Project**.

### Editing a project
Click **Edit** on any row, or open the project detail panel and click **Edit project**.

### Progress bars
Set progress (0–100% in 10% steps) when editing a project, during Monday Triage, or during the weekly update. The gold bar is visible on every view.

### Archiving
Open a project's detail panel and click **Archive** to hide it from the main view. Archived projects are still accessible via the "Show archived" checkbox.

---

## Export and backup

Click **Export** in the header to download a full JSON backup of all your projects and updates. Click **Import** to restore from a backup or migrate data between devices.

---

## Customising the design

All colours are defined as CSS variables at the top of `index.html`. The key ones:

```css
--purple:  #7d639b;   /* header, nav, primary actions */
--gold:    #AC9D71;   /* progress bars, active nav tab */
--ash:     #F0EFEB;   /* page background */
--charcoal:#39393B;   /* body text */
```

Change these hex values to match your brand colours.

---

## FAQ

**Do I need to pay for anything?**
No. GitHub accounts are free. GitHub Pages hosting is free. All integrations (Gist, Google SSO) use free tiers.

**Where is my data stored?**
In your browser's `localStorage` by default — it stays on your device. If you enable live sync, it's also stored in a GitHub Gist (a free file-hosting feature on GitHub) under your account.

**Can multiple people edit the dashboard at the same time?**
No — this is designed for one owner who manages the data. Colleagues can view the live shared link in read-only mode.

**What happens if I clear my browser data?**
If you have live sync enabled, your data is safe in the Gist and will reload automatically. If sync is not enabled, use the **Export** button regularly to back up your data.

**Can I rename the pillars after I've already added projects?**
Yes, but projects already saved with the old pillar name will keep that name. You'd need to re-edit each project to update the pillar. It's easiest to set the right pillar names before adding lots of projects.

**Can I use this without GitHub at all?**
Yes. Just open `index.html` directly in your browser. Everything works offline — you just won't have a live shareable link or public URL.

**How do I update to a newer version of the template?**
Because you forked the repo, you can sync updates by clicking **Sync fork** on your repository page. Be careful: if you've edited `index.html` with your own data, syncing may overwrite your changes. Always export a backup first.

---

## Project structure

```
index.html    ← the entire app (HTML + CSS + JavaScript in one file)
README.md     ← this guide
```

No build tools. No dependencies. No package.json. Just one file.

---

## Credits

Built on the [Special Projects Dashboard](https://github.com/Tr3v0r86/Special-Projects-Dashboard) by Trevor Cardozo at ELC Group Bangkok. Adapted as an open template for anyone to use.
