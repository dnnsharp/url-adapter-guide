# Examples

## How to redirect `http://site.com` to `http://www.site.com`

There are two methods in which this can be achieved:

1. Use the `Portal Aliases` settings to choose how the site is accessed:
    * When it is set to `any` both URL types are accepted.
    * When it is set to `www` only `www.` URLs will be accepted and redirects will be made to accomplish that.
        * **Note:** when this option is selected a check-box will show up that changes the behavior for sub-domains. When that option is checked sub-domains will be accessible without the `www.` in front of them.
    * When it is set to `non-www` only URLs without `www.` will be accepted.

* Use the `Advanced Rules` settings:
    * When you need to redirect a site or any URLs which are not using `www.` and you want to force them to use `www.` for all `http://` or `https://` calls, then you need to create an Advanced Rule in URL Adapter like:
    
    ```
    Match In: Absolute URL
    Condition: http://site.com/{*}
    Target URL: http://www.site.com{*}
    Type: Redirect
    ```
    * In this way, only the specified portal will be "affected" by the advanced rule, and if you have, for example, other portals like `http://blog.site.com`, it will remain without `www`.
    
## Redirects to https://

URL Adapter also provides the ability to redirect all `http://` traffic to `https://` - it respects the HTTPS settings made in DNN (Admin > Site Settings and page settings), therefore, pages checked as secured should be served with `https://`.

There is also an advanced rule if you want to redirect from `http://` to `https://` without relying on DNN settings:
```
Match In: Absolute URL
Condition: http://site.com/{*path}
Target URL: https://www.site.com{*path}
Type: Redirect
```
