# Textures

Textures are saved in the global `textures` array. `textures.selected` will return the currently selected texture. If single_texture is enabled in the current format, only one texture can exist at a time.

## new Texture( data, uuid )

Creates a new texture

* `id` Texture key used in java edition and OBJ models
* `name` Texture name
* `folder` Subfolder of the textures folder that the texture is in.
* `namespace` Texture namespace, used for mods
* `path` Full texture path
* `particle` Whether to use the texture as the particle texture for java edition models
* `source` Source string of the texture. Can either be a base64 string or a path. Paths will usually have `?2` or similar appended to make them update after being changed.
* `selected` Whether the texture is selected
* `show_icon` Whether the source of the texture should be displayed in the textures list.
* `dark_box` If true, the UV editor will use a dark border for this texture. Calculated from the average color of the texture
* `error` Numerical error code:
	* `0` No errors
	* `1` File error, texture could not be loaded
	* `2` Invalid aspect ratio
	* `3` Placeholder texture, the actual texture gets defined by the parent model
* `width` Texture width
* `height` Texture height
* `ratio` Texture aspect ratio
* `frameCount` Returns the frame count if the texture is an animated texture
* `img` HTML Image instance of the texture
* `saved` Whether the texture is saved
* `mode` How the texture source is handled. Can be `'link'` or `'bitmap'`. Link textures are loaded from a path on the computer, so textures in the web app are always mode bitmap.
* `uuid` Texture uuid.

#### Canvas.materials[texture.uuid]
THREE.JS materials are saved in a separate location to increase performance. You can get the material using the texture's uuid.

#### texture.getErrorMessage()
Returns the translated error message of the texture.

#### texture.extend( data: Object )
Copy properties from `data` into the texture.

#### load( callback: Function )
Loads the texture by updating its source.

* `callback` function to call after the update is finished. The update is asynchronous.

## Loading Textures

#### texture.fromJavaLink( link: String, path_array: Array )
Tries to load the texture from a java edition resource pack using the relative path provided in the model file and the absolute path of the model.

#### texture.fromFile( file: String )
Loads the texture from a file object, as used in Blockbench.import.

#### texture.fromPath( path: String )
Loads the texture from an absolute path.

#### texture.fromDataURL( data_url: String )
Loads the texture from a data URL (base64 encoded image)

#### texture.fromDefaultPack()
Attempts to load the texture from the default resource pack if defined in the Blockbench settings.

#### texture.loadEmpty( error_id: Number )
Loads the texture with an empty (error) texture and sets the error code to `error_id`.

#### texture.add( undo: Boolean )
Adds the texture to Blockbench and takes care of applying the texture to all cubes if required by the format.

* `undo` Whether to create an undo point for adding the texture.

#### texture.generateFolder( path: String )
Generate the java edition texture folder from a given path.

## Updating textures

#### texture.updateSource( data_url: String )
Updates the source of the texture. This is used if the texture gets edited. Also updates the material and UV Editor view of the texture

#### texture.updateMaterial()
Only update the THREE.JS material of the texture.

#### texture.reopen( force: Boolean )
Opens a file dialog to replace the texture source with another file.

* `force` If true, Blockbench won't show a warning message if the texture has unsaved changes.

#### texture.reloadTexture()
Reloads the texture to update changes to the file. This is usually not necessary as the texture updates automatically when there are any changes.

## Handling textures

#### texture.select( event: Event )
Select this texture.


#### texture.remove( no_update: Boolean )
Removes the texture.

* `no_update` If true, don't update the interface and don't create an undo point 

#### enableParticle()
Marks this texture as particle texture for java edition models.

#### fillParticle()
Marks this texture as particle texture for java edition models, unless there is already a particle texture.

#### apply( all: Boolean )
Applies the texture to all selected cubes. Creates an undo point.

* `all` When true, apply the texture to all faces

#### texture.javaTextureLink()
Returns the link of the texture as used in java edition block/item models.

## Texture Menu

#### texture.openFolder()
Show the source file of the texture in a new Explorer/Finder window.

#### texture.openEditor()
Open the texture in the preferred image editor as specified in the settings.

#### texture.showContextMenu( event )
Show the context menu of the texture using the position of the event.

#### texture.openMenu()
Opens the texture menu dialog.

## Editing Textures

#### texture.edit( callback: Function, options: Object )
Edits the texture using the callback function.
* `callback` Function to edit the texture. If omitted, the texture will be converted to an editable texture but won't be edited.

#### texture.save( as: Boolean )
Saves changes to the texture.
* `as` If true, a file dialog will be opened even if the location of the file is known.

#### texture.getBase64()
Returns the base64 string of the texture.


## TextureAnimator
Tool to control animated textures.

#### TextureAnimator.start()

#### TextureAnimator.stop()

#### TextureAnimator.toggle()

#### TextureAnimator.updateSpeed()
Updates the playback speed of animated textures.

#### TextureAnimator.reset()
Sets all animated textures back to frame 0 and stops playing.

#### TextureAnimator.updateButton()
Updates whether the animation button displays a play or pause icon.

