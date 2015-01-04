# rarchdb
A small read only database
Mainly to be used by retroarch

# Usage
To convert a dat file use `dat_converter <dat file> <db file>`

To list out the content of a db `rarchdb_tool <db file> list`
To create an index `rarchdb_tool <db file> create-index <index name> <field name>`
To find an entry with an index `rarchdb_tool <db file> find <index name> <value>`

The util `mkdb.sh <dat file> <db file>` will create a db file with indexes for crc sha1 and md5

# lua converters
In order to write you own converter you must have a lua file that implements the following functions:

~~~.lua
-- this function gets called before the db is created and shuold validate the
-- arguments and set up the ground for db insertion
function init(...)
	local args = {...}
	local script name = args[1]
end

-- this is in iterator function. It is called before each insert.
-- the function should return a table for insertion or nil when there are no
-- more records to insert.
function get_value()
	local args = {...}
	local script name = args[1]
end
~~~
