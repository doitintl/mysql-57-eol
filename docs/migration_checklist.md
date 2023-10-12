# MySQL 5.7 migration to 8.0 checklist  
This document will help make sure that proper conversations, planning, and testing have happened in order to ensure a successful migration.    

## Initial requirements, impact assessment and planning
Properly planning a major RDBMS upgrade requires an understanding of both the technical and business requirements.   
There are potential blockers that can come up, so identifying them early is key to properly executing an upgrade on time.    

- [ ] ***Business***
  - [ ] Define the **"business owner"** of the migration
    - [ ] Define success criteria
  - [ ] Identify UAT resources
  - [ ] Define a roadmap for migration milestones 
  - [ ] Validate RTO/RPO/SLA/SLO requirements for application
    - [ ] Define fail-back criteria/decision point
  - [ ] Cost planning for additional resources during migration
- [ ] ***Technical***
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