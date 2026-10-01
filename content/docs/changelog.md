---
title: Changelog
weight: 99
next: /docs/changelog
prev: /docs
---

### v1.40.1 - 2026-10-01

#### **Changed**

* Daily: Updated the monthly PDF to use compound benchmark calculations.
* Daily: Aligned the Adjust Available Unit page with the Adjust NAV of Security page.
* Navigation & UI: Added fuzzy search with match highlighting to the sidebar menu.
* Frontend Architecture: Reworked the ResourceTransfer component and implemented it across the entire app.
* FX: Reworked the Trade Excel import.

#### **Fixed**

* Reports: Fixed monthly PDF page breaks, footer clipping, and blank page rendering.
* Dealing & Cash: Prevented commission adjustment values from being lost when refocusing pages and added form input validation before confirming submissions.
* Investment: Updated the order management NAV label to use the local currency.
* Resolved various minor bugs.


### v1.40.0 - 2026-09-07

#### **Added**

* Reports: Added support for MSTH Trial Balance (TB) format and template downloads.
* Daily: Added per-portfolio concatenated text files to GL export ZIP archives.
* Orders: Added partial approval support for orders triggering breached approval rules.

#### **Changed**

* System Management: Moved MKET export module under `sysmgmt.integration.mket`.
* Daily: Reworked end-of-day process to support many portfolio batches.


### v1.39.0 - 2026-09-01

#### **Added**

* Reports: Added a toggle for benchmark index rows in Daily Performance.
* Reports: Added edit permission gating for Daily Performance bulk toggle buttons.
* Reports: Added Excel export capability for Monthly Reports.
* Dealing: Added a new Transfer page.

#### **Fixed**

* Reports: Fixed monthly PDF page breaks and footer overlap.
* Resolved various minor bugs.


### v1.38.1 - 2026-08-13

#### **Changed**

* Dealing: Reordered MSTH commission adjustment columns and added Side and Price fields.
* Dealing: Updated the "Unconfirm Selected" button color to red.

#### **Fixed**

* FX Operations: Removed the unusable Delete action from Post Transaction.
* Daily Operations: Scoped Equity Price Adjustment edits to the clicked row.
* Reports: Returned `ErrExchangeRateNotFound` instead of triggering a panic in the PF1000 report.
* Reports: Used `THB_CURRENCY_ID` in monthly2 and statement reports.
* Masterfile: Fetched the bank list for all interest-rate modal actions.
* Masterfile: Cleared portfolios on FX mapping currency change.
* Enquiry: Ensured a unique `rowKey` for cash holding AI tree rows.
* Reports: Ensured a unique `rowKey` for cash AI report tree rows.
* Reports: Scoped the main cash account join to the security's own portfolio.
* Dealing: Cleared the commission adjustment sheet only after a successful update.
* Reports: Corrected MSTH monthly THB table rendering and YTD performance fallback.


### v1.38.0 - 2026-08-03

#### **Added**

* Reports: Added authorization gating, portfolio ACL scoping, and explicit permission gating for MKET Portfolio Summary exports.
* Reports: Added Excel download capability for Withholding Tax summary.
* Navigation: Added automatic disabling of Help links for pages the user cannot access.
* Enquiry: Added split layout options for History Transaction exports and included ISIN codes for Thai stocks in MSTH exports.
* FX Operations: Added Excel export support for FX Position data.
* Dealing: Added Excel export capability for selected Post Allocation transactions and enabled export name mapping for security codes in MSTH exports.

#### **Changed**

* Masterfile: Consolidated equity export ISIN columns into a single unified column.

#### **Fixed**

* Market Service: Enforced uppercase formatting for price codes in the service layer.
* Authentication & UI: Fixed role badge overflow in the sidebar menu and updated LDAP notifications to inform users that their passwords are managed externally.
* Enquiry: Fixed counterparty selection for DB FX broker codes and corrected DB investment security ID keying by exchange country.
* Compliance: Fixed field labels, placeholders, and log messages for `DeleteSecurityTarget`.
* Compliance: Redesigned the Performance Nav search form layout and made the rest of Compliance ▸ Performance fully responsive.


