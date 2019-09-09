# Outliner

## Outliner management

### OutlinerElement()

Parent of all groups and elements in the outliner. All properties and methods can be used on groups and elements.

* `title` Title used for the hover tooltip
* `type` Type of the group or element
* `menu` Context menu of the group or element type.
* `selected` Array (or single object in case of group) or the selected elements of this type
* `all` Array of all groups or elements of this type

#### OutlinerElement.init()

Initializes the element so it can be used in the outliner.

#### OutlinerElement.addTo( destination )

Adds the element to a specific place in the outliner.
* `destination` Can be a group, element or undefined for the outliner root.

#### OutlinerElement.sortInBefore( destination, index_mod )

Sorts the element in before another element.
* `destination` Reference group or element
* `index_mod` Modifier for the index. If 1, the element will be placed after (below) the destination.

#### OutlinerElement.getParentArray()

Returns the children array of the parent that the group or element is in.

#### OutlinerElement.showInOutliner()

Unfolds the outliner and scrolls up or down if necessary to show the group or element.

#### OutlinerElement.updateElement()

Updates the Vue node of the element.

#### OutlinerElement.remove()

Removes the element.

#### OutlinerElement.rename()

Marks the name of the group or element in the outliner for renaming.

#### OutlinerElement.saveName()

Saves the changed name of the element by creating an undo point and making the name unique if necessary.

#### OutlinerElement.createUniqueName()

Create a unique name for the group or element by adding a number at the end or increasing it.

#### OutlinerElement.isChildOf( group, max_levels )

Checks of the group or element is a child of `group`.
* `group` A group
* `max_levels` The maximum number of generations that can be between the element and `group`.

#### OutlinerElement.showContextMenu( event )

Displays the context menu of the element
* `event`. Mouse event, determines where the context menu spawns.


## Group

### new Group( data )

* `data` Object
	* `name` Group name
	* `children` Array of the groups content
	* `origin` Array of the group pivot point
	* `rotation` Array of the group rotation
	* `reset` If a bone, whether to reset the informations of inherited bones in bedrock edition.
	* `shade` Whether to shade the contents of the group
	* `selected` Whether the group is selected
	* `visibility` Whether the group is visible
	* `export` Whether to export the entire group
	* `autouv` Auto UV setting for the children. Can be 0, 1 or 2.
	* `parent` Parent group or `'root'`
	* `isOpen` Whether the group is currently opened in the outliner
	* `mesh` 3D representation of the group when using bone rig

### Group.selected

Static variable to get the currently selected groups. Note that children groups of this group can also have `selected` to make them appear selected in the outliner, but will not be treated as the primary selected group

#### Group.extend( data )

Modify data of the group.
* `data` Object of properties to apply to the group

#### Group.selectChildren( event )

Select the children of the group

#### Group.selectLow( highlight )

Select the group and its children without marking it the selected group.
* `highlight` Whether to highlight the group in the selection color in the outliner. Default is true.

#### Group.unselect()

Unselects the group

#### Group.matchesSelection()

Returns true if the content of the group matches the current selection.

#### Group.openUp()

Opens the group and all of its ancestor groups.

#### Group.remove( undo )

Removes the group
* `undo` If true, an undo point will be created.

#### Group.resolve()

Remove the group and leave all of its children in the parent array.

#### Group.transferOrigin( origin )

Move the origin of a bone to a specific location without visually affecting the position of it's content.
* `origin` Array of the new 3D origin

#### Group.sortContent()

Sort the content of the group alphabetically. This will automatically create an undo point.

#### Group.diplicate()

Duplicate the group

#### Group.getSaveCopy()

Returns a copy of the group that can be used to save the group to a JSON file.

#### Group.getChildlessCopy()

Returns a copy of the group without the children. Internally used by the duplicate function.

#### Group.compile( undo )

Generates a copy of the group that can be used for undo points or to save in block model files.
* `undo` Make the copy work for undo points.

#### Group.forEachChild( callback, type, for_self )

Run a funtion for each child of the group recursively.
* `callback` Function to run for each child. First argument is the child.
* `type` For which type to run the function. Can be `Group`, `NonGroup`, `Cube` etc. or undefined.
* `for_self` Whether to also run the function on itself.


## Cube

Cubes represent regular cubes in the outliner. Cubes inherit all properties and methods from OutlinerElement and NonGroup.

### new Cube( data ).init()


## Locator
