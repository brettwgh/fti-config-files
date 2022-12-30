# Fuel Transaction Import Add-In

## Provider Configuration File Structure
This describes the configuration file structure with it's properties and how to correctly compile it in order to successfully import [fuel transaction data](https://geotab.github.io/sdk/software/api/reference/#FuelTransaction) into the MyGeotab database system.

## Configuration File properties

**Name** (**Required**): Represents the name of the Fuel Provider. This name will be listed in a dropdown menu in the Add-in to fascilitate the provider selection in the import process.

**unitVolumeLiters** (default = Y): Y/N (boolean) value that specifies if the fuel in the transaction file is expressed in liters or gallons. Accepts only “Y” or “N".

**unitOdoKm** (default = Y): Y/N (boolean) value that specifies if the odometer in the transaction file is expressed in km or miles. Accepts only “Y” or “N”.

**isCellDateType** (default = Y): Y/N (boolean) value that specifies if the date cell in the Excel file is of a Date format or not. By default, the value is “Y” and indicates that the format is a date in Excel. If it is a date, the software does not check how the dateFormat field is filled. If it is date and time composed by multiple cells (for example, ColumnC + ColumnB), it is mandatory to fill out both fields dateFormat and timeFormat.

**dateFormat** (**Required**): Specifies the date format to be expected in the transaction file. This property can include the time depending on whether the time is contained in the same excel column or not, refer to the [date & time rules](#DateTimeRules) below.

Examples:
* DD/MM/YYYY
* YYYYDDMM
* YYYY-MM-DDTHH:mm:ss
* MM/DD/YYYY HHmmss
* DD/MM/YYYYTHH:mm:ss.SSSZ
* etc.

**timeFormat**: Defines the time format if the date and time values are contained in separate excel columns in the import file e.g. HHmmss or HH:mm:ss etc. Refer to the [date & time rules](#DateTimeRules) below.

**currencyCodeMapped** (default = USD): The ISO formatted currency code to be used if no currency code is found in the import excel file. Examples - https://www.iso.org/iso-4217-currency-codes.html.

**data**: a JSON object containing some or all of the [FuelTransaction](https://geotab.github.io/sdk/software/api/reference/#FuelTransaction) properties.

<table>
<tr><th>Data Metric</th><th>Details</th><th>Example</th></tr>
<tr><td>Location</td><td>Provide the location data (longitude & latitude) in an array</td>
<td>
<table>
<tr><td>x</td><td>number</td><td>Specify x for the longitude.</td></tr>
<tr><td>y</td><td>number</td><td>Specify y for the latitude.</td></tr>
</table>
</td></tr>
<tr><td>Address (Location)</td><td>Provide the address information in a single column</td><td>"address":"columnx"</td></tr>
</table>

## Examples
- A shell source file can be found here [source.json](source.json).
- The generic source reference file can be downloaded from [here](generic.json).

## <a name="DateTimeRules">Date & Time Rules</a>
1. **dateFormat** is required
2. If **date** and **time** are submitted in a **single** excel column then the complete **date and time format** should be provided in the **dateFormat** property of the configuration file.
3. If **date** and **time** are submitted in **separate** excel columns then the **date format** should be provided in the **dateFormat** property and the **time format** should be provided in the **timeFormat** of the configuration file.
