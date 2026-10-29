# CleanStream

Ad and popunder blocks for Nigerian sites. Plain filter files, no app, no account.

Plain-language intro: CleanStream is a blocklist. It stops the ad networks that Nigerian news, blog,
betting, download and streaming sites load from third parties - the popunders, push prompts, redirect
tabs and adult banners. It is not a browser and it does not touch the site's own content.

Two formats:

- `filters/cleanstream-adblock.txt` - Adblock Plus syntax for uBlock Origin and the AdGuard apps.
- `filters/cleanstream-dns.txt` - plain domain list for AdGuard Home, Pi-hole and Private AdGuard DNS.

Raw URLs:

https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-adblock.txt
https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-dns.txt

Setup guide with the one-tap routes: https://cleanstream.pally.site

## Counts

115 unique domains, the same set in both files: 31 adult ad networks and adult ad servers, 46
popunder/push/interstitial networks, 38 mainstream ad exchanges and trackers. The Adblock file adds
12 popup rules and 4 cosmetic rules.

## What it covers

Adult ad networks (ExoClick, JuicyAds, TrafficJunky, TrafficStars, TrafficFactory, TrafficForce,
TrafficHolder, EroAdvertising and similar), popunder and push networks (Adsterra, AdCash, Adnium,
AdsKeeper, AdSupply, HilltopAds, AdMaven, the PopAds CDN, the AdMeasures and CPM bundles, plus
notification spam hosts like allowpush.com and htmonster.com), and the mainstream exchanges and
trackers (Google ad domains, DoubleClick, adnxs.com, Criteo, Taboola, Outbrain, MGID, RevContent,
Zergnet, PubMatic, OpenX, Rubicon, Smart AdServer and the usual measurement pixels).

Content hosts are left out on purpose. Image hosts, video CDNs and link shorteners are not blocked,
because blocking them breaks the page instead of the ad. A site's own first-party ads are not
covered by a domain list.

## What it does not do

- It does not make a site legal or safe. Blocking the ads on a pirate stream or a betting mirror does not change what that site is or what it does with your data.
- It does not remove paywalls, DRM, logins or geo-restrictions, and it never will.
- It is not a malware or phishing product. Some of these networks also push bad creative; blocking them helps, but that is a side effect, not a guarantee.
- It is not affiliated with AdGuard, uBlock Origin, EasyList, Pi-hole or any DNS provider.
- It has not been audited by anyone.

## Setup

### Desktop browser, uBlock Origin

1. Open the uBlock Origin dashboard, then Filter lists.
2. Tick Import at the bottom, paste the adblock raw URL, apply changes.

AdGuard for Windows or macOS: Settings, Filters, Custom filters, Add custom filter, same URL.

### Android

No app, DNS level: Settings, Network and internet, Private DNS, Private DNS provider hostname,
enter dns.adguard-dns.com, Save. That path uses AdGuard DNS's own filter set, not this list.

To run this list: create a Private AdGuard DNS server, add the DNS raw URL under Servers, My server,
Blocklists, Custom, Add custom blocklist, then set Private DNS to your personal device hostname. The
Personal plan allows 1,000 filtering rules, well above this list.

### iPhone and iPad

No app, one tap: on https://adguard-dns.io/public-dns.html pick the iOS configuration profile,
download it, then Settings, Profile Downloaded, Install. That is AdGuard DNS's filter set, not this
list. A VPN on the phone overrides the profile.

To run this list on iOS: add the adblock raw URL as a custom DNS filter in the AdGuard app
(Protection, DNS protection, DNS filtering), or add it to a Private AdGuard DNS server and install
that server's profile.

### Home network or router

- AdGuard Home: Filters, DNS blocklists, Add blocklist, Add a custom list, paste the DNS raw URL.
- Pi-hole: Adlists, paste the DNS raw URL, then Update gravity.

## Sources

Domains came from public filter projects and vendor pages, not from guessing.

- EasyList adult ad servers and adult popup lists: https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers.txt and https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers_popup.txt
- LanikSJ ubo-filters, per-network lists (MIT): https://github.com/LanikSJ/ubo-filters
- Peter Lowe's ad and tracking server blocklist: https://pgl.yoyo.org/adservers/
- v2ray domain-list-community, category-ads: https://github.com/v2ray/domain-list-community/blob/master/data/category-ads
- ShadowWhisperer BlockLists, Ads: https://github.com/ShadowWhisperer/BlockLists
- Adsterra tracker origins seen on a live tag (highperformanceformat.com, effectivecpmnetwork.com): https://www.justads.click/
- MGID serving hostnames: https://openadlibrary.com/blog/how-to-identify-the-ad-network-behind-an-ad
- Mainstream exchange set cross-checked against: https://freedom.to/blog/how-to-block-ads-with-freedom/

## What was not verified

- No per-site testing. The lists were compiled from public lists and a few live tag observations; they were not loaded and browsed on Nigerian news, betting, blog or streaming sites. Expect the occasional false positive and the occasional miss.
- Named but not confirmed, so not in the list yet: PropellerAds, PopAds (the popads.net host itself), PopCash, RichAds, Galaksion, Evadav, ROIads, Clickadu's ad hosts, Monetag's rotating serving hosts. They rotate constantly and need a fresh observation.
- Counts are the file contents at this commit. There is no claim that the list catches every ad on any given site.
- No CDN. The lists are served from raw GitHub.

Pull requests that add a network with evidence are welcome. See CONTRIBUTING.md.

## License

MIT. See LICENSE.
