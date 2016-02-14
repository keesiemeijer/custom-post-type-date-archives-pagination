# Custom Post Type Date Archives Pagination #

A WordPress plugin to paginate your custom post type date archives by year, month or day.

**Note**
This plugin is meant to be used with the [Custom Post Type Date Archives plugin](https://github.com/keesiemeijer/custom-post-type-date-archives). For the same usage on date archives of the post type `post` see the [Date Archive Pagination plugin](https://github.com/keesiemeijer/date-archives-pagination)

## Description ##

This WordPress plugin provides functions you can use in your (archive) theme template files to paginate by day, month or year dependending on the type of date archive.

For example, when visiting a monthly date archive page, the functions provided will link to the next and previous month archive page if available.

## Usage ##

**Note**
Consider creating a <a href="http://codex.wordpress.org/Child_Themes">child theme</a> instead of editing your theme directly - if you upgrade the theme all your modifications will be lost.

Activate this plugin and find your theme's [date archive templates](https://developer.wordpress.org/themes/basics/template-hierarchy/#date).

Find the [pagination functions](https://codex.wordpress.org/Pagination#Function_Reference) used by your theme and replace them with one of these functions.

Display the next date archive page link.
```PHP
<?php cptdap_next_posts_link( $label = null ); ?>
```

Return the next date archive page link.
```PHP
<?php cptdap_get_next_posts_link( $label = null ); ?>
```

Display the previous date archive page link.
```PHP
<?php cptdap_previous_posts_link( $label = null ); ?>
```

Return the previous date archive page link.
```PHP
<?php cptdap_get_previous_posts_link( $label = null ); ?>

```

If you don't use the `$label` parameter in the functions above the default text format of the links depending on the date archive is:

* daily archive   — `March 12, 2016` (date format from wp-admin > Settings > General)
* monthly archive — `March 2016`
* yearly archive  — `2016`

### Example ###
Simple example to use the functions above.

```PHP
<?php
// Check if it's a custom post type date archive
if ( function_exists( 'cptda_is_cpt_date' ) && cptda_is_cpt_date() ) {

	// Next date archive
	if ( function_exists( 'cptdap_next_posts_link' ) ) {
		cptdap_next_posts_link();
	}

	// Previous date archive
	if ( function_exists( 'cptdap_previous_posts_link' ) ) {
		cptdap_previous_posts_link();
	}
} else {
	// Normal post type Post date archives pagination here
}
?>
```

## Next and Previous Date Archive Date ##
If you need to know the date of the next or previous date archive use these functions.

Returns a next adjacent date archive page date.
```PHP
<?php cptdap_get_next_cpt_date_archive_date(); ?>

```

Returns a previous adjacent date archive page date.
```PHP
<?php cptdap_get_previous_cpt_date_archive_date(); ?>

```

### Example ###
Example to print the previous date archive date.
```PHP
<?php
$next_date = '';

if ( function_exists( 'cptdap_get_previous_cpt_date_archive_date' ) ) {
	$next_date = cptdap_get_previous_cpt_date_archive_date();	
}

echo $next_date;
// If a next date archive date exist it prints something similar to this
// 2016-03-12
?>
```




