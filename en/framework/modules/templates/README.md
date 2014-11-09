Templates Module <a name="docs_home"></a>
=========================================

### Templates Functions & Variables

The Templates Module features the following functions:

* [`$.fn.blockstrap.templates.bootstrap`(type)](#templates_bootstrap)
* [`$.fn.blockstrap.templates.filter`(html, placeholders, replacements)](#templates_filter)
* [`$.fn.blockstrap.templates.process`(data, html)](#templates_process)
* [`$.fn.blockstrap.templates.render`(slug, callback, refresh)](#templates_render)

--------------------------------------------------------------------------------

#### `templates.bootstrap`(type) <a name="templates_bootstrap" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function will return the raw Mustache-compliant HTML template from `$.fn.blockstrap.snippets[key]`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `templates.filter`(html, placeholders, replacements) <a name="templates_filter" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function will return the sent `html` after having replaced all instances of each item in the `placeholders` array with the corresponding replacement found with the `replacements` array. Please note that the placeholder should be placed in-between two curly brackets within the `html` and that if no placeholders or replacements are provided it will use the following placeholders array:

<!--pre-javascript-->
```
var placeholders = [
    'urls.root', 
    'user.name',
    'vars.txid',
    'vars.key',
    'tx.size',
    'tx.time',
    'tx.block',
    'tx.input',
    'tx.output',
    'tx.fees',
    'address.tx_count',
    'address.balance'
];
```

And the following replacements array:

<!--pre-javascript-->
```
var replacements = [
    $.fn.blockstrap.settings.base_url,
    name,
    txid,
    key,
    tx.size + ' (Bytes)',
    tx.time,
    tx.block,
    parseInt(tx.input) / 100000000 + ' ' + tx_currency,
    parseInt(tx.output) / 100000000 + ' ' + tx_currency,
    parseInt(tx.fees) / 100000000 + ' ' + tx_currency,
    account.tx_count,
    parseInt(account.balance) / 100000000 + ' ' + add_currency
];
```

Assuming you were viewing the [DEMO WALLET](http://demo.blockstrap.com/wallet/v0.4.0.1/), this `html`:

<!--pre-html-->
```
<a href="{{urls.root}}">Homepage</a>
```

Would become:

<!--pre-html-->
```
<a href="http://demo.blockstrap.com/wallet/v0.4.0.1/">Homepage</a>
```

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `templates.process`(data, html) <a name="templates_process" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function takes the provided `data`, runs it through [`core.filter`](../../core/core-functions/#bs_filter), combines it with the `html` variable using [mustache templating](../../assets/mustache/) and then filters the rendered results using [`template.filter`](#templates_filter) before returning the final output.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `templates.render`(slug, callback, refresh) <a name="templates_render" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used to render page content by using the `slug` to collect data and HTML as follows:

<!--pre-javascript-->
```
var $bs = blockstrap_functions;
var data_url = 'themes/' + bs.settings.theme + '/' + bs.settings.data_base + slug;
var html_url = 'themes/' + bs.settings.theme + '/' + bs.settings.html_base + slug;
```

It then filters the collected data ([`$.fn.blovkstrap.core.filter`](../../core/core-functions/#bs_filter)), combines it with the HTML using [mustache templating](../../assets/mustache/) and then filters the rendered results using [`template.filter`](#templates_filter), at which point if `refresh` is set to true or the current `slug` is the homepage of the application, the current DOM will be replaced with new content.

If the `refresh` is not set or the current `slug` is not the homepage, the application will instead update the content by using `$.fn.blockstrap.settings.content_id`.

<a href="#docs_home"><small>- back to top</small></a>

---

1. Related Articles
2. [Back to Modules](../../modules/)
3. [Accounts](../accounts/)
4. [API](../api/)
5. [Buttons](../buttons/)
6. [Contacts](../contacts/)
7. [Currencies](../currencies/)
8. [Data](../data/)
9. [Filters](../filters/)
10. [Forms](../forms/)
11. [Security](../security/)
12. [Styles](../styles/)
13. [Templates](../templates/)
14. [Table of Contents](../../../)
