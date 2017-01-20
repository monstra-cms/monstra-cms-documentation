Плагины в Monstra позволяют легко добавить новый функционал, модифицировать поведение и менять настройки.

#### Структура плагина

myplugin/

	 ├── install/
	 │   ├── myplugin.install.php
	 │   ├── myplugin.manifest.xml
	 │   └── myplugin.uninstall.php
	 ├── languages/
	 │   ├── en.lang.php
	 │   └── ru.lang.php
	 ├── views/
	 │   ├── backend/
	 │   │   └── index.view.tpl
	 │   └── frontend/
	 │   	  └── index.view.tpl
	 ├── myplugin.admin.php
	 └── myplugin.plugin.php

Заготовка пустого плагина находится в дистрибутиве по адресу _plugins/sandbox_
На основе заготовки вы сможете сделать свой плагин.

#### Назначение файлов
	install/   
		myplugin.install.php - выполняется во время установки (активации) плагина   
		myplugin.manifest.xml - описание планина, название, путь до плагина и его приоритет.  
		myplugin.uninstall.php - выполняется во время удаления (деактивации) плагина   
	languages/   
		en.lang.php - файлы перевода   
		ru.lang.php   
	views/   
		backend/   
			index.view.tpl - шаблон фронтальной части плагина   
		frontend/   
			index.view.tpl - шаблон административной части плагина   
	myplugin.admin.php - для административной части   
	myplugin.plugin.php - Основной файл плагина.   

#### Доступ к плагину по адресу
Регистрация плагина

```
// Register plugin
Plugin::register( __FILE__,
                __('Sandbox', 'sandbox'),
                __('Sandbox plugin for Monstra', 'sandbox'),
                '1.0.0',
                'Awilum',
                'http://monstra.org/',
                'sandbox');
```

В последней строчки мы видим sandbox, именно по нему мы получим доступ к плагину http://my-site/sandbox/
Последний параметр в регистрации плагина, должен совпадать с названием класс. 
Пример _class Sandbox extends Frontend_

Параметры в плагин можно передать так http://my-site/sandbox/param1/param2/
Получить их в плагине можно через _Uri::segment_ (пример смотрите в плагине Users)
