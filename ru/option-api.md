Options API - это простой и стандартный способ хранения данных в базе данных (настройки, параметры, конфигурация итд).
API-интерфейс позволяет легко создавать, получать данные, изменять и удалять настройки ваших плагинов и решений. Все данные хранятся в options.table.xml в рамках данного пользовательского имени.

### Создание параметров

```php
Option::add('pages_limit', 10);
Option::add(array('pages_count' => 10, 'pages_default' => 'home'));
```


### Обновить значение

```php
Option::update('pages_limit', 12);
Option::update(array('pages_count' => 10, 'pages_default' => 'home'));
```


### Получить значение

```php
$pages_limit = Option::get('pages_limit');
if ($pages_limit == '10') {
    // do something...
}
```


### Проверить существование параметра

```php
if (Option::exists('pages_limit')) {
    // do something...        
}
```


### Удаление параметра

```php
Option::delete('pages_limit');
```
