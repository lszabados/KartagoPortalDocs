# Tax number check

With the Tax number check function you can check a Hungarian or EU tax number.

## Check Hungarian tax number

Enter the first 8 digits of the tax number. The one-digit VAT code and the two-digit territorial classification code at the end of the tax number are not required, but if they are, they are not a problem. The separator "-" can also be included.

> The system doesn't really work with 3 more digits after the 8 digits, so if you enter an incorrect number there, it's no problem. 

> Please note that if you enter a tax number with more than 8 digits, the last 3 digits must match the result, because the system only searches for the 8 digit tax number and the end of the tax number may be different if it is found. 


### HU prefix in the tax number

You can also enter the EU comform Hungarian tax number which is the 8 digits of the tax number after the prefix HU. This makes it easier if you copy the tax number from somewhere else, you don't have to bother with omitting the HU prefix.

## EU tax numbers

The EU tax numbers are taken from the [VIES](https://ec.europa.eu/taxation_customs/vies/?locale=hu) system operated by the European Union.

### EU tax number structure


|Member State|Development|Format|
|--------|:--------:|--------|
|AT-Austria|ATU99999999|Single character string consisting of 9 characters|
|BE-Belgium|BE0999999999 , BE1999999999|Single sequence of 10 digits|
|BG-Bulgaria|BG99999999999 , BG99999999999999|Single sequence of 9 or 10 digits|
|CY-Ciprus|CY9999999999L|Single character string consisting of 9 characters|
|CZ-Cseh Republic|CZ99999999999999 , CZ99999999999 , CZ99999999999999|Single sequence of 8, 9 or 10 digits|
|DE-Germany|DE999999999|Single sequence of 9 digits|
|DK-Denmark|DK99 99 99 99 4|Series of 2 digits each|
|EE-Estonia|EE999999999|Single sequence of 9 digits|
|EL-Greece|EL999999999|Single sequence of 9 digits|
|ES-Spain|ESX9999999999X4|Single string of 9 characters|
|FI-Finland|FI9999999999|Single sequence of 8 digits|
|FR-France|FRXX 99999999999|A sequence of characters consisting of 2 characters and a sequence of 9 digits|
|HR-Croatia|HR99999999999|Single sequence of 11 digits|
|HU-Hungary|HU9999999999|Single sequence of 8 digits|
|IE-Ireland|IE9S99999L, IE9999999WI|Single character string consisting of 8 or 9 characters|
|IT-Italy|IT99999999999|Single sequence of 11 digits|
|LT-Lithuania|LT99999999999,LT9999999999999999|Single sequence of 9 or 12 digits|
|LU-Luxembourg|U99999999|Single sequence of 8 digits|
|LV-Latvia|LV9999999999999|Single sequence of 11 digits|
|MT-Malta|T9999999999|Single sequence with 8 digits|
|NL-Holland|NLSSSSSSSSSSSSSSSS|Single string of 12 characters|
|PL-Poland|L999999999999|Single sequence of 10 digits|
|PT-Portugal|PT999999999|Single sequence of 9 digits|
|RO-Romania|RO999999999|Single sequence with at least 2 digits and up to 10 digits|
|SE-Sweden|SE9999999999999999|Single sequence with 12 digits|
|SI-Slovenia|SI999999999999|Single sequence with 8 digits|
|SK-Slovakia|SK99999999999999|Single sequence with 10 digits|
|XI-From Ireland|XI999 9999 99, XI999 9999 99 9995, XIGD9996, XIHA9997|1 block of 3 digits, 1 block of 4 digits and 1 block of 2 digits; or the above followed by a block of 3 digits; or 1 block of 5 characters|



**Explanation:**
    
    - *: The format does not include the two-letter country code
    - 9: digit
    - X: letter or digit
    - S: letter; digit; or one of the following symbols: +, *
    - L: letter
    
 **Notes:**
    
    1. The first character following the country code is always 'U'.
    2. The first digit following the country code is always '0'.
    3. The (new) 10-digit format is created by adding a zero to the beginning of the (former) 9-digit number sequence.
    4. The first and last characters can be a letter or a number, but not both.
    5. Indicates a branch.
    6. Indicates government offices.
    7. Indicates health authorities.
    8. Case-sensitive. Please enter the tax number in the search box exactly as shown here.

### What should I do if my customer's tax number is invalidated by the system?

The Commission's website is a real-time information system that checks the validity of tax identification numbers using databases managed by the Member States. So when you check a tax number in the system, you are actually checking it against the Member State database.

If the system indicates that your customer's EU VAT number is invalid, you should contact the tax authority in the country where your customer is based to resolve the problem.

### What should I do if the system does not work?

The Commission's website is a real-time information system that checks the validity of tax identification numbers using databases managed by Member States. So when you check a tax number in the system, you are actually checking it against the Member State database.

The system may not be able to perform certain queries at certain times due to maintenance of the national databases.

The Commission is aware of this problem and is working with Member States to ensure that databases are inaccessible for maintenance and updating for as short a period as possible.

### Can the name and address associated with the tax number be queried?

Some Member States allow the system to display the name and address of the taxable person if the EU VAT number is valid. If the name and address are not displayed, this means that the Member State that issued the tax number does not allow this information to be displayed.

Customers have the right to obtain information from their tax authorities on whether the EU VAT number includes a name and/or address.

### Austrian tax numbers

For Austria, the correct prefix is "AT". All Austrian tax numbers begin with the letter "U". Therefore, if you want to check the validity of an Austrian tax number, you must enter the letter "U" as the first character after "AT".

### I checked the validity of a Spanish tax number. The number is valid but the name and address of the taxable person are not displayed.

For Spain, the name and address information cannot be retrieved from the tax number.