# udf-debuf
The is no easy way to debug Lua, and Aerospike's uUser Defined Functions are written in Lua. Aerospike disables the lua debug library because of it's inherent performance issues. Your only option is writing log messages.

This project is a set of helpful utility routines that help debug Aerospike UDFs by writing useful message to the aerospike log.

## Function Library
### tprint()
`tprint()` recursively prints a table to the Aerospike log in a human readable format.
`dump()` dprints the variable in the current scope.

This is a work in progress, and I will produce more routines in time

