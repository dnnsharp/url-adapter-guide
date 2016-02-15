# FAQs

#### 1. I've redone a PHP website in DNN. I want to save SEO, so how do I permanently redirect old URLs to new DNN pages?

First think to keep in mind is that your new IIS server will probably not handle .php extension, or will handle it using the PHP engine. If that happens, DNN never executes so URL Adapter doesn't get the chance to do the redirects. To map the .php extension to Asp.NET handler:

For IIS 7+
1. Open IIS > Handler Mappings > Add Managed Handler
2. Under Request Path, add *.php
3. Under Type, add System.Web.UI.PageHandlerFactory
4. Under name, type anything you want, but make it descriptive (Php2DNN is a good name)
5. When done, click OK

For IIS 6
* Pretty much the same thing, only make sure to take out Check If File Exists option.