### Plugin

#### Register new plugin in system.

```php
Plugin::register(
	__FILE__,
	__('Blog'),
	__('Blog plugin'),
	'1.0.0',
	'Username',
	'http://example.org/',
	'blog'
);
```

#### Get plugin admin.
```php
Plugin::admin('blog');
```


### View

#### Create a new view object.

```php
// Create new view object
$view = new View('blog/views/backend/index');

// Assign some new variables
$view->assign('msg', 'Some message...');

// Get view
$output = $view->render();

// Display view
echo $output;
```

#### View factory.

```php
// Create new view object, assign some variables
// and displays the rendered view in the browser.
View::factory('blog/views/backend/index')
   ->assign('msg', 'Some message...')
   ->display();
```

#### Assign a view variable.

```php
$view->assign('msg', 'Some message...');
```

#### Include the view file and extracts the view variables before returning the generated output.

```php
// Get view
$output = $view->render();

// Display output
echo $output;
```

#### Displays the rendered view in the browser.

```php
$view->display();
```


### I18n

#### Returns translation of a string. If no translation exists, the original will be returned. No are replaced.

```php
$hello = I18n::find('Hello friends, my name is :name', 'namespace');
```

#### Global Translation/internationalization function.

Accepts an English string and returns its translation to the active system language. If the given string is not available in the current dictionary the original English string will be returned.

```php
// Display a translated message
echo __('Hello, world', 'namespace');

// With parameter replacement
echo __('Hello, :user', 'namespace', array(':user' => $username));
```


### Action

#### Hooks a function on to a specific action.

```php
// Hooks a function "newLink" on to a "footer" action.
Action::add('footer', 'newLink', 10);

function newLink() {
   echo '<a href="#">My link</a>';
}     
```

#### Run functions hooked on a specific action hook.

```php
// Run functions hooked on a "footer" action hook.
Action::run('footer');
```


### Filter

#### Apply filters.

```php
Filter::apply('content', $content);
```

#### Add filter.

```php
Filter::add('content', 'replacer');

function replacer($content) {
   return preg_replace(array('/\[b\](.*?)\[\/b\]/ms'), array('<strong>\1</strong>'), $content);
}
```


### Stylesheet

#### Add stylesheet

```php
Stylesheet::add('path/to/my/stylesheet1.css');
Stylesheet::add('path/to/my/stylesheet2.css', 'frontend', 11);
Stylesheet::add('path/to/my/stylesheet3.css', 'backend',12);
```

#### Minify, combine and load site stylesheet.

```php
Stylesheet::load();
```


### Javascript

#### Add javascript

```php
Javascript::add('path/to/my/script1.js');
Javascript::add('path/to/my/script2.js', 'frontend', 11);
Javascript::add('path/to/my/script3.js', 'backend', 12);
```

#### Combine and load site javascript.

```php
Javascript::load();
```


### Navigation

#### Add new item

```php
// Add link for left navigation
Navigation::add(__('Blog'), 'content', 'blog', 11);

// Add link for top navigation
Navigation::add(__('View site'), 'top', 'http://site.com/', 11, Navigation::TOP, true);
```

#### Draw items

```php
Navigation::draw('content');
Navigation::draw('top', Navigation::TOP);
```
