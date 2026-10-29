# CleanStream

CleanStream publishes browser and DNS filter files that may reduce requests to selected ad and tracking domains. Blocking is partial. Results depend on the site, player, app, browser, DNS route and which requests match the rules. No representative testing on Nigerian sites is claimed.

## Files

- `filters/cleanstream-adblock.txt` - ABP-style browser filter rules for uBlock Origin and AdGuard Browser Extension. It contains network rules, 12 popup rules and 4 cosmetic rules. Use it in a browser blocker that accepts these rules, not as a DNS-only blocklist.
- `filters/cleanstream-dns.txt` - domains-only text list for AdGuard Home, Pi-hole and a personal Private AdGuard DNS server. Use it for DNS filtering, not for the browser file's popup or cosmetic rules.

Raw URLs:

- https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-adblock.txt
- https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-dns.txt

Setup guide: https://cleanstream.pally.site

## Counts

Both files contain the same 115 listed domain names. The repository groups them as 31 adult ad-serving domains, 46 popunder/push/interstitial domains and 38 mainstream ad and tracking domains. These are file counts and editorial categories, not evidence of current use or traffic share. The browser file also has 12 popup rules and 4 cosmetic rules.

## What the entries target

The files include domains associated in public filter sources with adult advertising, popunder/push/interstitial delivery, mainstream ad exchanges and tracking. Examples of literal entries include `exoclick.com`, `adsterra.com`, `allowpush.com`, `taboola.com` and `doubleclick.net`. Their presence here does not establish that a particular Nigerian site uses them now, or that these domains account for most porn banners or ads.

The lists do not include site content hosts such as video CDNs or image hosts by design. A site's own first-party ads, unlisted hosts, direct-IP requests and ads delivered from a site's own domain are outside the coverage of these domain entries.

## Limits and possible breakage

- Blocking is partial. A site may still show ads, redirects or popunders, including inside a player. DNS filtering only blocks matching DNS lookups; it does not hide page elements or guarantee that a player will stop opening popunders. Browser rules may apply additional page-level actions, subject to browser support.
- DNS protection depends on the device using the resolver configured with this list. A VPN, a different Private DNS setting, browser-level secure DNS, mobile data or an app using another resolver can bypass a home-network DNS setup.
- The DNS file is a domains-only list, not a set of wildcard subdomain rules. AdGuard's DNS documentation says a plain entry such as `example.org` blocks `example.org` but not `www.example.org`. Some subdomain hosts may therefore remain unblocked. Check the behavior of the DNS provider you use.
- A listed domain may also serve a site's needed resources. Blocking it can break a page or feature. Disable the list or allowlist the affected domain if that happens.
- No site-by-site testing has been done on Nigerian news, blog, betting, download or streaming sites. We have not verified that the listed networks serve ads on those sites or measured what share of ads they account for. The rules may miss ads or cause false positives.
- CleanStream is not a malware or phishing protection product. Blocking ads does not make a site legal or safe. The lists do not bypass paywalls, DRM, logins or geo-restrictions.
- CleanStream is not affiliated with or endorsed by AdGuard, uBlock Origin, EasyList, Pi-hole or any DNS provider. No audit or blocking guarantee is claimed.

## Setup

### Desktop browser

For uBlock Origin, open Dashboard → Filter lists, enable `Import` under `Custom`, paste the browser-list URL and apply or update the lists. uBlock Origin documents this third-party list import flow.

For AdGuard Browser Extension, open `Filters` → `Custom`, add the browser-list URL and confirm. AdGuard documents custom filters from a URL or local file.

Use `cleanstream-adblock.txt` here. For DNS services, use `cleanstream-dns.txt`.

### iPhone or iPad with AdGuard for iOS

Enable DNS protection, then open `Protection` → `DNS protection` → `DNS filtering` → `DNS filters` → `Add a filter`. Paste the DNS-list URL and tap `Next` → `Add`. This route needs AdGuard for iOS and DNS protection enabled; it does not configure other devices.

### Android with Private AdGuard DNS

