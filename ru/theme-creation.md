Создайте директорию в `/public/themes/`   
Создайте файл шаблона index.temlplate.php для определения HTML-структуры.
Так же вы можете разделить вашу тему на куски с помощью чанков footer и header. Это поможет вам в будущем.

### Структура простой темы

	my-theme/
	 ├── css/
	 │   └── theme.css
	 ├── js/
	 ├── img/
	 ├── header.chunk.php
	 ├── footer.chunk.php
	 └── index.template.php


### Простой пример темы с разделением на чанки

#### header.chunk.php

	<!DOCTYPE html>
	<html lang="en">
	<head>
	<meta charset="utf-8">
	<title><?php echo Site::name() . ' - ' . Site::title(); ?></title>
	<meta name="viewport" content="width=device-width, initial-scale=1.0">       
	<meta name="description" content="<?php echo Site::description(); ?>">
	<meta name="keywords" content="<?php echo Site::keywords(); ?>">
	<meta name="robots" content="<?php echo Page::robots(); ?>">
	<!-- Styles -->
	<link rel="stylesheet" href="<?php echo Site::url(); ?>/public/assets/css/bootstrap.css" type="text/css" />
	<?php Stylesheet::add('public/themes/theme/css/theme.css', 'frontend', 2); ?>
	<?php Stylesheet::add('public/assets/css/bootstrap-responsive.css', 'frontend', 3); ?>
	<?php Stylesheet::load(); ?>
	<?php Action::run('theme_header'); ?>
	<!-- Le HTML5 shim, for IE6-8 support of HTML5 elements -->
	<!--[if lt IE 9]>
	<script src="http://html5shim.googlecode.com/svn/trunk/html5.js"></script>
	<![endif]-->
	<!-- Fav icons -->
	<link rel="icon" href="<?php echo Site::url(); ?>favicon.ico" type="image/x-icon">
	<link rel="shortcut icon" href="<?php echo Site::url(); ?>favicon.ico" type="image/x-icon">
	</head>
	<body>
	<div class="navbar navbar-fixed-top">
	<div class="navbar-inner">
	  <div class="container">
	    <a class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse">
	      <span class="icon-bar"></span>
	      <span class="icon-bar"></span>
	      <span class="icon-bar"></span>
	    </a>
	    <a class="brand" href="<?php echo Site::url(); ?>"><?php echo Site::name(); ?></a>
	    <div class="nav-collapse collapse">
	      <ul class="nav">
	          <?php echo Menu::get(); ?>
	      </ul>
	      <div class="pull-right user-panel">
	        <?php Users::getPanel(); ?>
	      </div>
	    </div><!--/.nav-collapse -->
	  </div>
	</div>
	</div>
	
Обратите внимание! Если в файле стилей имеются ссылки на фоновые изображения или шрифты, то вам необходимо:

или отказаться от объединения файлов т.е не добавлять в список минификации Stylesheet::add (кстати bootstrap.css именно поэтому и не учавствует в минификации)

или в файл стилей добавить теги, а именно переменную адреса сайта. О переменных css вы можете узнать в статье "CSS переменные"


#### index.template.php

	<?php Chunk::get('header'); ?>
	<div class="container">
	<div>
	<?php Action::run('theme_pre_content'); ?>
	</div>
	<div>
	<?php echo Site::content(); ?>
	</div>
	<div>
	<?php Action::run('theme_post_content'); ?>
	</div>
	<hr>
	<?php Chunk::get('footer'); ?>   

#### footer.chunk.php

	<footer>
	<p>                      
	<div style="float:right;"><?php Action::run('theme_footer'); ?><?php echo Site::powered(); ?></div>
	</p>            
	</footer>
	</div> <!-- /container -->
	<!-- Javascript
	================================================== -->
	<!-- Placed at the end of the document so the pages load faster -->
	<script type="text/javascript" src="<?php echo Option::get('siteurl'); ?>public/assets/js/jquery.js"></script>
	<script type="text/javascript" src="<?php echo Option::get('siteurl'); ?>public/assets/js/bootstrap.js"></script>
	<?php Javascript::load(); ?>
	</body>
	</html>
