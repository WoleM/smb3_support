
# Infos

This is a modified version of the lua with additional support for the emulator that runs the TAS bot made by orange.
This works with rom (U)PRG0


# Installation && Information

First you will have to replace the lua the emulator running with [this modified one](https://github.com/WoleM/smb3_support/raw/main/lua51.dll)

A fully working script with the boxes and sound can be found [here](https://github.com/WoleM/smb3_support/raw/main/eh-helper-v0.4.lua)

The audio file must be in the same path as the lua. A demo sound can be found [here](https://github.com/WoleM/smb3_support/raw/main/alarm.wav)

## Scripting will now have additional abilities.
new build relies much on math so make sure to first include:

```lua
require 'math';

```

Enabling additional extension before anything else:
```lua
local libinit = package.loadlib("lua_extensions.dll", "libinit")
libinit()

```

Call extension functions:
```lua
local alert = package.loadlib("lua_extensions.dll", "lua_alert")
alert("ingga")--this will pop up a message and freeze the application until you click ok
```
Acoustic information:
```lua
local acoustic = package.loadlib("lua_extensions.dll", "lua_acoustic")
acoustic(0, frame)--first parameter is delay to play the sound, zero is when u hit it from teh back, -1 plays the sound 1 frame earlier, 3 plays the sound 3 frames later(can be mixed with finish card audio if overlaps) for each earlier frame u apply same ammount should be added to the framecounter and vice versa (read script)

```

Experimental functionality:

to add any custom native code to your scripts without messing with the lua compilng you can call:
```lua
insert_code()

```
This can automatically load your native dll if exists under the same directory with lua named as "charlize.dll".
The exported function has to be named "code" and must be an int without any params, for now.

```cpp
extern "C" __declspec(dllexport) int code()
{
    //ur stuff
	return 0;
}
```


