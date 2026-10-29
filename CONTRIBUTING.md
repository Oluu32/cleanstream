# Contributing

One domain per pull request line, with evidence.

## Adding a domain

1. Pick the section it belongs to: adult ad network, popunder or push network, or mainstream exchange and tracker.
2. Add it to both `filters/cleanstream-adblock.txt` (`||domain^$third-party`) and `filters/cleanstream-dns.txt`.
3. Update the per-section count in the heading and the total at the bottom of both files.
4. Say in the pull request where the domain came from: the network's own site, a request you watched fire on a page (give the page URL), or a public filter list that already carries it (give the link).

## Rules

- Base domains only. `ads.example.com` goes in as `example.com`, unless the parent domain serves real content.
- No content hosts: no image or video CDNs, no link shorteners, no domain that is a news outlet or a streaming site itself.
- Nothing that bypasses a paywall, DRM, login or geo-restriction.
- A domain that breaks a normal site feature does not belong here. If you are not sure, say what broke.

## Style

- Lowercase, one domain per line, no `www.`, no trailing slash, no protocol.
- Sections are alphabetical. Keep them that way.
- Keep comments starting with `!` short and factual. No marketing.
