# CleanStream

Ad and popunder filters for Nigerian sites. Two plain text filter files. No app, no account.

Most of the junk on Nigerian news, blog, betting, streaming and download sites does not come from
the site itself: a third-party network injects popunders, push prompts, redirects and adult banners
into the page or into the video player. CleanStream blocks those networks.

## What is in here

| File | Format | Use in |
| --- | --- | --- |
| [`filters/cleanstream-adblock.txt`](filters/cleanstream-adblock.txt) | Adblock Plus syntax | uBlock Origin, AdGuard (browser, Android, iOS, Home) |
| [`filters/cleanstream-dns.txt`](filters/cleanstream-dns.txt) | Plain domain list | AdGuard Home, Pi-hole, Private AdGuard DNS custom blocklist, any DNS filter that takes plain domains |

Raw URLs:

- https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-adblock.txt
- https://raw.githubusercontent.com/Oluu32/cleanstream/main/filters/cleanstream-dns.txt

Current count: 115 unique domains. 31 adult ad networks and adult ad servers, 46 popunder / push /
interstitial networks, 38 mainstream ad exchanges and trackers. The Adblock file adds 12 popup rules
and 4 cosmetic rules on top. Both files carry the same domain set.

## What it covers

- **Adult ad networks and adult ad servers.** ExoClick, JuicyAds, TrafficJunky, TrafficStars, TrafficFactory, TrafficForce, TrafficHolder, EroAdvertising and similar. These are behind most of the porn banners and popunders that land on non-adult sites.
- **Popunder, push and interstitial networks.** Adsterra, AdCash, Adnium, AdsKeeper, AdSupply, HilltopAds, AdMaven, the PopAds CDN, the AdMeasures and CPM bundles, plus notification spam hosts such as allowpush.com and htmonster.com.
- **Mainstream ad exchanges and trackers.** Google ad domains, DoubleClick, adnxs.com, Criteo, Taboola, Outbrain, MGID, RevContent, Zergnet, PubMatic, OpenX, Rubicon, Smart AdServer and the usual measurement pixels.

It deliberately leaves out content hosts. Image hosts, video CDNs and link shorteners are not
blocked, because blocking them breaks the page rather than the ad. Ads served from a site's own
domain are not covered by a list like this.

## What it does not do

- It does not make a site legal or safe. Blocking the ads on a pirate stream or a betting mirror does not change what that site is or what it does with your data.
- It does not remove paywalls, DRM, logins or geo-restrictions, and it never will.
- It is not a malware or phishing protection product. Some of these networks also push malicious creative; blocking them helps, but that is a side effect, not a guarantee.
- It is not affiliated with AdGuard, uBlock Origin, EasyList, Pi-hole or any DNS provider.
- It has not been audited by anyone.

## Setup

### Desktop browsers, uBlock Origin

1. Open the uBlock Origin dashboard, then Filter lists.
2. Tick **Import** at the bottom and paste the raw adblock URL.
3. Apply changes.

AdGuard browser extension and desktop app: Settings, Filters, Custom filters, Add custom filter, then
paste the same URL.

### Android

The fastest route is DNS level and needs no app: Settings, Network and internet, Private DNS, then
Private DNS provider hostname, enter `dns.adguard-dns.com`, Save. That uses AdGuard DNS's own filter
set, not this list.

To run this list on Android, add it as a custom blocklist in Private AdGuard DNS (the Personal plan
allows 1,000 rules, well above this list), then set Private DNS to your personal device hostname.

### iPhone and iPad

One tap: download the AdGuard DNS configuration profile from https://adguard-dns.io/en/public-dns.html,
then Settings, Profile Downloaded, Install. That is AdGuard's filter set, not this list.

To run this list on iOS, add the raw adblock URL as a custom DNS filter inside the AdGuard app
(Protection, DNS protection, DNS filtering), or add it to a Private AdGuard DNS server and install
that server's profile.

### Home network or router

- AdGuard Home: Filters, DNS blocklists, Add blocklist, Add a custom list, paste the raw DNS list URL.
- Pi-hole: Adlists, paste the raw DNS list URL, then Update gravity.

## Sources

Domains were taken from public filter projects and vendor pages, not invented.

- EasyList adult ad servers and adult popup lists:
  https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers.txt and
  https://raw.githubusercontent.com/easylist/easylist/master/easylist_adult/adult_adservers_popup.txt
- LanikSJ ubo-filters, per-network lists (MIT): https://github.com/LanikSJ/ubo-filters (AdMaven, HilltopAds, AdMeasures, MacUpload, VideoAdex, Contentza, PopAds)
- Peter Lowe's ad and tracking server blocklist: https://pgl.yoyo.org/adservers/
- v2ray domain-list-community, category-ads: https://github.com/v2ray/domain-list-community/blob/master/data/category-ads
- ShadowWhisperer BlockLists, Ads: https://github.com/ShadowWhisperer/BlockLists
- Adsterra tracker origins seen on a live tag, highperformanceformat.com and effectivecpmnetwork.com: https://www.justads.click/
- MGID serving hostnames: https://openadlibrary.com/blog/how-to-identify-the-ad-network-behind-an-ad
- Mainstream exchange and tracker set cross-checked against: https://freedom.to/blog/how-to-block-ads-with-freedom/

## What was not verified

- **No per-site testing.** The lists were compiled from public lists and a few live tag observations. They were not loaded and browsed on Nigerian news, betting, blog or streaming sites. Expect the occasional false positive and the occasional miss.
- **Named but not confirmed, so not in the list:** PropellerAds, PopAds (the popads.net host itself), PopCash, RichAds, Galaksion, Evadav, ROIads, Clickadu's ad hosts, and Monetag's rotating serving hosts. These rotate constantly and need a fresh observation before they go in.
- **Counts are the file contents at this commit.** There is no claim that the list catches every ad on any given site.
- **No CDN.** The lists are served from raw GitHub.

A pull request that adds a network with evidence is welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT. See [LICENSE](LICENSE).
