# oracle_pdb_ass_II__29007_marnisse
# Oracle PDB Administration Assignment - INSY 8311

**Student:** Marnise  
**ID Number:** 29007  
**Course:** Database Development with PL/SQL (INSY 8311)  
**Instructor:** Eric Maniraguha  
**Date:** February 2026

---



---



---

## Assignment Tasks

### Task 1: Permanent Pluggable Database Creation

**Goal:** Establish a new PDB with appropriate user credentials following specified naming standards.

**Implementation Steps:**
1. Established connection to the container database with SYSDBA privileges
2. Generated pluggable database: `ma_pdb_29007`
3. Activated the PDB in READ WRITE operational mode
4. Navigated into the PDB container context
5. Established user account: `marnise_plsqlauca_29007`
6. Assigned necessary privileges (CONNECT, RESOURCE, DBA)
7. Validated successful user account creation

**SQL Implementation:**
```sql
-- Establish SYSDBA connection
CONNECT sys AS SYSDBA;

-- Generate pluggable database
CREATE PLUGGABLE DATABASE ma_pdb_29007
ADMIN USER pdb_admin IDENTIFIED BY 12345
CREATE_FILE_DEST = 'C:\APP\MARNISSE\PRODUCT\21C\ORADATA\XE';

-- Activate PDB
ALTER PLUGGABLE DATABASE ma_pdb_29007 OPEN;

-- Confirm PDB operational status
SELECT name, open_mode FROM v$pdbs WHERE name = 'MA_PDB_29007';

-- Navigate to PDB context
ALTER SESSION SET CONTAINER = ma_pdb_29007;

-- Establish user account
CREATE USER marnise_plsqlauca_29007 IDENTIFIED BY 12345;

-- Assign privileges
GRANT CONNECT, RESOURCE, DBA TO marnise_plsqlauca_29007;

-- Validate user account
SELECT username FROM dba_users WHERE username = 'MARNISE_PLSQLAUCA_29007';
```

**Documentation:**
- Evidence: PDB creation execution and confirmation
- Evidence: PDB operational in READ WRITE mode
- Evidence: User account successfully created and verified

---

### Task 2: Temporary PDB Lifecycle Management

**Goal:** Demonstrate complete PDB lifecycle by creating and subsequently removing a temporary pluggable database.

**Implementation Steps:**
1. Returned to container database root context
2. Generated temporary PDB: `ma_to_delete_pdb_29007`
3. Validated temporary PDB existence
4. Executed complete PDB removal including associated data files
5. Verified successful removal

**SQL Implementation:**
```sql
-- Return to CDB root context
ALTER SESSION SET CONTAINER = CDB$ROOT;

-- Generate temporary PDB
CREATE PLUGGABLE DATABASE ma_to_delete_pdb_29007
ADMIN USER temp_admin IDENTIFIED BY 12345
CREATE_FILE_DEST = 'C:\APP\MARNISSE\PRODUCT\21C\ORADATA\XE';

-- Validate PDB existence
SELECT name, open_mode FROM v$pdbs WHERE name = 'MA_TO_DELETE_PDB_29007';

-- Execute complete removal
DROP PLUGGABLE DATABASE ma_to_delete_pdb_29007 INCLUDING DATAFILES;

-- Verify removal completion
SELECT name, open_mode FROM v$pdbs WHERE name = 'MA_TO_DELETE_PDB_29007';
-- Expected result: no rows selected
```

**Documentation:**
- Evidence: Temporary PDB creation
- Evidence: PDB existence confirmation
- Evidence: Successful PDB removal execution
- Evidence: Removal verification (no rows returned)

---

### Task 3: Database Monitoring with Oracle Enterprise Manager

**Goal:** Access and document the database environment using Oracle's web-based management interface.

