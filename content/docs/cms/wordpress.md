---
title: "Wordpress"
description: "Matrix Wordpress Docs."
lead: "As we use Wordpress for almost everything, docs may need its own section"
date: 2021-03-16T08:43:34+01:00
lastmod: 2021-03-16T08:43:34+01:00
draft: false
images: []
menu:
  docs:
    parent: "cms"
weight: 190
toc: true
---

## Add Style Sheets & Scripts to Functions.php

>Replace **ThemeName** with your themes name.  Replace styles and scripts with your own

```

if ( ! function_exists( 'ThemeName_enqueue_scripts' ) ) :
    function ThemeName_enqueue_scripts() {

        /* Theme generated Enqueue Scripts Begin */

    wp_enqueue_script( 'jquery' );

    wp_enqueue_script( 'slick', 'https://cdnjs.cloudflare.com/ajax/libs/slick-carousel/1.6.0/slick.js', null, null, true );

    wp_deregister_script( 'popper' );
    wp_enqueue_script( 'popper', get_template_directory_uri() . '/assets/js/popper.js', false, null, true);

    wp_deregister_script( 'bootstrap' );
    wp_enqueue_script( 'bootstrap', get_template_directory_uri() . '/bootstrap/js/bootstrap.min.js', false, null, true);


    /* Theme generated Enqueue Scripts End */

    /* Theme generated Enqueue Styles Begin */

    wp_deregister_style( 'bootstrap' );
    wp_enqueue_style( 'bootstrap', get_template_directory_uri() . '/bootstrap/css/bootstrap.css', false, null, 'all');

    wp_deregister_style( 'style' );
    wp_enqueue_style( 'style', get_bloginfo('stylesheet_url'), false, null, 'all');

    /*Theme generated Enqueue Styles End */

    }
    add_action( 'wp_enqueue_scripts', 'ThemeName_enqueue_scripts' );
endif;

```

## How to Build a Custom Theme

## Wordpress Loop

Used to display content such as Page Content, Post Content, a list of posts etc

```

<?php if ( have_posts() ) : ?>
    <?php while ( have_posts() ) : the_post(); ?>
        <article id="post-<?php the_ID(); ?>">
            <?php the_content(''); ?>
        </article>
    <?php endwhile; ?>
<?php else : ?>
    <p><?php _e( 'Sorry, no posts matched your criteria.', 'ThemeName' ); ?></p>
<?php endif; ?>

```



## Add Custom Post Types

Change ThemeName to your themes name.

```

if ( ! function_exists( 'ThemeName_init' ) ) :
    
    function ThemeName_init() {
    
        
        // Use categories and tags with attachments
        register_taxonomy_for_object_type( 'category', 'attachment' );
        register_taxonomy_for_object_type( 'post_tag', 'attachment' );
    
        /*
         * Register custom post types. You can also move this code to a plugin.
         */
        /* Theme generated Custom Post Types Begin */
    
        
        register_post_type('films', array(
            'labels' => 
                array(
                    'name' => __( 'films', 'ThemeName' ),
                    'singular_name' => __( 'film', 'ThemeName' )
                ),
            'public' => true,
            'hierarchical' => true,
            'supports' => array( 'title', 'thumbnail', 'editor' ),
            'show_in_menu' => true,
            'taxonomies' => array( 'category' )
        ));  
    
        /* ThemeName generated Custom Post Types End */
        
        /*
         * Register custom taxonomies. You can also move this code to a plugin.
         */
        /* ThemeName generated Taxonomies Begin */
    
        /* ThemeName generated Taxonomies End */
    
    }
    endif; // ThemeName_setup
    
    add_action( 'init', 'ThemeName_init' );


```

## ACF Cheatsheet

> Replace **FIELD_NAME** with the actual name of your field eg background_image

### Basic Fields

#### Text, Text Area, Number, Range, email, URL

```
<?php the_field( 'FIELD_NAME' ); ?>

```

#### Password

```
<?php $password = get_field( 'FIELD_NAME' ); ?>

```

