# Publish steps for loyalnumber.com (NOT EXECUTED)

Do these only after Landon approves publishing. Nothing below has been done.
Checked against GitHub Docs, "Managing a custom domain for your GitHub Pages site" (docs.github.com, read Oct 21, 2026).

## 0. Before you start
- GitHub Pages is free for **public** repos. A private repo needs a paid plan (GitHub Pro or higher), so plan on making `landonbsmith/loyalnumber-site` public. Everything in this folder is meant to be public; nothing secret is in it.
- Recommended by GitHub: verify the domain first so no one else can claim it. Go to GitHub (profile picture) > **Settings** > **Pages** > **Add a domain**, enter `loyalnumber.com`, then add the TXT record GitHub shows you (host `_github-pages-challenge-landonbsmith`, value given by GitHub) in Namecheap, and click **Verify**.

## 1. Create the repo and push
1. On GitHub, create a new repository `landonbsmith/loyalnumber-site`, Public, with **no** README, .gitignore, or license (so it's empty).
2. Push this folder:
   ```bash
   cd /workspace/loyalnumber-site
   git branch -M main
   git remote add origin https://github.com/landonbsmith/loyalnumber-site.git
   git push -u origin main
   ```
   Optional: remove `README-DRAFT.md` and `PUBLISH-STEPS.md` first if you don't want them public (they'd be at loyalnumber.com/README-DRAFT.md otherwise). Also strip the `<!-- DRAFT ... -->` and `<!-- OPEN QUESTION ... -->` comments from the HTML once the questions are answered, since anyone can read page source.

## 2. Turn on GitHub Pages
1. Repo > **Settings** > **Pages** (under "Code and automation").
2. **Build and deployment** > Source: **Deploy from a branch**. Branch: **main**, folder: **/ (root)**. Save.
3. **Custom domain**: enter `loyalnumber.com` and Save. (The repo already has a `CNAME` file with `loyalnumber.com`; if GitHub adds its own commit, pull it.)
4. Do the DNS steps below, then wait for the DNS check to pass.
5. Tick **Enforce HTTPS**. GitHub says this can take up to 24 hours to become available.

## 3. Namecheap DNS (BasicDNS)
Namecheap > **Domain List** > `loyalnumber.com` > **Manage** > **Advanced DNS** > **Host Records**.

**Leave these alone:** the existing **MX** records and the **SPF TXT** record (`v=spf1 ...`) that make support@loyalnumber.com and the catch-all forward to landonbsmith@gmail.com. Don't change the "Mail Settings" (Email Forwarding) section either.

**Remove only** the default parking records that conflict with `@` and `www`. Usually these are:
- **URL Redirect Record** `@` -> `http://www.loyalnumber.com/` (or similar)
- **CNAME Record** `www` -> `parkingpage.namecheap.com.`

**Add:**
| Type | Host | Value | TTL |
|---|---|---|---|
| A Record | `@` | `185.199.108.153` | Automatic |
| A Record | `@` | `185.199.109.153` | Automatic |
| A Record | `@` | `185.199.110.153` | Automatic |
| A Record | `@` | `185.199.111.153` | Automatic |
| CNAME Record | `www` | `landonbsmith.github.io.` | Automatic |

Optional IPv6 (GitHub recommends keeping the A records too):
| Type | Host | Value |
|---|---|---|
| AAAA Record | `@` | `2606:50c0:8000::153` |
| AAAA Record | `@` | `2606:50c0:8001::153` |
| AAAA Record | `@` | `2606:50c0:8002::153` |
| AAAA Record | `@` | `2606:50c0:8003::153` |

Notes:
- The `www` CNAME points to `landonbsmith.github.io` with no repo name (per GitHub). GitHub then redirects `www.loyalnumber.com` to `loyalnumber.com` automatically.
- Don't add a wildcard (`*`) record; GitHub warns it risks domain takeover.
- DNS changes can take up to 24 hours.

## 4. Check it
```bash
dig loyalnumber.com +noall +answer -t A      # expect the four 185.199.10x.153 addresses
dig www.loyalnumber.com +nostats +nocomments +nocmd   # expect CNAME landonbsmith.github.io.
dig loyalnumber.com MX +short                # expect the same Namecheap mail forwarding MX as before
```
Then open https://loyalnumber.com, https://loyalnumber.com/sms.html, /privacy.html, /terms.html, and send a test email to support@loyalnumber.com to confirm forwarding still works.
