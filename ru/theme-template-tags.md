### Информация о сайте

#### Название сайта
```php
<?php echo Site::name(); ?>
```

#### Название темы
```php
<?php echo Site::theme(); ?>
```

#### Заголовок сайта
```php
<?php echo Site::title(); ?>
```

#### Описание сайта
```php
<?php echo Site::description(); ?>
```

#### Ключевые слова
```php
<?php echo Site::keywords(); ?>
```

#### Слоган сайта
```php
<?php echo Site::slogan(); ?>
```

#### Контент сайта
```php
<?php echo Site::content(); ?>
```

#### Адрес сайта
```php
<?php echo Site::url(); ?>
```

#### Выводит название CMS
```php
<?php echo Site::powered(); ?>
```


### Инофрмация о странице

#### Дата текущей страницы
```php
<?php echo Page::date(); ?>
```

#### Автор текущей страницы
```php
<?php echo Page::author(); ?>
```

#### Дочернии страницы у текущей страницы
```php
<?php echo Page::available(); ?>
```

#### Хлебные крошки
```php
<?php echo Page::breadcrumbs(); ?>
```

#### Адрес страницы (полный адрес http://xxx/ru/site/page)
```php
<?php echo Page::url(); ?>
```

#### Ссылка страницы (url)
```php
<?php echo Page::slug(); ?>
```

#### Мета информация о индексации
```php
<?php echo Page::robots(); ?>
```

#### Выводит дочернии страницы по его url
```php
<?php $pages = Page::children('page'); ?>
<?php foreach($pages as $page) { ?>
    <a href="<?php echo Site::url().'about/'.$page['slug']; ?>"><?php echo $page['title']; ?></a>
<?php } ?>
```


### Меню

#### Выводит меню
```php
<?php echo Menu::get(); ?>
<?php echo Menu::get('category_name'); ?>
```


### Блоки

#### Выводит блок по его имени
```php
<?php echo Block::get('block_name'); ?>
```

### Сниппеты

#### Выводит сниппет по его имени
```php
<?php echo Snippet::get('snippet_name'); ?>
```

#### Выводит сниппет  по его имени с параметрами
```php
<?php echo Snippet::get('snippet_name', array('message' => 'Hello World')); ?>
```
