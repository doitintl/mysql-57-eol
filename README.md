# MySQL 5.7 End of life

Documents to help guide the world through MySQL 5.7 End of life, particularly those on a managed service, such as Amazon RDS and Google Cloud SQL.    
We are not looking to reproduce technical documentation, but rather supplement and aggregate documentation to help create an actionable and successful plan.

---
[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg    

---

## What is happening?

The MySQL community is planning to [deprecate MySQL 5.7 after October 31, 2023](https://www.oracle.com/us/support/library/lifetime-support-technology-069183.pdf).     
This means that there will be no security patches or bug fixes after this date.

## Amazon RDS
If you haven't already upgraded your instance to MySQL 8, [you will be automatically upgraded by the end of March, 2024](https://repost.aws/articles/ARWm1Gv0vJTIKCblhWhPXjWg/announcement-amazon-rds-for-mysql-5-7-will-reach-end-of-standard-support-on-february-29-2024).

> RDS will upgrade your MySQL 5.7 database to MySQL 8.0 during a scheduled maintenance window 
> between March 1, 2024 00:00:01 UTC and March 31, 2024 00:00:01 UTC. 
> On March 31, 2024 00:00:01 AM UTC, any MySQL 5.7 databases that remain 
> will be automatically upgraded to version 8.0 regardless of instances’ scheduled maintenance window. 

This goes without saying, but letting AWS automatically upgrading your instances will lead to major problems. 

## Google Cloud SQL
There is no officially announced end of support date, which means that it will be at [least 12 months](https://cloud.google.com/sql/docs/mysql/db-versions#major_version_deprecation_plan) from the date of writing this.
> When Cloud SQL intends to end support for a specific major version, we will send a deprecation notice alerting project owners a minimum of 12 months ahead.    

[According to a GCP community thread](https://www.googlecloudcommunity.com/gc/Databases/Cloud-SQL-MySQL-5-7-EOL/m-p/646209/highlight/true#M1743), end of support will be December, 2024.     
***NOTE:*** This is not an official announcement, but including it here for completeness.    
Upgrading to MySQL 8 also gives you the ability to use [Cloud SQL Editions Enterprise Plus](https://cloud.google.com/blog/products/databases/announcing-the-cloud-sql-enterprise-plus-edition-for-mysql-and-postgresql).

## When should we start planning/executing the upgrade?

We ***do not recommend*** waiting for automatic upgrades or deprecation notices.    
***Start planning/executing your upgrade now***

