# Large-Messy-Hospital-Data---HUGE-CLEANING-DONE
I Have Transformed Large Uncleaned Data Into Easy to Understandable Data..
150 Columns , 25 Issues found , 9 Critical
Duplicate columns , Multiple columns store the same data:
GenderGENDER  ·  Blood Typeblood_type  ·  Bill Amountbill_amt  ·  Admission Dateadmission date  ·  Room No.room_number
→ Keep one column per field, drop the redundant ones ( ISSUES FOUND )
Critical
Inconsistent date formats
DOB and admission dates appear in mixed formats:
dd/mm/yyyyyyyy-mm-dddd-mm-yyyy
→ Standardize all dates to one format e.g. YYYY-MM-DD using pandas to_datetime()
Critical
Inconsistent categorical values
Gender uses 10+ variants: MalemaleMALEMm
Payment status: PaidPAIDpaidpartialPending
→ Normalize with .str.strip().str.upper() then map to standard values
Medium
Age column mixed types
age column has numeric entries like 34 mixed with strings like 34yrs
→ Strip non-numeric characters, convert to integer
Medium
Inconsistent doctor names
Doctor has: Dr. MehtaDR MEHTAdr. sharmaDoctor Sharma — same doctor, different spellings
→ Standardize to "Dr. Lastname" format; cross-reference with Doctor ID column
Medium
Missing discharge dates
Discharge Date is blank for ~10% of rows — could mean patient is still admitted or data is missing
→ Flag as "Active Admission" vs null with a new status column
Medium
Inconsistent ward names
GeneralgeneralGENERALicuICU
→ Apply .str.title() or a manual mapping dictionary
Low
Inconsistent column header names
Headers mix snake_case, ALLCAPS, spaces, trailing spaces: patientIDPATIENT NAMEage
→ Rename all headers to consistent snake_case
Low
Arbitrary cell highlighting
Random cells have yellow/red fill with no documented meaning
→ Remove all formatting or document what each highlight color means
