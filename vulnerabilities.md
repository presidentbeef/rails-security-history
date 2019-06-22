---
layout: default
title: Ruby on Rails Vulnerabilities
---

This is a collection of historical Ruby on Rails vulnerabilities, originally based on the talk "The Evolution of Rails Security" by Justin Collins presented at RailsConf 2018.

# July 2004

Ruby on Rails is released to the world!

# December 2005

Rails 1.0 is released!

https://weblog.rubyonrails.org/2005/12/13/rails-1-0-party-like-its-one-oh-oh/

# August 2006

## CVE-2006-4111/CVE-2006-4112 

This was the first Ruby on Rails CVE!

https://weblog.rubyonrails.org/2006/8/9/rails-1-1-5-mandatory-security-patch-and-other-tidbits/

https://weblog.rubyonrails.org/2006/8/10/security-update-rails-1-0-not-affected/

https://weblog.rubyonrails.org/2006/8/10/rails-1-1-6-backports-and-full-disclosure/

https://blog.evanweaver.com/2006/08/12/anatomy-of-an-attack-against-1-1-4/

# October 2007

## CVE-2007-5380

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
