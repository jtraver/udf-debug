# udf-debug
The is no easy way to debug Lua, and Aerospike's User Defined Functions are written in Lua. Aerospike disables the lua debug library because of it's inherent performance issues. Your only option is writing log messages.

This project is a set of helpful utility routines that help debug Aerospike UDFs by writing useful message to the Aerospike log.

## Function Library
### tprint()
`tprint()` recursively prints a table in a human readable format, to the Aerospike log.
### dumpLocal()
`dumpLocal()` prints the variables, in the current scope, to the Aerospike log.

##Example usage
```lua
local function filter_record(rec, filterFuncStr, filterFunc)
  -- if there is no filter, select all records
  if filterFuncStr == nil then
    return true
  end
  -- if there was a filter specified, and was successfully compiled
  if filterFunc ~= nil then
    local context = {rec = rec, selectedRec = false, string = string}

    -- sandbox the function
    setfenv(filterFunc, context)
    filterFunc()
    dumpLocal()
    return context.selectedRec
  end

  -- if there was a filter function, but failed to compile
  return true
end
```
## Conclusion
This is a work in progress, and I will produce more routines over time

