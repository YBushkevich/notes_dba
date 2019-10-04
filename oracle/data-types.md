# Oracle datatypes



## Character datatypes

	The character datatype store character (alplanumeric) data in strings, with byte values corresponding to the character encoding scheme, generally called a character set of code page.

### CHAR Datatype

	The `CHAR` datatype stores a fixed-length character strings. When you create a table with a `CHAR` column, you must specify a string length (in bytes or characters) between 1 and 2000 bytes for the `CHAR` column width. The default is 1 byte. Oracle then guarantees that:

	* When you insert or update a row in the table, the value for the `CHAR` columb has the fixed length.
	* If you give a shorter value, then the value is blank-padded to the fixed length. 
	* If a value is too large, Oracle Database returns an error.

### VARCHAR2 and VARCHAR Datatypes

	
