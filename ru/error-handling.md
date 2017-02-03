Обработчик ошибок Monstra преобразует все ошибки в ErrorExceptions.
Это позволяет Monstra отобразить страницу ошибки, который содержит гораздо больше информации, чем стандартные страницы ошибок PHP, когда случается что-то плохое
Обработчик ошибок также будет записывать лог ошибки.

Обратите внимание, что страница с информацией об ошибке будет отображаться, если `Monstra::$environment` = `Monstra::DEVELOPMENT`

### Примеры

Это пример вывода ошибки в Monstra CMS:
![Error handling](http://monstra.org/public/uploads/images/general/docs/error-handling.png)
