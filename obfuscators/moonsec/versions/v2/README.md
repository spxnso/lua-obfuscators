# Moonsec v2

## Settings

- StringEncryption (default: false)
- ConstantEncryption (default: false)
- AntiDump (default: false)
- SmallOutput (default: false)

## Macros

MoonSec provides a small set of convenient macros to control how the obfuscator treats strings and comparisons, plus helpers for debugging. Use macros inline in your source strings (they’re detected by literal prefix) or in code where noted.

## `ENCRYPT:` String encryption

Prefix a string with `ENCRYPT:` to force MoonSec to encrypt that specific literal.

Usage:

```lua
local str1 = "ENCRYPT:Hi LOL"
local str2 = [[ENCRYPT:Whats good?]]
local api = game:HttpGet("ENCRYPT:https://f3d.at")
local a = [[ENCRYPT:
Multiline
thing]]
```

## `NO_ENCRYPT:` Exclude from encryption

If you want to encrypt all strings but a specific one, include `NO_ENCRYPT:` in the string.

Usage:

```lua
local c = "NO_ENCRYPT:Hello there";
local f = [[NO_ENCRYPT:Hello world!]]
local x = 'NO_ENCRYPT:Hello!';
local s = [[NO_ENCRYPT:
Multiline
string
]]
```

Notes:

- Strings smaller than 4 characters or longer than 512 characters will not be encrypted.

## `GetDST(<void>)` Get decrypted string table

Returns the table that stores decrypted strings. This can be used for debugging purposes or to modify a string directly from the script.

Usage:

```lua
table.foreach(GetDST(), print)

for i,v in pairs(GetDST()) do
    if v == "Hello world" then
        GetDST()[i] = "New value"
    end
end
```
