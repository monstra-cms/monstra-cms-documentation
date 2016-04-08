The Options API is a simple and standardized way of storing data in the database. The Options API makes it easy to create, access, update, and delete those options. All the data is being stored in the options.table.xml under a given custom name.


### Add new option

```php
Option::add('pages_limit', 10);
Option::add(array('pages_count' => 10, 'pages_default' => 'home'));
```


### Update option value

```php
Option::update('pages_limit', 12);
Option::update(array('pages_count' => 10, 'pages_default' => 'home'));
```


### Get option value

```php
$pages_limit = Option::get('pages_limit');
if ($pages_limit == '10') {
    // do something...
}
```


### Check if option exist

```php
if (Option::exists('pages_limit')) {
    // do something...        
}
```


### Delete option

```php
Option::delete('pages_limit');
```
