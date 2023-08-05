# SuperOBJ
Give OBJs composite static meshes, custom origins, parenting and sockets (empty)!

This enables you to import an OBJ as a whole asset and enables you to animate static meshes (more efficient) instead of building skeletal meshes every frame.

This file format is to be used as a separate file in the same directory as the `.obj` file.

# Example

Let's say we have body1 which should be a child of body2. Let's assume that body2 is an arm of some sorts, which has a joint (new origin) and a socket for holding items (socket).

obj:
```obj
# ...
o body1
v -0.839469 2.615359 -4.873873
vn 0.8655 -0.0064 0.5009
vt 0.599640 -0.931876
f 22/56/1 16/40/2 18/44/3
# [...]

o body2
# [...]
```

sobj:
```obj
o body1
parent body2
origin -0.839469 2.615359 -4.873873
socket socketName 0.5 -2.0 0.5

o body2
# [...]
```

Just as simple as that! Now write your own parser into your application if you need this new format.


# Motivation

I am writing a custom Minecraft mesh renderer (hence the Iris fork) and want to import mulitple objects with different origins and parenting from an obj file. FBX does already support all of this and MUCH more but OBJ is easy to parse for everyone and often the choice for a simple game engine or renderer.

# TODO
- Write Blender AddOn for exporting
- rotation
- implement socket rotation
- implement range of motion into joints (or new joint format alltogether)
