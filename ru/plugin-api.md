### Плагин

#### Регистрация нового плагина в системе.

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

#### Подключение плагина административной части.
```php
Plugin::admin('blog');
```


### Представление

#### Представление через создания нового объекта.

```php
// Создать новый объект
$view = new View('blog/views/backend/index');

// Присвоить некоторые новые переменные
$view->assign('msg', 'Some message...');

// Получить представление
$output = $view->render();

// Отобразить представление
echo $output;
```

#### Представление через метод factory.

```php
// Создает новое представление, присваиваются
// значения переменных и отображается.
View::factory('blog/views/backend/index')
   ->assign('msg', 'сообщение...')
   ->display();
```

#### Присваивание новых переменных для представлению.

```php
$view->assign('msg', 'сообщение...');
```

#### Подключает файл представления и получает переменные в представление

```php
// Получить представление
$output = $view->render();

// Отобразить представление
echo $output;
```

#### Сразу получает и отображает представление. 

```php
$view->display();
```


### I18n

#### Возвращает перевод строки. Если перевода не существует, то передается оригинальное значение без перевода. Параметры не будут заменены.

```php
$hello = I18n::find('Hello friends, my name is :name', 'namespace');
```

#### Глобальный перевод/функция интернационализации

Принимает английскую строку и возвращает ее перевод в активный язык системы. Если данная строка отсутствует в текущем словаре, то оригинальная английская строка будет возвращена.
```php
// Отобразить перевод
echo __('Hello, world', 'namespace');

// С параметрами замены
echo __('Hello, :user', 'namespace', array(':user' => $username));
```


### Действия (Экшены)

#### Хуки это крючки на определенные действия.

```php
// Зацепка функции "newLink" в экшен "footer"
Action::add('footer', 'newLink', 10);

function newLink() {
   echo '<a href="#">My link</a>';
}     
```

#### Выполнение зацепленной функции 

```php
// Выполняет зацепренную функцию "footer" , которая была добавлена выше.
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
