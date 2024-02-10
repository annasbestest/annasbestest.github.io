---
layout: post
---

One of my favourite websites <a href="https://pricehipster.com/">Price Hipster</a> tracks and displays the price changes of products online, allowing you to set up alerts based on your specified price threshold.

About two years ago, Dan Murphy's products stopped being displayed and tracked on Price Hipster due to unknown reasons. To this day, the products remain absent from the site.

As I had become dependent on this feature to find wine at discounted prices, I set out to build my own price tracker. This way, I could continue to complement my wife's expensive taste in <a href="https://toscanos.com.au/">Toscano's</a> cheese with equally fine wines, acquired at more affordable prices.

### Unexpected Results
I pieced together a script to collect Dan Murphy's wine price data <a href="https://en.wikipedia.org/wiki/Web_scraping">"en masse"</a>. These scripts ran several times over a few weeks to compile price snapshots, allowing me to spot price drops.

Eventually I noticed price drops on some interesting wines so I added them to my cart for checkout. Strangely, the prices at checkout did not match those captured by the data collection script. 

After some digging around, I found that the VPN used during the data collection process (to avoid the risk of Dan's perma-banning my own IP) was having a different Click&Collect store automatically assigned than my local one.

The two different Dan Murphy's stores had their own price for identical bottles of wine, and the cheaper price was not marked as a clearance or "Member Offer" offer.

For example, the two identical wines shown below have different prices as of 17/01/2024: the bottle at Kew is priced at $40.60, whereas at Alphington, it's $57.99. That's a $17 discount for a drive of less than ten minutes. There is also no indication of a sale or "Member Offer" offer when viewing the bottle with the Kew store selected.

<figure>
  <img src="/assets/2024-02-03-img01.png" alt="" loading="lazy">
  <figcaption>
    As of 17/01/2024 two identical wines with a 30% price variation, dependent on Dan Murphy's stores that are approx. 10 minutes drive from one another.
  </figcaption>
</figure>

Even more baffling than the first example, the bottle below (Fawkner store) marked as a "Member Offer" offer is priced higher than an identical bottle with no sale mentioned (Collingwood store).

<figure>
  <img src="/assets/2024-02-03-img02.png" alt="" loading="lazy">
  <figcaption>
    A bottle marked "Member Offer" offer is priced higher than an identical bottle with no sale mentioned
  </figcaption>
</figure>

### Exploring Store-based Pricing
Now aware that there are two dimensions influencing price drops (time and location) I set out to explore the relationship between location and price. 
