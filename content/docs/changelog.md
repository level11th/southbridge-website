---
title: Changelog
weight: 99
next: /docs/changelog
prev: /docs
---

### v1.32.0 - 2025-12-29

#### **Added**

- Churning: Added the ability to export raw transaction data.
- Market: Added an "Equity Price Today" checker dialog.
- Other: Added functionality to map account codes for duplicate portfolios.

#### **Changed**

- Churning: Updated the calculation formula.
- Churning: Added error handling to display a message when there is no investment activity in the selected period.

- Daily Performance: Removed the "Submit" setting button in the daily performance workflow.

- Investment: Updated the Investment Matrix to include "Other Assets" positions and refined the Simulation Details dialog.

- Monitoring Report: Configured the report to return an empty state instead of an error when no breaches are found.

- System: Rewrote the notification system to improve resilience and include detailed logging for future debugging.
- System: Updated role permissions.

#### **Fixed**

- Allocation: Fixed an export issue where empty (nil) task dates caused failures.

- Commission Adjustment: Fixed the Excel reader to correctly handle import data.

- Composite: Added validation to trigger an error when the selected date range precedes the portfolio's creation date.

- Investment: Fixed numerical calculation errors in the Simulation Details modal.


### v1.31.0 - 2025-12-08

#### **Added**

- Dealing: Added Highest NAV allocation settings
- Investment: Added a History dialog (accessible from the rightmost toolbar dropdown or by Cmd/Ctrl + clicking Undo/Redo) to view actions and perform multi-step undo/redo.
- Investment: Added a column-wide cancel button to remove all staged orders for a portfolio.

#### **Changed**

- Churning Page: Added error handling to display a message when there is no investment activity in the selected period.

- Investment: Accrued and regular fees before the investment date are now reserved from usable cash in the matrix.
- Investment: Simulation Details dialog is now accessible by clicking the portfolio code in the matrix header.
- Investment: Undo/Redo buttons are now disabled when no further actions are available.

#### **Fixed**

- Composite Return Page: Added error handling to clearly inform users when the selected date is earlier than the portfolio creation date, preventing errors during search or export.

- Commission Adjustment Page: Fixed an issue where adding a column caused incorrect Excel parsing due to column shifting.

- Corporate Action: Fixed an issue where generated XE transactions did not convert all warrant units to stock.

- Dealing: allocation size table wrong models / portfolios


### v1.30.0 - 2025-11-18

#### **Added**

- Enquiry history transactions can now be exported as XLSX.

- FX trades now have a swap BUY/SELL currency button.

#### **Changed**

- Added **CostAmount** and **Price** columns to the commission adjustment Excel export.

- VaR/VaR backtesting now displays a usable-portfolio hint.

#### **Fixed**

- Improved decimal precision in Allocation Excel exports.

- The process EOD page now shows the range of portfolios where holdings are not empty.


### v1.29.0 - 2025-11-06

#### Changed

* Market ▸ Exchange Market: changed the Country field to a dropdown.
* Dealing ▸ Post Allocation; Daily ▸ Post/Close Transaction: added page size control.

#### Fixed

* VaR portfolio/investment colors were previously capped; they now support unlimited items, with colors cycling once the palette is exhausted.
* Broker Commission showed the wrong creator.
* Investments: fix same issuer investment able to be found before main one.
* Broker Commission field lacked validation for large numeric values.


### v1.28.0 - 2025-10-27

#### **Changed**

-   Investment export: updated ISIN, VAT, and liability row fund code to meet new requirements
-   Equity page: unified ISIN input into a single field
-   Liquidity report: updated to meet new requirement

### v1.27.0 - 2025-10-21

#### **Changed**

- Dealing: Commission Adjustment: Added an option to query unconfirmed transactions by **Trade Date** instead of previously using **Create Date**. The earlier version incorrectly labeled the date range as “Trade Date,” which has now been corrected to “Create Date.”

- Dealing: Commission Adjustment: The unconfirmed transaction listing table previously displayed **Trade Date**. A new **Create Date** column has been added as the rightmost column in this table.

