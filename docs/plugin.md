# Plugin

## Creating a plugin

Plugins consist of a Javascript file. To create a plugin, create a new Javascript file named `[plugin-id].js`. Inside this file, use the method Plugin.register to initialize the plugin, as seen in the example. Note that the plugin ID should be the same as the file name minus extension.
```javascript
Plugin.register('plugin_id', {
	title: 'Plugin Name',
	author: 'Your Name',
	icon: 'icon',
	description: 'Your Description',
	version: '1.0.0',
	variant: 'both',
	onload() {
	}
});
```
* `title` Plugin title as shown in the store in Blockbench
* `author` Author name or names 
* `description` Plugin description for the store in Blockbench
* `about` Longer Plugin description or instructions, can be unfolded in the store
* `icon` Blockbench icon string, see [Blockbench#icon](blockbench.md#icon)
* `version` Version number for your plugin using [semver](https://semver.org) 
* `variant` Variant of Blockbench which supports your plugin. Can be `desktop`, `web` or `both`
* `onload` function. Runs whenever the plugin is loaded or after a reload
* `onunload` function. Runs whenever the plugin unloads
* `oninstall` function. Runs when the player installs the plugin
* `onuninstall` function. Runs when the player uninstalls the plugin

If you want to declare variables that can be used anywhere within the plugin, you can wrap your whole within a self-invoking function and create variables like this:
```javascript
(function() {
	var plugin_variable_1;

	Plugin.register('plugin_id', {
		onload() {
			plugin_variable_1 = 'foo';
		},
		...
	});

})();
```
To test your plugin, you can load it from the plugin menu using the button in the title bar, or you can simply drag and drop it into Blockbench.


## Submitting your plugin

For testing


