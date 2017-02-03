### Сниппеты
Сниппеты это расширения, написанные на PHP, которые добавляют разные возможности на сайте, редактировать их могут только администраторы.

Редактирование сниппетов производится через панель администратора в **Расширения -> Сниппеты**

#### Использование сниппетов
Вывести на страницу сниппет можно коротким кодом (шорткодом) так:

Пример
```
{snippets get="NameSnippets"}
```
<br>
Пример вывода сниппета с помощью шоткода, но с передачей параметров.
```
{snippet get="NameSnippet" file="price.xls"}
```
 
 В коде сниппета патаметры будут доступны как переменные.
 
 Пример кода сниппета
 ```php
<?php
echo '<div class="files-style">';
echo $file;
echo '</div>';
?>
 ```
 
#### Сниппеты можно вывести в шаблоне

##### Выводит сниппет по его имени
```php
<?php echo Snippet::get('snippet_name'); ?>
```

##### Выводит сниппет  по его имени с параметрами
```php
<?php echo Snippet::get('snippet_name', array('message' => 'Hello World')); ?>
```