### v1.37.3 - 2026-07-08

#### **Changed**

- Revoked report permissions from Accounting according to the access matrix.
- Compliance: Added a VaR weight basis (NAV vs. invested).

#### **Fixed**

- Market: Corrected the price-code pending guard and fixed a loading notification that remained visible.
- Masterfile: Allowed updates to the issuer IsCompany type.
- Reports & Masterfile: Kept error notifications visible after final cleanup.


### v1.37.2 - 2026-06-29

#### **Changed**

- Dealing: Swapped the ISIN and Security Description column positions in the Allocation Excel export.

#### **Fixed**

- Resource: Derived the `fundPortfolioType` value `ASSET` in the Deutsche Bank export.
- Daily: Corrected the unit display and taxpayer mapping in Cash In/Out imports.
- Investment: Settled FX position cash legs on their settlement date.


### v1.37.1 - 2026-06-26

#### **Changed**

- Dealing: Prefilled the limit price in the multi-order XLSX export.
- Role: Renamed the `pf_admin` role to `pf_dealer`.
- Export Portfolio: Renamed the `liabilityAssets` column value from `ASSET` to `ASSETS`.

#### **Fixed**

- Dealing: Exported the order remark instead of the empty pre-transaction remark.
- Exceptions: Fixed multiple unhandled exception scenarios.


### v1.37.0 - 2026-06-22

#### **Added**

- Role: Added two new roles: Accounting and Dedicated Fund Manager.

#### **Fixed**

- Business Logic: Corrected various business logic issues.
- Exceptions: Fixed multiple unhandled exception scenarios.


### v1.36.3 - 2026-06-12

#### **Added**

- Startup: Added a splash screen on application startup.
- Design: Added a responsive off-canvas navigation drawer.
- FX Trade: Added four-eyes principle enforcement for FX trade confirm and unconfirm actions.

#### **Changed**

- Monthly Report: Renamed `Fixed Fee` to `Base Fee`.

#### **Fixed**

- Business Logic: Corrected various business logic issues.
- Exceptions: Fixed multiple unhandled exception scenarios.


### v1.36.1 - 2026-05-25

#### **Added**

- Compliance: Added portfolio and security target usage rules.
- Cash Security: Added capability to search by security code or portfolio code.

#### **Changed**

- Permissions: Adjusted the `RolePFAdmin` permission rule.
- Investment: Adjusted right transaction options to automatically add real units if end-of-day (EOD) processing was omitted.
- Export Portfolio: Renamed `liabilityAssets` column value from `ASSETS` to `ASSET`.

#### **Fixed**

- Security Type: Corrected CRUD operations for security types.
- Investment: Added missing active flag validation when importing orders.
- FX Trade: Fixed incorrect mapping for `amount from` and `amount to` values.


### v1.36.0 - 2026-04-29

#### **Added**

- FX Trade: Added pin functionality for FX trades.
- Lockscreen: Introduced a lockscreen feature.
- Unit Allocation: Refined unit allocation workflow.
- Market Portfolio Summary: Added a market portfolio summary feature.
- Compliance Statement: Added a compliance statement feature.

#### **Changed**
- FX Trade: Added pin functionality for FX trades.

#### **Fixed**

- Proving System: Corrected active flag handling across dependent components.
- Dealing & Allocation Size: Prevented the application from hanging during mode switching.
- Daily Equity: Improved input validation and error messaging in equity forms.


### v1.35.1 - 2026-04-17

#### **Added**

- Dealing: Added a Dealing Manager page to support multi-deal workflows.


#### **Changed**

- Global Config: Updated cross-role transaction mutation behavior for public configurations.
- Daily Post Transaction: Disabled editing for buy/sell transactions in the equity edit modal.


#### **Fixed**

- FX Post Transaction: Fixed the unintended display of unconfirmed FX transactions.
- Daily Performance: Fixed preview button functionality.
- Cash In/Out: Corrected display of Reference Rate and Effective Date.
- Portfolio Valuation PDF: Fixed layout issues.
- Portfolio Export TXT: Corrected column formatting.