- Dealing: Commission Adjustment: The unconfirmed transaction listing table now includes a **TX Type** column. Previously, it was impossible to distinguish different transaction types within the same portfolio and security except by ID. Additionally, the left columns are now sticky, allowing users to scroll horizontally and adjust commission numbers without losing track of the corresponding transactions.

#### **Fixed**

- Consolidated Report: Fixed market value calculations to use settlement amounts and correct FX conversions. Added safe division operations to prevent division-by-zero errors and corrected cash conversion to base currency using proper FX rates.


### v1.26.0 - 2025-10-14

#### **Added**

-   Allocation export for MSTH.

#### **Changed**

-   Investment Matrix: The cells in the Value Perspective view are now interactable, allowing investments to be made in terms of value instead of only percentage or units as previously available.

#### **Fixed**

-   Prevented dealers from deleting and confirming `CASH` transactions on the Post Allocation page, which was unexpected behavior.
-   Fixed the issue with reporting the maximum number of days for VaR/VaR backtesting options.
-   Handled cases where an investment group or model has zero members.


### v1.25.0 - 2025-10-08

#### **Added**

-   Introduced equity export functionality.

#### **Changed**

-   Updated investment module to allow investments without an account cash balance.

#### **Fixed**

-   Resolved an issue in EOD where split and increase transactions were incorrectly auto-generated or assigned the wrong currency.
-   Corrected formatting issues in the investment order export.


### v1.24.0 - 2025-10-02

#### **Added**

-   Compliance: VaR price filler

#### **Changed**

-   New fee type: "Fund Administration Fee"
-   Gain/Loss report: added percentage column

#### **Fixed**

-   Monthly: failed to upload when the portfolio code was the same as a deleted one
-   Log: missing activity log when performing resource preset CRUD
-   Daily Performance: internal error when the portfolio had no returns since the start date
-   Portfolio performance policy could not be removed in some cases
-   Missing timestamp when creating fee transaction

### v1.23.0 - 2025-09-15

#### **Added**

-   Compliance: reimplemented VaR and VaR Backtesting.
-   Exchange Country Concentration rules.
-   Assumption preset option in Stress Test.

#### **Changed**

-   Pop-up wording when generating XD.
-   Dealing: unit cost precision is now fixed to 6 regardless of price scale.
-   Daily Performance: now possible to select by portfolios.

#### **Fixed**

-   Dealing: fixed order listing failure when approval rule exists.
-   Dealing: added dedicated error if main cash account for creating TX is not found.
-   Compliance rule inversion issue.
-   Missing activity log when updating Corporate Actions.

### v1.22.0 - 2025-08-18

#### **Added**

-   Dealing > Commission Adjustment: Improved Filters and Export

#### **Changed**

-   Investment > Investment Model: Enhanced Investment Model Listing Table

#### **Fixed**

-   Regression issue with Equity, FX, and benchmark index import malfunction
-   SQL parameter limit error in report monitoring when handling many items


### v1.21.0 - 2025-08-15

#### **Added**

-   Post/Close order selection dialog when selecting mixed in/out transactions.
-   Order Placement Manager and new Allocation Dialogs.
-   Composite Return and Broker Volume Trade access permissions for Fund Manager and PF Admin.

#### **Changed**

-   Performance Group & Portfolio Benchmark Index: improved preview and edit modal.
-   Export Investment Orders can now export as type Default and Standard.
-   Redesigned the report instruction page flow to make it clearer.

#### **Fixed**

-   Missing Report Instruction Signer setup in App Config.
-   Incorrect behavior in report instruction page.
-   Incorrect Excel floating-point warning when uploading on FX, Equity, and Benchmark Index pages.


### v1.20.1 - 2025-08-12

#### **Fixed**
- Hide column when selecting PF1000 report.
- Unable to create PF1000 report mapping in some cases (incorrect unique SQL constraint).
- Missing FX security type filter in BOT report.
- Performance: removed excess data when no skip days; incorrect 'since' date.

### v1.20.0 - 2025-07-25

#### **Added**

-   Import functionality for benchmark index return.
-   Support for selling simulations in investment scenarios where there are 0 units to scale.

