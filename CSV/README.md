# Omnitracker CSV Import Connector

This connector facilitates various operations related to importing data from CSV files. It is intended to be used with Omnitracker, and the various connectors are outlined below.

## Features:
- Import specific rows.
- Import specific columns.
- Retrieve a specific value.
- Import all rows and columns.

## Connectors:

### 1. CSV Import - specific row/all columns
This connector returns all columns of a specific row.

**Inputs:**
- `RowNumber (LongInt)`: The row number to fetch.
- `Path (String)`: The path to the CSV file.

**Outputs:**
- `strHasErrorOut (Boolean)`: Indicates if an error has occurred.
- `strErrorMessageOut (String)`: Contains an error message if any error has occurred.
- `strucStrucRowOut (StrucOutRow)`: Structure containing the row data.
- `strHasRowOut (Boolean)`: Indicates if the row exists.

### 2. CSV Import - all rows/specifc column
This connector returns a specific column for all rows.

**Inputs:**
- `ColumnName (String)`: The column name to fetch.
- `Path (String)`: The path to the CSV file.

**Outputs:**
- `strHasErrorOut (Boolean)`: Indicates if an error has occurred.
- `strErrorMessageOut (String)`: Contains an error message if any error has occurred.
- `strucColumnOut (StrucOutColumn)`: Structure containing the column data.
- `strHasColumnOut (Boolean)`: Indicates if the column exists.

### 3. CSV Import - specific value
This connector retrieves a specific value from a given column and row.

**Inputs:**
- `ColumnName (String)`: The column name.
- `RowNumber (LongInt)`: The row number.
- `Path (String)`: The path to the CSV file.

**Outputs:**
- `strHasErrorOut (Boolean)`: Indicates if an error has occurred.
- `strErrorMessageOut (String)`: Contains an error message if any error has occurred.
- `strCellValue (String)`: The specific cell value.

### 4. CSV Import - all rows/all columns
This connector returns all rows and all columns.

**Inputs:**
- `Path (String)`: The path to the CSV file.

**Outputs:**
- `strHasErrorOut (Boolean)`: Indicates if an error has occurred.
- `strErrorMessageOut (String)`: Contains an error message if any error has occurred.
- `arrStrucsOut (Array of StrucOutRow)`: An array of structures containing data from all rows and columns.

## Structures:
### 1. StrucOutRow
Represents a single row of data.
| Member Name | Type   | Description   |
|-------------|--------|---------------|
| A           | String | Column A data |
| B           | String | Column B data |
| C           | String | Column C data |
| D           | String | Column D data |

### 2. StrucOutColumn
Represents a single column of data.
| Member Name | Type   | Description |
|-------------|--------|-------------|
| A           | String | Row A data  |
| B           | String | Row B data  |
| C           | String | Row C data  |
| D           | String | Row D data  |

## Note:
For all connectors, error handling mechanisms are in place. If an error occurs during the execution of any connector, the outputs `strHasErrorOut` will be set to true and `strErrorMessageOut` will contain the corresponding error message.

**Developer's Note:** This code uses PowerShell to interact with CSV files. Ensure you have the necessary permissions and environment setup to execute PowerShell scripts.
