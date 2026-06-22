# LAB 1 - Create the Banking Data Model

**Estimated Time:** 40 minutes

## Lab Scenario

**Contoso Emirates Bank (CEB)** is developing a new retail banking
solution using Microsoft Power Platform. The application will store
information about customers, bank branches, and customer bank accounts
using Microsoft Dataverse.

As a Power Platform Maker, you will create three Dataverse tables,
establish relationships between them, and populate them with sample
banking data.

## Solution Overview

``` text
Customer
    │
    │ 1
    │
    ├──────────∞ Bank Account
    │
Branch
    │
    │ 1
    │
    └──────────∞ Bank Account
```

------------------------------------------------------------------------

# Exercise 1 - Create the Customer table

## Task 1 - Create a Dataverse table

1.  Open **https://make.powerapps.com**.
2.  Sign in using your Microsoft account if prompted.
3.  Verify that you are connected to the correct Power Platform
    environment.
4.  Select **Tables** from the left navigation.
5.  Select **+ New table**.
6.  Under **Create a table**, choose **Blank table**.

> **Why Blank table?**\
> A Blank table is used because you are creating a custom banking data
> model from scratch rather than using a standard template.

Configure the following properties:

  Property              Value
  --------------------- -----------
  Display name          Customer
  Plural display name   Customers
  Primary column        Name

7.  Select **Create**.

## Task 2 - Add the Email column (Detailed walkthrough)

1.  Ensure the **Customer** table is open.
2.  Select **Columns**.
3.  Select **+ New column**.
4.  Configure the column:

  Property       Value
  -------------- -------------------
  Display name   Email
  Data type      Email
  Required       Business Required

5.  Select **Save**.

## Task 3 - Add the remaining Customer columns

Repeat the previous process.

  ------------------------------------------------------------------------
  Display Name       Data Type     Required     Additional Settings
  ------------------ ------------- ------------ --------------------------
  Phone Number       Phone         Optional     None

  Gender             Choice        Optional     Male, Female, Other

  City               Single line   Optional     Max Length = 100
                     of text                    

  KYC Status         Choice        Business     Pending, Verified,
                                   Required     Rejected
  ------------------------------------------------------------------------

------------------------------------------------------------------------

# Exercise 2 - Create the Branch table

## Task 1 - Create the Branch table

1.  Navigate to **Tables**.
2.  Select **+ New table**.
3.  Choose **Blank table**.
4.  Configure:

  Property              Value
  --------------------- -------------
  Display name          Branch
  Plural display name   Branches
  Primary column        Branch Name

5.  Select **Create**.

## Task 2 - Add Branch columns

  -----------------------------------------------------------------------
  Display Name          Data Type        Additional Settings
  --------------------- ---------------- --------------------------------
  Branch Code           Autonumber       BR-{SEQNUM:000}

  City / Emirate        Choice           Abu Dhabi, Dubai, Sharjah,
                                         Ajman, Umm Al Quwain, Ras Al
                                         Khaimah, Fujairah

  SWIFT Code            Text             Max Length 11

  Manager Name          Text             Max Length 100

  Phone                 Phone            None
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Exercise 3 - Create the Bank Account table

## Task 1 - Create the table

1.  Navigate to **Tables**.
2.  Select **+ New table**.
3.  Choose **Blank table**.
4.  Configure:

  Property              Value
  --------------------- ----------------
  Display name          Bank Account
  Plural display name   Bank Accounts
  Primary column        Account Number

5.  Select **Create**.

## Task 2 - Add columns

  Display Name   Data Type   Additional Settings
  -------------- ----------- --------------------------
  Customer       Lookup      Related table = Customer
  Branch         Lookup      Related table = Branch
  Account Type   Choice      Savings, Current
  Status         Choice      Active, Inactive

------------------------------------------------------------------------

# Exercise 4 - Verify Relationships

1.  Open the **Bank Account** table.
2.  Select **Relationships**.
3.  Verify the following relationships were automatically created:

  Parent     Child
  ---------- --------------
  Customer   Bank Account
  Branch     Bank Account

No manual relationship creation is required because Dataverse
automatically creates relationships for Lookup columns.

------------------------------------------------------------------------

# Exercise 5 - Add Sample Data

## Task 1 - Add Customer records

1.  Open the **Customer** table.
2.  Select **Edit data**.
3.  Select **+ New record**.
4.  Enter the following records and select **Save** after each one.

  -------------------------------------------------------------------------------------------------
  Name       Email                         Phone Number       Gender     City      KYC Status
  ---------- ----------------------------- ------------------ ---------- --------- ----------------
  Ahmed Al   ahmed.almansoori@example.ae   +971501112233      Male       Dubai     Verified
  Mansoori                                                                         

  Fatima Al  fatima.suwaidi@example.ae     +971551234567      Female     Abu Dhabi Verified
  Suwaidi                                                                          

  Omar Al    omar.kaabi@example.ae         +971507654321      Male       Sharjah   Pending
  Kaabi                                                                            

  Aisha Al   aisha.mazrouei@example.ae     +971521987654      Female     Dubai     Verified
  Mazrouei                                                                         

  Sarah      sarah.thomas@example.ae       +971509876543      Female     Ajman     Rejected
  Thomas                                                                           
  -------------------------------------------------------------------------------------------------

## Task 2 - Add Branch records

1.  Open the **Branch** table.
2.  Select **Edit data**.
3.  Select **+ New record**.
4.  Enter the following records.

  ----------------------------------------------------------------------------------
  Branch Name   Branch Code  City / Emirate SWIFT Code  Manager Name  Phone
  ------------- ------------ -------------- ----------- ------------- --------------
  Dubai Mall    BR-001       Dubai          CEBUAEAD    Khalid Hassan +97142001111
  Branch                                                              

  Abu Dhabi     BR-002       Abu Dhabi      CEBUAEAD    Mohammed Ali  +97126221111
  Main Branch                                                         

  Sharjah       BR-003       Sharjah        CEBUAEAD    Noor Ahmed    +97165441111
  Branch                                                              
  ----------------------------------------------------------------------------------

## Task 3 - Add Bank Account records

1.  Open the **Bank Account** table.
2.  Select **Edit data**.
3.  Select **+ New record**.
4.  Use the lookup icon to select existing Customer and Branch records.

  -------------------------------------------------------------------------
  Account Number       Customer     Branch     Account Type      Status
  -------------------- ------------ ---------- ----------------- ----------
  UAE-000001           Ahmed Al     Dubai Mall Savings           Active
                       Mansoori     Branch                       

  UAE-000002           Ahmed Al     Dubai Mall Current           Active
                       Mansoori     Branch                       

  UAE-000003           Fatima Al    Abu Dhabi  Savings           Active
                       Suwaidi      Main                         
                                    Branch                       

  UAE-000004           Omar Al      Sharjah    Current           Inactive
                       Kaabi        Branch                       

  UAE-000005           Aisha Al     Dubai Mall Savings           Active
                       Mazrouei     Branch                       
  -------------------------------------------------------------------------

## Expected Outcome

You have successfully created: - Three custom Dataverse tables. - Two
1:N relationships using Lookup columns. - Sample banking data
representing a fictional UAE bank.
