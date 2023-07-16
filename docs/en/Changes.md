# Changes

## 4.0

2023.07.16

### Changes, What's new
- Adding **EUB** module to the system
- **Feature of **EUB **EUB
- **Comparative filtering** function

### Improvements
- New invoice and invoice change dialog captions are displayed correctly
- Update documentation
- NAV invoice download was regularly interrupted due to timeout, so the whole process was moved to a background thread where it can run for any length of time

## 2.1

2021.04.19

### Changes
- Addition of **Sort ID** to columns
- Add **File** to columns
- [Error Handling](Finance/ErrorHandling.md) description in documentation.
- At the end of this error list, errors that are not in the table are summarized (e.g. non-existent/void tax number for an invoice)

### Corrections
- Correction of duplicate invoice error
- Based on SAP list, the invoice identification did not give the best match.
- Processing stopped in case of invalid tax number. Fixed, incorrect tax number line ignored.
- Upload '65 sheets: the operation could be long, so it was moved to background thread. When done email notification and screen message is sent.

## 2.0

2021.04.15

- Support for form 2021
- Support for 2021 NAV Online data link (Nav Online 3.0)
- New user interface
- Documentation system
- Support for EU tax number queries

## 1.0 

2020.06.30

Baseline for 2020.

- Support for the 2020 form
- support for invoice uploading
- Query of tax number
- Nav Online system data query (Nav Online 2.0)