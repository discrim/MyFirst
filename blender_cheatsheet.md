# Blender 2.8 Cheatsheet
1. [Misc](#misc)
	1. [Python Tooltips / Python References](#python-tooltips--python-references)
	1. [List All Objects](#list-all-objects)
	1. [Install Packages Using `pip`](#install-packages-using-pip)
1. [Select Related](#select-related)
	1. [All Objects](#all-objects)
	1. [Select, Active](#select-active)
1. [Track](#track)
1. [Render](#render)

## Misc
### Install Packages Using `pip`
1. Locate the directory of Blender's Python. E.g. `D:\Program Files\Blender Foundation\Blender 2.82\2.82\python`
1. Run terminal. (cmd, PowerShell, etc.) You may need to run it as administrator.
1. Go to the directory's binary folder.
	```
	C:\WINDOWS\system32> D:
	D:\> cd "D:\Program Files\Blender Foundation\Blender 2.82\2.82\python\bin"
	D:\Tools\Blender Foundation\Blender 2.82\2.82\python\bin>
	```
1. Use `pip` as a normal Python.
	```
	D:\Tools\Blender Foundation\Blender 2.82\2.82\python\bin> .\python.exe -m pip install scipy
	```
### Python Tooltips / Python References
Many buttons, drop-down menus, or anything that is clickable shows a tip when you hover your mouse.  
If you want to see Python code, reference, tooltips when hovering any menus:
> Go to the top left of the Blender window > `Edit` > `Preferences...` > `Interface` > `Display` > Check 'Python Tooltips'.  

Now, for example, if you select a cube in front of you, click 'Object Properties' (at the middle right part of the screen, an orange square with four right-angled snapped sides), hover your mouse over the value (maybe 0m) next to 'Location X', now the tooltip includes
```
Python: Object.location
bpy.data.objects["Cube"].location[0]
```
This means if you run a script `bpy.data.objects["Cube"].location[0] = 3` then its location along x-axis will change into 3m.
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
### Render
```python
# Full path including filename, excluding extension.
bpy.data.scenes["Scene"].render.filepath = "D:/Pictures/Blender_Renderings/image1"
# Shows the parameters of rendering. You can render animation, still image, etc.
print(bpy.ops.render.render)
# Saves still image (= screenshot = screen capture) from the camera view
bpy.ops.render.render(write_still=True)
```
