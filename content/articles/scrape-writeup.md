Title: Scraping Lobsters Writeup
Author: Sean Kung
Date: 2020-06-28
Category: posts
Tags: python
Slug: scraping-lobsters-wripteup


The code sample is found [here](https://github.com/seakun/Python-Projects/blob/master/scrape.py).

Modules used: bs4 from BeautifulSoup, requests, and pprint.

I created this program to scrape the popular tech website [Lobsters](https://lobste.rs/). It'll get the links, titles, and scores of each story and output to a dictionary the ones that have more than 10 upvotes. To run this run this program, type in:

    
    :::python3
    python3 scrape.py


There are 2 main parts - the global variables and the create_custom_lb_list():
    
    :::python3
    res = requests.get('https://lobste.rs/')
    soup = BeautifulSoup(res.text, 'html.parser')
    lobster_links = soup.select('.u-url')
    lobster_subtext = soup.select('.story')

    create_custom_lb_list(links, subtext)

The "res" variable gets the webpage.
"soup" breaksdown the "res" variable into HTML
"lobster_links" searches the tags in "soup" for the CSS classes 'u-url'.
"lobster_subtext" searches the tags in "soup" for the CSS classes 'story'.

In "create_custom_lb_list", we take the link and subtext parameter to create the list. I use "enumerate" function since I need to iterate through the links and also count upwards. I extract the title, link, and score from "lobster_links" and "lobster_subtext". If the score if over 10, I'll add them to the list as a dictionary.

The remaining parts "sort_stories_by_score" and "pprint" sorts the list by ascending score and outputs the dictionary in a readable format, respectively.

