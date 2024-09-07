---
layout: post
title: "Tracking Qantas Wine Bonus Point Deals"
---



Qantas Wine is a marketplace where you can purchase wines using either cash or Qantas points. Some offers even allow you to earn bonus Qantas points, making it a popular choice for those looking to boost their point-earning strategies.

For example, spend $354.00 on 6 bottles of this Tahbilk (priced at $59.00 per bottle), and you will receive 12k Qantas points. This equates to earning bonus points at 2.95 cents per point.

<figure style="text-align: center;">
  <img src="/assets/qantas-wine/eg1.png" alt="" loading="lazy" style="width: 50%; margin: 0 auto;">
</figure>

Alternatively, spend $215.88 on this 12 pack of d'Arenberg (priced at $17.99 per bottle), and you will receive 4.5k Qantas points. This equates to a less than ideal 2.8 cents per point, but with the benefit of not having to fork out $59.00 for a bottle of wine.

<figure style="text-align: center;">
  <img src="/assets/qantas-wine/eg2.png" alt="" loading="lazy" style="width: 50%; margin: 0 auto;">
</figure>

Currently there are a couple of websites (<a href="https://flightformula.com/tools/qfwine">here</a> and <a href="https://wines.reflyable.com.au/">here</a>) that track and display the wines sorted by Cents Per Point earned. However, not everyone is willing to buy an $80 bottle of wine to receive points at the best rate!

So I decided to build my own tracking and reporting tool that shows both factors (Cents Per Point and $/bottle) to make a more informed decision. This way, you can easily balance point-earning potential with the price of the bottle that suits your budget.

## The dashboard
Link to dashboard [HERE]([url](https://appappntaswine-b8zvhwxo7znduhwskkcmrh.streamlit.app/)).

The dashboard plots wine prices (per bottle) against the corresponding Cents per Point earned in a scatter plot, making it easier to spot the 'sweet spots.'

Both historical and current bonus point offers are displayed, helping you see whether current promotions are a good deal or if it’s better to wait for something else.

I’ve also highlighted Pareto efficient wines using star markers. A Pareto efficient wine is one where no other wine has both a lower price and a lower cost per point. In other words, it represents the best trade-off. You cannot lower one attribute (like price) without raising the other (like cost per point).

<figure style="text-align: center;">
  <img src="/assets/qantas-wine/dash1.png" alt="" loading="lazy" style="width: 100%; margin: 0 auto;">
  <figcaption>Hover mouse or tap wine to view details. Then search for wine below to get link to wine page.</figcaption>
</figure>

## Dashboard build (technical)

The dashboard is built using Streamlit, an open-source Python library that allows for the quick and easy creation of interactive web-based applications and dashboards for data science and reporting.

The code is hosted on my personal GitHub repository, and the app is deployed via Streamlit Cloud, which pulls updates directly from the repo to ensure the app stays current with any changes.

Dashboard code repo: https://github.com/sc0h0/streamlit_qantaswine

## Scraping and ETL (technical)

This was the most time-consuming part of the app! 

The wines with bonus point offers can be viewed at this URL (https://wine.qantas.com/c/browse-products?BonusPoints=1) which is unforuntatle a dynamicly loaded Javascript table rather than a html table.  