### Content Fields


#### Image

```
<?php $FIELD_NAME = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME ) { ?>
	<img src="<?php echo $FIELD_NAME['url']; ?>" alt="<?php echo $FIELD_NAME['alt']; ?>" title="<?php echo $FIELD_NAME['title']; ?>" />
<?php } ?>

```

#### File

```
<?php $FIELD_NAME = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME ) { ?>
	<a href="<?php echo $FIELD_NAME['url']; ?>"><?php echo $FIELD_NAME['filename']; ?></a>
<?php } ?>

```

#### Wysiwyg Editor, oEmbed

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### Gallery


```

<?php $FIELD_NAME_images = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME_images ) :  ?>
	<?php foreach ( $FIELD_NAME_images as $FIELD_NAME_image ): ?>
		<a href="<?php echo $FIELD_NAME_image['url']; ?>">
			<img src="<?php echo $FIELD_NAME_image['sizes']['thumbnail']; ?>" alt="<?php echo $FIELD_NAME_image['alt']; ?>" />
		</a>
	<p><?php echo $FIELD_NAME_image['caption']; ?></p>
	<?php endforeach; ?>
<?php endif; ?

```

### Choice Fields

#### Select  

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### Checkbox


```

<?php // FIELD_NAME ( value )
$FIELD_NAME_array = get_field( 'FIELD_NAME' );
if ( $FIELD_NAME_array ):
	foreach ( $FIELD_NAME_array as $FIELD_NAME_item ):
	 	echo $FIELD_NAME_item;
	endforeach;
endif; ?>

```

#### Radio Button

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### Checkbox

```

<?php // FIELD_NAME ( value )
$FIELD_NAME_array = get_field( 'FIELD_NAME' );
if ( $FIELD_NAME_array ):
	foreach ( $FIELD_NAME_array as $FIELD_NAME_item ):
	 	echo $FIELD_NAME_item;
	endforeach;
endif; ?>

```

#### Button Group

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### True / False

```

<?php if ( get_field( 'FIELD_NAME' ) == 1 ) { 
 // echo 'true'; 
} else { 
 // echo 'false'; 
} ?>

```

### Relational Fields

#### Link  

```

<?php $FIELD_NAME = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME ) { ?>
	<a href="<?php echo $FIELD_NAME['url']; ?>" target="<?php echo $FIELD_NAME['target']; ?>"><?php echo $FIELD_NAME['title']; ?></a>
<?php } ?>

```

#### Post Object

```

<?php $post_object = get_field( 'FIELD_NAME' ); ?>
<?php if ( $post_object ): ?>
	<?php $post = $post_object; ?>
	<?php setup_postdata( $post ); ?> 
		<a href="<?php the_permalink(); ?>"><?php the_title(); ?></a>
	<?php wp_reset_postdata(); ?>
<?php endif; ?>

```

#### Page Link


```

<?php the_field( 'FIELD_NAME' ); ?>

```

### Relationship

```

<?php $FIELD_NAME = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME ): ?>
	<?php foreach ( $FIELD_NAME as $post ):  ?>
		<?php setup_postdata ( $post ); ?>
			<a href="<?php the_permalink(); ?>"><?php the_title(); ?></a>
	<?php endforeach; ?>
<?php wp_reset_postdata(); ?>
<?php endif; ?>

```

#### Button Group

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### Taxonomy

```

<?php $FIELD_NAME_ids = get_field( 'FIELD_NAME' ); ?>
<?php // var_dump( $FIELD_NAME_ids ); ?>

```

#### User

```

<?php $FIELD_NAME_array = get_field( 'FIELD_NAME' ); ?> 
<?php // var_dump( $FIELD_NAME_array ); ?>

```

### Jquery Fields

#### Google Map


```

<?php $FIELD_NAME = get_field( 'FIELD_NAME' ); ?>
<?php if ( $FIELD_NAME ) { ?>
	<?php echo $FIELD_NAME['address']; ?>
	<?php echo $FIELD_NAME['lat']; ?>
	<?php echo $FIELD_NAME['lng']; ?>
<?php } ?>

```

