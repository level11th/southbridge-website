---
title: Changelog
weight: 99
next: /docs/changelog
prev: /docs
---

### v1.16.0
- Features
  - monthly report: remove fund financial section
  - be able to export portfolio information (Fund) to custodian
  - refine consolidate report
- Fixes
  - export Investment BIC_CODE,  Narrative Line1

### v1.15.0
- Features
  - Consolidated report (POC)
  - Investment: When attempting to sell all units by using Set mode and typed in 0% or 0 Units, Lot Size information on the bottom right of the popup shows that automatic lot size adjustment to 1 is going to occur.
  - Dealing > Allocation : Investment Date of the Investment that creates the order of that allocation is now visible above Trade Date input form.
  - Dealing > Allocation : Changing Trade Date will display a modal explaining possible consequences to the investment simulation in the Investment module.

- Fixes
  - Corrected the Main Cash Account query filter in edge cases.
  - Handle null value of FX input amount.
  - Investment : Correctly use lot size of 1 instead of 0 when attempting to sell every units (Set mode, inputting 0 % / 0 Units)
  - (Investment / Compliance) a bug where "Aggregated Equity Units Bought/Sold in a Day Per Portfolio" rule left operand was aggregating system-wide instead of per portfolio.

### v1.14.0
- Features
  - Removed sector number
  - Closed portfolio toggle in resource portfolio
  - Compliance rule approval
  - Sector/Country concentration
  - Country with Cash concentration
  - Change Company's country to drop down
  - Investment Matrix : Concentration View accessible from button to the right of Security column.
  - Investment Matrix : Issue severity dots can appear on Concentration View button, signifying issues related to one of the cells that is only visible inside a Concentration View.
  - Investment Matrix : Units and Value perspective : Currency code displayed on each applicable cells.
  - Investment Matrix : Units and Value perspective : "Local" checkbox appears to the right of perspective selector. Checking it converts all cash and value cells to portfolio's local currency. The currency code in each cell changes to show what was the currency and the new converted currency.
  - Investment Matrix : Issue listing table : Improved Cause column with coloring based on the type of cause.
  - Compliance > Investment Issue > Issue listing table : Improved Cause column with coloring based on the type of cause.

- Fixes
  - Reorder exporting investment columns
  - Exporting FX filename
  - Handle no unpaid fee tx error
  - Rounding in cash io fee calculation
  - Tax payer requirement when tax not equal to 0
  - UI investment refinement (Table view & Issues)

### v1.13.2
- Fixes
  - "Success Notification" in monthly not automatically close.
  - Monthly no paper setting when empty db
  - Missing role permission.
  - Export Investment and FX

### v1.13.1
- Fixes
  - Create main cash account select portfolio set when no cash security is present
  - Unable to create or update user command role
  - Export Cash In/Out for DB – filename issue

### v1.13.0
- Features
  - Added new roles: Compliance and CMD  
  - Added log view permission for PF Operation and PF Admin  
  - Added Cash Transaction Type filter on the History Transactions page  
  - Fulfilled export requirements for Cash In/Out DB  

- Fixes
  - Transaction table notification now clears mutated selected rows  
  - Sorted list and security currency pair list in the Main Cash Account preview details page  
  - Input size bug in History Transactions portfolio field  
  - Deletion issue in Dealing Allocation  
  - Redemption SIM and Left Cash Currency issues  

### v1.12.0
- Features
  - Improved event pub/sub publish retry logic  
  - Stricter cash security checks when deleting  
  - Hide Fast Mode in Cash IO (malfunctioning and unused)  
  - Nav-summary: changed table title language to English  
  - Prepared database for upcoming compliance features (proving and rules)

- Fixes
  - Investment: allow non-active cash securities if associated positions have zero cash  
  - Fixed incorrect base currency in FX  
  - FX trade: auto-calculation of Forward Rate  
  - Fixed overflow issue in Portfolio Create form for Trustee, Registrar, Auditor, and dropdown inputs  
  - Investment: issue list displayed “Inv. Date +X” before item was clicked  
  - Hide Fast Mode in Cash IO (malfunctioning)  
  - Fixed width issue when selecting long items in Equity Issuer  