### v1.35.0 - 2026-03-30

#### **Added**

- Monthly Report: Added logo support in the Port Valuation report for clients.
- FX Trade: Added support for importing FX trade files in the FX Trade function to automatically create bulk transactions.
- FX Trade: Added confirmation status = **No**.
- Portfolio: Added Excel export support.
- Portfolio: Added TXT export support for DB format.
- Order Placement: Added Excel export support.
- Reports: Updated High-Watermark per-unit value to show 4 decimal places.
- Unit Trust: Added unit allocation logic for unit trust.
- Cash In/Out: Added Accrued AR and Reverse Accrued AR transaction types.

#### **Changed**

- Daily: Updated NAV security and fee adjustment UI flow.
- Investment: Updated untradable unit simulation to use confirmed transactions from the same day.
- Compliance/Investment: Updated portfolio/security target preview.

#### **Fixed**

- Daily Performance: Fixed composite benchmark since-date calculation.
- Fixed multiple minor and edge-case issues.


### v1.34.0 - 2026-02-05

#### **Added**

- Cash In/Out: Added unit prefill for cash in/out transactions.
- Manage Rule: Added new selector sort logic and leading prefix search for securities when managing rule targets.
- Dealing: Added unit allocation support in dealing flows.
- Investment/Dealing: Added support for value-based investment and dealing flows.
- Investment: Added Cancel Order button for UT investments.

#### **Changed**

- Post Transactions: Updated the post-transaction error message to instruct users to check unit allocation.
- Investment: Set the export order default to **Standard** for investment exports.
- Reports: Updated high-watermark per-unit UI to show 4 decimal places.

#### **Fixed**

- Reports: Fixed incorrect maturity date displayed in reports.
- Activity Logs: Fixed an error when confirming/unconfirming in Post Allocation activity logs.
- Daily Performance (MSTH): Fixed an issue where Return and SD did not update when switching time frame modes.
- Approvals: Fixed an issue when clicking Disprove in the Pending state.


### v1.33.0 - 2026-01-14

#### **Added**

- Report: Added a row total for cash in the consolidated report.
- Investment: Added an option to skip accrued fee simulation.

#### **Changed**

- Cash Report: Highlighted non-zero disburseBuy values in the cash report.
- Monthly Report: Adjusted wording and decimal places.
- Monthly Report: Added line breaks in the portfolio description header.
- Role: Updated permissions to support view-only access.
- Investment: Set Investment Matrix column widths to fit staging data by default.

#### **Fixed**

- Investment: Fixed incorrect Simulation Details.
- Churning: Fixed an issue where the portfolio could be unselected in the Churning (1833) flow.
- Daily Performance: Fixed benchmark-since-inception settings to apply correctly (1825).
- Activity Logs: Refactored activity logs to improve correctness and stability.
- Investment: Fixed the incorrect AddToAll function behavior.
- UI: Fixed table text rendering on small screens.



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

- Dealing: Added Highest NAV allocation settings.
- Investment: Added a History dialog (accessible from the rightmost toolbar dropdown or by Cmd/Ctrl + clicking Undo/Redo) to view actions and perform multi-step undo/redo.
- Investment: Added a column-wide cancel button to remove all staged orders for a portfolio.

#### **Changed**

- Churning Page: Added error handling to display a message when there is no investment activity in the selected period.

- Investment: Accrued and regular fees before the investment date are now reserved from usable cash in the matrix.
- Investment: The Simulation Details dialog is now accessible by clicking the portfolio code in the matrix header.
- Investment: Undo/Redo buttons are now disabled when no further actions are available.

#### **Fixed**

- Composite Return Page: Added error handling to clearly inform users when the selected date is earlier than the portfolio creation date, preventing errors during search or export.

- Commission Adjustment Page: Fixed an issue where adding a column caused incorrect Excel parsing due to column shifting.

- Corporate Action: Fixed an issue where generated XE transactions did not convert all warrant units to stock.

