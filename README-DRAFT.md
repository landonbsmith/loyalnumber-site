# LoyalNumber site: LOCAL DRAFT (not published)

**Status:** Draft for Landon's review. Nothing has been pushed, published, or changed in DNS. No repo or remote exists.
Built Oct 21, 2026 (MT) by Grok Bot at Agent App Ava's request. LoyalNumber is the new brand for the Agent Phone Line, a DBA of LBS Enterprises, LLC.

## Pages
| File | What it is |
|---|---|
| `index.html` | Home/product page: dedicated US number for your AI agent (calls, texts, login codes), $20/month, for regular people and small businesses, AI disclosure on every call, pricing, short SMS summary linking to `sms.html`. |
| `sms.html` | Text message program page for 10DLC review: program name, opt-in at line setup (with the exact consent-box wording), who receives texts, frequency, "Msg & data rates may apply", STOP/HELP, no sharing of mobile info for marketing, sample messages (opt-in confirmation, agent text, HELP reply, STOP reply), links to privacy and terms. |
| `privacy.html` | Privacy Policy adapted from the LBS Agent Phone Line draft (anchor `#sms`). |
| `terms.html` | Terms & Conditions adapted from the LBS Agent Phone Line draft (anchor `#sms`), Utah governing law. |
| `styles.css` | Single responsive stylesheet. No JavaScript, no trackers, no external fonts or assets. |
| `CNAME` | `loyalnumber.com`, for GitHub Pages later. Harmless locally. |
| `PUBLISH-STEPS.md` | Exact publish steps. **Not executed.** |

Footer on every page: "LoyalNumber is a service of LBS Enterprises, LLC", 929 W. Sunset Boulevard, Suite 21-518, St. George, UT 84770, support@loyalnumber.com, (435) 767-9338.

Source content: `/workspace/lbs-site-phone-line-draft` branch `agent-phone-line-draft` (agent-phone-line.html, #agent-sms, terms/privacy #agent-phone-line), and `/workspace/agent-phone-line/build-plan.md`. Rebranded "LBS Agent Phone Line" to "LoyalNumber"; contact email changed from landonbsmith@gmail.com to support@loyalnumber.com.

## Open questions for Landon (also left as HTML comments in the pages, not visible copy)
1. **Who receives texts.** Texts go to the line owner *and* to the people or businesses the owner tells their agent to text. Those recipients never opted in on our site. Is that OK for the 10DLC campaign, or should outbound texts be limited to the owner (and to people who texted the line first)? (Comment in `sms.html`, "Who receives texts".)
2. **User responsibility.** How much responsibility does the line owner take for how their agent uses the line (who it calls or texts, consent, recording laws, misuse)? The draft says "You are responsible for your agent's calls and texts" and that we may pause or close a misused line. Needs your legal review. (Comment in `terms.html`, "Acceptable use and your responsibility".)
3. **Sign-up / opt-in flow.** The site describes opt-in at line setup: sign up, confirm email with a one-time code, enter mobile number, check an unchecked consent box, agree to terms. That flow isn't built or public yet (the MVP has no public sign-up). Confirm the real flow, and whether a live sign-up page with the consent box must exist before the 10DLC submission. (Comment in `sms.html`, "How you opt in".)

## Other things to check before publishing
- New wording not in the earlier draft: the consent-box text, the opt-in confirmation, the HELP and STOP reply samples, "Opting in to texts is not a condition of purchase," "Reply START to opt back in," "You can cancel at any time by emailing support@loyalnumber.com," the note that some services won't send codes to internet-based numbers, and "A real person reads every message."
- The (435) 767-9338 support number is the LoyalNumber line itself (LINE_NUMBER). Confirm that's the public support number you want.
- The "Email us to get started" button is a mailto link. There's no sign-up form yet.

## Preview
Open `file:///workspace/loyalnumber-site/index.html` in a browser. Screenshots: `/workspace/loyalnumber-site-home.png` (1280 wide), `/workspace/loyalnumber-site-sms.png`, `/workspace/loyalnumber-site-home-mobile.png` (390 wide).
