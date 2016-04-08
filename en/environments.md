The support of environments helps Monstra to make decisions based on the environment setting.<br>

<br>

<h3>Environments list</h3>

Monstra has four predefined environments.<br>

<br>

<code>Monstra::DEVELOPMENT</code>
The development environment.<br>

<br>
<code>Monstra::TESTING</code>
The test environment.<br>

<br>

<code>Monstra::STAGING</code>
The staging environment.<br>

<br>

<code>Monstra::PRODUCTION</code>
The production environment.<br>

<br>

<h3>Set Your Environment</h3>

Setting your environment is done by setting the <code>Monstra::$environment</code> in <code>/engine/_init.php</code>

<br><br>


<h3>Environments and Config</h3>

Based on the environment the Monstra is set to, the Monstra Core class looks for environment-specific defines and preloaded actions, filters, shortcodes. The Monstra Core class will look for the same file name in a directory that's named after the current environment.<br><br>

Here is an example to illustrate this:<br><br>

<pre class="prettyprint">
 boot/
  ├── development/
  │   ├── defines.php
  └── production/
      └── defines.php
</pre>
