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

If you want to jump straight into the example, go to [searchbox.html](../master/searchbox.html). The code example uses jQuery to override `onsubmit` and update the browsers location.

### 1. Setup a form

```html
<form>
  <h3>Search for a financial adviser near you</h3>
		<input type="text" name="town_postcode" value placeholder="Town / Postcode" />
  <button>Search VouchedFor</button>
</form>
```

### 2. Construct the url

```javascript
var source = 'partner-website-name';
var medium = 'referral';
var campaign = 'search_financial_adviser';

var vertical = 'financial-advisor-ifa';

function constuct_search_url(search_query) {

    return 'https://www.vouchedfor.co.uk/' + 
            vertical + '/' +
            encodeURIComponent(search_query) +
            '?' + 
            'utm_source=' + source + '&' +
	    'utm_medium=' + medium + '&' +
	    'utm_campaign=' + campaign;
}
```
 
Note: this function encodes the search query as a URI to handle spaces in the user input.

Example output is `https://www.vouchedfor.co.uk/financial-advisor-ifa/w4%203bu?utm_source=partner-website-name&utm_medium=referral&utm_campaign=search_financial_adviser`

### 3. Put it all together

Overide the form, select the input field, then update the windoe location with the constucted URL.

```javascript
$(document).ready(function($){ 
  $('form').on('submit', function(e) {
      var input = $( 'form' ).find( 'input[name="town_postcode"]' );
      window.location.href = ( constuct_search_url( input.val() ) );
      return false;
  });
});
```

