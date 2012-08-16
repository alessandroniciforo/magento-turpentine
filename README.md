# Nexcess.net Turpentine Extension for Magento

Turpentine is a Magento extension to improve Magento's compatibility with
[Varnish](https://www.varnish-cache.org/), a very-fast caching reverse-proxy. By
default, Varnish doesn't cache requests with cookies and Magento sends the
__frontend__ cookie with every request causing a (near) zero hit-rate for Varnish's cache.
Turpentine provides Varnish configuration files (VCLs) to work with Magento and
modifies Magento's behaviour to significantly improve the cache hit rate.

## Features

 - Full Magento Page Caching
 - Compatible with Varnish versions 2.1 and 3.0
 - Requires very little configuration for impressive results
 - Able to apply new Varnish VCL (configurations) on the fly, without
 restarting/changing Varnish's config files
 - Cache purging by URL and content type
 - Exclude URL paths, Request Parameters (__SID, __store, etc), cookies from caching
 - Configure cache TTL by URL
 - Ability to force static asset caching even after an action that disables
 caching for a client
 - Supports multiple Varnish instances for clustered usage

## Requirements

 - Magento Community Edition 1.6+ (earlier versions may work but have not been tested)
 - Varnish 2.1+

## Installation

 1. Install Varnish

  * Ensure that any Varnish instances that will be used have the management
  interface (-T option) enabled and are accessible from the web server(s) that
  Magento is running on.

 2. Install this Extension

  * [modman](https://github.com/colinmollenhour/modman) or MagentoConnect can
  be used (once this extension is actually on MagentoConnect)

 3. Configure the Varnish instance(s) and backend

  * The default is to connect to the Varnish management interface on localhost:6082
  and the backend on localhost:80 which will may not need to be changed for testing
  * Once the testing is complete and you're ready to go live, you can change backend
  setting and then change the web server's listening port

## Known Issues

 - Logging and Statistics will show all requests as coming from the same IP address
 (usually localhost/127.0.0.1). It should be possible to work around this using
 Apache's [mod_remoteip](http://httpd.apache.org/docs/trunk/mod/mod_remoteip.html)
