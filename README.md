# Introduction to Scraping

*Resources for a short class introducing scraping*.

Start here: [this is a webpage](http://www.numbeo.com/pollution/country_result.jsp?country=United+Kingdom) that publishes data on various types of pollution. 

Look at the URL: it has a pattern: `http://www.numbeo.com/pollution/country_result.jsp?country=United+Kingdom`

Click on one of the city links: [this is the page for London](http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=London). Some things to look for:
* The page has a similar **structure** to the last one - that's a pattern that helps us.
* The **URL** has a similar structure: `http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=London`

Can we generate URLs for other cities? Try:
* `http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=Birmingham`
* `http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=Manchester`

What happens when you add a city with a space in the name?

* `http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=milton%20keynes`

The URL **replaces the space** with `%20`

## Writing a scraper function in Google Sheets

We can try to scrape the page by using the `IMPORTHTML` function in Google Sheets. Here's an example:

`=IMPORTHTML("http://www.numbeo.com/pollution/city_result.jsp?country=United+Kingdom&city=London","table",1)`

What is this `IMPORTHTML`?

* `IMPORTHTML` is a **function** in Google Sheets. Functions are words that mean 'use a recipe'. The `SUM` function, for example, is a recipe for adding up a bunch of numbers. Other commonly used functions in spreadsheets include `AVERAGE`, `MEDIAN` and `COUNT`.
* Some functions work in all spreadsheet software, but `IMPORTHTML` is specific to Google Sheets. **It will not work in Excel**. 
* Functions are always followed by parentheses, and normally those parentheses include the *ingredients* for the recipe. Those ingredients are called 'arguments' or 'parameters'.
* Different functions require different numbers of arguments: `IMPORTHTML` needs 3 arguments, which are explained below.
* Functions are a core part of programming. If you want to write more advanced scrapers using languages like Python, Ruby, PHP or R, you will need to use functions too. Using them in spreadsheets is a good way to familiarise yourself with how they work.

Let's break the formula down:

* The `=` sign tells the spreadsheet we want it to do some work, not just store data we are entering
* Then we have the function, followed by ingredients in parentheses
* There are 3 ingredients
* The first ingredient is the URL of the page you want to scrape - **in quotation marks**. The quotation marks are important: if you don't use quotation marks the spreadsheet software will assume you are naming another function.
* The second ingredient is what you want to scrape from that page. There are only two options here: `"table"` or `"list"`. The first looks for the `<table>` tag; the second looks for the `<ul>` or `<ol>` tag (unordered list or ordered list).
* The third ingredient specifies *which* table or list you want to scrape: `1` means the first table or list, `2` the second, and so on.


