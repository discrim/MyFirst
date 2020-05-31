# Blender 2.8 Cheatsheet
1. [Misc](#misc)
	1. [List All Objects](#list-all-objects)
	1. [Python Tooltips / Python References](#python-tooltips--python-references)
1. [Select Related](#select-related)
	1. [All Objects](#all-objects)
	1. [Select, Active](#select-active)
1. [Track](#track)

## Misc
### Python Tooltips / Python References
Many buttons, drop-down menus, or anything that is clickable shows a tip when you hover your mouse. If you want to see Python code, reference, tooltips when hovering any menus, go to the top left of the Blender window > `Edit` > `Preferences...` > `Interface` > `Display` > Check 'Python Tooltips'. Now, for example, if you select a cube in front of you, click 'Object Properties' (at the middle right part of the screen, an orange square with four right-angled snapped sides), hover your mouse over the value (maybe 0m) next to 'Location X', now the tooltip includes `Python: Object.location / bpy.data.objects["Cube"].location[0]`. This means if you run a script `bpy.data.objects["Cube"].location[0] = 3` then its location along x-axis will change into 3m.
### List All Objects
```python
list(bpy.data.objects)
```
### Select Related
#### All Objects
```python
bpy.ops.objects.select_all(action='TOGGLE')
bpy.ops.objects.select_all(action='SELECT')
bpy.ops.objects.select_all(action='DESELECT')	# Most frequently used
bpy.ops.objects.select_all(action='INVERT')
```
#### Select, Active
```python
obj.select_set(True)  # Select obj. Deep orange border appears.
bpy.context.view_layer.objects.active = obj # Activate obj. Light orange border appears.
```
### Track
```python
bpy.ops.object.track_set(type='TRACKTO')  # Selected object(s) track(s) one active object.
bps.ops.object.track_clear(type='CLEAR')  # Remove tracking relationsthip.
```