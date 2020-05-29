# Blender 2.8 Cheatsheet
1. [Select Related](#select-related)
	1. [All Objects](#all-objects)
	1. [Select, Active](#select-active)
1. [Track](#track)

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
