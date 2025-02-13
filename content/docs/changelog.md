---
title: Changelog
weight: 99
next: /docs/changelog
prev: /docs
---

### v1.8.0
- Features:
* Added a search box to the backlog sidebar menu.  
* Added new role for specific company.  
* Added monthly report for specific company.  
* Warn users about portfolio end dates.  
* Added a clear button to forms with preset features.  
* Added a request timeout report.  

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