- Dealing: Corrected the models and portfolios displayed in the allocation size table.


### v1.30.0 - 2025-11-18

#### **Added**

- Enquiry history transactions can now be exported as XLSX.

- FX trades now have a swap BUY/SELL currency button.

#### **Changed**

- Added **CostAmount** and **Price** columns to the commission adjustment Excel export.

- VaR/VaR backtesting now displays a usable-portfolio hint.

#### **Fixed**

- Improved decimal precision in Allocation Excel exports.

- The Process EOD page now shows the range of portfolios where holdings are not empty.


### v1.29.0 - 2025-11-06

#### Changed

* Market ▸ Exchange Market: Changed the Country field to a dropdown.
* Dealing ▸ Post Allocation; Daily ▸ Post/Close Transaction: Added a page size control.

#### Fixed

* VaR portfolio/investment colors were previously capped; they now support unlimited items, with colors cycling once the palette is exhausted.
* Broker Commission showed the wrong creator.
* Investments: Fixed an issue where an investment from the same issuer could be found before the main investment.
* Broker Commission field lacked validation for large numeric values.


### v1.28.0 - 2025-10-27

#### **Changed**

-   Investment Export: Updated ISIN, VAT, and the liability row fund code to meet new requirements.
-   Equity: Unified ISIN input into a single field.
-   Liquidity Report: Updated the report to meet new requirements.

### v1.27.0 - 2025-10-21

#### **Changed**

- Dealing: Commission Adjustment: Added an option to query unconfirmed transactions by **Trade Date** instead of **Create Date**. The earlier version incorrectly labeled the date range as “Trade Date,” which has now been corrected to “Create Date.”.

- Dealing: Commission Adjustment: The unconfirmed transaction listing table previously displayed **Trade Date**. A new **Create Date** column has been added as the rightmost column in this table.

- Dealing: Commission Adjustment: The unconfirmed transaction listing table now includes a **TX Type** column. Previously, it was impossible to distinguish different transaction types within the same portfolio and security except by ID. Additionally, the left columns are now sticky, allowing users to scroll horizontally and adjust commission numbers without losing track of the corresponding transactions.

#### **Fixed**

- Consolidated Report: Fixed market value calculations to use settlement amounts and correct FX conversions. Added safe division operations to prevent division-by-zero errors and corrected cash conversion to base currency using proper FX rates.


### v1.26.0 - 2025-10-14

#### **Added**

-   Added an allocation export for MSTH.

#### **Changed**

-   Investment Matrix: The cells in the Value Perspective view are now interactive, allowing investments to be made in terms of value as well as percentages or units.

#### **Fixed**

-   Prevented dealers from deleting and confirming `CASH` transactions on the Post Allocation page, which was unexpected behavior.
-   Fixed the issue with reporting the maximum number of days for VaR/VaR backtesting options.
-   Handled cases where an investment group or model has zero members.


### v1.25.0 - 2025-10-08

#### **Added**

-   Introduced equity export functionality.

#### **Changed**

-   Updated the investment module to allow investments without an account cash balance.

#### **Fixed**

-   Resolved an issue in EOD where split and increase transactions were incorrectly auto-generated or assigned the wrong currency.
-   Corrected formatting issues in the investment order export.


### v1.24.0 - 2025-10-02

#### **Added**

-   Compliance: Added a VaR price filler.

#### **Changed**

-   Added a new fee type: "Fund Administration Fee".
-   Gain/Loss Report: Added a percentage column.

#### **Fixed**

-   Monthly: Fixed upload failures when the portfolio code matched that of a deleted portfolio.
-   Log: Added missing activity logs for resource preset CRUD operations.
-   Daily Performance: Fixed an internal error when the portfolio had no returns since the start date.
-   Fixed an issue where a portfolio performance policy could not be removed in some cases.
-   Added the missing timestamp when creating a fee transaction.

### v1.23.0 - 2025-09-15

#### **Added**

-   Compliance: Reimplemented VaR and VaR Backtesting.
-   Added Exchange Country Concentration rules.
-   Added an assumption preset option in Stress Test.