In the Private AdGuard DNS dashboard, add the DNS-list URL under `Servers` → `My server` → `Blocklists` → `Custom` → `Add custom blocklist`. Then set Android `Settings` → `Network & Internet` (or `Wi-Fi & Internet`) → `Advanced` → `Private DNS` → `Private DNS provider hostname` to the personal server hostname shown for your device and save. AdGuard's current Android instructions give that personal hostname format as `{Your_Device_ID}.d.adguard-dns.com`.

AdGuard's Personal plan has a 1,000-filtering-rule limit for the server. Existing filters count toward it; a custom list that exceeds the limit can be disabled.

### AdGuard public DNS is separate

The public Android hostname `dns.adguard-dns.com` and AdGuard's iOS configuration profile connect to AdGuard's public DNS service and its default filtering. They do not install or subscribe to CleanStream. Custom blocklists are configured on a personal Private AdGuard DNS server, a separate setup.

For the public iOS profile route, choose a profile on AdGuard's public DNS page, download it, then open `Settings` → `Profile Downloaded` → `Install`. This route uses AdGuard's public service, not the CleanStream list.

### Home network

In AdGuard Home, add the DNS-list URL as a custom DNS blocklist. Its documentation accepts domains-only lists; its plain domain rules do not match subdomains.

In Pi-hole, add the URL as a subscribed adlist and update Gravity (`pihole -g`). Pi-hole's documentation says Gravity downloads subscribed lists and parses them into domains-only format.

Devices are covered only while their DNS requests go through the server using this list. Setting the router to AdGuard's public DNS addresses does not add CleanStream. To use CleanStream across a home network, use a DNS service where you can add the CleanStream URL, such as your own AdGuard Home, Pi-hole or personal Private AdGuard DNS server.

## Sources for domain research

The list was assembled from public filter projects and other cited public sources. Source inclusion is not proof of current use on a particular site.

- EasyList adult ad servers and adult popup lists: https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers.txt and https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers_popup.txt
- LanikSJ ubo-filters, per-network lists: https://github.com/LanikSJ/ubo-filters
- Peter Lowe's ad and tracking server blocklist: https://pgl.yoyo.org/adservers/
- v2ray domain-list-community, category-ads: https://github.com/v2ray/domain-list-community/blob/master/data/category-ads
- ShadowWhisperer BlockLists, Ads: https://github.com/ShadowWhisperer/BlockLists
- Adsterra tracker origins observed on a live tag: https://www.justads.click/
- MGID serving hostnames reference: https://openadlibrary.com/blog/how-to-identify-the-ad-network-behind-an-ad
- Mainstream exchange reference: https://freedom.to/blog/how-to-block-ads-with-freedom/

## Current setup and format references

- uBlock Origin, importing third-party filter lists: https://github.com/gorhill/uBlock/wiki/Filter-lists-from-around-the-web
- AdGuard Browser Extension, custom filters: https://adguard.com/kb/adguard-browser-extension/features/filters
- AdGuard for iOS, system-wide filtering and custom DNS filter URL steps: https://adguard.com/kb/adguard-for-ios/solving-problems/system-wide-filtering/
- AdGuard DNS filtering syntax, including domains-only rules and their exact-domain behavior: https://adguard-dns.io/kb/general/dns-filtering-syntax/
- AdGuard Private DNS, custom blocklists by URL and plan limits: https://adguard-dns.io/kb/private-dns/setting-up-filtering/blocklists/
- AdGuard Android Private DNS hostname setup: https://adguard-dns.io/kb/private-dns/connect-devices/mobile-and-desktop/android
- AdGuard public DNS Android and iOS setup: https://adguard-dns.io/en/public-dns.html
- Pi-hole Gravity and subscribed lists: https://docs.pi-hole.net/main/pihole-command/

Provider documentation supports the respective import methods and general list formats. The files have not been imported and tested on every listed app, provider, device or version.

Pull requests that add a domain with a source and a clear reason are welcome. See `CONTRIBUTING.md`.

## License

MIT. See `LICENSE`.