# Duplicate LibXXXXX.so Counter For GameGuardian
Uses GameGuardian's built-in functions to (try) ignore duplicate libraries created by emulators due to some issue with x86-64 architecture.

This tool is used when hex patching on PC Emulators such as Bluestacks using GameGuardian where there are 2 LibXXXXX.so. This script has a function to ignore the fake LibXXXXX.so and edit the real LibXXXXX.so. (NOTE THAT EDITS MAY VARY AND FUNCTION(s) MAY FAIL DUE TO SPACE PADDING OR SCRIPTING ISSUE)

# Concept
It uses some math to check and get information about the hex to be passed on to the counter function (Note that this only supports 32/64 bytes of hex). After it is passed onto the counter function, it searches those bytes and checks if there are double the results, if so then the script will remove (ignore) the first 32/64 bytes basically ignoring the first library in hopes that it's the duplicate one and edits the last 32/64 bytes. (Note that if the first few results are the real lib, then it will edit the fake one.)

### Usage Example:
```lua
hex = "F5 53 BE A9 F3 7B 01 A9 35 8C 02 90 A8 1E 78 39 F3 03 01 2A F4 03 00 AA C8 00 00 37 60 64 02 90 00 84 46 F9 63 4A E2 97 28 00 80 52 A8 1E 38 39 94 36 40 F9 E0 03 13 2A E1 03 1F AA 5D F7 93 94"
edithex = "00 00 80 D2 C0 03 5F D6"
len, formathex = getHexInfo(hex)
counterDupeLib(len, formathex, edithex)
```
