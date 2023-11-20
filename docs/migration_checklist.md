# MySQL 5.7 migration to 8.0 checklist  
This document will help make sure that proper conversations, planning, and testing have happened in order to ensure a successful migration.    

## Initial requirements, impact assessment and planning
Properly planning a major RDBMS upgrade requires an understanding of both the technical and business requirements.   
There are potential blockers and critical issues that can crop up, so identifying them early is key to properly executing an upgrade on time.    

### Business
  - [ ] Define the [Business owner](glossary.md#business-owner) of the migration
    - [ ] Define success criteria
  - [ ] Identify [UAT](glossary.md#user-acceptance-testing) resources
  - [ ] Define a roadmap for migration milestones 
  - [ ] Validate [RTO](glossary.md#recovery-time-objective)/[RPO](glossary.md#recovery-point-objective)/SLA/SLO requirements for application
    - [ ] Define fail-back criteria/decision point
  - [ ] Cost planning for additional resources during migration

### Technical
  - [ ] Define the **"technical owner"** of the migration
  - [ ] Identify development and testing resources
  - [ ] Determine In-Place or parallel upgrade approach
    - [ ] In-place
    - [ ] If parallel, determine if async replication
  - [ ] [Review changes in MySQL 8.0](https://dev.mysql.com/doc/refman/8.0/en/upgrading-from-previous-series.html)
    - [ ] [Review blog post](https://dev.mysql.com/blog-archive/upgrading-to-mysql-8-0-here-is-what-you-need-to-know/) 
    - [ ] Run the [Upgrade Checker Utility](https://dev.mysql.com/blog-archive/mysql-shell-8-0-4-introducing-upgrade-checker-utility/)
      - ***RDS***: This can be done manually, or you can clone and upgrade in-place which will automatically run the check
      - ***GCP***: Must run the upgrade checker manually
    - [ ] Document breaking changes and other identified deprecations/etc 
    - [ ] Document features that may be useful in the future (backlog it!)
  - [ ] Identify new service features in the new version that could be useful (backlog it!)
  - [ ] Identify target Infrastructure configuration (instance class)
  - [ ] Estimate Development and testing efforts

## Development and Testing    
There are different phases of testing performed. Each phase has a specific goal. 
Often, the phases are aligned with specific testing environments. (EG: Development, staging, pre-prod, etc...)   
Testing can uncover bugs, which will require the development team to address.    

### Development Environment: Smoke test
The development environments should be used to initially "kick the tires" after an upgrade has been performed.   
This test should send at least one unit of work through the entire system.     
This is not an extensive test, the goal here is to expose any obvious breaking-changes.
  - [ ] Clone Development environment and perform MySQL upgrade
  - [ ] Perform [Smoke test](glossary.md#smoke-test)
    - [ ] Document and remediate any issues
  
### Development Environment: Integration test
Integration testing is typically done in the development environment and can be manual or automated.    
The level of testing here is more than a Smoke test.
  - [ ] Perform [Integration test](glossary.md#integration-testing)
    - [ ] Document and remediate any issues
  - [ ] Repeat Integration testing for each deployment

## Infrastructure testing
Infrastructure testing is the process of perfecting the upgrade process that will be used in Production.    
This can be done in parallel with other efforts.
  - [ ] Create an [Implementation Plan](glossary.md#implementation-plan) required to implement the upgrade approach [determined previously](#technical)
    - EG: Task execution, Backups, Deployments, Maintenance windows, communications, *any task that needs to be done* 
  - [ ] Execute the upgrade
  - [ ] Document the process

## Regression/UAT testing
[Regression testing](glossary.md#regression-testing) is one or more full tests of the system, ensuring no regressions.   
Typically, this testing is performed in a pre-prod or staging environment. 

### Regression testing (Establishing a baseline)
A successful upgrade hinges on the ability to capture [baseline](glossary.md#baseline) data. 
  - [ ] Identify method to capture baseline data
    - For Query performance, [see this article](https://engineering.doit.com/how-to-capture-sql-statements-with-aws-rds-mysql-da12d95c5c4f)
  - [ ] Capture data in existing environment to establish a [baseline](glossary.md#baseline)

### Regression testing (Business)
This testing is performed from a business perspective, aimed at validating the system from that lens.
  - [ ] Create a testing plan
  - [ ] Coordinate regression testing with the technical team
  - [ ] Execute regression tests
  - [ ] Document results

### Regression testing (Technical)
Ensures the system will operate at the same (or better) from a performance perspective.    
Performance regressions are one of the most common impacts of an upgrade. 
  - [ ] Perform database upgrade 
    - *This should be the steps identified in [Implementation Plan](glossary.md#implementation-plan)
    - [ ] Capture timings
    - [ ] Update Implementation plan with lessons learned
  - [ ] Coordinate regression testing with UAT
  - [ ] Capture data
  - [ ] Compare with the baseline
  - [ ] Document results

### ***Repeat regression testing as needed!!***
If critical issues were discovered during regression testing, then the testing will need to be done again after the issues have been resolved.

## Production/Go-Live!
As the name suggests, this is the Production cutover plan. This relies on successful regression testing and an     
implementation window agreed upon with the business. 

### Go/No-Go
Often, there will be outstanding issues related to the upgrade. This does not mean the upgrade can't happen,    
but there should be a point where the Go/No-go decision is made. 
  - [ ] Review current testing status, outstanding issues, performance regressions
  - [ ] Collaborate with the business to determine [Go/No-Go](glossary.md#gono-go)
  - [ ] Validate Maintenance window and Rollback criteria with the business

### Go-Live
The implementation should be well rehearsed at this point. Timings should be known.   
The only thing that is left is to execute the upgrade.
  - [ ] Execute the [Implementation Plan](glossary.md#implementation-plan)
