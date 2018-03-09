---
layout: post
title:  "Cloning a Wordpress Installation"
date:   2018-03-09
excerpt: ""
categories: dev
tags: [wordpress, mysql]
comments: true
---

## Need to Clone a wordpress blog?
I needed to move some old WP blog that I'm not using to a legacy location. But whatever your reason is. Here's now I did it by following mostly this [link][1] and this [one][2].

### Copy files to the new location
After you got the URL set up for the clone.

In SSH:
```sh
# copy all the wp files to the clone location
cp -a blog.originalwp.com/. new.clonewp.com/
```

### Create the Clone WP DB
This IMO took the most work. And you need to set it up in your hosting provider's dashboard.

More instructions are [here][3]

### Home Stretch
Last couple steps are super easy
1. [Update wp-config.php][4]
2. [Update siteurl or home in the DB table wp_*options][5]
3. Login via `new.clonewp.com/wp-admin` and install the plugin [**Better Search Replace**][6]  
  Use the **Better Search Replace** plugin to replace the original blog URL with the clone's URL every where in the DB.

[1]: https://www.inmotionhosting.com/support/website/wordpress/duplicate-wordpress-site-for-testing
[2]: https://torquemag.io/2015/05/how-to-duplicate-a-wordpress-website/
[3]: https://www.inmotionhosting.com/support/website/database-setup/create-database
[4]: https://www.inmotionhosting.com/support/edu/wordpress/migrating-wordpress-inmotion-hosting/configuring-wordpress-after-a-migration
[5]: https://www.inmotionhosting.com/support/website/wordpress/wordpress-changing-the-site-url-and-home-settings
[6]: https://wordpress.org/plugins/better-search-replace/
