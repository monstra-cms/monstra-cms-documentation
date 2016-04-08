<h3>Site Module</h3><br>



<h4>Outputs site name</h4>

<pre class="prettyprint">&lt;?php echo Site::name(); ?&gt;</pre>



<br><h4>Outputs site theme</h4>

<pre class="prettyprint">&lt;?php echo Site::theme(); ?&gt;</pre>



<br><h4>Outputs site title</h4>

<pre class="prettyprint">&lt;?php echo Site::title(); ?&gt;</pre>



<br><h4>Outputs site description</h4>

<pre class="prettyprint">&lt;?php echo Site::description(); ?&gt;</pre>



<br><h4>Outputs site keywords</h4>

<pre class="prettyprint">&lt;?php echo Site::keywords(); ?&gt;</pre>



<br><h4>Outputs site slogan</h4>

<pre class="prettyprint">&lt;?php echo Site::slogan(); ?&gt;</pre>



<br><h4>Outputs site content</h4>

<pre class="prettyprint">&lt;?php echo Site::content(); ?&gt;</pre>



<br><h4>Outputs site url</h4>

<pre class="prettyprint">&lt;?php echo Site::url(); ?&gt;</pre>



<br><h4>Outputs copyright information</h4>

<pre class="prettyprint">&lt;?php echo Site::powered(); ?&gt;</pre>





<br><h3>Pages plugin</h3><br>



<h4>Outputs date of current page</h4>

<pre class="prettyprint">&lt;?php echo Page::date(); ?&gt;</pre>



<br><h4>Outputs author of current page</h4>

<pre class="prettyprint">&lt;?php echo Page::author(); ?&gt;</pre>



<br><h4>Outputs the available pages</h4>

<pre class="prettyprint">&lt;?php echo Page::available(); ?&gt;</pre>



<br><h4>Outputs page breadcrumbs</h4>

<pre class="prettyprint">&lt;?php echo Page::breadcrumbs(); ?&gt;</pre>



<br><h4>Outputs page url</h4>

<pre class="prettyprint">&lt;?php echo Page::url(); ?&gt;</pre>



<br><h4>Outputs page slug</h4>

<pre class="prettyprint">&lt;?php echo Page::slug(); ?&gt;</pre>



<br><h4>Outputs page meta robots</h4>

<pre class="prettyprint">&lt;?php echo Page::robots(); ?&gt;</pre>



<br><h4>Get children pages for a specific parent page</h4>

<pre class="prettyprint">



&lt;?php $pages = Page::children('page'); ?&gt;



&lt;?php foreach($pages as $page) { ?&gt;

    &lt;a href="&lt;?php echo Site::url().'about/'.$page['slug']; ?&gt;"&gt;&lt;?php echo $page['title']; ?&gt;&lt;/a&gt;

&lt;?php } ?&gt;



</pre>



<br><h3>Menu plugin</h3><br>



<h4>Outputs menu</h4>

<pre class="prettyprint">

&lt;?php echo Menu::get(); ?&gt;

&lt;?php echo Menu::get('category_name'); ?&gt;

</pre>



<br><h3>Blocks plugin</h3><br>



<h4>Outputs block</h4>

<pre class="prettyprint">&lt;?php echo Block::get('block_name'); ?&gt;</pre>



<br><h3>Snippets plugin</h3>

<br>

<h4>Outputs snippet</h4>

<pre class="prettyprint">&lt;?php echo Snippet::get('snippet_name'); ?&gt;</pre>

<br>

<h4>Outputs snippet with parameters</h4>

<pre class="prettyprint">&lt;?php echo Snippet::get('snippet_name', array('message' => 'Hello World')); ?&gt;</pre>
