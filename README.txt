Fastly
=======================

http://drupal.org/project/fastly

What Is Fastly?
---------------

Fastly is a CDN (Content Delivery Network), which is to say, we speed up
delivery of your website and its content to your users. When your client in
Moscow, Montana or Vriezenveen, Netherlands clicks on your site requesting
a piece of information, we want them to feel your speed of delivery. No
waiting. We want them to get to your closest point of presence—in
milliseconds—to get what they want.

Founded in 2011 Fastly delivers the world's only real-time content delivery
network. At Fastly we think slow is unacceptable. Fastly enables a
next-generation of businesses to give their users the best online and mobile
experience. The patent-pending Fastly Caching Software delivers static,
dynamic and streaming content with the lowest recorded time to first byte.
Our customers include (but certainly aren't limited to) Twitter, Guardian
UK, GitHub, AddThis, Wikia, Shazam, Wanelo, and Yammer.

Fastly is a San Francisco based company, located in the heart of SOMA.
We are venture backed by Battery Ventures, OATV, August Capital, and Amplify
Partners. We provide challenging work, opportunities to learn, high-quality
teammates and, most importantly, we have a lot of fun doing what we love.
We offer some great benefits like a Tahoe ski cabin, stocked fridge,
flexible schedules, lots of company happy hours, and a no-vacation policy.
We are close to MUNI and BART, and Caltrain is just a pleasant 15-minute stroll.

We offer competitive compensation, stock options, and health benefits.


Module Features
---------------

1. Account Sign In. If you are already an authenticated Fastly user,
You can simply enter an API token and a list of service will show up in a
drop down.

2. Automated Purging. Content will be automatically purged when updated/created.
This is done using Drupal 8's CacheTagsInvalidatorInterface.

How To Install The Module?
--------------------------

1. Install Fastly (unpacking it to your Drupal
/modules directory if you're installing by hand, for example).

2. Fastly will appear in your Configuration > Web services menu section.

3. Enter your Fastly API token in the settings form and then select your service.

4. *IMPORTANT* Make sure you click Upload Fastly VCL snippets. Although this step is not
required it improves caching and enables features such as serve stale on errors etc.

If you find a problem, incorrect comment, obsolete or improper code or such,
please search for an issue about it at http://drupal.org/project/fastly/issues
If there isn't already an issue for it, please create a new one.

TLS and Fastly
--------------
Fastly can support TLS connections.
See https://docs.fastly.com/guides/securing-communications for a list showing
different options available. If you are using TLS, you should add the following
lines of code to your settings.php

// Enable Fastly TLS connections.
if (!empty($_SERVER['HTTP_FASTLY_SSL'])) {
  $_SERVER['HTTPS'] = 'on';
}

FASTLY API TOKEN
________________
You can change it in settings form or you can use environment variable FASTLY_API_TOKEN to set it also.
If you set this key via environment variable you will hide this entry on the config form.

FASTLY SERVICE ID
_________________
A Service represents the configuration for your website to be served through Fastly. You can override this with
FASTLY_API_SERVICE environment variable. If you set this key via environment variable you will hide this entry on the
config form.

FASTLY SITE ID
______________
Site identifier which is being prepended to cache tags. You can change it in settings form. Use this if you have
multiple sites in the same service in Fastly. Note: You can use the environment variable FASTLY_SITE_ID
to set this also. If nothing is set in either config or environment variable then one will be randomly generated for
you.

FASTLY CACHE TAG HASH LENGTH
____________________________

For sites with more content, it may be necessary to increase the length of the hashed cache tags that are used for the
<code>Surrogate-Key</code> header and when purging content. You can change it in settings form.
This is due to hash collisions (https://en.wikipedia.org/wiki/Hash_table#Collision_resolution) which will result in
excessive purging of content if the key length is too short.
Note that this number should not be as large as the total number of cache tags in your site, just high enough to
avoid most collisions during purging. Also you can override this with environment variable FASTLY_CACHE_TAG_HASH_LENGTH.
