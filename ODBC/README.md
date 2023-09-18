# ODBC Connector Package

This connector facilitates operations related to querying data via ODBC. The connector's code is written in PowerShell.

## Connectors:

### 1. ODBCQuery
Executes an ODBC query.

**Inputs:**
- `username (String)`: Database username.
- `password (String)`: Database password.
- `database (String)`: Name of the database.
- `server (String)`: Server name or address.
- `query (String)`: SQL query to execute.

**Outputs:**
- `HasError (Boolean)`: Indicates if an error has occurred.
- `ErrorMessage (String)`: Contains an error message if any error has occurred.
- `arrStrucOut (Array of StrucOut)`: An array of structures containing data from the query results.

## Structures:
### 1. StrucOut
Represents a row of the query result.
| Member Name | Type      | Description                       |
|-------------|-----------|-----------------------------------|
| column_a    | String    | First column data from the result |
| column_b    | String    | Second column data from the result|
| column_c    | DateTime  | Third column data from the result |

**Developer's Note:** The code uses PowerShell to interact with the database through ODBC. Ensure you have the necessary permissions and environment setup to execute PowerShell scripts and ODBC connections.

