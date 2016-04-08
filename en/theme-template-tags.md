### Site Module

#### Outputs site name
```php
<?php echo Site::name(); ?>
```

#### Outputs site theme
```php
<?php echo Site::theme(); ?>
```

#### Outputs site title
```php
<?php echo Site::title(); ?>
```

#### Outputs site description
```php
<?php echo Site::description(); ?>
```

#### Outputs site keywords
```php
<?php echo Site::keywords(); ?>
```

#### Outputs site slogan
```php
<?php echo Site::slogan(); ?>
```

#### Outputs site content
```php
<?php echo Site::content(); ?>
```

#### Outputs site url
```php
<?php echo Site::url(); ?>
```

#### Outputs copyright information
```php
<?php echo Site::powered(); ?>
```


### Pages plugin

#### Outputs date of current page
```php
<?php echo Page::date(); ?>
```

#### Outputs author of current page
```php
<?php echo Page::author(); ?>
```

#### Outputs the available pages
```php
<?php echo Page::available(); ?>
```

#### Outputs page breadcrumbs
```php
<?php echo Page::breadcrumbs(); ?>
```

#### Outputs page url
```php
<?php echo Page::url(); ?>
```

#### Outputs page slug
```php
<?php echo Page::slug(); ?>
```

#### Outputs page meta robots
```php
<?php echo Page::robots(); ?>
```

#### Get children pages for a specific parent page
```php
<?php $pages = Page::children('page'); ?>
<?php foreach($pages as $page) { ?>
    <a href="<?php echo Site::url().'about/'.$page['slug']; ?>"><?php echo $page['title']; ?></a>
<?php } ?>
```


### Menu plugin

#### Outputs menu
```php
<?php echo Menu::get(); ?>
<?php echo Menu::get('category_name'); ?>
```


### Blocks plugin

#### Outputs block
```php
<?php echo Block::get('block_name'); ?>
```

### Snippets plugin

#### Outputs snippet
```php
<?php echo Snippet::get('snippet_name'); ?>
```

#### Outputs snippet with parameters
```php
<?php echo Snippet::get('snippet_name', array('message' => 'Hello World')); ?>
```
