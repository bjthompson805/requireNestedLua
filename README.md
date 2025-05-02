# requireNested.lua

## Description

This module overrides the require() function so that module namespaces can be used when accessing modules during instantiation.

Example: A module is created under lib/LibraryX/ModuleY.lua. When you add the 'lib' directory to the package.path as './lib/?.lua', you will be able to resolve the directory structure and avoid naming conflicts when using the normal 'require()' function, by saying 'require("LibraryX.ModuleY"). But, when instantiating the object, the module would need to be accessed as 'ModuleY', i.e. 'local obj = ModuleY:new()'. This override allows you to access the module as 'LibraryX.ModuleY:new()' without erroring out.

## Example Code

The following is an example code snippet of how this module is used. The module instantiation (new()) can now be invoked using the full path.

```
-- Set path of our modules (lib).
package.path = package.path .. ";.\\lib\\?.lua"

require "requireNested"
require "Test.TestSubdir.TestSubdir2.TestModule"

local obj = Test.TestSubdir.TestSubdir2.TestModule:new()
```
