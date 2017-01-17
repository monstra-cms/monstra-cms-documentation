| Переменная               | Описание  возвращаемых данных           |
|--------------------|-------------------------|
| `@site_url`        | Полный адрес сайта        |
| `@theme_site_url`  | Адрес темы сайта  |
| `@theme_admin_url` | Адрес административной темы сайта |

###Пример
```
body {
    background:url(@theme_site_url/images/background.png);
}
```

**Результат**
```
body {
    background:url(http://site.ru/public/themes/default/images/background.png);
}
```
  
    
_Обратите внимание! Данные переменные работают если вы произвели минификацию css файлов_

**Пример минификации в шаблоне**
```
<?php Stylesheet::add('public/themes/default/css/default.css', 'frontend', 2); ?>
<?php Stylesheet::load(); ?>
```

