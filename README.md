# CakePHP 2.x Configuration plugin
[![Build Status](https://travis-ci.com/anklimsk/cakephp-config-plugin.svg?branch=master)](https://travis-ci.com/anklimsk/cakephp-config-plugin)

Initialize and get the plugin configuration.

## This plugin provides next features:

- Initialize and get the plugin configuration.

## Installation

1. Install the Plugin using composer: `composer require anklimsk/cakephp-config-plugin`
2. Add the next line to the end of the file `app/Config/bootstrap.php`:
```php
CakePlugin::load('CakeConfigPlugin', ['bootstrap' => true]);
```

## Using this plugin

1. Include in the `AppModel` model of your plugin the behavior `InitConfig`:
```php
    public $actsAs = [
        'CakeConfigPlugin.InitConfig' => [
            'pluginName' => 'SomePluginName',
            'checkPath' => 'SomePluginName.param'
        ]
    ];

2. Create a configuration file in the `Config` directory of your plug-in, e.g.:` somepluginname.php`
    
3. Fill configuration file, e.g.:
```php
    $config['SomePluginName'] = [
        'param' => 'value'
        ...
    ];
```

4. If necessary, copy config file from 'app/Plugin/SomePluginName/Config/somepluginname.php' to 'app/Config',
    and edit it.
    
5. If you need to overwrite the configuration parameter in the application, use:
```php
Configure::write('SomePluginName.param', 'newValue');
```
    After, in Model call:
```php
$this->initConfig(true);
```
