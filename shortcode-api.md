The Shortcode API s a simple regex based parser that allows you to replace simple bbcode-like tags within a HTMLText or HTMLVarchar field when rendered into a content.

Examples of shortcode tags:

```
{{shortcode}}
{{shortcode parameter="value"}}
```

Example of escaping shortcodes:

```
{{{shortcode}}}
```


### Add new shortcode

Your shorcode function:

```php
function returnSiteUrl() {
   return Option::get('siteurl');
}
```

Add shortcode {siteurl}

```php
Shortcode::add('siteurl', 'returnSiteUrl');
```


### Add new shortcode with Variables

Your shorcode function:

```php
function foo($attributes) {
    // Extract
    extract($attributes);

    // text
    if (isset($text)) $text = $text; else $text = '';

    // return
    return $text;
}
```



Add shortcode {foo text="Hello World"}

```php
Shortcode::add('foo', 'foo');
```

Usage:

```
{foo text="Hello World"}
```

Result:

```
Hello World
```



### Add new shortcode with Variables and Content

Your shorcode function:

```php
function foo($attributes, $content) {
    // Extract
    extract($attributes);

    // text
    if (isset($color)) $color = $color; else $color = 'black';

    // return
    return '<span style="color:' . $color . '">' . Filter::apply('content', $content) . '</span>';
}

```

Add shortcode {foo color="red"}

```php
Shortcode::add('foo', 'foo');
```

Usage:

```
{foo color="red"}Hello World{/foo}
```


Result:

```
<span style="color:red">Hello World</span>
```


### Check if a shortcode has been registered.

```php
if (Shortcode::exists('foo')) {
    // do something...
}
```


### Remove a specific registered shortcode.

```php
Shortcode::delete('foo');
```


### Remove all registered shortcodes.

```php
Shortcode::clear();
```


### Braces

The shortcode parser does not accept braces within attributes. Thus the following will fail:

```
{foo attribute="{Some value}"}Hello World{/foo}
```
