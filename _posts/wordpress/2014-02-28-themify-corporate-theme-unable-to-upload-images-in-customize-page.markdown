---
layout: post
comments: true
---
1) Customisation panel uploading portion no response

![couldn't upload](http://i.imgur.com/d4I6x3c.png)

2) Found out that there is an javascript error:

```
wp.media is undefined
```

3) Googled and found this [link](https://wordpress.org/support/topic/wpmedia-is-undefined):

Add the following script to custom-functions.php
Note: If you do not have a custom-functions.php, create one in the theme folder.

```php
<?php
/* Load media files needed for Uploader */
function load_wp_media_files() {
  wp_enqueue_media();
}
add_action( 'admin_enqueue_scripts', 'load_wp_media_files' );
?>
```
4) Works flawlessly.

![awesomeeee!](http://i.imgur.com/e5Jwhvv.png)
