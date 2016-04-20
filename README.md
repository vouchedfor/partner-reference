# partner-reference
Partner reference site, with simple demos

* [VouchedFor Search on Partner sites](#vouchedfor-search-on-partner-sites)
  * [Pre-requisites] (#pre-requisites)
  * [How it works] (#how-it-works)
* [Code Example](#code-example) 

## VouchedFor Search on Partner sites
This guide shows how to incorporate a VouchedFor search box into a partner site . The advantages of this method are: 
* the partner retains control of the look and feel, 
* any enquiries to advisors are associated with the partner, and 
* it’s simple and inexpensive to implement.

### Pre-requisites
Before getting started, you need to get the following tracking information from the VouchedFor partners team.

| Name     | Description                                                  | Example                  |
|----------|:-------------------------------------------------------------|:-------------------------|
| source   | where the traffic originates                                 | partner-website.com      |
| medium   | the marketing medium, eg, print, billboard, guide, affiliate | affiliate                |
| campaign | Specific marketing campaign/initiative                       | search_financial_adviser |

### How it works
The partner adds a location search box (and optionally other filters) and a submit button. When the user presses submit the partner site generates a VouchedFor Search Results URL and instructs the browser to go to that URL, typically within the same browser window. 

Based on the URL, the site will run a search for the location (and apply optional filters) and show the standard search results.

## Code Example

If you want to jump straight into the example, go to [../blob/master/searchbox.html]
