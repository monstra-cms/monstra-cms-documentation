The support of environments helps Monstra to make decisions based on the environment setting.

### Environments list

Monstra has four predefined environments.

`Monstra::DEVELOPMENT`
The development environment.

`Monstra::TESTING`
The test environment.

`Monstra::STAGING`
The staging environment.

`Monstra::PRODUCTION`
The production environment.

### Set Your Environment

Setting your environment is done by setting the `Monstra::$environment` in `/engine/_init.php`

### Environments and Config

Based on the environment the Monstra is set to, the Monstra Core class looks for environment-specific defines and preloaded actions, filters, shortcodes. The Monstra Core class will look for the same file name in a directory that's named after the current environment.

Here is an example to illustrate this:

	boot/
	 ├── development/
	 │   └── defines.php
	 └── production/
	     └── defines.php