#### **Changed**

-   Improved warning messages during Equity price import.

#### **Fixed**

-   PF1000 adjusted value now correctly resets after changing the date.
-   Fixed issue preventing deletion of split and increase transactions in post allocation.
-   Corrected bugs in fund performance: editing time frames and monthly remark text now works as expected.

### v1.19.0 - 2025-07-09
#### **Changed**

-   Improved warning messages for Equity and FX price imports regarding changes and excessive decimal places.
-   Enhanced performance of the SD (Standard Deviation) compliance feature.
    -   Performance and SD (Standard Deviation) are now expressed as percentages.
    -   BM (Benchmark) Fixed Rate is now calculated directly from the benchmark index rate (rate \* years), with SD set to null.
    -   Optimized the display of daily performance in PDF and Excel exports.
        -   Removed "BM since" from the first row.
        -   Added "BM since" for both performance and SD in each portfolio.
        -   Applied color-coding to the BM SD.

#### **Added**

-   Checks for securities missing a sector or for sector types without a designated currency.
-   "Make annualized" checkbox to the SD compliance feature.
-   "Skip weekend and holidays" checkbox to the SD compliance feature.
-   A preview button to the SD compliance feature.

#### **Fixed**

-   Corrected a mistake in the left operand explanation for a rule.
-   Addressed an issue where the transaction deletion timestamp was missing.
-   Replaced an internal error with a user-facing exception when EOD failed.
-   Fixed an incorrect query for the benchmark value.
-   Resolved a missing timeout duration for the "clear selected rows" notification.
-   Corrected an issue where unposting a transaction did not trigger a warning about a "security sold cost".
-   Fixed a bug that prevented the selection of a feebase.
-   Ensured a human-readable log is generated when requesting the creation of a corporate action.

### v1.18.0
- Features
  - Market: be able to select price source when import eq, fx price
  - Compliance: Stress test excel will use formula to calculate Cost Per unit, % NAV
  - Performance: show standard deviation in daily performance report and monthly report
  - Monthly: add option to toggle how High-Water Mark per unit, NAV Performance, Fund Financial Report (Revenue, Expense)

- Fixes
  - EOD process don't error when user forget to set main cash account

### v1.17.0
- Features
  - Report: Support for HWM value per unit
  - Portfolio: Updated export fund to match new requirements
  - Compliance : New left operand "Tradable Units"
  - Compliance : New left operand "Equity Value (in Local Currency)"
  - Investment : Lot Size display automatically changes to overriding value when user attempt to sell all units (Percentage Perspective: Set to 0%, Unit Perspective: Set to 0 units)
  - Dealing : Investment date is visible above Trade Date input box. Trade Date input box displays warning if user changes it from the Investment Date with explanation of the possible consequences.
  - Investment : Import Orders feature now dynamically determine the lot size of imported orders based on input XLSX. (e.g. Change from 100 to 1 automatically if the cell contains odd-lot units.) Added a result modal showing the details of your imports, including the lot size that was decided from your input.
  - Reworked application background workers
  - New HTML error page when previewing daily performance and monthly reports

- Fixes
  - Investment / Compliance : If user just edited Portfolio Model, rule evaluation was mistakenly using the pre-edit Portfolio Model members in the calculation.
  - Investment : Fix Country with Cash Concentration view not grouping currency found in the Portfolio Model but not in any Portfolio in the correct country.
  - Investment / Compliance : Fix "Aggregated unit sold/bought in a day" left operand that was not summing up the check per each portfolio.
  - Investment : Fix wrong concentration calculation in investment simulation after selling.
  - Investment : Fix investment matrix data gathering on load sometimes missing needed data, causing front-end error.
  - FX: Set wrong base currency when updating FX transaction
  - FX: How FX pos blottering (position) works underlying to support more new transaction types
  - Daily: Import Cash IO TX validation failed when there is no fee code
  - Enquiry: Export investment commission
  - Edge case where multiple workers try to acquire portfolio tasks
  - Slow EOD performance
  - Minor missing validations when creating/updating resources
  - Minor bugs

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
