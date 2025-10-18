# Migration-to-ATP-with-PL-SQL
PL/SQL Migration Script: On-Prem Oracle DB → Oracle Autonomous Transaction Processing (ATP)
This PL/SQL program is designed to automate and track the migration of data from an on-premises Oracle Database to an Oracle Autonomous Transaction Processing (ATP) database hosted in Oracle Cloud Infrastructure (OCI).

To simplify and monitor the process of moving data that has already been exported (e.g., CSV or other supported flat files) to Oracle ATP by:

Loading data from Object Storage using DBMS_CLOUD.COPY_DATA
Logging each load operation (success or failure)
Tracking errors with detailed diagnostic information
This program is especially useful when you have multiple tables to load and need an automated, auditable, and restartable migration process.

User should be familiar with following key components
Oracle Object Storage — Hosts exported CSV or data files.
DBMS_CLOUD Package — Loads the data into ATP tables.
Logging Tables — Capture migration activity and any errors.
PL/SQL Control Block — Iterates through tables, loads data, and logs outcomes.

Before I show you the PL/SQL script, I want to clarify an important point: migrating an on-premises Oracle Database to Oracle Autonomous Transaction Processing (ATP) usually involves data movement rather than pure PL/SQL code execution.

In most cases, Oracle recommends using one of these methods:
Data Pump (expdp/impdp) — the simplest and most reliable for full or partial migrations.
SQL Developer Migration Wizard — good for smaller databases.
GoldenGate or Data Guard — for minimal-downtime migration or replication.
DBMS_CLOUD — for loading data from files (CSV, Parquet, etc.) into ATP.

However, if you want a PL/SQL program that can automate the upload and import of your on-prem data into ATP (via DBMS_CLOUD), here’s PL/SQL that does give you a starting point.

