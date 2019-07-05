---
layout: default
title: Ruby on Rails Vulnerabilities
---

This is a collection of historical Ruby on Rails vulnerabilities, originally based on "[The Evolution of Rails Security](https://www.youtube.com/watch?v=Btrmc1wO3pc)" presented by [Justin Collins](https://github.com/presidentbeef/) at RailsConf 2018.

# July 2004

Ruby on Rails was released to the world as version 0.5.0.

# December 2005

At the end of 2005, Rails 1.0 was announced!

https://weblog.rubyonrails.org/2005/12/13/rails-1-0-party-like-its-one-oh-oh/

# August 2006

Less than a year later, the first vulnerabilities for Rails were announced.

### Sidenote - "CVE"

"Common Vulnerabilities and Exposures" is a trademark of a company called Mitre, which essentially manages these "CVE identifiers".

The reason they do this is to make it easier to talk about known vulnerabilities by referencing a CVE identifier.

## CVE-2006-4111/CVE-2006-4112

In 2006 there were two vulnerabilites that came out for Rails.

The blog posts around the vulnerabilities demonstrate the level of immaturity around handling security vulnerability announcements at the time.

In the first post, DHH starts off by promoting the work in progress on Rails 1.2.
Then the post transitions into discussing a "MANDATORY" upgrade Rails users must apply
because there is a security issue. However, the issue was so severe that the Rails team
was unwilling to disclosure what the security issue actually was. 

This style of vulnerability announcements - not disclosing the nature of the vulnerability at the time - is no longer acceptable in the security and development community.

https://weblog.rubyonrails.org/2006/8/9/rails-1-1-5-mandatory-security-patch-and-other-tidbits/

On the next day, likely in the very early morning hours, DHH posted again regarding the vulnerability.
In this post he says there are only a few versions affected, but it is severe and the whole team is working on it.

https://weblog.rubyonrails.org/2006/8/10/security-update-rails-1-0-not-affected/

About thirteen hours later, there is another post.
It notes that some people have started to figure out what the vulnerability is.
At the same time, the first attempt at fixing it was not a complete fix, so a second patched version was released.

Although this post says "full disclosure" in the title, it does not really say what the vulnerability is.
The post explains that an attacker could potentially load the "profiler", which does not make a lot sense.

https://weblog.rubyonrails.org/2006/8/10/rails-1-1-6-backports-and-full-disclosure/

The series of posts demonstrates a sense of panic.
It is likely the Rails team had never had to deal with a security issue before and as a result did not have
a good process for handling one.

Evan Weaver wrote a blog post around the time in which he attempts to uncover the actual vulnerability by looking
at code changes between Rails 1.1.4, 1.1.5, and 1.1.6.

https://blog.evanweaver.com/2006/08/12/anatomy-of-an-attack-against-1-1-4/

It was a bit difficult to tease out what those code changes were meant to fix.

Instead, he decided to instrument a test application application and go from there.

The vulnerability had something to do with how files were being automatically loaded by Rails.

In summary, the routing layer would look pretty much anywhere in the Rails application for a file matching the requested URL.
Then it would load the file. After loading and executing the file, _then_ Rails might return a 404 if nothing it loaded looked like a controller.

At the time it was not uncommon to have uploaded files be stored in the `/public/` directory within the Rails application, as well having utility
scripts in the `/script/` directory. With this vulnerability, an attacker could potentially execute any Ruby file accessible on the server.

This kind of vulnerability is referred to as "remote code execution" (RCE). More specifically, it falls under "local file inclusion" (LFI) where an existing file
on the server is loaded into the application and executed.

# October 2007

## CVE-2007-5380

This vulnerability is interesting because in order to fix the issue, the Rails team essentially dropped an entire feature of the framework.

https://weblog.rubyonrails.org/2007/10/5/rails-1-2-4-maintenance-release/

# February 2011

## CVE-2011-0447

https://weblog.rubyonrails.org/2011/2/8/csrf-protection-bypass-in-ruby-on-rails/

http://lists.webappsec.org/pipermail/websecurity_lists.webappsec.org/2011-February/007533.html

# March 2012

## Mass Assignment, GitHub, and Homakov

https://github.blog/2012-03-04-public-key-security-vulnerability-and-mitigation/

## Mass Assignment Over Time

TODO: Move to features

* Rails 2 - Optional allow/deny list of attributes defined in models
* Rails 3.1 - Option added to require allow list of attributes defined in models
* Rails 3.2.3 - Setting allowed list of attributes is enforced by default in new applications
* Rails 4 - Strong Parameters are introduced to specified allowed attributes at time of use

# January 2013

## CVE-2013-0156

### Part 1

### Part 2

# Remote Code Execution via `render`

## CVE-2014-0130

http://matasano.com/research/AnatomyOfRailsVuln-CVE-2014-0130.pdf

## CVE-2016-0752

https://nvisium.com/resources/blog/2016/01/26/rails-dynamic-render-to-rce-cve-2016-0752.html

# Sanitization-Related Vulnerabilities

(Link to sanitize vs. escape discussion)

* CVE-2011-2931
* CVE-2012-3465
* CVE-2013-1855
* CVE-2013-1857
* CVE-2015-7579
* CVE-2015-7580
* CVE-2018-8048
* CVE-2018-3741
