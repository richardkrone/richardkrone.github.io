---
layout: post
title: "Regular Expressions and Redirects in WPENGINE.com"
date: 2023-08-24 08:00:00 -0400
categories: wpengine regex
---

Recently, while working in wpengine.com on a 301 redirect, I decided to look into using regular expressions in a more effective way to catch trailing forward slash (/) cases in WordPress. The way, up until this point, was to add two independant rules to deal with the issue of the URL having, or not having, a trailing forward slash (/).

Regex Original
{% highlight regex %}
Rule 01: ^/unicorns?$
// Catches all URLS without a trailing forward slash (/)

Rule 02: ^/unicorns/?$
// Catches all URLS with a trailing forward slash (/)
{% endhighlight %}

Regex Improved
{% highlight regex %}
Rule 01: ^/unicorns[/]?$
// Catches all URLS, with or without, a trailing forward slash (/)
{% endhighlight %}

<h2>Case Insensitivity</h2>
Taking this 1 step further, we have modified the regex expression to be case insensitive. As we do not have direct control over what a user types into the browser URL bar we must try to account for potential edge cases.

While webservers treat capitilization in a URL as different URLs the reality is that the people doing the typing rarely pay attention to the case of the URL. To simplify things we remove the issue by adding in the regex to force case insensitivity. This works fine unless your intentionally serving pages that are case sensitive.

{% highlight regex %}
Rule 01: ^/unicorns[/]?$
// Case Sensitive
{% endhighlight %}

{% highlight regex %}
Rule 01: ^(?i)/unicorns[/]?$
// Case Insensitive thanks to adding in (?i) after the ^
{% endhighlight %}

Notes
https://wpengine.com/support/regex/

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
