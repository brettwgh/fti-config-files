# Fuel Transaction Import Add-In - Provider Configuration File Structure

## Config File properties

**Name** (Required): Represents the name of the Fuel Provider. This name will be listed in a dropdown menu in the Add-in.

**unitVolumeLiters**: Boolean value that specifies if the fuel in the transaction file is expressed in liters or gallons. Accepts only “Y” or “N”. This is a mandatory field, and cannot be empty.

**unitOdoKm**: Boolean value that specifies if the odometer in the transaction file is expressed in km or miles. Accepts only “Y” or “N.” This is a mandatory field, and cannot be empty.

**isCellDateType**: Boolean value that specifies if the date cell in the Excel file is Date format or not. By default, the value is “Y” and indicates that the format is a date in Excel. If it is a date, the software does not check how the dateFormat field is filled. If it is date and time composed by multiple cells (for example, ColumnC+ColumnB), it is mandatory to fill out both fields dateFormat and timeFormat.

**dateFormat**: Mandatory. Specifies the format found in the transaction file. Look at the table below in order to know the formats allowed. e.g. DD/MM/YYYY or YYYYDDMM etc.

**timeFormat**: Defines the time format if applicable e.g. HHmmss or HH:mm:ss etc.

**currencyCodeMapped**: The ISO formatted default currency code to be used if no currency code is found in the import excel file. Examples - https://www.iso.org/iso-4217-currency-codes.html.

**data**: The data object containing some or all of the MyGeotab SDK [FuelTransaction](https://geotab.github.io/sdk/software/api/reference/#FuelTransaction) properties.

Refer to the source files:
* [source.json](source.json) 
* [source-new.json](source-new.json)
