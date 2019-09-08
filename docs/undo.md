# Undo

## Creating an undo point

When modifying elements, textures, animations or anything else about the model, the changes need to be registered to the Undo system. This will a) create an Undo point to allow the user to undo the changes and b) synchronize the model to other users in an Edit Session. This can be achieved using Undo.initEdit and finishEdit.

### Undo.initEdit( aspects )

Initializes an edit. Call this when you are about to do an edit, before changing anything.

* `aspects`. Which aspects of the model to save. See [#Aspects](#aspects)

### Undo.finishEdit( edit_name[, aspects] )

* `action_name` Name of the performed edit.
* `aspects` Optional. If the set of aspects you are editing has changed, provide the changed aspects.

## Aspects

Aspects are used to tell Blockbench which parts of the model to save in an undo point. All aspects are within one `aspects` object. When adding or removing elements, textures etc., make sure the objects in question are stated in the first but not in the second aspects, or vice versa.

### selection
If true, the element and group selection will be saved

### elements
Array of all elements (cubes and locators) to save.

### outliner
If true, the complete outliner structure will be saved. This includes group data like names etc.

### group
A single group.

### textures
An array of textures.

### bitmap
If true, the content of the listed textures will be saved.

### uv_mode
When true, saves the current UV mode and project resolution settings.

### animations
Array of animations

### keyframes
Array of animation keyframes

### display_slots
Array of display slot ids, like `thirdperson_righthand` or `ground`

### uv_only
If true, only UV and face information of cubes will be saved.
