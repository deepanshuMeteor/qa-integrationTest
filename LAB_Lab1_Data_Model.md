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

------------------------------------------------------------------------

# Exercise 1 - Create the Customer table

## Task 1 - Create a Dataverse table

1.  Navigate to <https://make.powerapps.com> and sign in with the credentials provided (*Available from the Resources tab of your lab environment. Use* **Administrative Username** *and* **Administrative Password**).
1.  Ensure you are in the correct environment (**Dev One**) by checking the Environment picker in the upper-right corner of the screen.
1.  In the left navigation pane, select **Tables**.
1.  Select **+ New table** drop down, and from the menu that appears choose **Table (advanced properties)**
1.  In the table **Properties** panel, set the **Display name** to **Customer**. (Note: The plural name will auto-populate.)
1.  Select the **Save** button to create your new table.

## Task 2 - Add the required column 

1.  Ensure the **Customer** table is open.
2.  Select **Columns**.
3.  Select **+ New column**.
4.  Configure your new column as follows:
    - **Display name:** Phone Number
    - **Data Type:** Single line of text
5.  Expand **Advanced options** and ensure the **Maximum character count** is **2000**.
6.  Select the **Save** button.
7.  Configure your new column as follows:
    - **Display name:** City
    - **Data Type:** Single line of text

5.  Select **Save**.

## Task 3 - Add the remaining Customer columns

Repeat the previous process.

| **Column Display Name** | **Data Type**          | **Additional Settings**                                        |
|-------------------------|------------------------|----------------------------------------------------------------|
| Email                   | Text - Email           | Max length: 2000                                               |
| Gender                  | Choices                | Labels: Male, Female, Other                                    |
| KYC Status              | Choices                | Labels: Pending, Verified, Cancelled                           |




# Exercise 2 - Create the Branch table

## Task 1 - Create a Dataverse table

1.  In the left navigation pane, select **Tables**.
1.  Select **+ New table** drop down, and from the menu that appears choose **Table (advanced properties)**
1.  In the table **Properties** panel, set the **Display name** to **Branch**. (Note: The plural name will auto-populate.)
1.  Select the **Primary Column** Name, and set the **Display name** to **Branch Name**
1.  Select the **Save** button to create your new table.

## Task 2 - Add the required columns

1.  Ensure the **Branch** table is open.
2.  Select **Columns**.
3.  Select **+ New column**.
4.  Configure your new column as follows:
    - **Display name:** Phone
    - **Data Type:** Single line of text
5.  Expand **Advanced options** and ensure the **Maximum character count** is **10**.
6.  Select the **Save** button.
7.  Configure your new column as follows:
    - **Display name:** City
    - **Data Type:** Single line of text

5.  Select **Save**.

## Task 3 - Add the remaining Customer columns

Repeat the previous process.

| **Column Display Name** | **Data Type**          | **Additional Settings**                                        |
|-------------------------|------------------------|----------------------------------------------------------------|
| Branch Code             | Autonumber             | Prefix : BR-                                                   |
| Manager Name            | Single line of text    |                                                                |


# Exercise 3 - Create the Bank Account table

## Task 1 - Create the table

1.  In the left navigation pane, select **Tables**.
1.  Select **+ New table** drop down, and from the menu that appears choose **Table (advanced properties)**
1.  In the table **Properties** panel, set the **Display name** to **Bank Account**. (Note: The plural name will auto-populate.)
1.  Select the **Primary Column** Name, and set the **Display name** to **Account Number**
1.  Select the **Save** button to create your new table.

## Task 2 - Add the required columns

1.  Ensure the **Branch** table is open.
2.  Select **Columns**.
3.  Select **+ New column**.
4.  Configure your new column as follows:
    - **Display name:** Account Type
    - **Data Type:** Choices
    - **Labels:** Savings, Current
5.  Expand **Advanced options** and ensure the **Maximum character count** is **10**.
6.  Select the **Save** button.
7.  Configure your new column as follows:
    - **Display name:** Customer
    - **Data Type:** Lookup
    - **Related Table:** Customer
8.  Select **Save**.
9.  Configure your new column as follows:
    - **Display name:** Branch
    - **Data Type:** Lookup
    - **Related Table:** Branch

10.  Select **Save**.


No manual relationship creation is required because Dataverse
automatically creates relationships for Lookup columns.

------------------------------------------------------------------------

# Exercise 5 - Add Sample Data

## Task 1 - Add Customer records

1.  Open the **Customer** table.
2.  Select **Edit data**.
3.  Select **+ New record**.
4.  Enter the following records and select **Save** after each one.

  --------------------------------------------------------------------------------------------------------------------
  | **Name**            | **Email**                  | **Phone Number**  | **Gender** | **City**  | **KYC Status**   |
  |---------------------|----------------------------|-------------------|------------|-----------|------------------|
  |Ahmed Al Mansoori    |ahmed.almansoori@example.ae |  +971501112233    |  Male       | Dubai         | Verified    |
  |Fatima Al Suwaidi    |fatima.suwaidi@example.ae   |  +971551234567    |  Female     | Abu Dhabi     | Verified    |
  |Omar Al Kaabi        |omar.kaabi@example.ae       |  +971507654321    |  Male       | Sharjah       | Pending     |
  |Aisha Al Mazrouei    |aisha.mazrouei@example.ae   |  +971521987654    |  Female     | Dubai         | Verified    |
  |Sarah Thomas         |sarah.thomas@example.ae     |  +971509876543    |  Female     | Ajman         | Rejected    |
  --------------------------------------------------------------------------------------------------------------------

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
