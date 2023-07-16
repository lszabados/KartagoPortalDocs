# Troubleshooting

After loading the ´65 form, you will receive an email containing both the generated ´65 Form XML file and a text document about the processing and errors.

## About unhandled errors

Some of the errors are of a nature that the program does not provide a solution for, but only draws attention to them.

### No tax number

If there is no tax number in an SAP line, no vendor can be defined. Since the M-sheets have to be filled in by vendor, the line cannot be worked with without defining the tax number.

For such rows, a warning is displayed that the row cannot be processed. The line is ignored.

### Tax number length is not correct

If the tax number in an SAP line is typed out, it is not possible to define a vendor. Since the M-sheets have to be filled in by vendor, the line cannot be processed without specifying the tax number.

For such rows, a warning is given that the row cannot be processed. The line is ignored.

### Tax number is incorrect, NAV system cannot retrieve valid data

If an incorrect tax number is entered in a SAP line, it is not possible to define a vendor. Since the M-sheets have to be filled in per supplier, it is not possible to work with the line without specifying the tax number.

For such rows, a warning is given that the row cannot be processed. The line is ignored.

## Recorded invoices with errors

When the vendor is identified by the tax number in the SAP list, the invoice is found in the list and is added to the M tabs.
There are 3 possible cases for invoices found in this way:

1. an invoice fixed from NAV Online was found for the line. Here the invoice details are correct.
	- If the invoice number in the SAP list matches exactly the number of the fixed invoice, no comment will be added to the line.
	- If the invoice numbers do not match exactly, a comment **Check that the invoice number is correct** will be added to the line.
	
2. SAP line is used by the program to generate the invoice. In this case, the messages **Automatically generated invoice** and **Check that the invoice number is the correct e.** will be sent to the SAP system. 

3. This usually happens when the invoice does not come from NAV and for some reason it has been manually recorded in the past.
    - If the invoice numbers do not match exactly, a **Check that the invoice number is correct e** comment will be added to the line.

### "Check if the account number is correct" message 

In some cases, a NAV invoice is found based on the line from SAP, but the invoice number does not match exactly. The program uses a logic to find a matching NAV invoice for invoices that do not match exactly.

In such cases, the match is only probable, but the program cannot be sure, so it enters the invoice number recorded in SAP as My Reference for the NAV invoice, but marks the invoice as not an exact match, it needs to be checked.

If the match was correct, just close the comment.

If there was an incorrect match the following should be done:

- Pull out the invoice to check if the invoice number has been typo'd.
- We unmatch the account by deleting the **Relate to ** field.

There are then 2 options

1. search for all invoices based on the vendor's tax number and see if the invoice is included. If so, we enter the invoice number in SAP in the **Supplier reference** field.
2. If no matching invoice is found, we manually record it in the system.

> When manually recording, record the invoice details accurately based on the original invoice! If the SAP invoice number is different from the real one, change it after saving and enter the invoice number in SAP in the **Supply reference** field.

> Copy if possible, do not type. It is important to enter the reference exactly, including breaks and signs.

### "Automatically generated invoice" message

During processing, if no match is found based on the SAP invoice number, an invoice is recorded. This invoice is partial, dates and amounts must be checked in any case.

Here again, the first thing to do is to retrieve the original invoice and search for the invoice number in the system.

> When searching, don't forget to uncheck **Only with open messages**.

- If we have found an invoice, we delete the invoice recorded with the SAP invoice number and enter the invoice number recorded in SAP in the **Sort ID** field of the NAV invoice found.
- If no invoice was found, correct the pre-fixed invoice based on the original invoice (invoice number, dates, amounts). In the invoice number field, enter the **exact** invoice number on the original invoice and in the **variety reference** field, enter the invoice number in SAP.

> It is advisable to start a correction by copying the pre-fixed invoice number to the clipboard, because when making a correction or just entering a reference, you only need to paste it, avoiding typing errors.

### "Negative sign invoice without referenced original invoice" message

If you have a negative sign account and it cannot be linked to a NAV account, there are two possibilities:

1. Leave it as it is, we can close the messages. The program always throws it to the error list, but don't bother. A negative account will not be placed on the M-sheets.
2. The account is a modifying account. In this case, the value of the **Operation** field must be corrected from CREATE to MODIFY or STORNO. In this case, the **Original invoice number** field must be completed. If the original invoice is not recorded in the system, record it. Also look for any additional modifying invoices issued and if they are not in the system, record them. Make sure that the **Original invoice number** field is the same for all of them!

> The nav system allows you to record a modification invoice without the original invoice. In this case, the **Modifying invoice without original invoice ** field is ticked. This is not good for us, we have to record the original invoice as well, because we need it for the return.

> There will be less and less "non nav" invoices in the system, because in principle all invoices should already be sent in.
