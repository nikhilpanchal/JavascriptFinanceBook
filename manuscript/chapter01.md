#Getting Started with JavaScript

Much of our coding time is spent in an interactive environment, colloquially called the 'REPL', 'Read-Eval-Print Loop' or console.

The REPL reads input, evaluates it according to our code and prints it.

Javascript's REPLs, can be found in any browser, by pressing Ctrl+Shift+J, Command+Shift+J or F12 depending on your system (Firefox users may prefer 'K' over 'J').

Do some maths,

~~~~~~~~
1+1
~~~~~~~~

~~~~~~~~
>> 2
~~~~~~~~

or

~~~~~~~~
Math.log(Math.E)
~~~~~~~~

~~~~~~~~
>> 1
~~~~~~~~

##Welcome to the Web's OS

Every environment's console or REPL has its own flavour.

The UNIX command line is built around a file system. The Excel scripting environment's basic unit of currency is the spreadsheet.

The basic unit for Javascript is the web page.

Go to,

[http://dev.markitondemand.com/Api/v2/Quote/json?symbol=AAPL](http://dev.markitondemand.com/Api/v2/Quote/json?symbol=AAPL)

open the REPL or console, and type this

~~~~~~~~
location.reload();
~~~~~~~~

then

~~~~~~~~
JSON.parse( $('pre').innerHTML );
~~~~~~~~

which will result in this,

`>> Object { Status: "SUCCESS", Name: "Apple Inc", Symbol: "AAPL", ... }`

What have we just done?

The Markit API reports market action in real time (while markets are open). 

We first reload the web page to pull in the latest available information, and then parse the page's text into a format which JavaScript understands.

Javascript's lingua franca is objects (or 'JSON'). Each object has keys and values. We use keys to access the data we are interested in.

E.g.

~~~~~~~~
JSON.parse( $('pre').innerHTML ).LastPrice;
~~~~~~~~

will show the 'value' for the 'LastPrice' key,

`>> 113.48`

HTML web pages can be parsed in a similar manner, although by 'parse' I really mean 'scrape'.

For example go to, [one of Google finance's historical price pages](https://www.google.com/finance/historical?q=NYSEARCA%3ARSP&ei=X7D-VeC-NNCDsAHunLjoAQ).

Using code we will learn more about in the coming chapters, type or paste this line of code into the REPL,

~~~~~~~~
[].slice
 .call(
  $$('.gf-table.historical_price td')
  )
 .filter(
  (_,i) => i % 6 === 4
  )
 .map(
  i => +i.innerHTML
  );
~~~~~~~~

`>> [75.37, 77.04, 77.18, ... ]`

We select the HTML table containing historical data and have filtered every 6th number in the table which happens to coincide with each close price in the table.

As you can see, scraping HTML is trickier than parsing APIs - nevertheless Javascript is born to swim on the web.

##More Info

1) Take a look at [Google](https://developer.chrome.com/devtools/docs/console) and [Mozilla's](https://developer.mozilla.org/en/docs/Web/API/console) browser console reference pages.

2) The $() and $$() functions utilise [CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Getting_Started/Selectors) to search web pages.

##Try

1) Find a JSON API to parse or web page to scrape
2) Read up on JSON
3) [Watch](https://www.youtube.com/watch?v=v2ifWcnQs6M) Douglas Crockford's (the creator of JSON) talk about Javascript
