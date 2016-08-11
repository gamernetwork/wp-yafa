# WP-Yafa

A Wordpress client plugin for the YAFA ad server:

https://github.com:gamernetwork/yafa

## Installation

```
wp plugin install https://github.com/gamernetwork/wp-yafa/archive/master.zip
wp plugin activate wp-yafa-master
```

Set your YAFA server endpoint and site code in the 'YAFA Admin' panel in Wordpress settings.

### Enable YAFA units in Wordpress theme

Assuming standard GN style DFP container units:

```
<div
  class="advert skin" data-dfp-id="site-skin" data-dfp-sizes="1920x900"
  <?php
    if(function_exists("get_yafa")){
      echo get_yafa()->get_ad_attr("skin");
      ?> 
        data-yafa-target="#page-wrapper"
        data-yafa-style="padding-top:200px; background-color: white; background-repeat: no-repeat; background-position: 50% 0;"
        data-yafa-linktarget="#page-wrapper, #inner-wrapper, .page"
        data-yafa-linkheight="1200"
      <?php
    }
  ?>
></div>
```

### Render ads

Assuming you already have adblock detection of some sort, call `yafaIt()` when detected. e.g.

```
<script>
try
{
  $('.advert').getDFPads({
  ...
  });
catch(e) {
  <?php
    if( function_exists( "get_yafa" ) ) {
    ?>
      yafaIt();
    <?php
    }
 ?>
}
```

