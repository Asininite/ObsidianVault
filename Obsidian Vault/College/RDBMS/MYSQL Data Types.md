#DBMS
### Numeric

- **INT/INTEGER:** 4-byte integer.
- **TINYINT:** 1-byte integer.
- **SMALLINT:** 2-byte integer.
- **MEDIUMINT:** 3-byte integer.
- **BIGINT:** 8-byte integer.
- **DECIMAL(p,s):** Exact decimal with precision `p` and scale `s`.
- **FLOAT:** Single-precision floating-point.
- **DOUBLE:** Double-precision floating-point.

### Date and Time

- **DATE:** YYYY-MM-DD format.
- **TIME:** HH:MM:SS format.
- **DATETIME:** YYYY-MM-DD HH:MM:SS format.
- **TIMESTAMP:** Timestamp as number of seconds since Unix epoch.
- **YEAR:** YYYY or YY format.
### String

- **CHAR(n):** Fixed-length string with maximum length `n`.
- **VARCHAR(n):** Variable-length string with maximum length `n`.
- **TEXT:** Large text string.
- **ENUM('value1', 'value2', ...):** Enumeration of allowed values.
- **SET('value1', 'value2', ...):** Set of allowed values.
### Other
- **BINARY(n):** Binary byte string with fixed length `n`.
- **VARBINARY(n):** Binary byte string with variable length `n`.
- **BLOB:** Binary large object.
- **JSON:** JSON data.
### Spatial (for GIS)

- **GEOMETRY:** Geometric object (point, line, polygon).
- **POINT:** Geographic point.
- **LINESTRING:** Geographic line.
- **POLYGON:** Geographic polygon.

```
CREATE TABLE ExampleTable (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  age TINYINT,
  height DECIMAL(5,2),
  birthdate DATE,
  registration_datetime DATETIME,
  is_active BOOLEAN,
  profile_text TEXT,
  image_data BLOB
);
```