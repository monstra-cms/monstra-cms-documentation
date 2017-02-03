Shortcode API это простой парсер на основе регулярного выражения, которая позволяет заменить простые bbcode-подобные теги в определенный результа. Шоткод тег вставляется в контент страницы и заменяется во время генерации самой страниицы в браузере.

Пример шоткода тега:

```
{shortcode}
{shortcode parameter="value"}
```

Пример экранирования шоткода:

```
{{{shortcode}}}
```


### Добавить новый шоткод

Ваша функция для шоткода:

```php
function returnSiteUrl() {
   return Option::get('siteurl');
}
```

Регистрируем шоткод {siteurl}

```php
Shortcode::add('siteurl', 'returnSiteUrl');
```


### Добавление нового шокода с параметрами

Ваша функция для шоткода:

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



Регистрация шоткода {foo text="Hello World"}

```php
Shortcode::add('foo', 'foo');
```

Использование в контенте:

```
{foo text="Hello World"}
```

Результат:

```
Hello World
```



### Добавление нового шоткода с параметрами и контентом

Ваша функция для шоткода:

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

Регистрация шоткода {foo color="red"}

```php
Shortcode::add('foo', 'foo');
```

Применение:

```
{foo color="red"}Hello World{/foo}
```


Результат:

```
<span style="color:red">Hello World</span>
```


### Проверка зарегистрирован шоткод или нет.

```php
if (Shortcode::exists('foo')) {
    // do something...
}
```


### Удаление зарегистрированного шоткода.

```php
Shortcode::delete('foo');
```


### Удаление всех зарегистрированных шоткодов.

```php
Shortcode::clear();
```


### Фигурная скобка

Парсер шоткода не принимает фигурные скобки в качестве параметра. Это приведет к ошибки:

```
{foo attribute="{Some value}"}Hello World{/foo}
```
