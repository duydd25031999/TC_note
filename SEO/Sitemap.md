# Concept

- A sitemap is a signal about which URLs would like Google to crawl
- It may provide information on URLs that were recently created or modified, and give us some extra information about them.
- Google supports 4 main ways for to provide additional information:
    1. Image - Url extension
    2. Video - Url extension
    3. Alternate languages or country versions with hreflang annotations
    4. Sitemap variation
        - Recent updates - news site
----------------------------------------------------------------------------------------------------------------------------
- (!) If I don't have a sitemap, will Google find all my pages?
- Usually, if you have a relatively small websites + `pages are properly linked`
    - Googlebot can discover page content.
- A sitemap might be especially helpful if:
    - Site is really large
    - Pages are isolated
    - Site iss new/change quickly
- Sitemap doesn't guarantee that all your pages will be crawled and indexed.
    - But in most cases, site will benefit from having a sitemap.
    - Sitemaps don't replace normal crawling.
    - Not including URLs in a sitemap, won't result in those URLs no longer being crawled.
- Ideally, the system running website will make sitemap files, automatically.
    - Can find a WordPress plug-in
    - Recommend finding a way to automatically generate sitemaps, rather than creating them manually.
- There are limits to the number of URLs and the maximum size of a sitemap file.
    - Submit all of these sitemap files together

# Sitemap report

![Sitemap_report](/Sitemap_report.png)

- Status: the crawl status such as success, has errors, couldn't fetch, and others;
- Discovered Url: The number of URLs discovered in the sitemap.