# Glossary

This article will cover acronyms and terms used in this Repo

### Baseline
Capture baseline data is required in order to determine "All systems nominal" after an upgrade.   
Baselines can be captured for performance metrics, error rates, transactions/sec etc.   
The more baselines that can be compared against, the better. 

### Business owner

The business owner is a representative from the business that will be responsible for the upgrade from a business perspective:    
1. Making go/no go decisions related to the upgrade
2. [UAT](#user-acceptance-testing)
3. Downtime/Uptime requirements allowed

### Go/No-Go
The deadline for determining if the upgrade will proceed on the scheduled date/time. This is a business decision based on testing.

### Implementation Plan
This is a sequential, step-by-step plan that will be used to perform the upgrade in both the Staging/Pre-Prod and Production environments.   
Every step should be captured (with an asignee) to avoid any unexpected issues.    
***This includes testing and the rollback plan*** 

### Integration testing
Testing performed in a development environment that is more in-depth than a Smoke test. Exact criteria should be determined with the business.

### Recovery Point Objective
The amount of data the system can lose before a critical business impact, defined by the [Business Owner](#business-owner)    
Measured in seconds/minutes/hours, etc 

### Recovery Time Objective
The amount of time the system can be down before a critical business impact, defined by the [Business Owner](#business-owner)    
Measured in seconds/minutes/hours, etc

### Regression Testing
Testing performed by business and technical team in order to validate the system has not regressed in any way.    
From a business perspective: Everything functions as expected
From a technical perspective: No performance regressions

### Smoke Testing
Initial testing performed by the development team and testing teams to make sure the system comes "online"

### User Acceptance Testing
See [Regression Testing](#regression-testing)