#### **Changed**

-   Updated pop-up wording when generating XD.
-   Dealing: Unit cost precision is now fixed at 6 decimal places regardless of the price scale.
-   Daily Performance: Added the ability to select by portfolio.

#### **Fixed**

-   Dealing: Fixed an order listing failure when an approval rule exists.
-   Dealing: Added a dedicated error if the main cash account for creating a transaction is not found.
-   Fixed a compliance rule inversion issue.
-   Added the missing activity log when updating Corporate Actions.

### v1.22.0 - 2025-08-18

#### **Added**

-   Dealing > Commission Adjustment: Improved filters and exports.

#### **Changed**

-   Investment > Investment Model: Enhanced the Investment Model listing table.

#### **Fixed**

-   Fixed a regression affecting Equity, FX, and benchmark index imports.
-   Fixed a SQL parameter limit error in report monitoring when handling many items.


### v1.21.0 - 2025-08-15

#### **Added**

-   Post/Close order selection dialog when selecting mixed in/out transactions.
-   Order Placement Manager and new Allocation Dialogs.
-   Composite Return and Broker Volume Trade access permissions for Fund Manager and PF Admin.

#### **Changed**

-   Performance Group & Portfolio Benchmark Index: Improved the preview and edit modal.
-   Export Investment Orders can now export using the Default and Standard types.
-   Redesigned the report instruction page flow to make it clearer.

#### **Fixed**

-   Added the missing Report Instruction Signer setup in App Config.
-   Corrected behavior on the report instruction page.
-   Fixed an incorrect Excel floating-point warning when uploading on FX, Equity, and Benchmark Index pages.


### v1.20.1 - 2025-08-12

#### **Fixed**
- Hid the column when selecting the PF1000 report.
- Fixed an issue preventing PF1000 report mapping creation in some cases due to an incorrect unique SQL constraint.
- Added the missing FX security type filter in the BOT report.
- Performance: Removed excess data when there were no skip days and corrected the 'since' date.

### v1.20.0 - 2025-07-25

#### **Added**

-   Import functionality for benchmark index return.
-   Support for selling simulations in investment scenarios where there are 0 units to scale.

#### **Changed**

-   Improved warning messages during Equity price import.

#### **Fixed**

-   PF1000 adjusted value now correctly resets after changing the date.
-   Fixed an issue preventing deletion of split and increase transactions in post allocation.
-   Corrected bugs in fund performance: editing time frames and monthly remark text now work as expected.

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
  - Market: Added price source selection when importing equity and FX prices.
  - Compliance: The Stress Test Excel export now uses formulas to calculate Cost Per Unit and % NAV.
  - Performance: Added standard deviation to daily performance and monthly reports.
  - Monthly: Added options to toggle the display of High-Water Mark per Unit, NAV Performance, and Fund Financial Report (Revenue, Expense).

- Fixes
  - Corrected EOD error handling when the user forgets to set the main cash account.

### v1.17.0
- Features
  - Report: Added support for the HWM value per unit.
  - Portfolio: Updated the fund export to match new requirements.
  - Compliance: Added a new left operand: "Tradable Units".
  - Compliance: Added a new left operand: "Equity Value (in Local Currency)".
  - Investment: The Lot Size display automatically changes to the override value when the user attempts to sell all units (Percentage Perspective: Set to 0%, Unit Perspective: Set to 0 units).
  - Dealing: The investment date is visible above the Trade Date input box. The input box displays a warning explaining the possible consequences if the user changes the date to differ from the Investment Date.
  - Investment: The Import Orders feature now dynamically determines the lot size of imported orders based on the input XLSX file (e.g., changing from 100 to 1 automatically if the cell contains odd-lot units). Added a result modal showing the details of your imports, including the lot size determined from your input.
  - Reworked application background workers.
  - Added a new HTML error page when previewing daily performance and monthly reports.