**Implementation Steps:**
1. Navigated to OEM interface (https://localhost:5500/em)
2. Authenticated using SYSTEM credentials
3. Accessed Database Home dashboard
4. Reviewed container database configuration with active PDBs
5. Documented visual representation of database resources

**Dashboard Details:**
- Database Instance: XE (21.3.0.0.0)
- Instance Type: Single Instance (xe)
- Architecture: Container Database with multiple pluggable databases
- System Platform: Microsoft Windows x86 64-bit
- Visual Confirmation: MA_PDB_29007 visible in Data Storage visualization

**Documentation:**
- Evidence: Complete OEM dashboard screenshot with PDB visualization

---

### Task 4: Professional Documentation & Repository

**Repository Organization:**
```
oracle_pdb_ass_II_29007_marnise/
├── README.md (current document)
└── screenshots/
    ├── task1_pdb_creation.png
    ├── task1_pdb_open.png
    ├── task1_user_created.png
    ├── task2_temp_pdb_created.png
    ├── task2_temp_pdb_exists.png
    ├── task2_pdb_deleted.png
    ├── task2_deletion_confirmed.png
    └── task3_oem_dashboard.png
```

---

## Technical Challenges & Resolutions

### Challenge 1: Data File Path Configuration
**Issue:** Initial PDB creation failed due to incorrect data file destination path specification.

**Resolution Approach:** 
- Executed query against v$datafile system view to identify actual data file location
- Identified correct path: `C:\APP\MARNISSE\PRODUCT\21C\ORADATA\XE`
- Applied CREATE_FILE_DEST parameter with verified path
- Achieved successful PDB creation

### Challenge 2: Container Context Management
**Issue:** Ensuring operations execute within appropriate container context (CDB root vs specific PDB).

**Resolution Approach:**
- Implemented ALTER SESSION SET CONTAINER for context switching
- Confirmed container context prior to operation execution
- Recognized that user creation requires PDB container context

---

## Knowledge Acquired

1. **Multitenant Architecture:** Comprehensive understanding of CDB and PDB relationships
2. **PDB Management:** Proficiency in PDB creation, activation, and removal operations
3. **Context Awareness:** Critical importance of container context for different database operations
4. **User Administration:** Creating and configuring users within isolated PDB environments
5. **Problem Resolution:** Diagnosing and resolving path configuration and context issues
6. **Monitoring Tools:** Utilizing Oracle Enterprise Manager for database oversight
7. **Documentation Standards:** Maintaining precise naming conventions and comprehensive documentation

---

## Integrity Declaration

I, Marnise (Student ID: 29007), affirm that this submission represents my individual work. All database operations were performed personally, and all evidence screenshots originate from my Oracle Database installation. I have maintained academic integrity by not copying from peers and not utilizing artificial intelligence tools for solution generation. This assignment reflects my personal comprehension and hands-on execution of Oracle Pluggable Database administration.

---

## Deliverables Summary

### Database Objects Created:
- **Production PDB:** ma_pdb_29007 (operational in READ WRITE mode)
- **User Account:** marnise_plsqlauca_29007 (configured with CONNECT, RESOURCE, DBA privileges)
- **Temporary PDB:** ma_to_delete_pdb_29007 (created and subsequently removed)

### Evidence Provided:
Complete screenshot documentation demonstrating successful completion of all assignment requirements.

---

## Repository Details

- **Repository Identifier:** oracle_pdb_ass_II_29007_marnise
- **Access Level:** Public
- **Primary PDB:** ma_pdb_29007
- **User Account:** marnise_plsqlauca_29007
- **Submission Period:** February 2026
- **Repository URL:** [To be populated upon repository creation]

---

## Technical Environment

**Oracle Configuration:**
- Edition: Express Edition (XE)
- Version: 21.3.0.0.0
- Data Storage: C:\APP\MARNISSE\PRODUCT\21C\ORADATA\XE\
- Container Database: XE

**Platform Specifications:**
- Operating System: Microsoft Windows x86 64-bit
- Management Interface: Oracle Enterprise Manager Database Express (Port 5500)

---

## Reference Materials

- Oracle Database 21c Official Documentation
- Oracle Multitenant Architecture Administration Guide
- Oracle Database Administrator's Reference Manual
- INSY 8311 Course Materials: Database Development with PL/SQL
- Oracle Enterprise Manager Database Express User Documentation

---

## Scope Summary

This assignment validates Oracle Pluggable Database administration capabilities through four practical exercises:

1. **Exercise 1:** Production PDB establishment (`ma_pdb_29007`) with user configuration (`marnise_plsqlauca_29007`)

2. **Exercise 2:** Temporary PDB lifecycle demonstration (`ma_to_delete_pdb_29007`) - complete creation and removal

3. **Exercise 3:** Database monitoring through Oracle Enterprise Manager interface

4. **Exercise 4:** Professional technical documentation publication via GitHub platform

**Core Competencies:** PDB lifecycle administration, user management, Oracle Enterprise Manager utilization, technical documentation standards.

---

## Final Notes

This assignment successfully demonstrates essential Oracle Pluggable Database administration competencies, including creation, management, removal, and monitoring using SQL commands and Oracle Enterprise Manager interface.

Naming conventions strictly adhere to assignment specifications:
- PDB naming format: [FirstTwoLettersOfName]_pdb_[StudentID]
- User naming format: [FirstName]_plsqlauca_[StudentID]
- Repository naming format: oracle_pdb_ass_II_[StudentID]_[FirstName]

---

**Documentation Complete**
