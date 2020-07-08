Tests for rel=prefetch and HTTP/2 prioritisation, results were writen up in this post: https://andydavies.me/blog/2020/07/08/rel-equals-prefetch-and-the-importance-of-effective-http-slash-2-prioritisation/

Not all the test pages were used for post.

Each page has this set of prefetch Resource Hints added - see notes for location in each URL

```
<link rel="prefetch" href="https://www.wikipedia.org/portal/wikipedia.org/assets/img/Wikipedia-logo-v2.png" as="image" />
<link rel="prefetch" href="dummy-subresources/styles.css" as="style" />
<link rel="prefetch" href="dummy-subresources/scripts.js" as="script" />
<link rel="prefetch" href="dummy-subresources/image.jpg" as="image" />
```

Page         | Notes
-------------|-------------
/test-rel-prefetch/tests/electro/index-prefetch-subresources.html | Near the top of <head>, hints include as attribute
/test-rel-prefetch/tests/electro/index-prefetch-subresources-no-as.html | Near top of <head>, hints omit as attribute
/test-rel-prefetch/tests/electro/index-prefetch-subresources-no-font.html | Near top of <head>, hints have as attribute, no webfont used
/test-rel-prefetch/tests/electro/index-prefetch-subresources-top-with-preconnect.html | Near top of <head>, hints have as attribute, preconnect to wikimedia domain
/test-rel-prefetch/tests/electro/index-prefetch-subresources-top-with-preconnect-no-as.html | Near top of <head>, hints omit as attribute, preconnect to wikimedia domain
/test-rel-prefetch/tests/electro/index-prefetch-subresources-bottom.html | At bottom of body, hints include as attribute
/test-rel-prefetch/tests/electro/index-prefetch-subresources-bottom-no-as.html | At bottom of body, hints omit as attribute

Tests are available via github pages e.g. https://andydavies.github.io/test-rel-prefetch/tests/electro/index-prefetch-subresources.html

GH pages use Fastly so should exhibit the behaviour of a server that has good support for HTTP/2 Prioritisation.

I can't quite remember why I wrote tests without the as attribute will update the readme if I do.