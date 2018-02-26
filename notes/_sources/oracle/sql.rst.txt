===
SQL
===

SQL to update a column from another table
=========================================
UPDATE
    Sales_Import SI,
    RetrieveAccountNumber RAN
SET
    SI.AccountNumber = RAN.AccountNumber
WHERE
    SI.LeadID = RAN.LeadID;

