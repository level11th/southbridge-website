---
title: Changelog
weight: 99
next: /docs/changelog
prev: /docs
---

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