#### Date Time Picker

```

<?php the_field( 'FIELD_NAME' ); ?>

``` 

#### Time Picker

```

<?php the_field( 'FIELD_NAME' ); ?>

```

#### Color Picker


```

<?php the_field( 'FIELD_NAME' ); ?>

```

### Layout Fields

(Note Sub field as above except **the_sub_field** instead of **'the_field'**  )

#### Repeater

```

<?php if ( have_rows( 'FIELD_NAME' ) ) : ?>
	<?php while ( have_rows( 'FIELD_NAME' ) ) : the_row(); ?>
		<?php the_sub_field( 'SUBFIELD' ); ?>
	<?php endwhile; ?>
<?php else : ?>
	<?php // no rows found ?>
<?php endif; ?>

```
#### Flexible Content (Example has 2 Blocks of Flexi content)

```

<?php if ( have_rows( 'FIELD_NAME' ) ): ?>
	<?php while ( have_rows( 'FIELD_NAME' ) ) : the_row(); ?>
		<?php if ( get_row_layout() == 'BLOCKONE' ) : ?>
			<?php the_sub_field( 'SUBFIELD_ONE' ); ?>
		<?php elseif ( get_row_layout() == 'BLOCKTWO' ) : ?>
			<?php the_sub_field( 'SUBFIELD_TWO' ); ?>
		<?php endif; ?>
	<?php endwhile; ?>
<?php else: ?>
	<?php // no layouts found ?>
<?php endif; ?>

```

#### Clone

You Can use this field to clone previously built fields, in Groups used on other pages for example


## Remove FTP upload Message

Sometimes we get this error when uploading plugins:

"to perform the requested action wordpress needs to access your web server. please enter your ftp"

Add the following code to WP Config to remove the need to enter FTP credentials on uploads


```

define( 'FS_METHOD', 'direct' );

```

## Change Wp Content Folder Permissions to 777

Navigate to the site root directory like in the example below and run the following command (change the path after -R 777 to the relevant one)

Note: 777 is usually a bad idea as it is insecure, 755 is better.

```

sudo chmod -R 777 /var/www/vhosts/matrix-test.com/SITENAME.com

```

## How to Increase the Maximum File Upload Size in WordPress

Some times low file upload size limit can stop you from uploading files via media uploader, or install plugins and themes. We need to increase upload sizes in the PHP file to prevent this.

### Editing PHP INI file

Create a file called info.php (sometimes this will already be set up)

add the following code.

```

<?php phpinfo(); ?> 

```

Check to see what the max file upload size is set at in PHP.ini (usually it is 2 and you can search "2")

Usually the PHP.INI will somewhere like:

```

/etc/php/7.2/apache2

```

Open it and change the values like (you can use a different value):

```

post_max_size = 8M

upload_max_filesize = 30M

max_execution_time = 300

```

Next restart Apache and check Media Library to see if the value changed

```

sudo service apache2 reload

```

## Change WP options

You can edit WP Hosting Options from the WP admin by adding this to the site URL 
/wp-admin/options.php

https://EXAMPLESITE.com/wp-admin/options.php


## Display something on Home Page differently on another page

In the below example we are displaying a white version of a logo on the homepage, but black on all other pages.

```

<?php if ( is_front_page()){ ?>
		<a id="logo" href="/"><img src="PATH_TO_IMG_1" alt=""></a>
	<?php } else { ?>
		<a id="logo2" href="/"><img src="PATH_TO_IMG_2" alt=""></a>
<?php } ?>


```

A more robust way covering more template types


```

<?php if ( is_front_page() && is_home() ) { ?>
  
  //do something

  <?php } elseif ( is_front_page()){ ?>
    
    //do something

    <?php } elseif ( is_home()){ ?>

    //do something

    <?php } else { ?>

    //do something

    <?php } ?>

```