# Themes

Themes can be designed inside Blockbench using the Layout tab in the Settings dialog. When you are done editing, you can export the theme using the button in the top toolbar.

Themes can customize the app colors as well as the main font and the headline font. To customize Blockbench further, you can add custom CSS code to your theme. The easiest way to play around with custom CSS rules is to use the Chrome Dev Tools. You can open the dev tools by pressing `Ctrl + Shift + I`. Make sure that all CSS ends up in one line to keep the JSON file valid.

Right now you can share themes in the #themes channel on the Blockbench Discord server.

## Structure

BBStyle files are made in JSON use the following structure:
```JSON
{
	"border": {
		"hex": "#ffffff"
	},
	"selected": {
		"hex": "#ffffff"
	},
	"css": ""
}
```
