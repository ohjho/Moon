---
layout: post
title:  "Setting up OwnCloud on Dreamhost Shared Server"
date:   2018-04-11
excerpt: ""
categories: dev
tags: [dreamhost, OwnCloud]
comments: true
---

## What to Host your own File Server?
After read [this][1] I was sold on getting my [ownCloud][url_owncloud]!  

I use Dreamhost shared server. And I followed [this][2] installation guide. And first tried to install the lastest version, 10.0.7, using both the manual and web installer method. But both times got the following error message after installation:
```
    PHP module intl not installed.
    Please ask your server administrator to install the module.

    PHP modules have been installed, but they are still listed as missing?
    Please ask your server administrator to restart the web server.
```

And this seems like a [bug][3]. So I installed 10.0.3 per the example in the [guide][2].

### Word of advice:  

Make sure the PHP version you are using matches ownCloud's [requirements][4].
{: .notice}

My site was running PHP 7.2 so I had to to into the Dreamhost Control Panel to change it to 7.1


[1]: https://lifehacker.com/5993596/how-to-set-up-your-own-private-cloud-storage-service-in-five-minutes-with-owncloud
[2]: https://help.dreamhost.com/hc/en-us/articles/216472487-How-to-install-ownCloud
[3]: https://github.com/owncloud/core/issues/30498
[4]: https://doc.owncloud.org/server/10.0/admin_manual/installation/system_requirements.html
[url_owncloud]: https://owncloud.org/download/#instructions-server
