---
summary: >-
  <!--StartFragment-->


  In this post we will learn how we can crawl popular websites having multiple subdomain links and extract Indian Celebrity Personality data from them.


  <!--EndFragment-->
authors:
  - admin
lastMod: 2019-09-05T00:00:00Z
title: Crawl popular websites & create a database of Indian movie celebrities
  with their images and personality traits
subtitle: In this post we will learn how we can crawl popular websites having
  multiple subdomain links and extract Indian Celebrity Personality data from
  them.
date: 2019-02-05T00:00:00Z
tags: []
categories: []
projects: []
image:
  caption: ""
  focal_point: ""
---
<!--StartFragment-->

In this post we will learn how we can crawl popular websites having multiple subdomain links and extract Indian Celebrity Personality data from them.

![](https://miro.medium.com/max/280/1*8hJ5Eaj_n6Pi3bjxqHWiHQ.jpeg)

# **Modules** to be Installed-

* Scrapy
* Beautiful Soap
* MySQL-Connector-Python

![](https://miro.medium.com/max/700/1*9-Hf1rY3AN7ZOgRI-jlM0w.png)

# **Pre-Requisite -**

Table must be created in Database for saving required data

# STEP 1 — Creating Scrapy Project

Using Scrapy, we can create multiple crawlers for different subdomains of a website. Hence this is very helpful. We can create Scrapy project using below command in cmd terminal

> **scrapy startproject IndianCelebrity**
>
> **cd IndianCelebrity**
>
> **scrapy genspider celebrity in.bookmyshow.com**

# **STEP 2 — Extract Links for Navigation**

Step 1 will create following structure of project

![](https://miro.medium.com/max/499/1*-1NfNyp9bfuEIFCuSyJ10Q.png)

In spiders folder, as we can see there is **celebrity.py** class which is crawling specific website. Similarly we can add more classes here for multiple websites based on the requirement.

In our case, we are crawling below link

## [Bollywood Archives - BookMyShow](https://in.bookmyshow.com/entertainment/movies/hindi/)

### [Copyright 2019 © Bigtree Entertainment Pvt. Ltd. All Rights Reserved. The content and images used on this site are…](https://in.bookmyshow.com/entertainment/movies/hindi/)

[in.bookmyshow.com](https://in.bookmyshow.com/entertainment/movies/hindi/)

We will mention below rule to extract links for navigation

> ***Rule(LinkExtractor(allow=(), restrict_css=(‘.next.page-numbers’,)),*\
> *callback=”parse_item”,*\
> *follow=True),)***

Here, next.page-numbers is the name of class for navigating to next page

We are calling parse_item further after navigating to different pages

# STEP 3 — Parse Links for navigating to Celebrities Page

After navigating to next pages one by one, we will further filter links for celebrity pages and save them to **Filtered_itemlinks.**

See below Code Snippet

![](https://miro.medium.com/max/700/1*CMIoR4B7XskLZOTwaGtDQw.png)

# STEP 4 — Parse celebrity page for saving details of celebrities

Next step is to parse celebrity pages for fetching there data. We are fetching there name, picture and personality description on the respective page simultaneously.

After fetching data, we are connecting MySQL database and saving all the details.

Code snippet for above step -

![](https://miro.medium.com/max/700/1*4O-7XTzcMXq69qYGzLWe_g.png)

Here we are exploring the html structure of webpages and using xpath to extract the data.

<!--EndFragment-->