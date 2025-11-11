# Moonsec V3

## Settings

- Anti Tamper (default: false)
- Max security (default: false)
- Constant protection (default: false)

## Macros

MoonSec provides a small set of convenient macros to control how the obfuscator treats strings and comparisons, plus helpers for debugging. Use macros inline in your source strings (they’re detected by literal prefix) or in code where noted.

## `MS_ENCRYPT(<string>)` String encryption

Encrypts given string, alternatively you can use `ENCRYPT:` prefix too.

Usage:

```lua
print(MS_ENCRYPT('Hello World'));
local a = MS_ENCRYPT([[Oh god]]);
print(a, "ENCRYPT:Another hello world");

```

## `MS_WATERMARK(<string>)` Custom watermark

Changes the watermark on output files, and it will break the script if that watermark is somehow removed.

Usage:

```lua
MS_WATERMARK('SkiddedSS - Join us discord.gg/ğ')
print('hello world');
```

Notes:

- By default, this is `MS_WATERMARK([[This file was protected with MoonSec Private by Federal#9999]])`
- You can't pass a variable to this macro, because it is not actually a function defined in the code. The watermark gets replaced at parsing process, and function call gets removed from your code automatically.

## `MOONSEC_EXIT(<void>)` Exit the process

Kills the interpreter and ends the script execution immediately, with all sub-threads.

Usage:

```lua
-- example threads:
for i=1,15 do
    spawn(function() 
        while wait(1) do 
            print'x' 
        end 
    end)
end

print('bye bye');
MOONSEC_EXIT();
print('this will never be printed');
```

## `MOONSEC_GET_SCRIPT_ID(<void>)` Get script ID

This is an unique script identifier fingerprint, and it changs between every obfuscated file. IDs have a range between `111111111` and `999999999`

Usage:

```lua
print(MOONSEC_GET_SCRIPT_ID())
```
