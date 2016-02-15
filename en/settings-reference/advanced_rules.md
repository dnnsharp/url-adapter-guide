# Advanced Rules

This section lets you write rules that match directly against URLs. They are per host, so apply to all URLs regardless of which is the current portal. Later on, we'll plan to also add Advanced Rules per portal.

In many cases they can be interchanged with Custom Rules. The difference is that with Advanced Rules you'd normally target a class of redirects with one rule, while with Custom Rules you'd do one at a time. If you end up doing one Advanced Rule for every redirect, and these refer to DNN pages, it's highly recommended to switch to Custom Rules as it may perform faster and be easier to understand.

Here are just a few cases when Advanced Rules are most appropriate:
* **Redirect a class of URLs**
<br/>For example, redirect all incoming request from `/products.aspx?id={id}` to `/we-re-out-of-stock.aspx`

* **Rewrite a class of URLs**
<br />Note that when you're doing rewriting through Advanced Rules, you'll most likely end up with 2 rules: one redirecting from old url to new url, one one that rewrites the new url to old url.
For example, originally you had `/articles.aspx?title=My Article` and you wish to use `/articles/My article.aspx` instead. First, write a redirect rule that sends the users to the new page. Then, a second rule will rewrite the rule, so even if the browser address bar displays `/articles/My article.aspx`, in fact the server components see the original `/articles.aspx?title=My Article` which they can handle.

Domain redirect
So you've changed domain from old-unattractive.com to new-cool.com? Write a rule to permanently redirect traffic to the exact path on the new domain.

Pass Query String parameters
The Custom Rules will map to a page and you don't have the ability to pass additional parameters in query string. This may change in the future, but if this is the case, then you'll need Advanced Rules.
