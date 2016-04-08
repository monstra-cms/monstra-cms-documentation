<p>You must create themes in the <code>/public/themes/</code> folder.<br>

All themes must include an index.temlplate.php file to define the HTML structure of the theme. <br>

You can seperate your theme on footer and header with help of chunks.</p>



<br>

<h4>Theme structure</h4>

<pre class="prettyprint">
 theme/
  ├── css/
  │   ├── theme.css
  ├── js/
  ├── img/
  ├── header.chunk.php
  ├── footer.chunk.php
  └── index.template.php
</pre>



<br>



<h3>Simple Example</h3>

<hr>



<h4>header.chunk.php</h4>

<pre class="prettyprint">
&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
&lt;meta charset="utf-8"&gt;
&lt;title&gt;&lt;?php echo Site::name() . ' - ' . Site::title(); ?&gt;&lt;/title&gt;
&lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;       
&lt;meta name="description" content="&lt;?php echo Site::description(); ?&gt;"&gt;
&lt;meta name="keywords" content="&lt;?php echo Site::keywords(); ?&gt;"&gt;
&lt;meta name="robots" content="&lt;?php echo Page::robots(); ?&gt;"&gt;
&lt;!-- Styles --&gt;
&lt;?php Stylesheet::add('public/assets/css/bootstrap.css', 'frontend', 1); ?&gt;
&lt;?php Stylesheet::add('public/themes/theme/css/theme.css', 'frontend', 2); ?&gt;
&lt;?php Stylesheet::add('public/assets/css/bootstrap-responsive.css', 'frontend', 3); ?&gt;
&lt;?php Stylesheet::load(); ?&gt;
&lt;?php Action::run('theme_header'); ?&gt;
&lt;!-- Le HTML5 shim, for IE6-8 support of HTML5 elements --&gt;
&lt;!--[if lt IE 9]&gt;
&lt;script src="http://html5shim.googlecode.com/svn/trunk/html5.js"&gt;&lt;/script&gt;
&lt;![endif]--&gt;
&lt;!-- Fav icons --&gt;
&lt;link rel="icon" href="&lt;?php echo Site::url(); ?&gt;favicon.ico" type="image/x-icon"&gt;
&lt;link rel="shortcut icon" href="&lt;?php echo Site::url(); ?&gt;favicon.ico" type="image/x-icon"&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div class="navbar navbar-fixed-top"&gt;
&lt;div class="navbar-inner"&gt;
  &lt;div class="container"&gt;
    &lt;a class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse"&gt;
      &lt;span class="icon-bar"&gt;&lt;/span&gt;
      &lt;span class="icon-bar"&gt;&lt;/span&gt;
      &lt;span class="icon-bar"&gt;&lt;/span&gt;
    &lt;/a&gt;
    &lt;a class="brand" href="&lt;?php echo Site::url(); ?&gt;"&gt;&lt;?php echo Site::name(); ?&gt;&lt;/a&gt;
    &lt;div class="nav-collapse collapse"&gt;
      &lt;ul class="nav"&gt;
          &lt;?php echo Menu::get(); ?&gt;
      &lt;/ul&gt;
      &lt;div class="pull-right user-panel"&gt;
        &lt;?php Users::getPanel(); ?&gt;
      &lt;/div&gt;
    &lt;/div&gt;&lt;!--/.nav-collapse --&gt;
  &lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
</pre>

<h4>index.template.php</h4>

<pre class="prettyprint html">
&lt;?php Chunk::get('header'); ?&gt;
&lt;div class="container"&gt;
&lt;div&gt;
&lt;?php Action::run('theme_pre_content'); ?&gt;
&lt;/div&gt;
&lt;div&gt;
&lt;?php echo Site::content(); ?&gt;
&lt;/div&gt;
&lt;div&gt;
&lt;?php Action::run('theme_post_content'); ?&gt;
&lt;/div&gt;
&lt;hr&gt;
&lt;?php Chunk::get('footer'); ?&gt;   
</pre>



<h4>footer.chunk.php</h4>

<pre class="prettyprint">
&lt;footer&gt;
&lt;p&gt;                      
&lt;div style="float:right;"&gt;&lt;?php Action::run('theme_footer'); ?&gt;&lt;?php echo Site::powered(); ?&gt;&lt;/div&gt;
&lt;/p&gt;            
&lt;/footer&gt;
&lt;/div&gt; &lt;!-- /container --&gt;
&lt;!-- Javascript
================================================== --&gt;
&lt;!-- Placed at the end of the document so the pages load faster --&gt;
&lt;script type="text/javascript" src="&lt;?php echo Option::get('siteurl'); ?&gt;public/assets/js/jquery.js"&gt;&lt;/script&gt;
&lt;script type="text/javascript" src="&lt;?php echo Option::get('siteurl'); ?&gt;public/assets/js/bootstrap.js"&gt;&lt;/script&gt;
&lt;?php Javascript::load(); ?&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>