- Fixes
  - Investment / Compliance: Fixed an issue where rule evaluation used the previous Portfolio Model members in calculations immediately after the user edited the model.
  - Investment: Fixed the Country with Cash Concentration view to group currencies under the correct country when they are present in the Portfolio Model but absent from its portfolios.
  - Investment / Compliance: Fixed the "Aggregated unit sold/bought in a day" left operand to sum values for each portfolio.
  - Investment: Fixed an incorrect concentration calculation in investment simulation after selling.
  - Investment: Fixed an issue where the investment matrix sometimes failed to load required data, causing a frontend error.
  - FX: Fixed an incorrect base currency assignment when updating an FX transaction.
  - FX: Updated the underlying FX position blottering logic to support additional transaction types.
  - Daily: Fixed Cash IO transaction import validation failures when no fee code is present.
  - Enquiry: Corrected the investment commission export.
  - Handled an edge case where multiple workers tried to acquire portfolio tasks.
  - Improved slow EOD performance.
  - Added missing validations when creating or updating resources.
  - Fixed minor bugs.

### v1.16.0
- Features
  - Monthly Report: Removed the fund financial section.
  - Added the ability to export portfolio information (Fund) to the custodian.
  - Refined the consolidated report.
- Fixes
  - Corrected BIC_CODE and Narrative Line1 in the Investment export.

### v1.15.0
- Features
  - Added a consolidated report (POC).
  - Investment: When selling all units by entering 0% or 0 Units in Set mode, the Lot Size information at the bottom right of the pop-up shows that the lot size will automatically adjust to 1.
  - Dealing > Allocation: The Investment Date of the investment that created the allocation order is now visible above the Trade Date input field.
  - Dealing > Allocation: Changing the Trade Date displays a modal explaining the possible consequences for the investment simulation in the Investment module.

- Fixes
  - Corrected the Main Cash Account query filter in edge cases.
  - Handled null values for the FX input amount.
  - Investment: Corrected the lot size to 1 instead of 0 when selling all units (entering 0% or 0 Units in Set mode).
  - (Investment / Compliance) Fixed a bug where the "Aggregated Equity Units Bought/Sold in a Day Per Portfolio" rule left operand was aggregating system-wide instead of per portfolio.

### v1.14.0
- Features
  - Removed the sector number.
  - Added a closed portfolio toggle in Resource Portfolio.
  - Added compliance rule approval.
  - Added Sector/Country concentration.
  - Added Country with Cash concentration.
  - Changed the Company's country field to a dropdown.
  - Investment Matrix: The Concentration View is accessible from the button to the right of the Security column.
  - Investment Matrix: Issue severity dots can appear on the Concentration View button, indicating issues with cells that are only visible inside a Concentration View.
  - Investment Matrix: Units and Value perspective: Currency codes are displayed in each applicable cell.
  - Investment Matrix: Units and Value perspective: The "Local" checkbox appears to the right of the perspective selector. Checking it converts all cash and value cells to the portfolio's local currency. Each cell shows both the original and converted currency codes.
  - Investment Matrix: Issue listing table: Improved the Cause column with coloring based on the type of cause.
  - Compliance > Investment Issue > Issue listing table: Improved the Cause column with coloring based on the type of cause.

- Fixes
  - Reordered the Investment export columns.
  - Corrected the FX export filename.
  - Handled the error when no unpaid fee transactions are found.
  - Corrected rounding in Cash IO fee calculations.
  - Required a taxpayer when the tax is not equal to 0.
  - Refined the Investment UI (Table View & Issues).

### v1.13.2
- Fixes
  - Fixed an issue where the "Success Notification" in Monthly did not close automatically.
  - Fixed missing paper settings in Monthly when the database is empty.
  - Added a missing role permission.
  - Fixed Investment and FX exports.

### v1.13.1
- Fixes
  - Fixed portfolio selection when creating a main cash account without a cash security.
  - Fixed an issue preventing the creation or update of the user command role.
  - Corrected the filename in the Cash In/Out export for DB.

### v1.13.0
- Features
  - Added new roles: Compliance and CMD.
  - Added log view permission for PF Operation and PF Admin.
  - Added a Cash Transaction Type filter on the History Transactions page.
  - Fulfilled export requirements for Cash In/Out DB.

