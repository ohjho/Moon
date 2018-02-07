---
layout: post
title:  "Fixing a broken Wordpress Installation"
date:   2018-02-07
excerpt: ""
categories: dev
tags: [wordpress, mysql]
comments: true
---

## My wordpress blog is dead!
Have you seen this before when going to your wordpress page after having been away for quite sometime:

![what happened???][img_wp_error]

This [page][2] has list out a couple possible reasons. But I think the main reason is...

Your Wordpress installation has automatically updated to a new version but some plugins you use is behind. The outdated plugins caused the site to fail. Now you need to **deactivate all plugins**
{: .notice}

## Deactivate Plugins
There are two ways! See [ref][1].

### Hard deactivate: Change the plugin folder name
```sh
# start form the dir where wordpress is installed
$ cd wp-content
$ mv plugins/ plugins_deactivate
```

### Doing it properly: in MySQL
connect to the WordPress mySQL DB, you will edit the wp_options table:
```sql
udpate wp_options
set option_value ="a:O:{}"
where option_name = "active_plugins";
```

Done this way, you could go back to the wp-admin page and turn the plugins back on one by one.

[img_wp_error]: http://cdn.wpbeginner.com/wp-content/uploads/2018/01/internalservererror-example.png
[1]: http://www.wpbeginner.com/plugins/how-to-deactivate-all-plugins-when-not-able-to-access-wp-admin/
[2]: http://www.wpbeginner.com/wp-tutorials/how-to-fix-the-internal-server-error-in-wordpress/
