# XX65M Cards

This function fills in the xx65M pages based on the txt export file received from SAP and the xx65 form XML file exported from the NAV's SAD system. 

## Sheet XX65

### What is a xx65 sheet?

The xx indicates the year. In 2021 it is 21, so for 2021 returns, the 65 sheets are marked with the number 2165.
Obviously for the year 2022 it is 2265. 

The 65 sheets contain pages marked A and M. This function of the program fills in the M sheets, this requires a basic 65 sheet export.

### Export xx65 file from the SSC system

For the program to work, a prepared 65 sheet (numbered 2165 in 2021) is required, with a minimum of the filing company details to be filled in. This is the company name and tax number.
It is possible to fill in additional data (sheets 2165A), this does not affect the operation of the system, it only affects the fields on sheet A that need to be filled in due to the aggregation of the M sheets.

The 65 sheet prepared in this way can be exported from the SSC system using the **Service/Developers/Create test XML file** menu item.

The export is placed in the user's folder on the local machine at ````AbevJava\import\pelda.xml````. 

> Full example: ````c:\users\%username%\abevjava\import\pelda.xml```, where %username% is the logged in user account name.

This is the filename that should be attached to the program.

<img src="images/ANYK.png">

## SAP export

### What is SAP export

The SAP export file contains the data needed to fill in the M sheets.

It is in a bound format, only a properly prepared export file will fit the program.

Please check that the format is as shown below:

<img src="images/sap-1.png">

It is also important to have tax numbers in the last column, because partners are identified by tax number.

<img src="images/sap-2.png">

## ´65 Loading pages

Start the program under the Finance menu:

<img src="images/65page-menu.png">

Select the 2 prepared files in the corresponding rows. Email value will be automatically filled in by the system based on the logged in user's preferences, but you can also enter another email address.

You can start the program by clicking on the **Fill** button.

<img src="images/65page-view.png">

The program will immediately go to the [Invoices](Finance/Invoices.md) module. At this point the data processing and loading has not taken place, no changes to the data have been made. The operation is performed by a background process and can take minutes. When it finishes it sends a screen message and emails the results.


## Result

The result of running the program is an email with 2 attachments. An error list and an XML file.

The error list contains the errors detected during the run. As long as the list contains errors that need to be fixed, the XML file is not accurate.

At the end of the error list, there is a separate section for errors that are not in the loaded table (in the open messages section). This is possible if the system finds a counter line that it cannot load into the table. Such as an incorrect or empty tax number. The system will only allow a verified good tax number, i.e. it will always check the tax number in the NAV system. If this fails, the system cannot include the invoice and it will be missing from the table.

The XML file must be loaded into the SAD system. All opened forms must be closed in the SSC system, at which point the menu item ```` service/import```` is available. Here you have to select the XML file you have downloaded from the email.

> when loading, select XML as the file type, otherwise you will not be able to select the saved file.

## Internal operation

On ´65 NAV forms, the system fills in the sheets marked M.
An M sheet must be issued for each supplying partner, so it is important to know the details of the supplying partner (Name, Tax number).
Sub-pages 02 and 02-K must be filled for each partner.

### M sheets marked 02

The invoices of the supplier must be entered one by one: invoice number, dates of issue and execution of invoices, net and VAT amounts of invoices in HUF 1000 units.

### Sheets marked 02-K

Invoices which were amending invoices and therefore original invoices previously.
List not only the invoice involved in the reclaim, but also the invoice that modified the original invoice and the invoice in the order of issue. There is a separate indication of which of these are taken into account in this return and which have been taken into account previously.

> According to the new NAV guidelines, there can be only one invoice and its amending invoices for the same transaction. In other words, if an invoice is completely spoiled and a new invoice is issued, the new invoice must refer to the original invoice and this invoice is considered as a modifying invoice. The system will in turn take into account the invoices as they are entered in the NAV or as they are recorded. On this basis, if the partner does not issue the invoices as required, we will either accept them as incorrect and report them to the NAV as such, or we will not accept them and have the partner correct them.

### SAP data and error possibilities

The data comes from the SAP system in a text file. This gives me a tax number identifying the supplier, an invoice number and a date.

#### Account number error
For invoices manually entered into the SAP system, invoice number errors are possible:
- The invoice number field in the SAP system is short, the original invoice number may not fit, so it is somehow entered into the system shortened
- Recording error
- Blank characters or delimiters are dropped when recording

#### Date error
A single completion date is transferred from the SAP system, but this may not be the date on the invoice, but the date that was recorded for the month. The tax authorities need the exact date on the invoice.

#### Amount error
In the SAP system, the amounts next to the invoice only include the amounts recovered but the total amount shown on the invoice should be included in the return.

#### Invoice duplication
In the SAP system, the same invoice number can be duplicated more than once if it contains several items with different VAT percentages. An invoice should only be transferred once to the NAV system

### Repair SAP Errors

Some of the errors in the data coming from the SAP system are automatically corrected by the system, others require user intervention. In order to keep track of invoices in a transferable way, a database is needed where the invoices with the exact data are stored.

#### Invoice database

The system contains an [invoice](/Finance/Invoices.md) database where all invoices are listed. The database is linked to the NAV online invoice system, so theoretically all domestic invoices are included with the exact details.

Invoices that are not included in the database are automatically pre-fixed by the system based on SAP data. This is incomplete and inaccurate, and therefore needs to be corrected on the basis of the original invoice.

#### Error handling

The system adds an error handling comment to the invoices. All such errors should be checked/corrected. Once all comments are corrected, the comments can be closed so that it is possible to track which errors have been addressed. 
After all errors have been handled, a list of no errors will be returned when the program is run again, at which point the completed form can be used.

#### Account number error

The system tries to select the correct invoice in the invoice database for the incorrectly entered short invoice number. If it finds a correctly similar invoice number, it matches the SAP invoice number with the invoice in the database. As this may be an error, you should check! If the matching is incorrect, the matching must be deleted and either the matching must be corrected or, if there is no matching invoice, it must be manually recorded.

#### Date errors

For invoices where the system has recorded the invoice from SAP data, the invoice dates should be checked and corrected.

#### Amount errors

For invoices where the invoice has been captured from SAP data, the net and VAT amounts of the invoice should be checked and corrected.