- Fixes
  - The transaction table notification now clears selected rows that have been modified.
  - Sorted the list and the security currency pair list on the Main Cash Account preview details page.
  - Fixed an input size bug in the History Transactions portfolio field.
  - Fixed a deletion issue in Dealing Allocation.
  - Fixed issues with Redemption SIM and Left Cash Currency.

### v1.12.0
- Features
  - Improved event pub/sub publish retry logic.
  - Added stricter cash security checks when deleting.
  - Hid Fast Mode in Cash IO (malfunctioning and unused).
  - Nav-summary: Changed the table title language to English.
  - Prepared the database for upcoming compliance features (proving and rules).

- Fixes
  - Investment: Allowed inactive cash securities if their associated positions have zero cash.
  - Fixed an incorrect base currency in FX.
  - FX Trade: Fixed automatic calculation of the Forward Rate.
  - Fixed an overflow issue in the Portfolio Create form for Trustee, Registrar, Auditor, and dropdown inputs.
  - Investment: Fixed an issue where the issue list displayed “Inv. Date +X” before an item was clicked.
  - Hid Fast Mode in Cash IO (malfunctioning).
  - Fixed a width issue when selecting long items in Equity Issuer.

### v1.11.0
- Features:
  - Added a Liquidity stress test.
  - Reworked the module-wide investment model.

- Fixes:
  - Daily: Handled errors when split and increase transactions could not be generated.
  - Daily: Corrected the main cash account in Cash IO.
  - Resources: Disabled duplicate dates in the calendar.
  - Resources: Moved the model detail input for currency pairs.
  - Investment: Adjusted column widths.
  - Investment: Corrected placement progress when placing orders with multiple brokers.
  - Dealing: Hid Broker Group Target.
  - Report: Added support for previously unsupported cash transactions.
  - Report: Handled the error message when no portfolio is available in Daily Performance.

### v1.10.0
- Features:
  - Added a Deutsche Bank export.

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
  - Added a new role for a specific company.
  - Added a monthly report for a specific company.
  - Added warnings about portfolio end dates.
  - Added a clear button to forms with preset features.
  - Added a request timeout report.

- Fixes:
  - Resource: Fixed an issue preventing updates to resource preset names.
  - Resource: Validated interest rate condition limits for the "range-to" field.
  - System Management: Fixed an issue preventing admin user edits.
  - Tracing: Removed tracing for fetching FX prices in the production environment.
  - Compliance: Fixed incorrect pagination.
  - Navigation Summary Report: Fixed an edge case causing an infinite loop.
  - Equity Price: Removed duplication.
  - Notification: Sent a welcome ping notification to clients to prevent reconnection issues.
  - Dashboard: Hid the "expired password" warning when there is no latest update.

### v1.7.6
- Fixes:
  - App: Fixed an unhandled 500 error.
  - App: Fixed an issue where the logger did not log panics.
  - App: Hid unused sidebar modules.
  - Dashboard: Hid the expired password warning for AD users.
  - Resource: Fixed the interest rate condition preview.
  - Help: Corrected an incorrect link.
  - Benchmark: Fixed an issue where removing a benchmark index did not cascade to delete its benchmark index portfolios.
  - Compliance: Fixed an internal report error for portfolios with no data.
  - Cash IO: Added a check for bank account open/closed status.
  - User: Added a gray background for inactive users.
  - Invps: Corrected the error receiver.
  - Investment: Fixed an issue where the investment matrix did not show errors in the outer component.
  - System Management: Fixed numeric forms in the number section.

### v1.7.5

- Fixes:
  - Resolved duplicate error logs.
  - Removed line breaks from LDAP error messages.
  - Allowed SMTP configuration without a username and password.
  - Removed the price code search in Daily EQ Price Adjustment.
  - Handled duplicates in Daily Price Adjustment.
  - Improved TLS connections across all components.
  - Deprecated the `TLS_CERT` and `TLS_KEY` environment variables.
