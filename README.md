# Oracle Pluggable Database Management Report
**Course Assignment II**

## 1. Submission Details
* **Student Name:** Nt... Fabrice
* **Student ID:** 29264
* **GitHub Repository URL:** https://github.com
* **Submission Date:** September 22, 2026

---

## 2. Oracle Environment Used
* **Database Management System:** Oracle AI Database 26ai (Free Developer Edition)
* **Graphical User Interface:** Oracle SQL Developer
* **Operating System Environment:** Windows Local Environment / Docker Container Architecture
* **Connection Profile:** Administrative `SYS` connection executing as `SYSDBA`

---

## 3. Overview of Completed Tasks

### Task 1: Creation of a New Pluggable Database (PDB)
* **Goal:** Provision a dedicated pluggable database infrastructure and establish a distinct student database user schema for long-term course utilization.
* **Database Name:** `nt_pdb_29264`
* **Local User Schema:** `nt_plsqlauca_29264`
* **Implementation Logic:** Initiated an isolated clone container using the base database seed. A custom dedicated storage tablespace (`USERS`) was constructed to serve as the default storage workspace layer for the schema. Full operational grants (`CREATE SESSION`, `TABLE`, `VIEW`, `SEQUENCE`, `PROCEDURE`) were allocated to ensure full sandbox development autonomy.

### Task 2: Lifecycle Management (Create and Delete a PDB)
* **Goal:** Verify administrative database lifecycle capabilities by creating and entirely destroying a container profile.
* **Database Name:** `nt_to_delete_pdb_29264`
* **Implementation Logic:** A temporary container database was provisioned to test isolated allocation rules. The active container instance was forcefully unmounted, closed, and permanently removed from the master cluster configuration using the `INCLUDING DATAFILES` clause to ensure complete physical disk cleaning.

### Task 3: Infrastructure Verification via Dashboard Management
* **Goal:** Leverage graphical administrative consoles to monitor architecture mappings, running database instances, and user access layers.
* **Implementation Logic:** Utilized the native built-in SQL Developer DBA Management dashboard console. Because legacy web browser engines (EM Express) have been officially desupported in the Oracle 23ai / 26ai family line, the database status environment trees and administrative tablespace monitors were examined and validated directly through the modern DBA workspace suite.

---

## 4. Technical Challenges Faced & Resolutions

1. **Missing File Paths Setup (`ORA-65016`):**
   * *Challenge:* The seed database clone initially failed because explicit storage pathways were not defined.
   * *Resolution:* Re-engineered the syntax to include an active `FILE_NAME_CONVERT = ('pdbseed', 'nt_pdb_29264')` mapping, aligning the database architecture cleanly to the server file paths.

2. **Special Characters in Passwords (`ORA-00922`):**
   * *Challenge:* The use of unquoted trailing exclamation marks (`!`) broke the SQL engine syntax rules for user provisioning.
   * *Resolution:* Standardized the credentials into a clean, alphanumeric layout (`StudentPass123`) to ensure absolute platform compliance.

3. **Tablespace Area Discrepancy (`ORA-02156` / Missing Tablespace):**
   * *Challenge:* A newly cloned pluggable database contains only bare-minimum system folders, meaning assigning profiles directly to a missing `USERS` directory breaks database mapping.
   * *Resolution:* Executed a `CREATE TABLESPACE` script ahead of setting the default profile options to map structural parameters perfectly.

---

## 5. Integrity Statement
I hereby declare that the assignments, structural adjustments, and database administrative configurations presented across this repository represent my own individual, authentic work. All configuration metrics, architecture names, and student attributes precisely follow the explicit validation rules dictated by the department.

---
*Note: Evidence screenshots validating successful execution strings for Tasks 1, 2, and 3 have been committed directly to the repository asset tree alongside this file.*