### v1.11.0
- Features:
  - Added Liquidity stress test
  - Rework module-wide investment model

- Fixes:
  - daily: handle missing split & inc generate error
  - daily: wrong main cash in cashIO
  - resources: disable date duplicate in calendar
  - resources: currency pair move model detail input
  - investment: column width tuning
  - investment: incorrect placed progress when placed on multiple brokers
  - dealing: hide Broker Group Target
  - report: implement unsupport tx in cash
  - report: handle daily performance no portfolio error message

### v1.10.0
- Features:
  - Added deutsche bank export

### v1.9.0
- Features:
  - Added a confirmation modal for WHTax.  
  - Added a "Select All" button for the Daily Performance report.  
  - Displayed the ID on the preview for each configurable resource in the global configuration.  
  - Automatically filtered out unavailable bank accounts when creating or editing cash security.  

- Fixes:
  - Investment, compliance: The aggregate order rule should not check for the same portfolio.  
  - Daily: Transactions of type "convert unit" should not be counted in the corporate actions list.  
  - Corporate Actions: Fixed a data race issue in the corporate action form state.  
  - Corporate Actions: Fixed an issue where XD stock and cash types could not be created on the same date.  
  - Fee Code: A warning is now displayed when updating the "Fee Code Period From" and "Period To" fields.  
  - User Management: Disabled autocomplete when creating a user.  
  - Employee: Added a missing "Confirm Password" input box when changing passwords.  
  - Security Type: Creating a security type now disallows a nullable currency and removes the currency requirement.  
  - Reports: Fixed an issue where performance groups without a benchmark index caused a user error.  
  - Investment: The zero-out lot size is now fixed at 1 instead of 0.  
  - Resources: Fixed an issue preventing the update of currency pairs.  
  - Daily: Fixed an issue preventing FX price adjustments.  
  - Daily: The "EQ Price Adj" feature now only shows mapped price sources with securities.  


### v1.8.0
- Features:
  - Added a search box to the backlog sidebar menu.  
  - Added new role for specific company.  
  - Added monthly report for specific company.  
  - Warn users about portfolio end dates.  
  - Added a clear button to forms with preset features.  
  - Added a request timeout report.  

- Fixes:
  - Resource: Fixed issue preventing updates to resource preset names.  
  - Resource: Validated interest rate condition limits for the "range-to" field.  
  - System Management: Fixed issue preventing admin user edits.  
  - Tracing: Removed tracing for fetching FX prices in the production environment.  
  - Compliance: Fixed incorrect pagination.  
  - Navigation Summary Report: Fixed an edge case causing an infinite loop.  
  - Equity Price: Removed duplication.  
  - Notification: Send a welcome ping notification to clients to prevent reconnection issues.  
  - Dashboard: Do not show "expired password" warning if there is no latest update.  

### v1.7.6
- Fixes:
  - app: fix unhandle 500 error
  - app: logger not log when panic.
  - app: hide unuse side module
  - dashboard: don't show expire password for AD user
  - resource: int rate cond preview
  - help: fix wrong link
  - bechmark: remove benchmark index not cascade delete bechmark index portfolio
  - compliance: internal error on report on ports with no data
  - cashio: check bank account open / close
  - user: gray bg on inactive user
  - invps: fix wrong error receiver
  - investment: fix investment matrix not showing errors on outer component
  - sysmgmt: fix numerical forms in number section

### v1.7.5

- Fixes: 
  - Resolve duplicate error logs  
  - Remove line breaks from LDAP error messages  
  - Allow SMTP configuration without a username and password  
  - Remove search price code in Daily EQ Price Adjustment
  - Handle duplicates in Daily Price Adjustment
  - Improve TLS connection across all components
  - Deprecated TLS_CERT, TLS_KEY enviroments
