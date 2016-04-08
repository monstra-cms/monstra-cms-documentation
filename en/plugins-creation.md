Monstra Plugins allow easy modification, customization, and enhancement to a Monstra.

#### Plugin structure</h4>

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
