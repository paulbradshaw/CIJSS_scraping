# Introduction to Scraping

![](https://s3.amazonaws.com/titlepages.leanpub.com/scrapingforjournalists/large?1458984302.png)

This repository contains resources related to the sessions on scraping at the Centre for Investigative Journalism Summer School.

## Slides and notes

* The [first presentation introducing scraping ideas and tips, and examples of its use in journalism is on Slideshare here](https://www.slideshare.net/onlinejournalist/scraping-for-journalists-ideas-concepts-and-tips-cij-summer-school-2019)
* The [second presentation on tools, using Outwit Hub and Workbench to explore scraping techniques is on Slideshare here](https://www.slideshare.net/onlinejournalist/scraping-in-60-minutes-cij-summer-school-2019)

## Scraping in Google Sheets

* [Here's the tutorial on using scraping function in Google Sheets](https://github.com/paulbradshaw/CIJSS_scraping/blob/master/scrapingfunctions.md)
* You can also [follow this tutorial by Dan Wainwright](https://onlinejournalismblog.com/2016/11/29/how-the-bbc-england-data-unit-scraped-airport-noise-complaints/)

## Scraping in Outwit Hub

OutWit Hub is particularly useful for: 

* Situations where data is spread across a series of pages (e.g. with 'next' links)
* Situations where you have to log in, or where cookies may be involved
* Bulk-downloading of documents or images for analysis on your own computer

However, the free version only scrapes 100 rows of data. You need to pay for the Pro version.

## Scraping in Workbench

Workbench has 3 scraping tools: a HTML table scraper, a webpage scraper, and a Twitter scraper. 

* [Here is an example of a HTML table scraper](https://app.workbenchdata.com/workflows/22852/) - note that new data overwrites old data (although a copy is stored), so it is not easy to combine all the results if old data disappears from the page.
* [Here is an example of a webpage scraper](https://app.workbenchdata.com/workflows/22850/) - note that you need Xpath to extract specific parts
* [Here is an example of a Twitter scraper](https://app.workbenchdata.com/workflows/25739/) - there are lots of additional tabs here which contain all sorts of analysis and cleaning you can do with Workbench

## Examples

I keep examples of stories that have used scraping on Pinboard at [https://pinboard.in/u:paulbradshaw/t:scrapingeg](https://pinboard.in/u:paulbradshaw/t:scrapingeg) - you can drill down to more specific examples by adding `+` and a particular topic, e.g. [https://pinboard.in/u:paulbradshaw/t:scrapingeg+sport](https://pinboard.in/u:paulbradshaw/t:scrapingeg+sport) will narrow down to examples related to sport.

Here are some of the examples in the slides, with a little explanation:

* Channel 4 News: [Why is the government website carrying fake jobs?](http://www.channel4.com/news/why-is-government-website-carrying-fake-jobs)  [(video)](https://www.youtube.com/watch?v=Efr-VEkwWoM) - this was based on a scrape of the Universal Jobmatch website by a non-journalist, who the reporter worked with.
* Daily Mirror: [Which singer has the best vocal range in the UK - No, it's not who you think](http://www.mirror.co.uk/news/uk-news/singer-best-vocal-range-uk-4323076) - a great example of spotting a story in a website which isn't explicitly 'data': each page on MusicNotes.com contains the vocal range, among other pieces of information - see [this example](https://www.musicnotes.com/sheetmusic/mtd.asp?ppn=MN0053340&intcmp=Recommended)
* BuzzFeed: [The Tennis Racket](https://www.buzzfeednews.com/article/heidiblake/the-tennis-racket) - tennis results and odds needed to be scraped to establish unusual patterns
* BBC News: [David Cameron's prime questioners](http://www.bbc.co.uk/news/uk-politics-26231651) - scraped Prime Minister's Questions to see which names appeared the most
* NOS [investigated the modelling industry](https://www.youtube.com/watch?v=DWRGqmywNYs&t=2m10s) using 25 different scrapers (around 20 were basic, a few needed more work)
* New York Times: [Inside the Evolving Hotel Bathroom](http://www.nytimes.com/2013/12/15/travel/inside-the-evolving-hotel-bathroom.html?pagewanted=all) - based on a scrape of hotel reviews and a text analysis
* Sunday Post: [Council sick days cost taxpayers £250m](http://paulbradshaw.tumblr.com/post/66183765520/council-sick-days-cost-taxpayers-250m-follow) - based on a scrape of Excel spreadsheets published by every council in Scotland.
* Independent (also Guardian and others): [Seb Coe promised an 'uplifting torch relay to inspire a generation'. So are these really the role models to do it?](http://www.independent.co.uk/sport/olympics/seb-coe-promised-an-uplifting-torch-relay-to-inspire-a-generation-so-are-these-really-the-role-models-to-do-it-7815150.html) - one of the earliest stories based on a scrape of the Olympic Torch Relay website. All the stories to come from the investigation can be found in the free ebook [8000 Holes: How the Olympic Torch Relay Lost its Way](https://leanpub.com/8000holes)
* BBC News: [Libraries lose a quarter of staff as hundreds close](http://www.bbc.co.uk/news/uk-england-35707956) - based on a combination of FOI requests and scraping hundreds of reports by CIPFA.
* BBC News: [Check NHS cancer, A&E and operations targets in your area](http://www.bbc.co.uk/news/health-41483322) - based on live scraping of NHS 'sitrep' spreadsheets, but also manual checking and cleaning.
* BBC News: [Help to Buy Isa scheme 'helps lucky few'](http://www.bbc.co.uk/news/uk-england-36424548) - based on a scrape of Zoopla, who were approached to obtain permission. The scraped data was more detailed than Zoopla were able to easily provide.

## What makes a website suitable for scraping?

Ultimately, it comes down to **structure**:

* A HTML table (using the `<table>` tag) is the easiest thing to scrape.
* Alternatively, other HTML structures such as tags or attributes (e.g. `<class>`) can be used
* Another structure might be *textual*, e.g. the information is always preceded by a particular string of characters.
* URL structures are also important. Examples include:
  * Pagination, e.g. `p=1`, `p=2` and so on.
  * Search criteria may be encoded in the URL in **key-value** pairs, e.g. `category=companies`
  * ID codes that refer to entities being described, e.g. `SchoolID=5323320`
* Website structures: often it is possible to start from an 'index' page that links to all the pages or documents that you want to scrape.

URLs can often be simplified: many sites insert keywords into URLs for SEO or analytics purposes which can be removed without preventing the URL from working. For example in Reed jobs URLs the job title part can be replaced by anything - it is only the code for the job which is essential.

## How easy is it to scrape a website?

Different challenges require different skills and tools. Broadly speaking factors affecting difficulty include:

* Check if there is an API for the data (e.g. Mediawiki for Wikipedia) - this is designed to be queried to collect data, in other words to be 'scraped'
* HTML tables are the easiest - these can be scraped by most tools
* HTML tags are somewhat harder
* Textual patterns come next
* Generating the list of pages to scrape may add further difficulty
* Websites which require cookies are problematic, but there are ways to scrape these
* Document types add further difficulty: XML and JSON are still data formats but will need converting
* XLS and XLSX files are more difficult still
* PDFs present the highest level of difficulty - if they are scanned PDFs then you will need to consider an OCR (optical character recognition) stage

## Tools

* [Outwit Hub](https://www.outwit.com/products/hub/)
* [Workbench](http://workbenchdata.com)
* [IFTTT](http://ifttt.com/)
* [Open Refine](http://openrefine.org/download.html)
* Chrome extensions including [Web Scraper](http://webscraper.io/) and [Grepsr](https://www.grepsr.com)
* [Morph.io](https://morph.io/)

[Other scraping tools can be found in my bookmarks](http://pinboard.in/u:paulbradshaw/t:scraping+tools)

## Law and ethics

* [Ethics in data journalism: mass data gathering – scraping, FOI and deception](https://onlinejournalismblog.com/2013/09/18/ethics-in-data-journalism-mass-data-gathering-scraping-foi-and-deception/)
* [TO SCRAPE OR NOT TO SCRAPE: TECHNICAL AND ETHICAL CHALLENGES OF COLLECTING DATA OFF THE WEB](http://www.storybench.org/to-scrape-or-not-to-scrape-the-technical-and-ethical-challenges-of-collecting-data-off-the-web/)
* [Resources on ethics and scraping bookmarked here](http://pinboard.in/u:paulbradshaw/t:scraping+ethics)
* [Resources on law and scraping bookmarked here](http://pinboard.in/u:paulbradshaw/t:scraping+law)

## Resources

* The book [Scraping for Journalists](https://leanpub.com/scrapingforjournalists) covers scraping using Google Sheets and tools like OutWit Hub, plus programming techniques for scraping databases, spreadsheets and PDFs.
